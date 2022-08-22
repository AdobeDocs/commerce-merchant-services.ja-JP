---
title: ガイドの概要
description: Adobe Commerce用Adobe Experience Platformコネクタは、コマースインスタンスを他のAdobe Experience Cloud製品に接続します。
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
source-git-commit: 2fb44e73a76ad4e1433b2abd88be1304e7e10596
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---

# Experience Platformコネクタの概要

Experience Platformコネクタ拡張機能を使用すると、Adobe CommerceのマーチャントがAdobe Experience Platform Edge にデータを送信し、Adobe AnalyticsやAdobe Targetなどの他のAdobe Experience Cloud製品がそのコマースデータを使用できるようになります。 コマースデータをAdobe Experience Cloud内の他の製品に接続することで、サイトでのユーザー行動の分析、AB テストの実行、パーソナライズされたキャンペーンの作成などのタスクを実行できます。

ストアフロントイベントは、買い物客のインタラクションをキャプチャします ( 例： `View Page`, `View Product`, `Add to Cart`など。 取り込まれたデータには、個人を特定できる情報 (PII) は含まれません。 Cookie ID や IP アドレスなどのすべてのユーザー識別子は厳密に匿名化されます。 [詳細情報](https://www.adobe.com/privacy/experience-cloud.html). 詳しくは、 [storefront イベント](events.md).

Experience Platformコネクタは、次の場所にあるコマース管理に表示されます。 **システム** /サービス/ **Experience Platformコネクタ**.

![Experience Platformコネクタ拡張機能の管理ビュー](assets/epc-adminui.png)

## Experience Platformコネクタ使用の前提条件 {#prereqs}

Experience Platformコネクタを使用するには、まず次の操作を行う必要があります。

- 次の情報を入力します。 [フォーム](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4VH_dtG9hJVAk_TqGkZC2DxUM1FSWkdJOE41UVpUWUw0M1JWV0RKS1VXQi4u) およびAdobeは、（必要に応じて）Datastreams とAdobe Experience Platformへのアクセスを提供します。

アクセス権が付与された場合：

1. [ログイン](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) をAdobeアカウントに追加します。
1. 以下を見てください： [組織](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=en#concept_EA8AEE5B02CF46ACBDAD6A8508646255). 組織 ID は、プロビジョニングされた組織の会社に関連付けられたExperience CloudID です。 この ID は 24 文字の英数字から成る文字列で、その後にが続きます（必須） `@AdobeOrg`.
1. を作成または更新します。 [XDM スキーマ](update-xdm.md) コマース固有のフィールドグループを持つ
1. [データストリームの作成](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) を選択し、コマース固有の **フィールドグループ**.

>[!NOTE]
>
> 組織 ID とデータストリームは、Adobe CommerceインスタンスをAdobe Experience Platformに接続するために使用されます。

## 次の手順

- のインストール [Experience Platformコネクタ拡張](install.md).

   Experience Platformコネクタ拡張機能は、サーバーのコマンドラインからインストールされ、Adobe Commerceインストールに as a [サービス](../landing/saas.md). 処理が完了すると、Experience Platformコネクタが **システム** 下のメニュー **サービス** （コマース内） _管理者_.
- [買い物客プロファイルのアップロード](profile.md) Adobe Experience Platformのストアフロントデータを特定の買い物客に関連付けて、買い物体験を向上させることができます。

## 対象ユーザ

このガイドは、Adobe Commerceの店舗データを他のAdobeDX 製品に接続する必要があるAdobe Commerceの商人を対象にしています。

### PWA Studioサポート

詳しくは、 [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/) ドキュメントを参照してください。Experience PlatformストアフロントでのPWA Studioコネクタの使用方法に関する情報です。

## 既知の問題

現在、Experience Platformコネクタには次の既知の問題があります。

- B2B モジュールがインストールされているAdobe Commerce Enterprise Edition では、検索イベントはサポートされていません。
- ストアフロントデータは、Adobe Experience Platform Edge に接続した後、Adobe Commerceから様々な宛先に到達するまでに約 1 時間かかります。

このガイドに記載されていない情報や質問がある場合は、次のリソースを使用してください。

- [ヘルプセンター](https://support.magento.com/hc/en-us){target=&quot;_blank&quot;}
- [サポートチケット](https://support.magento.com/hc/en-us/articles/360000913794#submit-ticket){target=&quot;_blank&quot;} — 追加のヘルプを受け取るには、チケットを送信します。
