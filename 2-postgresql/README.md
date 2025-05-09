# 🗄️ Seção 2 – Explorando Dados da NovaDrive Motors (PostgreSQL)

Nesta etapa do projeto, exploramos o banco de dados transacional da NovaDrive Motors, que simula um **sistema de vendas utilizado por concessionárias**. O objetivo é entender a estrutura das tabelas, relacionamentos e os dados disponíveis para planejamento da modelagem no Data Warehouse.

---

## 🏢 Sobre o Sistema de Vendas

O sistema representa o ambiente de vendas da montadora, com registros como:

- Clientes
- Vendas
- Veículos
- Modelos
- Concessionárias
- Tabelas auxiliares (status, formas de pagamento, regiões etc.)

Esses dados são armazenados em um banco de dados relacional PostgreSQL, que serve como **fonte primária para o pipeline de dados**.

---

## 🔎 Objetivos da Seção

- Conectar ao banco PostgreSQL usando o **PgAdmin**
- Explorar tabelas e colunas disponíveis
- Identificar **relacionamentos entre entidades**
- Compreender os dados que serão carregados no Snowflake
- Criar scripts de consulta exploratória para análise inicial

---

## 🧱 Exemplo de Estrutura de Tabelas

> A estrutura pode variar conforme o curso, mas normalmente temos:

- `clientes (id, nome, email, data_nascimento, genero, cidade_id)`
- `vendas (id, cliente_id, veiculo_id, data_venda, valor, forma_pagamento_id)`
- `veiculos (id, modelo_id, ano_fabricacao, cor, chassi)`
- `modelos (id, nome_modelo, fabricante_id)`
- `concessionarias (id, nome, cidade_id)`
- `formas_pagamento (id, descricao)`
- `cidades (id, nome, estado)`

---

## 🛠️ Ferramentas Utilizadas

- **PostgreSQL**: banco de dados relacional
- **PgAdmin 4**: interface para navegação e execução de queries
- **SQL**: para explorar e consultar os dados

---

## 💡 Insights da Análise Exploratória

Durante a análise exploratória, buscamos responder perguntas como:

- Quais são os modelos de veículos mais vendidos?
- Quais concessionárias mais faturam?
- Qual o perfil dos clientes (gênero, localização)?
- Quais formas de pagamento são mais usadas?

Essas perguntas ajudarão a guiar a modelagem dimensional futura com dbt e Snowflake.

---

## 📂 Arquivos nesta pasta

| Arquivo                            | Descrição                                        |
|------------------------------------|--------------------------------------------------|
| `estrutura_banco.sql`              | Script com o `CREATE TABLE` das principais tabelas |
| `consultas_exploratorias.sql`      | Consultas com `JOIN`, `GROUP BY`, filtros, etc.   |

---

📚 **Referência**: Baseado no curso [Engenharia de Dados: Construa um Projeto Real](https://www.udemy.com/course/engenharia-de-dados-projeto-real/) da Udemy.

