# Case Técnico – Pipeline de Dados de Vendas

### Contexto

Este repositório contém a implementação de um pipeline de dados analítico, desenvolvido como parte de um case técnico para a vaga de Analytics Engineer Sênior.

O objetivo do projeto é demonstrar o raciocínio técnico aplicado à construção de um fluxo de dados de ponta a ponta, contemplando:

ingestão de arquivos CSV

armazenamento em banco de dados

tratamento e modelagem dos dados

organização em camadas analíticas

versionamento de código

preparação para consumo analítico e visualização


Os dados utilizados são fictícios, contendo informações de vendas entre os anos de 2017 e 2019.


---

### Arquitetura Geral

A solução foi estruturada utilizando o modelo medalhão, com separação clara de responsabilidades entre as camadas.

Google Cloud Storage
        ↓
     Python
        ↓
 BigQuery - Raw
        ↓
 BigQuery - Trusted
        ↓
 BigQuery - Analytics
        ↓
     Dashboard



Essa abordagem permite:

rastreabilidade dos dados desde a origem

tratamento progressivo das informações

simplicidade no consumo analítico

possibilidade de evolução futura do pipeline



---


#### Notebooks

create_raw_table.ipynb

Responsável pela ingestão dos arquivos CSV armazenados no Google Cloud Storage, leitura dos dados via Python e carga da camada Raw no BigQuery.

create_trusted_table.ipynb

Responsável pelo tratamento dos dados, definição da granularidade analítica, padronização de tipos e consolidação de registros para controle de duplicidade, resultando na camada Trusted.

#### SQL

analytics_tables.sql

Contém as queries responsáveis pela criação das tabelas analíticas finais, conforme solicitado no escopo do case.


---

### Processo de Ingestão

O processo de ingestão foi dividido em duas etapas principais:

#### 1. Ingestão Raw (Python)

leitura dos arquivos CSV armazenados no Google Cloud Storage

conversão dos dados em DataFrames

carga dos dados no BigQuery preservando o formato original da fonte


#### 2. Tratamento e Modelagem (SQL)

padronização de tipos de dados

definição da granularidade analítica

consolidação de registros para controle de duplicidade

criação das tabelas de consumo


Essa separação garante clareza, organização e facilidade de manutenção do pipeline.


---

### Tabelas Analíticas

Foram construídas quatro tabelas analíticas, conforme solicitado no case:

consolidado de vendas por mês e ano

consolidado de vendas por marca e linha

consolidado de vendas por marca, mês e ano

consolidado de vendas por linha, mês e ano


Essas tabelas foram desenhadas como marts de consumo, prontas para uso em dashboards e análises descritivas.


---

### Orquestração

O fluxo de atualização do pipeline foi modelado de forma conceitual utilizando Airflow, representando as seguintes etapas:

1. ingestão da camada Raw


2. transformação da camada Trusted


3. atualização das tabelas da camada Analytics



Para o escopo do case, a orquestração não foi executada em ambiente produtivo, sendo apresentada de forma conceitual, com possibilidade de execução futura via Cloud Composer.


---

### Versionamento

Todo o código do projeto foi versionado utilizando GitHub, permitindo:

controle de histórico de alterações

rastreabilidade das decisões técnicas

organização do desenvolvimento


Os commits foram realizados de forma incremental ao longo da construção do case.


---

### Visualização

As tabelas analíticas serviram como base para a construção de um dashboard com visões consolidadas de vendas por marca, linha e evolução temporal.

O objetivo do dashboard foi demonstrar o potencial analítico da solução, considerando que os dados utilizados são fictícios e possuem limitações de contexto.


---

### Possíveis Evoluções

A solução foi desenhada de forma simples, porém escalável. Algumas evoluções naturais incluem:

implementação de cargas incrementais

inclusão de validações de qualidade de dados

enriquecimento das bases com novas dimensões

execução da orquestração em ambiente produtivo

criação de camada semântica para consumo analítico



---

### Observações

Este projeto possui caráter demonstrativo, com foco na avaliação do raciocínio técnico, organização do pipeline e clareza das decisões arquiteturais.

O desenvolvimento respeitou o escopo e o prazo definidos para o case técnico.