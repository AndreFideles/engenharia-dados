# 5. dbt - Transformações e Modelagem de Dados

Este módulo documenta a implementação de um projeto **dbt (data build tool)** que transforma e modela os dados carregados no Snowflake. O objetivo é organizar os dados brutos da camada `STAGE` em estruturas analíticas otimizadas, seguindo boas práticas de engenharia de dados.

---

## 📐 Estrutura do Projeto

```
5-dbt/
├── README.md
├── models/
│   ├── staging/
│   │   ├── stg_clientes.sql
│   │   ├── stg_cidades.sql
│   │   ├── stg_concessionarias.sql
│   ├── dimensions/
│   │   ├── dim_clientes.sql
│   │   ├── dim_cidades.sql
│   │   ├── dim_concessionarias.sql
│   │   ├── dim_estados.sql
│   │   ├── dim_veiculos.sql
│   │   ├── dim_vendedores.sql
│   ├── facts/
│   │   └── fct_vendas.sql
```

---

## 🧠 Etapas Realizadas

- Criação dos modelos *staging* para padronizar nomes, tipos e estruturas dos dados.
- Construção das tabelas de **dimensões** com dados enriquecidos e relacionados.
- Modelagem da **tabela fato** `fct_vendas` contendo as principais métricas da operação.
- Utilização de `ref()` e `source()` para garantir rastreabilidade entre modelos.
- Execução via `dbt run` e geração da documentação com `dbt docs generate`.

---

## 🧪 Testes e Validações

- Aplicação de *unique* e *not null* em chaves primárias das dimensões.
- Garantia de integridade referencial entre fatos e dimensões via testes de relacionamento.

---

## 🔄 Ambientes e Branches

- Desenvolvimento: feito em branches isoladas por desenvolvedor.
- Deploy: realizado a partir da branch `main`, criando os objetos no schema oficial.
- Ambientes separados (dev, staging, prod) com schemas distintos no Snowflake.

---

## 🧰 Tecnologias Utilizadas

- dbt Cloud (IDE)
- Jinja Templates
- SQL (Snowflake SQL)
- Snowflake como Data Warehouse

---

📎 *Este projeto segue as práticas recomendadas de modelagem dimensional para construção de um Data Warehouse robusto, escalável e documentado.*
