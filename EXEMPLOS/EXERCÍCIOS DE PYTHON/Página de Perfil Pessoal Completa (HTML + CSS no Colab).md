**Problema:**  
Construir um site básico de portfólio de currículo digital contendo cabeçalhos de identificação, sessões estruturadas de competências de trabalho, exibição de imagens e links sociais interativos integrados de forma visual.

**Conceito utilizado:**  
Design modular, estilização CSS inline, listas estruturadas sem marcadores e propriedades de links sociais externos.

**Solução:**

```
from IPython.display import HTML

html_code = """
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Meu Perfil</title>
</head>
<body style="font-family: 'Arial', sans-serif; background-color: #f8f8f8; margin: 0; padding: 0;">

    <header style="text-align: center; background-color: #3498db; color: #fff; padding: 20px;">
        <h1 style="margin: 0;">Anderson Inácio Salata de Abreu</h1>
        <p style="margin: 5px 0;">Desenvolvedor Web</p>
    </header>

    <section style="margin: 20px; text-align: center;">
        <img src="content/sua_foto.jpg" alt="Sua Foto" style="border-radius: 50%; margin-bottom: 20px;">
        <div id="informacoes-pessoais" style="max-width: 400px; margin: 0 auto;">
            <p>Cidade: Sorocaba</p>
            <p>País: Brasil</p>
            <p>Interesses: Web Development, Programação, etc.</p>
        </div>
    </section>

    <section style="margin: 20px; text-align: center;">
        <h2>Habilidades</h2>
        <ul style="list-style: none; padding: 0;">
            <li>Linguagens: Python, HTML, CSS, JavaScript</li>
            <li>Ferramentas: Git, VS Code</li>
        </ul>
    </section>

    <section style="margin: 20px; text-align: center;">
        <h2>Projeto Recente</h2>
        <p>Trabalhando em um site pessoal para mostrar meu portfólio.</p>
    </section>

    <footer style="text-align: center; margin-top: 20px;">
        <a href="https://www.linkedin.com/in/andersonsalata/" target="_blank" style="margin: 0 10px; color: #3498db; text-decoration: none;">LinkedIn</a>
    </footer>

</body>
</html>
"""

HTML(html_code)
```

**Resultado:**  
Um site pessoal de currículo elegante renderizado e formatado em tela, contendo um cabeçalho e um link direto para o LinkedIn profissional.

**Por que essa solução funciona:**  
As regras de CSS inline determinam o design da interface (margens, preenchimentos, fontes e cores de fundo). A propriedade `target="_blank"` garante que o link social seja aberto em uma nova guia sem fechar a página original.

**O que preciso aprender com esse exemplo:**  
A criação de páginas ricas estruturadas com CSS inline permite organizar informações profissionais de forma atrativa e facilmente compartilhável em navegadores web.