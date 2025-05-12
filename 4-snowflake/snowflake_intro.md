# ❄️ Introdução Técnica ao Snowflake

Este documento reúne os principais conceitos, arquiteturas e recursos do Snowflake, uma das principais plataformas de Data Warehousing em nuvem.

---

## 🚀 Visão Geral

- Fundado em 2012 por ex-funcionários da Oracle.
- Lançado em 2014 como uma solução moderna para Data Warehousing.
- Plataforma **SaaS** que roda sobre **AWS**, **Azure** e **GCP**.
- Totalmente separado entre **armazenamento** e **processamento**.

---

## 🧱 Estrutura da Plataforma

- **Banco de Dados → Schema → Tabelas**
- **Warehouse**: representa os recursos computacionais (CPU/Memória) usados para processar dados.
- **Warehouse Size** (tamanho influencia no custo em créditos/hora):
  - X-Small, Small, Medium, Large, X-Large até 6X-Large (e múltiplos)

---

## 💰 Custo por Uso

- **Processamento**: cobrado por créditos/hora baseado em tamanho e edição.
  - Exemplo (Standard – South America East1): $3.10/h
  - Enterprise: $6.20/h
- **Armazenamento**:
  - On-Demand: $74/TB/mês
  - Capacidade Provisionada: $40,50/TB/mês

---

## ⚙️ Recursos Técnicos

### 🧠 Multi-Cluster Warehouse

- Permite escalar automaticamente com base em carga.
- **Auto-scale**: define número mínimo e máximo de nós.
- **Maximized**: sempre aloca o máximo de clusters.

#### Scaling Policy:
- **Standard**: escala de forma dinâmica.
- **Economy**: escala de forma mais econômica.

---

### 💤 Auto-suspend e Auto-resume

- **Auto-suspend**: pausa a warehouse após inatividade.
- **Auto-resume**: reativa automaticamente quando necessário.
- Ideal para economia de custos.

---

## 📊 Armazenamento Colunar

- Snowflake utiliza **armazenamento colunar** para otimizar performance de leitura e compressão.

---

## 🧩 Recursos Avançados

### 🔁 Time Travel

- Permite consultar versões anteriores dos dados em até 1 ou 90 dias (dependendo da edição).
- Ideal para restauração de dados ou auditoria.

### 📤 SnowPipe

- Carregamento contínuo e automatizado de arquivos para dentro do Snowflake.
- Funciona com notificações automáticas via AWS S3, GCP Storage ou Azure Blob.

### 🔐 Segurança

- Criptografia de dados em repouso e em trânsito por padrão.
- Suporte a autenticação multi-fator, roles, políticas de acesso detalhadas.

### ⚡ Query Acceleration

- Otimização automática de performance.
- Usa algoritmos distribuídos e, em casos avançados, recursos paralelos como GPUs.

---

## 🧪 Clustering

- Clustering automático com base em **Cluster Keys**.
- Evita necessidade de particionamento manual.
- Melhora performance em tabelas muito grandes com filtros específicos.

---

## 🤝 Data Sharing

- Compartilhamento seguro e direto de dados com outras contas Snowflake.
- Sem duplicação física dos dados.
- Suporte a **Data Exchange** (mercado de dados da Snowflake).

---

## 💬 Linguagens e Conectores

- Linguagens:
  - SQL (principal)
  - Python (via Snowpark)
  - R, Java, Scala
- Conectores:
  - JDBC, ODBC, SnowSQL, Python Connector, dbt Adapter

---

## 📈 Integrações

- Power BI, Looker, Tableau, dbt, Apache Airflow, Fivetran, Matillion, DataRobot, entre outros.

---

> ✅ Este material faz parte do projeto prático de Engenharia de Dados (NovaDrive Motors) e será usado como documentação oficial da seção Snowflake no portfólio.

---

## 📎 Script de Criação de Estrutura

Você pode baixar o script `.sql` com toda a estrutura de tabelas do projeto NovaDrive para execução no Snowflake:

📄 [`novadrive_snowflake_estrutura.sql`](novadrive_snowflake_estrutura.sql)
