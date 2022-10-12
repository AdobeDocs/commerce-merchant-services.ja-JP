---
title: ガイドの概要
description: Experience Platformコネクタを使用してAdobe CommerceデータをAdobe Experience Platformに統合する方法について説明します。
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
source-git-commit: f5d1c39fe1b02d2a661b92f971fba5b3e836dd6a
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# Experience Platformコネクタの概要

Experience Platformコネクタ拡張機能を使用すると、Adobe CommerceのマーチャントがAdobe Experience Platform Edge にデータを送信し、Adobe AnalyticsやAdobe Targetなどの他のAdobe Experience Cloud製品がそのコマースデータを使用できるようになります。 コマースデータをAdobe Experience Cloud内の他の製品に接続することで、サイトでのユーザー行動の分析、AB テストの実行、パーソナライズされたキャンペーンの作成などのタスクを実行できます。

[ストアフロントイベント](events.md) 買い物客のインタラクションのキャプチャ `View Page`, `View Product`, `Add to Cart`など。 取り込まれたデータには、個人を特定できる情報 (PII) は含まれません。 Cookie ID や IP アドレスなどのすべてのユーザー識別子は厳密に匿名化されます。 [詳細情報](https://www.adobe.com/privacy/experience-cloud.html).

Experience Platformコネクタは、次の場所にあるコマース管理に表示されます。 **システム** /サービス/ **Experience Platformコネクタ**.

![Experience Platformコネクタ拡張機能の管理ビュー](assets/epc-adminui.png)

## 前提条件 {#prereqs}

Experience Platformコネクタを使用するには、次が必要です。

- Adobe Commerce 2.4.3 以降
- Adobe IDと組織 ID
- 他のAdobeDX 製品の使用権限

## オンボーディング手順

1. [インストール](install.md) Experience Platformコネクタ拡張
1. [ログイン](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) をAdobeアカウントに追加し、 [表示](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=en#concept_EA8AEE5B02CF46ACBDAD6A8508646255) 組織 ID。 組織 ID は、プロビジョニングされた組織の会社に関連付けられたExperience CloudID です。 この ID は 24 文字の英数字から成る文字列で、その後にが続きます（必須） `@AdobeOrg`.
1. [接続](connect-data.md) Adobe CommerceインスタンスをAdobe Experience Platformに追加します。
1. [作成または更新](update-xdm.md) コマース固有のフィールドグループを持つ XDM スキーマ。
1. [データストリームの作成](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) をクリックし、コマース固有のフィールドグループを含む XDM スキーマを選択します。
1. （オプション） [買い物客プロファイルのアップロード](profile.md) Adobe Experience Platformのストアフロントデータを特定の買い物客に関連付けて、買い物体験を向上させることができます。

## 対象ユーザ

このガイドは、Adobe Commerceストアフロントデータを他のAdobeDX 製品に接続するAdobe Commerceの商人を対象としています。

### PWA Studioサポート

詳しくは、 [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/) ドキュメントを参照してください。Experience PlatformストアフロントでのPWA Studioコネクタの使用方法に関する情報です。

### AEMサポート {#aem-support}

詳しくは、 [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html) AEM-Product Connector を使用して、Experience Platformレンダリングの製品ページからExperience Platformに storefront イベントデータを送信する方法を説明するドキュメントです。

このガイドに記載されていない情報や質問がある場合は、次のリソースを使用してください。

- [ヘルプセンター](https://support.magento.com/hc/en-us){target=&quot;_blank&quot;}
- [サポートチケット](https://support.magento.com/hc/en-us/articles/360000913794#submit-ticket){target=&quot;_blank&quot;} — 追加のヘルプを受け取るには、チケットを送信します。
