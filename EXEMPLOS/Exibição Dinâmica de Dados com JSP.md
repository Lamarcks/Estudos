**Problema:** Exibir em tempo de execução para o usuário a data e hora em que ele acessou uma página web corporativa sem usar componentes front-end pesados para processar a hora do dispositivo.

**Conceito utilizado:** **JavaServer Pages (JSP)** e renderização dinâmica no servidor (_Server-Side Rendering_).

**Solução:** Desenvolver uma página contendo marcação HTML regular com expressões e rotinas de lógica Java embutidas em tags de scriptlet especiais (`<% %>` e `<%= %>`).

```
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
    pageEncoding="ISO-8859-1"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Insert title here</title>
</head>
<body>
    Olá Mundo! Aqui é um código HTML simples.
    <%
        int valor = 88;
        out.println("Olá Mundo! Exemplo de código com JSP");
    %>
    <h1> A hora atual é: <%= new java.util.Date() %> </h1>
    <%
        out.println("O valor é: " + valor);
    %>
</body>
</html>
```

- **`<%@ page ... %>`:** Diretiva lúdica inicial que especifica configurações do container e a codificação do arquivo web gerado.
- **`<% ... %>`:** Tag de Scriptlet utilizada para inserir instruções lógicas Java nativas diretamente na página.
- **`out.println()`:** Objeto nativo implicitamente instanciado para transmitir mensagens dinâmicas diretamente à resposta HTML visualizada.
- **`<%= ... %>`:** Tag de expressão que insere e imprime de forma direta a representação de texto do objeto Java no documento gerado.

**Resultado:** A página renderiza de forma dinâmica e atualizada a data/hora local do servidor e exibe os valores lógicos calculados ao usuário final a cada atualização do navegador.

**Por que essa solução funciona:** Ao receber a chamada do arquivo JSP, o container de servlet compila o código e gera fisicamente um Servlet Java em segundo plano no servidor, responsável por processar o código dinâmico e devolver HTML puro formatado para o usuário.

**O que preciso aprender com esse exemplo:** O JSP mescla HTML e Java para gerar telas e dados lógicos dinâmicos no servidor de forma ágil.