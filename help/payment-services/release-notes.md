---
title: “[!DNL Payment Services] リリースノート」
description: すべてについて詳しくは、リリースノートを確認してください [!DNL Payment Services] リリース。
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
feature: Payments, Release Notes
source-git-commit: 9f0381546a98a8a5d72394adbd3ddd49daf539cb
workflow-type: tm+mt
source-wordcount: '2547'
ht-degree: 0%

---

# リリースノート

これらのリリースノートは、の初回リリースについて説明しています [!DNL Payment Services] これには以下が含まれます。

![新規](../assets/new.svg) 新機能
![修正された問題](../assets/fix.svg) 修正点および改善点
![既知の問題](../assets/bug.svg) 既知の問題

通常の機能リリースバージョン以外でリリースされた機能の変更および修正については、 _ホステッド サービスの更新_ セクション。

今後のリリース、製品のサポート、およびサポートされるAdobe Commerceのバージョンについて詳しくは、こちらを参照してください [!DNL Payment Services] 拡張機能については、Adobe Commerceを参照 [リリーススケジュール](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/schedule) および [製品の可用性](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability) トピック。

## ホステッド サービスの更新

これらのリリースノートでは、ホステッド サービスの通常の機能リリースの外部で発生した機能の変更と修正について説明します。

+++ホステッド サービスの更新

_2024 年 7 月 9 日（Pt）_

![新規問題](../assets/new.svg)<!-- Issue PAY-5488 --> マーチャントは、Commerce顧客 ID をの列として表示できるようになりました。 [トランザクションレポート](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html) 特定の顧客が行ったトランザクションの特定に役立ちます。 さらに、マーチャントは、このCommerce顧客 ID でトランザクションレポートをフィルタリングして、関連する注文を確認できます。

_2024 年 3 月 5 日（Pt）_

![修正された問題](../assets/fix.svg)<!-- Issue PAY-5252 --> マーチャントは、単一のセルの内容を選択することで、ダッシュボードグリッドからデータをコピーできるようになりました。

_2023 年 10 月 10 日（Pt）_

![新規問題](../assets/fix.svg)<!-- Issue PAY-4888 --> 現在は、以下のカード番号の最後の 4 桁でクレジット カードとデビット カードの取引をフィルタリングできます [トランザクションレポート](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html).

_2023 年 7 月 12 日（Pt）_

![修正された問題](../assets/fix.svg)<!-- Issue PAY-4587 --> で発生した問題 [!DNL Payment Services] 以前の拡張機能バージョンで設定された認証ボイドを防止していた 2.1.0 リリースが解決されました。 任意のバージョンの [!DNL Payment Services] 承認を無効にできます。

_2023 年 6 月 9 日（Pt）_

![新規](../assets/new.svg)<!-- Issue PAY-4288 --> 現在では、マーチャントは以下を実行できます [設定 _のみ_ PayPal 支払いボタン](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#use-only-paypal-payment-buttons) – および _ではない_ paypal クレジットカードの支払いオプションを使用してください。 これにより、マーチャントは、Venmo や PayPal の支払いボタンなど様々な支払いオプションを提供したり、PayPal のクレジットカード支払いオプションの代わりに既存のクレジットカード会社を使用したりできます。

![新規](../assets/new.svg)<!-- Issue PAY-4050 --> がを追加しました [データビジュアライゼーションビュー](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#order-payment-status-data-visualization-view)支払いサービスのホームに表示される、注文の支払いステータスレポート用。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-4486--> 以前は、PayPal PayLater ボタンは、英国のマーチャントのチェックアウトには表示されていませんでした。 その問題は解決しました。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-4485--> レポートデータビジュアライゼーションビューがに表示されるようになりました [!DNL Payment Services] ホーム条件[!DNL Payment Services] が無効になっています。

_2023 年 1 月 25 日（Pt）_

![既知の問題](../assets/bug.svg)<!-- Issue PAY-4102 --> の新規インストール [!DNL Payment Services] Commerce サービスを設定できません。レンダリングします [!DNL Payment Services] 操作不能 この問題を修正するには、 [!DNL Payment Services] バージョン 1.5.3 の拡張機能。

_2022 年 9 月 12 日（Pt）_

![新規](../assets/new.svg)<!-- Issue PAY-3705 --> この `increment_id` は、外部 ERP システムでの支払いの調整に使用できるようになりました。 ダイアログは、に伝播されます。 [`custom_id` _および_ `invoice_id`](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/data.html#reconcile-with-erp-system)（支払い用の PayPal Webhook とマーチャントアクティビティの詳細の両方に表示）。

_2022 年 8 月 31 日（Pt）_

![修正された問題](../assets/fix.svg)<!-- Issue PAY-3629 --> 新しいマーチャントが以下にアクセスした場合 [!DNL Payment Services] ホームは初めて、ページを更新する必要がなく、ページがすぐに読み込まれてコンテンツが表示されるようになりました。

_2021 年 8 月 9 日（Pt）_

![新規](../assets/new.svg)<!-- Issue PAY-3420 --> Apple Pay が PayPal スマートボタンとして使用できるようになりました。 この [支払オプション](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-options.html#apple-pay-button) を使用すると、お客様はiOSまたはmacOS デバイスでタッチ ID 機能を使用して、Apple Pay を選択できます。 Apple Pay は、デバイスに保存されているクレジットカードとデビットカードの支払資格情報を使用して支払いを処理します。

_2021 年 6 月 28 日（Pt）_

![新規](../assets/new.svg)<!-- Issue PAY-1720 --> 店舗注文の争議がで利用できるようになりました [注文支払いステータスレポート](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#view-disputes). から PayPal 解決センターに直接移動することで、紛争に対処できます。 [!DNL Payment Services].

![新規](../assets/new.svg)<!-- Issue PAY-2854 --> のユーザーエクスペリエンスの向上 [!DNL Payment Services] ホームには、現在の継承レベルで設定を変更する機能や、ヘッダーとナビゲーションの表示を改善する機能が含まれています。

![新規](../assets/new.svg)<!-- Issue PAY-2854 --> サンドボックスモードから実稼動モードに切り替えた場合や、保存されていない更新を含むビューから移動しようとした場合に、警告が表示されるようになりました。

![新規](../assets/new.svg)<!-- Issue PAY-2761 --> に表示されるデータをカスタマイズできるようになりました [注文支払いステータスレポート](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#show-and-hide-columns) および [支払いレポート](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/payouts.html#show-and-hide-columns) 列設定コントロールを使用して、列を表示または非表示にする。

+++

## v2.6.0

_2024 年 6 月 4 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg)<!-- PAY-4877 --> さて、 [!DNL Payment Services] のサポート [L2/L3 の価格機能](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/levels-card-payment-transactions.html). これは、 [!DNL Payment Services] ic++の価格設定が有効な顧客。 以下に対して L2/L3 処理データを使用する場合： [!DNL Payment Services]、にお問い合わせください [!DNL Payment Services] アカウントマネージャー。

![修正](../assets/fix.svg)<!-- PAY-5455 -->[!DNL Payment Services] をダウンロードしてホストすることなく、拡張機能から直接Apple Pay を有効にすることができます [ドメイン関連付けファイル](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain).

## v2.5.0

_2024 年 4 月 23 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![修正](../assets/fix.svg)<!-- Issue PAY-5396 -->[!DNL Payment Services] がサポートされるようになりました [Adobe Commerceのガイドライン `--db-prefix` パラメーター](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/advanced#install-from-the-command-line) （Adobe Commerce バージョン 2.4.7 以降の場合）

## v2.4.3

_2024 年 4 月 16 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![修正](../assets/fix.svg)<!-- Issue PAY-5106 --> PayPal とAdobe Commerceの間のチェックアウト時に注文金額の合計が正しく入力されない問題を修正しました。 マーチャントは、注文を行う際に注文金額の合計が正しいことを確認できるようになりました。

## v2.4.2

_2024 年 4 月 11 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg)<!-- Issue xxx --> Adobe Commerce 2.4.7 がサポートされるようになりました。

## v2.4.1

_2024 年 4 月 4 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![修正](../assets/fix.svg)<!-- PAY-5322 --> 新しいAdobe Commerce リリースとの PCI 互換性の問題を修正しました。 さて、 [!DNL Payment Services] は、支払いオプションとしてAdobe Commerceのチェックアウト要件に適応します。

![修正](../assets/fix.svg)<!-- PAY-5323 --> PayLater および Venmo は、Adobe Commerceで正しく表示されます。 管理者に PayLater と Venmo の切り替えオプションを表示できなかったエラーを修正しました。

## v2.4.0

_2024 年 3 月 20 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg)<!-- PAY-4868 --> マーチャントは正常に [購入体験全体を通したGoogle Pay の設定](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html)（の他の支払いボタンと同様）[!DNL Payment Services] admin を使用する。

![新規](../assets/new.svg)<!-- PAY-4381 --> [支払いサービスは、GraphQLを通じてGoogle Pay をサポートします](https://developer.adobe.com/commerce/webapi/graphql/payment-services/) マーチャントは、Google Pay 支払い方法でヘッドレスなCommerceエクスペリエンスを得ることができます。

![新規](../assets/new.svg)<!-- PAY-4878 --> さて、 [!DNL Payment Services] 基本的なチェックアウト機能は、Adobe CommerceおよびMagento Open Sourceマーチャントにバンドルされています。[!DNL Payment Services] は、世界中の 200 か所の地域で、ビジネスを持つマーチャントをサポートできるようになりました。[!DNL Payment Services] ベーシックチェックアウトでは、デビット/クレジット、PayPal、Venmo （利用可能な場合）、PayLater （利用可能な場合）のオプションがセルフサービスのオンボーディングで提供されます。

![修正](../assets/fix.svg)<!-- PAY-5291 --> 一部の取引に関する支払確認の受信が遅延する場合があります。 その場合、マーチャントは注文の更新された支払いステータスを取得できるようになりました。 [支払サービスは、支払トランザクションの保留状態を検出します](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html) 保留中のトランザクションを検出し、これらのトランザクションをプロアクティブに監視し、保留中ステータスが取り込まれたときに更新します。

## v2.3.4

_2024 年 3 月 1 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg)<!-- PAY-5244 --> 非同期チェックアウトの互換性を修正しました。

![修正](../assets/fix.svg)<!-- PAY-5253 --> Vault トークンがに属していないエラーを修正しました [!DNL Payment Services] を削除できませんでした。

## v2.3.3

_2024 年 2 月 14 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg)<!-- PAY-5048 --> PHP 8.3 のサポートを追加

![修正](../assets/fix.svg)<!-- PAY-5048 --> エラーを修正しました `is_deleted` フラグ。 現在は、 `Rejected` 拡張機能から送信されたステータス。

## v2.3.2

_2024 年 1 月 26 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![修正](../assets/fix.svg)<!-- PAY-5183 --> REST/GraphQLのパフォーマンスの問題を修正しました。 現在は、API を介して取得された際に、クレジットカードのボタンがレンダリングされるようになりました。

## v2.3.1

_2023 年 12 月 7 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg)<!-- PAY-5047 --> クレジット/デビットカードのブランドまたは支払い方法のタイプを、次の場所から利用できるようになりました。

- ストアフロントの顧客注文ページ
- 買い物客に送信された注文確認メール
- から [注文の詳細表示](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-processing.html#view-an-order) Commerce Admin.

## v2.3.0

_2023 年 12 月 1 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg)<!-- PAY-4381 --> [支払いサービスでGraphQL統合がサポートされるようになりました](https://developer.adobe.com/commerce/webapi/graphql/payment-services/). PayPal 支払いボタン、ホストされたフィールド、Apple Pay のGraphQL サポートにより、[!DNL Payment Services] では、ヘッドレス Commerceの設定をサポートするようになりました。

## v2.2.1

_2023 年 9 月 27 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![修正された問題](../assets/fix.svg)<!-- Issue PAY-4870 --> 最新リリースで拡張機能バージョンを送信する際に、ストアフロントで新しいヘッダー属性が正しく入力されない問題を修正しました。 以前は、 `1.3.0` Commerce サービスコネクタのリリースでは、を拡張できませんでした `User-Agent header` から [!DNL Payment Services] 拡張機能。

## v2.2.0

_2023 年 8 月 30 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg)<!-- PAY-4638 --> さんがを追加しました [signifyd との統合](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/security-compliance/fraud-protection.html)を使用すると、自動的に不正を保護するサービスを提供できます。

![新規](../assets/new.svg)<!-- PAY-3981 --> [昇格済みApple別のお支払い方法への支払い](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html?lang=en#apple-pay-button)（PayPal 支払いボタンの外側）を使用すると、買い物客による支払いオプションの可視性を高め、マーチャントがApple Pay の配置とスタイル設定を制御できるようになります。

![新規](../assets/new.svg)<!-- PAY-4002 --> 買い物客の認知負荷を軽減し、コンバージョンを増やすために、支払いアイコンの追加などのスタイル設定の強化を含め、クレジットカードフィールドのチェックアウトのユーザーエクスペリエンスを改善しました。

![新規](../assets/new.svg)<!-- PAY-4002 --> マーチャントがにアクセスできる機能を追加しました。 [支払いオプションの順序の並べ替え](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#payment-buttons) 特定の支払いオプションに優先順位を付ける。 この機能により、チェックアウトの会話率を高くすることをお勧めします。

![新規](../assets/new.svg)<!-- PAY-4035 --> マーチャントは、ストアの正常性を効率的に監視し、新しいを使用してトランザクションの問題を特定できるようになりました [トランザクションレポート](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html) から使用可能[!DNL Payment Services] 管理者ホームページ。 このレポートには、トランザクションの承認レートと負のトランザクションのトレンドに関するデータも表示されます。

## v2.1.0

_2023 年 6 月 9 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg)<!-- Issue xxx --> Adobe Commerce 2.4.7-beta1 がサポートされるようになりました。

![新規](../assets/new.svg)<!-- Issue xxx --> 追加済み [次の国および関連通貨での提供](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#availability)：オーストラリア、フランス、英国。

![新規](../assets/new.svg)<!-- Issue PAY-4296 --> 追加済み [管理者ロール用の拡張リソース](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-roles) 管理者ユーザーが顧客の注文を作成および管理し、次の情報を確認できるようにします[!DNL Payment Services] 営業メニューに移動します。

![新規](../assets/new.svg)<!-- Issue PAY-4236 --> 追加済み [チェックアウト中にエラーが発生した注文の自動無効化](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/checkout.html#order-auto-voided-if-error).

![新規](../assets/new.svg)<!-- Issue PAY-4183 --> に機能を作成しました [クレジット/デビット カード支払オプション ボタンを表示します](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#debit-or-credit-card-button) チェックアウトページで、次の操作を行います。

## v2.0.0

_2023 年 3 月 10 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg)<!-- Issue PAY-4152 --> PHP 8.2 およびAdobe Commerce 2.4.6 がサポートされるようになりました。PHP 7.x との互換性はありません。

## v1.6.1

_2023 年 3 月 10 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![修正](../assets/fix.svg)<!-- Issue PAY-4226 --> 新規に追加できない問題を修正しました [!DNL Payment Services] 管理でチェックアウトを使用しているマーチャント。[!DNL Payment Services] 以前は、はCommerceの顧客 ID を使用していましたが、これは新規の顧客には存在しません。

![修正](../assets/fix.svg)<!-- Issue PAY-4205 --> を使用してチェックアウトする際に、指定した配送先住所の州がデフォルトの税金設定の州に置き換えられる問題を修正しました [PayPal オプション](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#paypal-smart-buttons). これで、顧客は注文をマーチャントの税金設定でデフォルトとして設定された以外の州に出荷できます。

![修正](../assets/fix.svg)<!-- Issue PAY-4202 --> 顧客がカードボルトを使用して店舗の購入を完了したり、ボルトを使用した支払い方法を削除したりできない問題を修正しました [の使用 `Authorize and Capture` 支払いアクション](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/production.html#set-payment-services-as-payment-method). 以前は、お客様がボールトに登録されているクレジットカードを使用または変更しようとすると、「Provider Vault ID が見つかりません」というエラーが表示されていました。

## v1.6.0

_2023 年 2 月 17 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg)<!-- Issue PAY-3540 --> 追加済み [欧州連合（EU）および英国で取引される商社向けの PCI 3DS コンプライアンス機能](security.md#3ds). この追加のセキュリティレイヤーは、購入者にクレジットカード発行者との認証を求め、オンラインでの詐欺を防ぐのに役立ち、欧州連合（EU）のコンプライアンス規制の一部として必要です。

![新規](../assets/new.svg)<!-- Issue PAY-3609 --> にを追加しました。 [管理者でのカードボルトの有効化](vaulting.md#use-vaulting-in-the-admin). これにより、マーチャントは、ボールト内の支払い方法を使用して、管理者で顧客の注文を作成できます。

## v1.5.4

_2023 年 1 月 29 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![修正された問題](../assets/fix.svg)<!-- Issue PAY-4110 --> 購入者が商品ページ、ミニカート、カートの支払いボタンを使用して注文できない問題を修正しました。 バイヤーは正常に注文を完了できるようになりました。

## v1.5.3

_2023 年 1 月 25 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![修正された問題](../assets/fix.svg)<!-- Issue PAY-4102 --> 後方互換性のない既知の問題の修正をリリースしました。 このリリースでは、サービス ID 拡張機能のバージョンが最新の安定したバージョンにロックされるので、新しい [!DNL Payment Services] Commerce サービスを設定するためのインストール。

## v1.5.2

_2022 年 12 月 22 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![修正された問題](../assets/fix.svg)<!-- Issue PAY-3992 --> での請求の改善 [!DNL Payment Services] 支払い方法が却下されたとき。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-3999 -->[!DNL Payment Services] を使用しているマーチャントに対して PayPal 支払いボタンを正しく表示するようになりました。 [火災チェックアウト`s](https://commercemarketplace.adobe.com/swissup-firecheckout.html){target=_blank} チェックアウトページのカスタムテンプレート。 以前は、ミニカートは断続的にボタンを表示していました。

## v1.5.1

_2022 年 11 月 23 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg)<!-- Issue PAY-3923 -->[!DNL Payment Services] では、ユーザーエージェントヘッダーにバージョン番号が含まれるようになりました。これにより、リクエストで未使用のエンドポイントを追跡、フィルタリングまたは非推奨（廃止予定）にできるようになりました。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-3968 -->[!DNL Payment Services] 支払いボタンを使用して製品ページから注文する際に、注文データが正しく表示されるようになりました。

## v1.5.0

_2022 年 11 月 18 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg)<!-- Issue PAY-3880 --> 買い物客は、次のことが可能になりました [チェックアウト時のクレジットカード情報の vault （保存）](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html) 同じマーチャントアカウント内の同じ店舗または別の店舗の後の購入で使用する。

![新規](../assets/new.svg)<!-- Issue PAY-3950 --> マーチャントは、 [Commerceの即時購入機能](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/checkout-instant-purchase.html) 買い物客ができるように店舗のために（使用 [ヴォールト・クレジット・カード情報](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html)）を指定して、チェックアウトを迅速化します。

## v1.4.1

_2022 年 10 月 14 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![修正](../assets/fix.svg)<!-- Issue PAY-3766 --> 顧客の支払い方法が拒否された場合、表示されるエラーメッセージはより説明的です。 支払い情報を再度入力し、もう一度試すか、別の支払い方法を試すか、または拒否されたトランザクションについて銀行に連絡することを顧客に勧めます。

## v1.4.0

_2022 年 9 月 30 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg)<!-- Issue PAY-784 -->[!DNL Payment Services] には、にマーチャントアカウントを設定する機能が含まれるようになりました [複数の PayPal ビジネスアカウントの使用](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#use-multiple-paypal-accounts). これにより、マーチャントは、異なる通貨を使用して複数の国で店舗を運営したり、ビジネスの一部にAdobe Commerceを使用したりできます。

![新規](../assets/new.svg)<!-- Issue PAY-3231 --> マーチャントは [を追加 [!UICONTROL Soft Descriptor]](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#add-soft-descriptor) 顧客トランザクションの銀行取引明細書に表示される、ブランド、店舗または製品ラインを区別するための Web サイトまたは個々の店舗ビュー設定です。

![新規](../assets/new.svg)<!-- Issue PAY-3707 --> [クレジットカードのフィールドと PayPal 支払いボタンを有効または無効にする](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-payment-options) チェックアウト場所[!DNL Payment Services] 設定。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-3546 --> 顧客がクリックしたとき **[!UICONTROL Edit cart]**&#x200B;ページが買い物かごページにリダイレクトされ、空の買い物かごが表示されるのではなく、更新された項目が表示されます。

## v1.3.1

_2022 年 9 月 6 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![修正された問題](../assets/fix.svg)<!-- Issue PAY-3663 --> これで、非世界通貨で承認された注文をマーチャントの店舗が取り込む際に、取り込みプロセスが完了し、エラーは表示されません。

## v1.3.0

_2022 年 8 月 9 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg)<!-- Issue PAY-XX --> 一般提供リリース – [!DNL Payment Services] が現在 [サポート者 [!DNL Adobe Commerce] および [!DNL Magento Open Source] バージョン 2.4.0 ～ 2.4.5](https://devdocs.magento.com/release/availability.html#compatibility).

![修正された問題](../assets/fix.svg)<!-- Issue PAY-x --> Apple Pay は、モバイルとデスクトップの Safari ブラウザー v15.5 と互換性を持つようになりました。

## v1.2.0

_2022 年 6 月 29 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![既知の問題](../assets/bug.svg)<!-- Issue PAY-x --> Apple Pay は、モバイルおよびデスクトップ上の Safari ブラウザー v15.5 と互換性がありません。 Safari バージョン 15.5 をご利用の場合、Apple Pay でチェックアウトを完了できません。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-3264 --> 以前は、ログインユーザーが自分のアカウントのデフォルトの住所以外の請求/配送先住所を選択すると、チェックアウトに失敗していました。 これで、デフォルトの保存済み住所ではなく、選択した請求先/配送先住所が送信され、チェックアウトが正常に完了します。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-3314 --> チェックアウト時に PayPal 支払いボタンを無効にしても、エラーは表示されません。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-3330 --> ゲストユーザーがダッシュを含む電話番号を入力しても、チェックアウト中に支払いが失敗しなくなりました。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-3338 PAY-2502 --> Commerce サービスの資格情報が無効な場合、[!DNL Payment Services] では、から資格情報エラーを表示することでアラートを表示するようになりました [!DNL Payment Services] 管理者のホーム。

![既知の問題](../assets/bug.svg)<!-- Issue PAY-0 --> [!DNL Payment Services] と互換性がありません `commerce-data-export` v101.20 以降（との互換性がない） [[!DNL Channel manager] 拡張子](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/guide-overview.html).

## v1.1.0

_2022 年 3 月 31 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg)<!-- Issue PAY-2127 --> 一般提供リリース – [!DNL Payment Services] が現在 [サポート者 [!DNL Adobe Commerce] および [!DNL Magento Open Source] バージョン 2.4.0 ～ 2.4.4](https://devdocs.magento.com/release/availability.html#compatibility).

![新規](../assets/new.svg)<!-- Issue PAY-2682 --> この [!DNL Payment Services] の拡張機能 [!DNL Adobe Commerce] および [!DNL Magento Open Source] がカナダのマーチャントで利用できるようになりました。 マーチャントは、次のいずれかで支払設定を表示できます [フランス語](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=fr#carte-de-cr%C3%A9dit-et-devises-accept%C3%A9es) または [英語](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#accepted-credit-cards-and-currencies).

![新規](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] のサポート [カナダドル （CAD）](overview.md#accepted-credit-cards-and-currencies) クレジットカードおよび PayPal トランザクションの場合。

![新規](../assets/new.svg)<!-- Issue PAY-2680 --> マーチャントは [機内 [!DNL Payment Services]](onboard.md) 英語またはフランス語の拡張機能。

![新規](../assets/new.svg)<!-- Issue PAY-2678 --> マーチャントは、財務レポートを両方とも表示できるようになりました [注文支払いステータス](order-payment-status.md) および [支払いレポート](payouts.md)をカナダ ドル （CAD）で表示します。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-2710 -->[!DNL Payment Services] は、と互換性を持つようになりました [PHP 8.1](https://www.php.net/releases/8.1/en.php).

![修正された問題](../assets/fix.svg)<!-- Issue PAY-3017 --> サンドボックスモードのアラートが改善され、複数のストアに対して適切なアラートが表示されるようになりました。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-2742 --> ストア表示レベルで、Venmo などの使用可能な支払い方法を有効または無効にできるようになりました。 以前は、web サイトごとにのみ支払い方法を設定できました。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-2277 --> 選択的に使用できるようになりました [個々の PayPal 支払いボタンを有効または無効にする](settings.md#payment-buttons).

![修正された問題](../assets/fix.svg)<!-- Issue PAY-2561 --> 以前に削除した製品は、のカートには表示されません _レビュー注文_ ページ。

![既知の問題](../assets/bug.svg)<!-- Issue PAY-2842 --> クレジット カード トランザクションのテスト [は PayPal で失敗する場合があります](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html) サンドボックス環境で支払いを処理する場合。

## v1.0.0

_2021 年 11 月 29 日（Pt）_

[!BADGE サポート]{type=Informative tooltip="サポート"}

![新規](../assets/new.svg)<!-- Issue PAY-2127 --> 一般提供リリース – [[!DNL Payment Services]](https://commercemarketplace.adobe.com/magento-payment-services.html) は、でサポートされるようになりました。 [!DNL Adobe Commerce] および [!DNL Magento Open Source] バージョン 2.4.0 ～ 2.4.3-p1。

![新規](../assets/new.svg)<!-- Issue PAY-124 --> この [!DNL Payment Services] の拡張機能 [!DNL Adobe Commerce] および [!DNL Magento Open Source] は、次のいずれかの目的でインストールできます [[!DNL Adobe Commerce] クラウドインフラストラクチャー上](install.md#adobe-commerce-on-cloud-infrastructure) または [オンプレミス](install.md#on-premises) インスタンス。 これらのメソッドを使用するには、コマンドラインインターフェイスを使用する必要があります。

![新規](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] はをサポートします [サンドボックスアカウント](sandbox.md) これにより、マーチャントはテストモードで拡張機能を評価できます。

![新規](../assets/new.svg)<!-- Issue PAY-666 --> マーチャントは [支払いサービスの設定](settings.md) 使用などの基本的な支払い行動を伴う拡張 [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) サンドボックス環境または実稼動環境の切り替え。

![新規](../assets/new.svg)<!-- Issue PAY-780 --> 買い物客は以下を確認できます。 [!DNL Payment Services] または経由 [手動での注文の作成](create-order.md).

![新規](../assets/new.svg)<!-- Issue PAY-1856 --> 包括的なレポート機能（次を使用） [注文支払いステータス](order-payment-status.md) および [支払いレポート](payouts.md)、は以下で利用できます。 [!DNL Payment Services] ストアの注文と関連する支払いを明確に把握できるようにします。

![新規](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] では、総処理量に基づいて、あらゆる販売会社に合わせた柔軟な階層型価格がサポートされています。

![新規](../assets/new.svg)<!-- Issue PAY-1443 --> あなたは簡単にできます [ルックアンドフィールをカスタマイズ](payments-options.md) の PayPal 支払いボタンとクレジットカードフィールド [!DNL Payment Services] 拡張機能。

![既知の問題](../assets/bug.svg)<!-- Issue PAY-2473 --> 使用 [間違った Composer キー](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html) 拡張機能のインストール中に、ユーザーは次の操作を実行できません [認証中](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 正しい `MAGEID`.

![既知の問題](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] 報告書 [すぐには同期されない場合があります](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html).

![既知の問題](../assets/bug.svg)<!-- Issue PAY-2475 --> あなたの [PayPal サンドボックスアカウント](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html) （用） [!DNL Payment Services] オンボーディング中にそのアカウントを作成した場合は、検証できません。
