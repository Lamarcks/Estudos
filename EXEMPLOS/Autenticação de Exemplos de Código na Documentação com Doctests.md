**Problema:**  
Validar de forma ágil se as funções matemáticas de um projeto estão calculando os resultados corretos, garantindo adicionalmente que os exemplos de código descritos nas docstrings de documentação do projeto nunca fiquem desatualizados ou incorretos.

**Conceito utilizado:**  
String de documentação estruturada, simulador de prompt virtual interativo (`>>>`) e automação de testes com o módulo nativo `doctest`.

**Solução:**

```
def square(x):
    """
    Retorna o quadrado de um número.

    Exemplos de uso (Doctest):
    >>> square(3)
    9
    >>> square(-2)
    4
    >>> square(0)
    0
    """
    return x * x

import doctest
# Invoca o motor que lê e valida os testes integrados na documentação
doctest.testmod()
```

**Resultado:**  
O comando de teste analisa os exemplos e retorna `TestResults(failed=0, attempted=3)` indicando aprovação total.

**Por que essa solução funciona:**  
O módulo `doctest` escaneia todas as strings de documentação do arquivo procurando por marcações do console Python (`>>>`). Ele executa a expressão contida no comentário, captura o resultado gerado pelo interpretador e valida se o valor de saída gerado coincide exatamente com o valor documentado na linha logo abaixo.

**O que preciso aprender com esse exemplo:**  
O doctest garante de forma automatizada que a documentação técnica de suporte do sistema continue funcionando perfeitamente em conformidade com as rotinas reais de execução.