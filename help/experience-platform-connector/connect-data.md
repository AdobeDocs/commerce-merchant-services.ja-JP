---
title: コマースデータをAdobe Experience Platformに接続
description: コマースデータをAdobe Experience Platformに接続する方法を説明します。
source-git-commit: 9b5f2da08167e22bbba504009bccc87d0ab02c48
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# コマースデータをAdobe Experience Platformに接続 {#connectaep}

Adobe CommerceデータをAdobe Experience Platformに接続する前に、 [Commerce Services コネクタ](../landing/saas.md#organizationid). ログインして組織 ID を選択した後、 **Experience Platformコネクタ** ページを管理者に表示します。

1. 管理者で、に移動します。 **システム** /サービス/ **Experience Platformコネクタ**.

1. 内 **範囲** 」ドロップダウンで、ストアビューのコンテキストまたは「範囲」を選択します。

   組織 ID はグローバルです。 1 つのAdobe Commerceインスタンスに関連付けることができる組織 ID は 1 つだけです。

1. 内 **IMS 組織** 」フィールドに、Adobe Experience Platformアカウントに関連付けられている ID が表示されます。この ID は、 [Commerce Services コネクタ](../landing/saas.md#organizationid).

1. 内 **データストリーム ID** 「 」フィールドに、データストリームの ID を貼り付けます。 [作成済み](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html) Adobe Experience Platform

## Datastream ID とコマースインスタンスストアの関係

Datastream ID を使用すると、Adobe Experience Platformから他のAdobeDX 製品へのイベント転送が可能になり、特定のAdobe Commerceインスタンス内の特定のストレビューに関連付けることができます。 また、複数のストレビューを同じ Datastream ID に関連付けることもできます。 ビジネスにとって最も意味のある要素によって異なります。

## フィールドの説明

| フィールド | 説明 |
|--- |--- |
| 範囲 | 設定を適用する特定のストアレビュー。 |
| IMS Org（グローバル） | AdobeDX 製品を購入した組織に属する ID。 この ID は、Adobe CommerceインスタンスをAdobe Experience Platformにリンクします。 |
| データストリーム ID （ストアレビュー） | Adobe Experience Platformから他のAdobeDX 製品にデータを送信できるようにする ID。 この ID は、特定のAdobe Commerceインスタンス内の特定の storeView に関連付けることができます。 |

Experience Platformコネクタ拡張機能がインストールされ、Adobe CommerceとAdobe Experience Platformの間にリンクが作成され、データストリーム ID が指定されました。 [!DNL Commerce] データがAdobe Experience Platform edge および他のAdobeDX 製品に送られ始めます。

## エッジでのコマースデータ

コマースデータがAdobe Experience Platform Edge に送信されると、次のようなレポートを作成できます。

![Adobe Experience Managerのコマースデータ](assets/aem-data-1.png)
_Adobe Experience Managerのコマースデータ_
