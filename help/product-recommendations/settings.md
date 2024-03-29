---
title: 設定
description: ソースの変更方法を学ぶ [!DNL Product Recommendations] データと、視覚的なレコメンデーションを有効にする方法を説明します。
exl-id: 8c074e11-e0cb-4d55-b646-30279c79bbc2
source-git-commit: 75ff893bf5867ededa49807835676ddf9b19adc9
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# 設定

次の場合： [SaaS データ領域の設定](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) Recommendationsの場合、SaaS データスペースは、カタログデータとストアフロント行動データを収集します。 [Adobe Sensei](https://www.adobe.com/sensei.html) はそのデータを分析し、製品Recommendationsを提供するために使用される製品関連付けを計算します。

テストまたはステージング用の非実稼動環境では、通常、現実的な製品のレコメンデーションを提供するストアフロントの行動データの量や質がありません。 実際の買い物客の規模に応じた行動は、実稼動環境でのみ取り込むことができます。 この問題を解決するために、Adobe Commerceでは、実稼動環境の製品レコメンデーションを、他の非実稼動 SaaS データスペースと共に使用できます。 実稼動以外の環境で実際のストアフロントデータを使用すると、買い物客が表示するレコメンデーションをプレビューし、様々なレコメンデーションタイプや配置の場所を試すことができます。 異なる SaaS データスペースからのRecommendationsは、買い物客はプレビューできますが、クリックはできません。

ステージングの注文は、ステージングを使用して記録されます `environmentId`. 実稼動データには影響しません。 実稼動データは、 `alternateEnvironmentId`.

>[!NOTE]
>
>REST を通じて製品Recommendationsを使用する場合、 `alternateEnvironmentId` パラメーターは、他のデータスペースを指定するために使用できます。 GraphQLを通じて Product Recommendationsを使用する場合、このパラメーターは使用できません。

## レコメンデーションソースを選択

製品レコメンデーションデータのソースを変更するには、使用する行動データを含む SaaS データスペースを選択します。 始める前に、次の点を確認します。

- ストアフロントのデータ収集は必ず必要です [設定済みおよび有効](install-configure.md) （実稼動環境用）および [検証済み](verify.md) その行動データがAdobe Commerceに送信されます。
- 非実稼動環境のカタログは、実稼動カタログと基本的に同じにする必要があります。 同様のカタログを使用すると、製品のレコメンデーションユニットが実稼働環境でのレコメンデーションユニットと密接に似たものを返すようになります。

1. 実稼動以外のAdobe Commerce環境の管理者にログインします。

1. 次の日： _管理者_ サイドバー、移動 **マーケティング** > _プロモーション_ > **製品Recommendations**.

1. クリック **設定**.

   ![製品レコメンデーション設定](assets/settings.png)
   _設定_

1. Adobe Analytics の _Recommendationsソース_ セクションで、 **別の SaaS データスペースからレコメンデーションを取得する** オプション。 The _Recommendationsソース_ セクションは、実稼動以外の環境にのみ表示されます。

   リスト _利用可能な SaaS データスペース_ が表示されます。

   ![製品レコメンデーション設定](assets/settings-select-saas.png)
   _設定_

1. 使用する買い物客データが含まれる SaaS データスペースを選択します。

1. クリック **変更を保存**.

   Adobe Commerceは、選択したデータスペースからレコメンデーションを取得するようになりました。

   >[!NOTE]
   >
   > 別の SaaS データスペースから取得したレコメンデーションを実稼動以外のストアフロントで表示できますが、レコメンデーションをクリックすることはできません。

### 新しい SaaS データ領域の設定

1. 「 Recommendations source 」セクションで、「 **設定を編集**.

1. 手順に従って新しい [[!DNL Commerce] サービス](/help/landing/saas.md).

## 視覚的なレコメンデーションを有効にする

次の場合、 [Visual Product Recommendations](install-configure.md) モジュールがインストールされている場合、Visual Recommendationsを有効にして、 [視覚的類似性](type.md#visualsim) レコメンデーションタイプ。

Adobe Analytics の _Visual Recommendations_ セクション、設定 **Visual Recommendationsを有効にする** をアクティブな位置に追加します。
