# Arquitetura do Data Lakehouse
O objetivo desta arquitetura é centralizar dados operacionais (SQL), semiestruturados (NoSQL) e históricos em um único repositório analítico.

## Estrutura de Camadas (Medalhão)
1.  **Raw Zone (Bronze)**: Armazena os dados brutos conforme extraídos das fontes originais (ex: dump do MongoDB, logs do Cassandra).
2.  **Cleansed Zone (Prata)**: Dados processados, sem duplicidade e padronizados (ex: padronização de datas e limpeza de strings).
3.  **Business Zone (Ouro)**: Tabelas agregadas e otimizadas para consumo final em ferramentas de BI como Power BI.

## Tecnologias Sugeridas
* **Armazenamento**: Amazon S3 ou Azure Data Lake Storage.
* **Processamento**: Apache Spark ou Databricks para as transformações entre camadas.
* **Consulta**: Amazon Athena ou Google BigQuery para análises rápidas via SQL.

## Diagrama Data Lakehouse
![Data Lakehouse](../img/diagrama_lakehouse.png)

## Fluxo de Integração entre Camadas
A integração ocorre de forma fluida através de pipelines de dados que movem a informação do estado bruto para o valor de negócio. Para essa integração, foram utilizadas as seguintes ferramentas: **Amazon S3** (Armazenamento), **Apache Spark** (Processamento) e **Amazon Athena** (Consulta).

Logo abaixo, detalhamos o fluxo utilizando essas ferramentas:

* **Ingestão (Raw -> Bronze):** O Apache Spark extrai os dados dos bancos operacionais (SQL e NoSQL) e os deposita no Amazon S3 na camada Bronze em seu formato original para garantir um histórico imutável.
* **Processamento (Bronze -> Prata):** O Spark lê os arquivos da Bronze, realiza a limpeza (remoção de duplicatas, tratamento de nulos e tipos) e converte os dados para o formato Parquet (colunar), salvando-os na camada Prata do S3 para maior eficiência de leitura.
* **Refinamento (Prata -> Gold):** O Spark aplica as regras de negócio, como o cálculo de KPIs de vendas e agregações por perfil de cliente, salvando os dados finais na camada Ouro.
* **Consumo (Analytics):** O Amazon Athena cataloga esses dados da camada Ouro, permitindo que ferramentas de BI (como o Power BI) ou analistas realizem consultas SQL instantâneas sobre os dados refinados, concluindo o ciclo do Lakehouse.
