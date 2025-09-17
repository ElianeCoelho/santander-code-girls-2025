# 🚀 AWS Santander Code Girls 2025 – Desafios Práticos

Este repositório foi criado como parte dos desafios finais do **bootcamp AWS Santander Code Girls 2025 (DIO)**.  
O objetivo é consolidar os conhecimentos adquiridos em **serviços AWS** e documentar, de forma organizada, as práticas e insights obtidos durante o curso.  

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

7. **Desafios Finais**  
   - Aplicação prática dos conceitos com **EC2** e **Step Functions**.  

---

# 🖥️ Desafio 1 – Gerenciando Instâncias EC2 na AWS

### 📌 Objetivo
Consolidar os conhecimentos sobre criação, configuração e gerenciamento de **instâncias EC2**, aplicando boas práticas de segurança e custo.  

### ☁️ Arquitetura Prática
Fluxo de dados em nuvem inspirado no contexto de **auditoria e monitoramento em tempo real de dados satelitais**:

![Diagrama AWS](./diagramas/diagramaAWS.drawioComFluxoDescrito.png)

**Fluxo:**
1. Satélite envia dados → Ground Station.  
2. Ground Station → **Amazon S3** (Landing Zone).  
3. **AWS Lambda → EC2/EBS** processam arquivos.  
4. **NDR/IDS** faz auditoria de tráfego em tempo real.  
5. Dados processados → **S3 Analytics → Glue → Glacier**.  

### 💡 Insights
- O **S3** centraliza dados brutos.  
- **Lambda** garante escalabilidade serverless.  
- **EC2 + IDS/NDR** reforçam segurança.  
- **Glacier** é ideal para arquivamento de longo prazo.  

### 📷 Evidências
- As capturas de tela do laboratório estão na pasta [`Desafio_1/imagens`](./Desafio_1/imagens/).  
- Mostram a criação da instância EC2, configuração de segurança e conectividade SSH.  

---

# 🔄 Desafio 2 – Explorando AWS Step Functions

### 📌 Objetivo
Experimentar o **AWS Step Functions** como serviço de **orquestração de workflows**, integrando serviços da AWS (Lambda, S3, SNS, SQS, DynamoDB) de forma visual e com pouco código.  

### ☁️ Arquitetura Prática
**Caso de uso:** Validação e processamento de arquivos em bucket S3.  

1. Arquivo enviado ao **S3** dispara o fluxo.  
2. **Lambda** valida metadados.  
3. Se válido → **Lambda** processa.  
4. Em caso de erro → notificação via **SNS/SQS**.  
5. Dados processados → armazenados/analisados.  

### 🧩 State Machine (ASL JSON)
Exemplo simplificado da definição do workflow:

```json
{
  "Comment": "Workflow: validar e processar arquivo do S3",
  "StartAt": "ValidarEntrada",
  "States": {
    "ValidarEntrada": {
      "Type": "Task",
      "Resource": "arn:aws:lambda:REGIAO:CONTA:function:validar_entrada",
      "Next": "EntradaValida?"
    },
    "EntradaValida?": {
      "Type": "Choice",
      "Choices": [
        { "Variable": "$.valido", "BooleanEquals": true, "Next": "ProcessarArquivo" }
      ],
      "Default": "NotificarErro"
    },
    "ProcessarArquivo": {
      "Type": "Task",
      "Resource": "arn:aws:lambda:REGIAO:CONTA:function:processar_arquivo",
      "Next": "Sucesso"
    },
    "NotificarErro": {
      "Type": "Fail",
      "Cause": "Erro na validação"
    },
    "Sucesso": { "Type": "Succeed" }
  }
}


## 💡 Insights Pessoais

- O **S3** se mostrou fundamental como ponto de entrada e organização dos dados.  
- O uso de **Lambda** traz escalabilidade sem a necessidade de provisionamento manual.  
- A combinação de **EC2 + NDR/IDS** reforça a importância da segurança em tempo real.  
- **Glacier** é ideal para arquivamento de longo prazo, reduzindo custos.  
- Esse exercício mostrou como os conceitos aprendidos no bootcamp podem ser aplicados em cenários reais, inclusive no contexto de **cibersegurança aeroespacial**.  

---

## 📷 Evidências
As capturas de tela do laboratório Desafio 1 foram adicionadas na pasta [`Desafio_1/imagens`](./Desafio_1/imagens/). 

Elas mostram o processo de criação da instância EC2, configuração de segurança e teste de conectividade.

s capturas de tela do laboratório Desafio_Explorando_o_AWS_Step_Functions foram adicionadas na pasta [`Desafio_Explorando_o_AWS_Step_Functions`](./Desafio_Explorando_o_AWS_Step_Functions/imagens/). 


---

## 📚 Referências
- [Documentação AWS – EC2](https://docs.aws.amazon.com/ec2/)  
- [Documentação AWS – S3](https://docs.aws.amazon.com/s3/)  
- [Documentação AWS – Lambda](https://docs.aws.amazon.com/lambda/)  
- [Guia GitHub Markdown](https://docs.github.com/pt/get-started/writing-on-github)  
- [DIO – Formação AWS Santander Code Girls](https://web.dio.me/)  

---
