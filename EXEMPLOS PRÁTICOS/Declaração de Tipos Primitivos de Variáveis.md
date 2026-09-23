**Problema:** Apresentar de que forma diferentes tipos de dados (inteiros, reais e caracteres) são alocados e inicializados na memória de trabalho do computador.

**Conceito utilizado:** Tipos primitivos (`int`, `float`, `char`) e inicialização imediata.

**Solução:**

```
#include <stdio.h>

int main() {
    int num;
    int num2 = 5;       // Declarado e inicializado imediatamente
    float num3;
    char caractere;
    
    num = 10;           // Atribuição de valor inteiro
    num3 = 2.5;         // Atribuição de valor real
    caractere = 'a';    // Atribuição de caractere simples (aspas simples)
    
    return 0;
}
```

**Resultado:** O programa reserva 4 bytes para `num` e `num2`, 4 bytes para `num3` e 1 byte para `caractere`, preenchendo-os com os respectivos valores.

**Por que essa solução funciona:** A linguagem C exige tipagem estática e explícita. Caractere único deve ser delimitado obrigatoriamente com aspas simples (`'a'`).

**O que preciso aprender com esse exemplo:** Variáveis podem ser inicializadas no momento da sua declaração, o que evita que posições físicas de memória carreguem valores residuais indesejados ("lixo de memória")