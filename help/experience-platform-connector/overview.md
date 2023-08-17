---
title: ガイドの概要
description: Experience Platformコネクタを使用してAdobe CommerceデータをAdobe Experience Platformに統合する方法について説明します。
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
recommendations: noCatalog
source-git-commit: 1d8609a607e0bcb74fdef47fb8e4e582085836e2
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# Experience Platformコネクタの概要

Experience Platformコネクタ拡張機能を使用すると、Adobe Commerceのマーチャントが [店頭の](events.md#storefront-events) および [バックオフィス](events.md#back-office-events) Adobe AnalyticsやAdobe Targetなどの他のAdobe Experience Cloud製品がそのコマースデータを使用できるように、Adobe Experience Platform Edge にデータを送信します。 コマースデータをAdobe Experience Cloud内の他の製品に接続することで、サイトでのユーザー行動の分析、AB テストの実行、パーソナライズされたキャンペーンの作成などのタスクを実行できます。

[ストアフロントイベント](events.md#storefront-events) 買い物客のインタラクションのキャプチャ `View Page`, `View Product`, `Add to Cart`、および [購買依頼リスト](events.md#b2b-events) 情報（B2B 商人用） [バックオフィス](events.md#back-office-events) イベントは、注文が発行されたか、取り消されたか、返金されたか、出荷されたか、完了したかなど、注文のステータスに関する情報をキャプチャします。 取り込まれたデータには、個人を特定できる情報 (PII) は含まれません。 Cookie ID や IP アドレスなどのすべてのユーザー識別子は厳密に匿名化されます。 [詳細情報](https://www.adobe.com/privacy/experience-cloud.html).

Experience Platformコネクタは、次の場所にあるコマース管理に表示されます。 **システム** /サービス/ **Experience Platformコネクタ**.

![Experience Platformコネクタ拡張機能の管理ビュー](assets/epc-adminui.png)

## 前提条件 {#prereqs}

Experience Platformコネクタを使用するには、次の条件を満たす必要があります。

- Adobe Commerce 2.4.3 以降
- Adobe IDと組織 ID
- [Adobeクライアントデータレイヤー (ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html). ストアフロントイベントデータを収集するには、ACDL が必要です。
- 他のAdobeDX 製品の使用権限

## オンボーディング手順

1. [インストール](install.md) Experience Platformコネクタ拡張
1. [ログイン](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) をAdobeアカウントに追加し、 [確認するビュー](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255) 組織 ID。 組織 ID は、プロビジョニングされた組織の会社に関連付けられたExperience CloudID です。 この ID は 24 文字の英数字から成る文字列で、その後にが続きます（必須） `@AdobeOrg`.
1. [作成または更新](update-xdm.md) コマース固有のフィールドグループを持つ XDM スキーマ。
1. [データセットの作成](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) 作成または更新したスキーマに基づいて このデータセットには、送信したコマースデータが含まれます。
1. [データストリームの作成](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) をクリックし、コマース固有のフィールドグループを含む XDM スキーマを選択します。
1. [Commerce Services に接続](../landing/saas.md).
1. [Adobe Experience Platformに接続](connect-data.md).

## 対象ユーザ

このガイドは、Adobe Commerceデータを他のAdobeDX 製品に接続するAdobe Commerceのマーチャント向けに設計されています。

### PWA Studioのサポート

詳しくは、 [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/) ドキュメントを参照してください。Experience PlatformストアフロントでのPWA Studioコネクタの使用方法に関する情報です。

### AEMサポート {#aem-support}

詳しくは、 [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html) AEM-Product Connector を使用して、Experience Platformレンダリングの製品ページからExperience Platformに storefront イベントデータを送信する方法を説明するドキュメントです。

このガイドに記載されていない情報や質問がある場合は、次のリソースを使用してください。

- [ヘルプセンター](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html){target="_blank"}
- [サポートチケット](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket){target="_blank"} — 追加のヘルプを受け取るには、チケットを送信します。
