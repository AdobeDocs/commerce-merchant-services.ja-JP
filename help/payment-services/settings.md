---
title: 支払いサービス設定
description: インストール後に、 [!DNL Payment Services] 家の中で
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
feature: Payments, Checkout, Configuration
source-git-commit: 8dd4f629fa60959588cee4ea22f9fb577f338716
workflow-type: tm+mt
source-wordcount: '2372'
ht-degree: 0%

---

# 設定

カスタマイズ可能 [!DNL Payment Services] の設定が役に立ちます。 [!DNL Payment Services] ホーム。

を設定するには、以下を実行します。 [!DNL Payment Services] 対象： [!DNL Adobe Commerce] および [!DNL Magento Open Source] click **[!UICONTROL Settings]**. これらの設定オプションは、 _[!UICONTROL Payment mode]_フィールドの[_&#x200B;一般&#x200B;_設定オプション](#configure-general-settings).

マルチストアまたはレガシー設定については、 [管理での設定](configure-admin.md).

## 一般設定の指定

The [!UICONTROL General] 設定を使用すると、支払い方法として支払いサービスを有効または無効にし、顧客トランザクションに情報を追加して、Web サイトにマークを付けたり、カスタム情報を付けて表示することができます。

### 支払いサービスの有効化

次を有効にすることができます。 [!DNL Payment Services] web サイトに対して、サンドボックステストまたはライブ支払いを有効にします。

1. 次の日： _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![ホームビュー](assets/payment-services-menu-small.png){width="400" zoomable="yes"}

1. クリック **[!UICONTROL Settings]**. 詳しくは、 [の概要 [!DNL Payment Services] ホーム](payments-home.md) を参照してください。

   The _[!UICONTROL General]_セクションには、を有効にするための設定が含まれています [!DNL Payment Services] を支払い方法として使用します。

1. 有効にするには [!DNL Payment Services] お客様の店舗の支払い方法として、 _[!UICONTROL General]_セクション、切り替え&#x200B;**[!UICONTROL Enable Payment Services as payment method]**から `Yes`.

1. まだテストを行っている場合 [!DNL Payment Services] お客様のストアに対して、 **支払いモード** から `Sandbox`. ライブ支払いを有効にする準備が整ったら、次のように設定します。 `Production`.

   >[!NOTE]
   >
   >お使いの _[!UICONTROL Sandbox Merchant ID]_および_[!UICONTROL Production Merchant ID]_ は自動生成され、サンドボックスや実稼動のオンボーディングを完了すると、該当するフィールドに存在します。

1. クリック **[!UICONTROL Save]**.

   変更を保存せずにこのビューから移動しようとすると、モーダルが表示され、変更の破棄、編集の続行、変更の保存を求めるプロンプトが表示されます。

1. に移動します。 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** をクリックします。 **[!UICONTROL Flush Cache]** 無効なキャッシュをすべて更新します。

次に、のデフォルト設定の変更に進むことができます： [支払いオプション](#configure-payment-options) 関数とストアフロントディスプレイ。

### ソフト記述子を追加

次の項目を追加できます： [!UICONTROL Soft Descriptor] を web サイトまたは個々のストア表示設定に追加します。 顧客トランザクション銀行明細書にソフト記述子が表示されます。 例えば、複数の店舗/ブランド/カタログがある場合、 [!UICONTROL Soft Descriptor] フィールドに入力します。

1. 次の日： _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. クリック **[!UICONTROL Settings]**. 詳しくは、 [の概要 [!DNL Payment Services] ホーム](payments-home.md) を参照してください。
1. Web サイトまたはストア表示を、 **[!UICONTROL Scope]** ソフト記述子を作成するドロップダウンメニュー。 初期設定の場合、これはのままにします。 **[!UICONTROL Default]** をクリックしてデフォルト値を設定します。
1. テキストフィールドにカスタムテキスト（最大 22 文字）を追加し、 `Custom descriptor`.
1. クリック **[!UICONTROL Save]**.
1. Web サイトまたはストア表示に設定されたデフォルト以外のソフト記述子を作成するには、次の手順を実行します。
   1. Web サイトまたはストア表示を、 **[!UICONTROL Scope]** ソフト記述子を作成するドロップダウンメニュー。
   1. 切り替え _オフ_ **[!UICONTROL Use website]** ( または **[!UICONTROL Use default]**（選択した範囲に応じて異なります）。
   1. テキストフィールドにカスタムテキストを追加します。
   1. クリック **[!UICONTROL Save]**.
1. Web サイトまたはストアに対して有効にするには、デフォルトのソフト記述子を表示します _または_ 親 web サイトに使用されるソフト記述子：
   1. Web サイトまたはストア表示を、 **[!UICONTROL Scope]** 既存のソフト記述子を有効にするドロップダウンメニュー。
   1. 切り替え _オン_ **[!UICONTROL Use website]** ( または **[!UICONTROL Use default]**（選択した範囲に応じて）。
   1. クリック **[!UICONTROL Save]**.

   変更を保存せずにこのビューから移動しようとすると、モーダルが表示され、変更の破棄、編集の続行、変更の保存を求めるプロンプトが表示されます。

### 設定オプション

| フィールド | 範囲 | 説明 |
|---|---|---|
| [!UICONTROL Enable] | web サイト | 有効または無効 [!DNL Payment Services] を設定します。 オプション： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Payment mode] | ストア表示 | ストアのメソッドまたは環境を設定します。 オプション： [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | ストア表示 | サンドボックスマーチャント ID。サンドボックスのオンボーディング中に自動生成されます。 |
| [!UICONTROL Production Merchant ID] | ストア表示 | サンドボックスのオンボーディング中に自動生成される、実稼動マーチャント ID。 |
| [!UICONTROL Soft Descriptor] | web サイトまたはストア表示 | ソフト記述子を Web サイトに追加し、ビューを保存して、ブランド、店舗または製品ラインを説明する顧客トランザクションに情報を追加します。 The [!UICONTROL Use website] toggle は、web サイトレベルに追加されたソフト記述子を適用します。 The [!UICONTROL Use default] toggle は、デフォルトとして追加されたソフト記述子を適用します。 |

## 支払いオプションを設定

これで、を有効にしました。 [!UICONTROL Payment Services] web サイトでは、支払い機能とストアフロント表示のデフォルト設定を変更できます。

1. 次の日： _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. クリック **[!UICONTROL Settings]**. 詳しくは、 [の概要 [!DNL Payment Services] ホーム](payments-home.md) を参照してください。
1. 支払いオプションを設定 [クレジットカード](#credit-card-fields), [支払ボタン](#payment-buttons)、および [ボタンのスタイル](#button-style)、以降のセクションに従って。

### クレジットカードのフィールド

The _[!UICONTROL Credit Card Fields]_設定は、クレジットカードまたはデビットカードの支払い方法のためのシンプルでセキュアなチェックアウトオプションを提供します。

詳しくは、 [支払いオプション](payments-options.md#credit-card-fields) を参照してください。

1. 次の日： _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. ストア表示を選択します ( **[!UICONTROL Scope]** 支払い方法を有効にするドロップダウンメニュー。
1. Adobe Analytics の **[!UICONTROL Credit card fields]** セクションで、 **[!UICONTROL Checkout title]** 「 」フィールドを使用して、チェックアウト時に表示される支払い方法の名前を変更します。
1. 宛先 [支払いアクションを設定](production.md#set-payment-services-as-payment-method)，トグル **[!UICONTROL Payment action]** から `Authorize` または `Authorize and Capture`.
1. 支払い方法をチェックアウトページで優先順位付けするには、 `Numeric Only` 値を **[!UICONTROL Sort order]** フィールドに入力します。
1. 有効にするには [3DS セキュア認証](security.md#3ds) (`Off` （デフォルト）切り替え **[!UICONTROL 3DS Secure authentication]** セレクター `Always` または `When required`.
1. チェックアウトページのクレジットカードフィールドを有効または無効にするには、 **[!UICONTROL Show on checkout page]** セレクター。
1. 有効または無効にするには [カード保管](#card-vaulting)、切り替え **[!UICONTROL Vault enabled]** セレクター。
1. 有効または無効にするには [管理者の管理者の支払い方法](#card-vaulting) （管理者が管理者に対し、管理者が自分の vault の支払い方法で顧客の注文を完了するために）、 **[!UICONTROL Show vaulted methods in Admin]** セレクター。
1. デバッグモードを有効または無効にするには、 **[!UICONTROL Debug Mode]** セレクター。
1. クリック **[!UICONTROL Save]**.

   変更を保存せずにこのビューから移動しようとすると、モーダルが表示され、変更の破棄、編集の続行、変更の保存を求めるプロンプトが表示されます。

1. [キャッシュをフラッシュ](#flush-the-cache).

#### 設定オプション

| フィールド | 範囲 | 説明 |
|---|---|---|
| [!UICONTROL Title] | ストア表示 | チェックアウト時に「支払い方法」ビューで、この支払いオプションのタイトルとして表示するテキストを追加します。 オプション： [!UICONTROL text field] |
| [!UICONTROL Payment Action] | web サイト | The [支払手続](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} 指定した支払い方法の オプション： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Sort order] | ストア表示 | チェックアウトページでの指定した支払い方法の並べ替え順。 `Numeric Only` 値 |
| [!UICONTROL 3DS Secure authentication] | web サイト | 有効または無効 [3DS セキュア認証](security.md#3ds). オプション： [!UICONTROL Always] / [!UICONTROL When Required] / [!UICONTROL Off] |
| [!UICONTROL Show on checkout page] | web サイト | チェックアウトページに表示するクレジットカードフィールドを有効または無効にします。 オプション： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Vault enabled] | ストア表示 | 有効または無効 [クレジットカードの保管](vaulting.md). オプション： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show vaulted payment methods in Admin] | ストア表示 | 管理でマーチャントが顧客の注文を完了する機能を有効または無効にします [跳ね上げ式の支払い方法を使用する](vaulting.md). オプション： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Debug Mode] | web サイト | デバッグモードを有効または無効にします。 オプション： [!UICONTROL Off] / [!UICONTROL On] |

### Apple Pay

The [!UICONTROL Apple Pay] ボタンの支払いオプションを使用すると、 [!UICONTROL Apple Pay] Safari ブラウザーからのストアのチェックアウト時の支払いボタン（マーチャントアカウントあたり最大 99 ドメイン）。

Apple Pay は、 [Appleは Paypal を通じて自己登録を支払う](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) その後 [Apple Pay の設定](settings.md/#payment-buttons) お客様の店舗用に。 詳しくは、 [支払いオプション](payments-options.md#apple-pay-button) を参照してください。

を有効にして、 [!UICONTROL Apple Pay] ボタンの支払いオプション：

1. 次の日： _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. ストア表示を選択します ( **[!UICONTROL Scope]** 支払い方法を有効にするドロップダウンメニュー。
1. Adobe Analytics の **[!UICONTROL Apple Pay]** セクションで、 _[!UICONTROL Checkout title]_「 」フィールドを使用して、チェックアウト時に表示される支払い方法の名前を変更します。
1. 宛先 [支払いアクションを設定](production.md#set-payment-services-as-payment-method)，トグル **[!UICONTROL Payment action]** から `Authorize` または `Authorize and Capture`.
1. チェックアウトページでApple Pay を有効または無効にするには、 **[!UICONTROL Show Apple Pay on checkout page]** セレクター。
1. 製品の詳細ページでApple Pay を有効または無効にするには、 **[!UICONTROL Show Apple Pay on product detail page]** セレクター。
1. ミニ買い物かごのプレビューでApple Pay を有効または無効にするには、 **[!UICONTROL Show Apple Pay on the mini cart preview]** セレクター。
1. 買い物かごページでのApple Pay の有効/無効を切り替えるには、 **[!UICONTROL Show Apple Pay on cart page]** セレクター。
1. デバッグモードを有効または無効にするには、 **[!UICONTROL Debug Mode]** セレクター。
1. クリック **[!UICONTROL Save]**.

   変更を保存せずにこのビューから移動しようとすると、モーダルが表示され、変更の破棄、編集の続行、変更の保存を求めるプロンプトが表示されます。

1. [キャッシュをフラッシュ](#flush-the-cache).

#### 設定オプション

| フィールド | 範囲 | 説明 |
|---|---|---|
| [!UICONTROL Checkout title] | ストア表示 | チェックアウト時に「支払い方法」ビューで、この支払いオプションのタイトルとして表示するテキストを追加します。 オプション： [!UICONTROL text field] |
| [!UICONTROL Payment Action] | web サイト | The [支払手続](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions) 指定した支払い方法の オプション： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show on checkout page] | web サイト | 「Apple Pay」ボタンを有効または無効にして、チェックアウトページに表示します。 オプション： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show on checkout page] | web サイト | 製品の詳細ページに表示する「 Apple Pay 」ボタンを有効または無効にします。 オプション： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show on mini cart preview] | web サイト | 「Apple支払い」ボタンを有効または無効にして、ミニ買い物かごのプレビューに表示します。 オプション： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show on cart page] | web サイト | 「Apple支払い」ボタンを有効または無効にして、買い物かごページに表示します。 オプション： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Debug Mode] | web サイト | デバッグモードを有効または無効にします。 オプション： [!UICONTROL Off] / [!UICONTROL On] |

### 支払いボタン

The [!DNL PayPal payment buttons] 支払いオプションは、お客様に対して、シンプルで迅速かつ安全なチェックアウトプロセスを提供します。 詳しくは、 [支払いオプション](payments-options.md#paypal-smart-buttons) を参照してください。

PayPal の支払いボタンの支払いオプションを有効にして設定できます。

1. ストア表示を選択します ( **[!UICONTROL Scope]** 支払い方法を有効にするドロップダウンメニュー。
1. チェックアウト時に表示される支払い方法の名前を変更するには、 **[!UICONTROL Checkout Title]** フィールドに入力します。
1. 宛先 [支払いアクションを設定](production.md#set-payment-services-as-payment-method)，トグル **[!UICONTROL Payment action]** から `Authorize` または `Authorize and Capture`.
1. 支払い方法をチェックアウトページで優先順位付けするには、 `Numeric Only` 値を **[!UICONTROL Sort order]** フィールドに入力します。
1. 切り替えセレクターを使用して、有効または無効にします [!DNL PayPal smart button] 表示機能：

   - **[!UICONTROL Show PayPal buttons on product checkout page]**
   - **[!UICONTROL Show PayPal buttons on product detail page]**
   - **[!UICONTROL Show PayPal buttons in mini-cart preview]**
   - **[!UICONTROL Show PayPal buttons on cart page]**
   - **[!UICONTROL Show PayPal Pay Later button]**
   - **[!UICONTROL Show PayPal Pay Later message]**
   - **[!UICONTROL Show Venmo button]**
   - **[!UICONTROL Show Apple Pay button]**
   - **[!UICONTROL Show PayPal Credit and Debit Card button]**

     >[!NOTE]
     >
     > Apple Pay を使用するには [は、Apple Sandbox テスターアカウントを持っている必要があります](https://developer.apple.com/apple-pay/sandbox-testing/#create-a-sandbox-tester-account) （偽のクレジットカードと請求情報を含む）をテストします。 サンドボックスでApple Pay を使用する準備が整ったら、 _または_ 実稼動モード（任意の完了後） [テストと検証](test-validate.md#test-in-sandbox-environment), complete [～との自己登録 [!DNL Apple Pay]](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) (_ライブドメインを登録_ セクションのみ ) および [次のストアに対して設定します。 [!DNL Payment Services]](settings.md#payment-buttons).

     支払いボタンや PayPal Pay Later メッセージの表示/非表示を切り替えると、設定ページの下部にその設定の視覚的なプレビューが表示されます。

1. デバッグモードを有効にするには、 **[!UICONTROL Debug Mode]** セレクター。
1. クリック **[!UICONTROL Save]**.

   変更を保存せずにこのビューから移動しようとすると、モーダルが表示され、変更の破棄、編集の続行、変更の保存を求めるプロンプトが表示されます。

1. [キャッシュをフラッシュ](#flush-the-cache).

#### 設定オプション

| フィールド | 範囲 | 説明 |
|---|---|---|
| [!UICONTROL Title] | ストア表示 | チェックアウト時に「支払い方法」ビューで、この支払いオプションのタイトルとして表示するテキストを追加します。 オプション：テキストフィールド |
| [!UICONTROL Payment Action] | web サイト | The [支払手続](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} 指定した支払い方法の オプション： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Sort order] | ストア表示 | チェックアウトページでの指定した支払い方法の並べ替え順。 `Numeric Only` 値 |
| [!UICONTROL Show PayPal buttons on checkout page] | ストア表示 | 有効または無効 [!DNL PayPal payment buttons] を「チェックアウト」ページに追加します。 オプション： [!UICONTROL  Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons on product detail page] | ストア表示 | 有効または無効 [!DNL PayPal payment buttons] 製品の詳細ページに表示されます。 オプション： [!UICONTROL  Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons in mini-cart preview] | ストア表示 | 有効または無効 [!DNL PayPal payment buttons] をクリックします。 オプション： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show PayPal buttons on cart page] | ストア表示 | 有効または無効 [!DNL PayPal payment buttons] を買い物かごページに追加します。 オプション： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show PayPal Pay Later button] | ストア表示 | 支払いボタンが表示される後払いオプションの外観を有効または無効にします。 オプション： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show PayPal Pay Later Message] | web サイト | 買い物かご、製品ページ、ミニ買い物かごおよびチェックアウトフローの「後で支払う」メッセージを有効または無効にします。 オプション： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show Venmo button] | ストア表示 | 支払いボタンが表示される Venmo 支払いオプションを有効または無効にします。 オプション： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show Apple Pay button] | ストア表示 | 支払いボタンが表示される「Apple支払」支払いオプションを有効または無効にします。 オプション： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show PayPal Credit and Debit card button] | ストア表示 | 支払いボタンが表示される「クレジット」および「デビット」カードの支払いオプションを有効または無効にします。 オプション： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Debug Mode] | web サイト | デバッグモードを有効または無効にします。 オプション： [!UICONTROL Off] / [!UICONTROL On] |

### ボタンのスタイル

また、 _[!UICONTROL Button style]_支払いボタンのオプション：

1. 次の手順で **[!UICONTROL Layout]**&#x200B;を選択します。 `Vertical` または `Horizontal`.

   >[!NOTE]
   >
   > ボタンのスタイルが `Horizontal` お客様のストアが複数の支払いボタンを表示するように設定されている場合、製品ページ、チェックアウトページ、ミニカートに 2 つのボタンと、カートに 1 つのボタンのみが表示されます。

1. 横置きレイアウトでタグラインを有効にするには、 **[!UICONTROL Show tagline]** セレクター。
1. 次の手順で **[!UICONTROL Color]**」で、目的のカラーオプションを選択します。
1. 次の手順で **[!UICONTROL Shape]**&#x200B;を選択します。 `Pill` または `Rectangle`.
1. ボタンの高さセレクターを有効にするには、 **[!UICONTROL Responsive button height]** セレクター。
1. 次の手順で **[!UICONTROL Label]**「 」で、目的のラベルオプションを選択します。

   レイアウト、色、形状、高さ、ラベルの設定オプションを変更すると、その設定の視覚的なプレビューが設定ページの下部に表示されます。 下の画像では、 **[!UICONTROL Shape]** が _長方形_ そして **[!UICONTROL Label]** が _PayPal （推奨）_.

   ![[!DNL PayPal payment buttons] options](assets/payment-buttons.png){width="400" zoomable="yes"}

1. クリック **[!UICONTROL Save]**.

   変更を保存せずにこのビューから移動しようとすると、モーダルが表示され、変更の破棄、編集の続行、変更の保存を求めるプロンプトが表示されます。

1. [キャッシュをフラッシュ](#flush-the-cache).

支払いボタンのスタイル設定を設定できます [（管理者の従来の設定）](configure-admin.md#configure-paypal-smart-buttons) またはここに [!DNL Payment Services Home]. 詳しくは、 [PayPal のボタンスタイルガイド](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) PayPal の支払いボタンのスタイル設定の詳細については、を参照してください。

#### 設定オプション

| フィールド | 範囲 | 説明 |
|--- |--- |--- |
| [!UICONTROL Layout] | ストア表示 | 支払いボタンのレイアウトのスタイルを定義します。 オプション： [!UICONTROL Vertical] / [!UICONTROL Horizontal] |
| [!UICONTROL Tagline] | ストア表示 | タグラインを有効/無効にします。 オプション： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Color] | ストア表示 | 支払いボタンの色を定義します。 オプション： [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black] |
| [!UICONTROL Shape] | ストア表示 | 支払いボタンの形状を定義します。 オプション： [!UICONTROL Rectangular] / [!UICONTROL Pill] |
| [!UICONTROL Responsive Button Height] | ストア表示 | 支払いボタンが既定の高さを使用するかどうかを定義します。 オプション： [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Height] | ストア表示 | 支払いボタンの高さを定義します。 デフォルト値：なし |
| [!UICONTROL Label] | ストア表示 | 支払いボタンに表示されるラベルを定義します。 オプション： [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment] |

## 役割の設定

管理者ユーザーがコマース管理で注文を作成および管理できるようにするには、 [!DNL Payment Services] — ユーザーの役割に固有のリソース。

詳しくは、 [ユーザーの役割](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-user-roles.html) 役割の管理方法を参照してください。

ロールにリソースを割り当てる場合は、次の項目を選択する必要があります。

- **支払い方法[!DNL Payment Services]** — このリソースは、管理で注文を作成する際に、 [!DNL Payment Services] クレジットカードは支払い方法として利用できます。 次を選択した場合、 **アクション** 親リソースの場合は、このリソースも選択されます。
- **[!DNL Payment Services]** — このリソースには、 **ダッシュボード** および **SaaS Services プロキシ** リソース（選択する必要もあります）。 また、 [!DNL Payment Services] が _セールス_ メニュー。

  ![支払いサービスのリソース](assets/roles-payments.png){width="400" zoomable="yes"}

## キャッシュをフラッシュ

設定を _設定_&#x200B;例えば、Apple Pay、Venmo、PayPal PayLater の各ボタンを切り替える場合は、ストアに最新の設定が表示されるように、手動でキャッシュをフラッシュします。

1. 次の日： _管理者_ サイドバー、移動 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. クリック **[!UICONTROL Flush Cache]** 無効なキャッシュをすべて更新します。

キャッシュ管理テーブルのキャッシュタイプに `INVALIDATED` のステータスになっている場合は、ストアにその項目の最新の設定が表示されない可能性があります。 キャッシュをフラッシュしてストアを更新し、最新の設定を表示します。

ストアで正しい設定が表示されていることを確認するには、定期的に [キャッシュをフラッシュ](https://docs.magento.com/user-guide/system/cache-management.html).

## カードの保管

顧客が自分のアカウントにクレジットカード情報を格納（保存）して、将来の購入に使用できる機能を有効にすることができます。

また、管理でカードヴォールティングを使用して、既存顧客に対する以降の注文を完了することもできます。

でのカードの保管を有効または無効にします。 [クレジットカードフィールドの設定](#credit-card-fields).

詳しくは、 [クレジットカードの保管](vaulting.md) を参照してください。

## 3DS

3DS は、店舗での不正行為から顧客や商人を保護し、EU（欧州連合）標準への準拠を可能にします。

での 3DS の有効/無効を切り替えます。 [クレジットカードフィールドの設定](#credit-card-fields).

詳しくは、 [3DS のセキュリティ](security.md#3ds) を参照してください。

## 複数の PayPal アカウントを使用する

In [!UICONTROL Payment Services]の場合、内で複数の PayPal アカウントを使用できます **1 つ** ウェブサイトレベルのマーチャントアカウント。 例えば、複数の国 ( 異なる [通貨](https://docs.magento.com/user-guide/stores/currency.html)) またはAdobe Commerceをビジネスの一部に使用したいが、使用しない場合 _すべて_&#x200B;複数の PayPal アカウントを使用するようにマーチャントアカウントを設定することができます。

詳しくは、 [サイト、ストア、および表示範囲](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html) web サイト、ストア、ストア表示の階層に関する詳細。

セールス担当者が新しい [範囲](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) お客様のマーチャントアカウントに対して、PayPal を使用して追加サイトをオンボーディングし、設定した PayPal ボタンがサイトに表示されるようにします。 Web サイトに複数の PayPal アカウントを使用する方法については、セールス担当者にお問い合わせください。
