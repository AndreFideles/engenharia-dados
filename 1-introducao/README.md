# 📘 Seção 1 – Introdução ao Projeto de Engenharia de Dados

Esta seção apresenta o contexto e a motivação do projeto realizado durante o bootcamp, que simula um ambiente real de engenharia de dados em uma montadora fictícia chamada **NovaDrive Motors**. O objetivo é desenvolver um pipeline completo de dados, do banco transacional até o dashboard analítico.

---

## 🚗 Sobre a NovaDrive Motors

A NovaDrive Motors é uma montadora fictícia com base de dados de vendas ativas. O projeto simula sua operação com:

- Um banco de dados de vendas em tempo real
- Um ambiente analítico para gerar relatórios e dashboards
- Desafios reais enfrentados por engenheiros de dados

---

## 👨‍💻 Papel do Engenheiro de Dados

Durante o bootcamp, você assume o papel de **Engenheiro de Dados da área de vendas** da NovaDrive. Sua principal missão é:

- **Construir um Data Warehouse (DW)** confiável
- **Fornecer dados prontos para análise** por gestores
- Automatizar e orquestrar os processos de ingestão, transformação e entrega dos dados

---

## 🏗️ Arquitetura Geral do Projeto

O pipeline será construído utilizando ferramentas de mercado:

| Ferramenta     | Função no projeto                                         |
|----------------|-----------------------------------------------------------|
| **PostgreSQL** | Banco relacional de origem, com dados transacionais       |
| **Airflow**    | Orquestração de pipelines com DAGs                        |
| **Snowflake**  | Data Warehouse para análise e visualização                |
| **dbt**        | Modelagem e transformação de dados dentro do Snowflake    |
| **Looker Studio** | Visualização dos dados transformados e métricas de negócio |

---

## 🔄 Visão das Etapas do Projeto

As principais etapas do bootcamp são:

1. **Explorar o banco PostgreSQL** com os dados de vendas
2. **Configurar o ambiente do Airflow** (EC2 + Docker)
3. **Criar conta no Snowflake** e montar a estrutura
4. **Construir pipeline de carga com Airflow**
5. **Criar a camada analítica com dbt**
6. **Visualizar os dados no Looker Studio**
7. **Avaliar alternativas e melhorias no projeto**

---

## 💡 Considerações Gerais

- Você será responsável por **criar contas gratuitas**, configurar acessos e garantir que os recursos utilizados sejam desativados após o uso.
- O projeto segue boas práticas de versionamento (CI/CD) e controle de código fonte.
- Todos os scripts e arquivos utilizados durante o bootcamp serão organizados nas seções correspondentes deste repositório.

---

## 💰 Custos e Contas

- **Importante:** verifique os limites de uso gratuito das ferramentas (AWS, Snowflake, etc.).
- Desative os recursos quando não estiver utilizando para evitar cobranças.
- Mantenha controle de todas as credenciais, usuários e permissões utilizados.

---

**Vamos começar a jornada! 🚀**
