---
title: productSearch クエリ
description: 「Adobe Commerce Catalog Service の「productSearch」GraphQL クエリのリファレンスガイド。」
source-git-commit: 7edfdd71c0900a6bdc7c064a29a6cce405a361ab
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---


# productSearch クエリ

Adobe Commerceのカタログサービス `productSearch` クエリでは、LiveSearch を使用して、入力として指定された SKU に関する詳細を返すことができます。 このクエリは [`productSearch` クエリ](https://devdocs.magento.com//live-search/product-search.html)を返す場合、LiveSearch は `productView` オブジェクト。 詳しくは、 [`productSearch` クエリ](https://devdocs.magento.com//live-search/product-search.html) トピックを参照してください。

## 構文

```graphql
productSearch(
    phrase: String!
    page_size: Int = 20
    current_page: Int = 1
    filter: [SearchClauseInput!]
    sort: [ProductSearchSortInput!]
): ProductSearchResponse!
```

## 必須ヘッダー

このクエリを実行するには、次の HTTP ヘッダーを指定する必要があります。

| ヘッダー | 説明 |
|--- | ---|
| `Magento-Customer-Group` | ストアフロントクライアントの場合、この値は `dataservices_customer_group` cookie. |
| `Magento-Environment-Id` | この値は、 **システム** > **Commerce Services コネクタ** > **SaaS 識別子** > **データスペース ID** または、 `bin/magento config:show services_connector/services_id/environment_id` コマンドを使用します。 |
| `Magento-Store-Code` | アクティブなストア表示に関連付けられたストアに割り当てられたコード。 例： `main_website_store`. |
| `Magento-Store-View-Code` | アクティブなストア表示に割り当てられたコード。 例： `default`. |
| `Magento-Website-Code` | アクティブなストア表示に関連付けられた Web サイトに割り当てられたコード。 例： `base`. |
| `X-Api-Key` | オンボーディングプロセス中に生成される一意のキー。 |

## 使用例

次の例では、クエリは前の例と同じ製品に関する情報を返します。 ただし、カタログサービス内の項目情報を返すように構築されています `productView` コアの代わりにオブジェクト `product` オブジェクト。 価格情報は、製品タイプに応じて異なります。 簡潔にするために、ファセット情報は表示されません。

**リクエスト：**

```graphql
{
  productSearch(
    phrase: "bag"
    sort: [
      {
        attribute: "price"
        direction: DESC }]
    page_size: 9
  ) {
    page_info {
      current_page
      page_size
      total_pages
    }
    items {
      productView {
        name
        sku
        ... on SimpleProductView {
          price {
            final {
              amount {
                value
                currency
              }
            }
            regular {
              amount {
                value
                currency
              }
            }
          }
        }
        ... on ComplexProductView {
          options {
            id
            title
            required
            values {
              id
              title
            }
          }
          priceRange {
            maximum {
              final {
                amount {
                  value
                  currency
                }
              }
              regular {
                amount {
                  value
                  currency
                }
              }
            }
            minimum {
              final {
                amount {
                  value
                  currency
                }
              }
              regular {
                amount {
                  value
                  currency
                }
              }
            }
          }
        }
      }
    }
  }
}
```

**応答：**

```json
{
  "data": {
    "productSearch": {
      "page_info": {
        "current_page": 1,
        "page_size": 9,
        "total_pages": 3
      },
      "items": [
        {
          "productView": {
            "name": "Impulse Duffle",
            "sku": "24-UB02",
            "price": {
              "final": {
                "amount": {
                  "value": 74,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 74,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Fusion Backpack 567890",
            "sku": "24-MB02",
            "price": {
              "final": {
                "amount": {
                  "value": 59,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 59,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Rival Field Messenger",
            "sku": "24-MB06",
            "price": {
              "final": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Push It Messenger Bag",
            "sku": "24-WB04",
            "price": {
              "final": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Overnight Duffle",
            "sku": "24-WB07",
            "price": {
              "final": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Wayfarer Messenger Bag 987",
            "sku": "24-MB05",
            "price": {
              "final": {
                "amount": {
                  "value": 44,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 44,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Driven Backpack",
            "sku": "24-WB03",
            "price": {
              "final": {
                "amount": {
                  "value": 36,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 36,
                  "currency": "USD"
                }
              }
            }
          }
        }
      ]
    }
  }
}
```
