---
title: を設定します。 [!DNL Quick Checkout] Adobe Commerce拡張機能
description: の設定オプションについて説明します。 [!DNL Quick Checkout] およびは、拡張機能のオンボーディングとセットアップに成功する方法を示しています。
exl-id: 892e04dc-17d6-45e9-b2ab-c7a0735a75bc
feature: Checkout, Services
source-git-commit: 6ba5a283d9138b4c1be11b80486826304c63247f
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 1%

---

# [!DNL Quick Checkout] 設定

[!DNL Quick Checkout] Adobe CommerceとMagento Open Sourceの場合は、拡張機能の設定に必要な情報がすべて表示され、設定ビューが表示されます。

次の設定にアクセスするには：

1. 次の日： _管理者_ サイドバー、移動 **ストア** > _設定_ > **設定**.
1. 左側のパネルで、を展開します。 **セールス** を選択し、 **チェックアウト**.

   ![クイックチェックアウト](assets/config-new-logo-view.png){width="800" zoomable="yes"}

詳しくは、 [オンボーディング](../quick-checkout/onboarding.md) の設定方法の詳細に関するトピック [!DNL Quick Checkout] Adobe Commerceの

## 拡張機能を有効にする

![クイックチェックアウト](assets/enable-method.png){width="500" zoomable="yes"}

| フィールド | 範囲 | 説明 |
|---|---|---|
| [!UICONTROL Enable] | web サイト | 有効または無効 [!DNL Quick Checkout] を設定します。 オプション： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Method] | web サイト | のメソッドまたは環境を設定します。 [!DNL Quick Checkout]. オプション： [!UICONTROL Sandbox] / [!UICONTROL Production] |

{style="table-layout:auto"}

## アカウント資格情報

![クイックチェックアウト](assets/account-creds.png){width="500" zoomable="yes"}

| フィールド | 範囲 | 説明 |
|---|---|---|
| [!UICONTROL API key] | web サイト | バックエンドがとのやり取りに使用する秘密鍵 [!DNL Bolt] API |
| [!UICONTROL Publishable key] | web サイト | フロントエンドがとやり取りする際に使用するキー [!DNL Bolt] API |
| [!UICONTROL Signing secret] | web サイト | から受信した要求の署名検証に使用されます [!DNL Bolt]. |

{style="table-layout:auto"}

## サービス設定

![クイックチェックアウト](assets/service-settings.png){width="500" zoomable="yes"}

| フィールド | 範囲 | 説明 |
|---|---|---|
| [!UICONTROL Title] | ストア表示 | チェックアウト時に「支払い方法」ビューで、この支払いオプションのタイトルとして表示するテキストを追加します。 オプション： [!UICONTROL text field] |
| [!UICONTROL Payment Action] | web サイト | The [支払手続](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} 指定した支払い方法の オプション： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | web サイト | デバッグモードを有効または無効にします。 オプション： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Enable checkout tracking] | web サイト | Adobe Commerceがチェックアウトのトラッキング情報を Bolt と共有するかどうかを定義します。 デフォルトで有効です。 無効にした場合、レポートは影響を受けます。 オプション： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Next Stage After Login Mode] | web サイト | 顧客がログインした後にナビゲーションフローを変更する。 オプション： [!UICONTROL Payment] / [!UICONTROL Shipping] |
| [!UICONTROL Automatic Login Enabled] | web サイト | 次の場合に定義 [!DNL Quick Checkout] では、チェックアウト時の自動ログインを許可します。 デフォルトで有効です。 オプション： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Automatic Login Network] | web サイト | 顧客が自動的にログインするネットワークを選択します。 既定で Bolt が有効になっています。 オプション： [!UICONTROL Bolt + Merchant] / [!UICONTROL Bolt] |

{style="table-layout:auto"}
