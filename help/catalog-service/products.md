---
title: 製品クエリ
description: 「Adobe Commerce Catalog Service の「products」GraphQL クエリのリファレンスガイドです。」
source-git-commit: d9b8c89f6d04aa9d569b450af2893b92938119ad
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 製品クエリ

Adobe Commerceのカタログサービス `products` クエリを実行すると、入力として指定された SKU に関する詳細が返されます。 このクエリは [`products` クエリ](https://devdocs.magento.com/guides/v2.4/graphql/queries/products.html) コアAdobe CommerceとMagento Open Sourceで提供される統合環境には、いくつかの違いがあります。

カタログサービスクエリでは、1 つ以上の SKU 値を入力として必要とします。 このクエリは主に、次のタイプのコンテンツをレンダリングするための情報を取得するように設計されています。

* 製品の詳細ページ — 指定した SKU で識別される製品に関する完全な詳細を指定できます。

* 製品の比較ページ — 名前、価格、画像など、複数の製品に関する選択した情報を取得できます。

この `ProductView` 出力オブジェクトはコアとは大きく異なります `products` クエリ `Products` 出力オブジェクト。 主な違いは次のとおりです。

* 製品は、単純なものか複雑なもののどちらかです。 シンプルな、仮想、ダウンロード可能な、ギフトカード製品は、 `SimpleProductView`. その他すべての製品タイプは、 `ComplexProductView`. シンプルな製品が価格を定義しています。 複雑な製品は価格帯がある。 複雑な製品は複数のシンプルな製品で構成されているので、シンプルな製品価格にアクセスできます。

* マーチャント定義属性は、トップレベルのコンテナに公開され、ストアフロントの役割を示します。 役割には、PDP で表示、PLP で表示、検索結果で表示が含まれます。

* 画像は最上位のコンテナとしてもアクセスでき、役割でフィルタリングできます。 画像には、基本、小、サムネールの役割を設定できます。

## 構文

```graphql
products (skus [String]) [ProductView]
```

## 必須ヘッダー

このクエリを実行するには、次の HTTP ヘッダーを指定する必要があります。

| ヘッダー | 説明 |
| --- | --- |
| `Magento-Customer-Group` | ストアフロントクライアントの場合、この値は `dataservices_customer_group` cookie. |
| `Magento-Environment-Id` | この値は、 **システム** > **Commerce Services コネクタ** > **SaaS 識別子** > **データスペース ID** または、 `bin/magento config:show services_connector/services_id/environment_id` コマンドを使用します。 |
| `Magento-Store-Code` | アクティブなストア表示に関連付けられたストアに割り当てられたコード。 例： `main_website_store`. |
| `Magento-Store-View-Code` | アクティブなストア表示に割り当てられたコード。 例： `default`. |
| `Magento-Website-Code` | アクティブなストア表示に関連付けられた Web サイトに割り当てられたコード。 例： `base`. |
| `X-Api-Key` | オンボーディングプロセス中に生成される一意のキー。 |

## 使用例

### 単純な製品に関する詳細を返す

次のクエリは、単純な製品に関する詳細を返します。

**リクエスト：**

```graphql
query {
  products(skus: ["24-MB02"]) {
    id
    sku
    name
    url
    description
    shortDescription
    attributes(roles: ["visible in Search"]) {
      name
      label
      value
      roles
    }
    ... on SimpleProductView {
      price {
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
```

**応答：**

```json
{
  "data": {
    "products": [
      {
        "id": "TWpRdFRVSXdNZwBaR1ZtWVhWc2RBAE16UmxNamMwTUdFdE56UTNNeTAwWXpnNUxUZzNNekF0TlRjME1ETm1ZMlV5TjJGbABiV0ZwYmw5M1pXSnphWFJsWDNOMGIzSmwAWW1GelpRAFRVRkhVMVJITURBMU5UYzVNRE00",
        "sku": "24-MB02",
        "name": "Fusion Backpack 567890",
        "url": "http://example.com/fusion-backpack.html",
        "description": "<p>With the Fusion Backpack strapped on, every trek is an adventure - even a bus ride to work. That's partly because two large zippered compartments store everything you need, while a front zippered pocket and side mesh pouches are perfect for stashing those little extras, in case you change your mind and take the day off.</p>\r\n<ul>\r\n<li>Durable nylon construction.</li>\r\n<li>2 main zippered compartments.</li>\r\n<li>1 exterior zippered pocket.</li>\r\n<li>Mesh side pouches.</li>\r\n<li>Padded, adjustable straps.</li>\r\n<li>Top carry handle.</li>\r\n<li>Dimensions: 18\" x 10\" x 6\".</li>\r\n</ul>",
        "shortDescription": "",
        "attributes": [
          {
            "name": "activity",
            "label": "Activity",
            "value": [
              "Hiking",
              "School",
              "Yoga"
            ],
            "roles": [
              "visible in PDP",
              "visible in compare list",
              "visible in Search"
            ]
          },
          {
            "name": "features_bags",
            "label": "Features",
            "value": [
              "Hydration Pocket",
              "Audio Pocket",
              "Waterproof",
              "Lightweight"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "material",
            "label": "Material",
            "value": [
              "Burlap",
              "Nylon",
              "Polyester"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "strap_bags",
            "label": "Strap/Handle",
            "value": [
              "Adjustable",
              "Double",
              "Padded"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "style_bags",
            "label": "Style Bags",
            "value": [
              "Backpack",
              "Laptop"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          }
        ],
        "price": {
          "regular": {
            "amount": {
              "value": 59,
              "currency": "USD"
            }
          }
        }
      }
    ]
  }
}
```

### 複雑な製品に関する詳細を返す {#complex-product-example}

次のクエリは、設定可能な製品に関する詳細を返します。

**リクエスト：**

```graphql
query {
  products(skus: ["MH12"]) {
    __typename
    id
    sku
    name
    url
    description
    shortDescription
    attributes(roles: ["visible in Search"]) {
      name
      label
      value
      roles
    }
    ... on ComplexProductView {
      priceRange {
        maximum {
          regular {
            amount {
              value
              currency
            }
          }
        }
        minimum {
          regular {
            amount {
              value
              currency
            }
          }
        }
      }
      options {
        id
        required
        title
        values {
          id
          title
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
    "products": [
      {
        "__typename": "ComplexProductView",
        "id": "VFVneE1nAFpHVm1ZWFZzZEEATXpSbE1qYzBNR0V0TnpRM015MDBZemc1TFRnM016QXROVGMwTURObVkyVXlOMkZsAGJXRnBibDkzWldKemFYUmxYM04wYjNKbABZbUZ6WlEAVFVGSFUxUkhNREExTlRjNU1ETTQ",
        "sku": "MH12",
        "name": "Ajax Full-Zip Sweatshirt 2",
        "url": "http://example.com/ajax-full-zip-sweatshirt.html",
        "description": "<p>The Ajax Full-Zip Sweatshirt makes the optimal layering or outer piece for archers, golfers, hikers and virtually any other sportsmen. Not only does it have top-notch moisture-wicking abilities, but the tight-weave fabric also prevents pilling from repeated wash-and-wear cycles.</p>\r\n<p>&bull; Mint striped full zip hoodie.<br />&bull; 100% bonded polyester fleece.<br />&bull; Pouch pocket.<br />&bull; Rib cuffs and hem. <br />&bull; Machine washable.</p>",
        "shortDescription": "",
        "attributes": [
          {
            "name": "climate",
            "label": "Climate",
            "value": [
              "All-Weather",
              "Cool",
              "Indoor",
              "Spring",
              "Windy"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "customattribute",
            "label": "customAttribute",
            "value": "asd",
            "roles": [
              "visible in PDP",
              "visible in PLP",
              "visible in Search"
            ]
          },
          {
            "name": "material",
            "label": "Material",
            "value": [
              "Fleece",
              "Polyester"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "pattern",
            "label": "Pattern",
            "value": "Striped",
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "testtttattribute",
            "label": "testtttAttribute",
            "value": "asd",
            "roles": [
              "visible in PDP",
              "visible in PLP",
              "visible in Search"
            ]
          }
        ],
        "priceRange": {
          "maximum": {
            "regular": {
              "amount": {
                "value": 69,
                "currency": "USD"
              }
            }
          },
          "minimum": {
            "regular": {
              "amount": {
                "value": 69,
                "currency": "USD"
              }
            }
          }
        },
        "options": [
          {
            "id": "color",
            "required": false,
            "title": "Color",
            "values": [
              {
                "id": "Y29uZmlndXJhYmxlLzkzLzU5",
                "title": "Blue"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzkzLzY3",
                "title": "Red"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzkzLzYy",
                "title": "Green"
              }
            ]
          },
          {
            "id": "size",
            "required": false,
            "title": "Size",
            "values": [
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzU=",
                "title": "XS"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzY=",
                "title": "S"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzc=",
                "title": "M"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzg=",
                "title": "L"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzk=",
                "title": "XL"
              }
            ]
          }
        ]
      }
    ]
  }
}
```

## 出力フィールド

この `ProductView` return オブジェクトは、次のフィールドを含むことができるインターフェイスです。 これは、 [`SimpleProductView`](#SimpleProductView-type) および [`ComplexProductView`](#ComplexProductView-type) タイプ。

| フィールド | データタイプ | 説明 |
|--- | --- | ---|
| `attributes(roles: [String])` | [ProductViewAttribute] | ストアフロント用に指定されたマーチャント定義属性のリスト。 |
| `description` | 文字列 | 製品の詳細な説明。 |
| `id` | ID! | 複合キーとして生成された、ロケールごとに一意の製品 ID。 |
| `images(roles: [String])` | [ProductViewImage] | 製品に定義された画像のリスト。 |
| `metaDescription` | 文字列 | 検索結果リストの製品の概要です。 |
| `metaKeyword` | 文字列 | 検索エンジンにのみ表示されるキーワードのコンマ区切りリスト。 |
| `metaTitle` | 文字列 | ブラウザーのタイトルバーとタブおよび検索結果リストに表示される文字列。 |
| `name` | 文字列 | 製品名。 |
| `shortDescription` | 文字列 | 製品の概要。 |
| `sku` | 文字列 | 製品 SKU。 |
| `url` | 文字列 | 製品の正規 URL。 |

### ComplexProductView タイプ {#ComplexProductView-type}

この `ComplexProductView` type は、バンドル、設定可能、およびグループ製品を表します。 価格の値は選択したオプションに基づいて異なる場合があるので、複雑な製品価格が価格範囲として返されます。 タイプはを実装します `ProductView`.

| フィールド | データタイプ | 説明 |
|--- | --- | ---|
| `attributes(roles: [String])` | [ProductViewAttribute] | ストアフロント用に指定されたマーチャント定義属性のリスト。 |
| `description` | 文字列 | 製品の詳細な説明。 |
| `id` | ID! | 複合キーとして生成された、ロケールごとに一意の製品 ID。 |
| `images(roles: [String])` | [ProductViewImage] | 製品に定義された画像のリスト。 |
| `metaDescription` | 文字列 | 検索結果リストの製品の概要です。 |
| `metaKeyword` | 文字列 | 検索エンジンにのみ表示されるキーワードのコンマ区切りリスト。 |
| `metaTitle` | 文字列 | ブラウザーのタイトルバーとタブおよび検索結果リストに表示される文字列。 |
| `name` | 文字列 | 製品名。 |
| `options` | [ProductViewOption] | 選択可能なオプションのリスト。 |
| `priceRange` | ProductViewPriceRange | 複雑な製品に対して可能な幅広い価格。 |
| `shortDescription` | 文字列 | 製品の概要。 |

### 価格のタイプ

この `Price type` 複雑な製品の単純な製品または価格範囲の一部の価格を定義します。 価格調整のリストを含めることができます。

| フィールド | データタイプ | 説明 |
|--- | --- | ---|
| `amount` | ProductViewMoney | 商品の金額と通貨コードが含まれます。 |

### PriceAdjustment タイプ

この `PriceAdjustment` type は、価格調整の金額と種類を指定します。 コード値の例： `weee`.

| フィールド | データタイプ | 説明 |
|--- | --- | ---|
| `amount` | 浮動小数 | 価格調整の金額。 |
| `code` | 文字列 | 価格調整のタイプを識別します。 |

### ProductViewAttribute タイプ

この `ProductViewAttribute` type は、ストアフロントに表示される顧客定義属性のコンテナです。

| フィールド | データタイプ | 説明 |
|--- | --- | ---|
| `label` | 文字列 | 属性のラベル。 |
| `name` | 文字列！ | 属性コードの名前。 |
| `roles` | [文字列] | ストアフロントの属性に指定された役割（「PLP で表示」、「PDP で表示」、「検索で表示」など）。 |
| `value` | JSON | 属性値（任意のタイプ）。 |

### ProductViewImage タイプ

この `ProductViewImage` タイプには、製品画像に関する詳細が含まれます。

| フィールド | データタイプ | 説明 |
|--- | --- | ---|
| `label` | 文字列 | 商品画像の表示ラベル。 |
| `roles` | [文字列] | 画像の使用方法を示すリスト。 可能 `image`, `small_image`または `thumbnail`. |
| `url` | 文字列！ | 製品画像の URL。 |

### ProductViewMoney タイプ

この `ProductViewMoney` 「タイプ」は、数値や通貨コードを含む金額を定義します。

| フィールド | データタイプ | 説明 |
|--- | --- | ---|
| `currency` | ProductViewCurrency | 3 文字の通貨コード（USD や EUR など）。 |
| `value` | 浮動小数 | 金額を表す数値。 |

### ProductViewOption タイプ

製品オプションを使用すると、特定のオプション値を選択して製品を設定できます。 1 つまたは複数のオプションを選択すると、特定のシンプルな製品が示されます。

| フィールド | データタイプ | 説明 |
|--- | --- | ---|
| `id` | ID | オプションの ID。 |
| `multi` | ブール値 | オプションで複数選択を許可するかどうかを示します。 |
| `required` | ブール値 | オプションを選択する必要があるかどうかを示します。 |
| `title` | 文字列 | オプションの表示名。 |
| `values` | [ProductViewOptionValue!] | 使用可能なオプション値のリスト。 |

### ProductViewOptionValue インターフェイス

この `ProductViewOptionValue` インターフェイスは、 `ProductViewOptionValueProduct` および `ProductViewOptionValueConfiguration` タイプ。

| フィールド | データタイプ | 説明 |
|--- | --- | ---|
| `id` | ID | オプション値の ID。 |
| `title` | 文字列 | オプション値の表示名。 |

### ProductViewOptionValueConfiguration タイプ

この `ProductViewOptionValueConfiguration` タイプは、 `ProductViewOptionValue` 設定値の場合。

| フィールド | データタイプ | 説明 |
|--- | --- | ---|
| `id` | ID | オプション値の ID。 |
| `title` | 文字列 | オプション値の表示名。 |

### ProductViewOptionValueProduct type

この `ProductViewOptionValueProduct` タイプは、 `ProductViewOptionValue` これにより、単純な製品に関する詳細が追加されます。

| フィールド | データタイプ | 説明 |
|--- | --- | ---|
| `id` | ID | オプション値の ID。 |
| `title` | 文字列 | オプション値の表示名。 |
| `product` | SimpleProductView | シンプルな製品の詳細。 |

### ProductViewPrice タイプ

この `ProductViewPrice` 「タイプ」は、シンプルな製品に固有の基本製品価格表示を提供します。

| フィールド | データタイプ | 説明 |
|--- | --- | ---|
| `final` | 価格 | 割引後の価格の値（パーソナライズされたプロモーションを除く）。 |
| `regular` | 価格 | 商人が指定した基本製品価格。 |
| `roles` | [文字列] | 価格を表示するか非表示にするかを指定します。 |

### ProductViewPriceRange タイプ

この `ProductViewPriceRange` 「タイプ」には、複雑な製品の最小価格と最大価格が表示されます。

| フィールド | データタイプ | 説明 |
|--- | --- | ---|
| `maximum` | ProductViewPrice | 最大価格。 |
| `minimum` | ProductViewPrice | 最小価格。 |

### SimpleProductView タイプ {#SimpleProductView-type}

この `SimpleProductView` type は、bundle、configurable、group を除くすべての製品タイプを表します。 単純な製品価格には、価格範囲が含まれません。 `SimpleProductView` 実装 `ProductView`.

| フィールド | データタイプ | 説明 |
|--- | --- | ---|
| `attributes(roles: [String])` | [ProductViewAttribute] | ストアフロント用に指定されたマーチャント定義属性のリスト。 |
| `description` | 文字列 | 製品の詳細な説明。 |
| `id` | ID! | 複合キーとして生成された、ロケールごとに一意の製品 ID。 |
| `images(roles: [String])` | [ProductViewImage] | 製品に定義された画像のリスト。 |
| `metaDescription` | 文字列 | 検索結果リストの製品の概要です。 |
| `metaKeyword` | 文字列 | 検索エンジンにのみ表示されるキーワードのコンマ区切りリスト。 |
| `metaTitle` | 文字列 | ブラウザーのタイトルバーとタブおよび検索結果リストに表示される文字列。 |
| `name` | 文字列 | 製品名。 |
| `price` | ProductViewPrice | 基本製品価格表示。 |
| `shortDescription` | 文字列 | 製品の概要。 |
| `sku` | 文字列 | 製品 SKU。 |
| `url` | 文字列 | 製品の正規 URL。 |
