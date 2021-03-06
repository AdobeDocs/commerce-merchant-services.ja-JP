---
title: ガイドの概要
description: Adobe Commerce用Adobe Experience Platform Connector が [!DNL Commerce] インスタンスを他のAdobe Experience Cloud製品に追加します。
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
source-git-commit: 334ee967ec2379a87acfc5fb427d7ada6fa25ee7
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# Experience Platformコネクタの概要

Experience Platformコネクタ拡張機能を使用すると、Adobe CommerceのマーチャントがAdobe Experience Platform Edge にデータを送信して、Adobe AnalyticsやAdobe Targetなどの他のAdobe Experience Cloud製品でそのデータを使用できるようになります [!DNL Commerce] データ。 接続する [!DNL Commerce] Adobe Experience Cloudの他の製品に対するデータを使用すると、サイトでのユーザー行動の分析、AB テストの実行、パーソナライズされたキャンペーンの作成などのタスクを実行できます。

ストアフロントイベントは、買い物客のインタラクションをキャプチャします ( 例： `View Page`, `View Product`, `Add to Cart`など。 取り込まれたデータには、個人を特定できる情報 (PII) は含まれません。 Cookie ID や IP アドレスなどのすべてのユーザー識別子は厳密に匿名化されます。 [詳細情報](https://www.adobe.com/privacy/experience-cloud.html). 詳しくは、 [storefront イベント](events.md).

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

   Experience Platformコネクタ拡張機能は、サーバーのコマンドラインからインストールされ、Adobe Commerceインストールに as a [サービス](../landing/saas.md). 処理が完了すると、Experience Platformコネクタが **システム** 下のメニュー **サービス** 内 [!DNL Commerce] _管理者_.

## 対象ユーザ

このガイドは、Adobe Commerceの店舗データを他のAdobeDX 製品に接続する必要があるAdobe Commerceの商人を対象にしています。

## 既知の問題

現在、Experience Platformコネクタには次の既知の問題があります。

- B2B モジュールがインストールされているAdobe Commerce Enterprise Edition では、検索イベントはサポートされていません。
- ストアフロントデータは、Adobe Experience Platform Edge に接続した後、Adobe Commerceから様々な宛先に到達するまでに約 1 時間かかります。

## サポート

このガイドに記載されていない情報や質問がある場合は、次のSlackチャネルに投稿してください。

- `#beacon-ama`
