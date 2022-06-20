---
title: イベント
description: どのイベントがデータをキャプチャし、完全なスキーマ定義を確認するかを説明します。
source-git-commit: ce1ce5a7e028d1c957a9a36c73c371eedfb1e1e8
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# プロジェクトビーコンイベント

以下に、 [!DNL Commerce] イベントコネクタ拡張機能をインストールするとExperience Platformが使用できます。 これらのイベントで収集されたデータは、Adobe Experience Platform Edge に送信されます。 また、 [カスタムイベント](custom-events.md) 標準で提供されていない追加データを収集する場合。

イベント名をクリックすると、完全なスキーマ定義が表示されます。

| イベント | タイプ |
|---|---|---|
| [買い物かごに追加](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/addToCartAEP.ts) | ストアフロント |
| [買い物かごを表示](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/viewAEP.ts) | ストアフロント |
| [ページを表示](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/page/viewAEP.ts) | ストアフロント |
| [製品を表示](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/viewAEP.ts) | ストアフロント |
| [チェックアウトを開始](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/initiateCheckoutAEP.ts) | ストアフロント |
| チェックアウトの完了 | ストアフロント |
| [ログイン](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signInAEP.ts) | プロファイル |
| [ログアウト](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signOutAEP.ts) | プロファイル |
| [アカウントを作成](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/createAccountAEP.ts) | プロファイル |
| [アカウントの編集](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/editAccountAEP.ts) | プロファイル |

>[!NOTE]
>
> この `Sign In`, `Sign Out`, `Create Account`、および `Update Account` イベントは、特定のアクションが試行されたときにトリガーされます。 アクションが成功したことは示されません。
