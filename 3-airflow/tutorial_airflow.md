# ☁️ Tutorial: Configurando o Apache Airflow na AWS (EC2 + Ubuntu)

Este tutorial detalha o passo a passo para configurar o Apache Airflow utilizando uma instância EC2 com Ubuntu na AWS, conforme realizado no projeto de Engenharia de Dados para a NovaDrive Motors.

---

## 🖥️ Etapa 1: Criando a Instância EC2

### Acessando o serviço EC2:
1. Acesse o [Console da AWS](https://aws.amazon.com/console/)
2. Vá para a aba lateral **EC2 > Instances**
3. Clique em **Executar Instância (Launch Instance)**

### Configurações básicas:
- **Nome da instância:** `NovaDriveAF`
- **Imagem (AMI):** Ubuntu Server 24.04 LTS (HVM), 64-bit (x86)
- **Tipo de instância:** `t2.micro` (gratuito) ou `t2.large` para mais performance
- **Volume de armazenamento:** 8 GiB SSD padrão

> ⚠️ Importante: Ao finalizar os testes, encerre a instância para evitar custos inesperados.

---

## 🔐 Etapa 2: Criando um Par de Chaves (Key Pair)

1. Na etapa de criação da instância, vá até **Par de chaves (login)**
2. Clique em **Criar novo par de chaves**
3. Escolha as opções:
   - **Nome:** `keypairaws`
   - **Tipo:** RSA
   - **Formato:** `.pem` (para uso com terminal SSH/OpenSSH)

> 💾 Salve o arquivo `.pem` no seu computador. Você vai precisar dele para acessar a máquina.

---

## ✅ Etapa 3: Confirmação da Instância

Após criar a instância:
- Ela aparecerá com status **Executando** (`Running`)
- O IP público estará visível na tabela
- O DNS público também estará disponível (ex: `ec2-13-58-82-73.us-east-2.compute.amazonaws.com`)

Você usará esse IP para acessar via terminal:

```bash
ssh -i keypairaws.pem ubuntu@<ENDERECO-IP>
```

---

📌 Este documento será atualizado com os próximos passos: instalação do Docker, Docker Compose, Airflow, e criação da DAG.