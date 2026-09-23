**Problema:** Em uma agência de marketing digital de pequeno porte, arquivos importantes de análise de mercado criados pelo setor comercial simplesmente desapareceram de pastas compartilhadas na rede interna. O técnico de suporte, Pedro, descobriu que funcionários de outros departamentos (desenvolvimento e vendas) deletaram os arquivos de forma acidental, pois a pasta de uso comum estava acessível sem restrições a todos.

**Conceito utilizado:** **Controle de Acesso** e políticas de permissões em diretórios do S.O..

**Solução:** Pedro deve remover os privilégios amplos de administrador dos funcionários comuns e aplicar regras rígidas baseadas em grupos de usuários:

1. Configurar as pastas de análises de mercado para que apenas o grupo do setor Comercial possua privilégios de **Escrita/Modificação**.
2. Definir o acesso de todos os outros setores comuns da empresa para **"Somente Leitura" (Read-Only)**.
3. Utilizar o arquivo de backup de rede realizado anteriormente para restaurar os arquivos deletados de volta para a pasta de origem.

**Resultado:** Os arquivos são recuperados, e novos incidentes de exclusões indevidas são impedidos, já que o S.O. bloqueia tentativas de escrita de usuários não autorizados.

**Por que essa solução funciona:** Os sistemas operacionais modernos validam as credenciais do usuário em listas de controle de acesso (ACL) antes de executar operações destrutivas como exclusão de arquivos. Se a conta do usuário não possuir o bit de modificação ativo para aquela pasta específica, a operação é abortada com mensagem de erro.

**O que preciso aprender com esse exemplo:** Contas com privilégios administrativos de gravação/exclusão total para todos os usuários em pastas corporativas são uma grave falha de segurança. O uso de perfis com permissões limitadas ("mínimo privilégio") e rotinas de backup são cruciais para a resiliência e integridade dos dados empresariais.