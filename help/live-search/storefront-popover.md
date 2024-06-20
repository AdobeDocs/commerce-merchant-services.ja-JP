---
title: "[!DNL Storefront Popover]"
description: 「その [!DNL Live Search storefront popover] は、提案された製品とサムネールを動的に返します。」
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: e375404a50dd4972ab584f69d7953aba2c8f4566
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# [!DNL Storefront Popover]

条件 [!DNL Live Search] 等しい [installed](install.md), a [!DNL popover] 買い物客がを入力すると、ストアフロントに表示されます [検索](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) ボックス。 各文字を入力すると、 [!DNL popover] に、上位の検索結果の推奨製品とサムネール画像を更新しました。

[!DNL Live Search] 2 文字以上のクエリの結果を返します。 部分一致の場合、1 単語あたりの最大文字数は 20 文字です。 「入力中の検索」クエリの文字数は設定できません。

デフォルトでは [!DNL Live Search] のサポート [検索語句のリダイレクト](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html).

![[!DNL Live Search popover]](assets/storefront-search-as-you-type.png)

>[!TIP]
>
>で検索可能な製品属性を設定する方法を説明します [Live Search のセットアップ](workspace.md) 記事。

## [!DNL Popover] ページサイズ

のページサイズ [!DNL popover] オートコンプリートされた製品のライン数を指定します。 Live Search のインストール中、 `page_size` の値が現在のの値に変更されます。 [カタログ検索](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/catalog.html) - `Autocomplete Limit` の設定値。

デフォルトでは、「カタログ検索 – オートコンプリートの制限」の値は 8 行（1 行）に設定されています。 のページサイズを変更するには [!DNL popover]、次の手順を実行します。

1. 日 *Admin* サイドバー、に移動 **ストア** > 設定 > **設定**.
1. 左側のパネルで、を展開します **カタログ** を選択します **カタログ** 設定のリストから。
1. を展開します。 *カタログ検索* セクション。
1. を **オートコンプリートの制限** を許可する行の数 [!DNL popover].
1. 完了したら、 **設定を保存**.

## スタイル設定 [!DNL Popover] 例

の外観をカスタマイズできます [!DNL Popover] 会社のスタイルやブランディングガイドラインに合わせたウィジェット。

この [!DNL storefront popover] 常に商品を表示 `name` および `price`、およびフィールドの選択は変更できません。 ただし、 [!DNL popover] 要素は、を使用してスタイルを設定できます [CSS](https://developer.adobe.com/commerce/frontend-core/guide/css/) クラス。 例えば、次の宣言は、 [!DNL popover] コンテナとフッター。

```css
.livesearch.popover-container {
    background-color: lavender;
}

.livesearch.view-all-footer {
    background-color: magenta;
}
```

## コンテナの表示

の親コンポーネント `.livesearch.popover-container` 等しい `.search-autocomplete`.  この `.active` クラスは、コンテナの表示/非表示を示します。 この `.active` クラスが条件付きで追加されるのは、 [!DNL popover] が開いています。

```css
.search-autocomplete.active   /* visible */
.search-autocomplete          /* not visible */
```

ストアフロント要素のスタイル設定について詳しくは、次を参照してください。 [カスケーディングスタイルシート（CSS）](https://developer.adobe.com/commerce/frontend-core/guide/css/) が含まれる [フロントエンド開発者ガイド](https://developer.adobe.com/commerce/frontend-core/guide/).

## クラスセレクター

次のクラスセレクターを使用して、でコンテナおよび製品要素のスタイルを設定することができます [!DNL popover].

- `.livesearch.popover-container`
- `.livesearch.view-all-footer`
- `.livesearch.products-container`
- `.livesearch.product-result`
- `.livesearch.product-name`
- `.livesearch.product-price`

### コンテナクラスセレクター

#### .livesearch.popover-container

![[!DNL Popover] コンテナ](assets/livesearch-popover-container.png)

#### .livesearch.view-all-footer

![すべてのフッターを表示](assets/livesearch-view-all-footer.png)

### 製品クラスセレクター

#### .livesearch.products-container

![製品コンテナ](assets/livesearch-product-container.png)

#### .livesearch.product-result

![製品の結果](assets/livesearch-product-result.png)

#### .livesearch.product-name

![製品名](assets/livesearch-product-name.png)

#### .livesearch.product-price

![製品価格](assets/livesearch-product-price.png)

#### .livesearch product-link

![製品の結果](assets/livesearch-product-link.png)

## 変更したテーマの操作 {#working-with-modified-theme}

を使用できます [!DNL storefront popover] カスタマイズされたを使用 [テーマ](https://developer.adobe.com/commerce/frontend-core/guide/themes/) から必要なファイルを継承します *Luma*. この `top.search` ブロックする `header-wrapper` の `Magento_Search` モジュールは変更できません。

```html
<referenceContainer name="header-wrapper">
   <block class="Magento\Framework\View\Element\Template" name="top.search" as="topSearch" template="Magento_Search::form.mini.phtml">
      <arguments>
         <argument name="configProvider" xsi:type="object">Magento\Search\ViewModel\ConfigProvider</argument>
      </arguments>
   </block>
</referenceContainer>
```

## の無効化 [!DNL popover]

を無効にするには [!DNL popover] 標準を復元します [クイック検索](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) 機能を使用するには、次のコマンドを入力します。

```bash
bin/magento module:disable Magento_LiveSearchStorefrontPopover
```

## ヘッドレス実装

ヘッドレス実装を使用する場合は、 [!DNL Live Search popover] の使用 [npm パッケージ](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).
