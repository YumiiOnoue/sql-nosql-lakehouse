# Desafio - Construindo uma solução completa de dados

### Objetivo
Integrar conceitos de modelagem, armazenamento e consulta de dados usando bancos relacionais, bancos NoSQL e uma solução Data Lakehouse, simulando um cenário real de uma empresa que gerencia produtos, clientes e transações.

### Cenário
Uma empresa de tecnologia está desenvolvendo um novo sistema para gerenciar seu estoque, acompanhar transações de vendas e entender o comportamento dos clientes. O sistema precisa combinar dados relacionais para controle operacional, dados NoSQL para análises flexíveis e um Data Lakehouse para centralizar os dados analíticos.

## Parte 1: Modelagem Relacional
Crie um Modelo Entidade-Relacionamento (MER) que represente os seguintes elementos:

* **Clientes** (ID, Nome, Email, Data de Cadastro).
* **Produtos** (ID, Nome, Categoria, Preço).
* **Vendas** (ID, Cliente_ID, Data da Venda, Total).
* **ItensVenda** (ID, Venda_ID, Produto_ID, Quantidade, Preço Unitário).

## Parte 2: Implementação SQL
Com base no MER criado, implemente as tabelas no banco de dados relacional e realize as seguintes operações:

* **Criar as tabelas** de acordo com o modelo.
* **Inserir dados iniciais** (pelo menos 5 registros em cada tabela).
* **Consultar os produtos** com preço superior a 100.
* **Atualizar a quantidade de um produto** em um pedido.
* **Remover um produto do estoque.**

**Tarefa:** Entregue um script SQL com a implementação.

## Parte 3: Aplicação dos Bancos NoSQL
Agora, a empresa precisa armazenar diferentes tipos de dados de forma flexível. Associe cada necessidade ao tipo de banco NoSQL mais adequado e explique sua escolha:

* **Banco de Documentos:** o sistema precisa armazenar detalhes dos produtos, incluindo especificações técnicas que variam por categoria.
* **Banco Chave-Valor:** o sistema precisa salvar sessões de usuários para autenticação rápida.
* **Banco de Grafos:** a empresa quer analisar recomendações baseadas nas conexões entre clientes e produtos comprados.
* **Banco de Colunas:** os logs de acessos ao sistema precisam ser armazenados de maneira otimizada para análises.

**Tarefa:** Para cada cenário, justifique sua escolha do banco NoSQL e forneça um exemplo de estrutura de dados.

## Parte 4: Arquitetura de Data Lakehouse
A empresa deseja centralizar os dados em uma solução Data Lakehouse, integrando dados operacionais (banco relacional), semiestruturados (NoSQL) e arquivos históricos.

**Tarefa:** Desenhe a arquitetura do Data Lakehouse, incluindo:

1. Zonas do Data Lakehouse:

* **Raw Zone:** armazena os dados brutos coletados dos bancos transacionais e NoSQL.
* **Cleansed Zone:** dados processados e padronizados para análises.
* **Business Zone:** dados preparados para consumo, otimizados para BI e relatórios.

2. Tecnologias possíveis:

* **Armazenamento:** Amazon S3, Google Cloud Storage, Azure Data Lake.
* **Processamento:** Apache Spark, Databricks, AWS Glue.
* **Consulta e BI:** Amazon Athena, Google BigQuery, Snowflake.

> Tarefa Extra - Escolha ferramentas e serviços para cada camada do Data Lakehouse e explique como elas se integram.

### ENTREGA
* MER desenhado (ferramenta ou à mão).
* Script SQL com as consultas.
* Justificativas e exemplos para os bancos NoSQL.
* Desenho da Arquitetura de Data Lakehouse.
* Explicação das tecnologias escolhidas.