# ☁️ Seção 3 – Configurando Airflow no AWS com EC2 e Ubuntu

Nesta etapa, configuramos o ambiente necessário para rodar o Apache Airflow na nuvem, utilizando uma instância EC2 da AWS com o sistema operacional Ubuntu. Essa infraestrutura servirá como orquestrador dos pipelines de dados do projeto.

---

## 💡 Objetivos da Seção

- Criar e configurar conta na AWS
- Criar máquina virtual (VM) com Ubuntu na EC2
- Instalar Docker e Docker Compose
- Configurar e iniciar o Apache Airflow
- Validar o funcionamento via interface web (Airflow Web UI)

---

## 📋 Aulas da Seção

| Aula                          | Duração | Objetivo                                                                 |
|------------------------------|---------|--------------------------------------------------------------------------|
| **21. Criando Conta na AWS** | 4 min   | Criação da conta gratuita na AWS com acesso ao EC2                       |
| **22. Passo a Passo para Instalar Airflow** | 1 min | Visão geral do processo de instalação                                    |
| **23. Criando VM com EC2 e Ubuntu** | 10 min  | Configuração da instância, grupos de segurança, SSH                      |
| **24. Instalando Airflow**   | 17 min  | Instalação de Docker, Docker Compose e containers do Airflow             |
| **25. Configurando Airflow** | 10 min  | Configuração do Airflow (users, dags, conexões, variáveis)               |

---

## ⚙️ Estrutura Esperada

> A pasta `3-airflow/` conterá:

| Arquivo / Pasta           | Descrição                                                 |
|---------------------------|-----------------------------------------------------------|
| `docker-compose.yml`      | Arquivo com os containers necessários para o Airflow      |
| `dags/`                   | Diretório onde ficarão as DAGs criadas para o projeto     |
| `tutorial_airflow.md`     | Tutorial detalhado com o passo a passo da criação da VM   |

---

📘 **Tutorial completo passo a passo da configuração da máquina virtual:**

→ [Clique aqui para ver o tutorial técnico de criação da instância EC2 e configuração do ambiente Airflow](tutorial_airflow.md)
