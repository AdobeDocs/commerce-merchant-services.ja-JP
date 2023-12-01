---
title: "[!DNL Payment Services] リリースノート"
description: すべての [!DNL Payment Services] リリース。
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
feature: Payments, Release Notes
source-git-commit: 03349802fb747028cbd66ed6ce3ca7ad247f4c07
workflow-type: tm+mt
source-wordcount: '2316'
ht-degree: 0%

---

# リリースノート

以下のリリースノートでは、 [!DNL Payment Services] およびを含めます。

![新規](../assets/new.svg) 新機能
![修正された問題](../assets/fix.svg) 修正点および改善点
![既知の問題](../assets/bug.svg) 既知の問題

通常のバージョン管理された機能リリース以外でリリースされた機能の変更および修正については、ホストされたサービスの更新の節を参照してください。

詳しくは、 [今後のリリース](https://devdocs.magento.com/release/) を参照してください。

詳しくは、 [製品の可用性](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html) を参照して、この拡張機能をサポートしているAdobe Commerceバージョンを確認してください。

## ホストされるサービスの更新

これらのリリースノートでは、ホストされているサービスの通常のバージョン管理機能リリース以外でリリースされた、機能の変更点と修正点について説明します。

+++ホストされたサービスの更新

_2023 年 10 月 11 日_

![新しい問題](../assets/fix.svg)<!-- Issue PAY-4888 --> 現在は、商人はクレジットカードとデビットカードの取引を、 [トランザクションレポート](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html).

_2023 年 7 月 13 日_

![修正された問題](../assets/fix.svg)<!-- Issue PAY-4587 --> 支払いサービス 2.1.0 リリースで発生した、以前の拡張バージョンで置かれた認証の無効化を妨げていた問題が解決されました。 どのバージョンの支払いサービスを使用しているマーチャントも、認証を無効にすることができます。

_2023 年 6 月 10 日_

![新規](../assets/new.svg)<!-- Issue PAY-4288 --> 現在、商人は [設定 _のみ_ PayPal の支払いボタン](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#use-only-paypal-payment-buttons) — そして _not_ PayPal クレジットカードの支払いオプションを使用します。 これにより、商人は Venmo や PayPal の支払いボタンを含む様々な支払いオプションを提供し、PayPal のクレジットカード支払いオプションの代わりに既存のクレジットカードプロバイダを使用することができます。

![新規](../assets/new.svg)<!-- Issue PAY-4050 --> が追加されました。 [データビジュアライゼーション表示](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#order-payment-status-data-visualization-view)（注文の支払ステータスレポートに対して「支払サービスホーム」に表示されます）

![修正された問題](../assets/fix.svg)<!-- Issue PAY-4486--> 以前は、PayPal の PayLater ボタンは英国の商人のチェックアウトには表示されませんでした。 その問題は解決しました。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-4485--> 支払サービスが無効な場合、レポートのデータ視覚化ビューが支払サービスホームに表示されるようになりました。

_2023 年 1 月 26 日_

![既知の問題](../assets/bug.svg)<!-- Issue PAY-4102 --> 支払いサービスの新規インストールでコマースサービスを構成できず、支払いサービスが操作できなくなりました。 この問題を修正するには、Payment Services 拡張機能をバージョン 1.5.3 に更新してください。

_2022 年 9 月 13 日_

![新規](../assets/new.svg)<!-- Issue PAY-3705 --> The `increment_id` は、外部 ERP システムでの支払いの調整に使用できるようになりました。 これは、 [`custom_id` _および_ `invoice_id`](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/data.html#reconcile-with-erp-system)。PayPal Webhook と、支払のマーチャント活動の詳細の両方に表示されます。

_2022 年 8 月 31 日_

![修正された問題](../assets/fix.svg)<!-- Issue PAY-3629 --> 新しい商人が初めて支払サービスホームにアクセスすると、ページの更新を必要とせずに、ページが即座に読み込まれてコンテンツが表示されるようになりました。

_2021 年 8 月 10 日_

![新規](../assets/new.svg)<!-- Issue PAY-3420 --> Apple Pay が PayPal のスマートボタンとして利用できるようになりました。 この [支払いオプション](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-options.html#apple-pay-button) を使用すると、iOSまたはmacOSデバイスでタッチ ID 機能を使用してApple Pay を選択できます。 Apple Pay は、デバイスに保存されたクレジットカードおよびデビットカードの支払資格情報を使用して支払を処理します。

_2021 年 6 月 29 日_

![新規](../assets/new.svg)<!-- Issue PAY-1720 --> 店舗注文に関する紛争は、 [注文の支払い状況レポート](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#view-disputes). PayPal Resolution Center に直接アクセスして、紛争に対する対処を行うことができます。 [!DNL Payment Services].

![新規](../assets/new.svg)<!-- Issue PAY-2854 --> 次のユーザーエクスペリエンスの改善： [!DNL Payment Services] ホームには、現在の継承レベルで設定を変更する機能や、ヘッダーとナビゲーションの表示を改善する機能が含まれます。

![新規](../assets/new.svg)<!-- Issue PAY-2854 --> サンドボックスモードから実稼動モードに切り替えた場合や、保存されていない更新を含むビューから移動しようとすると、警告が表示されるようになりました。

![新規](../assets/new.svg)<!-- Issue PAY-2761 --> これで、 [注文の支払いステータスレポート](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#show-and-hide-columns) そして [ペイアウトレポート](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/payouts.html#show-and-hide-columns) 列設定コントロールを使用して、列を表示または非表示にする。

+++

## v2.3.0

_2023 年 12 月 1 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg)<!-- PAY-4381 --> [支払いサービスでGraphQLの統合がサポートされました](https://developer.adobe.com/commerce/webapi/graphql/payment-services/). GraphQLが PayPal の支払いボタン、ホストフィールド、Apple Pay をサポートするようになり、支払いサービスはヘッドレスコマースの設定をサポートするようになりました。

## v2.2.1

_2023 年 9 月 28 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![修正された問題](../assets/fix.svg)<!-- Issue PAY-4870 --> 最新のリリースで拡張機能バージョンを送信する際、Storefront で新しいヘッダー属性が正しく入力されない問題を修正しました。 以前は、 `1.3.0` Commerce Services コネクタのリリースにより、 `User-Agent header` を Payment Services 拡張機能から削除します。

## v2.2.0

_2023 年 8 月 31 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg)<!-- PAY-4638 --> 追加された [Signifyd との統合](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/security-compliance/fraud-protection.html)：自動化された不正保護サービスを提供します。

![新規](../assets/new.svg)<!-- PAY-3981 --> [Apple Pay を別の支払いオプションに昇格しました](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html?lang=en#apple-pay-button)（PayPal の支払いボタン以外）を使用して、買い物客が支払いオプションを表示しやすくし、商人がApple Pay の配置とスタイル設定を制御できるようにします。

![新規](../assets/new.svg)<!-- PAY-4002 --> クレジットカードフィールドのチェックアウト時のユーザーエクスペリエンスが改善され、支払いアイコンの追加などのスタイル設定の強化により、買い物客の認知負荷が減り、コンバージョンが増加しました。

![新規](../assets/new.svg)<!-- PAY-4002 --> 商人が [支払いオプションの順序を並べ替える](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#payment-buttons) をクリックして特定の支払いオプションを優先します。 この機能は、チェックアウト時の会話率の向上を推奨します。

![新規](../assets/new.svg)<!-- PAY-4035 --> 新しい [トランザクションレポート](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html) 支払サービスの管理者ホームに対して、取引の認証率とネガティブな取引の傾向を明確に表示できるようにすることで、商人は店舗の状態を効果的に監視し、取引の問題を特定できます。

## v2.1.0

_2023 年 6 月 10 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg)<!-- Issue xxx --> Adobe Commerce 2.4.7-beta1 のサポートを追加しました。

![新規](../assets/new.svg)<!-- Issue xxx --> 追加済み [次の国および関連通貨での使用可能性](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#availability)：オーストラリア、フランス、英国。

![新規](../assets/new.svg)<!-- Issue PAY-4296 --> 追加済み [管理者ロール用のリソースの拡張](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-roles) 管理者ユーザーが顧客の注文を作成および管理でき、セールスメニューの支払いサービスを表示できるようにする。

![新規](../assets/new.svg)<!-- Issue PAY-4236 --> 追加済み [チェックアウト時にエラーが発生した注文を自動無効化](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/checkout.html#order-auto-voided-if-error).

![新規](../assets/new.svg)<!-- Issue PAY-4183 --> 次の機能を作成しました： [クレジット/デビットカードの支払いオプションボタンを表示](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#debit-or-credit-card-button) を「チェックアウト」ページに追加します。

## v2.0.0

_2023 年 3 月 11 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg)<!-- Issue PAY-4152 --> PHP 8.2 およびAdobe Commerce 2.4.6 のサポートを追加しました。PHP 7.x との互換性はありません。

## v1.6.1

_2023 年 3 月 11 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![修正点](../assets/fix.svg)<!-- Issue PAY-4226 --> 新しい支払いサービスマーチャントが管理でチェックアウトを使用できない問題を修正しました。 支払いサービスは、以前はコマース顧客 ID を使用していましたが、新規顧客には存在しません。

![修正点](../assets/fix.svg)<!-- Issue PAY-4205 --> 指定した配送先住所の州が、チェックアウト時に [PayPal オプション](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#paypal-smart-buttons). 現在は、顧客は、マーチャントの税設定でデフォルトとして設定されたもの以外の州に注文を発送することができます。

![修正点](../assets/fix.svg)<!-- Issue PAY-4202 --> お客様がカード保管機能を使用して、店舗の購入を完了したり、保管された支払い方法を削除したりできない問題を修正しました。 [の使用 `Authorize and Capture` 支払手続](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/production.html#set-payment-services-as-payment-method). 以前は、お客様が Vault に保存されたクレジットカードの使用または変更を試みると、「Provider Vault ID not found」（プロバイダー Vault ID が見つかりません）というエラーが表示されていました。

## v1.6.0

_2023 年 2 月 18 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg)<!-- Issue PAY-3540 --> 追加済み [欧州連合 (EU) および英国で取引を行う商人向けの PCI 3DS コンプライアンス機能](security.md#3ds). この追加のセキュリティ層は、購入者にクレジットカード発行者の認証を要求するので、オンライン詐欺を防ぐのに役立ち、EU（欧州連合）コンプライアンス規制の一部として必要になります。

![新規](../assets/new.svg)<!-- Issue PAY-3609 --> 次の機能を追加しました。 [管理でのカードの保管を有効にする](vaulting.md#use-vaulting-in-the-admin). これにより、マーチャントは管理者の顧客に対して、ヴォールトされた支払い方法を使用して注文を作成できます。

## v1.5.4

_2023 年 1 月 30 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![修正された問題](../assets/fix.svg)<!-- Issue PAY-4110 --> 購入者が製品ページ、ミニカート、買い物かごのスマートボタンを使用して注文できなかった問題を修正しました。 購入者は注文を正常に完了できるようになりました。

## v1.5.3

_2023 年 1 月 26 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![修正された問題](../assets/fix.svg)<!-- Issue PAY-4102 --> 後方互換性のない既知の問題の修正をリリースしました。 このリリースでは、サービス ID 拡張バージョンが最新の安定したバージョンにロックされ、新しい支払いサービスのインストールでコマースサービスを構成できるようになります。

## v1.5.2

_2022 年 12 月 22 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![修正された問題](../assets/fix.svg)<!-- Issue PAY-3992 --> 支払い方法が拒否された場合の支払いサービスの請求を改善しました。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-3999 --> Payment Services で、PayPal のスマートボタンが [Fire Checkout&#39;s](https://commercemarketplace.adobe.com/swissup-firecheckout.html){target=_blank} チェックアウトページのカスタムテンプレート。 以前は、ミニカートがボタンを断続的に表示していました。

## v1.5.1

_2022 年 11 月 24 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg)<!-- Issue PAY-3923 --> 支払いサービスで、未使用のエンドポイントを追跡、フィルタリングまたは廃止するためのリクエストのバージョン番号がユーザーエージェントヘッダーに含まれるようになりました。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-3968 --> スマートボタンを使用して製品ページから注文が行われた場合、支払サービスで注文データが正しく表示されるようになりました。

## v1.5.0

_2022 年 11 月 19 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg)<!-- Issue PAY-3880 --> 買い物客は今、 [チェックアウト時にクレジットカード情報を保管（保存）](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html) 同じ商人アカウント内の同じ店舗または別の店舗に対して後での購入で使用する

![新規](../assets/new.svg)<!-- Issue PAY-3950 --> 商人は、 [即時購入コマース機能](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/checkout-instant-purchase.html) 買い物客が ( [入金済みのクレジットカード情報](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html)) をクリックして、チェックアウトを迅速に行います。

## v1.4.1

_2022 年 10 月 15 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![修正点](../assets/fix.svg)<!-- Issue PAY-3766 --> 顧客の支払い方法が拒否された場合、表示されるエラーメッセージの内容がよりわかりやすくなります。 お客様に、支払い情報を再入力して、もう一度やり直すか、別の支払い方法を試すか、拒否された取引について銀行に問い合わせるよう勧めます。

## v1.4.0

_2022 年 9 月 31 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg)<!-- Issue PAY-784 --> 支払いサービスには、次のようなマーチャントアカウントを設定する機能が含まれるようになりました。 [複数の PayPal ビジネスアカウントを使用する](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#use-multiple-paypal-accounts). これにより、マーチャントは異なる通貨を使用して複数の国で店舗を運営したり、ビジネスの一部にAdobe Commerceを使用したりできます。

![新規](../assets/new.svg)<!-- Issue PAY-3231 --> 商人は次のことができます。 [を追加します。 [!UICONTROL Soft Descriptor]](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#add-soft-descriptor) 顧客取引銀行明細書に表示され、ブランド、店舗、または製品ラインを説明する web サイトまたは個々の店舗ビュー構成。

![新規](../assets/new.svg)<!-- Issue PAY-3707 --> [クレジットカードフィールドと PayPal スマートボタンの有効化/無効化](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-payment-options) をクリックして、支払いサービス設定のチェックアウトを行います。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-3546 --> 顧客が **[!UICONTROL Edit cart]**&#x200B;をクリックした場合、ページは買い物かごページにリダイレクトされ、空の買い物かごを表示する代わりに、更新された項目が表示されます。

## v1.3.1

_2022 年 9 月 7 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![修正された問題](../assets/fix.svg)<!-- Issue PAY-3663 --> これで、マーチャントのストアが非グローバル通貨で許可された注文を取得すると、取得プロセスが完了し、エラーは表示されません。

## v1.3.0

_2022 年 8 月 10 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg)<!-- Issue PAY-XX --> GA リリース —[!DNL Payment Services] は今 [サポート対象： [!DNL Adobe Commerce] および [!DNL Magento Open Source] バージョン 2.4.0 ～ 2.4.5](https://devdocs.magento.com/release/availability.html#compatibility).

![修正された問題](../assets/fix.svg)<!-- Issue PAY-x --> Apple Pay は、モバイルおよびデスクトップ上の Safari ブラウザー v15.5 と互換性があるようになりました。

## v1.2.0

_2022 年 6 月 30 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![既知の問題](../assets/bug.svg)<!-- Issue PAY-x --> Apple Pay は、モバイルおよびデスクトップ上の Safari ブラウザー v15.5 と互換性がありません。 Safari バージョン 15.5 を使用している場合、Apple Pay でチェックアウトを完了できません。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-3264 --> 以前は、ログインしたユーザーが自分のアカウントにデフォルトの住所以外の別の請求先/配送先住所を選択した場合、チェックアウトに失敗していました。 この問題を修正し、選択した請求先/配送先住所（デフォルトの保存済み住所ではなく）が送信され、チェックアウトが正常に完了しました。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-3314 --> PayPal のスマートボタンをチェックアウト用に無効にした場合、エラーは表示されません。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-3330 --> ゲストユーザーがダッシュを含む電話番号を入力した場合に、チェックアウト中に支払いが失敗することはなくなりました。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-3338 PAY-2502 --> Commerce Services の資格情報が無効な場合、 [!DNL Payment Services] これで、管理画面にホームが表示されます。 資格情報エラーが表示され、資格情報が無効であることが警告されます。

![既知の問題](../assets/bug.svg)<!-- Issue PAY-0 --> [!DNL Payment Services] は現在、 `commerce-data-export` v101.20 以降 ( [[!DNL Channel manager] 拡張](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/guide-overview.html).

## v1.1.0

_2022 年 3 月 31 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg)<!-- Issue PAY-2127 --> GA リリース —[!DNL Payment Services] は今 [サポート対象： [!DNL Adobe Commerce] および [!DNL Magento Open Source] バージョン 2.4.0 ～ 2.4.4](https://devdocs.magento.com/release/availability.html#compatibility).

![新規](../assets/new.svg)<!-- Issue PAY-2682 --> The [!DNL Payment Services] 拡張 [!DNL Adobe Commerce] および [!DNL Magento Open Source] は現在、カナダの商人が利用できます。 商人は次のいずれかで支払の構成を表示できます： [フランス語](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=fr#carte-de-cr%C3%A9dit-et-devises-accept%C3%A9es) または [英語](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#accepted-credit-cards-and-currencies).

![新規](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] サポート [カナダドル (CAD)](overview.md#accepted-credit-cards-and-currencies) クレジットカードと PayPal トランザクションの場合。

![新規](../assets/new.svg)<!-- Issue PAY-2680 --> 商人は次のことができます。 [オンボード [!DNL Payment Services]](onboard.md) 英語またはフランス語の言語の拡張。

![新規](../assets/new.svg)<!-- Issue PAY-2678 --> マーチャントは、現在、 [注文の支払いステータス](order-payment-status.md) および [ペイアウトレポート](payouts.md)、カナダドル (CAD)。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-2710 --> [!DNL Payment Services] は現在、 [PHP 8.1](https://www.php.net/releases/8.1/en.php).

![修正された問題](../assets/fix.svg)<!-- Issue PAY-3017 --> サンドボックスモードのアラートが改善され、複数のストアで適切なアラートを表示するようになりました。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-2742 --> ストア表示レベルで、Venmo などの利用可能な支払い方法を有効または無効にできるようになりました。 以前は、Web サイトごとに支払い方法を設定することができました。

![修正された問題](../assets/fix.svg)<!-- Issue PAY-2277 --> 次に、選択的に [個々の PayPal スマートボタンの有効化または無効化](settings.md#payment-buttons).

![修正された問題](../assets/fix.svg)<!-- Issue PAY-2561 --> 以前に削除した製品は、 _注文を確認_ ページに貼り付けます。

![既知の問題](../assets/bug.svg)<!-- Issue PAY-2842 --> クレジットカードトランザクションのテスト [PayPal で失敗する場合があります](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html) サンドボックス環境で支払いを処理する場合。

## v1.0.0

_2021 年 11 月 30 日_

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg)<!-- Issue PAY-2127 --> GA リリース —[[!DNL Payment Services]](https://commercemarketplace.adobe.com/magento-payment-services.html) がでサポートされるようになりました。 [!DNL Adobe Commerce] および [!DNL Magento Open Source] バージョン 2.4.0 から 2.4.3-p1。

![新規](../assets/new.svg)<!-- Issue PAY-124 --> The [!DNL Payment Services] 拡張 [!DNL Adobe Commerce] および [!DNL Magento Open Source] 次のどちらかに対してインストールできます。 [[!DNL Adobe Commerce] クラウドインフラストラクチャ](install.md#adobe-commerce-on-cloud-infrastructure) または [オンプレミス](install.md#on-premises) インスタンス。 これらのメソッドでは、コマンドラインインターフェイスを使用する必要があります。

![新規](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] を支持する [サンドボックスアカウント](sandbox.md) これにより、マーチャントは拡張機能をテストモードで評価できます。

![新規](../assets/new.svg)<!-- Issue PAY-666 --> 商人は次のことができます。 [支払サービスの設定](settings.md) 基本的な支払い行動を伴う拡張（利用など） [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) サンドボックス環境または実稼動環境の切り替え。

![新規](../assets/new.svg)<!-- Issue PAY-780 --> 買い物客は、 [!DNL Payment Services] または経由 [手動オーダー作成](create-order.md).

![新規](../assets/new.svg)<!-- Issue PAY-1856 --> 包括的なレポート（を使用） [注文の支払いステータス](order-payment-status.md) および [ペイアウトレポート](payouts.md)、で使用できます。 [!DNL Payment Services] 店舗の注文と関連する支払いを明確に表示するために。

![新規](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] は、あらゆる商人に合わせた、総処理量に基づく柔軟な階層型価格設定をサポートします。

![新規](../assets/new.svg)<!-- Issue PAY-1443 --> 簡単に [外観をカスタマイズする](payments-options.md) / PayPal スマートボタンとクレジットカードフィールド [!DNL Payment Services] 拡張子。

![既知の問題](../assets/bug.svg)<!-- Issue PAY-2473 --> 使用 [誤ったコンポーザーキー](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html) 拡張機能のインストール中に、ユーザーは [認証](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 正しい `MAGEID`.

![既知の問題](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] レポート [すぐに同期できない](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html).

![既知の問題](../assets/bug.svg)<!-- Issue PAY-2475 --> お使いの [PayPal サンドボックスアカウント](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html) 対象： [!DNL Payment Services] は、オンボーディング中にそのアカウントを作成した場合は検証できません。
