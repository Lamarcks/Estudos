**Problema:**  
Executar rotinas de cálculos matemáticos avançados (raiz quadrada, logaritmo binário e cosseno) demonstrando as melhores práticas de carregamento e o consumo de recursos na memória.

**Conceito utilizado:**  
Modularização de código e três sintaxes distintas de importação de módulos com o recurso nativo `math`.

**Solução:**

```
# Método 1: Importa o módulo completo na memória
import math
v1 = math.sqrt(25)
print(f"Método 1 (Raiz): {v1}")

# Método 2: Importa o módulo atribuindo um alias/apelido
import math as m
v2 = m.log2(1024)
print(f"Método 2 (Log2): {v2}")

# Método 3: Importa elementos específicos diretamente
from math import sqrt, log2, cos
v3 = cos(45)
print(f"Método 3 (Cosseno): {v3}")
```

**Resultado:**  
Computação precisa dos valores matemáticos por meio de chamadas corretas e organizadas no código.

**Por que essa solução funciona:**  
O interpretador Python mapeia e isola escopos dos arquivos `.py`. O uso do `as` cria apelidos para facilitar o manuseio sintático, e o comando `from` economiza chamadas de prefixos ao importar as variáveis diretamente ao escopo global.

**O que preciso aprender com esse exemplo:**  
Saber dosar a forma de importação ajuda a manter a legibilidade, evita poluição do escopo de nomes global e racionaliza a memória.