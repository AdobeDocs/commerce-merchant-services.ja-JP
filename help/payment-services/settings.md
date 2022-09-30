---
title: 支払いサービス設定
description: インストール後、 [!DNL Payment Services] 家に
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
source-git-commit: 785528d5940af28fa8bf6873d636b40d8e7bc05f
workflow-type: tm+mt
source-wordcount: '1594'
ht-degree: 0%

---

# 設定

カスタマイズ可能 [!DNL Payment Services] の設定が役に立ちます。 [!DNL Payment Services] ホーム。

を設定するには、以下を実行します。 [!DNL Payment Services] 対象 [!DNL Adobe Commerce] および [!DNL Magento Open Source] クリック **[!UICONTROL Settings]**. これらの設定オプションは、 _[!UICONTROL Payment mode]_～に入る_[!UICONTROL Settings]_ > _[!UICONTROL General]_.

>[!IMPORTANT]
>
> マルチストアまたはレガシー設定については、 [管理での設定](configure-admin.md) トピック。

## 一般設定の指定

この [!UICONTROL General] 設定を使用すると、支払い方法として支払いサービスを有効または無効にし、顧客トランザクションに情報を追加して、Web サイトにマークを付けたり、カスタム情報を付けて表示することができます。

### 支払いサービスの有効化

次を有効にすることができます。 [!DNL Payment Services] web サイトに対して、サンドボックステストまたはライブ支払いを有効にします。

1. の _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![ホームビュー](assets/payment-services-menu-small.png)

1. クリック **[!UICONTROL Settings]**. 詳しくは、 [の概要 [!DNL Payment Services] ホーム](payments-home.md) を参照してください。

   この _[!UICONTROL General]_セクションには、を有効にするための設定が含まれています [!DNL Payment Services] を支払い方法として使用します。

1. 有効にするには [!DNL Payment Services] お客様の店舗の支払い方法として、 _[!UICONTROL General]_セクション、切り替え&#x200B;**[!UICONTROL Enable Payment Services as payment method]**から `Yes`.

1. まだテストを行っている場合 [!DNL Payment Services] お客様のストアには、 **支払いモード** から `Sandbox`. ライブ支払いを有効にする準備が整ったら、次のように設定します。 `Production`.

   >[!NOTE]
   >
   >お使いの _[!UICONTROL Sandbox Merchant ID]_および_[!UICONTROL Production Merchant ID]_ は自動生成され、サンドボックスや実稼動のオンボーディングを完了すると、該当するフィールドに存在します。

1. クリック **[!UICONTROL Save]**.

   変更を保存せずにこのビューから移動しようとすると、モーダルが表示され、変更の破棄、編集の続行、変更の保存を求めるプロンプトが表示されます。

1. に移動します。 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** をクリックし、 **[!UICONTROL Flush Cache]** 無効なキャッシュをすべて更新します。

次に、のデフォルト設定の変更に進むことができます： [支払いオプション](#configure-payment-options) 関数とストアフロントディスプレイ。

### ソフト記述子を追加

次の項目を追加できます： [!UICONTROL Soft Descriptor] を web サイトまたは個々のストア表示設定に追加します。 顧客トランザクション銀行明細書にソフト記述子が表示されます。 例えば、複数の店舗/ブランド/カタログがある場合、 [!UICONTROL Soft Descriptor] フィールドに入力します。

1. の _管理者_ サイドバー、移動 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![ホームビュー](assets/payment-services-menu-small.png)

1. クリック **[!UICONTROL Settings]**. 詳しくは、 [の概要 [!DNL Payment Services] ホーム](payments-home.md) を参照してください。
1. Web サイトまたはストア表示を、 **[!UICONTROL Scope]** ソフト記述子を作成するドロップダウンメニュー。 初期設定の場合、これは **[!UICONTROL Default]** をクリックしてデフォルト値を設定します。
1. テキストフィールドにカスタムテキスト（最大 22 文字）を追加し、 `Custom descriptor`.
1. クリック **[!UICONTROL Save]**.
1. Web サイトまたはストア表示に設定されたデフォルト以外のソフト記述子を作成するには、次の手順を実行します。
   1. Web サイトまたはストア表示を、 **[!UICONTROL Scope]** ソフト記述子を作成するドロップダウンメニュー。
   1. 切り替え *オフ* **[!UICONTROL Use website]** ( または **[!UICONTROL Use default]**（選択した範囲に応じて異なります）。
   1. テキストフィールドにカスタムテキストを追加します。
   1. クリック **[!UICONTROL Save]**.
1. Web サイトまたはストアに対して有効にするには、デフォルトのソフト記述子を表示します *または* 親 web サイトに使用されるソフト記述子：
   1. Web サイトまたはストア表示を、 **[!UICONTROL Scope]** 既存のソフト記述子を有効にするドロップダウンメニュー。
   1. 切り替え *オン* **[!UICONTROL Use website]** ( または **[!UICONTROL Use default]**（選択した範囲に応じて異なります）。
   1. クリック **[!UICONTROL Save]**.

   変更を保存せずにこのビューから移動しようとすると、モーダルが表示され、変更の破棄、編集の続行、変更の保存を求めるプロンプトが表示されます。

### 設定オプション

| フィールド | 範囲 | 説明 |
|---|---|---|
| [!UICONTROL Enable] | web サイト | 有効または無効 [!DNL Payment Services] を設定します。 オプション： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Payment mode] | ストア表示 | ストアのメソッドまたは環境を設定します。 オプション： [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | ストア表示 | サンドボックスマーチャント ID。サンドボックスのオンボーディング中に自動生成されます。 |
| [!UICONTROL Production Merchant ID] | ストア表示 | サンドボックスのオンボーディング中に自動生成される、実稼動マーチャント ID。 |
| [!UICONTROL Soft Descriptor] | web サイトまたはストア表示 | ソフト記述子を Web サイトに追加し、ビューを保存して、ブランド、店舗または製品ラインを説明する顧客トランザクションに情報を追加します。 この [!UICONTROL Use website] toggle は、web サイトレベルに追加されたソフト記述子を適用します。 この [!UICONTROL Use default] toggle は、デフォルトとして追加されたソフト記述子を適用します。 |

## 支払いオプションを設定

Web サイトで支払いサービスが有効になったので、支払い機能とストアフロント表示のデフォルト設定を変更できます。

### クレジットカードのフィールド

この _[!UICONTROL Credit Card Fields]_設定は、クレジットカードまたはデビットカードの支払い方法のためのシンプルでセキュアなチェックアウトオプションを提供します。

詳しくは、 [支払いオプション](payments-options.md#credit-card-fields) を参照してください。

1. ストア表示を選択します ( **[!UICONTROL Scope]** 支払い方法を有効にするドロップダウンメニュー。
1. チェックアウト時に表示される支払い方法の名前を変更するには、 **[!UICONTROL Checkout title]** フィールドに入力します。
1. 宛先 [支払い処理を設定](production.md#set-payment-services-as-payment-method)，切り替え **[!UICONTROL Payment action]** から `Authorize` または `Authorize and Capture`.
1. チェックアウトページのクレジットカードフィールドを有効または無効にするには、 **[!UICONTROL Show on checkout page]** セレクター。
1. デバッグモードを有効または無効にするには、 **[!UICONTROL Debug Mode]** セレクター。
1. クリック **[!UICONTROL Save]**.

   変更を保存せずにこのビューから移動しようとすると、モーダルが表示され、変更の破棄、編集の続行、変更の保存を求めるプロンプトが表示されます。

1. に移動します。 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** をクリックし、 **[!UICONTROL Flush Cache]** 無効なキャッシュをすべて更新します。

#### 設定オプション

| フィールド | 範囲 | 説明 |
|---|---|---|
| [!UICONTROL Title] | ストア表示 | チェックアウト時に「支払い方法」ビューで、この支払いオプションのタイトルとして表示するテキストを追加します。 オプション： [!UICONTROL text field] |
| [!UICONTROL Payment Action] | web サイト | この [支払手続](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;} （指定した支払い方法） オプション： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show on checkout page] | web サイト | チェックアウトページに表示するクレジットカードフィールドを有効または無効にします。 オプション： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | web サイト | デバッグモードを有効または無効にします。 オプション： [!UICONTROL Yes] / [!UICONTROL No] |

### 支払いボタン

この [!DNL PayPal Smart Buttons] 支払いオプションは、お客様に対して、シンプルで迅速かつ安全なチェックアウトプロセスを提供します。 詳しくは、 [支払いオプション](payments-options.md#paypal-smart-buttons) を参照してください。

PayPal スマートボタンの支払いオプションを有効にして設定できます。

1. ストア表示を選択します ( **[!UICONTROL Scope]** 支払い方法を有効にするドロップダウンメニュー。
1. チェックアウト時に表示される支払い方法の名前を変更するには、 **[!UICONTROL Checkout Title]** フィールドに入力します。
1. 宛先 [支払い処理を設定](production.md#set-payment-services-as-payment-method)，切り替え **[!UICONTROL Payment action]** から `Authorize` または `Authorize and Capture`.
1. 切り替えセレクターを使用して、有効または無効にします [!DNL PayPal smart button] 表示機能：
   - **[!UICONTROL Show PayPal buttons on product checkout page]**
   - **[!UICONTROL Show PayPal buttons on product detail page]**
   - **[!UICONTROL Show PayPal buttons in mini-cart preview]**
   - **[!UICONTROL Show PayPal buttons on cart page]**
   - **[!UICONTROL Show PayPal Pay Later button]**
   - **[!UICONTROL Show PayPal Pay Later message]**
   - **[!UICONTROL Show Venmo button]**
   - **[!UICONTROL Show Apple Pay button]**

      >[!NOTE]
      >
      > Apple Pay を使用するには [は、Apple Developer アカウントを持っている必要があります](test-validate.md#test-in-sandbox-environment) （偽のクレジットカードと請求情報を含む）をテストします。 サンドボックスでApple Pay を使用する準備が整ったら、 *または* 実稼動モード（任意の完了後） [テストと検証](test-validate.md)を使用する場合は、営業担当者に連絡して、ライブストアで有効にしてもらってください。

      支払いボタンや PayPal Pay Later メッセージの表示/非表示を切り替えると、設定ページの下部にその設定の視覚的なプレビューが表示されます。

1. デバッグモードを有効にするには、 **[!UICONTROL Debug Mode]** セレクター。
1. クリック **[!UICONTROL Save]**.

   変更を保存せずにこのビューから移動しようとすると、モーダルが表示され、変更の破棄、編集の続行、変更の保存を求めるプロンプトが表示されます。

1. に移動します。 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** をクリックし、 **[!UICONTROL Flush Cache]** 無効なキャッシュをすべて更新します。

#### 設定オプション

| フィールド | 範囲 | 説明 |
|---|---|---|
| [!UICONTROL Title] | ストア表示 | チェックアウト時に「支払い方法」ビューで、この支払いオプションのタイトルとして表示するテキストを追加します。 オプション：テキストフィールド |
| [!UICONTROL Payment Action] | web サイト | この [支払手続](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;} （指定した支払い方法） オプション： [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show PayPal buttons on checkout page] | ストア表示 | 有効または無効 [!DNL PayPal Smart Buttons] をチェックアウトページに追加します。 オプション： [!UICONTROL  Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons on product detail page] | ストア表示 | 有効または無効 [!DNL PayPal Smart Buttons] 製品の詳細ページに表示されます。 オプション： [!UICONTROL  Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons in mini-cart preview] | ストア表示 | 有効または無効 [!DNL PayPal Smart Buttons] をクリックします。 オプション： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons on cart page] | ストア表示 | 有効または無効 [!DNL PayPal Smart Buttons] を買い物かごページに追加します。 オプション： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal Pay Later button] | ストア表示 | 支払いボタンが表示される後払いオプションの外観を有効または無効にします。 オプション： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal Pay Later Message] | web サイト | 買い物かご、製品ページ、ミニ買い物かごおよびチェックアウトフローの「後で支払う」メッセージを有効または無効にします。 オプション： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show Venmo button] | ストア表示 | 支払いボタンが表示される Venmo 支払いオプションを有効または無効にします。 オプション： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show Apple Pay button] | ストア表示 | 支払いボタンが表示される「Apple支払」支払いオプションを有効または無効にします。 オプション： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | web サイト | デバッグモードを有効または無効にします。 オプション： [!UICONTROL Yes] / [!UICONTROL No] |

### ボタンのスタイル

また、 _[!UICONTROL Button style]_PayPal スマートボタンのオプション：

1. 次の手順で **[!UICONTROL Layout]**&#x200B;を選択します。 `Vertical` または `Horizontal`.

   >[!NOTE]
   >
   > ボタンのスタイルが `Horizontal` お客様のストアは、複数の PayPal スマートボタンを表示するように設定されています。製品ページ、チェックアウトページ、ミニカートに表示されるボタンが 2 つ、カートに表示されるボタンが 1 つだけです。

1. 横置きレイアウトでタグラインを有効にするには、 **[!UICONTROL Show tagline]** セレクター。
1. 次の手順で **[!UICONTROL Color]**」で、目的のカラーオプションを選択します。
1. 次の手順で **[!UICONTROL Shape]**&#x200B;を選択します。 `Pill` または `Rectangle`.
1. ボタンの高さセレクターを有効にするには、 **[!UICONTROL Responsive button height]** セレクター。
1. 次の手順で **[!UICONTROL Label]**」で、目的のラベルオプションを選択します。

   レイアウト、色、形状、高さ、ラベルの設定オプションを変更すると、その設定の視覚的なプレビューが設定ページの下部に表示されます。

1. クリック **[!UICONTROL Save]**.

   変更を保存せずにこのビューから移動しようとすると、モーダルが表示され、変更の破棄、編集の続行、変更の保存を求めるプロンプトが表示されます。

1. に移動します。 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** をクリックし、 **[!UICONTROL Flush Cache]** 無効なキャッシュをすべて更新します。

次の項目を設定できます。 [!DNL PayPal Smart Buttons] スタイル設定 [（管理者の従来の設定）](configure-admin.md#configure-paypal-smart-buttons) またはここに [!DNL Payment Services Home]. 詳しくは、 [PayPal のボタンスタイルガイド](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) を参照してください。

#### 設定オプション

| フィールド | 範囲 | 説明 |
|--- |--- |--- |
| [!UICONTROL Layout] | ストア表示 | 支払いボタンのレイアウトのスタイルを定義します。 オプション： [!UICONTROL Vertical] / [!UICONTROL Horizontal] |
| [!UICONTROL Tagline] | ストア表示 | タグラインを有効/無効にします。 オプション： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Color] | ストア表示 | 支払いボタンの色を定義します。 オプション： [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black] |
| [!UICONTROL Shape] | ストア表示 | 支払いボタンの形状を定義します。 オプション： [!UICONTROL Rectangular] / [!UICONTROL Pill] |
| [!UICONTROL Responsive Button Height] | ストア表示 | 支払いボタンが既定の高さを使用するかどうかを定義します。 オプション： [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Height] | ストア表示 | 支払いボタンの高さを定義します。 デフォルト値：なし |
| [!UICONTROL Label] | ストア表示 | 支払いボタンに表示されるラベルを定義します。 オプション： [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment] |

## 複数の PayPal アカウントを使用

支払いサービスでは、 **1 つ** ウェブサイトレベルのマーチャントアカウント。 例えば、複数の国 ( 異なる [通貨](https://docs.magento.com/user-guide/stores/currency.html)) またはAdobe Commerceをビジネスの一部に使用したいが、使用しない場合 *すべて*&#x200B;複数の PayPal アカウントを使用するようにマーチャントアカウントを設定することができます。

詳しくは、 [サイト、ストア、および表示範囲](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html) web サイト、ストア、ストア表示の階層に関する詳細。

セールス担当者が新しい [範囲](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) お客様のマーチャントアカウントに対して、PayPal を使用して追加サイトをオンボーディングし、設定した PayPal ボタンがサイトに表示されるようにします。 Web サイトに複数の PayPal アカウントを使用する方法については、セールス担当者にお問い合わせください。
