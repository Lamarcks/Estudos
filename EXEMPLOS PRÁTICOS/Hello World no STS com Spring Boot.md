**Problema:** Construir uma aplicação web RESTful com Java em tempo recorde, expondo uma URL que responda a requisições externas sem a necessidade de configurar arquivos XML ou servidores Tomcat manuais.

**Conceito utilizado:** Serviços RESTful e anotações do framework **Spring Boot** (utilizando seu servlet _Front Controller_ embutido).

**Solução:** Gerar um projeto no Spring Tool Suite (STS) com a dependência **Spring Web** e criar uma classe de controle mapeada para receber e tratar as solicitações lógicas HTTP.

```
package com.example.demo;

import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.bind.annotation.RequestMapping;

@RestController // Indica controle de requisições e respostas web RESTful
public class PrimeiroProgramaApplication {

    @RequestMapping("/hello") // Mapeia o endpoint lógico HTTP URL
    public String hello() {
        return "Hello World";
    }
}
```

- **`@RestController`:** Combinação de `@Controller` e `@ResponseBody`. Configura as classes Java lógicas para retornarem o resultado serializado diretamente na mensagem HTTP.
- **`@RequestMapping("/hello")`:** Direciona qualquer requisição recebida no endpoint `/hello` para a execução correspondente do método lógico anotado.
- **`return "Hello World";`:** Corpo da resposta enviado de volta para exibição em primeiro plano no navegador do usuário.

**Resultado:** A aplicação escuta conexões ativas na porta padrão `8080`. Ao acessar `http://localhost:8080/hello` no navegador, o conteúdo do texto "Hello World" é exibido em tela dinâmica de forma limpa.

**Por que essa solução funciona:** O servlet embutido intercepta a chamada de entrada de rede HTTP no computador local, analisa os mapeamentos de anotação existentes no container e executa o método Java correspondente de forma automatizada.

**O que preciso aprender com esse exemplo:** As anotações `@RestController` e `@RequestMapping` do Spring removem códigos ceremoniais repetitivos (_boilerplate_) associados a Servlets puros, facilitando a exposição de APIs lógicas na internet.
