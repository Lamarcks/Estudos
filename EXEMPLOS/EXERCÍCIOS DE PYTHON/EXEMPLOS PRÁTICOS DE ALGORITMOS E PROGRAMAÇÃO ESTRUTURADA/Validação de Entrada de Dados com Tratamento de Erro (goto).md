**Problema:** Solicitar a digitação de um número positivo. Se o usuário cometer um erro e digitar um número menor ou igual a zero, o programa deve saltar de forma direta e incondicional para uma rotina isolada de tratamento de erro.

**Conceito utilizado:** Desvios incondicionais não estruturados de fluxo por meio de identificadores de rótulo (`goto`).

**Solução:**

```
#include <stdio.h>

int main() {
    int numero;
    
    printf("Insira um número positivo: ");
    scanf("%d", &numero);
    
    if (numero <= 0) {
        goto erro; // Salta diretamente para a etiqueta 'erro'
    }
    
    printf("Número válido: %d\n", numero);
    return 0;
    
erro: // Rótulo estruturado para manipulação de erros e encerramento
    printf("Erro: Número inválido.\n");
    return 0;
}
```

**Resultado:** O programa ignora o fluxo normal de confirmação se o número for inválido, pulando diretamente para a mensagem de erro.

**Por que essa solução funciona:** A instrução `goto erro` desloca de forma incondicional o ponteiro de execução do compilador para a linha identificada pelo rótulo `erro:`.

**O que preciso aprender com esse exemplo:** O comando `goto` possui escopo estritamente local e não pode ser utilizado para desviar a execução do fluxo para fora da função corrente. Seu uso indiscriminado cria códigos confusos ("código espaguete") e propensos a falhas de manutenção.