# Sobre este projeto

Este projeto é um template baseado no template do create-react-app em typescript para fins de processo seletivo

# API p/ usar

### Lista todos os SKUs 
`GET http://demotestalb-88047269.us-east-2.elb.amazonaws.com/product`
```
{
"status": number,
"success": boolean,
"results": [{
    "key": string,
    "product_key": string,
    "inventory": number,
    "price": string, # em centavos
    "created_at": string, # timestamp
    "updated_at": string, # timestamp
    "product": {
        "key": number,
        "name": string,
        "image": string,
        "created_at": string, # timestamp
        "updated_at": string # timestamp
    }
}...]}
```

### Retorna um carrinho
`GET http://demotestalb-88047269.us-east-2.elb.amazonaws.com/cart/{key}`
Se {key} não existir, retorna um novo carrinho
```
{
    "status": number,
    "success": string,
    "data": {
        "key": string,
        "cartSkus": [{
          "key": string,
          "qty": number,
          "cart_key": string,
          "sku_key": string,
          "sku": {
            "key": string,
            "product_key": string,
            "inventory": number,
            "price": string, # em centavos
            "created_at": string, # timestamp
            "updated_at": string, # timestamp
            "product": {
                "key": number,
                "name": string,
                "image": string,
                "created_at": string, # timestamp
                "updated_at": string # timestamp
            }
          },
          "created_at": string, # timestamp
          "updated_at": string  # timestamp
        }, ... ],
        "created_at": string, # timestamp
        "updated_at": string  # timestamp
    }
}
```


### Adiciona um produto a um carrinho
`POST http://demotestalb-88047269.us-east-2.elb.amazonaws.com/cart/{key}/product`
```
{
  "sku_key": string,
  "qty": number
}
```

### Edita um produto em um carrinho
`PUT http://demotestalb-88047269.us-east-2.elb.amazonaws.com/cart/{key}/product/{cart_sku_key}`
```
{
  "qty": number
}
```

### Deleta um produto de um carrinho
`DELETE http://demotestalb-88047269.us-east-2.elb.amazonaws.com/cart/{key}/product/{cart_sku_key}`





