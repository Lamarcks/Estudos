**Problema:** Um software que gerencia dispositivos IoT precisa processar dados lidos de um arquivo físico de configurações chamado `"config.txt"`. Caso o arquivo esteja ausente ou corrompido, o sistema não deve interromper de forma abrupta o seu funcionamento, e deve garantir que a liberação dos recursos seja executada, evitando vazamentos graves de memória.

**Conceito utilizado:** Gerenciamento profissional de erros com a estrutura de controle `try-catch-finally` e liberação de recursos escassos.

**Solução:** Colocar a rotina perigosa dentro do bloco `try`, interceptar falhas específicas de arquivo em bloco `catch` e utilizar o escopo obrigatório do `finally` para fechar os leitores de dados de forma garantida.

```
import java.io.File;
import java.io.FileNotFoundException;
import java.util.Scanner;

public class GerenciadorConfiguracao {
    public static void main(String[] args) {
        Scanner scanner = null;

        try {
            File arquivoConfig = new File("config.txt");
            scanner = new Scanner(arquivoConfig); // Operação que pode gerar erro

            while (scanner.hasNextLine()) {
                System.out.println(scanner.nextLine());
            }
        } catch (FileNotFoundException e) {
            // Tratamento do erro amigável ao usuário de forma transparente
            System.out.println("Erro: O arquivo de configuração não foi encontrado.");
        } finally {
            // O escopo do bloco finally garante a execução incondicional deste trecho
            if (scanner != null) {
                scanner.close(); // Libera recursos
                System.out.println("Recurso liberado: Scanner fechado.");
            } else {
                System.out.println("Nenhum recurso para fechar.");
            }
        }
    }
}
```

**Resultado:** Se o arquivo estiver ausente, o programa captura o erro de forma controlada, exibe o alerta explicativo na tela e garante a execução do fluxo de liberação antes de continuar o funcionamento normal.

**Por que essa solução funciona:** Ao ocorrer uma falha dentro do `try`, o Java abandona a execução desse bloco e salta imediatamente ao escopo do `catch` correspondente para mitigar o erro. Após concluir o tratamento ou a execução normal, o bloco `finally` é executado incondicionalmente pelo processador antes de continuar com as próximas instruções de código.

**O que preciso aprender com esse exemplo:**

- O bloco `try` isola códigos sensíveis propensos a gerar erros de execução.
- O bloco `catch` captura e trata exceções específicas de forma amigável.
- O bloco `finally` **sempre** será executado, ocorrendo erro ou não, sendo o local obrigatório para fechamento seguro de canais e fluxos de dados escassos de rede ou arquivos.
