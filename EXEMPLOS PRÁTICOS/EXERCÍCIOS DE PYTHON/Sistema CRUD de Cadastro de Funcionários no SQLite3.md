**Problema:**  
Implementar de ponta a ponta as rotinas de gerenciamento de pessoal para uma empresa de recursos humanos, controlando nome, cargo e remuneração salarial no SQLite.

**Conceito utilizado:**  
Lógicas CRUD completas, execução SQL com tuplas e fechamento de conexões físicas.

**Solução:**

```
import sqlite3

# Conectar e criar o cursor
conn = sqlite3.connect("funcionarios.db")
cursor = conn.cursor()

# 1. Criação física da tabela de funcionários
cursor.execute('''
    CREATE TABLE IF NOT EXISTS funcionarios (
        id INTEGER PRIMARY KEY,
        nome TEXT,
        cargo TEXT,
        salario REAL
    )
''')

# 2. CREATE: Insere o funcionário inicial de teste
novo_funcionario = (1, "João", "Analista", 5000.00)
cursor.execute("INSERT INTO funcionarios VALUES (?, ?, ?, ?)", novo_funcionario)
conn.commit()

# 3. READ: Consulta e imprime a tabela de registros
cursor.execute("SELECT * FROM funcionarios")
funcionarios = cursor.fetchall()
print("Funcionários Cadastrados:")
for funcionario in funcionarios:
    print(funcionario)

# 4. UPDATE: Atualiza dados do empregado ID 1
atualizacao = ("João Silva", 5500.00, 1)
cursor.execute("UPDATE funcionarios SET nome = ?, salario = ? WHERE id = ?", atualizacao)
conn.commit()

# 5. DELETE: Remove o registro de pessoal do ID 1
id_para_deletar = 1
cursor.execute("DELETE FROM funcionarios WHERE id = ?", (id_para_deletar,))
conn.commit()

# Encerra processos
cursor.close()
conn.close()
```

**Resultado:**  
Criação, recuperação, atualização e deleção íntegra do cadastro de João no banco `funcionarios.db`.

**Por que essa solução funciona:**  
Os parâmetros contidos no caractere curinga `?` são sanitizados pelo módulo de banco de dados do SQLite, evitando falhas sintáticas ou possíveis injeções de SQL indesejadas.

**O que preciso aprender com esse exemplo:**  
A sanitização de comandos SQL por meio de placeholders `?` é crucial para segurança e robustez no desenvolvimento de banco de dados no ecossistema Python.