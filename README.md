# Sistema Híbrido de Dados: Integração SQL, NoSQL e Data Lakehouse
## Sobre o Projeto
Este projeto simula um cenário real de uma empresa de tecnologia que necessita gerenciar estoque, transações de vendas e comportamento de clientes utilizando uma arquitetura híbrida. O objetivo é demonstrar a aplicação prática de modelagem relacional para operações críticas, bancos NoSQL para necessidades específicas de escala e flexibilidade, e a consolidação de dados em um Data Lakehouse para fins analíticos.

O projeto foi desenvolvido como parte do desafio do módulo de Fundamentos de Dados Relacionais e NoSQL da Pós-Graduação em Data Analytics da FIAP.

## Arquitetura da Solução
**1. Camada Relacional (SQL)**
Utilizada para o controle operacional e garantia de integridade transacional (ACID).

* **Modelo Entidade-Relacionamento (MER):** Estruturado com tabelas de Clientes, Produtos, Vendas e Itens de Venda.
* **Operações:** Scripts automatizados para criação de tabelas, inserção de dados e consultas de negócio (ex: filtragem de produtos por preço e atualização de estoque).
+2

**2. Camada NoSQL (Poliglota)**
Para atender requisitos que o modelo relacional não supre com eficiência, foram implementados quatro modelos NoSQL:

Necessidade | Banco Escolhido | Justificativa Técnica
----------- | --------------- | ---------------------
Documentos | MongoDB | Flexibilidade para armazenar especificações técnicas variadas por categoria de produto sem um esquema rígido.
Chave-Valor | Redis | Ultrabaixa latência para gestão de sessões de usuários e autenticação rápida.
Grafos | Neo4j | Eficiência em percorrer relacionamentos complexos para motores de recomendação ("quem comprou X também comprou Y").
Colunas | Cassandra | Otimização de escrita e leitura em massa para logs de acesso distribuídos.

**3. Data Lakehouse**
Centralização de dados brutos e refinados para BI e Machine Learning.

* **Raw Zone (Bronze):** Dados brutos do SQL e NoSQL.
* **Cleansed Zone (Prata):** Dados limpos, padronizados e enriquecidos.
* **Business Zone (Ouro):** Agregados e otimizados para consumo em ferramentas como Power BI e Google BigQuery.

## Tecnologias Utilizadas
* **Linguagens:** Python e SQL.
* **Bancos e Bibliotecas:** 
    * mongomock: Simulação de MongoDB para testes locais.
    * fakeredis: Simulação de servidor Redis em memória.
    * networkx: Modelagem e visualização de estruturas de grafos.
    * astrapy: Integração real com Apache Cassandra via DataStax Astra DB.
* **Configuração:** Uso de arquivos .toml para gestão segura de segredos e configurações de ambiente.

## Estrutura do Repositório

```
├── arquitetura/
|   └── arquitetura_data_lakehouse   # Detalhamento técnico da estratégia de camadas e integração de dados
├── img/
|   ├── MER.png                      # Diagrama de Entidade-Relacionamento
|   ├── grafo_cliente_produto.png    # Grafo relacional entre cliente e produto
|   └── diagrama_lakehouse.png       # Arquitetura do Lakehouse
├── modelagem/ 
|   └── modelo_entidade_relacional   # Documentação dos conceitos, entidades e regras de negócio do modelo SQL
├── sql/
│   ├── 1.script_create_table.sql    # DDL - Estrutura do banco
│   ├── 2.script_insert_into.sql     # DML - Dados iniciais
│   └── 3.script_queries_drop.sql    # Consultas e manutenção
├── nosql/
│   ├── 1.banco_documentos.ipynb     # Exemplo MongoDB
│   ├── 2.banco_chave_valor.ipynb    # Exemplo Redis
│   ├── 3.banco_grafos.ipynb         # Recomendação com NetworkX
│   └── 4.banco_colunas.ipynb        # Logs com Cassandra/AstraDB
|   ├──config/
|   ├── settings.toml                # Configurações de endpoint
│   └── .secrets.example.toml        # Modelo de credenciais (sem dados reais)
├── .gitignore                       # Para ignorar a pasta .venv e o .secrets.toml real
├── requirements.txt                 # Lista de dependências do projeto
└── README.md                        # Documentação completa do projeto

```

## Como Executar
Siga os passos abaixo para configurar o ambiente e executar os notebooks em sua máquina local:

**Clone o repositório:**

```PowerShell
git clone https://github.com/YumiiOnoue/sql_nosql_lakehouse.git
cd sql_nosql_lakehouse
```

**Crie e ative um ambiente virtual (Recomendado):**

```PowerShell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

**Instale as dependências a partir do requirements.txt:**

```PowerShell
pip install -r requirements.txt
```

**Configuração de Segredos:**
* Navegue até a pasta config/.
* Renomeie o arquivo `.secrets.toml`.
* Insira suas credenciais do Astra DB (Cassandra) para habilitar o notebook de logs.

**Execute os Notebooks:**
* Abra o VS Code ou Jupyter Lab e execute os arquivos na pasta nosql/ para ver as simulações NoSQL em funcionamento.

---
Desenvolvido por: Erica Yumi Onoue