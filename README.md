# BD-E-COMMERCE

### É um projeto conceitual de banco de dados E-COMMERCE

##### Diagrama Plantuml

![iagram Image Link](https://www.plantuml.com/plantuml/png/fLJDQjj04BxlKsnzILjmGg2z21fYJ4nJWfiwnbUnrKwIXLsjkrfHQEZJz907yOjLYcObswEiREBJpe_d-sRcqrmMNZXV6itU-KSmm8LH3u8nhxm6VZMUMcF0PS3OsGbVYf-W1Pzg1Ra7VdB6Z5YtvXExbk7zvO9VpvTiRitBUpLPJBzE5ky_VVvG9LKPwbvbOlEy-MVtmv1BSB1v9e6_snHkGIffaK1ZlE3Z4-7llF1bmIl7klQJaXAApAbU6jX8IbgQEMYCsSttoNAFbREozBP0Nes9nF2DLK8cWHKU7gnJuWYgAw6jYqvhPbqE6KZhS6VRdffTPmQ22_6dXhgpcHAQi9pVVei2Bcl9A6Vv2d9PbqNOu4yRFw87BpeFut1ZCw6Z9AuARt-LhKo3MIE6Dm8DrvB05w15fcmk37ZRxXQ2_16bocfqdM96-YYAj97b4mi-eeSc8Mq57Fm_If5x9OKCN0-crQsKhBoXr8fpAz2d1CAvE9RAWMeWn6YSQ2N2ykqZH9KWs-rzOYIoKCn8Ewt5wMnnoAigcJNjNOLmu2eYw4kIxYwDfVsTZoymAKd8vKhuw7p4H_pyzFJZYBy2XlHtmD1NWuNmk5nNK36H9mcToGu35l9QiOyrtFl1ilkVo4xHmQwwNTAkkX7I5G-tqoPsgyOnzPOZmZYu4V9THpRK_x7tD5FimNT_h8jsLZEZIENNhiXntT5J4LiOkI23tUwo8NzF4dfXSA83KCEtYiwY_brMiTBe_m00)

```plantuml
@startuml


title E-Commerce

/' Tabela Cliente '/
map Cliente {
IdCliente => INT
Nome => VARCHAR(45)
Identificação => VARCHAR(45)
endereço => VARCHAR(45)
}

/' Tabela Pedido'/
map Pedido {
IdPedido => INT
Status do pedido => VARCHAR(45)
descrição => VARCHAR(45)
Cliente_IdCliente => INT
Frete => FLOAT
}

/' Tabela Produtos'/
map Produto {
IdProduto => INT
Produtos => VARCHAR(45)
Categoria => VARCHAR(45)
descrição => VARCHAR(45)
Valor => VARCHAR(45)
}

/' Tabela Fornecedor '/
map Fornecedor {
IdFornecedor => INT
Razão Social => VARCHAR(45)
CNPJ => VARCHAR(45)
}

/' Tabela Terceiro Vendedor'/
map Terceiro_Vendedor {
IdTerceiroVendedor => INT
Razão Social => VARCHAR(45)
Local => VARCHAR(45)
}

/' Tabela Estoque '/
map Estoque {
IdEstoque => INT
Local => VARCHAR(45)
}

/' Tabela de Relacionameto Produto e Cliente'/
map Relação_Produto_has_Pedido{
Produto_IdProduto => INT
Pedido_IdPedido  => INT
Quantidade => INT
}

/' Tabela de Relacionameto Produto e Fornecedor'/
map Fornecedor_has_Produto {
Fornecedor_IdFornecedor => INT
Produto_IdProdutos => INT
}

/' Tabela de Relacionameto Produto e Terceiro Vendedor'/
map Terceiro_Vendedor_has_Produto {
Terceiro_Vendedor_IdTerceiroVendedor => INT
Produto_IdProdutos => INT
Quantidade => INT
}

/' Tabela de Relacionameto Produto e Estoque'/
map Produto_has_Estoque{
Produto_IdProduto => INT
Estoque_IdEstoque => INT
Quantidade => INT
}

/'Relacionamento com Cliente e Pedido '/
Cliente::IdCliente -down-> Pedido::Cliente_IdCliente: "1" " 1..*" 

/'Relacionamento com Produto e Pedido '/
Produto::IdProduto -up-> Relação_Produto_has_Pedido::Produto_IdProduto : "1" " 1..*"
Pedido::IdPedido -left-> Relação_Produto_has_Pedido::Pedido_IdPedido : "1" " 1..*"

/'Relacionamento com Produto e Estoque'/
Produto::IdProduto -down-> Produto_has_Estoque::Produto_IdProduto : "1" " 1..*"
Estoque::IdEstoque  -up-> Produto_has_Estoque::Estoque_IdEstoque : "1" " 1..*"

/'Relacionamento com Produto e Fornecedor'/
Produto::IdProduto -up-> Fornecedor_has_Produto::Produto_IdProdutos : "1" " 1..*"
Fornecedor::IdFornecedor -down-> Fornecedor_has_Produto::Fornecedor_IdFornecedor : "1" " 1..*"

/'Relacionamento com Produto e Terceiro Vendedor'/
Produto::IdProduto -down-> Terceiro_Vendedor_has_Produto::Produto_IdProdutos: "1" " 1..*"
Terceiro_Vendedor::IdTerceiroVendedor -up-> Terceiro_Vendedor_has_Produto::Terceiro_Vendedor_IdTerceiroVendedor : "1" " 1..*"

@enduml
```
