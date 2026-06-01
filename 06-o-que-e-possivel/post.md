# O que é possível (e quando não vale): o critério de delegação que separa projeto útil de POC caro

![Cover](https://raw.githubusercontent.com/DScardini91/medium-ai-series/main/06-o-que-e-possivel/images/cover.png)

---

Quase tudo que alguém pode fazer manualmente, um agent pode tentar fazer. Isso não é razão suficiente para automatizar. O ponto de partida errado produz projetos que funcionam em demo e quebram em produção.

## O viés do possível

Quando uma nova tecnologia fica acessível, a primeira pergunta que aparece é "o que ela consegue fazer?". É a pergunta certa para exploração inicial. É a pergunta errada para decisão de investimento.

Projetos de IA agentic que falham seguem um padrão. Alguém demonstra que o agent consegue fazer X em condições controladas. A decisão de implementar vem da demonstração, não de uma análise do que acontece quando X falha em produção. Meses depois, o sistema está em manutenção constante por causa de casos que o demo nunca mostrou.

O viés do possível é real: se funciona uma vez, parece que vai funcionar sempre. Não funciona assim.

## Onde agents fazem sentido

Três condições juntas indicam boa candidatura para delegação.

Primeiro: tarefa bem definida com critério claro de sucesso. O agent precisa saber quando terminou e se terminou bem. Tarefas abertas com critério subjetivo de qualidade produzem loops sem parada ou aprovação de resultado ruim.

Segundo: custo de falha tolerável e reversível. Se o agent tomar a decisão errada, o que acontece? Uma resposta de email pode ser relida antes de enviar. Uma transação financeira não. O nível de autonomia adequado depende diretamente do custo de erro.

Terceiro: volume que justifica o setup. Automatizar uma tarefa que acontece duas vezes por semana com agent que precisa de manutenção constante tem ROI negativo. O ponto de equilíbrio muda por caso, mas a pergunta tem que ser feita antes, não depois.

Onde esses três se encontram: triagem e roteamento de informação, geração de primeiro rascunho em formato estruturado, extração de dado de documento com esquema fixo, monitoramento e alerta com critério explícito, pesquisa com entregável padronizado.

## Onde agents não fazem sentido

Custo de falha alto sem supervisão humana no loop. Qualquer decisão que afeta contrato, relacionamento de cliente, conformidade regulatória ou dado sensível precisa de humano validando, pelo menos nos casos de fronteira. Agent pode preparar, não decidir sozinho.

Tarefa com ambiguidade estrutural. Se dois especialistas humanos discordariam sobre o resultado correto, um agent não vai resolver. Vai polarizar para a resposta estatisticamente mais provável, que pode ser sistematicamente errada para o contexto específico.

Processo que muda frequentemente. Agent com prompt complexo que reflete um processo que muda a cada trimestre vai ficar desatualizado. O custo de manutenção vai superar o ganho de automação.

## O critério de decisão

Uma pergunta direta antes de aprovar qualquer projeto de automação agentic: se o agent tomar a pior decisão possível nessa tarefa, o que acontece?

Se a resposta é "nada irreversível e o humano pode corrigir rápido", a delegação faz sentido com supervisão leve. Se a resposta é "dano significativo antes de alguém perceber", o nível de autonomia precisa ser menor ou o projeto precisa de arquitetura diferente.

Possível é uma barra baixa. O critério é: possível, com custo de falha tolerável, em volume que justifica, com definição clara de sucesso. Quando todas as quatro condições estão presentes, vale avançar. Quando falta qualquer uma, o risco está escondido no entusiasmo do demo.

No próximo post, como montar sistemas que sobrevivem quando as quatro condições estão presentes: o que os que ficam em produção têm em comum.

---

🐧 _"Possível é a barra errada. Custo de falha é a barra certa."_
