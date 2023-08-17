---
title: '[!DNL Quick Checkout] リリースノート'
description: すべての [!DNL Quick Checkout] リリース。
exl-id: 511be2fc-d24d-4323-a47a-d376e38a5c47
feature: Release Notes, Services, Checkout
source-git-commit: 0c8d9498ea7a30a99f834694ef8a865ad24466ab
workflow-type: tm+mt
source-wordcount: '1422'
ht-degree: 0%

---

# リリースノート

以下のリリースノートでは、 [!DNL Quick Checkout] およびを含めます。

![新規](../assets/new.svg) 新機能
![修正された問題](../assets/fix.svg) 修正点および改善点
![既知の問題](../assets/bug.svg) 既知の問題

詳しくは、 [今後のリリース](https://devdocs.magento.com/release/) を参照してください。

詳しくは、 [可用性](https://devdocs.magento.com/release/availability.html) 製品の互換性について詳しくは、開発者向けドキュメントを参照してください。

## 管理パネルのアップデート

これらのリリースノートでは、管理パネルの通常のバージョン管理機能リリース以外でリリースされた、機能の変更点と修正点について説明します。

+++管理パネルのアップデート

2023 年 5 月 23 日_

![修正された問題](../assets/fix.svg)<!-- Issue BOLT-489 --> さて、 **新規アカウント** コンポーネント [!DNL Quick Checkout] レポートページにはスペクトルが含まれます [ワークフローアイコン](https://react-spectrum.adobe.com/react-spectrum/workflow-icons.html){target=_blank}.

_2023 年 4 月 26 日_

![修正された問題](../assets/fix.svg)<!-- Issue BOLT-452 --> The [!DNL Quick Checkout] **ツアーを見る** ボタンにカーソルを合わせると、クリック可能なハンドカーソルが表示されるようになりました。

_2023 年 4 月 20 日_

![修正された問題](../assets/fix.svg)<!-- Issue BOLT-596 --> The [!DNL Quick Checkout] 日付を ISO 8601 形式に解析する際、レポートページに新しいアカウントのグラフが正しく表示されるようになりました。

_2022 年 12 月 14 日_

![修正された問題](../assets/fix.svg)<!-- Issue BOLT-524 --> The [!DNL Quick Checkout] 管理パネルに、正しい合計注文件数と更新されたレポート情報が表示されるようになりました。

_2022 年 11 月 31 日_

![新規](../assets/new.svg)<!-- Issue BOLT-502 --> さて、 [レポート](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) タブには、新しい「昨年」プリセットがあります。

![新規](../assets/new.svg)<!-- Issue BOLT-471 --> のユーザーエクスペリエンスの改善 [!DNL Quick Checkout] 管理パネルに詳細情報を表示： [ツールチップ](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html).

![修正された問題](../assets/fix.svg)<!-- Issue BOLT-514 --> のユーザーエクスペリエンスの改善 [!DNL Quick Checkout] 管理パネルには、正しい合計注文数、色の一貫性、すべてのグラフの正しい凡例が表示されます。

_2022 年 11 月 3 日_

![新規](../assets/new.svg)<!-- Issue BOLT-293 --> さて、 [レポート](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) 」タブをクリックします。 [!DNL Quick Checkout] 管理パネルには、ストアのチェックアウトエクスペリエンス統計のグラフとレポート情報が表示されます。

![新規](../assets/new.svg)<!-- Issue BOLT-422 --> The [_概要_](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#reports-overview) 「レポート」トピックセクションの「 」セクションには、ストアのチェックアウトパフォーマンスに関する詳細情報が表示されます。これには、平均チェックアウト時間、チェックアウト中に作成された新しいアカウント、チェックアウトの中断などが含まれます。

![新規](../assets/new.svg)<!-- Issue BOLT-423 --> The [_トレンド_](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#reports-trends) 「レポート」タブの「 」セクションには、チェックアウト時に作成されたアカウントタイプおよび新しいアカウント別にフィルタリングしたチェックアウトエクスペリエンスのトレンドが表示されます。

![新規](../assets/new.svg)<!-- Issue BOLT-439 --> The **レポート** タブ表示 [デフォルトのフィルタープリセット](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#filter-data) を使用して、特定のデータ範囲を表示できます。

![新規](../assets/new.svg)<!-- Issue BOLT-433 --> これで、 _データがありません_ リクエストがデータを返さない場合のグラフに関する警告

![新規](../assets/new.svg)<!-- Issue BOLT-473 --> 次の機能を使用してユーザーエクスペリエンスを改善： [!DNL Quick Checkout] 管理パネルには、 [チェックアウトトラッキング](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/settings-quick-checkout.html#service-settings) Adobe Commerceがレポート情報を Bolt と共有できるようにする設定。

_2022 年 10 月 6 日_

![新規](../assets/new.svg)<!-- Issue BOLT-379 --> さて、新しい商人が [!DNL Quick Checkout] 初めての管理パネル [Gainsight を活用した機能ツアー](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) が表示されます。

![新規](../assets/new.svg)<!-- Issue BOLT-377 --> The **レポート** 」タブをクリックします。 [!DNL Quick Checkout] 管理パネルにグラフとレポート分析が表示されます。

![新規](../assets/new.svg)<!-- Issue BOLT-377 --> The **レポート** 」タブをクリックします。 [!DNL Quick Checkout] 管理パネルには、グラフおよびレポート分析用の日付範囲およびフィルタープリセットが表示されます。

![修正された問題](../assets/fix.svg)<!-- Issue BOLT-369 --> さて、 [[!DNL Quick Checkout] 管理パネル](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) フッターにアプリのバージョンを表示します。

+++

## v1.8.0

_2023 年 2 月 25 日_

[!BADGE 互換性]{type=Informative tooltip="互換性"}

![新規](../assets/new.svg)<!-- Issue BOLT-520 --> GA リリース —[[!DNL Quick Checkout]](https://commercemarketplace.adobe.com/magento-quick-checkout.html) は、Adobe Commerce Cloudバージョン 2.4.6 以降にプリインストールされるようになりました。

![修正された問題](../assets/fix.svg)<!-- Issue BOLT-592 --> 注文を [管理パネル](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/create-order-admin.html) using [Braintree](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/stored-payment-methods.html) 支払い方法として。 この機能を使用すると、顧客は、チェックアウト時にBraintreeを支払い方法として注文を行うことができます。 [!DNL Quick Checkout] が有効になっている。

## v1.7.0

_2023 年 2 月 23 日_

[!BADGE 互換性]{type=Informative tooltip="互換性"}

![修正された問題](../assets/fix.svg)<!-- Issue AC-8002 --> を使用して注文を行う際のユーザーエクスペリエンスの改善 [Multishipping](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/multishipping-settings.html) メソッド。 この機能により、チェックアウト時に支払い方法を [!DNL Quick Checkout] が有効になっている。

## v1.6.0

_2023 年 2 月 10 日_

[!BADGE 互換性]{type=Informative tooltip="互換性"}

![修正された問題](../assets/fix.svg)<!-- Issue BOLT-567 --> 次の場合のユーザーエクスペリエンスの改善 [注文の実施](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) の使用 [店舗での配信](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/delivery/basic-methods/shipping-in-store-delivery.html) メソッドの [!DNL Quick Checkout] 無効。

![修正された問題](../assets/fix.svg)<!-- Issue BOLT-569 --> ログアウト機能を改善し、買い物客が次の操作を実行できるようにしました。 [Bolt Network からログアウトする](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/user-session-lifetime.html).

## v1.5.0

_2023 年 1 月 19 日_

[!BADGE 互換性]{type=Informative tooltip="互換性"}

![新規](../assets/new.svg)<!-- Issue BOLT-522 --> 新しい設定を有効/無効にして、 [買い物客](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/manage-checkout/checkout-options/checkout-adobe-commerce.html) は自動的に Bolt にログインできます。

![新規](../assets/new.svg)<!-- Issue BOLT-523 --> 新しい設定を有効/無効にすると、商人は買い物客を両方のネットワークに自動的にログインできるか、Bolt ネットワークにのみログインできるかを指定できます。

![修正された問題](../assets/fix.svg)<!-- Issue BOLT-542 --> 次の場合のユーザーエクスペリエンスの改善 [Bolt アカウントへのカードまたは住所の保存](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) 買い物客が電子メールを提供したとき。

![修正された問題](../assets/fix.svg)<!-- Issue BOLT-550 --> のユーザーエクスペリエンスの改善 [自動ログイン](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#configure-service-settings) Bolt ユーザが電子メールを入力したとき。

![修正された問題](../assets/fix.svg)<!-- Issue BOLT-544 --> の互換性の改善 [コールバック URL](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#check-shopper-valid-account) 次を使用 [マルチサイト](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/multi-sites/ms-overview.html) Bolt 内

## v1.4.0

_2022 年 11 月 31 日_

[!BADGE 互換性]{type=Informative tooltip="互換性"}

![新規](../assets/new.svg)<!-- Issue BOLT-513 --> これで、Adobe Commerceの顧客がチェックアウトプロセス中にストアにログインし、Bolt アカウントを持っている場合に、買い物客の Bolt アカウントにログインするためのオプションが表示されます。

![新規](../assets/new.svg)<!-- Issue BOLT-512 --> 新しい設定では、ログインした買い物客が Bolt にログインできるかどうかを自動的に検出します。

![新規](../assets/new.svg)<!-- Issue BOLT-480 --> 新しい設定 ( [!DNL Quick Checkout] 管理パネルでは、デフォルトのナビゲーションフローを **送料** Bolt のお客様がログインした後にページを開きます。 デフォルトでは、 **支払い** ページに貼り付けます。

## v1.3.0

_2022 年 11 月 3 日_

[!BADGE 互換性]{type=Informative tooltip="互換性"}

![新規](../assets/new.svg)<!-- Issue BOLT-293 --> さて [!DNL Quick Checkout] を有効にする機能が含まれる [チェックアウトトラッキング](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/settings-quick-checkout.html#service-settings) Adobe Commerceがレポート情報を Bolt と共有できるようにする設定。

![新規](../assets/new.svg)<!-- Issue BOLT-461 --> これで、 [!DNL Quick Checkout] 次の場合は管理パネル [チェックアウトトラッキング](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) 設定が無効です。

## v1.2.0

_2022 年 9 月 9 日_

[!BADGE 互換性]{type=Informative tooltip="互換性"}

![新規](../assets/new.svg)<!-- Issue BOLT-341 --> GA リリース —[[!DNL Quick Checkout]](https://commercemarketplace.adobe.com/magento-quick-checkout.html) は、Adobe Commerceバージョン 2.4.5 と互換性があります。

![新規](../assets/new.svg)<!-- Issue BOLT-328 --> [!DNL Quick Checkout] Adobe Commerce版およびMagento Open Source版には、 [管理パネルビュー](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) と、拡張機能の設定と使用に必要なすべての情報を含んでいます。

![新規](../assets/new.svg)<!-- Issue BOLT-364 --> 管理者ユーザー [ユーザーの役割と権限を設定できます。](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/user-roles-setup.html) 他のユーザーが [!DNL Quick Checkout] 管理パネル。

![新規](../assets/new.svg)<!-- Issue BOLT-377 --> [!DNL Quick Checkout] 管理パネルに、次のような特定のセクションを含むページヘッダーが追加されました。 **概要**, **レポート**、および **設定**.

![新規](../assets/new.svg)<!-- Issue BOLT-379 --> 新しい商人が [!DNL Quick Checkout] 機能ツアーを提供するようこそウィジェットが初めて表示されるときの管理パネル。

![新規](../assets/new.svg)<!-- Issue BOLT-378 --> [!DNL Quick Checkout] [管理パネルビュー](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) を組み込む **設定** API と公開可能なキーが [設定](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 表示。

![新規](../assets/new.svg)<!-- Issue BOLT-380 --> [!DNL Quick Checkout] [管理パネルビュー](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) を組み込む **リソース** オンボーディングステージに応じて変わるセクション。

![新規](../assets/new.svg)<!-- Issue BOLT-381 --> [!DNL Quick Checkout] [管理パネルビュー](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) を含む **ヘルプとサポート** 」セクションに入力します。

![修正された問題](../assets/fix.svg)<!-- Issue BOLT-369 --> The [[!DNL Quick Checkout] 管理パネル](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) フッターに拡張機能のバージョンが表示されるようになりました。

## v1.1.0

_2022 年 8 月 13 日_

[!BADGE 互換性]{type=Informative tooltip="互換性"}

![修正された問題](../assets/fix.svg)<!-- Issue BOLT-375 --> のユーザーエクスペリエンスの改善 [[!DNL Quick Checkout] 管理パネル](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 拡張機能が有効になっている場合に表示および検証されるパラメーターのみを含めるようになりました。

![修正された問題](../assets/fix.svg)<!-- Issue BOLT-349 --> 既存の配送先住所と Bolt ウォレットの互換性を改善しました。

## v1.0.0

_2022 年 8 月 10 日_

[!BADGE 互換性]{type=Informative tooltip="互換性"}

![新規](../assets/new.svg)<!-- Issue BOLT-341 --> GA リリース —[[!DNL Quick Checkout]](https://commercemarketplace.adobe.com/magento-quick-checkout.html) は、Adobe Commerceバージョン 2.4.1 ～ 2.4.4 と互換性があるようになりました。

![新規](../assets/new.svg)<!-- Issue BOLT-340 --> The [!DNL Quick Checkout] Adobe Commerce版は、Adobe Commerce版としてインストールできます。 [クラウドインフラストラクチャ](install.md#adobe-commerce-on-cloud-infrastructure) または [オンプレミス](install.md#on-premises) インスタンス。 これらのメソッドでは、コマンドラインインターフェイスを使用する必要があります。

![新規](../assets/new.svg)<!-- Issue BOLT-1 --> The [!DNL Quick Checkout] Adobe Commerce向けに最適化されたストアフロントを使用すると、 [ワンクリックチェックアウトエクスペリエンス](overview.md) を使用する場合、ユーザーに必要な入力フィールドはありません。

![新規](../assets/new.svg)<!-- Issue BOLT-1 --> The [!DNL Quick Checkout] for Adobe Commerceは、 [ワンクリック購入](checkout-flow.md) 直接アクセスできます。

![新規](../assets/new.svg)<!-- Issue BOLT-1 --> The [!DNL Quick Checkout] Adobe Commerceの場合、買い物客は同時に [Adobe Commerceと Bolt の両方のネットワークにログインしました](checkout-flow.md/#quick-checkout-use-cases) より良い物を提供する `one-click checkout` エクスペリエンス。

![新規](../assets/new.svg)<!-- Issue BOLT-218 --> [!DNL Quick Checkout] (Adobe Commerceの場合はをサポート ) [サンドボックスアカウント](testing.md#testing-in-sandbox) これにより、マーチャントは拡張機能をテストモードで評価できます。

![新規](../assets/new.svg)<!-- Issue BOLT-780 --> 買い物客は、 [[!DNL Quick Checkout]](checkout-page.md) 拡張または経由 [手動オーダー作成](create-order-admin.md).

![新規](../assets/new.svg)<!-- Issue BOLT-666 --> マーチャントが [!DNL Quick Checkout] 次のような基本的な支払いアクションを持つ [`Authorize and Capture` または `Authorize`](onboarding.md#complete-admin-configuration)、またはサンドボックスと実稼動環境を切り替えることができます。

![新規](../assets/new.svg)<!-- Issue BOLT-288 --> カスタム [ユーザーセッションの有効期間](user-session-lifetime.md) 対象： [!DNL Quick Checkout] Adobe Commerceの

![修正された問題](../assets/fix.svg)<!-- Issue BOLT-375 --> のユーザーエクスペリエンスの改善 [[!DNL Quick Checkout] 管理パネル](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) を使用すると、必要なパラメーターがすべて指定された場合に設定を保存できます。

![既知の問題](../assets/bug.svg)<!-- Issue BOLT-342 --> 共通 [トラブルシューティング](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) インストール中の問題 [!DNL Quick Checkout].
