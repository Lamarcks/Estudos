**Problema:** Como responsável pela construção e implantação do sistema SMPA, seu objetivo é desenvolver uma arquitetura capaz de coletar e analisar um volume massivo de dados variados ao longo do tempo (temperatura, umidade do solo, qualidade da terra), disponibilizar alertas em tempo real e fornecer um painel de visualização para agricultores. Como estruturar o sistema de modo que a manutenção futura seja fácil e as mudanças de tecnologia não quebrem o código-fonte?.

**Conceito utilizado:** Estilo de **Arquitetura de Software em Camadas**.

**Solução:** Estruturar o software em 4 camadas de responsabilidades progressivas e independentes:

1. **Camada de Dispositivos IoT (A mais próxima do "mundo físico"):** Responsável exclusiva por coletar dados dos sensores de solo, temperatura e nível de água.
2. **Camada de Armazenamento de Dados:** Armazena os dados processados em um banco de dados integrado (relacional ou NoSQL).
3. **Camada de Processamento e Análise:** Executa a limpeza dos dados brutos e realiza a análise preditiva (inclusive com aprendizado de máquina).
4. **Camada de Aplicação Web (Interface Externa):** Painel acessível via web e celulares para que os agricultores acompanhem o estado das fazendas e recebam alertas de previsão de chuvas.

**Resultado:** Entendimento claro de onde cada alteração tecnológica deve ocorrer (ex: se trocar o modelo físico de um sensor IoT, altera-se apenas a camada IoT, sem afetar o processamento ou a interface web).

**Por que essa solução funciona:** Funciona porque implementa a separação de interesses (_low coupling_). As camadas realizam operações progressivas onde cada camada fornece serviços para a imediatamente superior.

**O que preciso aprender com esse exemplo:** A escolha de um estilo de arquitetura estruturada (como camadas) garante a **manutenibilidade e legibilidade do código-fonte** no longo prazo.