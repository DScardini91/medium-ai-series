# Como montar sistemas que sobrevivem ao mundo real: memória, handoffs e o supervisor que sabe parar

![Cover](https://raw.githubusercontent.com/DScardini91/medium-ai-series/main/07-sistemas-que-sobrevivem/images/cover.png)

---

A maioria dos sistemas agentic que vejo em produção não morreu de uma falha catastrófica. Morreu de degradação silenciosa. Funcionou bem no primeiro mês, ficou instável no segundo, e foi desligado no terceiro por custo de manutenção que não estava no plano.

Os que sobrevivem têm três componentes em comum. Os que quebram ignoraram pelo menos um.

## O que mata sistemas agentic

Antes das soluções, o diagnóstico. Os três padrões de falha mais comuns que encontro.

Primeiro: contexto sem gestão. O sistema funciona em tarefas curtas. Em tarefas longas ou em uso contínuo, perde coerência porque ninguém projetou como o contexto cresce, é comprimido e recuperado. O agent começa a contradizer decisões anteriores porque elas saíram da janela.

Segundo: handoffs implícitos. Um agent passa resultado para o próximo sem formato definido. O segundo agent interpreta o que recebeu de forma diferente do que o primeiro pretendia. O erro não aparece como falha técnica. Aparece como resposta que parece certa mas está errada nos detalhes que importam.

Terceiro: ausência de critério de parada. O agent executa passos em loop porque não tem definição clara de quando a tarefa está concluída. Ou para cedo demais porque o critério padrão não distingue "objetivo atingido" de "próximo passo indisponível".

## Memória projetada

Memória não é um feature que se adiciona depois. É uma decisão de arquitetura que precisa estar no design desde o início.

O mínimo para um sistema que vai além de tarefas de uma sessão: scratchpad de progresso em formato estruturado, acessível entre sessões. O agent grava onde parou. A próxima instância lê antes de começar. Sem isso, cada sessão começa do zero independente do trabalho acumulado.

O próximo nível: recuperação seletiva. Em vez de injetar todo o histórico na janela, o sistema mantém índice e recupera o que é relevante para a tarefa corrente. Busca por similaridade semântica, filtro por recência, priorização por tipo de conteúdo. O que entra na janela é curado, não despejado.

Memória bem projetada tem dois critérios: o agent encontra o que precisa quando precisa, e o sistema não acumula ruído que degrada a qualidade das recuperações com o tempo.

## Handoffs que não quebram

Cada handoff entre agents é um ponto de falha potencial. A mitigação não é eliminar handoffs: é torná-los explícitos.

Três propriedades de um handoff robusto.

Formato estruturado: o output de um agent é um contrato com o próximo. Se o formato mudar, o próximo agent falha de forma previsível em vez de silenciosa. JSON com schema definido, markdown com seções fixas, qualquer formato com estrutura verificável.

Contexto suficiente: o agent que recebe o handoff precisa ter o que precisa para continuar sem reler todo o histórico. O que foi feito, por que, o que ficou em aberto. Mais não é melhor: contexto excessivo entope a janela e dilui o que importa.

Verificação de recebimento: o sistema confirma que o handoff foi processado antes de prosseguir. Handoff silencioso que falha sem sinalizar produz trabalho subsequente sobre base incorreta.

Nos projetos que funcionaram por mais de seis meses, o contrato de handoff estava documentado antes de o código estar escrito.

## O supervisor que sabe parar

Todo sistema com autonomia real precisa de um componente que monitora o estado geral e decide quando parar.

Parar pode significar: tarefa concluída com sucesso, tarefa concluída com falha documentada, tarefa em estado de bloqueio que exige intervenção humana, ou custo acumulado que excede o orçamento previsto.

Um supervisor fraco aprova tudo o que o agent entrega. Um supervisor ausente deixa o sistema em loop quando algo dá errado. Um supervisor bem projetado tem critérios explícitos para cada condição de parada e escala para o humano apenas nos casos que realmente exigem julgamento.

O ponto que mais vejo negligenciado: o supervisor precisa ter visão do estado do sistema, não apenas da última saída do agent. Um agent que produziu boa saída individual mas que está no turno 47 de uma tarefa que deveria ter terminado no turno 10 está em loop. Só o supervisor com visão de sequência consegue detectar isso.

## O que não precisa ser perfeito de início

Nenhum sistema começa com todos os três componentes funcionando bem. O caminho prático: começar com handoffs explícitos (o mais rápido de implementar e com maior retorno imediato), adicionar memória de progresso mínima antes de escalar para uso contínuo, e construir critérios de parada antes de dar autonomia real ao sistema.

A sequência importa. Memória sofisticada em sistema com handoffs quebrados não resolve. Supervisor robusto em sistema sem memória vai parar as coisas certas pelos motivos errados.

---

🐧 _"Sistema que sobrevive não é o mais complexo. É o que falha de forma previsível."_
