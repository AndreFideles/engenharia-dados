# 🛠️ Criação da DAG e Carregamento de Dados para o Snowflake

Esta etapa descreve a criação da DAG no Airflow para orquestrar o processo de carga de dados do PostgreSQL para o Snowflake no projeto NovaDrive Motors.

---

## 💡 Conceitos-Chave

### ETL vs ELT

- **ETL (Extract, Transform, Load):**
  Transformações ocorrem antes da carga no destino.
- **ELT (Extract, Load, Transform):**
  Dados brutos são carregados primeiro no destino (Snowflake), e transformações ocorrem lá.

> O modelo utilizado neste projeto segue a abordagem **ELT**, aproveitando a capacidade de processamento do Snowflake para transformação posterior.

---

## 🔄 Estratégias de Carga

- **Carga Incremental por ID**:
  - Cada tabela carrega apenas os registros com `id > max_id` no destino.
- **Execução em Paralelo por Tabela**:
  - Cada tabela possui duas tasks:
    - `get_max_id_<tabela>`
    - `load_data_<tabela>`

---

## ⚙️ Estrutura da DAG

A DAG é escrita em Python e usa `PythonOperator`. Abaixo um exemplo da estrutura simplificada:

```python
from airflow import DAG
from airflow.operators.python_operator import PythonOperator

with DAG("etl_novadrive", ...) as dag:
    for table in ["veiculos", "vendedores", "vendas"]:
        get_max = PythonOperator(task_id=f"get_max_id_{table}", python_callable=...)
        load = PythonOperator(task_id=f"load_data_{table}", python_callable=...)
        get_max >> load
```

---

## 🔌 Conexões Utilizadas

As conexões foram previamente configuradas no Airflow e referenciadas por seus respectivos **Connection IDs**.

### PostgreSQL

| Campo         | Valor de Exemplo         |
|---------------|--------------------------|
| Connection Id | `postgres`               |
| Host          | (personalizado)          |
| Database      | `novadrive`              |
| Login         | (personalizado)          |
| Password      | (personalizado)          |
| Port          | `5432`                   |

### Snowflake

| Campo         | Valor de Exemplo         |
|---------------|--------------------------|
| Connection Id | `snowflake`              |
| Account       | (personalizado)          |
| Database      | `NOVADRIVE`              |
| Schema        | `STAGE`                  |
| Warehouse     | `DEFAULT_WH`             |
| Login         | (personalizado)          |

> 🔒 As credenciais exatas utilizadas para conectar ao banco de dados foram substituídas por valores genéricos por questões de segurança.

---

## 🛑 Boas Práticas e Prevenção de Erros

- **Falhas de conexão**: usar `retries` e `retry_delay` nos Operators.
- **Concorrência acidental**: definir `max_active_runs=1` para evitar DAGs paralelas.
- **Carga incompleta**: implementar controle de transação (tudo ou nada).
- **Qualidade de Dados**: implementar validações pós-carga com `pytest` ou queries SQL.

---

## 📈 Melhoria Contínua

- Substituir incremental por **UPSERT** (`MERGE`) para garantir consistência de dados.
- Avaliar uso de `timestamp` ao invés de `id` como critério de carga.
- Incorporar testes de qualidade via `dbt`.

---

> ✅ Este processo representa a orquestração automatizada da carga de dados transacionais para o Snowflake, utilizando Airflow com conexão a banco PostgreSQL.