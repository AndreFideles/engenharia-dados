# 🧱 Projeto dbt – NovaDrive Motors

Este diretório contém o projeto de transformação de dados utilizando `dbt` (Data Build Tool) para a camada analítica do Data Warehouse da NovaDrive Motors.

---

## 🎯 Objetivo

Transformar os dados brutos carregados no Snowflake em modelos analíticos limpos, confiáveis e reutilizáveis, organizados em camadas:

```
Stage → Dimensões → Fatos → Análises
```

---

## 🧬 Estrutura do Projeto

```
dbt_project/
├── models/
│   ├── stage/
│   ├── dim/
│   ├── fct/
│   └── analysis/
├── macros/
├── tests/
├── dbt_project.yml
└── profiles.yml
```

- **Stage:** dados brutos replicados (ex: `stg_clientes`)
- **Dimensões:** entidades descritivas (ex: `dim_clientes`, `dim_veiculos`)
- **Fatos:** eventos transacionais (ex: `fct_vendas`)
- **Análises:** visões agregadas e analíticas (ex: `vw_vendas_mensais`)

---

## 🔄 Materializações (Materializations)

| Tipo        | Descrição |
|-------------|-----------|
| `view`      | Executado em tempo de consulta |
| `table`     | Persistido no banco ao ser criado |
| `incremental` | Atualiza com novos dados, mantendo o histórico |
| `ephemeral` | Substituído inline durante execução; não gera objeto |

Exemplo de configuração:
```jinja
{{ config(materialized='incremental', unique_key='venda_id') }}
```

---

## 🔗 Referências entre modelos

O dbt utiliza o sistema de templating `Jinja` para conectar modelos entre si:

- **Referência interna com `ref()`**:
```sql
SELECT * FROM {{ ref('stg_clientes') }}
```

- **Referência externa com `source()`**:
```sql
SELECT * FROM {{ source('sources', 'clientes') }}
```

Essas funções garantem a rastreabilidade, verificação de dependências e geração automática de documentação.

---

## 📐 Naming Convention

Cada arquivo `.sql` do projeto gera uma tabela ou view com **o mesmo nome do arquivo**, a não ser que seja especificado um `alias:`.

---

## 🧪 Testes e Validações

Testes foram implementados para garantir:

- Consistência entre preço pago e preço sugerido
- Identificação de registros incompletos ou duplicados

Exemplo de teste SQL:
```sql
SELECT venda_id
FROM fct_vendas v
JOIN dim_veiculos d ON v.veiculo_id = d.veiculo_id
WHERE v.valor_venda < d.valor_sugerido * 0.95
```

---

## 📈 Documentação e Lineage

Para gerar e visualizar a documentação:

```bash
dbt docs generate
dbt docs serve
```

A interface apresenta:
- Modelos com descrições
- Conexões entre tabelas (`ref`, `source`)
- Dependências
- Camadas do pipeline de dados

---

## 🛠️ Principais Comandos dbt

```bash
dbt init                        # Inicializa projeto
dbt run                         # Executa todos os modelos
dbt run --models dim_clientes   # Executa modelo específico
dbt test                        # Executa testes definidos
dbt docs generate && dbt docs serve  # Gera e abre documentação web
```

---

## 🔐 Ambientes

- **dev:** usado localmente por desenvolvedores
- **prod:** utilizado em execução automatizada por Airflow

---

## 📌 Observações

- Todas as tabelas finais são criadas no schema `analytics` no Snowflake
- O projeto segue boas práticas de modularização, reutilização e versionamento
- A execução do dbt será orquestrada por uma DAG do Airflow no módulo posterior

---

📄 Este projeto representa a etapa de transformação e modelagem do pipeline ELT da NovaDrive Motors usando o dbt com Snowflake.
