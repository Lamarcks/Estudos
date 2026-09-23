**Problema:** Em um site de e-commerce, as usuárias enfrentam barreiras intransponíveis no fluxo de checkout devido a uma falha no campo "Data de Validade" do cartão de crédito. A interface não exibe nenhuma indicação visual de instrução ou formato esperado. O sistema espera que o ano seja inserido com 4 dígitos (ex: 2026), mas quando as usuárias inserem com apenas 2 dígitos (ex: 26), o site emite um alerta de erro genérico que não especifica qual é a falha. Isso resulta em tentativas repetidas de preenchimento incorreto, frustração e desistência imediata de compra.

**Conceito utilizado:**

- Heurística de Nielsen nº 5 (Prevenção de Erros) e Heurística nº 9 (Reconhecimento e Recuperação de Erros).
- Design de diálogos claros e assistência na entrada de dados (Princípio 3 da WCAG).

**Solução:**

1. **Instrução Prévia (Prevenção):** Adicionar uma máscara de texto ou um exemplo visual explícito no próprio campo de preenchimento indicando o formato esperado (ex: MM/AAAA).
2. **Tratamento de Mensagem de Erro (Recuperação):** Substituir códigos ou mensagens genéricas de sistema por uma mensagem de erro construtiva, legível e em linguagem natural que informe exatamente o formato incorreto e como corrigi-lo.

**Resultado:** Preenchimento fluido e sem erros do formulário, redução imediata na frustração do usuário e conclusão bem-sucedida do pagamento de forma autônoma.

**Por que essa solução funciona:** A solução funciona porque remove a necessidade de o usuário tentar adivinhar a lógica técnica de backend do sistema. Ao guiar a digitação ou oferecer caminhos de recuperação claros, evita-se o atrito e preserva-se o controle do usuário.

**O que preciso aprender com esse exemplo:** Mensagens de erro devem ser expressas em **linguagem clara e compreensível** (sem expor códigos técnicos internos de programação), devem **indicar precisamente o problema** e **sugerir de forma construtiva uma solução prática**.
