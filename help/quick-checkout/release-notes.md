---
title: '"[!DNL Quick Checkout] リリースノート"'
description: すべての [!DNL Quick Checkout] リリース。
source-git-commit: dc13c1e38c92341cfd3221a72e6568220b44690a
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 2%

---

# リリースノート

以下のリリースノートでは、 [!DNL Quick Checkout] およびを含めます。

![新規](../assets/new.svg) 新機能
![修正された問題](../assets/fix.svg) 修正点および改善点
![既知の問題](../assets/bug.svg) 既知の問題

詳しくは、 [今後のリリース](https://devdocs.magento.com/release/) を参照してください。

詳しくは、 [可用性](https://devdocs.magento.com/release/availability.html) 製品の互換性について詳しくは、開発者向けドキュメントを参照してください。

## v1.0.0

![新規](../assets/new.svg)<!-- Issue BOLT-341 --> GA リリース —[[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) は、Adobe Commerceバージョン 2.4.1 ～ 2.4.4 と互換性があるようになりました。

![新規](../assets/new.svg)<!-- Issue BOLT-340 --> この [!DNL Quick Checkout] Adobe Commerce版は、Adobe Commerce版としてインストールできます [クラウドインフラストラクチャ](install.md#adobe-commerce-on-cloud-infrastructure) または [オンプレミス](install.md#on-premises) インスタンス。 これらのメソッドでは、コマンドラインインターフェイスを使用する必要があります。

![新規](../assets/new.svg)<!-- Issue BOLT-1 --> この [!DNL Quick Checkout] Adobe Commerceの場合は、 [ワンクリックチェックアウトエクスペリエンス](overview.md) を使用する場合、ユーザーに必要な入力フィールドはありません。

![新規](../assets/new.svg)<!-- Issue BOLT-1 --> この [!DNL Quick Checkout] for Adobe Commerceは、 [ワンクリック購入](checkout-flow.md) 直接アクセスできます。

![新規](../assets/new.svg)<!-- Issue BOLT-218 --> [!DNL Quick Checkout] (Adobe Commerceの場合はをサポート ) [サンドボックスアカウント](testing.md#testing-in-sandbox) これにより、マーチャントは拡張機能をテストモードで評価できます。

![新規](../assets/new.svg)<!-- Issue BOLT-780 --> 買い物客は、 [[!DNL Quick Checkout]](checkout-page.md) 拡張または経由 [手動オーダー作成](create-order-admin.md).

![新規](../assets/new.svg)<!-- Issue BOLT-666 --> マーチャントが [!DNL Quick Checkout] 次のような基本的な支払いアクションを持つ [`Authorize and Capture` または `Authorize` ](onboarding.md#complete-admin-configuration)、またはサンドボックスと実稼動環境を切り替えることができます。

![既知の問題](../assets/bug.svg)<!-- Issue BOLT-342 --> 使用 [誤ったコンポーザーキー](https://support.magento.com/hc/en-us/articles/6909450342541) ～の設置中に [!DNL Quick Checkout] ユーザーが [認証](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 正しい `MAGEID`.
