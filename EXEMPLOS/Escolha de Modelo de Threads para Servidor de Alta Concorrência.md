**Problema:** Um arquiteto de sistemas de TI precisa desenvolver um servidor web robusto para hospedar múltiplos portais corporativos. O sistema exige alta concorrência para suportar milhares de acessos síncronos de clientes, uso eficiente e econômico de CPU/RAM para poupar infraestrutura física e ampla escalabilidade para expansões futuras. Qual modelo de mapeamento de threads adotar?

**Conceito utilizado:** Modelos de mapeamento de threads: _Many-to-One_, _One-to-One_, _Many-to-Many_ e _Híbridos_.

**Solução:** Implementar o modelo **Many-to-Many (Muitos-para-Muitos)**.

**Resultado:** Múltiplas threads criadas pelas aplicações dos usuários são mapeadas dinamicamente para um número reduzido (e sob demanda) de threads gerenciadas pelo núcleo (kernel) do sistema operacional.

**Por que essa solução funciona:**

- **Contraste com o Many-to-One**: Se um thread de usuário fizesse uma chamada bloqueante ao disco, o processo inteiro travaria.
- **Contraste com o One-to-One**: Evita criar um processo no kernel para cada usuário ativo, o que exauriria a RAM e a CPU devido ao overhead extremo de criação e troca de contexto de hardware.
- O **Many-to-Many** une o melhor de dois mundos: as threads de nível de usuário são rápidas de criar na memória, e os núcleos reais da CPU são divididos apenas entre as threads ativas do kernel, otimizando o paralelismo real do processador.

**O que preciso aprender com esse exemplo:** O modelo _Many-to-Many_ oferece o melhor equilíbrio para sistemas de alto desempenho, pois fornece escalabilidade robusta com baixo consumo de memória, permitindo que servidores manipulem picos de tráfego sem sofrer sobrecargas de hardware.
