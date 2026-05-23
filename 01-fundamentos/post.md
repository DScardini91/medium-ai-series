# Da IA clássica aos agentic systems: capivaras e ratos são roedores, mas é melhor não confundir

**Subtítulo:** IA clássica, ML, LLM, agent e agentic system: mesma família técnica, problemas diferentes. Confundir custa caro em escopo, custo e risco.

![Capítulo 1, Fundamentos](https://raw.githubusercontent.com/DScardini91/medium-ai-series/main/01-fundamentos/images/cover.png)

---

"Vamos usar IA" virou frase de reunião. E quase nunca quer dizer a mesma coisa duas vezes.

Na prática, embrulha seis coisas diferentes: IA clássica, machine learning, IA generativa, LLM, agent e agentic system. Mesma família técnica, problemas bem diferentes. Entre uma ponta e outra, quatro viradas históricas que vale separar antes de assinar qualquer projeto.

## De regras a exemplos

Programação tradicional é assim: o humano escreve regras explícitas, o computador executa. Se a temperatura passa de X, dispara o alarme. Direto. Funciona bem quando o problema cabe em regras.

A IA clássica, que dominou dos anos 70 aos 90, é uma extensão natural disso. A ideia era pegar o raciocínio de um médico, de um engenheiro, de um analista de crédito, e codificar em árvores de regras gigantes — os famosos sistemas especialistas. Funcionou pra problemas estreitos. Mas quando o domínio crescia, a combinatória explodia. Não tem como escrever regra pra tudo.

A virada foi o machine learning. Em vez de escrever regras, mostrar exemplos.

Mostre dez mil casos de crédito que deram certo e dez mil que deram errado. O modelo ajusta parâmetros sozinho pra minimizar o erro. O humano sai de cena? Não. Continua escolhendo arquitetura, features, função de perda, critério de validação. A inteligência muda de lugar. Não some das mãos humanas.

Isso entrou em produção empresarial nos anos 2010 e até hoje é a espinha dorsal de ML em escala. Detecção de fraude, churn, scoring de crédito, recomendação: tudo isso roda majoritariamente em modelos não-generativos. GenAI não substituiu ML clássico. Complementou.

## De previsão de palavras a compreensão de contexto

ML escalou bonito. Mas continuava preso a tarefas estreitas — uma rede pra fraude, outra pra churn, outra pra recomendação.

Aí em 2017, oito pesquisadores do Google e da University of Toronto publicaram *Attention Is All You Need*. A arquitetura proposta, o transformer, estreou em tradução automática. O que ela destravou foi outra coisa: dava pra treinar previsão de próxima palavra em escala de bilhões de parâmetros sem perder o contexto inteiro de vista.

Modelos treinados assim, transformer em cima de volumes massivos de texto, são as LLMs (large language models). No início, faziam uma coisa só: prever a próxima palavra dado o contexto. Acontece que, em escala suficiente, essa previsão simples começou a parecer compreensão de verdade. Síntese, reformulação, tradução de intenção em linguagem estruturada — tudo emerge da mesma mecânica de "qual a próxima palavra".

![Como uma LLM é treinada](https://raw.githubusercontent.com/DScardini91/medium-ai-series/main/01-fundamentos/images/llm-training.png)

ChatGPT chegou em novembro de 2022. O modelo subjacente não era novidade. GPT-3 já estava em API desde junho de 2020, e InstructGPT, variante fine-tuned com RLHF e ancestral direto do ChatGPT, saiu em janeiro de 2022. O que mudou em novembro foi a interface: uma API técnica virou caixa de texto com memória de turno. Salto de distribuição, não de capacidade.

E isso muda escopo de projeto inteiro. Quando alguém fala em "comprar uma IA generativa", pode estar falando de acesso a um modelo via API ou de uma experiência conversacional pronta pra usar. Dois esforços, dois orçamentos, dois timelines.

## De resposta a ação

A LLM, por dentro, é uma máquina probabilística: prevê a sequência de palavras mais provável dado o contexto que recebeu. Isso resolve um monte de coisa: gerar, sumarizar, traduzir, reformular. Mas tem um limite claro. Quando o problema exige resposta determinística ou ação no mundo real, "palavra mais provável" não basta.

A saída foi dar ferramentas pra LLM usar. Primeiro pra validar: calculadora, busca, consulta a banco de dados. Se a LLM precisa de um número exato, ela aprende a chamar a calculadora em vez de usar previsões mais prováveis. Depois veio o passo natural: deixar a LLM atuar de fato — chamar API, escrever arquivo, executar código, mandar email.

Agent não se define pela tecnologia que tem por baixo, e sim pelo loop que ele roda: percebe, decide a ação, executa, observa, decide o próximo passo. E olha que isso não é invenção recente. Agents existem em reinforcement learning desde os anos 80, com marcos como TD-Gammon (1992) e AlphaGo (2016), muito antes de LLM virar assunto. O que mudou foi o substrato: hoje a receita comum é LLM mais ferramentas mais um loop de decisão. Mas a definição vem antes da tecnologia.

E o ponto prático é esse: quem usa agent terceiriza julgamento, não só execução.

Então, quando alguém diz "estou usando agent", duas perguntas separam substância de etiqueta — quais ferramentas o agent acessa, e qual loop de decisão ele roda. Sem resposta clara, provavelmente é LLM rebatizada.

## De um a muitos

Um agent sozinho cobre uma faixa de tarefas. Boa, mas finita. Quando o problema cresce além disso, o caminho natural é orquestrar vários trabalhando juntos. É aí que entra agentic system.

E aparecem vários padrões pra fazer essa orquestração: paralelismo, especialização, hierarquia, entre outros. Cada um resolve um tipo de gargalo, e cada um cobra um tipo de custo. O Capítulo 3 da série abre essas arquiteturas com calma.

Agentic system é mais um nível de abstração em cima do agent solo. Resolve problemas que um agent sozinho não resolve, sim. Mas cada handoff entre agents é mais um ponto de falha que precisa ser desenhado. Não vem de graça.

## Em 2026, o erro caro não é mais "não fazer IA"

É confundir uma família com a outra na hora de decidir. É contratar agentic system pra um problema que um classificador resolve com metade do custo e o dobro da confiabilidade. É prometer agent quando o que está em pé é uma LLM com prompt. É comprar uma plataforma generativa quando o caso de uso é previsão de demanda.

Capivara não é rato. Saber qual bicho está na mesa é metade do projeto.

A outra metade é abrir cada um deles. No próximo post, abro a LLM por dentro: por que a janela de contexto é a restrição estrutural de todo agent que vem depois, e o que isso muda na hora de assinar contrato.

---

🐧 _"Sorriam e acenem, rapazes."_
