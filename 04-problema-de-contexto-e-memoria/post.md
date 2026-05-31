# O problema de contexto e memória: por que a janela é a restrição estrutural de todo agent

![Cover](https://raw.githubusercontent.com/DScardini91/medium-ai-series/main/04-problema-de-contexto-e-memoria/images/cover.png)

---

O erro mais caro que vejo em projetos de IA agentic não é escolher o modelo errado. É ignorar o problema de contexto até ele aparecer em produção, numa tarefa longa, quando o sistema perde o fio do que estava fazendo.

## O que é a janela de contexto

Cada chamada a uma LLM tem um limite de texto que pode ser processado de uma vez. Esse limite se chama janela de contexto. Ele é medido em tokens, onde um token corresponde aproximadamente a quatro caracteres.

A janela inclui tudo: instrução do sistema, histórico de conversa, documentos de referência, resposta gerada. Quando o total ultrapassa o limite, o que está fora da janela desaparece da perspectiva do modelo. Não é comprimido, não é resumido automaticamente. Some.

Os modelos atuais têm janelas grandes comparadas aos primeiros LLMs. Isso resolve muitos casos simples. Não resolve o caso geral.

Um agent que trabalha em tarefas longas, processa documentos extensos ou mantém contexto entre sessões vai enfrenter esse limite como questão de design, não como exceção.

## Por que isso é o limite real

Um agent com ferramentas pode executar ações externas. Mas a LLM que decide qual ação executar só vê o que está na janela. Se o contexto relevante não couber, a decisão é tomada com informação parcial.

Isso produz falhas características. O agent contradiz uma decisão tomada dez turnos antes porque essa decisão já saiu da janela. O agent refaz trabalho que já estava feito porque perdeu o registro do progresso. O agent falha em manter coerência entre etapas de um plano porque o início do plano não cabe junto com o estado atual.

Essas não são falhas do modelo. São falhas de arquitetura. O modelo está fazendo o que pode com o que recebeu. O problema é que o sistema não gerenciou o que entregar.

## Memória como problema de design

Sistemas duráveis resolvem isso com arquitetura de memória. Não é um feature que se liga, é uma decisão de projeto.

Existem quatro tipos de memória relevantes para agents. Memória de trabalho é o que está na janela agora: contexto imediato, estado atual, instrução em vigor. Memória episódica é o histórico de interações anteriores: o que foi pedido, o que foi feito, o que funcionou. Memória semântica é conhecimento estruturado persistido externamente: documentos, bases de dados, especificações. Memória procedural é o registro de como fazer coisas: sequências, padrões, heurísticas.

Um agent ingênuo só tem memória de trabalho. Cada sessão começa do zero. Um sistema robusto gerencia os quatro tipos: recupera o que é relevante, comprime o que é histórico, descarta o que expirou.

A pergunta que separa pipelines ingênuos de sistemas sérios: quando esse agent começar uma tarefa amanhã, o que ele vai saber sobre o que fez hoje?

## O que sistemas duráveis fazem diferente

Os projetos que funcionam em produção por mais de algumas semanas têm três propriedades em comum.

Primeiro: scratchpad explícito. O agent grava estado de progresso em formato estruturado fora da janela. A cada passo, lê o estado antes de decidir. Não depende do histórico de conversa para saber onde parou.

Segundo: recuperação seletiva. Em vez de injetar todo o contexto histórico na janela, o sistema recupera o que é relevante para a tarefa atual. Busca semântica, filtro por metadado, priorização por recência. O que entra na janela é curado, não despejado.

Terceiro: fronteiras de sessão deliberadas. O sistema define quando uma sessão termina e o que deve persistir para a próxima. Isso evita que uma tarefa longa tente caber em uma janela que não comporta e produza degradação silenciosa no meio do caminho.

Esses três padrões não são sofisticação desnecessária. São o mínimo para que um agent faça trabalho real sem ser supervisionado turno a turno.

## O problema que não desaparece com modelos maiores

Janelas maiores empurram o problema para frente. Não resolvem.

Uma tarefa suficientemente longa vai encher qualquer janela. Um sistema com múltiplos agents vai dividir contexto entre eles. Uma organização que usa IA em fluxos de trabalho vai precisar de memória persistente que atravessa sessões, usuários e instâncias.

No próximo post, como um sistema agentic completo lida com isso na prática: não um agent com janela grande, mas uma arquitetura projetada para durar.

---

🐧 _"O modelo esquece. O sistema não pode esquecer."_
