---
title: セキュリティとコンプライアンス
description: サイトのセキュリティとコンプライアンス要件を確認します。
exl-id: 083c5a12-1d78-48b5-b9e3-612b104ce7e0
feature: Payments, Checkout, Compliance
redirect_from: https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/security.html
source-git-commit: 5fe23b5aba9ad0a2a6c995fa6ade78f46fe7e3e1
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 0%

---

# セキュリティとコンプライアンス

～には安全が最も重要である [!DNL Payment Services] また、お客様に対しては、プライベートまたは支払いカード業界 (PCI) の規制情報が渡されることはありません。 [!DNL Payment Services].

## コマースセキュリティ

[!DNL Adobe Commerce] および [!DNL Magento Open Source] いくつかのセキュリティ機能のサポートが含まれています。

詳しくは、 [セキュリティ](https://docs.magento.com/user-guide/stores/security.html){target="_blank"} セキュリティのベストプラクティスを確認し、管理者セッションと資格情報の管理、CAPTCHA の実装、web サイト制限の管理の方法を学ぶためのコアユーザーガイドです。

## PCI コンプライアンス

決済カード業界 (PCI) は、インターネットを介してクレジットカードによる支払いを受け入れる企業に対して一連の要件を定めました。 安全な環境の維持に加え、顧客のクレジットカード情報を扱う商人は、いくつかの標準的なガイドラインに従う責任を負います。

詳しくは、 [PCI コンプライアンスガイドライン](https://docs.magento.com/user-guide/stores/compliance-pci.html){target="_blank"} を参照してください。

マーチャントが [自己評価アンケート (SAQ)](https://www.pcisecuritystandards.org/pci_security/completing_self_assessment){target="_blank"}：カード所有者データのセキュリティを評価するための自己検証ツールです。

### クレジットカードのフィールド

クレジットカードフィールドを使用すると、PCI 規制のデータはサービスを通じて渡されません。 データの保存や保守を行う必要がなく、PCI への準拠に関する懸念が大幅に軽減されます。

### 3DS

PCI 3-D セキュア (3DS) は、オンラインでクレジットカードを購入する際に、クレジットカード発行者との購入者認証を可能にします。 この追加のセキュリティ層は、オンライン詐欺を防ぐのに役立ち、EU（欧州連合）コンプライアンス規制の一部として必要です。

[!UICONTROL Payment Services] は、3DS 機能を提供し、商人が EU 規制に準拠し、店舗での顧客や商人の不正行為を防ぐことを可能にします。

3DS への準拠が必要な EU または英国内の商人の場合は、手動で 3DS をオンにする必要があります ( `Off` デフォルトで ) [設定](settings.md#credit-card-fields).

>[!NOTE]
>
>3DS の要件は、ビジネスとカード所有者の銀行が [欧州経済圏](https://www.efta.int/eea) (EEA) と英国。 米国の商人は 3DS を必要としませんが、必要に応じて取引に対して有効にできます。

マーチャント/店舗担当者が購入者に対して行った注文は、3DS コンプライアンス対策で構成されていません。

詳しくは、 [3DS の設定](settings.md#3ds) を参照してください。

### カードの保管

買い物客が [クレジットカード情報を保管する（「保存する」）](vaulting.md) 店舗での今後の購入については、最小限のクレジットカード情報が買い物客（最後の 4 桁、カードの有効期限、カードのブランド）と共有されます。 クレジットカード情報は、支払いプロバイダーと共に保存されます。 カードの有効期限が切れたり、保存された情報が不要になった場合は、その情報を削除して、支払いプロバイダーが情報を保存しなくすることができます。

詳しくは、 [クレジットカードの保管](vaulting.md) を参照してください。

### PayPal の支払いボタン

PayPal の支払いボタンを使用すると、PCI 規制のデータがサービスを通じて渡されることはありません。 データの保存や保守を行う必要がなく、PCI への準拠に関する懸念が大幅に軽減されます。

セキュリティ上の理由から、PayPal はチェックアウト時に請求先住所を渡しません（国、E メール、名前は使用される唯一の請求情報です）。 必要に応じて、サイトの PayPal チェックアウトを有効にして、PayPal に問い合わせて、ベッティングプロセスを完了することで、完全な請求先住所を返すことができます。

また、PayPal は、機械学習を使用して詐欺との戦いに役立つ統合不正保護を備えています。 PayPal の「 [販売者保護ドキュメント](https://www.paypal.com/us/webapps/mpp/security/seller-protection) を参照してください。

## 不正の保護

支払いサービスの自動不正保護を有効にするには、 [Signifyd 拡張機能](https://commercemarketplace.adobe.com/signifyd-module-connect.html).

詳しくは、 [信頼できる不正保護](fraud-protection.md) を参照してください。

