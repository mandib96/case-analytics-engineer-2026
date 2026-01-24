# Case Analytics Engineer - Boticário 2026

Objetivo: Este projeto realiza a ingestão automatizada de dados de vendas armazenados no Google Cloud Storage (GCS) para o Google BigQuery. O pipeline consolida arquivos (CSV), realiza a padronização de esquemas e organiza os dados em uma arquitetura de medalhão.

Tecnologias: Google Colab, BigQuery, GCS, Looker Studio.

Arquitetura: 

  Armazenamento Raw: Google Cloud Storage (Bucket).
  
  Processamento & ETL: Python (Pandas) executado via Google Colab.
  
  Data Warehouse: Google BigQuery (Tabela Particionada).
  
  Orquestração: Apache Airflow (Docker).

Como rodar: 
  Pré-requisitos
    Possuir uma conta no Google Cloud Platform.
    
    Criar uma Service Account com as permissões:
    
        Storage Object Viewer
        
        BigQuery Admin
    
    Gerar a chave em formato JSON.

  Execução no Google Colab
  Abra o arquivo .ipynb localizado na pasta notebooks/.
  
  No menu lateral do Colab, faça o upload do seu arquivo JSON de credenciais.
  
  Renomeie o arquivo para credentials.json ou ajuste a variável PATH_CHAVE no código.
  
  Execute as células em sequência.
