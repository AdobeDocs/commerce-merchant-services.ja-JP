---
title: イベントコレクションを検証
description: 行動データがAdobe Commerceに送信されていることを確認する方法を説明します。
exl-id: c8c34db4-9d87-4012-b8f0-e9b1da214305
source-git-commit: d8be88f47f103c5d632540dae743ede398a9b7ad
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# イベントコレクションを検証

後 [インストールと設定](install-configure.md) の `magento/product-recommendations` モジュールの両方に属している場合は、行動データがAdobe Commerceに送信されていることを確認できます。 Chrome で利用可能な開発者ツールを使用するか、Snowplow Chrome 拡張機能をインストールできます。 追加のヘルプが必要な場合は、 [トラブルシューティング [!DNL Product Recommendations] モジュール](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce.html) 」を参照してください。

## Chrome の開発者ツールを使用した検証

イベントコレクターの JS ファイルをすべてのサイトページに確実に読み込むには、次の手順を実行します。

1. Chrome で、を選択します。 **Google Chrome のカスタマイズと制御** 次に、 **その他のツール** > **開発者ツール**.
1. を選択します。 **ネットワーク** 「 」タブをクリックし、「 」を選択します。 **JS** タイプ。
1. フィルター `ds.`
1. ページをリロードします。
1. 次のようになります。 `ds.js` または `ds.min.js` 内 **名前** 列。

![イベントコレクター JS](assets/filter-ds.png)
_イベントコレクター JS_

サイト（ホーム、製品、チェックアウトなど）全体のページでイベントが発生するようにするには：

1. ブラウザー上での広告ブロッカーを必ず無効にし、サイト上での cookie を受け入れてください。
1. Chrome で、を選択します。 **Google Chrome のカスタマイズと制御** （ブラウザーの右上隅の 3 つの縦のドット）次に、 **その他のツール** > **開発者ツール**.
1. を選択します。 **ネットワーク** タブとフィルター `tp2`.
1. ページをリロードします。
1. の下に呼び出しが表示されます。 `tp2` 内 **名前** 列。

![イベントの発生](assets/filter-tp2.png)
_イベントが発生していることを確認します。_

## Snowplow Chrome 拡張機能を使用した検証

のインストール [Chrome 用 Snowplow Analytics Debugger 拡張機能](https://chrome.google.com/webstore/detail/snowplow-analytics-debugg/jbnlcgeengmijcghameodeaenefieedm). この拡張機能では、収集され、Adobe Commerceに送信されるイベントを表示します。

1. ブラウザー上での広告ブロッカーを必ず無効にし、サイト上での cookie を受け入れてください。

1. Chrome で、を選択します。 **Google Chrome のカスタマイズと制御** （ブラウザーの右上隅の 3 つの縦のドット）次に、 **その他のツール** > **開発者ツール**.

1. を選択します。 **Snowplow Analytics デバッガー** タブをクリックします。

1. 以下 **イベント** 列、選択 **構造化イベント**.

1. 下にスクロールして、 **コンテキストデータ _n_**. でストアフロントインスタンスを探します。**スキーマ**.

1. を確認します。 [SaaS データ容量 ID](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) が正しく設定されている。

![Snowplow フィルター](assets/snowplow-filter.png)
_Snowplow フィルター_

>[!NOTE]
>
> 値： `Data validity : NOT FOUND` デバッガーに内部スキーマが表示されます。 Snowplow Chrome プラグインは、内部スキーマを持つイベントを検証できません。 これは、実際の機能には影響しません。

## イベントが正しく実行されていることを確認する

指標に使用されるイベントが正しく実行されていることを確認するには、 `impression-render`, `view`、および `rec-click` イベントを Snowplow Analytics Debugger に追加しました。 詳しくは、 [イベントの完全なリスト](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/events.html).

>[!NOTE]
>
> If [Cookie 制限モード](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) が有効になっている場合、Adobe Commerceは買い物客の同意を得るまで行動データを収集しません。 「Cookie Restriction Mode」が無効になっている場合、行動データはデフォルトで収集されます。
