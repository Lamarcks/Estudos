**Problema:** Uma loja de ferramentas precisa de uma alternativa viável para substituir o seu controle manual de estoque, que causa constantes inconsistências e atrasos nas entregas. O sistema deve permitir cadastrar novas ferramentas, atualizar dados pelo código, exibir todo o inventário ativo e gerar relatórios específicos sinalizando itens com níveis de estoque perigosamente baixos (menores que cinco unidades).

**Conceito utilizado:** Leitura e gravação sequencial de dados em arquivo físico (`estoque.txt`) por fluxos otimizados (`BufferedReader`/`BufferedWriter`) e manipulação de arquivos temporários para alteração de registros específicos de texto.

**Solução:** Os dados são escritos de forma persistente divididos por delimitadores (`" | "`). Para realizar atualizações sobre linhas estáticas, lê-se o arquivo original para escrever as modificações em um arquivo temporário secundário, substituindo o cadastro original ao final por manipulação do sistema operacional.

```
import java.io.*;

public class EstoqueManager {
    private static final String ARQUIVO_ESTOQUE = "estoque.txt";

    // Adição de registros usando modo "Append" (parâmetro true)
    public static void adicionarProduto(String codigo, String descricao, int quantidade, double preco) throws IOException {
        if (produtoExiste(codigo)) {
            System.out.println("Produto com código " + codigo + " já existe.");
            return;
        }
        try (BufferedWriter writer = new BufferedWriter(new FileWriter(ARQUIVO_ESTOQUE, true))) {
            writer.write(codigo + " | " + descricao + " | " + quantidade + " | " + preco);
            writer.newLine();
        }
    }

    // Atualização de registro através de arquivo temporário
    public static void atualizarProduto(String codigo, int novaQuantidade, double novoPreco) throws IOException {
        File arquivo = new File(ARQUIVO_ESTOQUE);
        File arquivoTemp = new File("estoque_temp.txt");

        try (BufferedReader reader = new BufferedReader(new FileReader(arquivo));
             BufferedWriter writer = new BufferedWriter(new FileWriter(arquivoTemp))) {
            String linha;
            while ((linha = reader.readLine()) != null) {
                String[] partes = linha.split(" \\| ");
                if (partes.equals(codigo)) {
                    linha = codigo + " | " + partes + " | " + novaQuantidade + " | " + novoPreco; // Altera dados específicos
                }
                writer.write(linha);
                writer.newLine();
            }
        }
        arquivo.delete(); // Exclui o arquivo antigo desatualizado
        arquivoTemp.renameTo(arquivo); // Substitui o arquivo temporário como o novo estoque oficial
    }

    // Relatório analítico de estoque baixo
    public static void gerarRelatorioEstoqueBaixo() throws IOException {
        System.out.println("Relatório de Estoque Baixo:");
        try (BufferedReader reader = new BufferedReader(new FileReader(ARQUIVO_ESTOQUE))) {
            String linha;
            while ((linha = reader.readLine()) != null) {
                String[] partes = linha.split(" \\| ");
                int quantidade = Integer.parseInt(partes.trim()); // Cast de texto para inteiro
                if (quantidade < 5) {
                    System.out.println(linha);
                }
            }
        }
    }
}
```

**Resultado:** Os produtos são gravados no arquivo de texto, as atualizações modificam as quantidades de itens específicos em tempo de execução e o relatório alerta no console apenas as ferramentas sob risco de desabastecimento.

**Por que essa solução funciona:** Como arquivos de texto convencionais não permitem alteração de dados no meio da sua estrutura, a estratégia de leitura linear e recriação em um arquivo auxiliar temporário simula perfeitamente um banco de dados rudimentar e garante a persistência física das informações mesmo após o encerramento do programa.

**O que preciso aprender com esse exemplo:**

- Sempre utilize buffers (`BufferedReader`/`BufferedWriter`) para leituras e gravações eficientes, pois eles diminuem as requisições diretas ao disco rígido do sistema.
- Use delimitadores consistentes (como `|` ou vírgulas) e faça a higienização de strings utilizando comandos de remoção de espaços em branco (`trim()`) antes de executar conversões de dados (`Integer.parseInt`).