**Problema:** Uma empresa desenvolveu um protótipo inicial de telas (estático, não funcional) de um novo serviço de streaming de shows e eventos de música. Os designers precisam validar de forma rápida se a hierarquia das funções (ver favoritos, consultar agenda de shows, se inscrever em eventos) e se a organização das categorias de músicas e o menu principal estão corretos antes de gastar recursos desenvolvendo um protótipo navegável interativo complexo.

**Conceito utilizado:** Avaliação Heurística baseada em princípios ergonômicos aplicada a protótipos de baixa fidelidade.

**Solução:**

1. **Mapeamento de Funcionalidades:** Mapear os objetivos essenciais da interface (consultar agenda, selecionar artistas favoritos, fazer inscrição e visualizar detalhes).
2. **Execução Prática:** Devido ao protótipo ser estático, o Percurso Cognitivo estrito seria ineficaz. Os especialistas aplicam a **Avaliação Heurística**, confrontando o layout estático com as Heurísticas de Nielsen.
3. **Auditoria Heurística:** Analisar a clareza e o contraste dos ícones selecionados, a consistência de cores adotada nas seções de shows e o layout dos menus propostos.
4. **Emissão de Relatório de Severidade:** Categorizar os possíveis desvios ergonômicos identificados de acordo com sua gravidade (Alta, Média ou Baixa) para orientar os ajustes rápidos nas telas.

**Resultado:** Ajustes imediatos e sem custos na estrutura de informações do layout estático do aplicativo, garantindo que o posterior protótipo interativo e o código final sejam desenvolvidos sobre uma arquitetura validada.

**Por que essa solução funciona:** Correções feitas em layouts estáticos e rabiscos de papel exigem apenas alguns minutos do designer. Se as falhas de usabilidade na agenda e nos menus de shows fossem identificadas apenas após a implementação do código, o custo de alteração das linhas de programação seria significativamente maior.

**O que preciso aprender com esse exemplo:** Se o protótipo **não for funcional**, o método do Percurso Cognitivo puro torna-se de difícil aplicação, sendo a **Avaliação Heurística** a técnica mais indicada para inspecionar e organizar a arquitetura visual estática.