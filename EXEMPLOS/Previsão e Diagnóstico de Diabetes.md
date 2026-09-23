**Problema:**
Classificar se um paciente desenvolveu ou possui propensão a ter diabetes.

**Conceito utilizado:**
Redes Neurais de Perceptron Multicamadas (MLP) aplicadas a problemas de Classificação Categórica.

**Solução:**
Utilizar um banco de dados de exames clínicos em formato tabular onde cada coluna representa um resultado de exame médico. Esses exames são passados como variáveis de entrada em uma rede MLP densamente conectada. A rede aprende a processar esses indicadores combinados através das camadas ocultas e, na camada de saída, fornece uma probabilidade ou classificação de diagnóstico de diabetes (positivo ou negativo).

**Resultado:**
Identificação automatizada e precoce de pacientes com diabetes a partir dos seus respectivos exames médicos.

**Por que essa solução funciona:**
As conexões densas (*fully connected*) cruzam e pesam todos os indicadores médicos coletados simultaneamente, mapeando as interações sutis entre múltiplos exames de saúde que um olho humano ou uma regra linear simples não detectaria com facilidade.

**O que preciso aprender com esse exemplo:**
Para problemas de classificação categórica (como diagnósticos binários "sim/não") baseados em tabelas estruturadas de exames, a MLP atua mapeando de forma não linear as conexões lógicas entre os dados para realizar o discernimento.