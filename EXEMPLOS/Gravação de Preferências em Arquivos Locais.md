**Problema:** Salvar e restaurar configurações simples de comportamento do aplicativo (como salvar se o tema ativo é o "Tema Escuro") de maneira rápida e leve, sem a complexidade de gerenciar tabelas SQL no SQLite.

**Conceito utilizado:** Armazenamento lúdico de dados em **arquivos locais** com modo privado no Android.

**Solução:** Utilizar o método utilitário `openFileOutput` do sistema para criar e gravar dados lógicos simples diretamente em arquivos de texto no diretório privado da aplicação.

```
openFileOutput("config.txt", Context.MODE_PRIVATE).use {
    it.write("Tema=Escuro".toByteArray())
}
```

- **`openFileOutput("config.txt", ...)`:** Abre uma conexão de escrita direta de bytes vinculada a um arquivo local criado no celular de forma automática.
- **`Context.MODE_PRIVATE`:** Diretiva de segurança obrigatória que indica que apenas a própria aplicação tem permissão lógica de abrir e ler o arquivo.
- **`.use { ... }`:** Expressão idiomática Kotlin que gerencia o fluxo de fechamento seguro de canais de arquivo lúdicos de forma automática.

**Resultado:** As configurações de preferência do usuário do aplicativo móvel persistem em disco mesmo se o celular for reiniciado, permitindo restaurar a interface corretamente sem buscas longas.

**Por que essa solução funciona:** O sistema aloca e reserva blocos específicos protegidos de memória física de disco do dispositivo celular para que a aplicação serialize dados pequenos e rápidos com total isolamento.

**O que preciso aprender com esse exemplo:** Persistir dados em **arquivos locais** é indicado para pequenas configurações ou dados serializados brutos que dispensam estruturas complexas de busca.