# Meu agentic OS: como um sistema de agents coordenados muda a lógica do trabalho

![Cover](https://raw.githubusercontent.com/DScardini91/medium-ai-series/main/05-meu-agentic-os/images/cover.png)

---

Construí o que chamo de agentic OS: um conjunto de agents especializados que coordenam trabalho de forma sistemática. Não é um projeto isolado. É infraestrutura.

O processo de construir e manter esse sistema mudou como penso sobre delegação e sobre o que vale automatizar.

## Um agent resolve uma tarefa. Um sistema resolve uma categoria.

O ponto de inflexão não foi adicionar mais agents. Foi quando parei de pensar em "qual agent faz X" e comecei a pensar em "como o sistema lida com a categoria X".

A diferença é real. Um agent de revisão de texto faz uma coisa bem e uma coisa só. Um sistema de revisão tem memória do que já foi revisado, padrões de feedback que persistem, critérios que evoluem, e capacidade de distinguir revisão de rascunho de revisão pré-publicação sem que eu explique a diferença a cada chamada.

Um agent é uma ferramenta. Um sistema é infraestrutura.

O custo de construir infraestrutura é maior. O retorno é que ela fica melhor com o uso, em vez de voltar ao zero a cada sessão.

## Como um agentic OS funciona na prática

O meu tem três camadas.

A primeira é memória. Não a janela de contexto de uma sessão, mas memória persistente entre sessões, usuários e contextos. O que foi decidido antes. Quais padrões emergiram. O que está em andamento. Um agent sem memória começa do zero toda vez. Um sistema sem memória central não tem coordenação real.

A segunda é especialização. Cada agent tem um domínio claro: análise financeira, revisão de texto, planejamento de projeto, pesquisa. Agente generalista que faz tudo não fica bom em nada. O custo da especialização é precisar de orquestração. O benefício é profundidade real em cada domínio.

A terceira é o plano de controle. Quem decide o que fazer agora. Que agent acionar. Como integrar resultados. Em sistemas simples, o humano faz isso turno a turno. Em sistemas maduros, há um orquestrador que lê estado, distribui trabalho e integra resultados. Não é magia: é código e critérios explícitos.

## O que o sistema ensina ao ser construído

Primeiro: a dificuldade está nos handoffs, não nos agents individuais. Cada agent funciona bem isolado. O problema aparece quando um precisa passar contexto para o outro sem perder fidelidade. Um briefing mal estruturado na saída de um agent produz retrabalho no próximo.

Segundo: memória mal projetada é pior que nenhuma memória. Um sistema que acumula tudo sem estrutura produz janelas entupidas e recuperação imprecisa. O que entra na memória, em qual formato e com qual metadado importa tanto quanto o que os agents fazem.

Terceiro: o valor composto aparece tarde. Nas primeiras semanas, um agent bem configurado individualmente parece mais eficiente do que o sistema. O sistema começa a ganhar quando os padrões persistem, quando o contexto se acumula com estrutura, quando o histórico de decisões informa decisões novas. O horizonte relevante é meses, não dias.

## O que é aplicável independente de escala

Não precisar de um sistema completo para aproveitar os princípios.

Mesmo com um único agent, a pergunta "o que esse agent precisa saber antes de começar" e "o que deve persistir quando terminar" muda a qualidade do resultado. A diferença entre um agent que começa do zero toda vez e um que tem contexto estruturado para trabalhar é a diferença entre um freelancer e um colaborador com histórico.

O que muda quando se pensa em sistema, mesmo pequeno: decisões sobre o que persistir, formatos que facilitam recuperação, critérios explícitos de quando uma tarefa termina.

No próximo post, como avaliar o que vale delegar e o que não vale. O critério não é o que é possível. É o que faz sentido dado o custo de falha.

---

🐧 _"A diferença entre agent e sistema é a diferença entre tarefa e infraestrutura."_
