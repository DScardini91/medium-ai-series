# Da IA clássica aos agentic systems: capivaras e ratos são roedores, mas é melhor não confundir

**Subtítulo:** IA clássica, ML, LLM, agent e agentic system: mesma família técnica, problemas diferentes. Confundir custa caro em escopo, custo e risco.

![Capítulo 1, Fundamentos](https://raw.githubusercontent.com/DScardini91/medium-ai-series/main/01-fundamentos/images/cover.png)

---

"Vamos usar IA" virou frase de reunião. E quase nunca quer dizer a mesma coisa duas vezes.

Na prática, embrulha seis coisas diferentes: IA clássica, machine learning, IA generativa, LLM, agent e agentic system. Mesma família técnica, problemas bem diferentes. Entre uma ponta e outra, quatro viradas históricas que vale separar antes de assinar qualquer projeto.

## De regras a exemplos

Programação tradicional é assim: o humano escreve regras explícitas, o computador executa. Se a temperatura passa de X, dispara o alarme. Direto. Funciona bem quando o problema cabe em regras.

A IA clássica, que dominou dos anos 70 aos 90, foi uma extensão natural disso. A ideia era pegar o raciocínio de um médico, de um engenheiro, de um analista de crédito, e codificar em árvores de regras gigantes — os famosos sistemas especialistas. Funcionou para problemas estreitos. Mas quando o domínio crescia, a combinatória explodia. Não tem como escrever regra para tudo.

A virada foi o machine learning. Em vez de escrever regras, mostrar exemplos.

Mostre dez mil casos de crédito que deram certo e dez mil que deram errado. O modelo ajusta os parâmetros sozinho para minimizar o erro. O humano sai de cena? Não. Continua escolhendo arquitetura, features, função de perda, critério de validação. A inteligência muda de lugar — não some das mãos humanas.

Isso entrou em produção empresarial nos anos 2010 e até hoje é a espinha dorsal de ML em escala. Detecção de fraude, churn, scoring de crédito, recomendação: tudo isso roda majoritariamente em modelos não-generativos. GenAI não substituiu ML clássico. Complementou.

## De previsão de palavras a compreensão de contexto

ML escalou bonito. Mas continuava preso a tarefas estreitas — uma rede para fraude, outra para churn, outra para recomendação.

Aí em 2017, oito pesquisadores do Google e da University of Toronto publicaram *Attention Is All You Need*. O nome é inocente. O que o paper destravou não foi. A arquitetura proposta, o transformer, estreou em tradução automática, mas o que ela realmente permitia era treinar previsão de próxima palavra em escala de bilhões de parâmetros sem perder o contexto inteiro de vista.

Modelos treinados assim — transformer em cima de volumes massivos de texto — são as LLMs (large language models). No início, faziam uma coisa só: prever a próxima palavra dado o contexto. Acontece que, em escala suficiente, essa previsão simples começou a parecer compreensão de verdade. Síntese, reformulação, tradução de intenção em linguagem estruturada: tudo emerge da mesma mecânica de "qual a próxima palavra".

![Como uma LLM é treinada](https://raw.githubusercontent.com/DScardini91/medium-ai-series/main/01-fundamentos/images/llm-training.png)

ChatGPT chegou em novembro de 2022. Mas o modelo subjacente não era novidade. GPT-3 já estava em API desde junho de 2020, e InstructGPT — variante fine-tuned com RLHF e ancestral direto do ChatGPT — saiu em janeiro de 2022. O que mudou em novembro foi a interface: uma API técnica virou caixa de texto com memória de turno. Salto de distribuição, não de capacidade.

Isso importa na hora de escopo. Quando alguém fala em "comprar uma IA generativa", pode estar falando de acesso a um modelo via API ou de uma experiência conversacional pronta para usar. Dois esforços, dois orçamentos, dois timelines. A confusão entre os dois está em quase toda licitação de IA que já li.

## De resposta a ação

A LLM, por dentro, é uma máquina probabilística: prevê a sequência de palavras mais provável dado o contexto que recebeu. Isso resolve bastante coisa — gerar, sumarizar, traduzir, reformular. Mas tem um limite natural. Quando o problema exige resposta determinística ou ação no mundo real, "palavra mais provável" não basta.

A saída foi dar ferramentas para a LLM usar. Primeiro para validar: calculadora, busca, consulta a banco de dados. Se a LLM precisa de um número exato, ela aprende a chamar a calculadora em vez de fazer conta no escuro. Depois veio o passo seguinte: deixar a LLM atuar de fato — chamar API, escrever arquivo, executar código, mandar email.

É aí que nasce o agent. Não é uma questão de tecnologia, é uma questão de loop: percebe o estado do mundo, decide uma ação, executa, observa o resultado, decide o próximo passo. E isso não é invenção recente — agents existem em reinforcement learning desde os anos 80, com marcos como TD-Gammon em 1992 e AlphaGo em 2016, muito antes de LLM virar assunto de reunião. O que mudou foi o substrato: hoje a receita comum é LLM mais ferramentas mais esse loop de decisão.

![ChatGPT responde, agent age — a diferença está no loop](https://raw.githubusercontent.com/DScardini91/medium-ai-series/main/01-fundamentos/images/agent-loop.png)

Há uma consequência prática que pouca gente nomeia: quem usa agent não está apenas terceirizando execução. Está terceirizando julgamento. O que muda completamente a conversa sobre governança, auditabilidade e tolerância ao erro.

Quando alguém diz "estou usando agent", duas perguntas bastam para separar substância de etiqueta: quais ferramentas ele acessa, e qual loop de decisão ele roda. Sem resposta clara para as duas, provavelmente é uma LLM com prompt bem feito — o que pode ser suficiente, mas é outra coisa.

## De um a muitos

Um agent sozinho cobre uma faixa de tarefas. Boa, mas finita. Quando o problema cresce além disso, o caminho natural é orquestrar vários trabalhando juntos — e é aí que entra agentic system.

Existem vários padrões para fazer essa orquestração: paralelismo, especialização, hierarquia, entre outros. Cada um resolve um tipo de gargalo. Cada um cobra um tipo de custo. O Capítulo 3 da série abre essas arquiteturas com calma.

O que vale registrar agora: agentic system não é agent com esteroides. É um nível de abstração diferente, com problemas próprios. Cada handoff entre agents é mais um ponto de falha que precisa ser desenhado. Cada decisão distribuída é uma decisão que ninguém tomou de forma centralizada. Não vem de graça, e a maioria dos projetos que conheço subestima esse custo.

## Em 2026, o erro caro não é mais "não fazer IA"

É confundir uma família com a outra na hora de decidir. É contratar agentic system para um problema que um classificador resolve com metade do custo e o dobro da confiabilidade. É prometer agent quando o que está em pé é uma LLM com prompt. É comprar uma plataforma generativa quando o caso de uso é previsão de demanda.

Capivara não é rato. Saber qual bicho está na mesa é metade do projeto.

A outra metade é abrir cada um deles. No próximo post, abro a LLM por dentro: por que a janela de contexto é a restrição estrutural de todo agent que vem depois, e o que isso muda na hora de assinar contrato.

---

🐧 _"Sorriam e acenem, rapazes."_
