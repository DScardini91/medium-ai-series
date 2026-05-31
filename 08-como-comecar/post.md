# Como começar: cinco arquétipos de uso de IA agentic e o que cada um exige

![Cover](https://raw.githubusercontent.com/DScardini91/medium-ai-series/main/08-como-comecar/images/cover.png)

---

Não existe um nível certo de uso de IA agentic. Existe o nível que faz sentido dado o papel, o contexto e o quanto de investimento de setup faz sentido agora.

O que existe são arquétipos reconhecíveis. Cada um tem um ponto de entrada diferente, um custo de setup diferente, e um retorno esperado diferente. O objetivo desta série foi dar vocabulário e profundidade suficientes para identificar em qual arquétipo cada um se encaixa, e o que fazer a partir daí.

## A pergunta errada

"Como usar IA" é a pergunta que gera mais confusão na prática. É vaga demais para produzir resposta útil.

A pergunta que abre caminho: que trabalho repetitivo ou cognitivamente caro consome tempo de forma desproporcional ao valor que gera? Esse é o candidato. A automação vai onde há repetição com custo de falha tolerável e volume suficiente para justificar o setup.

Sem essa pergunta respondida, o mais provável é adicionar mais uma ferramenta que se usa por duas semanas e some da rotina.

## Os cinco arquétipos

**Arquétipo 1: Usuário aumentado.** Usa LLM como assistente de texto e pesquisa. ChatGPT, Copilot, Claude direto pela interface. Nenhuma configuração de agent. Ganho imediato, teto de valor baixo. Não requer investimento técnico. É onde a maioria está e onde faz sentido começar se o objetivo é resultado rápido sem overhead.

**Arquétipo 2: Usuário com contexto.** Usa a mesma interface mas com prompts de sistema estruturados, documentos de referência injetados, e padrões de interação que persistem por projeto. O mesmo modelo rende três vezes mais quando recebe contexto rico antes da tarefa. Investimento: algumas horas de estruturação de prompt e organização de referências. Nenhum código necessário.

**Arquétipo 3: Construtor de fluxos.** Usa ferramentas como n8n, Make ou similares para montar pipelines com LLM como componente. Trigger acontece, dados passam por transformação, LLM processa parte específica, resultado segue o fluxo. Automação real sem código de agent. Investimento: um fim de semana para o primeiro fluxo funcionando. Exige clareza sobre o processo que está sendo automatizado.

**Arquétipo 4: Desenvolvedor de agents.** Escreve ou configura agents com ferramentas reais: acesso a API, execução de código, leitura de arquivo, busca na web. Usa frameworks ou API direta. Investimento: background técnico mais semanas de experimentação para primeiro agent robusto. Teto de valor alto. Exige gestão de contexto e memória desde o início.

**Arquétipo 5: Arquiteto de sistemas.** Projeta e opera sistemas com múltiplos agents coordenados, memória persistente e plano de controle. É o que este capítulo descreveu nos dois posts anteriores. Investimento: meses de desenvolvimento mais infraestrutura de monitoramento. Faz sentido quando há volume de trabalho complexo suficiente para justificar.

## Qual é o arquétipo relevante agora

Não existe progressão obrigatória do 1 ao 5. Alguém no arquétipo 2 que tem trabalho que é bem servido por prompts estruturados não precisa mover para o 3 por evolução natural.

O movimento que faz sentido é lateral quando o arquétipo atual encontra um limite real. O teto do arquétipo 1 é volume e personalização. Quando o processo de contextualizar cada sessão manualmente começa a custar mais do que a tarefa, é o sinal para o arquétipo 2. O teto do 2 é automação: quando vale mais deixar o processo rodar sozinho do que acionar manualmente.

A maioria das pessoas e organizações está no arquétipo 1 tentando decidir se vai para o 2 ou direto para o 4. O 3 é subestimado como ponto de entrada para quem tem processo bem definido mas não tem background de desenvolvimento.

## O que fazer esta semana

Uma ação concreta por arquétipo.

Se está no 1: escrever um prompt de sistema para a tarefa que mais usa LLM. Uma página com contexto, restrições e exemplos de bom output. Testar por uma semana antes de qualquer investimento adicional.

Se está no 2: mapear o processo que mais repete. Identificar qual parte dele tem critério claro de sucesso e custo de falha tolerável. Esse é o candidato para o primeiro fluxo no arquétipo 3.

Se está no 3: documentar o esquema de dados que entra e sai de cada passo do fluxo. Isso é o contrato que vai virar handoff quando o sistema crescer para o arquétipo 4.

Se está no 4: definir o critério de parada do agent que está em produção. Se ele não tem um, tem risco oculto.

Se está no 5: auditar o componente de memória. O que persiste, em qual formato, com que metadado, e como é recuperado. Se a resposta não é precisa, a memória está acumulando ruído.

## O que a série entregou

Dez posts, cinco capítulos, um objetivo: vocabulário e critério suficientes para tomar decisões informadas sobre IA agentic sem depender de quem vende a solução para explicar o que ela faz.

O mercado vai continuar produzindo novidades toda semana. O que muda com o vocabulário certo é a capacidade de filtrar o que é mudança de substância e o que é reembalagem do que já existia.

Quem chegou aqui com o Capítulo 1 e ficou no arquétipo 2 fez a escolha certa para o momento. Quem chegou no arquétipo 5 sabe o que construir a seguir. A série cumpriu o que prometeu no Post 0: não entregar o modelo mais novo, mas o filtro para avaliar o que chega.

---

🐧 _"A pergunta não é 'como usar IA'. É 'qual workflow, com qual custo de falha, para qual volume'."_
