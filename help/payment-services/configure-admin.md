---
title: レガシー支払いサービスの構成
description: インストール後に、 [!DNL Payment Services] ストア設定の「管理者」に表示されます。
role: Admin, User
level: Intermediate
exl-id: e1a3269d-bdf9-4b0f-972f-e8a0ef469503
feature: Payments, Checkout, Configuration
source-git-commit: 0dc370409ace6ac6b0a56511cd0071cf525620f1
workflow-type: tm+mt
source-wordcount: '1652'
ht-degree: 0%

---

# レガシー [!DNL Payment Services] 設定

カスタマイズ可能 [!DNL Payment Services] を必要に応じて管理者の設定オプションを使用できます。

設定時に [!DNL Payment Services] 対象： [!DNL Adobe Commerce] および [!DNL Magento Open Source] 管理では、これらの設定は、 _[!UICONTROL Method]_～の分野_[!UICONTROL General Configuration]_. 設定フィールドで行った変更は、 _[!UICONTROL Method]_「選択」(selection) — メソッドを切り替えても、選択はリセットされません。

## 一般設定

次を有効にすることができます。 [!DNL Payment Services] お客様のストアと  _[!UICONTROL Merchant Location]_を有効にし、でサンドボックステストまたはライブ支払いを有効にします。_[!UICONTROL General Configuration]_ 」セクションに入力します。

1. 次の日： _管理者_ サイドバー、移動 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 左側のパネルで、を展開します。 **[!UICONTROL Sales]** を選択します。 **[!UICONTROL Payment Methods]**.

   ![メソッドビュー](assets/methods-view.png){width="400" zoomable="yes"}

1. を設定します。 _[!UICONTROL Merchant Country]_フィールド_[!UICONTROL Merchant Location]_.
1. を展開します。 _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_セクションで_[!UICONTROL [!DNL Payment Services]]_ 」セクションに入力します。
1. Adobe Analytics の _[!UICONTROL [!DNL Payment Services]]_セクションで、_[!UICONTROL General Configuration]_ 」セクションに入力します。
1. の場合 **有効にする**&#x200B;に設定し、 `Yes` 有効にする [!DNL Payment Services] お客様のストアの。
1. の場合 **メソッド**&#x200B;に設定し、 `Sandbox` まだテスト中の場合 [!DNL Payment Services] お客様のストアまたは `Production` ライブ支払いを有効にする準備が整っている場合。

   >[!WARNING]
   >
   >お使いの _[!UICONTROL Sandbox Merchant ID]_および_[!UICONTROL Production Merchant ID]_ は自動生成され、サンドボックスや実稼動のオンボーディングが完了すると、該当するフィールドに存在します。 これらの ID を削除または変更しないでください。

1. の場合 **ソフト記述子** （店舗/ブランド/カタログ間で区切る顧客取引銀行明細書に表示されるカスタム値）、カスタムテキスト（最大 22 文字）をテキストフィールドに追加します。 `Custom descriptor` または既存の値。
1. クリック **[!UICONTROL Save Config]** をクリックして変更を保存します。
1. に移動します。 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**&#x200B;をクリックし、 **[!UICONTROL Flush Cache]** 無効なキャッシュをすべて更新します。

![注目のAdobeソリューション表示](assets/featured-adobe-solution-view.png){width="700" zoomable="yes"}

### 設定オプション

| フィールド | 範囲 | 説明 |
|---|---|---|
| [!UICONTROL Enable] | web サイト | 有効または無効 [!DNL Payment Services] を設定します。 オプション： `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Method] | ストア表示 | ストアのメソッドまたは環境を設定します。 オプション： [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | ストア表示 | サンドボックスマーチャント ID。サンドボックスのオンボーディング中に自動生成されます。 この ID を変更または変更しないでください。 |
| [!UICONTROL Production Merchant ID] | ストア表示 | サンドボックスのオンボーディング中に自動生成される、実稼動マーチャント ID。 この ID を変更または変更しないでください。 |
| [!UICONTROL Soft Descriptor] | web サイトまたはストア表示 | ソフト記述子を Web サイトに追加し、ビューを保存して、ブランド、店舗または製品ラインを説明する顧客トランザクションに情報を追加します。 |

## [!UICONTROL Credit Card Fields]

The [!UICONTROL Credit Card Fields] 支払いオプションは、クレジットカードまたはデビットカードの支払い方法のためのシンプルでセキュアなチェックアウトを提供します。

詳しくは、 [支払いオプション](payments-options.md#paypal-smart-buttons) を参照してください。

1. 次の日： _管理者_ サイドバー、移動 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 左側のパネルで、を展開します。 **[!UICONTROL Sales]** を選択します。 **[!UICONTROL Payment Methods]**.
1. を展開します。 _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_」セクションに入力します。
1. Adobe Analytics の _[!UICONTROL Payment Services]_セクションで、_[!UICONTROL Credit Card Fields]_ 」セクションに入力します。
1. の場合 **[!UICONTROL Title]**、（必要に応じて）テキストを入力して、チェックアウト時に表示される支払い方法の名前を変更します。
1. 宛先 [支払いアクションを設定](production.md#set-payment-services-as-payment-method)を選択します。 **[!UICONTROL Authorize]** または **許可してキャプチャ**.
1. 支払い方法をチェックアウトページで優先順位付けするには、 `Numeric Only` 値を **[!UICONTROL Sort order]** フィールドに入力します。
1. の場合 **[!UICONTROL Show on checkout page]**&#x200B;を選択します。 `Yes` をクリックして、「チェックアウト」ページのクレジットカードフィールドを有効にします。
1. の場合 **[!UICONTROL Vault Enabled]**&#x200B;を選択します。 `Yes` チェックアウト用のクレジットカード保管を有効にする。
1. の場合 **[!UICONTROL Vault Enabled in Admin]**&#x200B;を選択します。 `Yes` マーチャントが、アウトに保存されたクレジットカードを使用して顧客に対する注文を作成できるようにする。
1. 有効にするには **[!UICONTROL 3DS Secure authentication]** (`Off` デフォルトでは選択 `Always` または `When required`.
1. の場合 **[!UICONTROL Debug Mode]**&#x200B;を選択します。 `Yes` デバッグモードを有効にするには、または `No` を無効にします。
1. クリック **[!UICONTROL Save Config]** をクリックして変更を保存します。
1. に移動します。 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**&#x200B;をクリックし、 **[!UICONTROL Flush Cache]** 無効なキャッシュをすべて更新します。

### 設定オプション

| フィールド | 範囲 | 説明 |
|---|---|---|
| [!UICONTROL Title] | ストア表示 | チェックアウト時に「支払い方法」ビューで、この支払いオプションのタイトルとして表示するテキストを追加します。 オプション： [!UICONTROL text field] |
| [!UICONTROL Payment Action] | web サイト | The [支払手続](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) 指定した支払い方法の オプション： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Sort order] | ストア表示 | チェックアウトページでの指定した支払い方法の並べ替え順。 `Numeric Only` 値 |
| [!UICONTROL Show on checkout page] | web サイト | 「チェックアウト」ページのクレジットカードフィールドを有効または無効にします。 オプション： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled] | ストア表示 | 有効または無効 [クレジットカードの保管](vaulting.md). オプション： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled in Admin] | ストア表示 | の機能を有効または無効にします [マーチャントが管理で顧客の注文を完了する](vaulting.md) 跳ね上げられた支払い方法を使用して オプション： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL 3DS Secure authentication] | web サイト | 有効または無効 [3DS セキュア認証](security.md#3ds). オプション： [!UICONTROL Always] / [!UICONTROL When Required] / [!UICONTROL Off] |
| [!UICONTROL Debug Mode] | web サイト | デバッグモードを有効または無効にします。 オプション： `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## [!UICONTROL Apple Pay]

The [!UICONTROL Apple Pay] 支払いオプションを使用すると、商人はApple Pay を買い物客に提供でき、この買い物客はデバイスでタッチ ID を使用して Safari ブラウザーから購入を行うことができます。 商人は 1 商人口座につき最大 99 ドメインを追加できます。

詳しくは、 [支払いオプション](payments-options.md#apple-pay-button) を参照してください。

1. 次の日： _管理者_ サイドバー、移動 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 左側のパネルで、を展開します。 **[!UICONTROL Sales]** を選択します。 **[!UICONTROL Payment Methods]**.
1. を展開します。 _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_」セクションに入力します。
1. Adobe Analytics の _[!UICONTROL Payment Services]_セクションで、_[!UICONTROL Apple Pay]_ 」セクションに入力します。
1. の場合 **[!UICONTROL Title]**、（必要に応じて）テキストを入力して、チェックアウト時に表示される支払い方法の名前を変更します。
1. 宛先 [支払いアクションを設定](production.md#set-payment-services-as-payment-method)を選択します。 **[!UICONTROL Authorize]** または **[!UICONTROL Authorize and Capture]**.
1. ここで [!DNL Apple Pay] オプションは、「 Adobe Commerce 」で「 `Yes` 必要に応じて、次のオプションを選択します。
   * **[!UICONTROL Show Apple Pay on checkout page]**
   * **[!UICONTROL Show Apple Pay on product detail page]**
   * **[!UICONTROL Show Apple Pay in mini cart preview]**
   * **[!UICONTROL Show Apple Pay on cart page]**
1. デバッグモードを有効にするには、「 」を選択します。 `Yes` （の） **[!UICONTROL Debug Mode]** (`No` を無効にします )。
1. 変更を保存するには、 **[!UICONTROL Save Config]** .
1. に移動します。 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**&#x200B;をクリックし、 **[!UICONTROL Flush Cache]** 無効なキャッシュをすべて更新します。

### 設定オプション

| フィールド | 範囲 | 説明 |
|---|---|---|
| [!UICONTROL Title] | ストア表示 | チェックアウト時に「支払い方法」ビューで、この支払いオプションのタイトルとして表示するテキストを追加します。 オプション： [!UICONTROL text field] |
| [!UICONTROL Payment Action] | web サイト | The [支払手続](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) 指定した支払い方法の オプション： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show on checkout page] | web サイト | 有効または無効 [!DNL Apple Pay] を「チェックアウト」ページに追加します。 オプション： `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Sort order] | ストア表示 | チェックアウトページでの指定した支払い方法の並べ替え順です。 `Numeric Only` 値 |
| [!UICONTROL Show buttons on product detail page] | ストア表示 | 有効または無効 [!DNL Apple Pay] 製品の詳細ページに表示されます。 オプション： `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons in mini-cart preview] | ストア表示 | 有効または無効 [!DNL Apple Pay] をクリックします。 オプション： `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on cart page] | ストア表示 | 有効または無効 [!DNL Apple Pay] を買い物かごページに追加します。 オプション： `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Debug Mode] | web サイト | デバッグモードを有効または無効にします。 オプション： `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## [!UICONTROL Google Pay]

The [!UICONTROL Google Pay] 支払いオプションを使用すると、商人はGoogle Pay を買い物客に提供でき、購入者はデバイスでGoogle Wallet を使用して購入を行うことができます。

詳しくは、 [支払いオプション](payments-options.md#google-pay-button) を参照してください。

1. 次の日： _管理者_ サイドバー、移動 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 左側のパネルで、を展開します。 **[!UICONTROL Sales]** を選択します。 **[!UICONTROL Payment Methods]**.
1. を展開します。 _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_」セクションに入力します。
1. Adobe Analytics の _[!UICONTROL Payment Services]_セクションで、_[!UICONTROL Google Pay]_ 」セクションに入力します。
1. （オプション）チェックアウト時に表示される支払い方法の名前を、 **[!UICONTROL Title]** フィールドに入力します。
1. [支払い処理を設定](production.md#set-payment-services-as-payment-method) 選択する **[!UICONTROL Authorize]** または **[!UICONTROL Authorize and Capture]**.
1. ここで [!DNL Google Pay] オプションは、「 Adobe Commerce 」で「 `Yes` 必要に応じて、次のオプションを選択します。
   * **[!UICONTROL Show Google Pay on checkout page]**
   * **[!UICONTROL Show Google Pay on product detail page]**
   * **[!UICONTROL Show Google Pay in mini cart preview]**
   * **[!UICONTROL Show Google Pay on cart page]**
1. デバッグモードを有効にするには、「 」を選択します。 `Yes` （の） **[!UICONTROL Debug Mode]** (`No` を無効にします )。
1. の外観の設定 _[!UICONTROL Google Pay]_ボタンをクリックし、**[!UICONTROL Button Color]**,**[!UICONTROL Button Type]**、および&#x200B;**[!UICONTROL Button Style]**必要に応じて。
1. 高さを設定するには、で定義されている高さの既定値を使用します。 **[!UICONTROL Button Style]**.
1. 変更を保存するには、 **[!UICONTROL Save Config]** .
1. に移動します。 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**&#x200B;をクリックし、 **[!UICONTROL Flush Cache]** 無効なキャッシュをすべて更新します。

### 設定オプション

| フィールド | 範囲 | 説明 |
|---|---|---|
| [!UICONTROL Title] | ストア表示 | チェックアウト時に [ 支払い方法 ] ビューでこの支払いオプションに対して表示するテキストラベルを指定します。 オプション： `[!UICONTROL text field]` |
| [!UICONTROL Payment Action] | web サイト | The [支払手続](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) 指定した支払い方法の オプション： `[!UICONTROL Authorize]` / `[!UICONTROL Authorize and Capture]` |
| [!UICONTROL Show on checkout page] | web サイト | 有効または無効 [!DNL Google Pay] を「チェックアウト」ページに追加します。 オプション： `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Sort order] | ストア表示 | チェックアウトページでの指定した支払い方法の並べ替え順です。 `Numeric Only` 値 |
| [!UICONTROL Show buttons on product detail page] | ストア表示 | 有効または無効 [!DNL Google Pay] 製品の詳細ページに表示されます。 オプション： `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons in mini-cart preview] | ストア表示 | 有効または無効 [!DNL Google Pay] をクリックします。 オプション： `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on cart page] | ストア表示 | 有効または無効 [!DNL Google Pay] を買い物かごページに追加します。 オプション： `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Debug Mode] | web サイト | デバッグモードを有効または無効にします。 オプション： `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Button Color] | ストア表示 | 色の定義 [!DNL Google Pay] 」ボタンをクリックします。 オプション： `[!UICONTROL Default]` / `[!UICONTROL Black]` / `[!UICONTROL White]` |
| [!UICONTROL Button Type] | ストア表示 | タイプを定義 [!DNL Google Pay] 」ボタンをクリックします。 オプション： `[!UICONTROL buy]` / `[!UICONTROL checkout]` / `[!UICONTROL order]` / `[!UICONTROL pay]` / `[!UICONTROL plain]` |

詳しくは、 [Google Pay API リクエストオブジェクトオプション](https://developers.google.com/pay/api/web/reference/request-objects) ドキュメントを参照してください。

## [!DNL PayPal Payment Buttons]

The [!DNL PayPal payment buttons] 支払いオプションは、お客様に対して、シンプルで迅速かつ安全なチェックアウトプロセスを提供します。

詳しくは、 [支払いオプション](payments-options.md#paypal-smart-buttons) を参照してください。

設定 [!DNL PayPal payment buttons]

Admin 内で PayPal の支払いボタンの支払いオプションを有効にして設定できます。

1. 次の日： _管理者_ サイドバー、移動 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 左側のパネルで、を展開します。 **[!UICONTROL Sales]** を選択します。 **[!UICONTROL Payment Methods]**.
1. を展開します。 _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_」セクションに入力します。
1. Adobe Analytics の _[!UICONTROL Payment Services]_セクションで、_[!UICONTROL PayPal payment buttons]_ 」セクションに入力します。
1. チェックアウト時に表示される支払い方法の名前を変更するには、 _[!UICONTROL Title]_フィールドに入力します。
1. 宛先 [支払いアクションを設定](production.md#set-payment-services-as-payment-method)を選択します。 **[!UICONTROL Authorize]** または **[!UICONTROL Authorize and Capture]**.
1. 支払い方法をチェックアウトページで優先順位付けするには、 `Numeric Only` 値を **[!UICONTROL Sort order]** フィールドに入力します。
1. を有効/無効にするには [後で支払うメッセージ](payments-options.md#pay-later-button)を選択します。 `Yes`/`No` 対象： **[!UICONTROL Display Pay Later Message]**.
1. Adobe Commerceで PayPal の支払いボタンを有効にする場所を、 `Yes` 必要に応じて、次のオプションを選択します。
   * **[!UICONTROL Show buttons on checkout page]**
   * **[!UICONTROL Show buttons on product detail page]**
   * **[!UICONTROL Show buttons in mini cart preview]**
   * **[!UICONTROL Show buttons on cart page]**
1. 支払いオプションとして Venmo を有効にするには、 `Yes` 対象： **[!UICONTROL Venmo Enabled]**.
1. クレジットカードとデビットカードを支払いオプションとして有効にするには（PayPal のスマートボタン）、 `Yes` 対象： **[!UICONTROL Credit and Debit Card Enabled]**.
1. を有効/無効にするには [PayPal 後払い](payments-options.md#pay-later-button) 支払いオプション、選択 `Yes`/`No` 対象： **[!UICONTROL PayPal Pay Later Enabled]**.
1. デバッグモードを有効にするには、「 」を選択します。 `Yes` （の） **[!UICONTROL Debug Mode]** (`No` を無効にします )。
1. 変更を保存するには、 **[!UICONTROL Save Config]** .
1. に移動します。 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**&#x200B;をクリックし、 **[!UICONTROL Flush Cache]** 無効なキャッシュをすべて更新します。

### 設定オプション

| フィールド | 範囲 | 説明 |
|---|---|---|
| [!UICONTROL Title] | ストア表示 | チェックアウト時に「支払い方法」ビューで、この支払いオプションのタイトルとして表示するテキストを追加します。 オプション：テキストフィールド |
| [!UICONTROL Payment Action] | web サイト | The [支払手続](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} 指定した支払い方法の オプション： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Display Pay Later Message] | web サイト | 買い物かご、製品ページ、ミニ買い物かごおよびチェックアウトフローの「後で支払う」メッセージを有効または無効にします。 オプション： `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on checkout page] | ストア表示 | 有効または無効 [!DNL PayPal payment buttons] を「チェックアウト」ページに追加します。 オプション： `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on product detail page] | ストア表示 | 有効または無効 [!DNL PayPal payment buttons] 製品の詳細ページに表示されます。 オプション： `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons in mini-cart preview] | ストア表示 | 有効または無効 [!DNL PayPal payment buttons] をクリックします。 オプション： `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on cart page] | ストア表示 | 有効または無効 [!DNL PayPal payment buttons] を買い物かごページに追加します。 オプション： `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Venmo Enabled] | ストア表示 | 支払いボタンが表示される Venmo 支払いオプションを有効または無効にします。 オプション： `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Credit and Debit Card Enabled] | ストア表示 | 支払いボタンが表示されるクレジットカードおよびデビットカードのオプションを有効または無効にします。 オプション： `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL PayPal Pay Later Enabled] | ストア表示 | 支払いボタンが表示される PayPal Pay Later 支払いオプションの外観を有効または無効にします。 オプション： `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Debug Mode] | web サイト | デバッグモードを有効または無効にします。 オプション： `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## ボタンのスタイル

また、 _[!UICONTROL Button style]_支払いボタンのオプション：

1. 次の日： _管理者_ サイドバー、移動 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 左側のパネルで、を展開します。 **[!UICONTROL Sales]** を選択します。 **[!UICONTROL Payment Methods]**.
1. を展開します。 _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_」セクションに入力します。
1. Adobe Analytics の _[!UICONTROL [!DNL Payment Services]]_セクションで、_[!UICONTROL PayPal Smart Button Styling]_ 」セクションに入力します。
1. レイアウトを設定するには、「 `Vertical` または `Horizontal` 対象： **[!UICONTROL Layout]**
1. 色を設定するには、 **[!UICONTROL Color]**.
1. シェイプを設定するには、 `Rectangular` または `Pill` 対象： **[!UICONTROL Shape]**.
1. デフォルトの高さを使用するには、「 `Yes` または `No` 対象： **[!UICONTROL Use Default Height]**.
1. カスタムの高さを設定するには、 **[!UICONTROL Height]**.
1. タグラインを設定するには、「 `Yes` または `No` 対象： **[!UICONTROL Tagline]**.
1. 変更を保存するには、 **[!UICONTROL Save Config]** .
1. に移動します。 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**&#x200B;をクリックし、 **[!UICONTROL Flush Cache]** 無効なキャッシュをすべて更新します。

また、支払いボタンのスタイル設定を設定することもできます [設定内](settings.md#button-style) 支払サービスホームから。

### 設定オプション

| フィールド | 範囲 | 説明 |
|--- |--- |--- |
| [!UICONTROL Layout] | ストア表示 | Paypal の支払いボタンのレイアウトのスタイルを定義します。 オプション： `[!UICONTROL Vertical]` / `[!UICONTROL Horizontal]` |
| [!UICONTROL Color] | ストア表示 | Paypal の支払いボタンの色を定義します。 オプション： [!UICONTROL Blue] / `[!UICONTROL Gold]` / `[!UICONTROL Silver]` / `[!UICONTROL White]` / `[!UICONTROL Black]` |
| [!UICONTROL Shape] | ストア表示 | Paypal の支払いボタンの形状を定義します。 オプション： `[!UICONTROL Rectangular]` / `[!UICONTROL Pill]` |
| [!UICONTROL Use Default Height] | ストア表示 | PayPal の支払いボタンがデフォルトの高さを使用するかどうかを定義します。 オプション： `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Height] | ストア表示 | PayPal の支払いボタンの高さを定義します。 デフォルト値：なし |
| [!UICONTROL Label] | ストア表示 | PayPal の支払いボタンに表示されるラベルを定義します。 オプション： `[!UICONTROL PayPal]` / `[!UICONTROL Checkout]` / `[!UICONTROL Buynow]` / `[!UICONTROL Pay]` / `[!UICONTROL Installment]` |
| [!UICONTROL Tagline] | ストア表示 | タグラインを有効にします。 オプション： `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## キャッシュをフラッシュ

設定を変更した場合、 [キャッシュを手動でフラッシュする](/help/payment-services/settings.md#flush-the-cache) ストアに最新の設定が表示されるようにします。
