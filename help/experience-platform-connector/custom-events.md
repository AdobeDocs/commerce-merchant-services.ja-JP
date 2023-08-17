---
title: カスタムイベントの作成
description: Adobe Commerceのデータを他のAdobeDX 製品に接続するカスタムイベントを作成する方法を説明します。
exl-id: 5a754106-c66a-4280-9896-6d065df8a841
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: 1d8609a607e0bcb74fdef47fb8e4e582085836e2
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# カスタムイベントの作成

次の項目を拡張することができます： [イベントプラットフォーム](events.md) 独自のストアフロントイベントを作成して、自社の業界固有のデータを収集する。 カスタムイベントを作成して設定すると、 [Adobe Commerce Events Collector](https://github.com/adobe/commerce-events/tree/main/packages/commerce-events-collectors).

## カスタムイベントの処理

カスタムイベントは、Adobe Experience Platformでのみサポートされています。 カスタムデータは、Adobe Commerceのダッシュボードおよび指標トラッカーには転送されません。

任意の `custom` イベント、コレクターが `personId` (`ecid`) から `customContext` を囲んで `xdm` オブジェクトを囲んでから Edge に転送します。

例：

Adobe Commerce Events SDK を通じて公開されたカスタムイベント：

```javascript
mse.publish.custom({
    customContext: { customStrAttr: "cheetah", customNumAttr: 128 },
});
```

Experience PlatformEdge 内：

```javascript
{
    xdm: {
        personId: 'ecid1234',
        customStrAttr: 'cheetah',
        customNumAttr: 128
    }
}
```

>[!NOTE]
>
> カスタムイベントを使用すると、デフォルトのAdobe Analyticsレポートに影響を与える場合があります。

## イベントの上書きの処理（カスタム属性）

標準イベントの属性の上書きは、イベントでのみサポートされています。Experience Platform。 カスタムデータは、コマースダッシュボードおよび指標トラッカーには転送されません。

が設定された任意のイベントの `customContext`、コレクターが上書きされます `personId` およびAdobe Analyticsカウンタ。 `customContext`.

例：

Adobe Commerce Events SDK で公開された上書きを含む製品表示：

```javascript
mse.publish.productPageView({
    customContext: { customCode: "okapi" },
});
```

Experience PlatformEdge 内：

```javascript
{
    xdm: {
        eventType: 'commerce.productViews',
        personId: 'ecid1234',
        customCode: 'okapi',
        commerce: {
            productViews: {
                value : 1
            }
        }
    }
}
```

Adobe Commerce Events SDK で公開されたAdobe Commerceの製品表示が、次のように上書きされます。

```javascript
mse.publish.productPageView({
    customContext: { commerce: { customCode: "mongoose" } },
});
```

Experience PlatformEdge 内：

```javascript
{
    xdm: {
        eventType: 'commerce.productViews',
        personId: 'ecid1234',
        commerce: {
            customCode: 'mongoose',
            productViews: {
                value : 1
            }
        }
    }
}
```

>[!NOTE]
>
> カスタム属性を使用したイベントの上書きは、デフォルトのAdobe Analyticsレポートに影響を与える可能性があります。
