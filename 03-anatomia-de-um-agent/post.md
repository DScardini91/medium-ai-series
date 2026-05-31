# Anatomia de um agent: o que muda quando uma LLM ganha ferramentas e um loop para decidir

![Cover](https://raw.githubusercontent.com/DScardini91/medium-ai-series/main/03-anatomia-de-um-agent/images/cover.png)

---

Uma LLM devolve texto. Um agent executa ação. A distância entre os dois parece pequena. Na prática, muda tudo sobre o que pode ser delegado.

## Uma LLM não faz nada sozinha

O Post anterior mostrou como o ChatGPT funciona: LLM recebe texto, prevê continuação, wrapper organiza o contexto. O processo começa e termina em linguagem. A LLM não acessa internet, não escreve arquivo, não envia email. Pode descrever como fazer. Não faz.

Para um assistente conversacional, isso é suficiente. Para a maioria das tarefas reais de trabalho, não é.

## O loop que criou o agent

Agent não é um tipo de modelo. É um padrão de execução.

A receita: LLM mais ferramentas mais um loop de decisão. O loop funciona assim. O sistema percebe o estado atual do problema: o que foi pedido, o que já aconteceu, o que está disponível. A LLM decide qual ação tomar: chamar API, buscar dado, executar código, escrever arquivo. A ferramenta executa. O resultado volta como novo contexto. O sistema avalia se o objetivo foi atingido. Se não, decide o próximo passo.

Cada iteração é um turno de percepção, decisão e execução. O que muda entre um agent simples e um sofisticado não é o princípio, é a qualidade do planejamento, a variedade das ferramentas e o critério de parada.

O que não muda: é a LLM que decide, não o sistema que orquestra. A LLM lê o estado, produz a próxima ação como texto estruturado, e o executor chama a ferramenta correspondente.

## Três perguntas que separam agent de chatbot com prompts

Na prática, muito do que se vende como agent é uma LLM com prompt sofisticado. A distinção importa porque o risco é diferente.

Primeira pergunta: quais ferramentas o sistema pode chamar? Se a resposta é "nenhuma além de texto", não é agent.

Segunda pergunta: o sistema executa mais de um passo sem intervenção humana entre eles? Se cada ação exige confirmação manual, é um assistente com interface, não um agent com autonomia.

Terceira pergunta: quem define o critério de parada? Se o humano decide quando terminar a cada turno, o loop está no humano. Agent de verdade tem critério de conclusão embutido.

Essas três perguntas separam substância de etiqueta. Em projetos que conheço, a diferença vira custo real: agents que não são agents têm latência de humano em cada passo; agents reais sem critério de parada entram em loop.

## O que muda quando se delega ação, não resposta

Delegação de texto é relativamente segura. O pior que acontece é uma resposta errada que o humano lê e descarta.

Delegação de ação tem consequências no mundo real. O agent que escreve email envia. O que executa código modifica dados. O que chama API gasta crédito, altera estado, aciona efeitos colaterais.

Isso muda a conversa sobre governança. Quem usa LLM terceiriza julgamento sobre linguagem. Quem usa agent terceiriza julgamento sobre ação. São ordens de responsabilidade diferentes.

O critério prático que uso para avaliar se um sistema merece ser chamado de agent: ele consegue atingir um objetivo de múltiplos passos, com ferramentas reais, com critério de parada definido, sem intervenção humana em cada turno. Se sim, é agent. Se não, pode ser útil de outras formas, mas é outra coisa.

## O próximo problema

Quanto mais ferramentas, mais poderoso. Mas o substrato continua sendo a LLM, e a LLM tem um limite estrutural que nenhuma ferramenta resolve: a janela de contexto.

É esse limite que o próximo post abre. Por que ele é a restrição real de todo agent, e o que muda no design de sistemas quando se leva isso a sério.

---

🐧 _"Agent age. LLM responde. Saber a diferença é saber o que delegar."_
