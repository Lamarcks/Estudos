**Problema:**  
Replicar o protótipo de uma calculadora matemática funcional e interativa voltada para celulares e dispositivos multitouch com base nas diretrizes visuais do Google Material Design.

**Conceito utilizado:**  
Campos de texto de leitura numéricos (`MDTextField`), grade estruturada de botões de ações (`GridLayout`), dimensionamento espacial de pixels densos (`dp`), e avaliação automática de expressões em formato de texto (`eval()`).

**Solução:**

```
# Requisito: Executar o script em ambiente gráfico local habilitado
# !pip install kivymd

from kivy.lang import Builder
from kivy.uix.boxlayout import BoxLayout
from kivy.uix.gridlayout import GridLayout
from kivymd.app import MDApp
from kivymd.uix.button import MDRaisedButton
from kivymd.uix.textfield import MDTextField
from kivy.metrics import dp

# Interface declarada com as especificações do Material Design
KV = '''
<CalculatorApp>:
    orientation: 'vertical'
    MDTextField:
        id: input_field
        hint_text: "Insira um número"
        helper_text_mode: "on_focus"
        input_filter: "float"
    GridLayout:
        cols: 4
        spacing: dp(10)
        MDRaisedButton:
            text: "1"
            on_press: app.on_number_press(1)
        MDRaisedButton:
            text: "2"
            on_press: app.on_number_press(2)
        MDRaisedButton:
            text: "3"
            on_press: app.on_number_press(3)
        MDRaisedButton:
            text: "+"
            on_press: app.on_operator_press("+")
        MDRaisedButton:
            text: "4"
            on_press: app.on_number_press(4)
        MDRaisedButton:
            text: "5"
            on_press: app.on_number_press(5)
        MDRaisedButton:
            text: "6"
            on_press: app.on_number_press(6)
        MDRaisedButton:
            text: "-"
            on_press: app.on_operator_press("-")
        MDRaisedButton:
            text: "7"
            on_press: app.on_number_press(7)
        MDRaisedButton:
            text: "8"
            on_press: app.on_number_press(8)
        MDRaisedButton:
            text: "9"
            on_press: app.on_number_press(9)
        MDRaisedButton:
            text: "*"
            on_press: app.on_operator_press("*")
        MDRaisedButton:
            text: "C"
            on_press: app.clear_input()
        MDRaisedButton:
            text: "0"
            on_press: app.on_number_press(0)
        MDRaisedButton:
            text: "="
            on_press: app.calculate_result()
        MDRaisedButton:
            text: "/"
            on_press: app.on_operator_press("/")
'''

class CalculatorApp(BoxLayout):
    def on_number_press(self, number):
        current_text = self.ids.input_field.text
        new_text = f"{current_text}{number}"
        self.ids.input_field.text = new_text

    def on_operator_press(self, operator):
        current_text = self.ids.input_field.text
        new_text = f"{current_text} {operator} "
        self.ids.input_field.text = new_text

    def clear_input(self):
        self.ids.input_field.text = ""

    def calculate_result(self):
        try:
            # Avalia a string de expressão matemática diretamente
            result = eval(self.ids.input_field.text)
            self.ids.input_field.text = str(result)
        except Exception as e:
            self.ids.input_field.text = "Erro"

class CalculatorMDApp(MDApp):
    def build(self):
        return CalculatorApp()

    # Encaminha chamadas do front para os métodos internos
    def on_number_press(self, number):
        self.root.on_number_press(number)
    def on_operator_press(self, operator):
        self.root.on_operator_press(operator)
    def clear_input(self):
        self.root.clear_input()
    def calculate_result(self):
        self.root.calculate_result()

if __name__ == '__main__':
    Builder.load_string(KV)
    CalculatorMDApp().run()
```

**Resultado:**  
Construção visual e lógica de uma calculadora para celulares que computa operações de soma, subtração, multiplicação e divisão de forma interativa.

**Por que essa solução funciona:**  
O KivyMD mapeia os identificadores declarados no arquivo KV através do dicionário dinâmico `self.ids`. A função nativa `eval()` recebe a string textual da caixa de entrada de dados, interpreta e processa a computação matemática em tempo de execução de forma direta.

**O que preciso aprender com esse exemplo:**  
A separação de rotinas em arquivos declarativos (KV) e arquivos lógicos (Python) facilita o desenvolvimento organizado de aplicações mobile robustas.