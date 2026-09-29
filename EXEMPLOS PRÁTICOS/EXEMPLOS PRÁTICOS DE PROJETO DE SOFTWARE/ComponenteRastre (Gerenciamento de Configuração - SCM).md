**Problema:** No desenvolvimento do software ComponenteRastre, dezenas de programadores precisam alterar os mesmos arquivos de código de forma concorrente para atualizar a arquitetura do sistema. Sem controle formal de mudanças, as atualizações de um programador apagam as correções de outro, gerando inconsistências, falhas e impedindo que o Product Owner aprove o software utilizável.

**Conceito utilizado:** Elementos do Software Configuration Management (SCM) e Baseline.

**Solução:** A ComponenteRastre estabeleceu as diretrizes fundamentais do SCM:

1. **Elementos de Componente:** Instalaram um sistema centralizado de repositório (ex: Git) para gerenciar o histórico de acesso de cada item de configuração de software (SCI).
2. **Mecanismos de Controle Simultâneo:** Uso de branches e diretrizes de merge de código. Os programadores trabalham em áreas isoladas do repositório, mesclando suas evoluções e resolvendo conflitos antes da publicação.
3. **Criação de Baselines (Linha de Referência):** Quando uma versão do código é formalmente testada, avaliada e aprovada pela revisão técnica, ela se torna inalterável sem procedimentos formais de alteração.
4. **Histórico e Log:** Registro cronológico de todas as modificações detalhando os motivos de cada alteração de código.

**Resultado:** Ambiente de engenharia controlado, seguro e livre de alterações acidentais.

**Por que essa solução funciona:** O SCM implementa regras rígidas de integração onde o código é mantido em estado consistente e as alterações são monitoradas continuamente.

**O que preciso aprender com esse exemplo:** A **baseline** serve como base de referência estável. Novos desenvolvimentos continuam a partir dela, garantindo controle total dos artefatos de software.