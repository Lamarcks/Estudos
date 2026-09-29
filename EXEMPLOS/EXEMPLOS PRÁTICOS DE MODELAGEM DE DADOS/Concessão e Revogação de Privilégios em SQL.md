**Problema:** O administrador do banco de dados (DBA) precisa dar permissão para o usuário `user001` incluir e excluir dados da tabela `Clientes`, mas restringir consultas a salários ou alterações estruturais. Posteriormente, a permissão de exclusão precisa ser removida por razões de segurança.

**Conceito utilizado:** Controle de acesso em nível de relação/tabela e comandos SQL DDL/DML (especificamente `GRANT` e `REVOKE`).

**Solução:** O DBA deve executar os seguintes comandos lógicos no interpretador SQL:

1. Conceder permissão de escrita e exclusão na tabela:

```
GRANT INSERT, DELETE ON CLIENTES TO user001;
```

2. Revogar o privilégio de exclusão do mesmo usuário:

```
REVOKE DELETE ON CLIENTES FROM user001;
```

**Resultado:** O usuário `user001` consegue inserir registros na tabela `Clientes`, mas, se tentar realizar um comando `DELETE`, o servidor SQL retornará uma mensagem de erro de permissão.

**Por que essa solução funciona:** O SGBD possui um catálogo ativo (metadados) que armazena os privilégios de acesso associados a cada conta. Antes de executar qualquer instrução DML recebida, o interpretador do SGBD valida as permissões registradas para aquele usuário.

**O que preciso aprender com esse exemplo:** O gerenciamento de acessos deve obedecer ao princípio de privilégio mínimo. Para provas, lembre-se de que os comandos `GRANT` e `REVOKE` exigem a indicação clara do privilégio (`SELECT`, `INSERT`, `UPDATE`, `DELETE`), da tabela (`ON tabela`) e do usuário (`TO/FROM usuario`).