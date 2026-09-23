**Problema:** Um desenvolvedor precisa criar uma classe chamada `MaiorEMenor` que percorre a lista de produtos de um carrinho de compras para apontar quais são os produtos de maior e menor valor monetário. Durante testes manuais informais, o algoritmo funcionou corretamente quando os produtos foram inseridos em ordem crescente de preço (ex: Jogo de pratos R$ 70,0, Liquidificador R$ 250,0, Geladeira R$ 450,0). No entanto, ao testar manualmente o mesmo carrinho com os produtos em ordem decrescente, o sistema falhou apresentando um erro de exceção `NullPointerException`.

**Conceito utilizado:** **Desenvolvimento Orientado a Testes (TDD)** e automação de testes de unidade usando o framework **JUnit** no Java.

**Solução:** A equipe decide adotar o TDD e a automação para expor e corrigir o bug usando o ciclo **Red-Green-Refactor**:

1. **Escrever o teste que falha (Fase RED)**: Em vez de testar manualmente inserindo dados no console, o desenvolvedor escreve uma classe de teste JUnit (`TestaMaiorEMenor`) configurada especificamente com o cenário que causa o erro (produtos adicionados em ordem decrescente). O teste usa o método de asserção `Assert.assertEquals()` para validar os nomes esperados para o maior ("Geladeira") e menor ("Jogo de pratos") produtos:
    
    ```
    import org.junit.Assert;
    import org.junit.Test;
    public class TestaMaiorEMenor {
        @Test
        public void ordemDecrescente() {
            CarrinhoDeCompras carrinho = new CarrinhoDeCompras();
            carrinho.adiciona(new Produto("Geladeira", 450.0));
            carrinho.adiciona(new Produto("Liquidificador", 250.0));
            carrinho.adiciona(new Produto("Jogo de pratos", 70.0));
    
            MaiorEMenor algoritmo = new MaiorEMenor();
            algoritmo.encontra(carrinho);
    
            Assert.assertEquals("Jogo de pratos", algoritmo.getMenor().getNome());
            Assert.assertEquals("Geladeira", algoritmo.getMaior().getNome());
        }
    }
    ```
    
    Ao rodar, o teste falha conforme previsto, revelando o erro na lógica de produção.
2. **Corrigir o código de produção (Fase GREEN)**: Ao analisar o código de produção original, o desenvolvedor encontra um defeito lógico: a presença de um comando `else if` que impede o segundo `if` (que testa o limite superior) de ser executado adequadamente sob certas sequências de dados:
    
    ```
    // Código ORIGINAL defeituoso:
    for (Produto produto : carrinho.getProdutos()) {
        if (menor == null || produto.getValor() < menor.getValor()) {
            menor = produto;
        } else if (maior == null || produto.getValor() > maior.getValor()) { // BUG: else if
            maior = produto;
        }
    }
    ```
    
    O desenvolvedor substitui o `else if` por um bloco `if` independente:
    
    ```
    // Código CORRIGIDO:
    for (Produto produto : carrinho.getProdutos()) {
        if (menor == null || produto.getValor() < menor.getValor()) {
            menor = produto;
        }
        if (maior == null || produto.getValor() > maior.getValor()) { // CORREÇÃO: if isolado
            maior = produto;
        }
    }
    ```
    
    O teste JUnit é reexecutado e agora passa com sucesso (**Green**).
3. **Refatoração (Fase REFACTOR)**: O desenvolvedor limpa a estrutura de código de testes e de produção, otimizando nomes de variáveis e a legibilidade do código, rodando o JUnit após cada microajuste para ter certeza de que nenhuma alteração quebrou o funcionamento estável.

**Resultado:** O algoritmo `MaiorEMenor` é corrigido permanentemente para todas as ordenações possíveis de produtos no carrinho, e o caso de teste fica automatizado na base do sistema, rodando instantaneamente a cada futura alteração sem precisar de digitação manual.

**Por que essa solução funciona:** A solução funciona porque a abordagem do TDD força o isolamento de cenários críticos e força o desenvolvedor a escrever testes de unidade independentes de sua própria intervenção mecânica. O JUnit realiza as verificações lógicas de forma automatizada e matemática (usando `assertEquals`), eliminando erros de análise visual que deixariam passar exceções em condições marginais ou limites.

**O que preciso aprender com esse exemplo:** Aprenda para provas que testar manualmente (usando `print` no console) é ineficiente e propenso a falhas graves, pois os humanos raramente simulam todas as condições de erro necessárias. O ciclo do TDD (**Vermelho-Verde-Refatorar**) produz códigos mais enxutos (escreve-se apenas o código estritamente necessário para o teste passar) e livres de bugs residuais de regressão técnica.