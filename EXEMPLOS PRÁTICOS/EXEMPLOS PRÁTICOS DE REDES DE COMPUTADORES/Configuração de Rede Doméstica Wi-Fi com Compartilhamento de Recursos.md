**Problema:** Configurar de forma limpa e em poucos passos uma rede doméstica sem fio estável, permitindo que smartphones, Smart TVs, laptops e impressoras se comuniquem localmente e acessem a internet compartilhando um único link de internet banda larga residencial.

**Conceito utilizado:** Integração física e lógica residencial de **Modem**, **Roteador Wi-Fi**, **DHCP** e **NAT (Network Address Translation)**.

**Solução:** Guia de implementação residencial passo a passo:

1. **Passo 1 (Conexão Física de Hardware)**: Interconectar a porta WAN do roteador sem fio de alto desempenho à porta física LAN do modem do provedor de acesso (ISP) usando um cabo de rede Ethernet.
2. **Passo 2 (Acesso ao Painel Lógico de Controle)**:
    - Ligar ambos os dispositivos.
    - Em um laptop local, abrir o navegador web e acessar o IP de gerência interna padrão do roteador (geralmente `192.168.0.1` ou `192.168.1.1`).
    - Digitar o nome de login de administrador e a senha de fábrica descritos na parte traseira física do roteador.
3. **Passo 3 (Configurações WAN, Wi-Fi e Segurança)**:
    - Inserir as credenciais lógicas de conexão WAN fornecidas pela operadora (caso exigido).
    - Criar uma identificação de rede Wi-Fi residencial sem fios (**SSID**), ex.: `Familia_Silva_WiFi`.
    - Configurar segurança sem fio forte escolhendo o modo de criptografia pessoal e atribuindo uma senha de acesso longa e robusta.
    - Alterar a senha padrão de administrador de gerência do roteador para evitar invasões.
4. **Passo 4 (Conexão e Testes de Dispositivos)**:
    - Ligue os dispositivos Wi-Fi domésticos.
    - Procure a rede Wi-Fi configurada (`Familia_Silva_WiFi`) e conecte-se a ela usando a senha.

**Resultado:** Todos os aparelhos domésticos de forma sem fio acessam a internet ao mesmo tempo e compartilham com facilidade arquivos locais e conexões comuns de forma centralizada.

**Por que essa solução funciona:** O roteador ativa a tecnologia NAT internamente. O NAT converte de forma dinâmica os IPs privados de escopo de rede local (ex.: `192.168.1.X`) de cada celular ou laptop doméstico em um único IP público roteável globalmente fornecido pela operadora na interface WAN. Ele controla o retorno dos dados consultando sua tabela de tradução de portas para encaminhar as respostas do site ao computador correto.

**O que preciso aprender com esse exemplo:** Compreender como a segurança é aplicada em ambientes SOHO (Small Office/Home Office). Manter as senhas padrões de gerência intocadas (`admin/admin`) em roteadores domésticos é um dos principais erros de segurança explorados por cibercriminosos na internet.