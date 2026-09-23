**Problema:** Durante o uso cotidiano do computador, ao pesquisar algo em um navegador de internet e alternar rapidamente para um editor de textos a fim de colar o conteúdo encontrado, o computador apresenta um travamento momentâneo ou lentidão perceptível.

**Conceito utilizado:** Mapeamento e troca de processos da memória (**Swapping**).

**Solução:** O Sistema Operacional gerencia o esgotamento de memória real transferindo o processo que ficou em inatividade temporária (no caso, o editor de textos) para o disco rígido (área de swap). Quando o usuário clica de volta no editor, o S.O. realiza a troca física: retira o navegador da memória RAM, salva-o no disco e carrega o editor de textos do disco de volta para a RAM.

**Resultado:** Ambos os programas continuam funcionando sem que o sistema precise ser encerrado, mas o usuário experimenta um atraso momentâneo na troca devido à velocidade de transferência de dados do disco rígido.

**Por que essa solução funciona:** O disco rígido atua como uma extensão de emergência quando os programas abertos ultrapassam a capacidade física da memória RAM. A troca ocorre de forma invisível para o usuário, preservando o estado de execução de cada aplicação.

**O que preciso aprender com esse exemplo:** O _swapping_ é uma medida de contingência segura, mas tem alto custo de Entrada e Saída (E/S). Como o acesso ao disco rígido é ordens de grandeza mais lento que o acesso à RAM, o uso intenso de swapping degrada severamente o desempenho percebido.