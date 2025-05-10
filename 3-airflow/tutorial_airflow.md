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

## 🌐 Etapa 4: Liberando a Porta 8080 (Interface Web do Airflow)

Para acessar o Airflow via navegador, é necessário liberar a porta **8080** na instância EC2:

1. Clique na sua instância no painel do EC2
2. Vá até a aba **Segurança**
3. Clique em **Editar regras de entrada (Edit inbound rules)**
4. Adicione uma nova regra com os seguintes dados:

| Campo      | Valor                   |
|------------|--------------------------|
| **Type**   | `Custom TCP`            |
| **Port**   | `8080`                  |
| **Source** | `Anywhere (0.0.0.0/0)`  |

> ⚠️ Use "Anywhere" apenas para ambientes de estudo. Em produção, restrinja por IP.

---

## 🧩 Etapa 5: Acessando a Instância via SSH

Para configurar o Airflow, é necessário acessar a instância criada utilizando um terminal (Prompt de Comando, Terminal Linux, ou VS Code com SSH).

### ✅ Acesso rápido via Console AWS

1. No painel da EC2, clique em sua instância
2. Clique em **Connect**
3. Selecione a aba **SSH Client**
4. Copie o comando de exemplo sugerido, como:

```bash
ssh -i "keypairaws.pem" ubuntu@ec2-13-58-82-73.us-east-2.compute.amazonaws.com
```

---

### 🧭 Como executar o comando corretamente

#### Opção 1 – Especificar o caminho da chave:

```bash
ssh -i "C:/Users/SeuUsuario/Downloads/keypairaws.pem" ubuntu@<ENDERECO-IP>
```

#### Opção 2 – Navegar até a pasta da chave antes de rodar:

```bash
cd C:/Users/SeuUsuario/Downloads/
ssh -i "keypairaws.pem" ubuntu@<ENDERECO-IP>
```

> 💡 Dica: No primeiro acesso, digite `yes` se for perguntado sobre a autenticidade do host.

---

📌 Próximo passo: instalação do Docker, Docker Compose e o ambiente do Airflow.
