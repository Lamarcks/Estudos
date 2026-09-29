**Problema:** Em uma lan house com máquinas antigas, os clientes enviam documentos para impressão em um computador central. Quando mais de dois clientes tentam enviar arquivos de forma simultânea, o documento do último usuário acaba sobrescrevendo os dados do cliente anterior na pasta temporária da máquina de impressão central, gerando perda de dados.

**Conceito utilizado:** Problemas de **Relocação** e **Proteção de Memória** em sistemas multiprogramados.

**Solução:** Em termos teóricos de engenharia de S.O., a solução exige equipar o processador com registradores de **Base e Limite**. O registrador-base aponta para o endereço físico inicial do processo na memória RAM, enquanto o registrador-limite indica o tamanho máximo do bloco alocado. Qualquer tentativa do processo de acessar endereços fora desses limites é bloqueada pelo hardware. Como as máquinas eram excessivamente antigas e não permitiam essa implementação por hardware de forma ágil, a solução prática recomendada foi a substituição do computador central por uma máquina atual com suporte nativo a esses mecanismos.

**Resultado:** Cada arquivo enviado para impressão passa a ocupar um espaço de endereçamento de memória lógica isolado e protegido, impedindo que novas transferências sobrescrevam trechos de processos ainda ativos na RAM.

**Por que essa solução funciona:** Os registradores base e limite criam uma barreira de proteção física no hardware do processador. O S.O. confere cada instrução de leitura ou escrita dinamicamente; se o processo tentar extrapolar sua área de partição permitida, o hardware gera uma interrupção de erro imediatamente antes que qualquer dado alheio seja danificado.

**O que preciso aprender com esse exemplo:** A multiprogramação exige isolamento rigoroso. Sem mecanismos de proteção baseados em hardware (como registradores ou paginação), os processos concorrentes irão invadir os espaços uns dos outros inevitavelmente, gerando corrupção de dados e vulnerabilidades de segurança.
