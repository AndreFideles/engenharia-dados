# ❄️ Snowflake

Nesta seção, exploramos o uso do Snowflake como data warehouse na nuvem para o projeto de engenharia de dados da **NovaDrive Motors**.

---

## 📂 Conteúdo

| Arquivo | Descrição |
|--------|-----------|
| [`snowflake_intro.md`](snowflake_intro.md) | Introdução técnica ao Snowflake |
| [`novadrive_snowflake_estrutura.sql`](novadrive_snowflake_estrutura.sql) | Script SQL com estrutura das tabelas no Snowflake |
| [`dag_carregamento_snowflake.md`](dag_carregamento_snowflake.md) | Explicação da DAG para carga incremental de dados |
| [`postgres_to_snowflake_v2.8.py`](postgres_to_snowflake_v2.8.py) | Código da DAG (compatível com Airflow 2.8+) |

---

## 🚀 Visão Geral

- Integração entre PostgreSQL → Snowflake via Airflow
- Modelo **ELT** com carga incremental
- DAG com tarefas dinâmicas paralelas por tabela

---

## 🛠️ Tecnologias Utilizadas

- Airflow 2.8+
- Snowflake
- Docker (para orquestração local)
- PostgreSQL (base de origem)

---

## 📌 Observações

- Para rodar a DAG, certifique-se de configurar corretamente os `Connection IDs` no Airflow:
  - `postgres` → conexão com o banco de origem
  - `snowflake` → conexão com o data warehouse Snowflake

---

## 📈 Melhorias Futuras

- Validação dos dados com dbt ou Great Expectations
- Substituir `INSERT` por `MERGE` (UPSERT)
- Adicionar controle de qualidade e monitoramento de pipeline

---

[🔝 Voltar ao Repositório Principal](../README.md)
