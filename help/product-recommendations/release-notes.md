---
title: '[!DNL Product Recommendations] リリースノート'
description: の最新のリリース情報 [!DNL Product Recommendations] Adobe Commerceから
exl-id: 1758e688-d26f-45e7-818c-d4726338a6c3
feature: Services, Recommendations, Release Notes
source-git-commit: 1dc69bf92ce8c9105724dea0ce70c34afa25a091
workflow-type: tm+mt
source-wordcount: '1144'
ht-degree: 0%

---

# [!DNL Product Recommendations] リリースノート

リリースノートには、以下の更新が含まれています。 [!DNL Product Recommendations] モジュール：

* [!DNL Product Recommendations] メタパッケージ： `magento/product-recommendations`
* でのページビルダーのサポート [!DNL Product Recommendations] （オプション）モジュール： `magento/module-page-builder-product-recommendations`
* の視覚的類似性レコメンデーションタイプのサポート [!DNL Product Recommendations] （オプション）モジュール： `magento/module-visual-product-recommendations`

現在のメジャーリリースバージョンがサポートされています。 古いバージョンのリリースノートは参照用に提供されています。
リリースノートには次の内容が含まれます。

![新規](../assets/new.svg) 新機能
![修正点](../assets/fix.svg) 修正点および改善点
![バグ](../assets/bug.svg) 既知の問題

開発者向けドキュメントを参照してください。 [製品サポートの詳細](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## ホストされるサービスの更新

これらのノートでは、バージョン管理されたリリース以外で公開された更新や、ホストされたサービスの改善について説明します。

+++ホストされたサービスの更新

_2023 年 7 月 19 日_

![新規](../assets/new.svg) 製品のRecommendationsにGraphQLが追加されました [`recommendations`](https://developer.adobe.com/commerce/webapi/graphql/schema/product-recommendations/queries/recommendations/) クエリ。

_2023 年 4 月 26 日_

![新規](../assets/new.svg) 製品Recommendationsのお客様は、 [SaaS 価格のインデックス作成](../price-index/index.md).

+++

## 現在のメジャーバージョン

### magento/product-recommendations の 5.0.0

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) Adobe Commerce 2.4.6 をサポートするように製品Recommendationsを更新しました。
![新規](../assets/new.svg) これはメジャーバージョンのリリースです。 [編集](install-configure.md#update) 根 `composer.json` ファイルを作成します。

#### 既知の制限事項

* The `websiteCode` 値にアンダースコア (_) が含まれる場合、誤って値が返されます。

### 以前のバージョン

+++4.0.1 以前

### magento/product-recommendations の 4.0.1

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![修正点](../assets/fix.svg) 以前は、表示通貨がデフォルト以外の通貨に切り替えられた場合に、製品Recommendationsにエラーが表示されていました。 通貨の切り替えが正しく機能するようになりました。

### magento/product-recommendations の 4.0.0

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) 追加済み [対応指標](create.md) を使用すると、各レコメンデーションタイプのトレーニングの進行状況を視覚化できます。
![新規](../assets/new.svg) これはメジャーバージョンのリリースです。 [編集](install-configure.md#update) 根 `composer.json` ファイルを作成します。 また、このリリースでは、Product Recommendationsのインストールと設定時に、2 つの API キーを指定する必要があります。 [実稼働キーとサンドボックスキー](../landing/saas.md).

#### 既知の制限事項

* The `websiteCode` 値にアンダースコア (_) が含まれる場合、誤って値が返されます。

### magento/product-recommendations の 3.3.7

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) PHP 8.1 のサポートを追加しました。
![新規](../assets/new.svg) 画像のサイズ変更が改善され、参照表示テンプレートで画像のサイズ変更がより一貫して処理されるようになりました。

### magento/product-recommendations の 3.3.6

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) 最適化済み [!DNL Product Recommendations] 依存関係を明示的にリストしてメタパッケージ化する

### magento/product-recommendations の 3.3.5

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) 追加済み [B2B サポート](onboarding.md#b2bsupport) 製品のRecommendations
![新規](../assets/new.svg) に新しいフィードを追加しました [カタログデータを同期](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) コマンドラインからコマースサービスに

### magento/product-recommendations の 3.3.3

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) 新規追加 [レコメンデーションタイプ](type.md)：コンバージョン（買い物かごへの表示）、コンバージョン（購入への表示）、最近表示。 これらの新しいレコメンデーションタイプは、 `magento/product-recommendations` モジュール 3.2.2 以降。
![修正点](../assets/fix.svg) Fastly の Web アプリケーションファイアウォール (WAF) が Cookie を誤ってブロックしていた問題を修正しました。
![修正点](../assets/fix.svg) デフォルト以外のストア表示に割り当てられた製品が _Recommendations Product Preview_ パネルを使用して特定のストア表示のレコメンデーションを作成する
![修正点](../assets/fix.svg) ページビルダーの特定のレコメンデーション単位名が、ストアフロントにレコメンデーション単位を表示できない問題を修正しました。

### magento/product-recommendations の 3.3.2

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![修正点](../assets/fix.svg) B2B サポートの不足していた依存関係を修正しました。

### magento/product-recommendations の 3.3.1

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) B2B 顧客グループの価格設定に対するサポートが追加されました。 次の場合に、 [価格フィルター](filters.md) レコメンデーション・ユニットで、ログインした B2B 顧客には、表示される製品の顧客グループの価格設定が表示されます。

### magento/product-recommendations の 3.3.0

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) Adobe Commerceの機能およびサービスをまたいでAdobeデータの収集を標準化する、行動データレイヤーのサポートを追加しました。 詳しくは、 [readme](https://github.com/adobe/magento-storefront-event-collector/blob/main/README.md) を参照してください。

### magento/product-recommendations の 3.2.6

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![修正点](../assets/fix.svg) JavaScript モーダルエラーを修正しました。
![修正点](../assets/fix.svg) Fastly の Web アプリケーションファイアウォール (WAF) が Cookie を誤ってブロックしていた問題を修正しました。

### magento/product-recommendations の 3.2.5

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) Magentoサービスの名前をに変更しました [コマースサービス](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) 管理での使いやすさの向上

### magento/product-recommendations の 3.2.4

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![修正点](../assets/fix.svg) 製品属性のインデックス作成時の「設定可能な製品オプションデータを取得できません」エラーを修正しました。

### magento/product-recommendations の 3.2.3

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![修正点](../assets/fix.svg) カタログ同期中に「設定可能な製品オプションデータを取得できません」というエラーが発生する問題を修正しました。
![修正点](../assets/fix.svg) 「URL にストアコードを追加」設定を有効にすると、ストアコードが正しく設定されない問題を修正しました。
![修正点](../assets/fix.svg) 管理パネルの設定の変更を検出し、これらの変更がカタログ同期データに反映されるように改善しました。

### magento/product-recommendations の 3.2.2

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) 次の機能を追加しました。 [レコメンデーション結果のプレビュー](create.md) 作成時に その場合は、モジュールを最新バージョンに更新する必要が生じる可能性があります。
![新規](../assets/new.svg) 次の機能を追加しました。 [監視と管理](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) 管理者からのカタログ同期プロセス。
![新規](../assets/new.svg) 追加済み [フィルター](filters.md) を使用して、レコメンデーションに表示する製品を制御できます。
![新規](../assets/new.svg) 追加された [視覚的類似性](type.md#visualsim) レコメンデーションタイプ。

### Page Builder の magento/module-page-builder-product-recommendations の 1.2.1

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) 3.2.0 以降のバージョンのサポートを追加しました。 `magento/product-recommendations` モジュール

### magento/product-recommendations の 3.1.0

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) 次の機能を追加しました。 [再同期](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) コマンドラインを介してカタログを SaaS サービスに送信する。
![新規](../assets/new.svg) データベーステーブルのプレフィックスのサポートを追加しました。
![修正点](../assets/fix.svg) PHP 7.1 のサポートを削除しました。

### magento/product-recommendations の 3.0.8

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![修正点](../assets/fix.svg) モジュールが設定される前にイベントがデータ収集用に送信され、無効なトラフィックが発生する問題を修正しました。

### magento/product-recommendations の 3.0.6

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) **（ベータ版）** 新規のサポートを含む [視覚的類似性](type.md#visualsim) レコメンデーションタイプ。

### magento/module-visual-product-recommendations の 1.0.0

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) **（ベータ版）** [視覚的類似性](type.md#visualsim). を使用 _視覚的類似性_ レコメンデーションタイプを使用すると、表示されている製品と視覚的に類似した製品を表示する製品の詳細ページにレコメンデーション単位をデプロイできます。

### magento/product-recommendations の 3.0.5

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![修正点](../assets/fix.svg) カタログの書き出し中に発生する可能性がある「製品オプションデータを取得できません」エラーを修正しました。
![修正点](../assets/fix.svg) 通貨記号 ( _売上高_ 列 _製品Recommendations_ ダッシュボードに、設定済みのベース通貨が正しく反映されるようになりました。

### magento/product-recommendations の 3.0.4

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![修正点](../assets/fix.svg) Adobe Commerce 2.4.0 のサポートを追加しました。

### magento/product-recommendations の 3.0.3

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![修正点](../assets/fix.svg) ストアフロントテンプレートでのシンボルの実装を改善しました。

### Page Builder の magento/module-page-builder-product-recommendations の 1.0.4

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) Page Builder のコンテンツタイプの編集時に、製品のレコメンデーション名を追加しました。

### 3.0.2 magento/product-recommendations

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) ページビルダーでレコメンデーション単位を選択する際のグリッドにステータス列を追加しました。
![修正点](../assets/fix.svg) 製品 URL と画像 URL が正しくない http/https プロトコルに関する問題を修正しました

### magento/product-recommendations の 3.0.1

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

これはメジャーバージョンのリリースです。 [編集](install-configure.md#update) プロジェクトのルート composer.json ファイル。

![新規](../assets/new.svg) 取得 [!DNL Product Recommendations] 代替の SaaS データスペースから。 これにより、実稼動以外の他の環境で、お使いの製品環境で計算された製品レコメンデーションを使用できます。 [SaaS データスペースの切り替え](settings.md) この機能について詳しく説明します。

![修正点](../assets/fix.svg) uBlock Origin を使用する買い物客のチェックアウトが禁止されていた問題を修正しました。
![修正点](../assets/fix.svg) 買い物かごへの不要な追加イベントを送信する際の問題を修正しました。

### Page Builder の magento/module-page-builder-product-recommendations の 1.0.3

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) ページビルダーのサポート。 Page Builder の統合により、Page Builder が作成したコンテンツ上の任意の場所に、正確かつ詳細にレコメンデーション単位を配置できます。 見出しとレコメンデーション単位自体のスタイルを設定することもできます。 に移動します。 [Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) を参照してください。

### magento/product-recommendations の 2.0.0

[!BADGE サポート対象]{type=Informative tooltip="サポート対象"}

![新規](../assets/new.svg) GA リリース！

+++

## ドキュメント

詳しくは、以下を参照してください。 [!DNL Product Recommendations] および [!DNL Product Recommendations] 開発：

* [ユーザーガイド](overview.md)
* [開発者向けドキュメント](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/development-overview.html)
