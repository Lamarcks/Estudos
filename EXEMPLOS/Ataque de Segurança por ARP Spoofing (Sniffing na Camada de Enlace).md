**Problema:** Um invasor na rede local (LAN) corporativa deseja interceptar de forma silenciosa todos os pacotes lógicos de dados contendo dados altamente confidenciais (logins, credenciais de e-mails, senhas financeiras) trocados entre o computador de um funcionário e a internet, sem que a máquina de destino ou o roteador gateway central percebam a intrusão.

**Conceito utilizado:** Vulnerabilidade intrínseca de confiança cega do protocolo de camada 2 **ARP (Address Resolution Protocol)** e técnicas de interceptação de tráfego (**Sniffing**).

**Solução:** O ataque explora a falta de autenticação no protocolo ARP na rede local local:

1. **Fase de Varredura**: O atacante utiliza um software analisador de pacotes em sua placa de rede (NIC configurada em modo promíscuo de captura) para mapear o IP lógico da vítima e o IP do roteador gateway da empresa.
2. **Envenenamento de Tabela (Spoofing)**: O atacante passa a enviar ciclos de pacotes ARP falsificados na rede:
    - Envia um pacote ARP para a máquina do funcionário vítima alegando: _"Eu possuo o endereço IP do roteador gateway. O endereço físico MAC associado ao IP do roteador é o MAC da minha placa de rede"_.
    - Envia simultaneamente um pacote ARP para o roteador gateway alegando: _"Eu possuo o endereço IP da máquina da vítima. O endereço físico MAC associado a ela é o MAC da minha placa"_.
3. **Captura de Fluxo**: Ambas as tabelas ARP locais (da vítima e do roteador) são atualizadas com os dados maliciosos.
4. **Interceptação**: Quando o funcionário digita uma senha e envia dados, o computador da vítima consulta a tabela envenenada e envia os quadros Ethernet diretamente ao endereço MAC físico do atacante. O atacante captura e decodifica os pacotes (utilizando o software **Wireshark**), extrai as senhas e repassa os pacotes intactos ao roteador original para não levantar suspeitas de queda de conexão.

**Resultado:** Interceptação e vazamento de dados confidenciais do usuário corporativo.

**Por que essa solução funciona:** O protocolo ARP padrão foi concebido sem mecanismos internos fortes de validação, autenticação ou segurança ativa. Qualquer dispositivo pode responder a uma requisição ARP alegando possuir um determinado endereço IP local, e a máquina de envio aceitará a resposta sem realizar nenhuma verificação de autoridade para atualizar sua tabela de endereçamento local.

**O que preciso aprender com esse exemplo:** Para conter ataques destrutivos de ARP Spoofing e interceptação na camada de enlace, administradores de TI não devem confiar apenas na rede física comum. É fundamental implementar criptografia forte de ponta a ponta (como **SSL/TLS e HTTPS**) de forma que, mesmo que o pacote de dados seja interceptado pelo invasor, o conteúdo das credenciais permaneça completamente ilegível para terceiros.
