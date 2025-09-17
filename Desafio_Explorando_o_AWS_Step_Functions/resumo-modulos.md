# 🛠️ Resumo dos Serviços AWS Utilizados

## 🔄 AWS Step Functions
- **O que é**: Serviço de **orquestração de workflows**.  
- **Função principal**: coordena a execução de vários serviços AWS em etapas sequenciais ou paralelas.  
- **Diferencial**: construção visual de fluxos, com pouco ou nenhum código (no-code/low-code).  
- **Casos de uso**: pipelines de dados, processamento de arquivos, automação de tarefas e microserviços.  

---

## ⚡ AWS Lambda
- **O que é**: Serviço **serverless** para executar funções sob demanda.  
- **Função principal**: roda pequenos blocos de código sem necessidade de provisionar servidores.  
- **Diferencial**: escala automaticamente; cobra apenas pelo tempo de execução.  
- **Casos de uso**: validação de dados, ETL, automação de eventos do S3, APIs simples.  

---

## 📦 Amazon S3 (Simple Storage Service)
- **O que é**: Armazenamento de objetos na nuvem.  
- **Função principal**: guardar dados brutos, arquivos, logs, backups etc.  
- **Diferencial**: alta durabilidade (99,999999999%), classes de armazenamento com custo otimizado.  
- **Casos de uso**: landing zone de dados, armazenamento de imagens, logs e integrações com Lambda/Step Functions.  

---

## 📬 Amazon SNS (Simple Notification Service)
- **O que é**: Serviço de **pub/sub** (publicação e assinatura).  
- **Função principal**: enviar notificações ou mensagens para múltiplos assinantes.  
- **Diferencial**: entrega assíncrona e paralela (vários destinos ao mesmo tempo).  
- **Casos de uso**: alertas de erro, envio de mensagens a filas, SMS, e-mails.  

---

## 📮 Amazon SQS (Simple Queue Service)
- **O que é**: Serviço de **filas de mensagens**.  
- **Função principal**: desacoplar componentes distribuídos, garantindo entrega assíncrona.  
- **Diferencial**: garante que as mensagens sejam processadas mesmo que o consumidor esteja indisponível temporariamente.  
- **Casos de uso**: filas de processamento de pedidos, logs ou tarefas assíncronas.  

---

## 🗄️ Amazon DynamoDB
- **O que é**: Banco de dados **NoSQL gerenciado**.  
- **Função principal**: armazenamento rápido e escalável de chave-valor e documentos.  
- **Diferencial**: latência de milissegundos, escalabilidade automática, totalmente gerenciado.  
- **Casos de uso**: persistência de estado de workflows, aplicativos de alta escala, auditoria de execuções.  

---

## 🔗 Integração dos Serviços

👉 Esse conjunto de serviços forma a base para **workflows automatizados**:

1. **S3** armazena dados.  
2. **Step Functions** orquestra o fluxo.  
3. **Lambda** processa os pacotes.  
4. **SNS/SQS** notificam ou distribuem mensagens.  
5. **DynamoDB** registra estados e resultados.  
