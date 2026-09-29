**Problema:** A biblioteca de uma cidade pequena gerencia o empréstimo de seus livros usando um sistema legado obsoleto construído há décadas. O sistema roda sobre um modelo de banco de dados hierárquico, dificultando sua manutenção e evolução tecnológica. A equipe precisa modernizar o sistema migrando os dados para um SGBD relacional moderno sem paralisar o atendimento ao público.

**Conceito utilizado:** Engenharia Reversa (Bottom-Up), Normalização de Arquivos, Wrappers de Interoperabilidade e Processo ETL.

**Solução (Fluxo Passo a Passo):**

1. **Representação Inicial**: Coletar descrições de arquivos físicos e mapear a estrutura hierárquica legada na forma de tabelas lógicas não normalizadas.
2. **Processo de Normalização**: Aplicar as formas normais (1FN, 2FN, 3FN) para converter o emaranhado hierárquico em um esquema lógico relacional consistente de livros, autores, empréstimos, membros e histórico.
3. **Criação de Wrappers**: Desenvolver camadas de _software wrapper_ para permitir que as operações legadas do dia a dia continuem acessando o banco antigo enquanto o novo sistema relacional é testado.
4. **ETL (Extração, Transformação e Carga)**: Migrar todos os dados históricos limpos e normalizados do sistema antigo para o novo SGBD relacional.
5. **Transição Incremental**: Treinar os funcionários no novo sistema e desativar o backend legado gradualmente.

**Resultado:** Modernização completa do sistema da biblioteca. O novo banco relacional reduziu drasticamente os custos de manutenção e permitiu a emissão de relatórios rápidos de empréstimo.

**Por que essa solução funciona:** A engenharia reversa permite desestruturar o formato físico legado e focar na lógica de dados pura por meio de normalização, garantindo que o novo banco de dados nasça limpo e coerente.

**O que preciso aprender com esse exemplo:** Não tente substituir sistemas legados de forma abrupta (Abordagem Big-Bang), pois o risco de perda de dados e indisponibilidade operacional é catastrófico. Use abordagens incrementais suportadas por wrappers lógicos.