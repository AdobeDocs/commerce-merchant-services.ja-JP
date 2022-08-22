---
title: コマースデータをAdobe Experience Platformに接続
description: コマースデータをAdobe Experience Platformに接続する方法を説明します。
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: 5f8fcc3d6d05cdd854eadd14f53e1ca13625dae3
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# コマースデータをAdobe Experience Platformに接続 {#connectaep}

Adobe CommerceデータをAdobe Experience Platformに接続する前に、 [Commerce Services コネクタ](../landing/saas.md#organizationid). ログインして組織 ID を選択した後、 **Experience Platformコネクタ** ページを管理者に表示します。

![Experience Platformコネクタの設定](assets/epc-config.png)

1. 管理者で、に移動します。 **システム** /サービス/ **Experience Platformコネクタ**.

1. 内 **範囲** 」ドロップダウンで、ストアビューのコンテキストまたは「範囲」を選択します。

   IMS Org ID はグローバルです。 Adobe Commerceインスタンスごとに関連付けることができる IMS Org ID は 1 つだけです。

1. 内 **IMS Org ID** 」フィールドに、Adobe Experience Platformアカウントに関連付けられている ID が表示されます。この ID は、 [Commerce Services コネクタ](../landing/saas.md#organizationid).

1. 内 **データストリーム ID** 「 」フィールドに、 [作成済み](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) Adobe Experience Platform

## Datastream ID とコマースインスタンスストアの関係

Datastream ID を使用すると、Adobe Experience Platformから他のAdobeDX 製品へのイベント転送が可能になり、特定のAdobe Commerceインスタンス内の特定のストアビューに関連付けることができます。 また、複数のストアビューを同じデータストリーム ID に関連付けることもできます。 ビジネスにとって最も意味のある要素によって異なります。 [詳細情報](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en#event-forwarding-settings) イベントの転送について

## フィールドの説明

| フィールド | 説明 |
|--- |--- |
| 範囲 | 設定を適用する特定のストア表示。 |
| IMS Org（グローバル） | AdobeDX 製品を購入した組織に属する ID。 この ID は、Adobe CommerceインスタンスをAdobe Experience Platformにリンクします。 |
| データストリーム ID （ストア表示） | Adobe Experience Platformから他のAdobeDX 製品にデータを送信できるようにする ID。 この ID は、特定のAdobe Commerceインスタンス内の特定の storeView に関連付けることができます。 |

Experience Platformコネクタ拡張機能がインストールされ、Adobe CommerceとAdobe Experience Platform間のリンクが作成され、Datastream ID が指定されると、Commerce データがAdobe Experience Platformエッジおよび他のAdobeDX 製品に送られ始めます。

## エッジでのコマースデータ

コマースデータがAdobe Experience Platform Edge に送信されると、次のようなレポートを作成できます。

![Adobe Experience Managerのコマースデータ](assets/aem-data-1.png)
_Adobe Experience Managerのコマースデータ_
