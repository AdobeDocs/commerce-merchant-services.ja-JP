---
title: オンボーディング
description: での要件とサポートされるプラットフォームについて説明します。 [!DNL Product Recommendations].
exl-id: ad47ac39-8f6f-4765-84ad-9e3d104385db
source-git-commit: 09609fd0b5bd3da9e884115de001bc33832ad792
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# オンボーディング

のオンボーディングプロセス [!DNL Product Recommendations] は、サーバーのコマンドラインにアクセスする必要があり、次の手順で構成されます。 コマンドラインでの作業に慣れていない場合は、開発者またはシステムインテグレーターに問い合わせてください。

- [実装ワークフロー](implementation-workflow.md)
- [インストールと設定](install-configure.md)
- [設定](settings.md)
- [検証](verify.md)
- [ステージング環境](staging-environment.md)

## 要件

- Adobe Commerce 2.3.x, 2.4.x
- PHP 7.3 / 7.4
- コンポーザー

### サポートされるプラットフォーム

- Adobe Commerceオンプレミス (EE) :2.4.x
- Adobe Commerce on Cloud (ECE) :2.4.x

### ページビルダーのサポート

[!DNL Product Recommendations] は、Page Builder コンテンツタイプとしてページに追加できます。 Page Builder サポートを製品Recommendationsに追加するには、 [インストールと設定](install-configure.md).

>[!NOTE]
>
>[!DNL Page Builder] レコメンデーション単位は、デフォルトのストア表示に対してのみ作成できます。

### B2B サポート {#b2bsupport}

B2B ストアフロントでは、多くの場合、買い物客や顧客グループごとに製品の表示と価格を指示する複雑なロジックが必要です。 [!DNL Product Recommendations] now [サポート](release-notes.md) この機能は、次の点に従って動作します。 [カテゴリ権限](https://docs.magento.com/user-guide/catalog/category-permissions.html), [共有カタログ](https://docs.magento.com/user-guide/catalog/catalog-shared.html)、および [顧客グループ固有の価格](https://docs.magento.com/user-guide/catalog/pricing-advanced.html). 例えば、小売顧客セグメントで特定のカテゴリを非表示にしている場合、そのセグメントの買い物客には、そのカテゴリにある製品のレコメンデーションは表示されません。 また、特定の顧客グループや会社用に共有カタログを定義すると、それらの買い物客は、アクセス可能な製品のレコメンデーションのみを表示します。 すべての推奨商品は、各買い物客の顧客グループに基づく、正しい顧客グループ固有の価格を反映しています。
