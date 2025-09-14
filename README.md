# 📊 Projeto Final EBAC – Pipeline de Dados do Telegram  

## 📌 Introdução  
O uso de bots em plataformas de mensagens instantâneas tem crescido como solução para automação de processos e análise de interações digitais. O **Telegram**, por meio de sua **Bot API**, permite capturar diferentes tipos de mensagens (texto, imagens, áudios, vídeos e arquivos), tornando-se uma excelente fonte de dados.  

Este projeto, desenvolvido como **projeto final do curso de Analista de Dados da EBAC**, tem como propósito implementar um **pipeline de dados do Telegram** utilizando serviços da **AWS**, demonstrando na prática o ciclo completo de ingestão, transformação e análise de dados.  

---

## 🎯 Objetivo  
O objetivo deste projeto é demonstrar a construção de um pipeline de dados escalável e automatizado, passando pelas seguintes etapas:  

- Captura das mensagens enviadas em um grupo do Telegram por meio da **Bot API**.  
- Armazenamento dos dados crus em formato **JSON** em um bucket do **AWS S3**.  
- Processamento e transformação das mensagens em formato **Parquet**, enriquecidas e particionadas por dia, utilizando **AWS Lambda**.  
- Automação da execução diária do processo com **AWS Event Bridge**.  
- Disponibilização dos dados enriquecidos no **AWS Athena**, permitindo a execução de consultas SQL para extração de insights sobre o comportamento dos usuários e a utilização do bot.  

Este projeto evidencia a aplicação prática dos conceitos aprendidos ao longo do curso da EBAC, simulando um **caso real de engenharia e análise de dados em nuvem**.  

---

## 🛠️ Tecnologias Utilizadas  

- **Telegram Bot API** → Captura e integração das mensagens.  
- **AWS API Gateway** → Exposição do endpoint para recebimento das mensagens.  
- **AWS Lambda** → Funções serverless para ingestão e transformação de dados.  
- **AWS S3** → Armazenamento de dados crus (JSON) e enriquecidos (Parquet).  
- **AWS Event Bridge** → Agendamento da execução diária das funções.  
- **AWS Athena** → Consulta SQL e análise dos dados processados.  
- **Python** → Desenvolvimento das funções Lambda e manipulação dos dados (`json`, `pyarrow`, etc.).  

---

## 🚀 Estrutura do Pipeline  

1. **Ingestão**  
   - Bot do Telegram captura as mensagens enviadas no grupo.  
   - Mensagens são enviadas ao **API Gateway** e processadas por uma função **Lambda**.  
   - Dados são armazenados no **S3** em formato **JSON** e particionados por dia.  

2. **ETL (Transformação)**  
   - Uma função **Lambda** processa diariamente os dados crus do dia anterior (D-1).  
   - Os dados são transformados e salvos em **Parquet**, enriquecidos e particionados.  
   - O agendamento é feito via **Event Bridge**, executado todo dia à meia-noite (GMT-3).  

3. **Apresentação**  
   - Os dados enriquecidos são expostos no **AWS Athena**.  
   - Consultas SQL são executadas para explorar e analisar os dados.  
