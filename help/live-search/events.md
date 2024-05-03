---
title: '[!DNL Live Search] イベント'
description: イベントでのデータの収集方法を説明します [!DNL Live Search].
feature: Services, Eventing
exl-id: b0c72212-9be0-432d-bb8d-e4c639225df3
source-git-commit: 0d966c8dbd788563fa453912961fdc62a5a6c23e
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# [!DNL Live Search] イベント

[!DNL Live Search] では、イベントを使用して「最も多く閲覧」や「これを閲覧、それを閲覧」などの検索アルゴリズムを強化します。 LUMA ユーザーは初期設定のイベンティングを受け取りますが、ヘッドレスやその他のカスタム実装では、独自のニーズに応じてイベンティングを実装する必要があります。

以降 [!DNL Live Search] および [!DNL Product Recommendations] 同じバックエンドアルゴリズムを使用すると、一部のイベントは両方のサービスで共有されます。 一部の Product Recommendations イベントは、Recommendations ダッシュボードへの入力に必要です。

次の表に、で使用されるイベントを示します [!DNL Live Search] 戦略。

| 方法 | 製品 | イベント | ページ |
| --- | --- | --- | ---|
| 最も頻繁に閲覧された | Live Search<br>製品のレシピ | ページビュー<br>製品表示 | 製品詳細ページ |
| 最も多く購入された | Live Search<br>製品のレシピ | ページビュー<br>チェックアウトの完了 | 買い物かご/チェックアウト |
| 買い物かごに追加済み | Live Search<br>製品のレシピ | ページビュー<br>カートに追加 | 製品詳細ページ<br>製品リストページ<br>カート<br>ウィッシュリスト |
| がこれを表示し、が表示されました | Live Search<br>製品のレシピ | ページビュー<br>製品表示 | 製品詳細ページ |
| トレンド | Live Search<br>製品のレシピ | ページビュー<br>製品表示 | 製品詳細ページ |
| これを閲覧し、次を購入 | 製品のレシピ | ページビュー<br>製品表示 | 製品詳細ページ<br>買い物かご/チェックアウト |
| これを購入し、それを購入しました | 製品のレシピ | ページビュー<br>製品表示 | 製品詳細ページ |
| コンバージョン：表示から購入 | 製品のレシピ | ページビュー<br>製品表示 | 製品詳細ページ |
| コンバージョン：表示から購入 | 製品のレシピ | ページビュー<br>チェックアウトの完了 | 買い物かご/チェックアウト |
| コンバージョン：買い物かごに表示 | 製品のレシピ | ページビュー<br>製品表示 | 製品詳細ページ |
| コンバージョン：買い物かごに表示 | 製品のレシピ | ページビュー<br>カートに追加 | 製品詳細ページ<br>製品リストページ<br>カート<br>ウィッシュリスト |

>[!NOTE]
>
>～を目的としたデータ収集 [!DNL Live Search] 個人を特定できる情報（PII）は含まれません。 Cookie ID や IP アドレスなどのすべてのユーザー識別子は、厳密に匿名化されます。 [詳細情報](https://www.adobe.com/privacy/experience-cloud.html).

## 必須のダッシュボードイベント

一部のイベントは、に入力する必要があります。 [Live Search ダッシュボード](performance.md)

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

すべてのイベントには、 `Page` および `Storefront` コンテキスト。 これは、個々のイベントを生成する場合ではなく、ページレベル/ストアフロントアプリケーションレイヤーで行う必要があります（例えば、PHP ストアフロントでは、PHP アプリケーションコンテナが実行時に設定を行います）。

## 使用方法

の実装例を次に示します `search-request-sent` イベント：

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

広告ブロッカーとプライバシー設定は、イベントがキャプチャされるのを防ぎ、エンゲージメントと売上高を増やす可能性があります [指標](workspace.md) 報告不足。

イベントは、マーチャントサイトで発生するすべてのトランザクションを取り込むわけではありません。 イベントは、サイト上で発生しているイベントの一般的な考えをマーチャントに提供することを目的としています。

ヘッドレス実装では、イベントによってを強化する必要があります。 [製品Recommendationsダッシュボード](../product-recommendations/events.md).

>[!NOTE]
>
>次の場合 [Cookie 制限モード](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) を有効にすると、買い物客が cookie の使用に同意するまで、Adobe Commerceは行動データを収集しません。 Cookie 制限モードが無効になっている場合、Adobe Commerceはデフォルトで行動データを収集します。
