# Avaliação Diagnóstica — Banco de Dados

**Aluno:**
**Data:**

---

## Instruções

- Responda este e-mail copiando cada pergunta e escrevendo a resposta logo abaixo.
- Nas questões de múltipla escolha, indique a letra (ex.: `Resposta: b`).
- Nas questões de SQL, escreva o comando exatamente como o digitaria no MySQL Workbench.
- **Não consulte material, internet ou colega.**
- **Esta avaliação não vale nota.** O objetivo é verificar o que já está consolidado e o que ainda precisa ser trabalhado.
- Se não souber responder alguma questão, escreva `não sei`. É uma resposta válida.

---

## Parte 1 — Conceitos

**1.** O que é uma **chave primária** em uma tabela?

a) Uma senha que protege o banco de dados.
b) Um campo que identifica de forma única cada linha da tabela.
c) A primeira coluna de qualquer tabela.
d) Um campo que sempre contém números inteiros.

**2.** Considere a tabela `matricula(id, aluno_ra, curso_id)`. O campo `aluno_ra` aponta para a tabela `aluno`. Esse campo é:

a) Chave primária.
b) Chave estrangeira.
c) Índice único.
d) Atributo derivado.

**3.** Qual das opções abaixo **NÃO** é um Sistema Gerenciador de Banco de Dados?

a) MySQL
b) PostgreSQL
c) Microsoft Excel
d) SQL Server

**4.** O que significa a sigla **SQL**?

**5.** Em uma frase, explique o que é uma **tabela** em um banco de dados relacional.

**6.** Em um diagrama Entidade-Relacionamento (DER), o que normalmente um **retângulo** representa?

a) Um atributo.
b) Um relacionamento.
c) Uma entidade.
d) Uma chave estrangeira.

---

## Parte 2 — SQL: escreva os comandos

Considere a tabela `aluno` com as seguintes colunas:

| Coluna | Tipo          |
|--------|---------------|
| ra     | INT           |
| nome   | VARCHAR(100)  |
| curso  | VARCHAR(50)   |
| nota   | DECIMAL(4,2)  |

**7.** Escreva o comando SQL que retorna **todos os dados** da tabela `aluno`.

**8.** Escreva o comando SQL que retorna **apenas o nome** dos alunos do curso `'Informatica'`.

**9.** Escreva o comando SQL que retorna os alunos com `nota` **maior que 7**.

**10.** Escreva o comando SQL que retorna os alunos **ordenados pelo nome em ordem alfabética**.

**11.** Escreva o comando SQL que **insere** um aluno com: ra `2024010`, nome `'João Pereira'`, curso `'Informatica'`, nota `8.5`.

**12.** Escreva o comando SQL que **atualiza** a nota do aluno de ra `2024001` para `9.0`.

**13.** Escreva o comando SQL que **remove** todos os alunos do curso `'Administracao'`.

**14.** Escreva o comando SQL que **cria** a tabela `aluno` com as colunas descritas acima, definindo `ra` como chave primária.

---

## Parte 3 — SQL: interpretar

Para cada comando abaixo, explique em uma frase **o que ele faz**.

**15.**
```sql
SELECT COUNT(*) FROM aluno WHERE curso = 'Informatica';
```

**16.**
```sql
SELECT curso, AVG(nota) FROM aluno GROUP BY curso;
```

**17.**
```sql
SELECT a.nome, c.titulo
FROM aluno a
JOIN curso c ON a.curso_id = c.id;
```

---

## Parte 4 — Autoavaliação

Em uma escala de **0 a 10**:

**18.** Qual sua confiança em escrever um `SELECT` com `WHERE` sem consultar material?

**19.** Qual sua confiança em criar uma tabela com SQL (`CREATE TABLE`)?

**20.** Qual sua confiança em desenhar um diagrama Entidade-Relacionamento a partir de uma situação descrita em texto?
