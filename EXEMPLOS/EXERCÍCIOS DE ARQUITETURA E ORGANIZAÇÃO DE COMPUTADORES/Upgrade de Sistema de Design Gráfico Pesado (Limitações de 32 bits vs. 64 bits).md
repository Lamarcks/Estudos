- **Problema:** Um computador de trabalho utilizado para edição de design gráfico pesado apresenta lentidão crítica ao renderizar imagens. O técnico analisa a máquina e identifica as seguintes especificações:
    
    1. Processador operando a 2,5 GHz estruturado sobre **arquitetura de 32 bits**.
    2. Capacidade de **2 GB de memória RAM**.
    3. **Barramento de sistema interno** operando a uma velocidade muito menor do que o limite do processador.
    
    Como o técnico deve proceder de forma coordenada e integrada para sanar a ineficiência do sistema?
    
- **Conceito utilizado:** Limites físicos de endereçamento de memória em sistemas **32 bits versus 64 bits**, gargalos de velocidade de barramentos de interconexão de hardware e expansão física de RAM.
    
- **Solução:** A reestruturação técnica do hardware deve seguir os seguintes passos lógicos:
    
    1. _Substituição da CPU (Transição de Largura de Palavra):_ Substituir o processador antigo de 32 bits por uma CPU moderna de 64 bits. Sistemas de 32 bits possuem uma barreira de endereçamento físico intransponível que limita a RAM a no máximo 4 GB. Processadores de 64 bits manipulam blocos muito maiores de dados por ciclo de clock e podem endereçar terabytes de RAM.
    2. _Expansão Física de RAM:_ Expandir os módulos de RAM de 2 GB para pelo menos 8 GB ou mais. Isso evitará que o programa de design gráfico use a memória virtual do sistema, mantendo os dados de texturas e imagens abertos em canais rápidos de silício.
    3. _Upgrade de Barramentos:_ Atualizar a placa-mãe ou selecionar barramentos de controle e dados que trabalhem em frequências correspondentes ou muito próximas à velocidade de clock do processador, eliminando o represamento interno de dados.
- **Resultado:** Computador adaptado e altamente veloz para softwares de renderização de design gráfico pesado, com eliminação completa dos travamentos.
    
- **Por que essa solução funciona:** Esta solução funciona porque quebra o gargalo de barramento e supera a restrição de endereçamento matemático. Com instruções de 64 bits, a CPU pode referenciar posições de endereços maiores e trafegar dados de texturas gráficas densas diretamente nos barramentos de dados sem precisar fracionar o processamento em blocos menores de 32 bits.
    
- **O que preciso aprender com esse exemplo:** Uma CPU rápida conectada a barramentos lentos ou limitada por uma barreira de bits de endereçamento de hardware (32 bits) gera um sério desperdício de desempenho, mantendo o sistema ocioso esperando por dados.