---
title: データを収集
description: イベントが商品レコメンデーションのデータを収集する方法を説明します。
source-git-commit: 81ab2e22b0ec81e97d27ee135c88b50731a3986d
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# データを収集

SaaS ベースのAdobe Commerce機能 ( [製品Recommendations](install-configure.md) または [ライブ検索](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html)を使用する場合、モジュールは行動データ収集をストアフロントにデプロイします。 このメカニズムは、匿名化された行動データを買い物客から収集し、製品のレコメンデーションを強化します。 例えば、 `view` イベントは、 `Viewed this, viewed that` レコメンデーションタイプ、および `place-order` イベントは、 `Bought this, bought that` レコメンデーションタイプ。

>[!NOTE]
>
>製品レコメンデーションを目的としたデータ収集には、個人を特定できる情報 (PII) は含まれません。 Cookie ID や IP アドレスなどのすべてのユーザー識別子は厳密に匿名化されます。 [詳細情報](https://www.adobe.com/privacy/experience-cloud.html).

次のイベントは、Product Recommendationsに固有のものではありませんが、結果を返すために必要になります。

- `view`
- `add-to-cart`
- `place-order`

この [Adobe Commerce Storefront イベントコレクター](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/#quick-start) ストアフロントにデプロイされたすべてのイベントの一覧が表示されます。 ただし、このリストからは、Product Recommendationsに固有のイベントのサブセットが得られます。 これらのイベントは、買い物客がストアフロントでレコメンデーション単位を操作する際にデータを収集し、レコメンデーションのパフォーマンスを分析するのに役立つ指標を活用します。

| イベント | 説明 | [指標に使用されますか？](workspace.md) |
| --- | --- | --- |
| `impression-render` | レコメンデーション単位は、ページ上にレンダリングされます。 | はい |
| `rec-add-to-cart-click` | 顧客が **買い物かごに追加** ボタンを使用して、レコメンデーション単位の品目を表示できます。 | はい、 **買い物かごに追加** ボタンが recommendations テンプレートに存在すること。 |
| `rec-click` | 顧客がレコメンデーション単位で商品をクリックします。 | はい |
| `view` | レコメンデーションユニットは、ビューにスクロールして表示するなど、ページ上で表示可能になります。 | はい |

ストアフロントがPWA Studioで実装されている場合は、 [PWA文書](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). React や Vue JS などのカスタムフロントエンドテクノロジーを使用する場合は、ユーザーガイドを参照して、製品Recommendationsを [頭のない](headless.md) 環境。

広告ブロッカーやプライバシー設定が `magento/product-recommendations` イベントのキャプチャからモジュールを削除し、エンゲージメントと売上高を引き起こす可能性 [指標](workspace.md) 過少報告される

>[!NOTE]
>
>If [Cookie 制限モード](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) が有効になっている場合、Adobe Commerceは買い物客が cookie の使用を同意するまで行動データを収集しません。 「Cookie Restriction Mode」が無効になっている場合、Adobe Commerceはデフォルトで行動データを収集します。