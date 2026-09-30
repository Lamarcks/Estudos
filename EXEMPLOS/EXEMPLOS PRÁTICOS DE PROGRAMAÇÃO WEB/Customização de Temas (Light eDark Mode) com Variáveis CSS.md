
**Problema:**  
Permitir a troca de esquema de cores de um site (Modo Claro vs. Modo Escuro) sem precisar duplicar arquivos de estilo ou reescrever dezenas de regras CSS individuais.

**Conceito utilizado:**  
Variáveis CSS (Custom Properties) declaradas no pseudo-seletor `:root` e sobrescritas via classe de escopo.

**Solução:**

1. Declare a paleta de cores padrão no seletor global `:root` usando a sintaxe `--nome-da-variavel`.
2. Aplique essas variáveis nos elementos da página com a função `var(--nome-da-variavel)`.
3. Redefina os valores das variáveis sob uma classe específica (ex: `.dark-mode`).

```
/* Definição de Variáveis Globais no Tema Padrão (Claro) */
:root {
    --cor-primaria: #007bff;
    --cor-texto: #343a40;
    --cor-fundo: #f8f9fa;
    --espacamento-padrao: 1rem;
}

body {
    background-color: var(--cor-fundo);
    color: var(--cor-texto);
    font-family: Arial, sans-serif;
}

.botao {
    background-color: var(--cor-primaria);
    color: white;
    padding: var(--espacamento-padrao);
    border: none;
}

/* Redefinição das Variáveis para o Tema Escuro */
body.dark-mode {
    --cor-primaria: #6610f2;
    --cor-texto: #f8f9fa;
    --cor-fundo: #212529;
}
```

```
<!-- Aplicação da classe dark-mode no body -->
<body class="dark-mode">
  <div class="card">
    <h1>Bem-vindo ao Meu Site!</h1>
    <p>Este é um conteúdo com tema customizado dinâmico.</p>
    <button class="botao">Saiba Mais</button>
  </div>
</body>
```

**Resultado:**  
Ao adicionar a classe `dark-mode` ao elemento `<body>`, todas as propriedades que consomem `var(--cor-fundo)`, `var(--cor-texto)` e `var(--cor-primaria)` alteram suas cores instantaneamente na tela.

**Por que essa solução funciona:**  
As variáveis CSS respeitam a cascata e o escopo. Quando a classe `.dark-mode` é atribuída ao `body`, os novos valores definidos para as variáveis sobrescrevem os valores declarados em `:root`, atualizando automaticamente todos os seletores que as utilizam.

**O que preciso aprender com esse exemplo:**

- Variáveis CSS iniciam obrigatoriamente com dois traços (`--variavel`) e são consumidas com `var(--variavel)`.
- O uso de variáveis CSS facilita a manutenção do código e a implementação de temas (Light/Dark Mode) de maneira modular.
