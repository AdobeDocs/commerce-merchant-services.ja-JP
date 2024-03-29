---
title: Signifyd 不正保護
description: 次の自動不正保護を有効にする： [!DNL Payment Services] Signifyd を持つ
role: Admin, User
level: Intermediate
feature: Payments, Checkout, Configuration, Security
exl-id: 440296bb-a6ff-408b-8195-3027916e4f84
source-git-commit: 480b35fbc57b8528dbc305aa7db52483ba49d98c
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# 信頼できる不正保護

次の自動不正保護を有効にできます： [!DNL Payment Services] と [Signifyd 拡張機能](https://commercemarketplace.adobe.com/signifyd-module-connect.html).

Adobe Commerceは、Signifyd バージョン 5.4.0 以降をサポートしています。 [!DNL Payment Services] は、pre-auth および post-auth の署名フローをサポートします。

ザシグニフィド/[!DNL Payment Services] 統合では、クレジットカード、デビットカード、ヴォールトカード、Admin、PayPal およびApple Pay の支払い方法でのチェックアウトを提供します。 Signifyd は、支払いサービスと Signifyd の間では、取引の一部の詳細が共有されませんが、すべての支払い方法に対して包括的なリスクカバレッジを提供し、最大限の保護を確保します。

詳しくは、 [署名ドキュメント](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#downloadandinstallingmagento2extension) 拡張機能のインストールと設定について説明します。

## オンボーディング

で使用する拡張機能をオンボーディングするには、Signifyd と直接通信する必要があります。 [!DNL Payment Services] — なにもありません [!DNL Payment Services] 設定が必要です。 Signifyd 拡張機能は、インストール後に管理で設定できます。 この拡張機能に関連するサポートは、Signifyd が管理します。

Signifyd を使用したオンボーディングの際は、以下をおこなう必要があります。

1. 新しいアカウントを設定するには、署名者にお問い合わせください。
1. デフォルトでは、Signifyd は [許可リストに加える](https://github.com/signifyd/magento2/blob/main/docs/RESTRICT-PAYMENTS.md) Signifyd が他の支払いオプションをトリガーしないようにするため、現在サポートされていません。 特定の支払い方法を禁止する場合は、変更を加える必要があります。
1. Signifyd で PayPal が Paypal の商人の不正保護設定を通じて、Signifyd が承認できる注文を拒否しないことを確認します。
1. Signifyd 拡張機能との互換性を有効にする [!DNL Payment Services]:
   * を使用する場合 [!DNL Payment Services] in _ライブ_ モードの場合、署名は実稼働モードである必要があります。
   * を使用する場合 [!DNL Payment Services] in _サンドボックス_ モード、シグニフィードはテストモードである必要があります。

## 設定

Signifyd は注文に対して何らかのアクションを実行するので、に設定した支払い処理に基づいて拡張機能が適切に動作するように設定する必要があります。 [!DNL Payment Services].

以下の設定オプションは、支払いサービスおよび Signifyd 統合とは互換性がありません。

* 条件 [!DNL Payment Services] が `Authorize` 支払手続 _および_ Signifyd は次の場所にあります： `PostAuth` モード _[!UICONTROL Decline Guarantees]_オプションをに設定&#x200B;**クレジットメモの作成**.

  理由： [!DNL Payment Services] は、「Signify」が返金を試みる承認トランザクションを作成します。


* [!DNL Payment Services] が `Authorize and Capture` 支払手続 _および_ Signifyd は次の場所にあります： `PostAuth` モード _[!UICONTROL Decline Guarantees]_オプションをに設定&#x200B;**注文をキャンセル**.

  理由： [!DNL Payment Services] は、Signifyd が無効化を試みる取得トランザクションを作成します。


詳しくは、署名に関するドキュメントを参照してください。 [拡張機能の設定](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#configuringmagento2extension).

Signifyd のドキュメントを参照してください。 [順序ワークフローの詳細を説明します](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#howmagento2works).
