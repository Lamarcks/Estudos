**Problema:** Uma empresa que comercializa plantas ornamentais deseja expandir seus negócios via abertura de franquias, mas realiza quase todas as suas rotinas de forma estritamente manual, utilizando anotações em diversos cadernos físicos (com exceção apenas da máquina de cartão de crédito). Como analista detalhista, você precisa descobrir as rotinas internas, levantar, priorizar e especificar formalmente os requisitos funcionais e não funcionais do novo software de gestão.

**Conceito utilizado:**

- **Técnicas de Elicitação de Requisitos** (Visitas _in loco_, Observação Direta, Entrevistas Estruturadas e Coleta de Documentos).
- **Especificação de Requisitos** (padrão formal de identificação e descrição).
- **Classificação de Prioridades** (Essencial, Importante, Desejável).

**Solução:**

1. **Fase de Elicitação (Coleta)**: Realização de visitas programadas ao cultivo de plantas para observar rotinas implícitas (que os stakeholders esquecem de mencionar em entrevistas). Condução de entrevistas formais com os funcionários e recolhimento de cópias de anotações manuais, listas de estoque e formulários de pedidos.
2. **Identificação de Requisitos Funcionais (RF)**:
    - `[RF0001]` - Manter dados dos clientes (incluir, consultar, alterar, excluir): nome, endereço, CPF/CNPJ, e-mail, telefones.
    - `[RF0002]` - Gerar relatório das plantas disponíveis para venda.
    - `[RF0003]` - Permitir o cadastro de pedidos de encomendas de plantas e produtos da empresa.
    - `[RF0004]` - Autorizar a inclusão de pedidos de jardinagem/paisagismo com escolha de insumos.
    - `[RF0005]` - Manter cadastro de todos os produtos e plantas ornamentais.
    - `[RF0006]` - Manter informações botânicas das plantas.
    - `[RF0007]` - Emitir relatórios gerenciais sobre encomendas, estoque e status dos trabalhos paisagísticos em andamento.
    - `[RF0008]` - Manter cadastro de fornecedores.
    - `[RF0009]` - Emitir relatório de plantas adequadas por época do ano, solo e tipo de construção.
    - `[RF0010]` - Manter cadastro de usuários internos (Vendedor, Administrador, Supervisor).
3. **Identificação de Requisitos Não Funcionais (RNF)**:
    - `[RNF0001]` - Linguagem de programação: JAVA (Classificação: _Implementação_).
    - `[RNF0002]` - Tempo de carregamento dos relatórios: máximo 6 segundos (Classificação: _Desempenho_).
    - `[RNF0003]` - Visual do sistema: telas em cores claras pastel e ícones de grande tamanho (Classificação: _Usabilidade_).
    - `[RNF0004]` - Banco de dados: MySQL (Classificação: _Implementação_).
    - `[RNF0005]` - Permissão de relatórios gerenciais: restrito apenas a usuários Supervisores e Administradores (Classificação: _Segurança_).
4. **Especificação Estruturada**: Cada requisito foi padronizado em formulários próprios contendo: _Identificador, Nome, Módulo, Autor, Datas, Versão, Prioridade_ e _Descrição detalhada_. Exemplo para `[RF0008]`:
    - **Identificador**: `RF0008`
    - **Nome**: Manter o cadastro de fornecedores
    - **Prioridade**: Essencial (Sem o fornecedor, o software não realiza pedidos/encomendas)
    - **Descrição**: "Todo fornecedor deverá ser cadastrado antes de ser efetuada uma encomenda ou compra. Dados obrigatórios: Nome Fantasia, Razão Social, CNPJ, Inscrição Estadual, Endereço completo, E-mail".

**Resultado:** Uma tabela sólida e padronizada de requisitos especificados sem ambiguidades, validada junto ao dono da floricultura, pavimentando o caminho para a modelagem visual na UML.

**Por que essa solução funciona:** A palavra "**Manter**" unificou as ações de inclusão, consulta, alteração e exclusão lógicas, eliminando quatro requisitos redundantes e deixando o documento conciso. A observação direta permitiu mapear os serviços de jardinagem e paisagismo domiciliar, que a equipe operacional realizava rotineiramente, mas que não estavam documentados nos cadernos financeiros de vendas.

**O que preciso aprender com esse exemplo:** A elicitação de requisitos exige técnicas complementares de observação para coletar dados que o usuário executa mecanicamente e "esquece" de verbalizar nas entrevistas. Usar templates formais de requisitos evita falhas na comunicação com os desenvolvedores.