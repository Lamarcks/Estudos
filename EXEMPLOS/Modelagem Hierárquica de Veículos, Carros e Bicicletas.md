**Problema:**  
Projetar um sistema de modelagem física de veículos que unifique marca, modelo e ano, permitindo que carros acessem potência de aceleração de motor enquanto bicicletas tenham o seu tipo físico catalogado diretamente na exibição de seu status de velocidade.

**Conceito utilizado:**  
Herança múltipla e herança simples de classes, construtores e o comando chave `super()` para reaproveitamento de rotinas de inicialização de superclasses.

**Solução:**

```
# Classe Geral de Veículos (Superclasse)
class Veiculo:
    def __init__(self, marca, modelo, ano):
        self.marca = marca
        self.modelo = modelo
        self.ano = ano
        self.velocidade = 0

    def acelerar(self, incremento):
        self.velocidade += incremento

    def frear(self, decremento):
        self.velocidade -= decremento

    def status(self):
        return f"Marca: {self.marca}, Modelo: {self.modelo}, Ano: {self.ano}, Velocidade: {self.velocidade} km/h"

# Subclasse Especializada para Carros
class Carro(Veiculo):
    def __init__(self, marca, modelo, ano, potencia):
        # super() aciona e roda o construtor original da classe-pai
        super().__init__(marca, modelo, ano)
        self.potencia = potencia

    def acelerar(self, incremento):
        # Carros aceleram mais rápido de acordo com seu motor de potência
        self.velocidade += incremento + self.potencia

# Subclasse Especializada para Bicicletas
class Bicicleta(Veiculo):
    def __init__(self, marca, modelo, ano, tipo):
        super().__init__(marca, modelo, ano)
        self.tipo = tipo

    def status(self):
        # Retorna o status de veículo de bicicleta com a inclusão de seu tipo físico
        return f"Marca: {self.marca}, Modelo: {self.modelo}, Ano: {self.ano}, Tipo: {self.tipo}, Velocidade: {self.velocidade} km/h"

# Instanciação e Execução das Classes
carro1 = Carro("Toyota", "Corolla", 2022, 150)
bicicleta1 = Bicicleta("Trek", "Mountain Bike", 2021, "MTB")

# Aceleração de instâncias utilizando regras de polimorfismo e herança
carro1.acelerar(50)
bicicleta1.acelerar(20)

print("Status do Carro:")
print(carro1.status())

print("\nStatus da Bicicleta:")
print(bicicleta1.status())
```

**Resultado:**

- Carro atinge a velocidade de `200 km/h` (50 base + 150 potência de motor).
- Bicicleta exibe corretamente o seu status contendo o tipo do quadro cadastrado ("MTB").

**Por que essa solução funciona:**  
O comando `super().__init__()` garante a execução correta da rotina de instanciação central da classe superior, reduzindo redundâncias de atribuições redundantes. O método especializado de aceleração em `Carro` substitui o comportamento simples da classe genérica de base.

**O que preciso aprender com esse exemplo:**  
A herança com herança estendida (`super()`) viabiliza a estruturação robusta e altamente customizada de sistemas orientados a objetos.