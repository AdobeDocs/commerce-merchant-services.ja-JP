---
title: refineProduct クエリ
description: 「Adobe Commerce Catalog Service の「refineProduct」GraphQL クエリのリファレンスガイド。」
source-git-commit: 7edfdd71c0900a6bdc7c064a29a6cce405a361ab
workflow-type: tm+mt
source-wordcount: '1267'
ht-degree: 0%

---


# refineProduct クエリ

この `refineProduct` クエリによって、 `products` 複雑な製品に対して実行されたクエリ。 実行する前に `refineProduct` クエリを実行するには、 `products` クエリを実行し、次のリストを返すように応答を作成します。 `options` 内 `ComplexProductView` インラインフラグメント。 ショッパーがストアフロントで製品オプション（サイズや色など）を選択したら、 `refineProduct` クエリで、SKU と選択したオプション値 ID を入力として指定します。 複雑な製品の製品オプションの数に応じて、 `refineProduct` 買い物客が特定のバリアントを選択するまで、クエリを複数回おこないます。

クエリに `ComplexProductView` および `SimpleProductView` インラインフラグメント。 買い物客が必要なオプションをすべて選択していない場合、クエリは、選択したオプションと可能な残りのオプションに基づいて、選択されていないオプションの ID と、製品の最小価格および最大価格を返します。 買い物客が必要なオプションをすべて選択した場合、クエリは設定された価格を含む単純な製品に関する詳細を返します。

## 構文

```graphql
refineProduct(sku: String!, optionIds: [String!]!): ProductView
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

### 部分的に選択された複雑な製品に関する詳細を返す

次のクエリは、製品の中サイズバリアントに使用できるカラーオプションの詳細を返します `MH12`. の値 `optionIDs` 入力パラメーターは `products` クエリの [複雑な製品に関する詳細を返す](products.md#complex-product-example) 例：

**リクエスト：**

```graphql
query {
    refineProduct(optionIds: ["Y29uZmlndXJhYmxlLzE4Ni8xNzc="], sku: "MH12") {
        __typename
        id
        sku
        name
        url
        ... on SimpleProductView {
            price {
                final {
                    amount {
                        value
                    }
                }
                regular {
                    amount {
                        value
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
                        }
                    }
                    regular {
                        amount {
                            value
                        }
                    }
                }
                minimum {
                    final {
                        amount {
                            value
                        }
                    }
                    regular {
                        amount {
                            value
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
    "refineProduct": {
      "__typename": "ComplexProductView",
      "id": "VFVneE1nAFpHVm1ZWFZzZEEATXpSbE1qYzBNR0V0TnpRM015MDBZemc1TFRnM016QXROVGMwTURObVkyVXlOMkZsAGJXRnBibDkzWldKemFYUmxYM04wYjNKbABZbUZ6WlEAVFVGSFUxUkhNREExTlRjNU1ETTQ",
      "sku": "MH12",
      "name": "Ajax Full-Zip Sweatshirt 2",
      "url": "http://example.com/ajax-full-zip-sweatshirt.html",
      "options": [
        {
          "id": "color",
          "title": "Color",
          "required": false,
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
        }
      ],
      "priceRange": {
        "maximum": {
          "final": {
            "amount": {
              "value": 69
            }
          },
          "regular": {
            "amount": {
              "value": 69
            }
          }
        },
        "minimum": {
          "final": {
            "amount": {
              "value": 69
            }
          },
          "regular": {
            "amount": {
              "value": 69
            }
          }
        }
      }
    }
  }
}
```

### 完全に選択された複雑な製品の詳細を返す

次のクエリでは、買い物客はサイズと色の両方のオプションを選択しています。 応答には、対応するシンプルな製品の詳細が含まれます。

**リクエスト：**

```graphql
query {
    refineProduct(optionIds: ["Y29uZmlndXJhYmxlLzE4Ni8xNzc=", "Y29uZmlndXJhYmxlLzkzLzU5"], sku: "MH12") {
        __typename
        id
        sku
        name
        url
        ... on SimpleProductView {
            price {
                final {
                    amount {
                        value
                    }
                }
                regular {
                    amount {
                        value
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
                        }
                    }
                    regular {
                        amount {
                            value
                        }
                    }
                }
                minimum {
                    final {
                        amount {
                            value
                        }
                    }
                    regular {
                        amount {
                            value
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
    "refineProduct": {
      "__typename": "SimpleProductView",
      "id": "VFVneE1pMU5MVUpzZFdVAFpHVm1ZWFZzZEEATXpSbE1qYzBNR0V0TnpRM015MDBZemc1TFRnM016QXROVGMwTURObVkyVXlOMkZsAGJXRnBibDkzWldKemFYUmxYM04wYjNKbABZbUZ6WlEAVFVGSFUxUkhNREExTlRjNU1ETTQ",
      "sku": "MH12-M-Blue",
      "name": "Ajax Full-Zip Sweatshirt -M-Blue",
      "url": "http://example.com/catalog/product/view/id/235/s/ajax-full-zip-sweatshirt-m-blue/",
      "price": {
        "final": {
          "amount": {
            "value": 69
          }
        },
        "regular": {
          "amount": {
            "value": 69
          }
        }
      }
    }
  }
}
```

## 入力フィールド

SKU 値と、1 つ以上のオプション ID を入力として指定する必要があります。

| フィールド | データタイプ | 説明 |
|--- | --- | ---|
| `optionIds` | [文字列！]! | 買い物客が選択した製品オプションに割り当てられた ID のリスト（特定の色やサイズなど）。 |
| `sku` | 文字列！ | 複雑な製品の SKU。 |

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
