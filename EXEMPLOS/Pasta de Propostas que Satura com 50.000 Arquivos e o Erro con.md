**Problema:** O diretor de pré-vendas de uma grande empresa notou que a pasta destinada a guardar as propostas de vendas mensais não aceitava armazenar mais de 50.000 arquivos. Além disso, relatou que o Windows bloqueou a tentativa de salvar um arquivo de texto de conexões utilizando o nome **"con"**. Quem gerencia esse limite e por que o nome "con" foi rejeitado?

**Conceito utilizado:** Limitações físicas e lógicas de **Sistemas de Arquivos** e **Palavras Reservadas** de S.O..

**Solução:**

1. **Limite de Arquivos**: O limite não é gerido diretamente de forma genérica pelo S.O., mas sim pelo tipo de Sistema de Arquivos adotado na formatação da partição do disco rígido. Formatar a unidade de disco usando os sistemas de arquivos modernos **NTFS** (no Windows) ou **EXT4** (no Linux), que suportam mais de **4 bilhões de arquivos** em uma única pasta, resolvendo a saturação.
2. **O Erro "con"**: Alterar o nome do arquivo para algo descritivo, como "conexao_vendas.txt".

**Resultado:** O sistema aceita os novos lotes de propostas na pasta sem travamentos e valida o salvamento do arquivo renomeado.

**Por que essa solução funciona:** Os sistemas de arquivos mais antigos (como FAT16) tinham limites lógicos rígidos para o número total de entradas de diretórios por pasta. Sistemas modernos utilizam índices estruturados em árvore que suportam bilhões de registros. Quanto ao nome "con", trata-se de uma palavra reservada herdada do MS-DOS que designa o comando interno de dispositivo do console de entrada (teclado). O sistema bloqueia a criação de arquivos comuns com esses nomes para evitar conflitos de instruções no kernel.

**O que preciso aprender com esse exemplo:** A capacidade de armazenamento e quantidade máxima de diretórios dependem diretamente do sistema de arquivos utilizado. S.O.s mantêm uma lista de nomes exclusivos proibidos para os usuários comuns a fim de manter a estabilidade do sistema.