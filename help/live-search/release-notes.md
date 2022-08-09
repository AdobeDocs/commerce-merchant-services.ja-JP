---
title: '"[!DNL Live Search] リリースノート"'
description: 「 [!DNL Live Search] Adobe Commerceから」
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
source-git-commit: 097f8af7a1e3e904c69d3a7fe52cb0db5b1b4c23
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 1%

---

# [!DNL Live Search] リリースノート

これらのリリースノートでは、の最新バージョンについて説明します [!DNL Live Search] およびを含めます。

* ![新規](../assets/new.svg)  — 新機能
* ![修正点](../assets/fix.svg)  — 修正点および改善点
* ![バグ](../assets/bug.svg)  — 既知の問題

## [!DNL Live Search] 2.0.3

* Adobe Commerce(EE) との互換性：2.4.x
* Adobe Commerce for Cloud(ECE) との互換性：2.4.x
* 安定性：安定

* ![新規](../assets/new.svg)  — ライブ検索で、カテゴリ権限、共有カタログ、お客様グループ固有の価格設定を遵守することで、B2B 機能がサポートされるようになりました。

これらの機能にアクセスするには、マーチャントは Live Search 拡張機能バージョン 2.0.3 以降をアップグレードする必要があります。

実稼動環境にプッシュする前に、アップグレードおよびテストをおこなうことをお勧めします。 テスト環境の結果を確認した後、オフピーク時に実稼動環境のアップグレードを検討します。

>[!NOTE]
>
>B2B のサポートは、8 月 9 日からバックエンドサービスで段階的に追加され、8 月末までに移行が完了する予定です。 ライブ検索拡張機能がアップグレードされない場合、ストアフロントは引き続き正常に機能しますが、B2B 機能は使用されません。

### 既知の制限事項/バグ：

* ![バグ](../assets/bug.svg)  — 提案は、顧客グループに表示できない製品をソースとしています。
* ![バグ](../assets/bug.svg) - 「デフォルトの共有カタログ」に追加しない場合、製品は表示されません。
* PWA Studioのライブ検索を使用する B2B は、PWA Studioがサポートを追加するまで使用できません。
* 製品の上書きおよび製品属性フィードには、管理者の実行が必要な同期の問題が発生する場合があります `bin/magento indexer:reset` および `bin/magento indexer:reindex` をクリックして正しく同期し直してください。

## [!DNL Live Search] 2.0

* Adobe Commerce(EE) との互換性：2.4.x
* Adobe Commerce for Cloud(ECE) との互換性：2.4.x
* 安定性：安定

既存 [!DNL Live Search] インストールは、次にアップグレードする必要があります： [!DNL Live Search] 2.0.0 では、次の新機能、修正点および改善点を活用できます。

* ![新規](../assets/new.svg) - [!DNL Live Search] Adobe Commerce 2.4.4 を実行するインストールで、PHP 8.1 がサポートされるようになりました。
* ![新規](../assets/new.svg) - `Magento_ElasticsearchCatalogPermissionsGraphQl` モジュールは、インストール時に無効になるモジュールのリストに追加されます。
* ![新規](../assets/new.svg) - [[!DNL storefront popover]](quick-tour.md) は、 *管理者*.
* ![新規](../assets/new.svg)  — ベータ版 [PWA](https://developer.adobe.com/commerce/pwa-studio/) 互換性 [!DNL Live Search].
* ![新規](../assets/new.svg) - [!DNL Live Search] インストールプロセスは、高度なプロセス変更で更新されます。
* ![修正点](../assets/fix.svg) - [詳細検索](https://docs.magento.com/user-guide/catalog/search-advanced.html) storefront フッターからリンクが削除されました。
* ![バグ](../assets/bug.svg)  — 次の製品属性は、ではサポートされていません [MagentoGraphQL API](https://devdocs.magento.com/guides/v2.4/graphql) PWAのベータリリースに関連して使用する場合： `description`, `name`, `short_description`
* ![バグ](../assets/bug.svg)  — 用PWAのベータリリース [!DNL Live Search] はをサポートしていません [イベント処理](https://devdocs.magento.com/shared-services/storefront-events-sdk.html).

## [!DNL Live Search] 1.3.1

* Adobe Commerce(EE) との互換性：2.4.x
* Adobe Commerce for Cloud(ECE) との互換性：2.4.x
* 安定性：安定

* ![修正点](../assets/fix.svg) - [カスタム価格属性](https://docs.magento.com/user-guide/stores/attributes-input-types.html) が [ファセット]({% link live-search/facets-add.md %})。
* ![修正点](../assets/fix.svg)  — 次の場合にエラーが発生する問題を修正しました。 [通貨記号](https://docs.magento.com/user-guide/stores/currency-symbols.html) (`data-currency-symbol`) が使用可能です。
* ![修正点](../assets/fix.svg) - [[!DNL Storefront popover]](storefront-popover.md) 今は [特別価格](https://docs.magento.com/user-guide/catalog/product-price-special.html) （最終価格の最小値）を指定できます。

## [!DNL Live Search] 1.3.0

* Adobe Commerce(EE) との互換性：2.4.x
* Adobe Commerce for Cloud(ECE) との互換性：2.4.x
* 安定性：安定

* ![新規](../assets/new.svg) - [パフォーマンス](performance.md) レポートダッシュボードでは、買い物客が使用する検索用語に関するインサイトを得ることができます。
* ![新規](../assets/new.svg) - [!DNL Live Search] [Storefront Events SDK](https://devdocs.magento.com/shared-services/storefront-events-sdk.html) では、イベント公開および購読サービス、指標を含む、共通のデータレイヤーにアクセスできます。
* ![修正点](../assets/fix.svg) - [[!DNL Storefront Popover]](https://devdocs.magento.com/live-search/storefront-popover.html) 新しい `active` クラス `.search-autocomplete` 表示/非表示を制御するコンテナ。
* ![修正点](../assets/fix.svg)  — 店頭では、 [検索語句](https://docs.magento.com/user-guide/marketing/search-terms-popular.html) フッターリンクが削除され、そのキャッシュが無効になっている [!DNL Live Search] インストール。
* ![バグ](../assets/bug.svg)  — 検索アダプタのパッチは、重複する製品を処理します。
* ![バグ](../assets/bug.svg) - [!DNL Live Search] サポート [単一ソース](https://docs.magento.com/user-guide/catalog/inventory-sources.html) （物理）複数の（仮想）在庫場所 [在庫](https://docs.magento.com/user-guide/catalog/inventory-stock.html). 現時点では、複数の在庫ソースはサポートされていません。

## [!DNL Live Search] 1.2.0

* Adobe Commerce(EE) との互換性：2.4.x
* Adobe Commerce for Cloud(ECE) との互換性：2.4.x
* 安定性：安定

* ![新規](../assets/new.svg) - [[!DNL Storefront popover]](storefront-popover.md) 「検索」ボックスに買い物客タイプのクエリとして、上位の検索結果の推奨製品とサムネール画像を表示します。
* ![新規](../assets/new.svg)  — コマース *管理者* キーボードの操作が行われない時間が長く続く間、セッションは開いたままになる
* ![新規](../assets/new.svg) - [!DNL Live Search] オンボーディング後、が自動的に有効になります
* ![修正点](../assets/fix.svg)  — 初期インデックス作成時間が 1 時間未満です
* ![修正点](../assets/fix.svg)  — ほぼリアルタイムで製品の増分アップデート（インストールおよびセットアップ後）
* ![修正点](../assets/fix.svg)  — シノニム・エディタの並べ替え可能な列
* ![修正点](../assets/fix.svg) - [!DNL Live Search] 検索条件に空の並べ替え順の値が含まれる場合にエラーがスローされなくなりました。
* ![修正点](../assets/fix.svg)  — 属性コードに「to」または「from」の文字列が含まれる場合、範囲フィルタリングが壊れなくなりました

## [!DNL Live Search] 1.1.0

* Adobe Commerce(EE) との互換性：2.4.x
* Adobe Commerce for Cloud(ECE) との互換性：2.4.x
* 安定性：安定

* ![バグ](../assets/bug.svg) - [!DNL Live Search] サービスは、 [基準通貨](https://docs.magento.com/user-guide/stores/currency-configuration.html) Adobe Commerceのインストール
* ![バグ](../assets/bug.svg)  — ファセットを追加する場合、に設定すると、製品属性フィードが正しく更新されません。 `Update on Save`. この問題を回避するには、に移動します。 [インデックス管理](https://docs.magento.com/user-guide/system/index-management.html) 製品属性フィードをに設定します。 `Update by Schedule`.
* ![バグ](../assets/bug.svg) - [!DNL Live Search] シノニムはストア表示ごとに定義されますが、現在は Web サイトごとに保存され、次の組み合わせで識別されます。 `environmentId` + `storeViewCode`. その結果、Adobe Commerceのインストール内のすべての Web サイトおよびストア表示で、同じ同義語のセットが共有されます。 ストア表示のシノニムの最近作成したセットが優先されます。
* ![バグ](../assets/bug.svg)  — シノニム用語に複数の単語が含まれる場合、各単語は別々のシノニムとして扱われます。 例えば、「時間」を「時間」のシノニムとして定義した場合、「時間」と「ピース」の両方は、時間の同義語として扱われます。

## ドキュメント

詳しくは、以下を参照してください。

* [Adobe Commerce開発者向けドキュメント](https://devdocs.magento.com/)
* [Adobe Commerce User Guide](https://docs.magento.com/user-guide/)
* [[!DNL Live Search] Marketplace の](https://marketplace.magento.com/magento-live-search.html)
