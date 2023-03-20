---
title: カスタマイズ
description: 製品のレコメンデーションをカスタマイズする方法を説明します。
exl-id: b1b8e770-45ec-4403-b79b-4f0a9f7bd959
source-git-commit: acfaa1d72265e42b973677a7e014ba4b350ec56b
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---

# カスタマイズ

製品のRecommendationsモジュールをインストールすると、Adobe Commerceは `ProductRecommendationsLayout` ディレクトリ。 このディレクトリにはテンプレートファイルが含まれています。このファイルをカスタマイズして、レコメンデーションがストアフロントに表示される方法を変更できます。 特に、次のテンプレートを変更または上書きできます。

`<your theme>/Magento_ProductRecommendationsLayout/web/template/recommendations.html`

テンプレートファイルの変更について詳しくは、 [テンプレートのカスタマイズ](https://developer.adobe.com/commerce/frontend-core/guide/templates/walkthrough/) （Frontend 開発者ガイド）を参照してください。

次の変更を加えた場合、 `recommendations.html` ファイルに保存する場合、Adobe Commerceがストアフロントからレコメンデーション指標を確実に収集できるように、ファイルで次のタグを保持する必要があります。

| タグ | 用途 |
|---|---|
| `<div data-bind="attr : {'data-unit-id' : unitId }"...</div>` | ビューイベントを収集します。 |
| `<a data-bind="attr : {'data-sku' : sku, 'data-unit-id'}"...</a>` | クリックイベントを収集します。 <br/>**注意：** アンカータグを追加する場合は、これらの属性を含める必要があります。 |

また、 `recommendations.html` ファイル、 `ProductRecommendationsLayout` ディレクトリには、次のサブディレクトリが含まれます。

| ディレクトリ | 目的 |
|---|---|
| `layout` | 次を含む `*.xml` 各ページタイプのファイル |
| `templates` | フェッチおよびレンダリングスクリプトを呼び出すファイルを含みます |
| `web/js` | ストアのレコメンデーションを取得してレンダリングする JavaScript ファイルを含みます |
| `web/template` | 次のテンプレートを含む： `magento/product-recommendations` モジュール |

## レコメンデーション単位の配置

次の場合： [作成](create.md) レコメンデーションの場合は、 [場所](placement.md) ページ上で表示される場所です。 レコメンデーションユニットは、メインコンテンツコンテナの上部または下部に配置できます。 ただし、この配置はカスタマイズできます。 ページビルダーのレコメンデーションコンテンツタイプを作成する場合、ページビルダーツールを使用して、レコメンデーション単位をページ上に配置します。 その他のすべてのページタイプについては、 `*.xml` レコメンデーションの作成時に生成されるファイル。

1. を `layout` ディレクトリ：

   ```bash
   cd `<your theme>/Magento_ProductRecommendationsLayout/layout`
   ```

   次の表に、このディレクトリに存在する XML ファイルを示します。

   | ファイル名 | ページ |
   |---|---|
   | `catalog_category_view.xml` | カテゴリ |
   | `catalog_product_view.xml` | 製品の詳細 |
   | `checkout_cart_index.xml` | 買い物かご |
   | `checkout_onepage_success.xml` | チェックアウト |
   | `cms_index_index.xml` | ホーム |

   >[!NOTE]
   >
   >のファイル名 `layout` ストアでサードパーティの拡張機能を使用する場合は、ディレクトリが異なる可能性があります。

1. を変更します。 `catalog_product_view.xml` ファイルを作成して、商品の詳細ページの商品の画像の後にレコメンデーション単位を表示するようにします。 この XML ファイルをカスタマイズする前に、ファイルを見て、変更する必要のあるセクションを理解しておきましょう。

   ```xml
   <?xml version="1.0"?>
   <page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
       <referenceBlock name="page.wrapper">
           <block class="Magento\Framework\View\Element\Template" before="-" name="product_recommendations_fetcher" template="Magento_ProductRecommendationsStorefront::fetcher.phtml" />
       </referenceBlock>
       <body>
           <referenceBlock name="main.content">
               <block class="Magento\ProductRecommendationsStorefront\Block\Renderer" after="-" name="product_recommendations_product_below_content" template="Magento_ProductRecommendationsStorefront::renderer.phtml">
                   <arguments>
                       <argument name="pagePlacement" xsi:type="string">below-main-content</argument>
                   </arguments>
               </block>
           </referenceBlock>
       </body>
   </page>
   ```

   上記のスニペットでは、 `main.content` 参照ブロックは、レコメンデーション単位が、その要素を基準としたどこかに配置されることを示します。 その `block` 要素に次を含む `after="-"` 属性：レコメンデーション単位がページのメインコンテンツブロックの後に表示されるように指定します。

1. 別のコンテンツブロックを指定して、このファイルを変更します。

   参照ブロックを変更する `name` から `main.content` から `product.info.media`.

   ```xml
   <?xml version="1.0"?>
   <page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
       <referenceBlock name="page.wrapper">
           <block class="Magento\Framework\View\Element\Template" before="-" name="product_recommendations_fetcher" template="Magento_ProductRecommendationsStorefront::fetcher.phtml" />
       </referenceBlock>
       <body>
           <referenceBlock name="product.info.media">
               <block class="Magento\ProductRecommendationsStorefront\Block\Renderer" after="-" name="product_recommendations_product_below_content" template="Magento_ProductRecommendationsStorefront::renderer.phtml">
                   <arguments>
                       <argument name="pagePlacement" xsi:type="string">below-main-content</argument>
                   </arguments>
               </block>
           </referenceBlock>
       </body>
   </page>
   ```

   この変更により、レコメンデーション単位が、製品の詳細ページで製品の画像の後に表示されるようになります。 レコメンデーション単位を `product.info.media`、 `after="-"` 属性 `before="-"`. この `pagePlacement` 引数は、変更しない内部引数です。

参照： [レイアウトの概要](https://developer.adobe.com/commerce/frontend-core/guide/layouts/) を参照してください。

## カスタム製品属性

開発者は、多くの場合、ストアフロントのレコメンデーション単位のカスタム製品属性値にアクセスし、それらの属性に基づく製品に視覚的な処理を追加できる必要があります。

例えば、店舗で一部のオーガニック製品を販売している場合、それらの製品に対してカスタム属性を設定し、 `Organic = Yes`. ストアフロントでこの属性値にアクセスして、これらの製品がRecommendationsに表示されたときに特別な視覚的処理を行うことができるようにする必要がある場合があります。 同様に、これらのカスタム製品属性値にアクセスすると、サイトのプレゼンテーションレイヤーで製品にバッジを付けたり、カスタムロジックを駆動したりできます。

![バッジを追加](assets/unit-custom.png)

ページでレコメンデーション単位をレンダリングする際にカスタム製品属性が使用可能であることを確認するには、 `Used in Product Listing` プロパティを `Yes` 内 [製品属性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html) ページを管理者に表示します。

このプロパティを設定すると、JSON ペイロードに `attributes` 属性コードと値の配列を含むオブジェクト。 その後、これらの属性値に基づいて、前述のように特別な視覚的処理やバッジを追加するなど、カスタムのストアフロントスタイルを適用できます。

>[!NOTE]
>
>製品属性の変更は、JSON ペイロードに表示されるまでに最大 1 時間かかる場合があります。
