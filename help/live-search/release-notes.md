---
title: '''[!DNL Live Search] リリースノート`'
description: 「 [!DNL Live Search] Adobe Commerceから」
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
source-git-commit: fd3f71a1b3d958f3aa79f0ba6603d30e16e70507
workflow-type: tm+mt
source-wordcount: '1046'
ht-degree: 0%

---

# [!DNL Live Search] リリースノート

これらのリリースノートでは、の最新バージョンについて説明します [!DNL Live Search] およびを含めます。

![新規](../assets/new.svg) 新機能
![修正点](../assets/fix.svg) 修正点および改善点
![バグ](../assets/bug.svg) 既知の問題


## 現在のメジャーバージョン

### [!DNL Live Search] 2.0.5 {#205}

* Adobe Commerce(EE) との互換性：2.4.x
* Adobe Commerce for Cloud(ECE) との互換性：2.4.x
* 安定性：安定

![修正点](../assets/fix.svg) ネットワークの問題が原因で SDK リソースを使用できない場合、ライブ検索でエラーが発生していました。 このバグを修正しました。

これらの機能にアクセスするには、マーチャントは Live Search 拡張機能バージョン 2.0.5 以降をアップグレードする必要があります。

実稼動環境にプッシュする前に、アップグレードおよびテストすることをお勧めします。 テスト環境の結果を確認した後、オフピーク時に実稼動環境のアップグレードを検討します。

### [!DNL Live Search] 2.0.4 {#204}

* Adobe Commerce(EE) との互換性：2.4.x
* Adobe Commerce for Cloud(ECE) との互換性：2.4.x
* 安定性：安定

![新規](../assets/new.svg) ライブ検索で、管理の「在庫切れの製品を表示」設定によるフィルタリングがサポートされるようになりました。 「在庫切れの製品を表示」が false に設定されている場合、 `inStock = true` がフィルターに追加されます。
![修正点](../assets/fix.svg) パフォーマンスを向上させるために、ライブ検索ポップアップから「候補」ブロックが削除されました。 この機能を置き換える場合でも、データはGraphQL経由で渡されます。
![修正点](../assets/fix.svg) `categories` および `categoryPath` 置き換えられた `categoryIds` カテゴリのフィルタリング用。 詳しくは、 [productSearch](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) トピック。
![修正点](../assets/fix.svg) 以前は、B2B 会社に関連付けられているユーザーが検索をおこなうと、誤った顧客グループコードを受け取っていました。 ライブ検索で正しい値が返されるようになりました。
![修正点](../assets/fix.svg) 以前は、存在しない語句を検索すると、ライブ検索でエラーが返されていました。 そのバグは修正されました。

これらの機能にアクセスするには、マーチャントは Live Search 拡張機能バージョン 2.0.4 以降をアップグレードする必要があります。

実稼動環境にプッシュする前に、アップグレードおよびテストすることをお勧めします。 テスト環境の結果を確認した後、オフピーク時に実稼動環境のアップグレードを検討します。

### [!DNL Live Search] 2.0.3 {#203}

* Adobe Commerce(EE) との互換性：2.4.x
* Adobe Commerce for Cloud(ECE) との互換性：2.4.x
* 安定性：安定

![新規](../assets/new.svg) ライブ検索で、カテゴリ権限、共有カタログ、および顧客グループ固有の価格設定を遵守することで、B2B 機能がサポートされるようになりました。

これらの機能にアクセスするには、マーチャントは Live Search 拡張機能バージョン 2.0.3 以降をアップグレードする必要があります。

実稼動環境にプッシュする前に、アップグレードおよびテストすることをお勧めします。 テスト環境の結果を確認した後、オフピーク時に実稼動環境のアップグレードを検討します。

### [!DNL Live Search] 2.0 {#20}

* Adobe Commerce(EE) との互換性：2.4.x
* Adobe Commerce for Cloud(ECE) との互換性：2.4.x
* 安定性：安定

既存 [!DNL Live Search] インストールは、次にアップグレードする必要があります： [!DNL Live Search] 2.0.0 では、次の新機能、修正点および改善点を活用できます。

![新規](../assets/new.svg) [!DNL Live Search] Adobe Commerce 2.4.4 を実行するインストールで、PHP 8.1 がサポートされるようになりました。
![新規](../assets/new.svg) この `Magento_ElasticsearchCatalogPermissionsGraphQl` モジュールは、インストール時に無効になるモジュールのリストに追加されます。
![新規](../assets/new.svg) 内の使用可能な行の数 [[!DNL storefront popover]](quick-tour.md) は、 *管理者*.
![新規](../assets/new.svg) ベータ版 [PWA](https://developer.adobe.com/commerce/pwa-studio/) 互換性 [!DNL Live Search].
![新規](../assets/new.svg) この [!DNL Live Search] インストールプロセスは、高度なプロセス変更で更新されます。
![修正点](../assets/fix.svg) [詳細検索](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) storefront フッターからリンクが削除されました。
![バグ](../assets/bug.svg) 次の製品属性は、ではサポートされていません。 [Commerce GraphQL API](https://developer.adobe.com/commerce/webapi/graphql/) PWAのベータリリースに関連して使用する場合： `description`, `name`, `short_description`
![バグ](../assets/bug.svg) のPWAのベータリリース [!DNL Live Search] はをサポートしていません [イベント処理](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).

## 以前のバージョン

+++1.3.1 以前

### [!DNL Live Search] 1.3.1 {#131}

* Adobe Commerce(EE) との互換性：2.4.x
* Adobe Commerce for Cloud(ECE) との互換性：2.4.x
* 安定性：安定

![修正点](../assets/fix.svg) [カスタム価格属性](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html) が [ファセット]({% link live-search/facets-add.md %})。
![修正点](../assets/fix.svg) 次の場合にエラーが発生する問題を修正しました。 [通貨記号](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html#step-5%3A-customize-currency-symbols-(optional)) (`data-currency-symbol`) が使用可能です。
![修正点](../assets/fix.svg) [[!DNL Storefront popover]](storefront-popover.md) 今は [特別価格](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-special.html) （最終価格の最小値）を指定できます。

### [!DNL Live Search] 1.3.0 {#130}

* Adobe Commerce(EE) との互換性：2.4.x
* Adobe Commerce for Cloud(ECE) との互換性：2.4.x
* 安定性：安定

![新規](../assets/new.svg) [パフォーマンス](performance.md) レポートダッシュボードでは、買い物客が使用する検索用語に関するインサイトを得ることができます。
![新規](../assets/new.svg) [!DNL Live Search] [Storefront Events SDK](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) では、イベント公開および購読サービス、指標を含む、共通のデータレイヤーにアクセスできます。
![修正点](../assets/fix.svg) この [[!DNL Storefront popover]](storefront-popover.md) 新しい `active` クラス `.search-autocomplete` 表示/非表示を制御するコンテナ。
![修正点](../assets/fix.svg) 店頭では、 [検索語句](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html#popular-search-terms) フッターリンクが削除され、そのキャッシュが無効になっている [!DNL Live Search] インストール。
![バグ](../assets/bug.svg) 検索アダプタのパッチは、重複した製品を処理します。
![バグ](../assets/bug.svg) [!DNL Live Search] サポート [単一ソース](https://experienceleague.adobe.com/docs/commerce-admin/inventory/sources/sources-manage.html) （物理）複数の（仮想）在庫場所 [在庫](https://experienceleague.adobe.com/docs/commerce-admin/inventory/stocks/stocks-manage.html). 現在、複数の在庫ソースはサポートされていません。

### [!DNL Live Search] 1.2.0 {#120}

* Adobe Commerce(EE) との互換性：2.4.x
* Adobe Commerce for Cloud(ECE) との互換性：2.4.x
* 安定性：安定

![新規](../assets/new.svg) [[!DNL Storefront popover]](storefront-popover.md) 「検索」ボックスに買い物客タイプのクエリとして、上位の検索結果の推奨製品とサムネール画像を表示します。
![新規](../assets/new.svg) コマース *管理者* キーボードの操作が行われない時間が長く続く間、セッションは開いたままになる
![新規](../assets/new.svg) [!DNL Live Search] オンボーディング後、が自動的に有効になります
![修正点](../assets/fix.svg) 初期インデックス作成時間が 1 時間未満です
![修正点](../assets/fix.svg) ほぼリアルタイムで製品の増分アップデート（インストールおよびセットアップ後）
![修正点](../assets/fix.svg) シノニム・エディタの並べ替え可能な列
![修正点](../assets/fix.svg) [!DNL Live Search] 検索条件に空の並べ替え順の値が含まれる場合にエラーがスローされなくなりました。
![修正点](../assets/fix.svg) 属性コードに「to」または「from」の文字列が含まれる場合、範囲フィルターが壊れなくなりました。

### [!DNL Live Search] 1.1.0 {#110}

* Adobe Commerce(EE) との互換性：2.4.x
* Adobe Commerce for Cloud(ECE) との互換性：2.4.x
* 安定性：安定

![バグ](../assets/bug.svg) この [!DNL Live Search] サービスは、 [基準通貨](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html) Adobe Commerceのインストール
![バグ](../assets/bug.svg) ファセットを追加する場合、に設定すると、製品属性フィードが正しく更新されません。 `Update on Save`. この問題を回避するには、に移動します。 [インデックス管理](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) 製品属性フィードをに設定します。 `Update by Schedule`.
![バグ](../assets/bug.svg) [!DNL Live Search] シノニムはストア表示ごとに定義されますが、現在は Web サイトごとに保存され、次の組み合わせで識別されます。 `environmentId` + `storeViewCode`. その結果、Adobe Commerceのインストール内のすべての Web サイトおよびストア表示で、同じ同義語のセットが共有されます。 ストア表示のシノニムの最近作成したセットが優先されます。
![バグ](../assets/bug.svg) シノニム用語に複数の単語が含まれる場合、各単語は別々のシノニムとして扱われます。 例えば、「時間」を「時間」のシノニムとして定義した場合、「時間」と「ピース」の両方は、時間の同義語として扱われます。

+++

## ドキュメント

詳しくは、以下を参照してください。

* [Adobe Commerce開発者向けドキュメント](https://developer.adobe.com/commerce/docs)
* [Adobe Commerce User Guide](https://experienceleague.adobe.com/docs/commerce.html)
* [[!DNL Live Search] Marketplace の](https://marketplace.magento.com/magento-live-search.html)
