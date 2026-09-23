**Problema:** Dona Amélia, dona de uma pequena empresa de bolos e salgados sob encomenda, gerencia todo o negócio de forma manual. No último período de festas, ela não conseguiu dar conta do controle de pedidos e teve prejuízos. Ela deseja informatizar todo o fluxo (encomenda, entrega e cobrança), exige que as informações fiquem seguras na própria empresa de forma física, mas tem orçamento limitado para investimento.

**Conceito utilizado:** Análise de requisitos para dimensionamento e escolha de SGBD.

**Solução:** Como analista de sistemas, o processo de tomada de decisão é dividido em etapas:

1. **Descarte de soluções corporativas pesadas**: Descartar SGBDs de grande porte (como Oracle) devido ao alto custo de licenciamento e infraestrutura técnica desproporcional para o tamanho do negócio.
2. **Definição da Infraestrutura local**: Configurar uma máquina dedicada local para atuar como servidor físico na própria loja para cumprir a exigência de dados locais de Dona Amélia.
3. **Seleção de SGBD Custo-Benefício**: Adotar o **MySQL** como SGBD gratuito (código aberto), integrado a uma aplicação web local de controle de encomendas.
4. **Simplificação Física**: Desenvolver o sistema modular, iniciando pelo controle de pedidos e estoque de insumos críticos.

**Resultado:** Um sistema sob medida que resolve o gargalo de atendimento de Dona Amélia a um custo acessível de hardware local, livre de taxas caras de licenças de software.

**Por que essa solução funciona:** O MySQL oferece robustez transacional e suporte a acessos web simultâneos sem custo de licença, sendo perfeitamente adequado para aplicações de pequeno e médio porte.

**O que preciso aprender com esse exemplo:** Sistemas de banco de dados comerciais robustos (como Oracle ou SQL Server corporativo) são inadequados para pequenos comércios devido aos custos adicionais que inviabilizariam o projeto. O analista de sistemas deve alinhar a escolha tecnológica à capacidade financeira e operacional do cliente.