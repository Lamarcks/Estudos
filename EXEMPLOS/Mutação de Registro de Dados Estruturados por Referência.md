**Problema:** Modificar os campos internos de uma estrutura (tipo heterogêneo composto `Pessoa`) contendo nome e idade por meio de uma função externa estruturada de processamento.

**Conceito utilizado:** Ponteiro de estruturas e acesso a propriedades por meio do operador de seta (`->`).

**Solução:**

```
#include <stdio.h>
#include <string.h>

struct Pessoa {
    char nome[67];
    int idade;
};

// Função de processamento por referência
void modificarPessoa(struct Pessoa *p) {
    p->idade = 30; // Notação de seta para ponteiro de struct
}

int main() {
    struct Pessoa pessoa1;
    strcpy(pessoa1.nome, "João");
    pessoa1.idade = 25;
    
    modificarPessoa(&pessoa1); // Passagem de endereço de memória RAM do registro
    
    printf("Nome: %s\n", pessoa1.nome);
    printf("Idade: %d\n", pessoa1.idade); // Valida a alteração definitiva
    
    return 0;
}
```

**Resultado:** A idade do registro cadastral da pessoa é alterada com sucesso de 25 para 30 anos após a execução da função.

**Por que essa solução funciona:** O operador de seta `->` é o atalho correto da linguagem C utilizado para desreferenciar e acessar diretamente propriedades internas de variáveis heterogêneas (`structs`) que foram transmitidas como ponteiros de referência. Ele equivale à sintaxe mais detalhada `(*p).idade = 30;`.

**O que preciso aprender com esse exemplo:** Sempre que estiver acessando membros ou campos de dados contidos em um ponteiro que aponte para estruturas compostas do tipo `struct`, use o operador de seta `->` em vez da notação de ponto padrão