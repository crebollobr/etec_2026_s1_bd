# Aula de SQL — MySQL

**Duração:** ~2 horas
**Banco:** MySQL
**Objetivo:** entender o que é SQL e praticar os comandos mais usados para criar, consultar e modificar dados.

---

## Roteiro

1. O que é SQL
2. Por que SQL
3. Categorias de comandos (DDL, DML, DQL)
4. Prática: criar banco, tabela, inserir, consultar, atualizar, alterar estrutura, deletar
5. Limpeza do ambiente (`DROP`)
6. Atividade prática (enviar comandos por e-mail)

---

## 1. O que é SQL

**SQL** = *Structured Query Language* (Linguagem Estruturada de Consulta).

- É a linguagem padrão para se comunicar com **bancos de dados relacionais** (MySQL, PostgreSQL, SQL Server, Oracle, SQLite, ...).
- Foi criada nos anos 1970 pela IBM e padronizada pela ANSI/ISO.
- Cada banco tem pequenas variações ("dialetos"), mas o núcleo é o mesmo.

Em um banco relacional os dados ficam organizados em **tabelas** (linhas e colunas), como uma planilha — só que muito mais poderosa.

---

## 2. Por que SQL

- **Onipresente:** praticamente todo sistema corporativo usa um banco relacional em algum lugar.
- **Declarativa:** você diz *o que* quer, não *como* obter — o banco se encarrega da estratégia.
- **Padronizada:** o que você aprende em MySQL serve com pequenas adaptações em quase qualquer outro banco.
- **Indispensável** para áreas de TI, dados, BI, analytics, back-end, devops, segurança, auditoria etc.
- **Performance e integridade:** bancos relacionais oferecem transações (ACID), índices, constraints — garantias que dificilmente se constrói "na mão".

---

## 3. Categorias de comandos SQL

Os comandos SQL são agrupados em famílias. As três principais para a aula de hoje:

| Sigla   | Nome                          | Para que serve                                                          | Exemplos                            |
| ------- | ----------------------------- | ----------------------------------------------------------------------- | ----------------------------------- |
| **DDL** | *Data Definition Language*    | Definir/alterar a **estrutura** dos objetos (bancos, tabelas, colunas) | `CREATE`, `ALTER`, `DROP`, `TRUNCATE` |
| **DML** | *Data Manipulation Language*  | Manipular os **dados** dentro das tabelas                              | `INSERT`, `UPDATE`, `DELETE`        |
| **DQL** | *Data Query Language*         | **Consultar** dados                                                    | `SELECT`                            |

Existem ainda **DCL** (`GRANT`, `REVOKE` — permissões) e **TCL** (`COMMIT`, `ROLLBACK` — transações), que ficam para uma próxima aula.

> 💡 **Dica didática:** quando você for digitar um comando, tente identificar a qual categoria ele pertence. Isso ajuda a fixar o conceito.

---

## 4. DDL — Criando o banco de dados

**Convenção da aula:** `nome_sobrenome_AAAAMMDD` — assim cada aluno fica com seu próprio banco isolado.

Exemplo: `joao_silva_20260528`

```sql
CREATE DATABASE nome_sobrenome_20260528;
```

```sql
USE nome_sobrenome_20260528;
```

> `USE` diz ao MySQL: "a partir de agora, todos os comandos vão atuar nesse banco".

Para conferir os bancos existentes:

```sql
SHOW DATABASES;
```

---

## 5. DDL — Criando uma tabela

Vamos criar a tabela `pessoa` com 4 colunas.

Conceitos novos:

- **Tipo de dado:** cada coluna tem um tipo (número, texto, data...).
- **PRIMARY KEY:** coluna que identifica unicamente cada linha (não pode repetir nem ser nula).
- **AUTO_INCREMENT:** o próprio MySQL gera o `id` sequencialmente.
- **NOT NULL:** a coluna é obrigatória.
- **UNIQUE:** o valor não pode se repetir (CPF é um bom candidato).

Principais tipos de dados do MySQL que vamos usar:

| Tipo            | Para que serve                                                       |
| --------------- | -------------------------------------------------------------------- |
| `INT`           | Números inteiros                                                     |
| `VARCHAR(n)`    | Texto de tamanho variável até `n` caracteres                         |
| `CHAR(n)`       | Texto de tamanho fixo (bom para CPF, que sempre tem 11 dígitos)      |
| `DATE`          | Data (formato `AAAA-MM-DD`)                                          |
| `DATETIME`      | Data e hora                                                          |
| `DECIMAL(p,s)`  | Número com casas decimais (bom para dinheiro)                        |

```sql
CREATE TABLE pessoa (
    id              INT AUTO_INCREMENT PRIMARY KEY,
    nome            VARCHAR(100) NOT NULL,
    cpf             CHAR(11)     NOT NULL UNIQUE,
    data_nascimento DATE
);
```

```sql
DESCRIBE pessoa;
```

> `DESCRIBE` (ou `DESC`) mostra a estrutura da tabela — colunas, tipos e restrições.

---

## 6. DML — Inserindo dados (`INSERT`)

Sintaxe básica:

```sql
INSERT INTO tabela (col1, col2, ...) VALUES (val1, val2, ...);
```

Repare:

- Não passamos o `id` — o `AUTO_INCREMENT` cuida dele.
- Texto vai entre aspas simples (`'...'`).
- Data no formato `AAAA-MM-DD`.

```sql
INSERT INTO pessoa (nome, cpf, data_nascimento) VALUES ('Ana Silva',   '12345678901', '1990-03-15');
INSERT INTO pessoa (nome, cpf, data_nascimento) VALUES ('Bruno Souza', '23456789012', '1985-07-22');
INSERT INTO pessoa (nome, cpf, data_nascimento) VALUES ('Carla Lima',  '34567890123', '1995-11-30');
```

---

## 7. DQL — Consultando dados (`SELECT`)

O comando **mais usado** de SQL no dia a dia.

Forma geral:

```sql
SELECT   <colunas>
FROM     <tabela>
WHERE    <filtro>
ORDER BY <coluna>;
```

```sql
-- Todas as colunas, todas as linhas
SELECT * FROM pessoa;
```

```sql
-- Só as colunas que interessam
SELECT nome, data_nascimento FROM pessoa;
```

```sql
-- Filtrando com WHERE
SELECT * FROM pessoa WHERE nome = 'Ana Silva';
```

```sql
-- Operadores de comparação funcionam também em datas
SELECT nome, data_nascimento
FROM   pessoa
WHERE  data_nascimento > '1990-01-01'
ORDER BY data_nascimento;
```

---

## 8. DML — Atualizando dados (`UPDATE`)

> ⚠️ **Cuidado:** `UPDATE` sem `WHERE` altera **todas as linhas** da tabela.
> Sempre confirme o filtro antes com um `SELECT`.

```sql
-- 1) Confere quem é id = 1
SELECT * FROM pessoa WHERE id = 1;
```

```sql
-- 2) Atualiza o nome
UPDATE pessoa
SET    nome = 'Ana Silva Santos'
WHERE  id = 1;
```

```sql
-- 3) Confere o resultado
SELECT * FROM pessoa WHERE id = 1;
```

---

## 9. DDL — Alterando a estrutura da tabela (`ALTER TABLE`)

E se descobrirmos depois que faltou uma coluna? Não precisamos recriar a tabela — usamos `ALTER TABLE`.

Vamos adicionar a coluna **`rg`**:

```sql
ALTER TABLE pessoa ADD COLUMN rg VARCHAR(20);
```

```sql
-- A coluna apareceu, mas com valor NULL nas linhas existentes
SELECT * FROM pessoa;
```

```sql
-- Preenchendo o rg de uma pessoa específica
UPDATE pessoa SET rg = '12.345.678-9' WHERE id = 1;
UPDATE pessoa SET rg = '23.456.789-0' WHERE id = 2;
```

```sql
SELECT * FROM pessoa;
```

Outras variações úteis do `ALTER TABLE` (para conhecimento, não vamos rodar todas):

```sql
ALTER TABLE pessoa DROP COLUMN rg;                       -- remove coluna
ALTER TABLE pessoa MODIFY COLUMN nome VARCHAR(150);      -- muda tipo/tamanho
ALTER TABLE pessoa RENAME COLUMN nome TO nome_completo;  -- renomeia coluna
ALTER TABLE pessoa RENAME TO cliente;                    -- renomeia a tabela
```

---

## 10. DML — Removendo linhas (`DELETE`)

> ⚠️ Mesmo cuidado do `UPDATE`: **`DELETE` sem `WHERE` apaga tudo**.
> Confira sempre com um `SELECT` antes.

```sql
-- 1) Verifica quem vai ser apagado
SELECT * FROM pessoa WHERE id = 3;
```

```sql
-- 2) Apaga
DELETE FROM pessoa WHERE id = 3;
```

```sql
-- 3) Confere
SELECT * FROM pessoa;
```

---

## 11. Limpando o ambiente — `DROP`

No fim da aula, vamos remover a tabela e o banco para não deixar resíduo.

- `DROP TABLE` → apaga a tabela e todos os seus dados.
- `DROP DATABASE` → apaga o banco inteiro com todas as tabelas.

> ⚠️ Operações **irreversíveis**. Em produção, pense duas vezes.

```sql
DROP TABLE pessoa;
```

```sql
DROP DATABASE nome_sobrenome_20260528;
```

---

## 12. Atividade prática

**Tarefa:** envie por e-mail um arquivo `.sql` (ou o corpo do e-mail) contendo a sequência de comandos abaixo, **executada no seu próprio banco** `seu_nome_sobrenome_20260528`.

1. `CREATE DATABASE` com seu nome + data.
2. `USE` do banco que você criou.
3. `CREATE TABLE pessoa` com `id`, `nome`, `cpf`, `data_nascimento`.
4. **3 `INSERT`s** com dados fictícios (pode ser personagens, colegas etc.).
5. Um `SELECT *` mostrando os 3 registros.
6. Um `UPDATE` alterando o nome de uma das pessoas + `SELECT` para confirmar.
7. Um `ALTER TABLE` adicionando a coluna **`rg VARCHAR(20)`**.
8. Um `UPDATE` preenchendo o `rg` de pelo menos uma pessoa + `SELECT` para confirmar.
9. Um `DELETE` removendo uma das pessoas + `SELECT` final.
10. `DROP TABLE pessoa;`
11. `DROP DATABASE seu_nome_sobrenome_20260528;`

**Entrega:**

- E-mail para: *(preencher endereço do professor)*
- Assunto: `Atividade SQL - Seu Nome`
- Anexo ou corpo: o `.sql` com **todos** os comandos na ordem.

**Dica:** se algum comando falhar, leia a mensagem de erro com calma — o MySQL costuma indicar a linha e o motivo (coluna inexistente, aspas faltando, vírgula sobrando etc.).

---

## 13. Resumo da aula

| Comando                          | Categoria | Para que serve                              |
| -------------------------------- | --------- | ------------------------------------------- |
| `CREATE DATABASE`                | DDL       | Criar banco                                 |
| `USE`                            | —         | Selecionar banco atual                      |
| `CREATE TABLE`                   | DDL       | Criar tabela                                |
| `ALTER TABLE`                    | DDL       | Alterar estrutura (ex.: `ADD COLUMN`)       |
| `DROP TABLE` / `DROP DATABASE`   | DDL       | Apagar tabela / banco                       |
| `INSERT INTO`                    | DML       | Inserir linhas                              |
| `UPDATE`                         | DML       | Alterar linhas                              |
| `DELETE`                         | DML       | Remover linhas                              |
| `SELECT`                         | DQL       | Consultar dados                             |

**Boas práticas que ficam:**

1. Sempre `SELECT` antes de `UPDATE`/`DELETE` para conferir o filtro.
2. Use `WHERE` — quase nunca queremos afetar a tabela inteira.
3. Limpe o ambiente quando o trabalho terminar (`DROP`).
4. Nomeie objetos com clareza (`pessoa`, `cliente`, `pedido`...).
5. Leia as mensagens de erro — elas dizem onde está o problema.
