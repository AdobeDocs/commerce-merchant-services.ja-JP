---
title: 「 [!DNL Quick Checkout] for Adobe Commerce extension"
description: 「テストと検証により、 [!DNL Quick Checkout] 拡張機能は期待どおりに動作します。」
exl-id: 308f39e1-e2f6-40d8-b876-0f9013effed3
feature: Checkout, Services
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---


# をテストします。 [!DNL Quick Checkout] 拡張

を公開する前に、 [!DNL Quick Checkout] 買い物客に対するAdobe Commerce拡張機能の場合は、サンドボックス環境と実稼動環境でテストすることをお勧めします。 テストと検証は、 [!DNL Quick Checkout] は期待どおりに動作し、ストアや顧客に対してシームレスなチェックアウトエクスペリエンスを提供します。

設定する前に、 [!DNL Quick Checkout] Adobe Commerce Admin で、  [実稼動](https://merchant.bolt.com/register){target="_blank"} and [sandbox](https://merchant-sandbox.bolt.com/register){target="_blank"} ～の商人口座 [!DNL Bolt].

## サンドボックスでのテスト

のテスト [!DNL Quick Checkout] サンドボックス環境は、 [!DNL Bolt] サンドボックスアカウント。実際の銀行や商人には割り当てられません。

### Sandbox アカウントの使用

サンドボックスをテストおよび検証する際は、偽のクレジットカード番号と [sandbox](https://merchant-sandbox.bolt.com/register){target="_blank"} ～の商人口座 [!DNL Bolt]既存のクレジットカードアカウントに対して実際の料金を作成しないようにします。

## 実稼動環境でのテスト

>[!NOTE]
>
> をテストすることを強くお勧めします。 [!DNL Quick Checkout] 実稼動環境では、実際のクレジットカードと銀行を使用して、買い物客に公開する前に、拡張機能を使用します。 サンドボックスでのテストが重要ですが、実稼働環境でのテストは、期待どおりに動作することを確認する最も愚かな方法です。

実稼動環境をテストするには、次の 2 つの方法のいずれかを使用します。

- 買い物客が注文しないことがわかっている時間を選択します。
- 買い物客が一時的にアクセスできないが、テスト用にアクセスできる Web ストアを使用します。

実際のクレジットカードを使用して実稼動テストを完了し、 [!DNL Bolt] 実稼動アカウント、チェックアウトのライフサイクル全体をテストする。 テスト中にチェックアウトフロー全体を完了すると、ライブ買い物客が使用した場合の機能の仕組みを明確に示します。

また、生産テストで使用する支払い方法に関する銀行取引明細書に表示される情報が正しく、期待されるもの（お客様のビジネスの説明を含む）であることを確認する必要があります。

## テスト方法 [!DNL Quick Checkout] 拡張

ストアからのチェックアウトが正常に完了したことを確認します。

1. ストアフロントに移動し、カートに必要な項目を配置します。
1. チェックアウトに進みます。
1. 次に関連する電子メールアドレスを入力 [!DNL Bolt] アカウントに問い合わせるプロンプトが表示されます。
1. アカウントの電子メールアドレスに送信するワンタイムパスワード (OTP) を入力します。
1. 環境ダッシュボードを選択します。

   - サンドボックス
   - 実稼動

1. 注文を行います。

注文が完了すると、注文の詳細を _注文グリッド_ 表示：

1. に移動します。 _セールス_ > _購入回数_.
1. すべての注文のリストを表示します。

詳しくは、 [購入回数](https://docs.magento.com/user-guide/sales/orders.html) のトピックを参照してください。 _注文グリッド_ 表示。
