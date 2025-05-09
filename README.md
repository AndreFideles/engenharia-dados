# 🚗 Engenharia de Dados: Projeto Real com Data Warehouse

Este projeto é baseado em um bootcamp prático onde construímos, passo a passo, uma solução completa de engenharia de dados para uma **montadora de veículos fictícia**, com dados gerados em tempo real.

Ao longo do projeto, utilizamos tecnologias amplamente aplicadas no mercado como **PostgreSQL, Airflow, dbt, Snowflake** e **Looker Studio**, simulando um pipeline moderno de dados de ponta a ponta.

---

## 📌 Objetivo do Projeto

Criar um pipeline completo de engenharia de dados, do banco transacional até o dashboard, com foco em:

- Extração de dados em tempo real
- Automação de cargas com Airflow
- Modelagem e transformação com dbt
- Armazenamento em nuvem com Snowflake
- Visualização com Looker Studio

---

## 🧰 Tecnologias e Ferramentas

| Ferramenta        | Finalidade                                       |
|-------------------|--------------------------------------------------|
| **PostgreSQL**     | Banco de dados de origem                        |
| **Airflow**        | Orquestração de ETL                             |
| **dbt**            | Transformações e modelagem no Data Warehouse    |
| **Snowflake**      | Armazenamento e processamento em nuvem          |
| **Looker Studio**  | Criação de dashboards e visualizações           |
| **Python**         | Scripts e automações auxiliares                 |
| **Docker**         | Ambientes isolados e reprodutíveis              |

---

## 📂 Estrutura do Repositório

```bash
engenharia-dados/
├── 1-introducao/                  # Conceitos iniciais e arquitetura do projeto
├── 2-postgresql/                  # Exploração e estrutura do banco de origem
├── 3-airflow/                     # DAGs e configuração do Airflow
├── 4-snowflake/                   # Scripts de estruturação no Snowflake
├── 5-dbt/                         # Projeto dbt com transformações e testes
├── 6-dashboard_looker/           # Prints e link do dashboard no Looker
├── dados_exemplo/                # Dados simulados utilizados no projeto
└── README.md                     # Descrição geral do projeto


---

📚 **Créditos e Referência:**

Este projeto foi desenvolvido com base no [Bootcamp Engenharia de Dados: Construa um Projeto Real](https://www.udemy.com/course/bootcamp-engenharia-de-dados) disponível na Udemy, ministrado por Fernando Amaral.

Todo o conteúdo aqui foi adaptado e reestruturado para fins de aprendizado, prática e portfólio pessoal.

