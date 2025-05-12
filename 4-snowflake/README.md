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
---

## ⚠️ Possíveis Problemas e Melhorias

Durante a execução da DAG de carga entre PostgreSQL e Snowflake, alguns pontos críticos foram identificados:

### 1. ❌ Interrupções na Carga de Dados
Se o Snowflake ficar temporariamente indisponível durante o processo de carga, pode ocorrer uma **carga parcial ou inconsistente**.

**💡 Solução:** Implementar controle de transações com comandos como `BEGIN TRANSACTION`, `COMMIT` e `ROLLBACK` dentro das operações no Snowflake.

---

### 2. 🔁 Execuções Simultâneas da DAG
Execuções paralelas da mesma DAG podem causar **duplicidade de dados**.

**💡 Soluções:**
- Definir `max_active_runs=1` na DAG para garantir execução única por agendamento.
- Utilizar `MERGE` (UPSERT) em vez de `INSERT`, assegurando que registros duplicados não sejam inseridos caso já existam.

---

### 3. 🔌 Falha na Conexão com o Banco de Dados
Problemas temporários de rede ou conexão podem causar falhas esporádicas na DAG.

**💡 Soluções:**
- Definir `retries=3` e `retry_delay=timedelta(minutes=5)` para garantir reexecução automática.
- Monitorar logs e notificações de falha com `email_on_failure`.

---

### 4. ✅ Validação da Qualidade dos Dados
É fundamental garantir que os dados carregados estejam íntegros e consistentes.

**💡 Estratégias:**
- Testes de conformidade com `pytest`, `dbt tests` ou validações via SQL.
- Verificação de `nulls`, `chaves duplicadas`, e `tipos de dados inconsistentes`.

---

Essas práticas aumentam a **resiliência, segurança e confiabilidade** do pipeline de dados da NovaDrive.
