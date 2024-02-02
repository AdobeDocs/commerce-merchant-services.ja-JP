---
title: '''[!DNL Live Search] イベント`'
description: イベントでデータを収集する方法を説明します。 [!DNL Live Search].
feature: Services, Eventing
exl-id: b0c72212-9be0-432d-bb8d-e4c639225df3
source-git-commit: 8d669cf6042340659574c86a43836a02954f24ce
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# [!DNL Live Search] イベント

[!DNL Live Search] は、イベントを使用して、「最も多く閲覧された」や「これを表示した、これを表示した」などの検索アルゴリズムを強化します。 LUMA ユーザーがすぐに使用できるイベンティングを得る一方、ヘッドレスなどのカスタム実装は、独自のニーズに応じてイベンティングを実装する必要があります。

次以降 [!DNL Live Search] および [!DNL Product Recommendations] 同じバックエンドアルゴリズムを使用する場合、一部のイベントは両方のサービスで共有されます。 一部の製品Recommendationsイベントは、Recommendationsダッシュボードに入力するために必要です。

## イベント

次の表に、 [!DNL Live Search] 戦略。

| 方法 | 製品 | イベント | ページ |
| --- | --- | --- | ---|
| 最も頻繁に閲覧された | ライブ検索<br>製品 Recs | ページビュー<br>製品表示 | 製品の詳細ページ |
| 最も多く購入された | ライブ検索<br>製品 Recs | ページビュー<br>完全なチェックアウト | 買い物かご/チェックアウト |
| 買い物かごに最も多く追加されました | ライブ検索<br>製品 Recs | ページビュー<br>買い物かごに追加 | 製品の詳細ページ<br>製品リストページ<br>買い物かご<br>ウィッシュリスト |
| これを閲覧し、それを閲覧した | ライブ検索<br>製品 Recs | ページビュー<br>製品表示 | 製品の詳細ページ |
| トレンド | ライブ検索<br>製品 Recs | ページビュー<br>製品表示 | 製品の詳細ページ |
| これを見て、購入したもの | 製品 Recs | ページビュー<br>製品表示 | 製品の詳細ページ<br>買い物かご/チェックアウト |
| これを購入し、それを購入しました | 製品 Recs | ページビュー<br>製品表示 | 製品の詳細ページ |
| コンバージョン：購入に対する表示 | 製品 Recs | ページビュー<br>製品表示 | 製品の詳細ページ |
| コンバージョン：購入に対する表示 | 製品 Recs | ページビュー<br>完全なチェックアウト | 買い物かご/チェックアウト |
| コンバージョン：買い物かごに表示 | 製品 Recs | ページビュー<br>製品表示 | 製品の詳細ページ |
| コンバージョン：買い物かごに表示 | 製品 Recs | ページビュー<br>買い物かごに追加 | 製品の詳細ページ<br>製品リストページ<br>買い物かご<br>ウィッシュリスト |

>[!NOTE]
>
>の目的でのデータ収集 [!DNL Live Search] 個人を特定できる情報 (PII) は含まれません。 Cookie ID や IP アドレスなどのすべてのユーザー識別子は厳密に匿名化されます。 [詳細情報](https://www.adobe.com/privacy/experience-cloud.html).

## 必須のダッシュボードイベント

一部のイベントは、 [ライブ検索ダッシュボード](performance.md)

| ダッシュボード領域 | イベント | フィールドを結合 |
| ------------------- | ------------- | ---------- |
| 一意の検索 | `page-view`, `search-request-sent`, | searchRequestId |
| 結果がゼロの検索 | `page-view`, `search-request-sent`, | searchRequestId |
| ゼロの結果率 | `page-view`, `search-request-sent`, | searchRequestId |
| よく読まれる検索 | `page-view`, `search-request-sent`, | searchRequestId |
| 平均 クリック位置 | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click` | searchRequestId |
| クリックスルー率 | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click` | searchRequestId, sku |
| コンバージョン率 | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click`, `product-view`, `add-to-cart`, `place-order` | searchRequestId, sku |

### 必要なコンテキスト

すべてのイベントに `Page` および `Storefront` コンテキスト。 これは、個々のイベントを生成する場合ではなく、ページレベル/ストアフロントのアプリケーションレイヤーで発生する必要があります（例えば、PHP ストアフロントでは、PHP アプリケーションコンテナが実行時に設定を行います）。

## 使用状況

以下に、 `search-request-sent` イベント：

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

広告ブロッカーやプライバシーの設定は、イベントが取り込まれるのを防ぎ、エンゲージメントや売上高を引き起こす可能性があります [指標](workspace.md) 過少報告される

イベンティングは、商人のサイトで発生するすべてのトランザクションをキャプチャするわけではありません。 イベンティングは、サイト上で発生しているイベントに関する一般的なアイデアを商人に与えることを目的としています。

ヘッドレス実装では、 [製品のRecommendationsダッシュボード](../product-recommendations/events.md).

>[!NOTE]
>
>次の場合 [Cookie 制限モード](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) が有効になっている場合、Adobe Commerceは買い物客が cookie の使用を同意するまで行動データを収集しません。 「Cookie Restriction Mode」が無効になっている場合、Adobe Commerceはデフォルトで行動データを収集します。
