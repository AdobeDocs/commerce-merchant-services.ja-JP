---
title: イベント
description: 各イベントが取り込むデータと、完全なスキーマ定義の表示について説明します。
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
source-git-commit: 589d22f488572411b6632ac37d7bc5b752f72e2d
workflow-type: tm+mt
source-wordcount: '1818'
ht-degree: 0%

---

# Experience Platformコネクタイベント

次に、Commerce Connector 拡張機能をインストールする際に使用できる CommerceExperience Platformを示します。 これらのイベントで収集されたデータは、Adobe Experience Platform Edge に送信されます。 また、 [カスタムイベント](custom-events.md) 標準で提供されていない追加データを収集する場合。

以下のイベントで収集されるデータに加えて、 [追加データ](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) Adobe Experience Platform Web SDK によって提供されます。

>[!NOTE]
>
>すべてのイベントに `personID` フィールド。人物の一意の ID です。

## addToCart

製品が買い物かごに追加されたとき、または買い物かご内の製品の数量が増加したときにトリガーされます。 [フルスキーマ](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/addToCartAEP.ts).

### タイプ

ストアフロント

### 収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `productListAdds` | 製品が買い物かごに追加されたかどうかを示します。 値： `1` は、製品が追加されたことを示します。 |
| `SKU` | 在庫管理単位。 商品の一意の ID。 |
| `name` | 製品の表示名または人間が読み取り可能な名前 |
| `priceTotal` | すべての割引と税金が適用された後の、この注文の合計 |
| `quantity` | 顧客が製品の必要と示した数量 |
| `discountAmount` | 適用された割引額を示します |
| `currencyCode` | この [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 商品の通貨 |
| `productImageUrl` | 製品のメイン画像 URL |
| `selectedOptions` | 設定可能な製品に使用するフィールド。 `attribute` 設定可能な製品の属性を次のように指定します。 `size` または `color` および `value` 属性の値を次のように指定します。 `small` または `black`. |
| `cartID` | 顧客の買い物かごを識別する一意の ID |

## shoppingCartView

買い物かごのページが読み込まれたときにトリガーされます。 [フルスキーマ](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/viewAEP.ts).

### タイプ

ストアフロント

### 収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `productListViews` | 製品リストが表示されたかどうかを示します |
| `productListItems` | 買い物かごに追加された製品の配列 |
| `SKU` | 在庫管理単位。 商品の一意の ID。 |
| `name` | 製品の表示名または人間が読み取り可能な名前 |
| `priceTotal` | すべての割引と税金が適用された後の、この注文の合計 |
| `quantity` | 顧客が製品の必要と示した数量 |
| `discountAmount` | 適用された割引額を示します |
| `currencyCode` | この [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 商品の通貨 |
| `productImageUrl` | 製品のメイン画像 URL |
| `selectedOptions` | 設定可能な製品に使用するフィールド。 `attribute` 設定可能な製品の属性を次のように指定します。 `size` または `color` および `value` 属性の値を次のように指定します。 `small` または `black`. |
| `cartID` | 顧客の買い物かごを識別する一意の ID |

## pageView

ページが読み込まれたときにトリガーされます。 [フルスキーマ](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/page/viewAEP.ts).

### タイプ

ストアフロント

### 収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `pageViews` | ページが読み込まれたかどうかを示します。 A `value` / `1` ページが読み込まれたことを示します。 |

## productPageView

製品ページが読み込まれたときにトリガーされます。 [フルスキーマ](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/viewAEP.ts).

### タイプ

ストアフロント

### 収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `productViews` | 製品が表示されたかどうかを示します |
| `productListItems` | 買い物かごに追加された製品の配列 |
| `SKU` | 在庫管理単位。 商品の一意の ID。 |
| `name` | 製品の表示名または人間が読み取り可能な名前 |
| `priceTotal` | すべての割引と税金が適用された後の、この注文の合計 |
| `discountAmount` | 適用された割引額を示します |
| `currencyCode` | この [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 商品の通貨 |
| `productImageUrl` | 製品のメイン画像 URL |
| `selectedOptions` | 設定可能な製品に使用するフィールド。 `attribute` 設定可能な製品の属性を次のように指定します。 `size` または `color` および `value` 属性の値を次のように指定します。 `small` または `black`. |

## startCheckout

買い物客がチェックアウトボタンをクリックしたときにトリガーされます。 [フルスキーマ](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/initiateCheckoutAEP.ts).

### タイプ

ストアフロント

### 収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `checkouts` | チェックアウトプロセス中にアクションが発生したかどうかを示します |
| `productListItems` | 買い物かごに追加された製品の配列 |
| `SKU` | 在庫管理単位。 商品の一意の ID。 |
| `name` | 製品の表示名または人間が読み取り可能な名前 |
| `priceTotal` | すべての割引と税金が適用された後の、この注文の合計 |
| `quantity` | 顧客が製品の必要と示した数量 |
| `discountAmount` | 適用された割引額を示します |
| `currencyCode` | この [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 商品の通貨 |
| `productImageUrl` | 製品のメイン画像 URL |
| `selectedOptions` | 設定可能な製品に使用するフィールド。 `attribute` 設定可能な製品の属性を次のように指定します。 `size` または `color` および `value` 属性の値を次のように指定します。 `small` または `black`. |
| `cartID` | 顧客の買い物かごを識別する一意の ID |

## completeCheckout

買い物客が注文したときにトリガーされます。 [フルスキーマ](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/checkout/placeOrderAEP.ts).

### タイプ

ストアフロント

### 収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `purchases` | 注文が受け入れられたかどうかを示します |
| `order` | 1 つ以上の製品の注文に関する情報が含まれます |
| `purchaseID` | 販売者がこの購入または契約に割り当てた一意の ID。 ID が一意であるという保証はありません。 |
| `orderType` | 注文のタイプを示します（チェックアウト、即時購入など） |
| `payments` | この注文の支払いのリスト |
| `currencyCode` | この [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) この支払い項目に使用される通貨コード。 例： `USD` または `EUR`. |
| `paymentAmount` | 支払の値 |
| `paymentType` | この注文の支払い方法。 オプションは次のとおりです。 `cash`, `credit_card`, `debit_card`, `gift_card`, `check`, `paypal`, `wire_transfer`, `credit_card_reference`, `other` |
| `transactionID` | この支払い項目の一意のトランザクション識別子 |
| `shipping` | 1 つ以上の製品の出荷の詳細。 |
| `shippingMethod` | 顧客が選択した送料方法（標準配送、即時配送、店頭受け取りなど） |
| `shippingAmount` | 買い物かご内の品目の合計送料 |
| `promotionID` | プロモーションの一意の識別子（存在する場合） |
| `productListItems` | 買い物かごに追加された製品の配列 |
| `SKU` | 在庫管理単位。 商品の一意の ID。 |
| `name` | 製品の表示名または人間が読み取り可能な名前 |
| `priceTotal` | すべての割引と税金が適用された後の、この注文の合計 |
| `quantity` | 顧客が製品の必要と示した数量 |
| `discountAmount` | 適用された割引額を示します |
| `currencyCode` | この [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 注文の合計に使用する通貨コード。 |
| `productImageUrl` | 製品のメイン画像 URL |
| `selectedOptions` | 設定可能な製品に使用するフィールド。 `attribute` 設定可能な製品の属性を次のように指定します。 `size` または `color` および `value` 属性の値を次のように指定します。 `small` または `black`. |

## signIn

買い物客がログインしようとしたときにトリガーされます。 [フルスキーマ](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signInAEP.ts).

>[!NOTE]
>
> このイベントは、特定のアクションが試行されるとトリガーされます。 アクションが成功したことは示されません。

### タイプ

プロファイル

### 収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `eventType` | この時系列レコードの主なイベントタイプ。次に例を示します。 `userAccount.login` |
| `person` | 個々のアクター、連絡先、または所有者 |
| `accountID` | ユーザーアカウント ID をキャプチャします |
| `personalEmailID` | 個人用電子メールの一意の識別子を指定します |
| `address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているように |
| `userAccount` | ロイヤリティの詳細、環境設定、ログインプロセス、その他のアカウント環境設定を示します |
| `login` | 訪問者がログインしようとしたかどうかを示します |

## signOut

買い物客がサインアウトを試みたときにトリガーされます。 [フルスキーマ](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signOutAEP.ts).

>[!NOTE]
>
> このイベントは、特定のアクションが試行されるとトリガーされます。 アクションが成功したことは示されません。

### タイプ

プロファイル

### 収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `eventType` | この時系列レコードの主なイベントタイプ。次に例を示します。 `userAccount.logout` |
| `userAccount` | ロイヤリティの詳細、環境設定、ログインプロセス、その他のアカウント環境設定を示します |
| `logout` | 訪問者がログアウトしようとしたかどうかを示します |

## createAccount

買い物客がアカウントを作成しようとしたときにトリガーされます。 [フルスキーマ](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/createAccountAEP.ts).

>[!NOTE]
>
> このイベントは、特定のアクションが試行されるとトリガーされます。 アクションが成功したことは示されません。

### タイプ

プロファイル

### 収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `eventType` | この時系列レコードの主なイベントタイプ。次に例を示します。 `account.createProfile` |
| `person` | 個々のアクター、連絡先、または所有者 |
| `accountID` | ユーザーアカウント ID をキャプチャします |
| `accountType` | ユーザーアカウントタイプをキャプチャします（例： ）。 `Personal` または `Company`該当する場合は、 |
| `personalEmailID` | 個人用電子メールの一意の識別子を指定します |
| `address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているように |
| `userAccount` | ロイヤリティの詳細、環境設定、ログインプロセス、その他のアカウント環境設定を示します |
| `createProfile` | ユーザーがアカウントプロファイルを作成したかどうかを示します |

## editAccount

買い物客がアカウントを編集しようとしたときにトリガーされます。 [フルスキーマ](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/editAccountAEP.ts).

>[!NOTE]
>
> このイベントは、特定のアクションが試行されるとトリガーされます。 アクションが成功したことは示されません。

### タイプ

プロファイル

### 収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `eventType` | この時系列レコードの主なイベントタイプ。次に例を示します。 `account.updateProfile` |
| `person` | 個々のアクター、連絡先、または所有者 |
| `accountID` | ユーザーアカウント ID をキャプチャします |
| `accountType` | ユーザーアカウントタイプをキャプチャします（例： ）。 `Personal` または `Company`該当する場合は、 |
| `personalEmailID` | 個人用電子メールの一意の識別子を指定します |
| `personalEmail` | 個人の電子メールアドレスを指定 |
| `address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているように |
| `userAccount` | ロイヤリティの詳細、環境設定、ログインプロセス、その他のアカウント環境設定を示します |
| `updateProfile` | ユーザーがアカウントプロファイルを更新したかどうかを示します |

## searchRequestSent

「入力時に検索」ポップオーバーで、次のイベントによってトリガーされます。

- Enter キーを押します。
- クリック _すべて表示_

検索結果ページの次のイベントによってトリガーされます。

- フィルターを選択
- 並べ替え順を変更する (_並べ替え基準_)
- 並べ替え方向を変更（昇順または降順）
- 1 ページの結果数を変更します (_1 ページあたりの数を表示_)
- 次のページに移動します。
- 前のページに移動します。
- 別のページに移動

[フルスキーマ](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/search/searchRequestSentAEP.ts).

>[!NOTE]
>
>B2B モジュールがインストールされているAdobe Commerce Enterprise Edition では、検索イベントはサポートされていません。

### タイプ

検索

### 収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `searchRequest` | 検索リクエストが送信されたかどうかを示します |
| `filter` | 検索結果を制限するためにフィルターが適用されたかどうかを示します |
| `attribute` （フィルター） | 項目を検索結果に含めるかどうかを決定するために使用される項目のファセット |
| `value` | 検索結果に含まれる項目を決定するために使用される属性値 |
| `isRange` | true の場合、値は許容可能な値の範囲の終点を示します |
| `sort` | 検索結果の並べ替え方法を示します |
| `attribute` （並べ替え） | 検索結果の項目の並べ替えに使用する属性 |
| `order` | 検索結果を返す順序 |
| `query` | 検索された用語 |

## searchResponseReceived

「入力時に検索」ポップオーバーまたは検索結果ページの結果がライブ検索で返された場合にトリガーされます。

[フルスキーマ](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/search/searchResponseReceivedAEP.ts)

>[!NOTE]
>
>B2B モジュールがインストールされているAdobe Commerce Enterprise Edition では、検索イベントはサポートされていません。

### タイプ

検索

### 収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `searchResponse` | 検索応答を受信したかどうかを示します |
| `suggestions` | カタログに存在し、検索クエリに類似する製品とカテゴリの名前を含む文字列の配列。 |
| `numberOfResults` | 返された製品の数 |
| `productListItems` | 買い物かごに追加された製品の配列。 次を含む `SKU`（在庫管理単位）及び `name` 製品の名前（表示名または人間が読み取り可能な名前）。 |
