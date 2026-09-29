**Problema:**  
Desenvolver um programa para gerenciar o acervo de uma biblioteca acadêmica usando classes para representar cada livro, e gerar de forma automatizada um gráfico de linha temporal para mostrar a distribuição histórica das publicações existentes.

**Conceito utilizado:**  
Paradigma orientado a objetos, manipulação de coleções, unificação de chaves temporais com conjunto (`set`), ordenação nativa de listas (`sort()`), anotações matemáticas de rótulos sobre os eixos cartesianos e ativação de grades auxiliares (`grid`).

**Solução:**

```
import matplotlib.pyplot as plt

# Criação da classe estruturada que define um Livro
class Livro:
    def __init__(self, titulo, autor, ano_publicacao):
        self.titulo = titulo
        self.autor = autor
        self.ano_publicacao = ano_publicacao

    # Método especial que dita a representação em texto do objeto criado
    def __str__(self):
        return f"'{self.titulo}' por {self.autor}, Publicado em {self.ano_publicacao}"

# Instanciação da coleção de dados vazia do acervo da biblioteca
biblioteca = []

# Função auxiliar para realizar a inserção de novos livros no catálogo
def adicionar_livro(titulo, autor, ano_publicacao):
    novo_livro = Livro(titulo, autor, ano_publicacao)
    biblioteca.append(novo_livro)
    print(f"Livro '{titulo}' foi adicionado com sucesso.")

# Cadastra livros de teste no sistema da biblioteca
adicionar_livro("Dom Quixote", "Miguel de Cervantes", 1605)
adicionar_livro("Orgulho e Preconceito", "Jane Austen", 1813)
adicionar_livro("1984", "George Orwell", 1949)
adicionar_livro("Cem Anos de Solidão", "Gabriel Garcia Marquez", 1967)
adicionar_livro("Apanhador no Campo de Centeio", "J.D. Salinger", 1951)

# Lista todos os cadastros no painel do console
print("\n--- Listando Catálogo Físico ---")
for livro in biblioteca:
    print(livro)

# --- Processamento dos dados estruturados para plotagem ---
# Passo 1: Extrai todos os anos de publicação dos livros cadastrados
todos_anos = [livro.ano_publicacao for livro in biblioteca]

# Passo 2: Remove redundâncias de datas usando as propriedades de sets
anos_unicos = list(set(todos_anos))
anos_unicos.sort()  # Ordena cronologicamente os anos unificados

# Passo 3: Computa a contagem de quantos volumes existem para cada ano específico
contagem_por_ano = [todos_anos.count(ano) for ano in anos_unicos]

# Passo 4: Montagem do gráfico de distribuição temporal usando Matplotlib
plt.plot(anos_unicos, contagem_por_ano, marker='o', linestyle='-', color='darkblue')
plt.xlabel('Ano de Publicação')
plt.ylabel('Número de Livros Cadastrados')
plt.title('Distribuição de Obras na Biblioteca por Ano de Publicação')

# Insere dinamicamente rótulos textuais de dados sobre os marcadores
for i, valor in enumerate(contagem_por_ano):
    plt.text(anos_unicos[i], valor, str(valor), ha='center', va='bottom')

plt.grid(True)  # Ativa a grade de suporte visual ao fundo
plt.show()
```

**Resultado:**  
Impressão textual detalhada de todas as obras da biblioteca seguida da renderização gráfica precisa da distribuição temporal de publicações por ano.

**Por que essa solução funciona:**  
A conversão da lista de anos para `set()` remove automaticamente as datas repetidas. O laço com compressão quantifica as ocorrências com `.count()`, alinhando os eixos de forma correta. A função `plt.text()` permite plotar anotações descritivas em coordenadas cartesianas específicas.

**O que preciso aprender com esse exemplo:**  
A união estruturada de programação orientada a objetos (POO), estruturas de dados nativas e bibliotecas gráficas permite construir sistemas robustos e eficientes de gerenciamento de dados.
