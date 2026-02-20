# Modelo Entidade-Relacional (MER)
O modelo relacional foi projetado para garantir a integridade referencial e o suporte a transações ACID no sistema operacional da empresa.

## Entidades e Atributos
* **Clientes**: Contém dados cadastrais únicos (`ID`, `Nome`, `Email`, `Data_Cadastro`)
* **Produtos**: Contém dados dos produtos (`ID`, `Nome`, `Categoria`, `Preço`).
* **Vendas**: Registro de cabeçalho da transação, vinculado a um cliente (`ID`, `Cliente_ID`, `Data da Venda`, `Total`).
* **ItensVenda**: Detalhamento da venda (tabela associativa), permitindo o relacionamento N:N entre Vendas e Produtos (`ID`, `Venda_ID`, `Produto_ID`, `Quantidade`, `Preço Unitário`).

## Relacionamentos
* **Clientes -> Vendas**: 1:N (Um cliente pode realizar várias compras).
* **Vendas -> ItensVenda**: 1:N (Uma venda pode conter vários produtos).
* **Produtos -> ItensVenda**: 1:N (Um produto pode aparecer em diferentes itens de venda).

## Diagrama MER
![Diagrama MER](../img/MER.png)
