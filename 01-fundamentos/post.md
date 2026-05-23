# Da IA clássica aos agentic systems: capivaras e ratos são roedores, mas é melhor não confundir

**Subtítulo:** Capivara e rato são roedores, mas não intercambiáveis. IA clássica, ML, LLM, agent e agentic system: mesma família técnica, problemas diferentes. Confundir custa caro em escopo, custo e risco.

![Capítulo 1, Fundamentos](https://raw.githubusercontent.com/DScardini91/medium-ai-series/main/01-fundamentos/images/cover.png)

---

Capivara e rato são roedores. Confundir custa caro. "Vamos usar IA" virou frase de reunião e embrulha seis coisas diferentes: IA clássica, machine learning, IA generativa, LLM, agent e agentic system. Mesma família técnica, problemas diferentes. Quatro transições históricas separam os seis.

## De regras a exemplos

Programação tradicional é assim: o humano escreve regras explícitas, o computador executa. Se a temperatura passa de X, ligue o alarme. Funciona bem quando o problema cabe em regras.

A IA clássica, dos anos 70 aos 90, era extensão disso. Sistemas especialistas codificavam o raciocínio de um médico, um engenheiro, um analista de crédito em árvores de regras. Funcionou pra problemas estreitos. Não escalou pro mundo real porque a combinatória de regras explode quando o domínio cresce.

A virada foi o machine learning. Em vez de escrever regras, mostrar exemplos. Mostre dez mil casos de crédito que deram certo e dez mil que deram errado, e o modelo ajusta parâmetros pra minimizar erro nos exemplos. O humano deixa de escrever regras de negócio, mas continua escolhendo arquitetura, features, função de perda e critério de validação. A inteligência muda de lugar, não desaparece de mãos humanas.

Esse paradigma se consolidou em produção empresarial nos anos 2010 e continua sendo a espinha dorsal de ML em escala hoje. Detecção de fraude, churn, scoring de crédito, recomendação: tudo isso roda predominantemente em modelos não-generativos. GenAI não substituiu ML clássico. Complementou.

## De previsão de palavras a compreensão de contexto

ML escalou, mas continuava aprendendo padrões em tarefas estreitas. Em 2017, oito pesquisadores do Google e da University of Toronto publicaram *Attention Is All You Need*. A arquitetura proposta, o transformer, foi avaliada inicialmente em tradução automática. Permitia treinar previsão de próxima palavra em escala de bilhões de parâmetros, mantendo memória do contexto inteiro.

Modelos treinados com transformer em volumes massivos de texto são as LLMs (large language models). No início faziam uma coisa só: prever a próxima palavra dado um contexto. Em escala, essa previsão passou a produzir algo próximo de compreensão de contexto: síntese, reformulação, tradução de intenção em linguagem estruturada.

ChatGPT chegou em novembro de 2022. O modelo subjacente não era novo. GPT-3 foi liberado via API em junho de 2020, e InstructGPT, variante fine-tuned com RLHF e ancestral direto do ChatGPT, foi publicado em janeiro de 2022. O que mudou em novembro foi a interface conversacional com memória de turno: uma API técnica virou caixa de texto. O salto foi de distribuição, não de capacidade. Distinção que muda escopo de projeto: comprar "uma IA generativa" pode ser comprar acesso a um modelo via API ou comprar uma experiência conversacional pronta. São esforços diferentes.

## De resposta a ação

Uma LLM responde probabilisticamente. Prevê a sequência de palavras mais provável dado o contexto. Funciona pra gerar, sumarizar, traduzir, reformular. Não funciona quando o problema exige resposta determinística ou ação no mundo real.

A solução foi dar ferramentas à LLM. Primeiro pra validar: calculadora, busca, consulta a banco de dados. Quando a LLM precisava de um número exato, chamava a calculadora em vez de inventar. Depois pra atuar: chamar APIs, escrever arquivos, executar código, mandar email.

Agent se define pelo loop, não pelo stack: percebe, decide a ação, executa, observa, decide o próximo passo. Agents existiam em reinforcement learning desde os anos 80, com marcos como TD-Gammon (1992) e AlphaGo (2016) muito antes das LLMs. Hoje o substrato comum é LLM mais ferramentas mais um loop de decisão, mas a definição precede a tecnologia. Quem usa agent terceiriza julgamento, não execução.

Quando alguém diz "estou usando agent", duas perguntas separam substância de nome: quais ferramentas o agent acessa, e qual loop de decisão roda. Sem resposta, é LLM rebatizada.

## De um a muitos

Um agent sozinho cobre uma faixa de tarefas. Quando o problema cresce, o caminho natural é orquestrar vários.

Aparecem padrões diferentes para essa orquestração: paralelismo, especialização, hierarquia, e outros. Cada um resolve um tipo de gargalo, cada um cobra um tipo de custo. O Capítulo 3 da série abre essas arquiteturas.

O ponto pra fechar este post: agentic system é mais um nível de abstração sobre o agent solo. Resolve problemas que um agent não resolve, mas cada handoff entre agents é um ponto de falha adicional que precisa ser desenhado.

## Em 2026, o erro caro não é mais "não fazer IA"

É confundir uma família com a outra na hora de decidir. É contratar agentic system pra um problema que um classificador resolve com metade do custo e o dobro da confiabilidade. É prometer agent quando o que está em pé é uma LLM com prompt. É comprar uma plataforma generativa quando o caso de uso é previsão de demanda.

Capivara não é rato. Saber qual está na mesa é metade do projeto. A outra metade é abrir cada uma delas. No próximo post, abro a LLM: como funciona por dentro, por que a janela de contexto é a restrição estrutural do agent, e o que isso muda na hora de comprar.

---

🐧 _"Sorriam e acenem, rapazes."_
