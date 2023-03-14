---
title: '[!DNL Catalog Service and API Mesh]'
description: '''[!DNL API Mesh] 「for Adobe Commerceは、共通のGraphQLエンドポイントを使用して複数のデータソースを統合する方法を提供します。」'
source-git-commit: 41d6bed30769d3864d93d6b3d077987a810890cc
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# [!DNL Catalog Service and API Mesh]

この [Adobe Developer App Builder の API メッシュ](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) を使用すると、開発者は、Adobe I/O Runtimeを使用して、プライベートまたはサードパーティの API やその他のインターフェイスをAdobe製品と統合できます。

![カタログのアーキテクチャ図](assets/catalog-service-architecture-mesh.png)

API メッシュをカタログサービスで使用する最初の手順は、API メッシュをインスタンスに接続することです。 詳しい手順については、 [メッシュを作成する](https://developer.adobe.com/graphql-mesh-gateway/gateway/create-mesh/).

設定を完了するには、 [Adobe Developer CLI パッケージ](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/).

Adobe I/O Runtimeでメッシュを設定したら、次のコマンドを実行して、 `CommerceCatalogServiceGraph` メッシュにソースを設定します。

```bash
aio api-mesh:source:install "CommerceCatalogServiceGraph" -f variables.json
```

ここで、 `variables.json` は、Adobe I/O Runtimeの一般的に使用される値を保存する個別のファイルです。
例えば、API キーはファイル内に保存できます。

```json
{
    "CATALOG_SERVICE_API_KEY":"your_api_key"
}
```

このコマンドを実行した後、API メッシュを介してカタログサービスを実行する必要があります。 次を実行できます。 `aio api-mesh:get` コマンドを使用して、更新したメッシュの設定を表示します。

## API メッシュの使用

API メッシュを使用すると、外部のデータソースを使用してAdobe Commerceインスタンスを強化できます。 また、既存のコマースデータを設定して新しい機能を有効にする場合にも使用できます。

この例では、API Mesh を使用して、Adobe Commerceの階層価格を有効にします。
を `name `, `endpoint`、および `x-api-key` 値。

```json
{
  "meshConfig": {
    "sources": [
      {
        "name": "<Commerce Instance Name>",
        "handler": {
          "graphql": {
            "endpoint": "<Adobe Commerce GraphQL endpoint>"
          }
        },
        "transforms": [
            {
                "prefix": {
                    "includeRootOperations": true,
                    "value": "Core_"
                }
            }
        ]
      },
      {
        "name": "CommerceCatalogServiceGraph",
        "handler": {
          "graphql": {
            "endpoint": "https://commerce.adobe.io/catalog-service/graphql/",
            "operationHeaders": {
              "Magento-Store-View-Code": "{context.headers['magento-store-view-code']}",
              "Magento-Website-Code": "{context.headers['magento-website-code']}",
              "Magento-Store-Code": "{context.headers['magento-store-code']}",
              "Magento-Environment-Id": "{context.headers['magento-environment-id']}",
              "Magento-Customer-Group": "{context.headers['magento-customer-group']}"
            },
            "schemaHeaders": {
              "x-api-key": "<YOUR API-KEY>"
            }
          }
        }
      }
    ],
    "additionalTypeDefs": "extend interface ProductView {\n  price_tiers: [Core_TierPrice]\n}\n extend type SimpleProductView {\n  price_tiers: [Core_TierPrice]\n}\n extend type ComplexProductView {\n  price_tiers: [Core_TierPrice]\n}\n",
    "additionalResolvers": [
        {  
            "targetTypeName": "ProductView",
            "targetFieldName": "price_tiers",
            "sourceName": "MagentoStageCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{\n    items {\n  sku\n    price_tiers {\n        quantity,\n        final_price {\n          value\n          currency\n        }\n      }\n    }\n  }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].price_tiers"
        },
        {  
            "targetTypeName": "SimpleProductView",
            "targetFieldName": "price_tiers",
            "sourceName": "MagentoStageCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{\n    items {\n  sku\n    price_tiers {\n        quantity,\n        final_price {\n          value\n          currency\n        }\n      }\n    }\n  }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].price_tiers"
        },
        {  
            "targetTypeName": "ComplexProductView",
            "targetFieldName": "price_tiers",
            "sourceName": "MagentoStageCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{\n    items {\n  sku\n    price_tiers {\n        quantity,\n        final_price {\n          value\n          currency\n        }\n      }\n    }\n  }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].price_tiers"
        }
    ]
   }
}
```

設定が完了したら、メッシュに対して階層型の価格を問い合わせます。

```json
query {
  products(skus: ["24-MB04"]) {
    sku
    description
    price_tiers {
        quantity
        final_price {
          value
          currency
        }
      }
    ... on SimpleProductView {
      id
       
      price {
        final {
          amount {
            value
          }
        }
      }
    }
  }
}
```
