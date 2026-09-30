
**Problema:**  
Como criar o módulo de cadastro de pacientes (`cadastro.html`) e o painel de horários médicos (`horarios.html`) para a clínica online Saúde+, garantindo que a página seja intuitiva, validada e totalmente acessível a leitores de tela e motores de busca.

**Conceito utilizado:**  
Semântica HTML5, formulários estruturados com `<fieldset>`, `<legend>`, `<label>` e `<input>`, validação nativa de cliente (`required`, `pattern`), tabelas organizadas (`<table>`, `<thead>`, `<tbody>`, `scope="col"`) e acessibilidade via atributo `alt`.

**Solução:**

1. **Formulário de Cadastro (`cadastro.html`)**: Agrupe os campos por contexto com `<fieldset>` e `<legend>`. Associe cada `<label for="id">` com seu respectivo `<input id="id">`. Aplique atributos de validação nativos como `required` e `pattern` para validar e-mails sem necessidade imediata de scripts.
2. **Painel de Horários (`horarios.html`)**: Monte a tabela dividindo-a em `<thead>` e `<tbody>`. Adicione `scope="col"` aos cabeçalhos `<th>` e insira links `<a>` dentro das células `<td>` apontando para o perfil dos médicos.

```
<!-- Estrutura do Formulário Semântico e Validado -->
<form action="/cadastrar" method="post">
  <fieldset>
    <legend>Dados Pessoais</legend>

    <label for="nome">Nome Completo:</label>
    <input type="text" id="nome" name="nome" required minlength="3">

    <label for="email">E-mail:</label>
    <input type="email" id="email" name="email" required pattern="[a-z0-9._%+-]+@[a-z0-9.-]+\.[a-z]{2,4}$">
  </fieldset>
  <button type="submit">Cadastrar</button>
</form>

<!-- Estrutura da Tabela de Horários com Acessibilidade -->
<table>
  <caption>Horários de Atendimento Médico</caption>
  <thead>
    <tr>
      <th scope="col">Médico</th>
      <th scope="col">Horário</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><a href="perfil_dr_santos.html">Dr. João Santos</a></td>
      <td>08:00 - 12:00</td>
    </tr>
  </tbody>
</table>
```

**Resultado:**  
Uma interface web acessível, organizada e padronizada. O formulário impede o envio de dados incompletos ou em formatos incorretos no próprio navegador, e leitores de tela conseguem ler e associar corretamente cada rótulo ao seu respectivo campo e cabeçalho de tabela.

**Por que essa solução funciona:**  
A associação explícita entre `label` e `input` (via `for` e `id`) permite que assistentes de voz identifiquem a função de cada campo. Os atributos do HTML5 acionam os validadores embutidos dos navegadores modernos, enquanto os elementos estruturais de tabela (`thead`, `tbody`, `scope`) fornecem significado e hierarquia clara aos dados.

**O que preciso aprender com esse exemplo:**

- Formulários semânticos exigem a dupla `<label for="x">` e `<input id="x">`.
- Tabelas de dados devem utilizar `<thead>`, `<tbody>`, `<caption>` e o atributo `scope="col/row"` em tags `<th>` para garantir acessibilidade.
- A validação nativa HTML5 (`required`, `pattern`) economiza código e melhora a experiência do usuário.
