---
title: オンボーディング
description: での要件とサポートされるプラットフォームについて説明します。 [!DNL Product Recommendations].
exl-id: ad47ac39-8f6f-4765-84ad-9e3d104385db
source-git-commit: 209bdf9c69ff81481d6df7cb8e8832deef13c9f4
workflow-type: tm+mt
source-wordcount: '283'
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

- Adobe Commerce 2.4.4 以降
- PHP 8.1, 8.2
- コンポーザー 2

### サポートされるプラットフォーム

- Adobe Commerceオンプレミス (EE) :2.4.4 以上
- Adobe Commerce on Cloud (ECE) :2.4.4 以上

### ページビルダーのサポート

[!DNL Product Recommendations] は、Page Builder コンテンツタイプとしてページに追加できます。 Page Builder サポートを製品Recommendationsに追加するには、 [インストールと設定](install-configure.md).

詳しくは、 [[!DNL Page Builder] 統合](page-builder.md) 追加方法の手順 [!DNL Product Recommendations] into [!DNL Page Builder] コンテンツ。

### SaaS 価格のインデックス作成

製品レコメンデーションのお客様が [SaaS 価格のインデックス作成](../price-index/index.md)：価格変更の更新と同期時間を短縮します。

### B2B サポート {#b2bsupport}

B2B ストアフロントでは、多くの場合、買い物客や顧客グループごとに製品の表示と価格を指示する複雑なロジックが必要です。 [!DNL Product Recommendations] now [サポート](release-notes.md) この機能は、次の点に従って動作します。 [カテゴリ権限](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/category-permissions.html), [共有カタログ](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html)、および [顧客グループ固有の価格](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html). 例えば、小売顧客セグメントで特定のカテゴリを非表示にしている場合、そのセグメントの買い物客には、そのカテゴリにある製品のレコメンデーションは表示されません。 また、特定の顧客グループや会社用に共有カタログを定義すると、それらの買い物客は、アクセス可能な製品のレコメンデーションのみを表示します。 すべての推奨商品は、各買い物客の顧客グループに基づく、正しい顧客グループ固有の価格を反映しています。

>[!NOTE]
>
>マーチャントは、 [カタログサービス](../catalog-service/overview.md) ストアフロント API ですが、カスタマイズはAdobeのサポートチームの範囲外です。
