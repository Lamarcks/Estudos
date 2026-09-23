**Problema:** Mapear a arquitetura física de um **sistema de controle de cinema** grande e complexo, mostrando as dependências entre os módulos de venda de ingressos físicos/digitais, o armazenamento permanente de dados e o módulo de manutenção de registros (salas, filmes, sessões e atores).

**Conceito utilizado:** **Diagrama de Componentes UML** com interfaces fornecidas (notação _lollipop_) e requeridas (notação _soquete_).

**Solução:** Mapeia-se o sistema utilizando quatro blocos de componentes principais:

1. `Interface de Venda de Ingressos`: Componente que encapsula o software de tela de PDV e o hardware de impressão física dos ingressos. Possui uma interface **requerida** (soquete).
2. `Módulo de Venda de Ingressos`: Responsável pelas regras de transação e geração de bilhetes. Expõe uma interface **fornecida** (pirulito) conectada à interface requerida do componente de interface de venda, e possui uma interface requerida para se comunicar com o banco de dados.
3. `SGBD`: Banco de dados físico centralizado. Expõe interfaces fornecidas para consulta e persistência de dados das vendas e dos cadastros operacionais.
4. `Módulo de Manutenção do Sitema`: Responsável pelas telas de cadastro e edição de dados operacionais (salas, filmes, sessões). Possui interface requerida conectada ao `SGBD`.

**Resultado:** O diagrama mapeia as conexões físicas e lógicas exatas, esclarecendo quais módulos são autossuficientes e dependem de outros para rodar.

**Por que essa solução funciona:** A conexão via **lollipop-soquete** representa o acoplamento fraco. O `Módulo de Venda` não acessa o banco de dados de qualquer jeito; ele o faz estritamente através das regras de contrato definidas pela interface pública do componente `SGBD`.

**O que preciso aprender com esse exemplo:** No diagrama de componentes, o relacionamento de interfaces é visualmente representado pelo encaixe perfeito entre uma **esfera (interface fornecida - o serviço que eu disponibilizo)** e um **semicírculo (interface requerida - o serviço que eu preciso para funcionar)**.