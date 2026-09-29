**Problema:** Um sistema de recursos humanos para triagem de estagiários estava aprovando indevidamente estudantes não qualificados. Regras de aprovação exigidas pela empresa: o candidato deve estar cursando no mínimo o 3º semestre **E** apresentar rendimento acadêmico de no mínimo 70% na prova online. Casos de falha observados: um aluno no 5º semestre com 50% de rendimento foi aprovado; outro do 2º semestre com 80% de rendimento também passou.

**Conceito utilizado:** Operador de igualdade lógica restritiva de conjunção (`&&` - E) em substituição à conjunção alternativa (`||` - OU) e operadores de comparação relacionais.

**Solução:** _Código incorreto original:_

```
// O uso do operador || (OU) permitia que cumprir apenas uma das regras garantisse aprovação
if ((nota >= notaMinAprov) || (semCursado >= qtdeSemestres)) {
    return "Aprovado";
}
```

_Código corrigido:_

```
function primeiraEtapa(acertoProva, semCursado) {
    const NumQuestoes = 20;
    const notaMinAprov = 0.7; // Representa 70% de corte
    const qtdeSemestres = 3;

    let nota = acertoProva / NumQuestoes; // Calcula a nota percentual

    // Correção com o operador && (E)
    if ((nota >= notaMinAprov) && (semCursado >= qtdeSemestres)) {
        return "Aprovado";
    } else {
        return "Reprovado";
    }
}
```

**Resultado:** O sistema reprova corretamente os dois casos relatados (14 acertos e 2 semestres = reprovado; 10 acertos e 5 semestres = reprovado). Apenas quem acumula nota >= 70% **E** semestre >= 3 é aprovado.

**Por que essa solução funciona:** Ao alterar o operador lógico para `&&`, a estrutura condicional `if` exige de maneira cumulativa que ambas as expressões lógicas internas retornem `true` simultaneamente para que o código de aprovação seja executado.

**O que preciso aprender com esse exemplo:** Como a escolha inadequada de operadores lógicos pode criar falhas graves em regras de negócios de sistemas de software e a diferença crucial de comportamento de fluxo entre `&&` e `||`.