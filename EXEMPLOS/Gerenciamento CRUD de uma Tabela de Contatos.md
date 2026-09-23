**Problema:**  
Criar um sistema de catalogação interna para uma empresa onde seja possível registrar contatos (nome, e-mail, telefone), listar todos os cadastros e, posteriormente, demonstrar de forma íntegra a alteração de dados de registro e exclusão física de um contato de teste.

**Conceito utilizado:**  
Conexão SQL, operações fundamentais **CRUD** (_Create, Read, Update, Delete_), execução em massa (`executemany`) e controle transacional no disco local via módulo `sqlite3`.

**Solução:**

```
import sqlite3

# Passo 1: Inicia conexão e cria arquivo contatos.db no disco
conn = sqlite3.connect('contatos.db')
cursor = conn.cursor()

# Passo 2 [DDL]: Cria a tabela caso não exista
cursor.execute('''
    CREATE TABLE IF NOT EXISTS Contatos (
        id INTEGER PRIMARY KEY AUTOINCREMENT,
        nome TEXT,
        email TEXT,
        telefone TEXT
    )
''')

# Passo 3 [DML - CREATE]: Inserção rápida em lote de contatos iniciais
dados_exemplo = [
    ('João', 'joao@email.com', '123-456-7890'),
    ('Maria', 'maria@email.com', '987-654-3210'),
    ('Carlos', 'carlos@email.com', '555-555-5555')
]
cursor.executemany('INSERT INTO Contatos (nome, email, telefone) VALUES (?, ?, ?)', dados_exemplo)
conn.commit()  # Grava as inserções no disco local

# Passo 4 [DML - READ]: Leitura sequencial e impressão dos dados cadastrados
cursor.execute('SELECT * FROM Contatos')
contatos = cursor.fetchall()
print("Contatos Cadastrados Inicialmente:")
for contato in contatos:
    print(contato)

# Passo 5 [DML - UPDATE]: Altera de forma direcionada o contato do ID 2
novo_telefone = '999-999-9999'
contato_id = 2
cursor.execute('UPDATE Contatos SET telefone = ? WHERE id = ?', (novo_telefone, contato_id))
conn.commit()

# Passo 6 [DML - DELETE]: Remove fisicamente o contato contido no ID 1
contato_id_para_excluir = 1
cursor.execute('DELETE FROM Contatos WHERE id = ?', (contato_id_para_excluir,))
conn.commit()

# Finaliza cursor e conexão
cursor.close()
conn.close()
```

**Resultado:**  
Geração do banco físico, população de dados estruturados em lote, seguido da exclusão do contato ID 1 e modificação do telefone do contato ID 2.

**Por que essa solução funciona:**  
O comando `sqlite3.connect()` estabelece um pipe seguro. As interações ocorrem no buffer do cursor e são escritas fisicamente no arquivo binário de disco apenas quando o comando `conn.commit()` confirma a integridade da transação.

**O que preciso aprender com esse exemplo:**  
A correta execução de conexões relacionais usando a API regulada do PEP 249 garante a portabilidade e a integridade de dados locais do programa.
