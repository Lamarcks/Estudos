**Problema:** Um técnico de TI de um site de leilões online criou novas contas de usuários para funcionários recém-admitidos, realizou a rotina de backups preventivos e executou o utilitário de antivírus corporativo em um servidor Windows. No dia seguinte, o coordenador relatou desesperado que vários de seus arquivos haviam sumido do diretório compartilhado.

**Conceito utilizado:** Ações corretivas de antivírus e perfis de usuário redundantes.

**Solução:** Investigar o sumiço dos dados em duas frentes de ação:

1. **Verificar os Perfis de Usuário**: A criação de novas contas idênticas pode ter feito o Windows gerar uma pasta de perfil limpa e redundante para o coordenador, mascarando o acesso ao perfil original. Basta acessar o painel de gerenciador de contas de usuários para redirecionar ao perfil anterior contendo os arquivos intactos.
2. **Restaurar do Backup**: Se os arquivos sumiram porque estavam infectados por vírus e o antivírus realizou a exclusão automática para conter ameaças, deve-se reverter as cópias limpas e seguras de dados a partir do backup de segurança realizado no dia anterior.

**Resultado:** Os arquivos cruciais de fidelização são restabelecidos sem gerar atrasos para a equipe.

**Por que essa solução funciona:** O backup cria uma imagem estática dos dados que fica protegida contra falhas ou exclusões imediatas de antivírus. Ao acessar perfis de usuários de forma isolada, garante-se que os arquivos permaneçam associados aos IDs originais corretos.

**O que preciso aprender com esse exemplo:** Ações de manutenção do sistema (como rodar antivírus ou criar contas) podem causar perdas de dados imprevistas devido a vírus ou perfis corrompidos. A regra de ouro de qualquer administrador de sistemas é sempre efetuar um backup completo verificado antes de aplicar mudanças estruturais na rede ou no S.O..