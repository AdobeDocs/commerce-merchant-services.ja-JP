---
title: セキュリティとコンプライアンス
description: サイトのセキュリティとコンプライアンス要件を確認します。
exl-id: 083c5a12-1d78-48b5-b9e3-612b104ce7e0
source-git-commit: c993a2afe5b4da478ab57cbb391bb524d83c3d1a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# セキュリティとコンプライアンス

～は安全が最も重要である [!DNL Payment Services] また、お客様に対しては、プライベートまたは支払いカード業界 (PCI) の規制情報が渡されることはありません [!DNL Payment Services].

## コマースセキュリティ

[!DNL Adobe Commerce] および [!DNL Magento Open Source] いくつかのセキュリティ機能のサポートが含まれています。

詳しくは、 [セキュリティ](https://docs.magento.com/user-guide/stores/security.html)セキュリティのベストプラクティスを確認し、管理者セッションと資格情報の管理、CAPTCHA の実装、Web サイト制限の管理の方法を学ぶためのコアユーザーガイドの {target=&quot;_blank&quot;}。

## PCI コンプライアンス

決済カード業界 (PCI) は、インターネットを介してクレジットカードによる支払いを受け入れる企業に対して一連の要件を定めました。 安全な環境の維持に加え、顧客のクレジットカード情報を扱う商人は、いくつかの標準的なガイドラインに従う責任を負います。

詳しくは、 [PCI コンプライアンスガイドライン](https://docs.magento.com/user-guide/stores/compliance-pci.html){target=&quot;_blank&quot;} を参照してください。

商人が [自己評価アンケート (SAQ)](https://www.pcisecuritystandards.org/pci_security/completing_self_assessment){target=&quot;_blank&quot;}。カード所有者データのセキュリティを評価するための自己検証ツールです。

### クレジットカードのフィールド

クレジットカードフィールドを使用すると、PCI 規制のデータはサービスを通じて渡されません。 データの保存や保守を行う必要がなく、PCI への準拠に関する懸念が大幅に軽減されます。

### カードの保管

買い物客が [クレジットカード情報を保管する（「保存する」）](vaulting.md) 店舗での今後の購入については、最小限のクレジットカード情報が買い物客（最後の 4 桁、カードの有効期限、カードのブランド）と共有されます。 クレジットカード情報は、支払いプロバイダーと共に保存されます。 カードの有効期限が切れたり、保存された情報が不要になった場合は、その情報を削除して、支払いプロバイダーが情報を保存しなくすることができます。

### PayPal スマートボタン

PayPal スマートボタンを使用すると、PCI 規制のデータがサービスを通じて渡されることはありません。 データの保存や保守を行う必要がなく、PCI への準拠に関する懸念が大幅に軽減されます。

セキュリティ上の理由から、PayPal はチェックアウト時に請求先住所を渡しません（国、E メール、名前は使用される唯一の請求情報です）。 必要に応じて、サイトの PayPal チェックアウトを有効にして、PayPal に問い合わせて、ベッティングプロセスを完了することで、完全な請求先住所を返すことができます。

また、PayPal は、機械学習を使用して詐欺との戦いに役立つ統合不正保護を備えています。 PayPal の「 [販売者保護ドキュメント](https://www.paypal.com/us/webapps/mpp/security/seller-protection) を参照してください。
