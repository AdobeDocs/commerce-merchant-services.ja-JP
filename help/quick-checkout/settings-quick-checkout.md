---
title: 「 [!DNL Quick Checkout] for Adobe Commerce extension"
description: 「 [!DNL Quick Checkout] 拡張機能のオンボーディングとセットアップに成功する方法について説明します。
source-git-commit: bd02a8083d3f4c9cb0422b27d61bd5462187ffc3
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---


# [!DNL Quick Checkout] 設定

[!DNL Quick Checkout] Adobe CommerceとMagento Open Sourceの場合は、拡張機能の設定に必要な情報がすべて表示され、設定ビューが表示されます。

これらの設定にアクセスするには：

1. の _管理者_ サイドバー、移動 **ストア** > _設定_ > **設定**.
1. 左側のパネルで、を展開します。 **セールス** を選択し、 **チェックアウト**.

   ![クイックチェックアウト](assets/quick-checkout-main-view-react.png)

詳しくは、 [オンボーディング](../quick-checkout/onboarding.md) の設定方法の詳細に関するトピック [!DNL Quick Checkout] Adobe Commerce

## 拡張機能を有効にする

| フィールド | 範囲 | 説明 |
|---|---|---|
| [!UICONTROL Enable] | web サイト | 有効または無効 [!DNL Quick Checkout] を設定します。 オプション： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Method] | web サイト | のメソッドまたは環境を設定します。 [!DNL Quick Checkout]. オプション： [!UICONTROL Sandbox] / [!UICONTROL Production] |

## アカウント資格情報

| フィールド | 範囲 | 説明 |
|---|---|---|
| [!UICONTROL API key] | web サイト | バックエンドが操作に使用する秘密鍵 [!DNL Bolt] API |
| [!UICONTROL Publishable key] | web サイト | フロントエンドがとやり取りする際に使用するキー [!DNL Bolt] API |
| [!UICONTROL Signing secret] | web サイト | から受信した要求の署名検証に使用されます [!DNL Bolt]. |

## サービス設定

| フィールド | 範囲 | 説明 |
|---|---|---|
| [!UICONTROL Title] | ストア表示 | チェックアウト時に「支払い方法」ビューで、この支払いオプションのタイトルとして表示するテキストを追加します。 オプション： [!UICONTROL text field] |
| [!UICONTROL Payment Action] | web サイト | この [支払手続](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;} （指定した支払い方法） オプション： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | web サイト | デバッグモードを有効または無効にします。 オプション： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Enable checkout tracking] | web サイト | Adobe Commerceがチェックアウトのトラッキング情報を Bolt と共有するかどうかを定義します。 デフォルトで有効です。 無効にした場合、レポートは影響を受けます。 オプション： [!UICONTROL Yes] / [!UICONTROL No] |
