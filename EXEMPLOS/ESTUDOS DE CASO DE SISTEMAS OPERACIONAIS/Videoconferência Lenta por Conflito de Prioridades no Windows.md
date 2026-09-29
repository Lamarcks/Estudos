**Problema:** Em uma empresa, videoconferências diárias com notebooks na sala de reuniões começaram a apresentar lentidão e perda de frames de vídeo. O técnico José analisou o sistema e identificou que o processo da videoconferência (que trabalha em tempo real) estava operando com prioridade baixa, enquanto uma rotina de sincronização de e-mails em segundo plano estava configurada com prioridade alta (provavelmente alterada manualmente por um usuário anterior).

**Conceito utilizado:** **Escalonamento por Prioridades** e preempção de processos no Windows.

**Solução:** José deve ajustar a prioridade no S.O. para dar preferência ao processo crítico de tempo real:

1. Pressionar `Ctrl + Alt + Del` e abrir o **Gerenciador de Tarefas**.
2. Clicar na aba **Detalhes** ou encontrar o processo de videoconferência na lista.
3. Clicar com o botão direito sobre o processo do aplicativo de videoconferência.
4. Selecionar a opção **Definir prioridade**.
5. Alterar de "Baixa" para **"Alta"** ou **"Tempo Real"**.
6. Alterar a prioridade do leitor de e-mails para "Baixa" ou "Normal".

**Resultado:** A lentidão e os engasgos da videoconferência cessam imediatamente, permitindo comunicação de vídeo fluida.

**Por que essa solução funciona:** O escalonador preemptivo distribui fatias de tempo da CPU com base no valor de prioridade. Ao elevar a prioridade da videoconferência, o S.O. interrompe ativamente processos de menor prioridade (como e-mails) sempre que houver pacotes de vídeo/áudio para processar, garantindo tempo de CPU adequado para a tarefa em tempo real.

**O que preciso aprender com esse exemplo:** Aplicações interativas ou de tempo real dependem de prioridades elevadas para mitigar atrasos. O S.O. respeita as configurações de prioridade mesmo se o usuário fizer alterações que prejudiquem a performance geral da máquina.