---
title: 支払いオプション
description: 支払いオプションを設定して、店舗の顧客が利用できる方法をカスタマイズします。
exl-id: 95e648e6-6cb8-4226-b5ea-e1857212f20a
feature: Payments, Checkout, Configuration
source-git-commit: c4068d71eba45ea45b1c1eefc324bf830479e0e3
workflow-type: tm+mt
source-wordcount: '1048'
ht-degree: 0%

---

# 支払いオプション

を使用 [!DNL Adobe Commerce] および [!DNL Magento Open Source] [!DNL Payment Services]、複数の支払いオプションを使用できます。 これらの支払いオプションは、次の方法で設定できます。

* [ホーム設定](payments-home.md)
* [ストア設定](configure-admin.md) （従来の支払いオプションまたはマルチストア設定に推奨）

支払い方法ごとに、チェックアウトプロセスの場所に応じて異なる行動があります。

* 「製品」ページ — 品目の製品ページ
* 「ミニカート」(Mini cart) — 製品がカートに追加されたときに、カートアイコンをクリックすると使用できます。
* 買い物かご — クリックで利用可能 _買い物かごの表示と編集_ ミニカートから
* 「チェックアウト」(Checkout) ビュー — クリック時に使用可能 _チェックアウトに進みます。_ ミニカートまたは買い物かごから

>[!IMPORTANT]
>
>支払いを処理する前に、支払いサービスのオンボーディングを完了する必要があります。

## [!UICONTROL Credit Card Fields]

[!UICONTROL Credit Card Fields] クレジットカードまたはデビットカードの支払い方法に対して、簡単で安全なチェックアウトを提供します。 買い物客がクレジットカードのフィールドを使用してチェックアウトする際、名前、請求先住所、クレジットカードまたはデビットカードの情報を入力して、注文をおこないます。 顧客情報は、購入セッション中に安全に使用され、チェックアウトフローをシームレスに導きます。

有効にする [クレジットカードの保管](#vaulting) 店舗で買い物客が後で迅速なチェックアウトを行うために、クレジットカード情報を逃がす（保存する）ことを許可するため。

次の項目を設定できます。 [!UICONTROL Credit Card Fields] （ストア設定または支払いサービスホーム）を参照してください。 詳しくは、 [設定](settings.md#credit-card-fields) を参照してください。

また、クレジットカードフィールドのレイアウト、幅、高さ、外側のスタイルを変更することもできます。 詳しくは、 [PayPal ドキュメント](https://developer.paypal.com/docs/checkout/advanced/customize/card-field-style/) を参照してください。

## [!DNL Apple Pay] ボタン

お客様は、 [[!DNL Apple Pay]](https://www.apple.com/apple-pay/)：購入の際に、iOSまたはmacOSデバイスに保存されたクレジットカードおよびデビットカードの支払い資格情報を使用します。

The [!DNL Apple Pay] ボタンが製品ページ、ミニカート、買い物かご、チェックアウトビューに表示されます。

>[!NOTE]
>
> 次を使用するには： [!DNL Apple Pay] 店舗の場合は、 [～との自己登録 [!DNL Apple Pay]](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) (_ライブドメインを登録_ セクションのみ ) および [次のストアに対して設定します。 [!DNL Payment Services]](settings.md#payment-buttons).

次の項目を設定できます。 [!UICONTROL Apple Pay] （ストア設定または支払いサービスホーム）を参照してください。 詳しくは、 [設定](settings.md#apple-pay) を参照してください。

## [!DNL PayPal Smart Buttons]

[!DNL PayPal Smart Buttons]: PayPal を使用して購入を完了し、買い物客の配送先住所、請求先住所、支払いの詳細を保存して後で使用します。 買い物客は、以前に PayPal に保存または提供された任意の支払い方法を使用できます。

![[!DNL PayPal Smart Buttons] options](assets/payment-buttons.png){width="400" zoomable="yes"}

次の項目を設定できます。 [!UICONTROL PayPal Smart Buttons] （ストア設定または支払いサービスホーム）を参照してください。  詳しくは、 [設定](settings.md#payment-buttons) を参照してください。

PayPal の「 [支払い方法に関するドキュメント](https://developer.paypal.com/docs/checkout/payment-methods/) 各支払い方法が現在どの国で利用できるかを確認する。

### [!DNL PayPal] ボタン

お客様は PayPal ボタンを使用して、簡単かつ信頼性の高い方法でチェックアウトできます。

The [!DNL PayPal] ボタンが製品ページ、ミニカート、買い物かご、チェックアウトビューに表示されます。

### [!DNL Venmo] ボタン

お客様は、 [ベンモ](https://venmo.com/) 」ボタンをクリックします。

The [!DNL Venmo] ボタンが製品ページ、ミニカート、買い物かご、チェックアウトビューに表示されます。

### PayPal のデビットまたはクレジットカードボタン

お客様は、PayPal のデビットまたはクレジットカードのボタンを使用してチェックアウトできます。

PayPal のデビットまたはクレジットカードのボタンは、チェックアウトページに表示されます。

このオプションは、クレジットカード統合の代わりに PayPal がホストするボタンを使用して、買い物客にデビットまたはクレジットカードの支払いオプションを提示するために使用できます。

### [!DNL Pay Later] ボタン

顧客が今すぐ購入し、後で [!DNL Pay Later] 」ボタンをクリックします。

The [!DNL Pay Later] ボタンが製品ページ、ミニカート、買い物かご、チェックアウトビューに表示されます。

詳しくは、 [PayPal の Pay Later オファードキュメント](https://developer.paypal.com/docs/checkout/pay-later/us/). 以下を使用します。 **国または地域** 関心のある地域を選択するドロップダウン。

詳しくは、 [設定](settings.md#payment-buttons) 無効にする/有効にする方法を学ぶには [!DNL Pay Later] メッセージ。

### [!DNL Pay Now] ボタン

The [!DNL Pay Now] ボタンは、顧客が支払い画面で支払いボタンをクリックすると、PayPal ポップアップウィンドウに表示されます。

最終注文額が不明な場合（発送先住所情報がない場合など）、顧客が製品ページ、ミニカートまたは買い物かごからチェックアウトする過程にある場合、 _続行_ 」ボタンを使用できます。 顧客が _続行_&#x200B;支払い方法を確認した後、注文レビューページに移動し、チェックアウトを完了する前に必要な詳細を収集します。

## PayPal の支払いボタンのみを使用

ストアを実稼動モードにすばやく移行するには、を設定します。 _のみ_ PayPal の支払いボタン（Venmo、PayPal など）- PayPal クレジットカードの支払いオプションを使用する代わりに使用します。

次の操作が可能です。

* Venmo や PayPal の支払いボタンなど、顧客に対して様々な支払いオプションを提供し、PayPal がホストするカードフィールドをオフにし、既存のクレジットカードプロバイダーを使用するオプションを提供します。
* PayPal の他の支払いオプションを利用しながら、クレジットカードの支払いには、既存のクレジットカードプロバイダを使用します。
* PayPal がクレジットカードを支払いオプションとしてサポートしていない地域で、PayPal の支払いボタンを使用します。

宛先 **～で支払いをキャプチャする _のみ_ PayPal の支払いボタン (_not_ （PayPal クレジットカードの支払いオプション）**:

1. ストアが以下であることを確認します。 [実稼動モード](settings.md#enable-payment-services).
1. [PayPal の支払いボタンを設定します](settings.md#payment-buttons) 」と入力します。
1. 回転 _オフ_ の **[[!UICONTROL Show PayPal Credit and Debit card button]](settings.md#payment-buttons)** オプションを _[!UICONTROL Payment buttons]_」セクションに入力します。

宛先 **既存のクレジットカードプロバイダーに支払いをキャプチャする _および_ PayPal の支払いボタン**:

1. ストアが以下であることを確認します。 [実稼動モード](settings.md#enable-payment-services).
1. [PayPal の支払いボタンを設定します](settings.md#payment-buttons).
1. 回転 _オフ_ の **[[!UICONTROL PayPal Show Credit and Debit card button]](settings.md#payment-buttons)** オプションを _[!UICONTROL Payment buttons]_」セクションに入力します。
1. 回転 _オフ_ の **[[!UICONTROL Show on checkout page]](settings.md#credit-card-fields)** オプションを _[!UICONTROL Credit card fields]_セクションを開き、 [既存のクレジットカードプロバイダーアカウント](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/payments.html#payments).

## 注文の再計算

顧客がミニカート、買い物かごまたは製品ページからチェックアウトフローに入ると、注文レビューページに移動し、PayPal ポップアップウィンドウで選択した配送先住所を確認できます。 顧客が発送方法を選択すると、注文額が適切に再計算され、顧客は配送費と税金を確認できます。

顧客がチェックアウトページからチェックアウトフローに入ると、システムは既に配送先住所と最終的な計算額を認識し、合計が適切に表示されます。

税金の休日、送料、消費税は、場所によって大きく異なる場合があります。 後 [!DNL Payment Services] 配送先住所と料金を受け取ると、該当するすべてのコストがすぐに再計算され、チェックアウトの最後の段階で適切に表示されます。

## クレジットカードの保管

買い物客は、Web サイトレベル（同じ商人のアカウント内の任意の店舗）での将来の購入に備えて、クレジットカード情報を保管（保存）できます。

詳しくは、 [クレジットカードの保管](vaulting.md) を参照してください。

## セキュリティ

詳しくは、 [PCI コンプライアンス](security.md#pci-compliance) を参照してください。
