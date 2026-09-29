**Problema:** Um computador utilizado para reuniões corporativas foi emprestado a um funcionário em home office. No retorno, o proprietário percebeu que o carregamento do S.O. estava extremamente lento, o navegador e o chat de emergência não abriam, e a RAM registrava 90% de ocupação, com um programa desconhecido consumindo quase todos os recursos. Por que o swapping não impediu isso e como resolver?

**Conceito utilizado:** Infecção por malware e exaustão de memória física com saturação de _swapping_.

**Solução:**

1. Rodar um utilitário antivírus atualizado para remover o programa invasor.
2. Isolar o computador de redes corporativas durante a limpeza.
3. Monitorar o comportamento do processo suspeito.
4. Se mesmo após a remoção o consumo de RAM das ferramentas legítimas permanecer no limite, realizar um upgrade de memória física.

**Resultado:** A eliminação do vírus normaliza o uso de memória, cessando a necessidade de o sistema realizar swapping de forma ininterrupta, devolvendo a agilidade original da máquina.

**Por que essa solução funciona:** Programas maliciosos frequentemente operam em loops descontrolados ou realizam tarefas ocultas que consomem toda a RAM. Quando a RAM fica saturada a esse nível, o sistema dedica 100% do tempo de processamento apenas para realizar o swapping de páginas em disco, paralisando os aplicativos legítimos (fenômeno conhecido como _thrashing_).

**O que preciso aprender com esse exemplo:** O _swapping_ não é uma solução mágica para a falta permanente de memória ou para sistemas infectados. Se a CPU e o disco de armazenamento forem lentos ou se o sistema estiver sob ataque de software malicioso, o swapping se torna ineficaz.