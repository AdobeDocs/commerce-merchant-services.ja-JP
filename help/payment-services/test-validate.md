---
title: テストと検証
description: テストと検証は、 [!DNL Payment Services] 機能が期待どおりに動作し、顧客に最適な支払いオプションを提供する
exl-id: 95b4615e-73b0-41e8-83e2-e65a0b22f10f
source-git-commit: bcb817775fe9cd9ac7096931dd40d5ec0c4a5cfc
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# テストと検証

公開する前に [!DNL Payment Services] Adobe Commerceと買い物客のMagento Open Sourceについては、サンドボックス環境でテストすることをお勧めします。 _および_ 実稼動環境で テストと検証は、 [!DNL Payment Services] 機能は期待どおりに動作し、お客様の店舗や顧客に最適な支払いオプションを提供します。

## サンドボックス環境でテスト

テスト [!DNL Payment Services] サンドボックス環境は、実際の銀行や商人には接続されていない PayPal サンドボックスにのみ接続されたシミュレーション環境である場合でも、重要な検証手順です。

1. ストアのチェックアウトが成功したら、 [クレジットカードのフィールド](payments-options.md#credit-card-fields) または [PayPal スマートボタン](payments-options.md#paypal-smart-buttons). 詳しくは、 [サンドボックスモードを使用](#use-sandbox-mode) を参照してください。
1. キャプチャ ( 支払いアクションが [に設定 `Authorize and Capture`](onboard.md#set-payment-services-as-payment-method)), [払い戻し](refunds.md)または [ボイド](voids.md) 完了した注文。 また、 [請求書の作成](https://docs.magento.com/user-guide/sales/invoice-create.html){target=&quot;_blank&quot;}( 支払い処理が `Authorize` の代わりに `Authorize and Capture`.
1. 24 ～ 48 時間以内に、トランザクションおよびその他の情報を [ペイアウトレポート](payouts.md).
1. 注文の詳細を [注文の支払いステータスレポート](order-payment-status.md).

### サンドボックスモードを使用

サンドボックスをテストおよび検証する際は、既存のクレジットカードアカウントに対する実際の料金を作成しないように、偽のクレジットカード番号を使用する必要があります。

PayPal のクレジットカードジェネレーターを使用して [ランダムクレジットカード情報を生成](https://www.paypal.com/us/smarthelp/article/where-can-i-find-test-credit-card-numbers-ts2157) テスト用。

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
