**Problema:** O sistema unificado de vendas de ingressos para a Copa do Mundo registrou a venda simultânea do último bilhete disponível para uma partida decisiva entre Brasil e EUA. O erro ocorreu simultaneamente em postos de venda no Rio de Janeiro e em Nova York, lesando os consumidores devido à duplicação da poltrona.

**Conceito utilizado:** **Condição de Disputa (Corrida)** em sistemas concorrentes distribuídos e violação de **Região Crítica**.

**Solução:** O erro foi provocado por falha no controle de concorrência no banco de dados centralizado do sistema. Os desenvolvedores devem garantir a **Exclusão Mútua**: Implementar um mecanismo de **Mutex (Semáforo Binário)** na rotina de escrita do banco de dados (Região Crítica). Quando o processo do vendedor do Rio de Janeiro acessar a poltrona para concluir a transação, ele executa a primitiva `DOWN` no semáforo, alterando o valor do recurso de `1` para `0`. O processo de Nova York, ao tentar realizar a mesma venda, executa `DOWN`, lê o semáforo em `0` e é bloqueado na fila de espera. Somente após o Rio concluir a transação e executar `UP`, o processo de Nova York é liberado e recebe o aviso de que o ingresso já foi vendido, impedindo a compra duplicada.

```
Processo Rio (Tenta Comprar) ──> DOWN (S=1 -> S=0) ──> Conclui Venda (Sucesso) ──> UP (S=1)
                                                       ^
Processo NY  (Tenta Comprar) ──> DOWN (S=0) ─── [BLOQUEADO NA FILA] ───> Recebe "Esgotado"
```

**Resultado:** O sistema passa a ser consistente e imune a atrasos de rede ou cliques simultâneos, impossibilitando que um recurso único seja atribuído a mais de um usuário.

**Por que essa solução funciona:** A exclusão mútua garante que apenas uma thread possa executar o trecho de código que altera o estoque (Região Crítica) por vez. Qualquer outra thread concorrente que tente acessar o recurso simultaneamente é colocada em fila de espera pelo S.O. até que a primeira termine a operação de forma atômica.

**O que preciso aprender com esse exemplo:** A falta de sincronismo e exclusão mútua em sistemas que compartilham variáveis (como saldo de estoque ou saldos de contas) gera condições de corrida imprevisíveis e catastróficas. Em sistemas concorrentes, o controle de acesso à região crítica é obrigatório.
