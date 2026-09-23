**Problema:** Converter o endereço decimal de ponto `192.168.0.22` para sua representação de formato binário interna utilizada por roteadores e switches.

**Conceito utilizado:** Representação posicional de um octeto de 8 bits. Cada bit em um octeto possui um peso baseado em potências de 2 (da esquerda para a direita):

- \(2^7 = 128\)
- \(2^6 = 64\)
- \(2^5 = 32\)
- \(2^4 = 16\)
- \(2^3 = 8\)
- \(2^2 = 4\)
- \(2^1 = 2\)
- \(2^0 = 1\)

**Solução:** Para converter cada octeto decimal, decompomos o número através da soma desses pesos posicionais, ativando com `1` os valores necessários e deixando com `0` os demais:

1. **Conversão do primeiro octeto (192)**:
    - \(192 = 128 + 64\) (Ativamos os bits de pesos 128 e 64).
    - Binário: `1 1 0 0 0 0 0 0`.
2. **Conversão do segundo octeto (168)**:
    - \(168 = 128 + 32 + 8\) (Ativamos os bits de pesos 128, 32 e 8).
    - Binário: `1 0 1 0 1 0 0 0`.
3. **Conversão do terceiro octeto (0)**:
    - \(0 = 0\) (Nenhum bit ativado).
    - Binário: `0 0 0 0 0 0 0 0`.
4. **Conversão do quarto octeto (22)**:
    - \(22 = 16 + 4 + 2\) (Ativamos os bits de pesos 16, 4 e 2).
    - Binário: `0 0 0 1 0 1 1 0`.

**Resultado:** O endereço IP decimal `192.168.0.22` em binário é: `11000000.10101000.00000000.00010110`

**Por que essa solução funciona:** Os dispositivos eletrônicos operam de forma nativa com lógica binária discreta (nível lógico 0 e nível lógico 1). A conversão posicional permite mapear de forma precisa e sem ambiguidade qualquer número decimal no intervalo de 0 a 255 em exatamente um byte (8 bits).

**O que preciso aprender com esse exemplo:** A conversão decimal-binário é o primeiro passo para realizar cálculos de máscaras de sub-redes personalizadas manualmente. Memorizar a sequência \(128, 64, 32, 16, 8, 4, 2, 1\) torna esse processo instantâneo.