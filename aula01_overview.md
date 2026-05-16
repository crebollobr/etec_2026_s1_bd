# Aula 01 — Banco de Dados: Visão Geral da Disciplina

**Componente:** I.8 - Banco de Dados
**Curso:** Técnico em Informática para Internet — Módulo I
**Data:** 21/05/2026 (quinta-feira)
**Duração prevista:** ~100 min (2 h-aula)

---

## Objetivos da aula

Ao final desta aula, o aluno deverá ser capaz de:

- Explicar, com suas próprias palavras, o que é um banco de dados e para que ele serve.
- Diferenciar um banco de dados de uma planilha eletrônica e de um arquivo de texto.
- Identificar o papel de um Sistema Gerenciador de Banco de Dados (SGBD).
- Reconhecer os principais paradigmas de banco de dados existentes no mercado (relacional, NoSQL, colunar) e em qual deles esta disciplina se concentra.
- Executar suas primeiras instruções SQL em um SGBD relacional.

---

## Roteiro

### 1. Acolhimento e combinados (5 min)

- Apresentação do professor.
- Combinados da disciplina:
  - Frequência e pontualidade.
  - Forma de avaliação (a confirmar com o regimento da Etec).
  - Ferramenta principal de trabalho: **MySQL Community Server + MySQL Workbench**.
  - Postura em laboratório: cuidado com equipamentos, foco nas atividades.
- Apresentação rápida da ementa (sem entrar em detalhe — vamos construir junto).

### 2. Avaliação diagnóstica (20 min)

- Aplicação do questionário diagnóstico (ver arquivo separado).
- **Não vale nota.** Serve apenas para o professor entender o ponto de partida da turma.
- Recolher ao final do bloco.

### 3. O que é um Banco de Dados? (15 min)

**Definição construída com a turma:**

> Um banco de dados é uma coleção organizada de informações relacionadas entre si, armazenada de forma que possamos consultar, atualizar e proteger esses dados de maneira eficiente.

**Exemplo concreto — cadastro de alunos da Etec:**

| RA       | Nome              | Curso       | Módulo |
|----------|-------------------|-------------|--------|
| 2024001  | Ana Silva         | Informática | I      |
| 2024002  | Bruno Souza       | Informática | I      |
| 2024003  | Carla Mendes      | Informática | II     |

**Pergunta para a turma:** isso é um banco de dados? Por quê? E uma planilha do Excel com a mesma tabela — também é?

**Diferença essencial:**

| Arquivo .txt | Planilha (Excel) | Banco de Dados |
|---|---|---|
| Texto puro | Dados em linhas/colunas | Dados estruturados |
| Sem regras | Algumas regras (tipos, fórmulas) | Regras rígidas (tipos, chaves, relações) |
| Um usuário por vez | Um usuário por vez (normalmente) | Vários usuários simultâneos |
| Sem busca eficiente | Filtros simples | Consultas complexas e rápidas |
| Sem garantia de integridade | Pouca garantia | **Garante integridade** |

### 4. O SGBD — quem cuida do banco (10 min)

**SGBD (Sistema Gerenciador de Banco de Dados):** o software que fica entre o usuário/aplicação e os dados.

```
[ Usuário / Aplicação ]
          |
          v
       [ SGBD ]   <-- MySQL, PostgreSQL, SQL Server, Oracle...
          |
          v
   [ Dados em disco ]
```

**O que o SGBD faz por nós:**

- **Concorrência:** dezenas de pessoas acessando ao mesmo tempo sem bagunça.
- **Integridade:** impede dados inconsistentes (ex.: um aluno sem nome, uma nota maior que 10).
- **Persistência:** os dados continuam lá mesmo depois que a máquina é desligada.
- **Segurança:** controle de quem pode ver e alterar o quê.
- **Consultas:** linguagem específica (SQL) para perguntar coisas ao banco.

Exemplos de SGBDs que vamos citar: **MySQL** (usaremos), PostgreSQL, Microsoft SQL Server, Oracle, SQLite.

### 5. Tipos de banco de dados — panorama (15 min)

> Hoje só vamos **conhecer** os tipos. O foco da nossa disciplina é o **relacional**.

#### 5.1 Relacional (SQL) — **nosso foco**

- Dados organizados em **tabelas** (linhas e colunas).
- Tabelas se relacionam entre si por chaves.
- Linguagem padrão: **SQL**.
- Exemplos: **MySQL**, PostgreSQL, SQL Server, Oracle, SQLite.
- Onde aparece: sistemas bancários, e-commerce, ERPs, sistemas escolares (incluindo o NSA da Etec).

#### 5.2 NoSQL — "not only SQL"

Surgiu para resolver problemas que o relacional não resolve bem (escala massiva, dados sem formato fixo). Subdivide-se em:

- **Documento:** guarda objetos tipo JSON. Ex.: **MongoDB**. Usado em apps web/mobile modernos.
- **Chave-valor:** super rápido, simples. Ex.: **Redis**. Usado para cache, sessões de login.
- **Grafo:** guarda relações entre coisas. Ex.: **Neo4j**. Usado em redes sociais, sistemas de recomendação.
- **Colunar (wide-column):** Cassandra, HBase. Usado em big data.

#### 5.3 Colunar / Analítico

- Armazena dados por **coluna** em vez de por linha — ótimo para análise de grandes volumes.
- Exemplos: **Google BigQuery**, Amazon Redshift, Snowflake.
- Onde aparece: BI (Business Intelligence), dashboards, análise de dados.

#### Mensagem-chave

> Cada paradigma resolve um problema diferente. O **relacional é a base** — é o mais usado no mercado e o pré-requisito para você entender os outros. Por isso, é onde vamos passar quase toda a disciplina.

### 6. Como se constrói um banco de dados? (10 min)

Três etapas (vamos detalhar nas próximas aulas):

1. **Modelo Conceitual** — diagrama de entidades e relacionamentos (DER). Pensar no mundo real: o que existe? como se relaciona?
   - Ex.: *aluno* faz *matrícula* em *curso*.
2. **Modelo Lógico** — transformar o diagrama em tabelas, colunas e chaves. Aplicar **normalização** (1FN, 2FN, 3FN) para eliminar redundância.
3. **Modelo Físico** — escrever o SQL que cria de fato o banco no SGBD.

> Resumindo: **pensar → desenhar → codar**.

### 7. SQL — a linguagem que vamos dominar (5 min)

SQL = *Structured Query Language*. Padrão da indústria. Divide-se em três famílias principais:

- **DDL** — *Data Definition Language*: cria e altera a estrutura. `CREATE`, `ALTER`, `DROP`.
- **DML** — *Data Manipulation Language*: insere e modifica dados. `INSERT`, `UPDATE`, `DELETE`.
- **DQL** — *Data Query Language*: consulta dados. `SELECT`.

### 8. Mão na massa — primeiro contato com SQL (15 min)

Abrir o **MySQL Workbench** (ou, se o laboratório não estiver pronto, usar o [DB Fiddle](https://www.db-fiddle.com/) online).

**Demonstração ao vivo + reproduzir no computador do aluno:**

```sql
-- Criar um banco de dados
CREATE DATABASE escola;
USE escola;

-- Criar uma tabela
CREATE TABLE aluno (
    ra INT PRIMARY KEY,
    nome VARCHAR(100),
    curso VARCHAR(50)
);

-- Inserir dados
INSERT INTO aluno (ra, nome, curso) VALUES
    (2024001, 'Ana Silva', 'Informatica'),
    (2024002, 'Bruno Souza', 'Informatica'),
    (2024003, 'Carla Mendes', 'Administracao');

-- Consultar
SELECT * FROM aluno;

-- Consultar com filtro
SELECT nome FROM aluno WHERE curso = 'Informatica';
```

**Objetivo do momento:** vencer o medo da ferramenta. Não importa se ainda não entendem cada comando — vão entender ao longo do curso.

### 9. Fechamento (5 min)

Recapitular em 3 frases:

1. Banco de dados é uma forma estruturada de guardar e consultar informação.
2. Existem vários tipos, mas o **relacional** é a base e é o nosso foco.
3. SQL é a linguagem que usa para conversar com o banco — e hoje vocês já escreveram as primeiras linhas.

**Próxima aula:** Modelagem conceitual — Diagrama Entidade-Relacionamento (DER).

**Tarefa de casa (opcional):** instalar o MySQL Community + Workbench no computador de casa (passo a passo será compartilhado).

---

## Materiais necessários

- Projetor.
- Computadores com MySQL Workbench instalado (ou acesso à internet para DB Fiddle).
- Cópias impressas da avaliação diagnóstica (uma por aluno).
- Quadro / lousa.

## Vínculo com o plano de curso

Esta aula introduz, em panorama, as **bases tecnológicas** do componente **I.8 - Banco de Dados** previstas no Plano de Curso 819 do Centro Paula Souza:

- Sistemas Gerenciadores de Bancos de Dados (SGBDR).
- Arquitetura cliente/servidor.
- Linguagem SQL (DDL, DML, DQL).
- Modelagem relacional.

Os tópicos de NoSQL e bancos colunares são apresentados apenas como contexto de mercado e não compõem as bases tecnológicas avaliadas.
