---
title: ガイドの概要
description: を使用してAdobe CommerceデータをAdobe Experience Platformに統合する方法を説明します。 [!DNL Data Connection] 拡張子。
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
recommendations: noCatalog
source-git-commit: 4a5877d6e1a5c7d840e36f4913306b0c440bbac5
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# [!DNL Data Connection] 概要

>[!IMPORTANT]
>
>Experience Platformコネクタの名前は「 [!DNL Data Connection].

The [!DNL Data Connection] 拡張機能を使用すると、Adobe Commerceの商人が [店頭の](events.md#storefront-events) および [バックオフィス](events.md#back-office-events) Adobe AnalyticsやAdobe Journey Optimizerなどの他のAdobe Experience Cloud製品がそのコマースデータを使用できるように、Adobe Experience Platform Edge にデータを送信します。 コマースデータをAdobe Experience Cloud内の他の製品に接続することで、サイトでのユーザー行動の分析、AB テストの実行、パーソナライズされたキャンペーンの作成などのタスクを実行できます。

[ストアフロントイベント](events.md#storefront-events) 買い物客のインタラクションのキャプチャ `View Page`, `View Product`, `Add to Cart`、および [購買依頼リスト](events.md#b2b-events) 情報（B2B 商人用） [バックオフィス](events.md#back-office-events) イベントは、注文が発行されたか、取り消されたか、返金されたか、出荷されたか、完了したかなど、注文のステータスに関する情報をキャプチャします。 取り込まれたデータには、個人を特定できる情報 (PII) は含まれません。 Cookie ID や IP アドレスなどのすべてのユーザー識別子は厳密に匿名化されます。 [詳細情報](https://www.adobe.com/privacy/experience-cloud.html).

The [!DNL Data Connection] 拡張機能は、次の下のコマース管理に表示されます。 **システム** /サービス/ **[!DNL Data Connection]**.

![[!DNL Data Connection] 拡張機能の管理ビュー](assets/epc-adminui.png)

## 前提条件 {#prereqs}

次の手順で [!DNL Data Connection] 拡張機能には、以下が必要です。

- Adobe Commerce 2.4.3 以降
- Adobe IDと組織 ID
- [Adobeクライアントデータレイヤー (ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html). ストアフロントイベントデータを収集するには、ACDL が必要です。
- 他のAdobeDX 製品の使用権限

## オンボーディング手順

1. [インストール](install.md) の [!DNL Data Connection] 拡張子。
1. [ログイン](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) をAdobeアカウントに追加し、 [確認するビュー](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255) 組織 ID。 組織 ID は、プロビジョニングされた組織の会社に関連付けられたExperience CloudID です。 この ID は 24 文字の英数字から成る文字列で、その後にが続きます（必須） `@AdobeOrg`.
1. [作成または更新](update-xdm.md) コマース固有のフィールドグループを持つ XDM スキーマ。
1. [データセットの作成](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) 作成または更新したスキーマに基づいて このデータセットには、送信した Commerce データが含まれています。
1. [データストリームの作成](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) をクリックし、コマース固有のフィールドグループを含む XDM スキーマを選択します。
1. [Commerce Services に接続](../landing/saas.md).
1. [Adobe Experience Platformに接続](connect-data.md).

## 対象ユーザ

このガイドは、Adobe Commerceデータを他のAdobeDX 製品に接続するAdobe Commerceのマーチャント向けに設計されています。

### PWA Studioのサポート

詳しくは、 [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/) の使用方法に関するドキュメント [!DNL Data Connection] 拡張機能 (PWA Studioストアフロント )。

### AEMサポート {#aem-support}

詳しくは、 [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html) CIFを使用してAEMレンダリングされた製品ページからExperience Platformに storefront イベントデータを送信する方法を説明するドキュメント — [!DNL Data Connection] 拡張子。

このガイドに記載されていない情報や質問がある場合は、次のリソースを使用してください。

- [ヘルプセンター](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html){target="_blank"}
- [サポートチケット](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket){target="_blank"} — 追加のヘルプを受け取るには、チケットを送信します。