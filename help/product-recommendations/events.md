---
title: データを収集
description: イベントで製品レコメンデーションのデータを収集する方法を説明します。
exl-id: b827d88c-327f-4986-8239-8f1921d8383c
feature: Services, Recommendations, Eventing
source-git-commit: 67296ea42bfddb10b0c86cb1ca47324f5fec7825
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# データを収集

[Product Recommendations](install-configure.md) や [Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html) などの SaaS ベースのAdobe Commerce機能をインストールして設定すると、行動データ収集がストアフロントにデプロイされます。 このメカニズムにより、匿名化された行動データが買い物客から収集され、製品レコメンデーションが強化されます。 例えば、`view` イベントは `Viewed this, viewed that` レコメンデーションタイプの計算に使用され、`place-order` イベントは `Bought this, bought that` レコメンデーションタイプの計算に使用されます。

>[!NOTE]
>
>製品レコメンデーションのためのデータ収集には、個人を特定できる情報（PII）は含まれません。 Cookie ID や IP アドレスなどのすべてのユーザー識別子は、厳密に匿名化されます。 詳細情報 [ 詳細情報 ](https://www.adobe.com/privacy/experience-cloud.html)。

次のイベントは、製品Recommendationsに固有ではありませんが、結果を返すために必要です。

- `view`
- `add-to-cart`
- `place-order`

[Adobe Commerce ストアフロントイベントコレクター ](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/#quick-start) には、ストアフロントにデプロイされたすべてのイベントが一覧表示されます。 ただし、このリストからは、製品Recommendationsに固有のイベントのサブセットがあります。 これらのイベントは、買い物客がストアフロントでレコメンデーションユニットとやり取りする際にデータを収集し、レコメンデーションのパフォーマンスを分析するのに役立つ指標を強化します。

| イベント | 説明 | 指標に使用しますか？ |
| --- | --- | --- |
| `impression-render` | レコメンデーションユニットがページ上にレンダリングされます。 | はい |
| `rec-add-to-cart-click` | 顧客が、レコメンデーションユニット内の項目の **買い物かごに追加** ボタンをクリックする。 | はい。「**買い物かごに追加**」ボタンがレコメンデーションテンプレートに表示されている場合は有効です。 |
| `rec-click` | 顧客は、レコメンデーションユニット内の製品をクリックします。 | はい |
| `view` | レコメンデーションユニットは、スクロールして表示するなど、ページ上で表示可能になる。 | はい |

ダッシュボードに正しくデータを入力するには、次のイベントが必要です。

| ダッシュボード列 | イベント | 結合フィールド |
| ---------------- | --------- | ----------- |
| インプレッション | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render` | unitId |
| ビュー | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-unit-view` | unitId |
| クリック数 | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click` | unitId |
| 収益 | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`, `place-order` | unitId、sku |
| 長期収益 | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`, `place-order` | unitId、sku |
| CTR | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-item-click`, `recs-add-to-cart-click` | unitId、sku |
| vCTR | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-unit-view`, `recs-item-click`, `recs-add-to-cart-click` | unitId、sku |

ストアフロントがPWA Studioを使用して実装されている場合は、[PWAドキュメント ](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/) を参照してください。 React や Vue JS などのカスタムフロントエンドテクノロジーを使用している場合は、ユーザーガイドを参照して、[Product Recommendationsをヘッドレス ](headless.md) 環境に統合する方法を確認してください。

## 注意事項

広告ブロッカーとプライバシー設定は、`magento/product-recommendations` モジュールがイベントをキャプチャするのを防ぎ、エンゲージメントと売上高 [ 指標 ](workspace.md) が過小報告される可能性があります。

イベントは、マーチャントサイトで発生するすべてのトランザクションを取り込むわけではありません。 イベントは、サイト上で発生しているイベントの一般的な考えをマーチャントに提供することを目的としています。

ヘッドレス実装では、製品Recommendationsダッシュボードを強化するためにイベンティングを実装する必要があります。

>[!NOTE]
>
>[Cookie 制限モード ](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) が有効になっている場合、買い物客が Cookie の使用を同意するまで、Adobe Commerceは行動データを収集しません。 Cookie 制限モードが無効になっている場合、Adobe Commerceはデフォルトで行動データを収集します。
