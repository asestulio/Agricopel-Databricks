# Descrição
Esse projeto consiste em extrair dados sobre vendas da empresa Global Sales usando uma base de dados em formato json e csv, processando-o em diferentes níveis (Bronze, Silver, Gold) usando Databricks e orquestrando o fluxo de dados com o Azure Data Factory. O objetivo é criar uma visualização com a quantidade de vendas por país e produto

# Arquitetura do Projeto

# O projeto utiliza arquitetura medalhão
* Camada Bronze: Extração de dados brutos em formato Parquet e criação de colunas de controle.
* Camada Prata: Limpeza e estruturação de dados, criação de comentários e otimização de tabelas.
* Camada Ouro: Agregação de dados para insights, criação de comentários e otimização de tabelas.

# Tenologias usadas
* Databricks: Para processamento e análise de dados usando Spark.
* Azure Data Factory: Para orquestração de fluxo de trabalho de dados.
* Azure Key Vault: Para proteger o gerenciamento de chaves de recursos.

# Pré-requisitos
Conta do Azure com acesso ao Databricks, Azure Data Factory e Azure Key Vault.

# Etapas
## 1 Criação de grupos de recursos:
* Crie todos os grupos de recursos e recursos necessários para o desenvolvimento do projeto
<img width="1913" height="573" alt="image" src="https://github.com/user-attachments/assets/b86a242b-2eb5-4b13-8953-869d21cce565" />

## 2 Configuração do Azure Key Vault:
Inserir imagem dos KeyVault

## 3 Configuração do Azure Key Vault:
* Desenvolvimento de notebooks para o workspace Databricks aplicando extração, limpeza e agregação de dados.
* Como a ingestão foi feita diretamente pelo DataFactory e transformada em formato Parquet, os dados foram carregados na camada bronze e processador na camada silver e posteriormente na cama gold.
* Silver: https://github.com/asestulio/Agricopel-Databricks/tree/main/FINANCEIRO/CONTAS_RECEBER/01.silver/silver_fincanceiro
* Gold: https://github.com/asestulio/Agricopel-Databricks/tree/main/FINANCEIRO/CONTAS_RECEBER/02.gold

  ## 4 Azure Data Factory:
  * Criação de Linked Service para acessar o Databricks, DataLake Gen2
    <img width="1576" height="359" alt="image" src="https://github.com/user-attachments/assets/988bb983-20ba-4c82-a6f5-e65310900807" />

  * Configure os pipelines para orquestrar a execução dos notebooks no Databricks na ordem Fluxo de Dados -> orquestrador_silver
  * <img width="1332" height="448" alt="image" src="https://github.com/user-attachments/assets/e5feee72-1e05-4da6-94cc-b33f48ab8c44" />
  
  * Crie um gatilho para atualizar o pipeline de dados.
  * <img width="625" height="600" alt="image" src="https://github.com/user-attachments/assets/fd3aaf32-b0f1-4bc2-8620-b4755914d153" />
# Saída 
Essa é a saída para um dos indicadores
 <img width="1339" height="415" alt="image" src="https://github.com/user-attachments/assets/6286dfb8-0df0-445f-9ca6-7f96429dd500" />

