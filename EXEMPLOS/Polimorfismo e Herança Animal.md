**Problema:**  
Estruturar o modelo de uma hierarquia zoológica simples que compartilhe a propriedade de conter um nome, permitindo herdar as definições básicas, mas emitindo barulhos estritamente distintos de acordo com a espécie instanciada.

**Conceito utilizado:**  
Herança de classe simples, superclasse, subclasses e aplicação prática de **Polimorfismo**.

**Solução:**

```
# Superclasse Base
class Animal:
    def __init__(self, nome):
        self.nome = nome

    def fazer_barulho(self):
        pass  # Comportamento indefinido na classe abstrata de topo

# Subclasse especializada em cães
class Cachorro(Animal):
    def fazer_barulho(self):
        return "Latir"

# Subclasse especializada em felinos
class Gato(Animal):
    def fazer_barulho(self):
        return "Miar"

# Criando instâncias de subclasses
rex = Cachorro("Rex")
whiskers = Gato("Whiskers")

# Execução do mesmo método sobre objetos distintos (Polimorfismo)
print(f"{rex.nome} faz: {rex.fazer_barulho()}")
print(f"{whiskers.nome} faz: {whiskers.fazer_barulho()}")
```

**Resultado:**  
Rex retorna o barulho "Latir", enquanto whiskers devolve o som "Miar" de forma totalmente independente usando o mesmo método genérico de chamada.

**Por que essa solução funciona:**  
As classes filhas (`Cachorro` e `Gato`) herdam o construtor da superclasse (`Animal`), porém redefinem o comportamento do método `fazer_barulho()`. O interpretador invoca a versão especializada do método correspondente ao tipo real do objeto em execução.

**O que preciso aprender com esse exemplo:**  
O polimorfismo permite que diferentes classes derivadas executem suas próprias versões customizadas de um mesmo método herdado.