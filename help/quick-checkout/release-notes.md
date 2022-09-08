---
title: '[!DNL Quick Checkout] リリースノート'
description: すべての [!DNL Quick Checkout] リリース。
exl-id: 511be2fc-d24d-4323-a47a-d376e38a5c47
source-git-commit: 4dd8008901dbdbfaf1de5b1aa166dc70dd02440f
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 1%

---

# リリースノート

以下のリリースノートでは、 [!DNL Quick Checkout] およびを含めます。

![新規](../assets/new.svg) 新機能
![修正された問題](../assets/fix.svg) 修正点および改善点
![既知の問題](../assets/bug.svg) 既知の問題

詳しくは、 [今後のリリース](https://devdocs.magento.com/release/) を参照してください。

詳しくは、 [可用性](https://devdocs.magento.com/release/availability.html) 製品の互換性について詳しくは、開発者向けドキュメントを参照してください。

## v1.2.0

_2022 年 9 月 9 日_

![新規](../assets/new.svg)<!-- Issue BOLT-341 --> GA リリース —[[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) は、Adobe Commerceバージョン 2.4.5 と互換性があります。

![新規](../assets/new.svg)<!-- Issue BOLT-328 --> [!DNL Quick Checkout] Adobe Commerce版およびMagento Open Source版では、 [管理パネルビュー](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) と、拡張機能の設定と使用に必要なすべての情報を含んでいます。

![新規](../assets/new.svg)<!-- Issue BOLT-364 --> 管理者ユーザー [ユーザーの役割と権限を設定できます](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/user-roles-setup.html) 他のユーザーが [!DNL Quick Checkout] 管理パネル。

![新規](../assets/new.svg)<!-- Issue BOLT-377 --> [!DNL Quick Checkout] 管理パネルに、次のような特定のセクションを含むページヘッダーが追加されました。 **概要**, **レポート**、および **設定**.

![新規](../assets/new.svg)<!-- Issue BOLT-379 --> [!DNL Quick Checkout] 管理パネルにより、Gainsight を利用した機能ツアーを提供するようこそウィジェットが追加されます。

![新規](../assets/new.svg)<!-- Issue BOLT-378 --> [!DNL Quick Checkout] [管理パネルビュー](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) を組み込む **設定** API と公開可能なキーが [設定](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 表示

![新規](../assets/new.svg)<!-- Issue BOLT-380 --> [!DNL Quick Checkout] [管理パネルビュー](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) を組み込む **リソース** オンボーディングステージに応じて変わるセクション。

![新規](../assets/new.svg)<!-- Issue BOLT-381 --> [!DNL Quick Checkout] [管理パネルビュー](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) を含む **ヘルプとサポート** 」セクションに入力します。

![修正された問題](../assets/fix.svg)<!-- Issue BOLT-369 --> この [[!DNL Quick Checkout] 管理パネル](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) フッターに拡張機能のバージョンが表示されるようになりました。

## v1.1.0

_2022 年 8 月 13 日_

![修正された問題](../assets/fix.svg)<!-- Issue BOLT-375 --> のユーザーエクスペリエンスの改善 [[!DNL Quick Checkout] 管理パネル](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 拡張機能が有効になっている場合に表示および検証されるパラメーターのみを含めるようになりました。

![修正された問題](../assets/fix.svg)<!-- Issue BOLT-349 --> 既存の配送先住所と Bolt ウォレットの互換性を改善しました。

## v1.0.0

_2022 年 8 月 10 日_

![新規](../assets/new.svg)<!-- Issue BOLT-341 --> GA リリース —[[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) は、Adobe Commerceバージョン 2.4.1 ～ 2.4.4 と互換性があるようになりました。

![新規](../assets/new.svg)<!-- Issue BOLT-340 --> この [!DNL Quick Checkout] Adobe Commerce版は、Adobe Commerce版としてインストールできます [クラウドインフラストラクチャ](install.md#adobe-commerce-on-cloud-infrastructure) または [オンプレミス](install.md#on-premises) インスタンス。 これらのメソッドでは、コマンドラインインターフェイスを使用する必要があります。

![新規](../assets/new.svg)<!-- Issue BOLT-1 --> この [!DNL Quick Checkout] Adobe Commerceの場合は、 [ワンクリックチェックアウトエクスペリエンス](overview.md) を使用する場合、ユーザーに必要な入力フィールドはありません。

![新規](../assets/new.svg)<!-- Issue BOLT-1 --> この [!DNL Quick Checkout] for Adobe Commerceは、 [ワンクリック購入](checkout-flow.md) 直接アクセスできます。

![新規](../assets/new.svg)<!-- Issue BOLT-1 --> この [!DNL Quick Checkout] Adobe Commerceの場合、買い物客は同時に [Adobe Commerceと Bolt の両方のネットワークにログイン](checkout-flow.md/#quick-checkout-use-cases) より良い物を提供する `one-click checkout` エクスペリエンス。

![新規](../assets/new.svg)<!-- Issue BOLT-218 --> [!DNL Quick Checkout] (Adobe Commerceの場合はをサポート ) [サンドボックスアカウント](testing.md#testing-in-sandbox) これにより、マーチャントは拡張機能をテストモードで評価できます。

![新規](../assets/new.svg)<!-- Issue BOLT-780 --> 買い物客は、 [[!DNL Quick Checkout]](checkout-page.md) 拡張または経由 [手動オーダー作成](create-order-admin.md).

![新規](../assets/new.svg)<!-- Issue BOLT-666 --> マーチャントが [!DNL Quick Checkout] 次のような基本的な支払いアクションを持つ [`Authorize and Capture` または `Authorize` ](onboarding.md#complete-admin-configuration)、またはサンドボックスと実稼動環境を切り替えることができます。

![新規](../assets/new.svg)<!-- Issue BOLT-288 --> カスタム [ユーザーセッションの有効期間](user-session-lifetime.md) 対象 [!DNL Quick Checkout] Adobe Commerce

![修正された問題](../assets/fix.svg)<!-- Issue BOLT-375 --> のユーザーエクスペリエンスの改善 [[!DNL Quick Checkout] 管理パネル](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) を使用すると、必要なパラメーターがすべて指定された場合に設定を保存できます。

![既知の問題](../assets/bug.svg)<!-- Issue BOLT-342 --> 共通 [トラブルシューティング](https://support.magento.com/hc/en-us/articles/6909450342541) インストール中の問題 [!DNL Quick Checkout].
