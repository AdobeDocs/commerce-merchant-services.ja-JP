---
title: '[!DNL Live Search] イベント'
description: イベントで  [!DNL Live Search] のデータを収集する方法を説明します。
feature: Services, Eventing
exl-id: b0c72212-9be0-432d-bb8d-e4c639225df3
source-git-commit: 0d966c8dbd788563fa453912961fdc62a5a6c23e
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# [!DNL Live Search] イベント

[!DNL Live Search] はイベントを使用して、「最も多く閲覧された」、「これを閲覧し、それを閲覧した」などの検索アルゴリズムを強化します。 LUMA ユーザーは初期設定のイベンティングを受け取りますが、ヘッドレスやその他のカスタム実装では、独自のニーズに応じてイベンティングを実装する必要があります。

[!DNL Live Search] と [!DNL Product Recommendations] は同じバックエンドアルゴリズムを使用するので、一部のイベントは両方のサービスで共有されます。 一部の Product Recommendations イベントは、Recommendations ダッシュボードへの入力に必要です。

次の表に、戦略で使用されるイベント [!DNL Live Search] 説明します。

| 方法 | 製品 | イベント | ページ |
| --- | --- | --- | ---|
| 最も頻繁に閲覧された | Live Search<br>Product Recs | ページビュー <br> 製品表示 | 製品詳細ページ |
| 最も多く購入された | Live Search<br>Product Recs | ページビュー <br> チェックアウトの完了 | 買い物かご/チェックアウト |
| 買い物かごに追加済み | Live Search<br>Product Recs | ページ表示 <br> 買い物かごに追加 | 製品詳細ページ <br> 製品一覧ページ <br> 買い物かご <br> お気に入りリスト |
| がこれを表示し、が表示されました | Live Search<br>Product Recs | ページビュー <br> 製品表示 | 製品詳細ページ |
| トレンド | Live Search<br>Product Recs | ページビュー <br> 製品表示 | 製品詳細ページ |
| これを閲覧し、次を購入 | 製品のレシピ | ページビュー <br> 製品表示 | 製品詳細ページ <br> 買い物かご/チェックアウト |
| これを購入し、それを購入しました | 製品のレシピ | ページビュー <br> 製品表示 | 製品詳細ページ |
| コンバージョン：表示から購入 | 製品のレシピ | ページビュー <br> 製品表示 | 製品詳細ページ |
| コンバージョン：表示から購入 | 製品のレシピ | ページビュー <br> チェックアウトの完了 | 買い物かご/チェックアウト |
| コンバージョン：買い物かごに表示 | 製品のレシピ | ページビュー <br> 製品表示 | 製品詳細ページ |
| コンバージョン：買い物かごに表示 | 製品のレシピ | ページ表示 <br> 買い物かごに追加 | 製品詳細ページ <br> 製品リストページ <br> 買い物かご <br> ウィッシュリスト |

>[!NOTE]
>
>[!DNL Live Search] 用のためのデータ収集には、個人を特定できる情報（PII）は含まれません。 Cookie ID や IP アドレスなどのすべてのユーザー識別子は、厳密に匿名化されます。 [ 詳細情報 ](https://www.adobe.com/privacy/experience-cloud.html)。

## 必須のダッシュボードイベント

一部のイベントは、[ ライブ検索ダッシュボード ](performance.md) への入力に必要です

| ダッシュボード領域 | イベント | 結合フィールド |
| ------------------- | ------------- | ---------- |
| ユニーク検索 | `page-view`, `search-request-sent`, | searchRequestId |
| ゼロ結果検索 | `page-view`, `search-request-sent`, | searchRequestId |
| ゼロ結果率 | `page-view`, `search-request-sent`, | searchRequestId |
| 一般的な検索 | `page-view`, `search-request-sent`, | searchRequestId |
| 平均 クリック位置 | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click` | searchRequestId |
| クリックスルー率 | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click` | searchRequestId, sku |
| コンバージョン率 | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click`, `product-view`, `add-to-cart`, `place-order` | searchRequestId, sku |

### 必要なコンテキスト

すべてのイベントには、`Page` および `Storefront` コンテキストが必要です。 これは、個々のイベントを生成する場合ではなく、ページレベル/ストアフロントアプリケーションレイヤーで行う必要があります（例えば、PHP ストアフロントでは、PHP アプリケーションコンテナが実行時に設定を行います）。

## 使用方法

`search-request-sent` イベントの実装例を次に示します。

```javascript
const mse = window.magentoStorefrontEvents;

/* set in application container */
// mse.context.page(pageCtx);
// mse.context.setStorefrontInstance(storefrontCtx);

/* set before firing event */
mse.context.setSearchInput(searchInputCtx);
mse.publish.searchRequestSent("search-bar");
```

## 注意事項

広告ブロッカーとプライバシー設定は、イベントがキャプチャされるのを防ぎ、エンゲージメントと売上高 [ 指標 ](workspace.md) が過小報告される原因になる可能性があります。

イベントは、マーチャントサイトで発生するすべてのトランザクションを取り込むわけではありません。 イベントは、サイト上で発生しているイベントの一般的な考えをマーチャントに提供することを目的としています。

ヘッドレス実装では、[ 製品Recommendations ダッシュボード ](../product-recommendations/events.md) を強化するためにイベンティングを実装する必要があります。

>[!NOTE]
>
>[Cookie 制限モード ](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) が有効になっている場合、買い物客が Cookie の使用を同意するまで、Adobe Commerceは行動データを収集しません。 Cookie 制限モードが無効になっている場合、Adobe Commerceはデフォルトで行動データを収集します。
