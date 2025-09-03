# 🚀 AWS Santander Code Girls 2025 – Desafio EC2

Este repositório foi criado como parte do desafio final do **bootcamp AWS Santander Code Girls 2025 (DIO)**.  
O objetivo é consolidar os conhecimentos adquiridos em **gerenciamento de instâncias EC2 na AWS** e documentar, de forma organizada, as práticas e insights obtidos durante o curso.

---

## 📚 Resumo do Bootcamp

Durante o bootcamp, percorremos os seguintes módulos:

1. **Introdução à AWS Cloud Foundation**  
   - Conceitos fundamentais de computação em nuvem.  
   - Diferença entre modelos **IaaS, PaaS e SaaS**.  
   - Região, zona de disponibilidade e escalabilidade.  

2. **Essenciais da Infraestrutura AWS**  
   - Serviços principais da AWS: EC2, S3, IAM, RDS, entre outros.  
   - Entendimento da **arquitetura global** da AWS.  

3. **Configurando sua Conta AWS com Segurança e Eficiência**  
   - Criação e gerenciamento de usuários com **IAM**.  
   - Implementação do **MFA (Multi-Factor Authentication)**.  
   - Organização de **Billing & Cost Management**.  

4. **Primeiros Passos com Acesso Seguro e Controle de Custos na AWS**  
   - Como monitorar gastos com **Cost Explorer**.  
   - Estratégias para não ultrapassar limites do **Free Tier**.  
   - Boas práticas de shutdown de instâncias e uso de tags.  

5. **Entendendo as Instâncias EC2 e Otimização de Recursos na AWS**  
   - Tipos de instância e suas aplicações.  
   - Diferença entre **EBS (armazenamento persistente)** e **Instance Store**.  
   - Elastic IP e balanceamento de carga.  

6. **Armazenamento na Nuvem com Amazon EBS e S3**  
   - Configuração de volumes **EBS**.  
   - Uso do **Amazon S3** para armazenamento escalável e seguro.  
   - Classes de armazenamento (Standard, Infrequent Access, Glacier).  

7. **Gerenciando Instâncias EC2 na AWS (Desafio Final)**  
   - Criação, configuração e gerenciamento de instâncias EC2.  
   - Conexão segura via **SSH**.  
   - Configuração de **grupos de segurança**.  
   - Deploy simples de aplicações e encerramento seguro.

---

## ☁️ Arquitetura Prática (Fluxo de Dados em AWS)

Para consolidar o aprendizado, foi criado o seguinte **modelo arquitetural em nuvem**, inspirado no contexto de **auditoria e monitoramento em tempo real de dados satelitais**:

![Diagrama AWS](./diagramas/diagramaAWS.drawioComFluxoDescrito.png)

### 🔎 Explicação do Fluxo
1. **Satélite → Ground Station**  
   - Dados satelitais coletados e transmitidos para a estação terrestre.  

2. **Ground Station → Amazon S3 (Landing Zone)**  
   - Armazenamento inicial (dados brutos).  
   - Criação de um bucket de entrada para centralizar os dados recebidos.  

3. **AWS Lambda → EC2/EBS**  
   - Lambda processa eventos e envia para instâncias EC2.  
   - EC2 com EBS armazena e processa dados críticos.  

4. **NDR/IDS**  
   - Auditoria de tráfego em tempo real, monitorando possíveis incidentes de segurança.  

5. **S3 Analytics → AWS Glue → Glacier**  
   - Dados processados são organizados no **S3 Analytics**.  
   - O **AWS Glue** permite integração e preparação de dados.  
   - Dados de longo prazo são arquivados no **Amazon Glacier** (baixo custo).  

---

## 💡 Insights Pessoais

- O **S3** se mostrou fundamental como ponto de entrada e organização dos dados.  
- O uso de **Lambda** traz escalabilidade sem a necessidade de provisionamento manual.  
- A combinação de **EC2 + NDR/IDS** reforça a importância da segurança em tempo real.  
- **Glacier** é ideal para arquivamento de longo prazo, reduzindo custos.  
- Esse exercício mostrou como os conceitos aprendidos no bootcamp podem ser aplicados em cenários reais, inclusive no contexto de **cibersegurança aeroespacial**.  

---

## 📷 Evidências
As capturas de tela do laboratório foram adicionadas na pasta [`/images`](./images).  
Elas mostram o processo de criação da instância EC2, configuração de segurança e teste de conectividade.

---

## 📚 Referências
- [Documentação AWS – EC2](https://docs.aws.amazon.com/ec2/)  
- [Documentação AWS – S3](https://docs.aws.amazon.com/s3/)  
- [Documentação AWS – Lambda](https://docs.aws.amazon.com/lambda/)  
- [Guia GitHub Markdown](https://docs.github.com/pt/get-started/writing-on-github)  
- [DIO – Formação AWS Santander Code Girls](https://web.dio.me/)  

---
