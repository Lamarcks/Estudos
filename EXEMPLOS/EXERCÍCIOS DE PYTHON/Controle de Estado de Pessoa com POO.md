**Problema:**  
Modelar o comportamento biográfico de uma pessoa de forma que seja possível instanciar atributos básicos de identificação, recuperar saudações prontas e modificar de forma consistente o seu estado interno (como avançar a idade) no decorrer do tempo.

**Conceito utilizado:**  
Definição de classes (`class`), construtor de inicialização (`__init__`), variável de autorreferência (`self`) e métodos dinâmicos de alteração de atributos.

**Solução:**

```
class Pessoa:
    # Método Construtor: Inicializa o objeto com os atributos fornecidos
    def __init__(self, nome, idade, genero):
        self.nome = nome
        self.idade = idade
        self.genero = genero

    # Método de Comportamento: Devolve saudação personalizada
    def cumprimentar(self):
        return f"Olá, meu nome é {self.nome}."

    # Método de Mutação: Altera o estado do atributo interno 'idade'
    def aniversario(self):
        self.idade += 1

# Instanciação física da classe Pessoa
pessoa1 = Pessoa("João", 30, "Masculino")

print(pessoa1.cumprimentar())
print(f"Idade inicial de João: {pessoa1.idade} anos.")

# Invoca a ação para envelhecer a pessoa
pessoa1.aniversario()
print(f"Idade atualizada de João: {pessoa1.idade} anos.")
```

**Resultado:**  
João inicia sua instância com 30 anos, cumprimenta corretamente o usuário e passa a ter 31 anos de idade de forma imediata.

**Por que essa solução funciona:**  
O construtor `__init__` é invocado dinamicamente na instanciação na memória da máquina. O ponteiro reservado de contexto `self` vincula os atributos diretamente à identidade da instância concreta criada (`pessoa1`), permitindo atualizações de estado isoladas de outros objetos.

**O que preciso aprender com esse exemplo:**  
As classes estruturam o formato e as ações aceitáveis de objetos que refletem as entidades complexas do mundo físico real.