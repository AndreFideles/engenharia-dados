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

A DAG é escrita em Python e usa `@task` com o decorador `@dag`. Abaixo uma estrutura simplificada:

```python
from airflow.decorators import dag, task

@dag(...)
def etl():
    for table in tables:
        @task
        def get_max_id(table): ...
        @task
        def load_data(table, max_id): ...
        max_id = get_max_id(table)
        load_data(table, max_id)
```

---

## 🔌 Conexões Utilizadas

As conexões são configuradas no Airflow UI com os seguintes `Connection ID`:

- **PostgreSQL:** `postgres`
- **Snowflake:** `snowflake`

---

## 🛑 Boas Práticas

- `max_active_runs=1` para evitar execuções paralelas indesejadas
- `retries`, `retry_delay` e `catchup=False` para controle confiável
- Tratamento de exceções e validações de qualidade são recomendadas

---

## 📈 Melhorias Futuras

- Transformar em `UPSERT (MERGE)` em vez de carga bruta
- Carga incremental com base em `timestamp`
- Validações com `dbt` ou `Great Expectations`

---

## 📎 Código Fonte da DAG (Airflow 2.8+)

O código completo da DAG `postgres_to_snowflake`, compatível com Airflow 2.8+, está disponível abaixo:

📄 [`postgres_to_snowflake_v2.8.py`](postgres_to_snowflake_v2.8.py)
