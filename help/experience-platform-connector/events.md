---
title: イベント
description: どのイベントがデータをキャプチャし、完全なスキーマ定義を確認するかを説明します。
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
source-git-commit: 2b735c292920bb0e9052d86bf152748e7ce96079
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Experience Platformコネクタイベント

次に、Commerce Connector 拡張機能をインストールする際に使用できる CommerceExperience Platformを示します。 これらのイベントで収集されたデータは、Adobe Experience Platform Edge に送信されます。 また、 [カスタムイベント](custom-events.md) 標準で提供されていない追加データを収集する場合。

イベント名をクリックすると、完全なスキーマ定義が表示されます。

| イベント | タイプ |
|---|---|
| [買い物かごに追加](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/addToCartAEP.ts) | ストアフロント |
| [買い物かごを表示](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/viewAEP.ts) | ストアフロント |
| [ページを表示](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/page/viewAEP.ts) | ストアフロント |
| [製品を表示](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/viewAEP.ts) | ストアフロント |
| [チェックアウトを開始](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/initiateCheckoutAEP.ts) | ストアフロント |
| [チェックアウトの完了](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/checkout/placeOrderAEP.ts) | ストアフロント |
| [ログイン](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signInAEP.ts) | プロファイル |
| [ログアウト](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signOutAEP.ts) | プロファイル |
| [アカウントを作成](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/createAccountAEP.ts) | プロファイル |
| [アカウントの編集](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/editAccountAEP.ts) | プロファイル |
| [検索リクエストが送信されました](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/search/searchRequestSentAEP.ts) | 検索 |
| [検索応答を受信しました](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/search/searchResponseReceivedAEP.ts) | 検索 |

>[!NOTE]
>
> この `Sign In`, `Sign Out`, `Create Account`、および `Update Account` イベントは、特定のアクションが試行されたときにトリガーされます。 アクションが成功したことは示されません。
