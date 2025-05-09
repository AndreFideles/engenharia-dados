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
```

---

## 🚀 Como Executar o Projeto

> Pré-requisitos:
> - Docker
> - Conta gratuita no [Snowflake](https://signup.snowflake.com/)
> - Python 3.9+
> - Conta Google para o Looker Studio

### Etapas resumidas:

1. Clone o repositório  
   `git clone https://github.com/AndreFideles/engenharia-dados.git`

2. Execute o Airflow com Docker  
   Navegue até a pasta `3-airflow` e rode:  
   `docker-compose up -d`

3. Configure o Snowflake e o dbt  
   Siga os tutoriais disponíveis nas pastas `4-snowflake` e `5-dbt`

4. Gere o dashboard no Looker Studio  
   Veja os exemplos e prints na pasta `6-dashboard_looker`

---

## 📊 Resultado Esperado

- Dados atualizados em tempo real no Snowflake
- Modelos transformados com dbt
- Dashboard interativo com KPIs e gráficos relevantes

---

## 🧠 Aprendizados do Projeto

- Criação de pipelines reais de dados
- Conceitos de Data Warehouse e modelagem dimensional
- Automação com Airflow e versionamento com dbt
- Integração entre ferramentas de ponta no ecossistema de dados

---

## 📎 Licença

Este projeto está licenciado sob a [MIT License](LICENSE).

---

📚 **Créditos e Referência:**

Este projeto foi desenvolvido com base no curso [Engenharia de Dados: Construa um Projeto Real](https://www.udemy.com/course/engenharia-de-dados-projeto-real/) disponível na Udemy, ministrado por Fernando Amaral.

Todo o conteúdo aqui foi adaptado e reestruturado para fins de aprendizado, prática e portfólio pessoal.

---

**Desenvolvido por André Fideles 🚀**
