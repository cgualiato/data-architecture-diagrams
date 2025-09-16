# TaskDashboard - Fluxo Arquitetural de Dados

## Descrição

Este repositório contém um **diagrama arquitetural de dados** representando o fluxo desde as fontes de dados da **SaaSTechBrazil** até o **ambiente TOTVS**, com foco no **modelo de Churn**.  

O diagrama está definido em **Graphviz DOT**, permitindo geração visual em diversos formatos (PNG, PDF, SVG).

---

## Estrutura do Diagrama

### 1. Fontes de Dados (SaaSTechBrazil)
- **Bancos de Dados**: MySQL, PostgreSQL (dados transacionais).  
- **APIs Internas / Microsserviços**: dados via chamadas API.  
- **Arquivos CSV**: informações de clientes, tickets e uso.

### 2. Processos de Ingestão e Staging
- **Ingestão**: scripts Python, SFTP, Apache Airflow/Nifi.  
- **Staging (Data Lake)**: armazenamento de dados brutos (CSV) em S3/GCS.

### 3. Processamento
- Limpeza e transformação de dados usando **Python/Pandas, SQL e Apache Spark**.  
- Combinação de dados (joins), engenharia de features, normalização e criação da variável alvo para o modelo de Churn.

### 4. Acesso e Consumo (TOTVS)
- **Data Marts / Data Warehouse**: dados limpos e transformados.  
- Consumo via:
  - Dashboards e relatórios (**TOTVS BI**)  
  - Notebooks para análise e desenvolvimento de modelos (**Jupyter / Databricks**)  
  - APIs internas TOTVS  
  - Integração com sistemas ERP/CRM TOTVS  

---

## Tecnologias Utilizadas
- **Graphviz DOT**: para modelagem e visualização do diagrama.  
- **Python / Pandas / SQL / Spark**: processamento e transformação de dados.  
- **S3 / GCS**: armazenamento de dados brutos.  
- **Airflow / Nifi**: orquestração de pipelines de ingestão.

---

## Como Visualizar o Diagrama

1. Instale o Graphviz:  
   - Windows: [https://graphviz.org/download/](https://graphviz.org/download/)  
   - Linux: `sudo apt install graphviz`  
   - MacOS: `brew install graphviz`

2. Salve o arquivo DOT (por exemplo `churn_pipeline.dot`).  

3. Gere a imagem:

```bash
# Gerar PNG
dot -Tpng churn_pipeline.dot -o churn_pipeline.png

# Gerar PDF
dot -Tpdf churn_pipeline.dot -o churn_pipeline.pdf
