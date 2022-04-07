---
title: レガシー支払いサービスの設定
description: インストール後、 [!DNL Payment Services] ストア設定の「管理者」で、
role: Admin, User
level: Intermediate
exl-id: e1a3269d-bdf9-4b0f-972f-e8a0ef469503
source-git-commit: bfb2b6632fe494d6e392c214f5e3f5a11930c0b2
workflow-type: tm+mt
source-wordcount: '726'
ht-degree: 0%

---

# レガシー支払いサービスの設定

カスタマイズ可能 [!DNL Payment Services] を必要に応じて管理者の設定オプションを使用できます。

設定時に [!DNL Payment Services] Adobe Commerceと管理Magento Open Sourceの場合、これらの設定は、 [!UICONTROL Method] ～の分野 [!UICONTROL General Configuration]. 設定フィールドで行った変更は、 [!UICONTROL Method] 「選択」(selection) — メソッドを切り替えても、選択はリセットされません。

詳しくは、 [[!UICONTROL General Configuration] セクション](#general-configuration) を参照してください。

## 一般設定

次を有効にすることができます。 [!DNL Payment Services] ストアに対して、でサンドボックステストまたはライブ支払いを有効にします。 [!UICONTROL General Configuration] 」セクションに入力します。

1. の _管理者_ サイドバー、移動 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 左側のパネルで、を展開します。 **[!UICONTROL Sales]** を選択します。 **[!UICONTROL Payment Methods]**.

   ![メソッドビュー](assets/methods-view.png)

1. を展開します。 _[!UICONTROL Recommended Solutions]_」セクションに入力します。
1. 内 _[!UICONTROL [!DNL Payment Services]]_セクションで、_[!UICONTROL General Configuration]_ 」セクションに入力します。
1. の場合 **有効にする**&#x200B;に設定し、 `Yes` 有効にする [!DNL Payment Services] お客様のストアの
1. の場合 **メソッド**&#x200B;に設定し、 `Sandbox` まだテスト中の場合 [!DNL Payment Services] お客様のストアまたは `Production` ライブ支払いを有効にする準備が整っている場合。

   >[!WARNING]
   >
   >お使いの [!UICONTROL Sandbox Merchant ID] および [!UICONTROL Production Merchant ID] は自動生成され、サンドボックスや実稼動のオンボーディングが完了すると、該当するフィールドに存在します。 これらの ID を削除または変更しないでください。

1. クリック **[!UICONTROL Save Config]** 変更を保存します。

### 設定オプション

| フィールド | 範囲 | 説明 |
|---|---|---|
| [!UICONTROL Enable] | web サイト | 有効または無効 [!DNL Payment Services] を設定します。 オプション： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Method] | ストア表示 | ストアのメソッドまたは環境を設定します。 オプション： [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | ストア表示 | サンドボックスマーチャント ID。サンドボックスのオンボーディング中に自動生成されます。 この ID を変更または変更しないでください。 |
| [!UICONTROL Production Merchant ID] | ストア表示 | サンドボックスのオンボーディング中に自動生成される、実稼動マーチャント ID。 この ID を変更または変更しないでください。 |

## [!UICONTROL Credit Card Fields]

この [!UICONTROL Credit Card Fields] 支払いオプションは、クレジットカードまたはデビットカードの支払い方法のためのシンプルでセキュアなチェックアウトを提供します。

詳しくは、 [支払いオプション](payments-options.md#paypal-smart-buttons) を参照してください。

### クレジットカードフィールドの構成

1. の _管理者_ サイドバー、移動 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 左側のパネルで、を展開します。 **[!UICONTROL Sales]** を選択します。 **[!UICONTROL Payment Methods]**.
1. を展開します。 _[!UICONTROL Recommended Solutions]_」セクションに入力します。
1. 内 _[!UICONTROL Payment Services]_セクションで、_[!UICONTROL Credit Card Fields]_ 」セクションに入力します。
1. の場合 **[!UICONTROL Title]**、（必要に応じて）テキストを入力して、チェックアウト時に表示される支払い方法の名前を変更します。
1. 宛先 [支払い処理を設定](production.md#set-payment-services-as-payment-method)を選択します。 **[!UICONTROL Authorize]** または **許可してキャプチャ**.
1. の場合 **デバッグモード**&#x200B;選択 `Yes` デバッグモードを有効にする ( または `No` 無効にする )。
1. クリック **[!UICONTROL Save Config]** 変更を保存します。

#### 設定オプション

| フィールド | 範囲 | 説明 |
|---|---|---|
| [!UICONTROL Title] | ストア表示 | チェックアウト時に「支払い方法」ビューで、この支払いオプションのタイトルとして表示するテキストを追加します。 オプション： [!UICONTROL text field] |
| [!UICONTROL Payment Action] | web サイト | この [支払手続](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;} （指定した支払い方法） オプション： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | web サイト | デバッグモードを有効または無効にします。 オプション： [!UICONTROL Yes] / [!UICONTROL No] |

## [!DNL PayPal Smart Buttons]

この [!DNL PayPal Smart Buttons] 支払いオプションは、お客様に対して、シンプルで迅速かつ安全なチェックアウトプロセスを提供します。

詳しくは、 [支払いオプション](payments-options.md#paypal-smart-buttons) を参照してください。

### 設定 [!DNL PayPal Smart Buttons]

PayPal スマートボタンの支払いオプションは、Admin 内で有効にして設定できます。

1. の _管理者_ サイドバー、移動 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 左側のパネルで、を展開します。 **[!UICONTROL Sales]** を選択します。 **[!UICONTROL Payment Methods]**.
1. を展開します。 _[!UICONTROL Recommended Solutions]_」セクションに入力します。
1. 内 _[!UICONTROL Payment Services]_セクションで、_[!UICONTROL PayPal Smart Buttons]_ 」セクションに入力します。
1. チェックアウト時に表示される支払い方法の名前を変更するには、 _[!UICONTROL Title]_フィールドに入力します。
1. 宛先 [支払い処理を設定](production.md#set-payment-services-as-payment-method)を選択します。 **[!UICONTROL Authorize]** または **[!UICONTROL Authorize and Capture]**.
1. を無効にするには、以下を実行します。 [後で支払うメッセージ](payments-options.md#pay-later-button) （必要に応じて）、 `No` 対象 **[!UICONTROL Display Pay Later Message]**.
1. デバッグモードを有効にするには、 `Yes` の **[!UICONTROL Debug Mode]** (`No` 無効にします )。
1. 変更を保存するには、 **[!UICONTROL Save Config]** .

### 設定オプション

| フィールド | 範囲 | 説明 |
|---|---|---|
| [!UICONTROL Title] | ストア表示 | チェックアウト時に「支払い方法」ビューで、この支払いオプションのタイトルとして表示するテキストを追加します。 オプション：テキストフィールド |
| [!UICONTROL Payment Action] | web サイト | この [支払手続](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;} （指定した支払い方法） オプション： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Display Pay Later Message] | web サイト | 買い物かご、製品ページ、ミニ買い物かごおよびチェックアウトフローの「後で支払う」メッセージを有効または無効にします。 オプション： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Venmo Enabled] | ストア表示 | 支払いボタンが表示されるベンモ支払いオプションを有効または無効にします。 オプション： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL PayPal Pay Later Enabled] | ストア表示 | 支払いボタンが表示される後払いオプションの外観を有効または無効にします。 オプション： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | web サイト | デバッグモードを有効または無効にします。 オプション： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons on product detail page] | ストア表示 | 有効または無効 [!DNL PayPal Smart Buttons] 製品の詳細ページに表示されます。 オプション： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons in mini cart preview] | ストア表示 | 有効または無効 [!DNL PayPal Smart Buttons] ミニカートのプレビューで オプション： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons on cart page] | ストア表示 | 有効または無効 [!DNL PayPal Smart Buttons] を買い物かごページに追加します。 オプション： [!UICONTROL Yes] / [!UICONTROL No] |

### [!DNL PayPal Smart Buttons] スタイル設定オプション

| フィールド | [範囲]({% link configuration/scope.md %}) | 説明 |
|--- |--- |--- |
| [!UICONTROL Layout] | ストア表示 | Paypal スマートボタンのレイアウトのスタイルを定義します。 オプション： [!UICONTROL Vertical] / [!UICONTROL Horizontal] |
| [!UICONTROL Color] | ストア表示 | Paypal スマートボタンの色を定義します。 オプション： [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black] |
| [!UICONTROL Shape] | ストア表示 | Paypal スマートボタンの形状を定義します。 オプション： [!UICONTROL Rectangular] / [!UICONTROL Pill] |
| [!UICONTROL Use Default Height] | ストア表示 | PayPal スマートボタンがデフォルトの高さを使用するかどうかを定義します。 オプション： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Height] | ストア表示 | PayPal のスマートボタンの高さを定義します。 デフォルト値：なし |
| [!UICONTROL Label] | ストア表示 | PayPal のスマートボタンに表示されるラベルを定義します。 オプション： [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment] |
| [!UICONTROL Tagline] | ストア表示 | タグラインを有効にします。 オプション： [!UICONTROL Yes] / [!UICONTROL No] |
