**Problema:** Remover pontos e traços de uma string de CPF digitada pelo usuário no formato padrão `"NNN.NNN.NNN-NN"`, salvando os valores numéricos limpos em um segundo vetor dinâmico.

**Conceito utilizado:** Iteração em strings, validação condicional lógica (`||`) e pulo de caracteres especiais com `continue`.

**Solução:**

```
#include <stdio.h>

int main() {
    char cpf1[36]; // Vetor para CPF formatado
    char cpf2[33] = ""; // Vetor para CPF limpo, inicializado vazio
    int i = 0, n = 0;
    
    printf("Digite seu CPF na forma NNN.NNN.NNN-NN: \n");
    scanf("%s", cpf1); // Lê a entrada formatada
    
    // O CPF formatado possui 14 caracteres úteis físicos mais o '\0'
    for (i = 0; i < 14; i++) {
        if (cpf1[i] == '.' || cpf1[i] == '-') {
            continue; // Salta pontos e traços sem copiá-los
        } else {
            cpf2[n] = cpf1[i]; // Copia apenas os caracteres numéricos
            n++; // Avança o índice de escrita do vetor de destino
        }
    }
    
    printf("\n\nCPF formatado = %s\n", cpf2);
    return 0;
}
```

**Resultado:** O programa remove a formatação e imprime na tela o CPF limpo com apenas 11 dígitos numéricos.

**Por que essa solução funciona:** O loop analisa individualmente cada célula do array de caracteres. Quando o caractere na posição de índice `i` é avaliado como ponto ou traço, a instrução `continue` interrompe a iteração atual, forçando o avanço automático do loop sem que o caractere indesejado seja copiado.

**O que preciso aprender com esse exemplo:** Strings em C são vetores de caracteres terminados automaticamente com o caractere nulo `\0`, o que exige que a dimensão do vetor seja declarada com pelo menos um caractere a mais do que o tamanho do texto útil a ser armazenado.