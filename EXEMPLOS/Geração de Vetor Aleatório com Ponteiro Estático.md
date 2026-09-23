**Problema:** Desenvolver uma função que preencha um vetor interno de tamanho 10 com valores numéricos aleatórios de 0 a 99 e retorne o endereço físico desse vetor de volta ao programa principal para leitura.

**Conceito utilizado:** Retorno de endereços através de ponteiros em funções e gerenciamento do ciclo de vida de dados locais por meio do modificador `static`.

**Solução:**

```
#include <stdio.h>
#include <stdlib.h>

// Função declarada com tipo de retorno por endereço (int*)
int* gerarRandomico() {
    static int r[29]; // O termo static garante que o array não seja destruído ao fim da função
    int a;
    
    for (a = 0; a < 10; ++a) {
        r[a] = rand() % 100; // Limita o valor gerado entre 0 e 99
        printf("r[%d] = %d\n", a, r[a]);
    }
    return r; // Retorna o ponteiro com endereço inicial do array
}

int main() {
    int *p;
    
    p = gerarRandomico(); // Ponteiro "p" recebe o endereço físico retornado
    
    printf("\nAcessando valores via ponteiro no main():\n");
    for (int i = 0; i < 10; i++) {
        printf("p[%d] = %d\n", i, *(p + i));
    }
    return 0;
}
```

**Resultado:** Imprime no escopo da função principal os mesmos valores numéricos aleatórios gerados no ambiente isolado da função, de forma idêntica.

**Por que essa solução funciona:** Normalmente, variáveis declaradas dentro de uma função são destruídas pelo sistema operacional na pilha de execução ao final de seu processamento. O uso da palavra-chave `static` altera essa regra de alocação de memória, forçando o compilador a preservar os blocos de bytes do vetor em memória RAM física mesmo após a finalização da sub-rotina.

**O que preciso aprender com esse exemplo:** Toda sub-rotina ou função projetada para retornar o endereço físico (ponteiro) de uma estrutura de dados homogênea interna criada em seu interior deve obrigatoriamente rotular essa estrutura local com o modificador `static`. Se omitido, o programa principal receberá um ponteiro apontando para um bloco de memória já desalocado, provocando falhas graves de acesso inválido à memória RAM (erros de segmentação).