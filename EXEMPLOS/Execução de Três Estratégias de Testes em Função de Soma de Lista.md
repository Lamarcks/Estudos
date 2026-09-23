**Problema:**  
Demonstrar a aplicação combinada e as diferenças de desenvolvimento entre as três técnicas de testes em Python para validar o cálculo de soma acumulada de listas.

**Conceito utilizado:**  
Módulo `doctest`, framework `unittest`, assertivas preventivas (`assert`), testes em lote e comparação metodológica de frameworks.

**Solução:**

```
# --- Técnica 1: Validação Preventiva com Assertions ---
def sum_numbers_assert(numbers):
    assert sum() == 10
    assert sum([-1, 0, 1]) == 0
    assert sum([]) == 0
    return sum(numbers)

# --- Técnica 2: Exemplos de Documentação Automatizados com Doctest ---
def sum_numbers_doctest(numbers):
    """
    Soma os números em uma lista.
    Exemplos:
    >>> sum_numbers_doctest()
    10
    >>> sum_numbers_doctest([-1, 0, 1])
    0
    >>> sum_numbers_doctest([])
    0
    """
    return sum(numbers)

# --- Técnica 3: Classe de Testes Corporativa com Unittest ---
import unittest

def sum_numbers_unittest(numbers):
    return sum(numbers)

class TestSumNumbers(unittest.TestCase):
    def test_sum_numbers_positive(self):
        self.assertEqual(sum_numbers_unittest(), 10)
    def test_sum_numbers_mixed(self):
        self.assertEqual(sum_numbers_unittest([-1, 0, 1]), 0)
    def test_sum_numbers_empty(self):
        self.assertEqual(sum_numbers_unittest([]), 0)

# Execução e disparo dos testes integrados
if __name__ == '__main__':
    # Roda Doctests
    import doctest
    doctest.testmod()

    # Roda Unittest
    unittest.main(argv=['first-arg-is-ignored'], exit=False)
```

**Resultado:**  
Execução limpa com aprovação unificada de todas as validações estruturadas no código.

**Por que essa solução funciona:**  
Cada técnica atende a uma demanda do ecossistema:

- `assert` checa de forma pontual premissas em tempo de execução no código.
- `doctest` mantém a documentação viva e em sincronia com o código.
- `unittest` isola a complexidade de testes robustos em classes dedicadas.

**O que preciso aprender com esse exemplo:**  
A escolha da metodologia de testes ideal depende da complexidade do projeto e do rigor de cobertura exigido pelo sistema de software.