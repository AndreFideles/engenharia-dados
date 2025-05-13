# 🛋️ Conectando dbt Cloud ao Snowflake

Este guia apresenta o passo a passo para criar sua conta no dbt Cloud, conectar ao Snowflake, configurar ambientes e realizar o deploy com organização.

---

## 📅 1. Criar Conta no dbt Cloud

1. Acesse: [https://cloud.getdbt.com/signup/](https://cloud.getdbt.com/signup/)
2. Cadastre-se com seu e-mail
3. Crie sua organização e projeto inicial
4. Escolha a opção **"Start from scratch"**

---

## ⚒️ 2. Conectar dbt Cloud ao Snowflake

Ao finalizar o projeto, clique em **"Configure your connection"** e selecione o tipo **Snowflake**.

Preencha os dados conforme sua conta Snowflake:

| Campo     | Valor Exemplo              |
| --------- | -------------------------- |
| Account   | ktnlqur-va81917            |
| Role      | TRANSFORM                  |
| Warehouse | DEFAULT\_WH                |
| Database  | NOVADRIVE                  |
| Schema    | ANDRE\_FID (ou seu schema) |
| Username  | Seu login                  |
| Password  | Sua senha                  |

> 🔗 Dica: o campo **Account** está na URL do Snowflake (antes do `.snowflakecomputing.com`).

---

## 🔁 3. Versionamento com GitHub

1. Acesse o menu do projeto: **Settings > Repository**
2. Clique em **"Link a repository"**
3. Autorize o GitHub e selecione o repositório desejado (ex: `engenharia-dados`)
4. Escolha a branch `main` como padrão

---

## 🌐 4. Environments

Crie ambientes separados para desenvolvimento e produção:

### Produção (`prod`)

* **Branch**: `main`
* **Schema**: `analytics` (padrão de deploy)

### Desenvolvimento (`dev`, `teste`, etc.)

* Cada desenvolvedor pode usar sua branch
* Schema exclusivo (ex: `ANDRE_FID`)

> ✅ Permite que cada desenvolvedor teste isoladamente

---

## ⏳ 5. Criar Jobs de Execução

1. Menu lateral: **Deploy > Jobs**
2. Clique em **"New Job"**
3. Defina:

   * Nome: `Deploy Produção`
   * Ambiente: `prod`
   * Comandos:

     ```bash
     dbt run
     dbt test
     dbt docs generate
     ```
4. Agende se desejar execução automática

---

## 🚀 Resultado Final

Com esse setup:

* Os desenvolvedores atuam em schemas separados
* O deploy é feito pela branch `main`
* Jobs garantem execução agendada e confiável
* Toda execução gera documentação atualizada

---

> 📄 Sugestão: documentar este processo também dentro do projeto no GitHub (ex: `docs/` ou `5-dbt/README.md`).
