---
title: コマースデータをAdobe Experience Platformに接続
description: コマースデータをAdobe Experience Platformに接続する方法を説明します。
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: c7344efead97b0562a146f096123dd84f998fd5e
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# コマースデータをAdobe Experience Platformに接続 {#connectaep}

Adobe CommerceインスタンスをAdobe Experience Platformに接続するには、組織 ID とデータストリーム ID を指定する必要があります。

![Experience Platformコネクタの設定](assets/epc-config.png)

1. でAdobeアカウントにサインイン [Commerce Services コネクタ](../landing/saas.md#organizationid) 組織 ID を選択します。

1. 管理者で、に移動します。 **システム** /サービス/ **Experience Platformコネクタ**.

1. 内 **範囲** 」ドロップダウンで、ストアビューのコンテキストまたは「範囲」を選択します。

1. 内 **組織 ID** 」フィールドに、Adobe Experience Platformアカウントに関連付けられている ID が表示されます。この ID は、 [Commerce Services コネクタ](../landing/saas.md#organizationid). 組織 ID はグローバルです。 1 つのAdobe Commerceインスタンスに関連付けることができる組織 ID は 1 つだけです。

1. 内 **データストリーム ID** 「 」フィールドに、 [作成済み](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) Adobe Experience Platformで

## datastream ID とコマースインスタンスのストアレビューの関係

datastream ID を使用すると、Adobe Experience Platformから他のAdobeDX 製品へのイベント転送が可能になり、特定のAdobe Commerceインスタンス内の特定のストアビューに関連付けることができます。 また、複数のストアビューを同じデータストリーム ID に関連付けることもできます。 ビジネスにとって最も意味のある要素によって異なります。 [詳細情報](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en#event-forwarding-settings) イベントの転送について

## フィールドの説明

| フィールド | 説明 |
|--- |--- |
| 範囲 | 設定を適用する特定のストア表示。 |
| 組織 ID （グローバル） | AdobeDX 製品を購入した組織に属する ID。 この ID は、Adobe CommerceインスタンスをAdobe Experience Platformにリンクします。 |
| データストリーム ID （ストア表示） | Adobe Experience Platformから他のAdobeDX 製品にデータを送信できるようにする ID。 この ID は、特定のAdobe Commerceインスタンス内の特定のストア表示に関連付けることができます。 |

Experience Platformコネクタ拡張機能がインストールされ、Adobe CommerceとAdobe Experience Platform間のリンクが作成され、Datastream ID が指定されると、Commerce データがAdobe Experience Platformエッジおよび他のAdobeDX 製品に送られ始めます。

>[!NOTE]
>
> エッジから他のAdobeDX 製品へのデータの流れに要する時間は異なる場合があります。

## エッジでのコマースデータ

コマースデータがAdobe Experience Platform Edge に送信されると、次のようなレポートを作成できます。

![Adobe Experience Managerのコマースデータ](assets/aem-data-1.png)
_Adobe Experience Managerのコマースデータ_
