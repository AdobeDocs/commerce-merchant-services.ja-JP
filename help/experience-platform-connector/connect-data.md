---
title: コマースデータをAdobe Experience Platformに接続
description: コマースデータをAdobe Experience Platformに接続する方法を説明します。
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: 1af2dee51391c94e19b68481d390cc2629fe1d6e
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# コマースデータをAdobe Experience Platformに接続 {#connectaep}

Adobe CommerceインスタンスをAdobe Experience Platformに接続するには、組織 ID とデータストリーム ID を指定する必要があります。

![Experience Platformコネクタの設定](assets/epc-config.png)

1. でAdobeアカウントにサインイン [Commerce Services コネクタ](../landing/saas.md#organizationid) 組織 ID を選択します。

1. 管理者で、に移動します。 **システム** /サービス/ **Experience Platformコネクタ**.

1. 内 **範囲** ドロップダウンで、コンテキストを **Web サイト**.

1. 内 **組織 ID** 」フィールドに、Adobe Experience Platformアカウントに関連付けられている ID が表示されます。この ID は、 [Commerce Services コネクタ](../landing/saas.md#organizationid). 組織 ID はグローバルです。 1 つのAdobe Commerceインスタンスに関連付けることができる組織 ID は 1 つだけです。

1. 内 **データストリーム ID** 「 」フィールドに、 [作成済み](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html#create) Adobe Experience Platformで

   >[!NOTE]
   >
   >データストリーム ID の範囲は、Web サイトレベル以上で設定する必要があります。 そのレベルでは、階層内の各 Web サイトで同じデータストリーム ID が使用されます。 ストレビューレベルでデータストリーム ID スコープを設定することはできません。

1. （オプション）サイトに AEP Web SDK をデプロイしていない場合は、このフィールドを空白のままにしておくと、Experience Platformコネクタによってデプロイされます。 それ以外の場合は、AEP Web SDK の名前を追加します。

## フィールドの説明

| フィールド | 説明 |
|--- |--- |
| 範囲 | 設定を適用する特定の Web サイト。 |
| 組織 ID （グローバル） | AdobeDX 製品を購入した組織に属する ID。 この ID は、Adobe CommerceインスタンスをAdobe Experience Platformにリンクします。 |
| Datastream ID (Website) | Adobe Experience Platformから他のAdobeDX 製品にデータを送信できるようにする ID。 この ID は、特定のAdobe Commerceインスタンス内の特定の Web サイトに関連付ける必要があります。 |
| AEP Web SDK 名（グローバル） | サイトに AEP Web SDK をデプロイしていない場合は、このフィールドを空白のままにすると、Experience Platformコネクタによってデプロイされます。 既にサイトに AEP Web SDK がデプロイされている場合は、このフィールドにその SDK の名前を指定します。 これにより、Storefront Event Collector および Storefront Event SDK は、Experience Platformコネクタでデプロイされたバージョンではなく、AEP Web SDK を使用できます。 |

Experience Platformコネクタ拡張機能がインストールされ、Adobe CommerceとAdobe Experience Platform間のリンクが作成され、Datastream ID が指定されると、Commerce データがAdobe Experience Platformエッジおよび他のAdobeDX 製品に送られ始めます。

>[!NOTE]
>
> エッジから他のAdobeDX 製品へのデータの流れに要する時間は異なる場合があります。

## エッジでのコマースデータ

コマースデータがAdobe Experience Platform Edge に送信されると、次のようなレポートを作成できます。

![Adobe Experience Managerのコマースデータ](assets/aem-data-1.png)
_Adobe Experience Managerのコマースデータ_
