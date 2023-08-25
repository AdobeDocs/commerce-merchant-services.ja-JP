---
title: カスタムイベントの作成
description: Adobe Commerceのデータを他のAdobeDX 製品に接続するカスタムイベントを作成する方法を説明します。
exl-id: 5a754106-c66a-4280-9896-6d065df8a841
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: 659dd2d1b298ec2a98bb4365a46b09d7468daaad
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# カスタムイベントの作成

次の項目を拡張することができます： [イベントプラットフォーム](events.md) 独自のストアフロントイベントを作成して、自社の業界固有のデータを収集する。 カスタムイベントを作成して設定すると、 [Adobe Commerce Events Collector](https://github.com/adobe/commerce-events/tree/main/packages/commerce-events-collectors).

## カスタムイベントの処理

カスタムイベントは、Adobe Experience Platformでのみサポートされています。 カスタムデータは、Adobe Commerceのダッシュボードおよび指標トラッカーには転送されません。

任意の `custom` イベント、コレクター：

- 追加数 `identityMap` 次を使用 `ECID` プライマリ ID として
- 次を含む `email` in `identityMap` セカンダリ ID として _if_ `personalEmail.address` がイベントに設定されている
- イベント全体を `xdm` Edge に転送する前のオブジェクト

例：

Adobe Commerce Events SDK を通じて公開されたカスタムイベント：

```javascript
mse.publish.custom({
    commerce: {
        saveForLaters: {
            value: 1,
        },
    },
});
```

Experience PlatformEdge 内：

```javascript
{
  xdm: {
    identityMap: {
      ECID: [
        {
          id: 'ecid1234',
          primary: true
        }
      ],
      email: [
        {
          id: "runs@safari.ke",
          primary: false
        }
      ]
    },
    commerce: {
        saveForLaters: {
            value: 1
        }
    }
  }
}
```

>[!NOTE]
>
> カスタムイベントを使用すると、デフォルトのAdobe Analyticsレポートに影響を与える場合があります。

## イベントの上書きの処理（カスタム属性）

標準イベントの属性の上書きは、イベントでのみサポートされています。Experience Platform。 カスタムデータは、コマースダッシュボードおよび指標トラッカーには転送されません。

次を含む任意のイベントの `customContext`の場合、コレクターは関連するコンテキストで設定された結合フィールドを、 `customContext`. オーバーライドの使用例は、開発者が、既にサポートされているイベントでページの他の部分によって設定されたコンテキストを再利用し、拡張したい場合です。

>[!NOTE]
>
>カスタムイベントを上書きする場合は、そのイベントタイプに対してExperience Platformへのイベント転送をオフにして、二重カウントを回避する必要があります。

例：

Adobe Commerce Events SDK で公開された上書きを含む製品表示：

```javascript
mse.publish.productPageView({
    productListItems: [
        {
            productCategories: [
                {
                    categoryID: "cat_15",
                    categoryName: "summer pants",
                    categoryPath: "pants/mens/summer",
                },
            ],
        },
    ],
});
```

Experience PlatformEdge 内：

```javascript
{
  xdm: {
    eventType: 'commerce.productViews',
    identityMap: {
      ECID: [
        {
          id: 'ecid1234',
          primary: true,
        }
      ]
    },
    commerce: {
      productViews: {
        value : 1,
      }
    },
    productListItems: [{
        SKU: "1234",
        name: "leora summer pants",
        productCategories: [{
            categoryID: "cat_15",
            categoryName: "summer pants",
            categoryPath: "pants/mens/summer",
        }],
    }],
  }
}
```

>[!NOTE]
>
> カスタム属性を使用したイベントの上書きは、デフォルトのAdobe Analyticsレポートに影響を与える可能性があります。
