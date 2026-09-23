**Problema:** Refinar as regras da seleção de estagiários: candidatos que preencherem o critério acadêmico de pelo menos 70% de nota, mas não tiverem o tempo mínimo de curso (semestre < 3), não podem simplesmente ser reprovados; eles devem ser encaminhados para um "banco de currículos" para oportunidades futuras.

**Conceito utilizado:** Estruturas de desvio de fluxo condicionais encadeadas (`if...else if...else`).

**Solução:**

```
// 1. Verifica se atende a todos os requisitos
if ((nota >= notaMinAprov) && (semCursado >= qtdeSemestres)) {
    return "Aprovado";
// 2. Se falhar o de cima, mas tiver a nota mínima, entra para o banco de dados
} else if (nota >= notaMinAprov) {
    return "Você foi incluído no banco de currículos";
// 3. Casos em que não atinge nem a nota
} else {
    return "Reprovado";
}
```

**Resultado:** Um estudante com rendimento de 80% (nota >= 0.7) que esteja apenas no 2º semestre recebe como saída a mensagem: "Você foi incluído no banco de currículos".

**Por que essa solução funciona:** O interpretador lê os blocos ordenadamente de cima para baixo. Se a primeira validação restritiva cumulativa (`&&`) falhar, a execução testa a segunda condição do `else if`. Se esta for verdadeira, ela executa seu respectivo código e encerra a checagem, ignorando o `else` final de reprovação.

**O que preciso aprender com esse exemplo:** Como estruturar decisões hierárquicas e fluxos de exclusão ordenada utilizando desvios compostos de `else if`.