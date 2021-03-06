---
title: リリースノート
description: の最新のリリース情報 [!DNL Product Recommendations] Adobe Commerceから
exl-id: 1758e688-d26f-45e7-818c-d4726338a6c3
source-git-commit: 78f469dda853a6f46394d5969f879100cf22f8bb
workflow-type: tm+mt
source-wordcount: '945'
ht-degree: 0%

---

# リリースノート

リリースノートには、以下の更新が含まれています [!DNL Product Recommendations] モジュール：

* 2021 年 3 月現在 [!DNL Product Recommendations] は、 [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/) ストアフロント
* [!DNL Product Recommendations] メタパッケージ： `magento/product-recommendations`
* でのページビルダーのサポート [!DNL Product Recommendations] （オプション）モジュール： `magento/module-page-builder-product-recommendations`
* の視覚的類似性レコメンデーションタイプのサポート [!DNL Product Recommendations] （オプション）モジュール： `magento/module-visual-product-recommendations`

リリースノートには次の内容が含まれます。

* ![新規](../assets/new.svg)  — 新機能
* ![修正点](../assets/fix.svg)  — 修正点および改善点

開発者向けドキュメントを参照してください。 [製品の互換性の詳細](https://devdocs.magento.com/release/availability.html).

## Adobe Commerce 2.3.x および 2.4.x

## magento/product-recommendations の 4.0.0

* ![新規](../assets/new.svg)  — 追加済み [対応指標](create.md) を使用すると、各レコメンデーションタイプのトレーニングの進行状況を視覚化できます。
* ![新規](../assets/new.svg)  — これはメジャーバージョンリリースです。 必ず [編集](install-configure.md#update) 根 `composer.json` ファイルを作成します。 また、このリリースでは、Product Recommendationsのインストールと設定時に、2 つの API キーを指定する必要があります。 [実稼働キーとサンドボックスキー](../landing/saas.md).

## magento/product-recommendations の 3.3.7

* ![新規](../assets/new.svg) - PHP 8.1 のサポートを追加
* ![新規](../assets/new.svg)  — 画像のサイズ変更が改善され、参照表示テンプレートで異なるサイズの画像が一貫して処理されるようになりました。

## magento/product-recommendations の 3.3.6

* ![新規](../assets/new.svg)  — 最適化済み [!DNL Product Recommendations] 依存関係を明示的にリストしてメタパッケージ化

### magento/product-recommendations の 3.3.5

* ![新規](../assets/new.svg)  — 追加済み [B2B サポート](onboarding.md#b2bsupport) 製品のRecommendations
* ![新規](../assets/new.svg)  — に新しいフィードを追加しました [カタログデータを同期](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-catalog-sync.html) コマンドラインからコマースサービスに

### magento/product-recommendations の 3.3.3

* ![新規](../assets/new.svg)  — 新規追加 [レコメンデーションタイプ](type.md):コンバージョン（買い物かごへの表示）、コンバージョン（購入への表示）、最近表示。 これらの新しいレコメンデーションタイプは、 `magento/product-recommendations` モジュール 3.2.2 以降。
* ![修正点](../assets/fix.svg) - Fastly の Web アプリケーションファイアウォール (WAF) が Cookie を正しくブロックしない問題を修正しました
* ![修正点](../assets/fix.svg)  — デフォルト以外のストア表示に割り当てられた製品が _Recommendations Product Preview_ パネルを使用して特定のストア表示のレコメンデーションを作成する
* ![修正点](../assets/fix.svg)  — ページビルダーの特定のレコメンデーション単位名が、ストアフロントにレコメンデーション単位を表示できない問題を修正しました

### magento/product-recommendations の 3.3.2

* ![修正点](../assets/fix.svg) - B2B サポートの依存関係が見つからない問題を修正しました

### magento/product-recommendations の 3.3.1

* ![新規](../assets/new.svg) - B2B 顧客グループの価格設定に対するサポートが追加されました。 次の場合、 [価格フィルター](filters.md) レコメンデーション・ユニットで、ログインした B2B 顧客には、表示される製品の顧客グループの価格設定が表示されます。

### magento/product-recommendations の 3.3.0

* ![新規](../assets/new.svg) -AdobeクライアントデータレイヤーがAdobe Commerceの機能およびサービスをまたいで行動データの収集を標準化するようサポートを追加しました。 詳しくは、 [readme](https://github.com/adobe/magento-storefront-event-collector/blob/main/README.md) を参照してください。

### magento/product-recommendations の 3.2.6

* ![修正点](../assets/fix.svg) - JavaScript モーダルエラーを修正しました
* ![修正点](../assets/fix.svg) - Fastly の Web アプリケーションファイアウォール (WAF) が Cookie を正しくブロックしない問題を修正しました

### magento/product-recommendations の 3.2.5

* ![新規](../assets/new.svg) -Magentoサービスの名前をに変更しました [コマースサービス](https://docs.magento.com/user-guide/system/saas.html) 管理での使いやすさの向上

### magento/product-recommendations の 3.2.4

* ![修正点](../assets/fix.svg)  — 製品属性のインデックス作成時の「設定可能な製品オプションデータを取得できません」エラーを修正しました

### magento/product-recommendations の 3.2.3

* ![修正点](../assets/fix.svg)  — カタログ同期中に「設定可能な製品オプションデータを取得できません」というエラーが発生する問題を修正しました。
* ![修正点](../assets/fix.svg) - 「URL にストアコードを追加」設定を有効にした場合、ストアコードが正しく設定されない問題を修正しました
* ![修正点](../assets/fix.svg)  — 管理パネルの設定の変更が検出され、これらの変更がカタログ同期データに確実に反映されるようになりました

### magento/product-recommendations の 3.2.2

* ![新規](../assets/new.svg)  — 次の機能を追加しました。 [レコメンデーション結果のプレビュー](create.md) 作成時に その場合は、モジュールを最新バージョンに更新する必要が生じる可能性があります。
* ![新規](../assets/new.svg)  — 次の機能を追加しました。 [監視と管理](https://docs.magento.com/user-guide/system/catalog-sync.html) 管理者からのカタログ同期プロセス。
* ![新規](../assets/new.svg)  — 追加済み [フィルター](filters.md) を使用して、レコメンデーションに表示する製品を制御できます。
* ![新規](../assets/new.svg)  — が追加されました [視覚的類似性](type.md#visualsim) レコメンデーションタイプ。

### Page Builder の magento/module-page-builder-product-recommendations の 1.2.1

* ![新規](../assets/new.svg) - 3.2.0 以降のバージョンの `magento/product-recommendations` モジュール

### magento/product-recommendations の 3.1.0

* ![新規](../assets/new.svg)  — 次の機能を追加しました。 [再同期](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-catalog-sync.html) コマンドラインを介してカタログを SaaS サービスに送信する。
* ![新規](../assets/new.svg)  — データベーステーブルのプレフィックスのサポートを追加しました
* ![修正点](../assets/fix.svg) - PHP 7.1 のサポートを削除しました。

### magento/product-recommendations の 3.0.8

* ![修正点](../assets/fix.svg)  — モジュールが設定される前にイベントがデータ収集用に送信され、無効なトラフィックが発生する問題を修正しました

### magento/product-recommendations の 3.0.6

* ![新規](../assets/new.svg) - **（ベータ版）** 新しい [視覚的類似性](type.md#visualsim) レコメンデーションタイプ。

### magento/module-visual-product-recommendations の 1.0.0

* ![新規](../assets/new.svg) - **（ベータ版）** [視覚的類似性](type.md#visualsim). を使用 _視覚的類似性_ レコメンデーションタイプを使用すると、表示されている製品と視覚的に類似した製品を表示する製品の詳細ページにレコメンデーション単位をデプロイできます。

### magento/product-recommendations の 3.0.5

* ![修正点](../assets/fix.svg)  — カタログの書き出し中に発生する可能性がある「製品オプションデータを取得できません」エラーを修正しました。
* ![修正点](../assets/fix.svg) - _売上高_ 列 _製品Recommendations_ ダッシュボードに、設定済みのベース通貨が正しく反映されるようになりました。

### magento/product-recommendations の 3.0.4

* ![修正点](../assets/fix.svg) - Adobe Commerce 2.4.0 のサポートを追加しました

### magento/product-recommendations の 3.0.3

* ![修正点](../assets/fix.svg)  — ストアフロントテンプレートでのシンボルの実装を改善しました

### Page Builder の magento/module-page-builder-product-recommendations の 1.0.4

* ![新規](../assets/new.svg) - Page Builder コンテンツタイプの編集時に製品のレコメンデーション名を追加しました

### 3.0.2 magento/product-recommendations

* ![新規](../assets/new.svg)  — ページビルダーでレコメンデーション単位を選択する際に、グリッドにステータス列を追加しました
* ![修正点](../assets/fix.svg)  — 製品 URL と画像 URL が正しくない http/https プロトコルに関する問題を修正しました

### magento/product-recommendations の 3.0.1

これはメジャーバージョンのリリースです。 必ず [編集](install-configure.md#update) プロジェクトのルート composer.json ファイル。

* ![新規](../assets/new.svg)  — 取得 [!DNL Product Recommendations] 代替の SaaS データスペースから これにより、実稼動以外の他の環境で、お使いの製品環境で計算された製品レコメンデーションを使用できます。 [SaaS データスペースの切り替え](settings.md) この機能について詳しく説明します。

* ![修正点](../assets/fix.svg) - uBlock Origin を使用する買い物客のチェックアウトが禁止されていた問題を修正しました
* ![修正点](../assets/fix.svg)  — 買い物かごへの不要な追加イベントを送信する際の問題を修正しました

### Page Builder の magento/module-page-builder-product-recommendations の 1.0.3

* ![新規](../assets/new.svg)  — ページビルダーのサポート。 Page Builder の統合により、Page Builder が作成したコンテンツ上の任意の場所に、正確かつ詳細にレコメンデーション単位を配置できます。 見出しとレコメンデーション単位自体のスタイルを設定することもできます。 に移動します。 [Page Builder](https://docs.magento.com/user-guide/cms/page-builder-add-recommendations.html) を参照してください。

### magento/product-recommendations の 2.0.0

* ![新規](../assets/new.svg)  — 一般リリース (GA)!

## ドキュメント

詳しくは、以下を参照してください。 [!DNL Product Recommendations] および [!DNL Product Recommendations] 開発：

* [ユーザーガイド](overview.md)
* [開発者向けドキュメント](https://devdocs.magento.com/recommendations/product-recs.html)
