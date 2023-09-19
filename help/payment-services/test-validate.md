---
title: テストと検証
description: テストと検証は、 [!DNL Payment Services] 機能が期待どおりに動作し、顧客に最適な支払いオプションを提供する
exl-id: 95b4615e-73b0-41e8-83e2-e65a0b22f10f
feature: Payments, Checkout
source-git-commit: 75ff893bf5867ededa49807835676ddf9b19adc9
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---

# テストと検証

公開する前に [!DNL Payment Services] 対象： [!DNL Adobe Commerce] および [!DNL Magento Open Source] 買い物客にとって、サンドボックス環境でテストすることをお勧めします。 _および_ 実稼動環境で テストと検証は、 [!DNL Payment Services] 機能は期待どおりに動作し、お客様の店舗や顧客に最適な支払いオプションを提供します。

## サンドボックス環境でテスト

テスト [!DNL Payment Services] サンドボックス環境は、実際の銀行や商人には接続されていない PayPal サンドボックスにのみ接続されたシミュレーション環境である場合でも、重要な検証手順です。

1. ストアのチェックアウトが成功したら、 [クレジットカードのフィールド](payments-options.md#credit-card-fields) または [PayPal スマートボタン](payments-options.md#paypal-smart-buttons). 詳しくは、 [資格情報のテスト](#testing-credentials) を参照してください。
1. キャプチャ ( 支払いアクションが [に設定 `Authorize and Capture`](onboard.md#set-payment-services-as-payment-method)), [払い戻し](refunds.md)または [ボイド](voids.md) 注文が完了しました。 また、 [請求書の作成](https://docs.magento.com/user-guide/sales/invoice-create.html){target="_blank"} 注文の場合、支払い処理が `Authorize` の代わりに `Authorize and Capture`.
1. 24 ～ 48 時間以内に、トランザクションおよびその他の情報を [ペイアウトレポート](payouts.md).
1. 注文の詳細を [注文の支払いステータスレポート](order-payment-status.md).

### 資格情報のテスト

サンドボックスをテストおよび検証する際は、既存のクレジットカードアカウントに対する実際の料金を作成しないように、偽のクレジットカード番号を使用する必要があります。

PayPal のクレジットカードジェネレーターを使用して [ランダムクレジットカード情報を生成する](https://www.paypal.com/us/smarthelp/article/where-can-i-find-test-credit-card-numbers-ts2157) （テスト用）

Apple Pay をサンドボックスモードでテストするには：

* の作成 [Apple sandbox テスターアカウント](https://developer.apple.com/apple-pay/sandbox-testing/#create-a-sandbox-tester-account)（偽のクレジットカードと請求情報を含む）
* [サンドボックスドメインを登録](https://developer.paypal.com/docs/checkout/apm/apple-pay/#link-registeryoursandboxdomains).

>[!NOTE]
>
>PayPal のサンドボックス支払い処理が遅くなる場合があり、サービスが停止する場合があります。 この状況は、ライブ製品の支払い処理の速度と効率を示すものではありません。

## 本番でテスト

テストを実施することを強くお勧めします。 [!DNL Payment Services] 実稼働環境では、実際のクレジットカードと銀行を使用して、この機能を買い物客に公開します。 テスト中でも [!DNL Payment Services] サンドボックスでは、実稼働環境でのテストは、 [!DNL Payment Services] は期待どおりに動作します。

テスト可能 [!DNL Payment Services] 次の 2 つの方法のいずれかを実稼動環境で使用します。

* 買い物客が注文しないことがわかっている時間を選択します。
* 買い物客が一時的にアクセスできないが、テスト用にアクセスできる Web ストアを使用します。

実際のクレジットカードと PayPal アカウントを使用して本番テストを完了し、キャプチャと返金を含む支払いのライフサイクル全体をテストします。 テスト中にチェックアウトおよび支払いフロー全体を完了すると、 [!DNL Payment Services] 機能は、ライブ買い物客が使用している場合に機能します。

また、生産テストで使用する支払い方法に関する銀行取引明細書に表示される情報が正しく、期待されるもの（お客様のビジネスの説明を含む）であることを確認する必要があります。

Apple Pay を実稼働モードでテストするには、次の手順を実行する必要があります。 [実稼動ドメインを登録](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain).
