**Problema:** Uma rede de lojas de varejo decide substituir seu antigo sistema legado por uma plataforma de comércio eletrônico altamente robusta e escalável. Durante o desenvolvimento, o mercado dinâmico força frequentes solicitações de mudanças nos requisitos originais por parte dos designers, diretores e clientes. Sem controle estruturado, essas alterações descontroladas estão gerando atrasos graves e estouros de orçamento.

**Conceito utilizado:**

- **Processo de Gerenciamento de Mudanças**.
- **Rastreabilidade de Requisitos** (_Backward_ ou "para trás", _Forward_ ou "para frente", _Horizontal_).
- **Matriz de Rastreabilidade de Requisitos**.

**Solução:**

1. **Processo Formal de Alterações**:
    - _Etapa 1 - Análise do Problema_: Recebimento de uma solicitação de mudança específica no fluxo do carrinho de compras.
    - _Etapa 2 - Estimativa de Custo e Impacto_: Uso das conexões de rastreabilidade para descobrir quais diagramas de casos de uso, códigos-fonte e casos de testes seriam afetados pelo desvio e estimar o impacto financeiro.
    - _Etapa 3 - Implementação_: Atualização imediata do documento de requisitos original para refletir o novo comportamento do software antes de alterar o código.
2. **Uso da Matriz de Rastreabilidade**: Para gerenciar o requisito funcional de cobrança do carrinho (`RF20`, solicitado originalmente pelo _Gerente de Vendas_), o time estruturou uma matriz bidimensional:
    - **Rastreabilidade para Trás (Backward - Origem)**: Vinculou o `RF20` diretamente ao _Gerente de Vendas_ (solicitante) e ao _Objetivo Estratégico_ `OE3` da empresa.
    - **Rastreabilidade para Frente (Forward - Impactos técnicos)**: Mapeou que o `RF20` se desdobra diretamente no Caso de Uso `UC12` (UML), no Caso de Teste `CT20.1` e no Módulo de Código de programação `M1`.
    - **Rastreabilidade Horizontal (Interdependências lógicas)**: Mapeou a conexão funcional direta entre o `RF20` e o Requisito Não Funcional de segurança `RNF3`.

```
Representação Lógica da Rastreabilidade do Requisito RF20:

[OE3: Objetivo Estratégico] <--- (Backward) --- [RF20: Cobrança] --- (Forward) ---> [UC12: Caso de Uso UML]
[Gerente de Vendas: Origem]                         |                              [M1: Módulo de Código]
                                                    | (Horizontal)                 [CT20.1: Caso de Teste]
                                                    v
                                            [RNF3: Segurança]
```

**Resultado:** A loja conseguiu implementar as atualizações comerciais no e-commerce sem gerar bugs residuais ou atrasar o cronograma de homologação. Sempre que um requisito mudava, a matriz indicava precisamente quais trechos de código e testes deveriam ser modificados.

**Por que essa solução funciona:** A rastreabilidade elimina o risco de "requisitos órfãos" (funcionalidades adicionadas sem link com o negócio) ou de alterar uma linha de código e quebrar acidentalmente módulos legados cruciais e testes automatizados.

**O que preciso aprender com esse exemplo:** A **rastreabilidade** garante que a documentação técnica permaneça viva e consistente com o código-fonte ao longo da evolução do software, fornecendo dados matemáticos para análises precisas de impacto financeiro de mudanças.