---
title: イベント
description: 各イベントが取り込むデータを説明します。
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: f90ef4d2732a0b0676e0899712f94b41a1c2d85a
workflow-type: tm+mt
source-wordcount: '6894'
ht-degree: 0%

---

# [!DNL Data Connection] イベント

次のリストは、 [!DNL Data Connection] 拡張子。 これらのイベントで収集されたデータは、Adobe Experience Platform Edge に送信されます。 また、 [カスタムイベント](custom-events.md) 標準で提供されていない追加データを収集する場合。

以下のイベントで収集されるデータに加えて、 [その他のデータ](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) Adobe Experience Platform Web SDK によって提供されます。

## ストアフロントイベント

ストアフロントイベントは、サイトを閲覧する買い物客から匿名化された行動データを収集します。 これらのイベントで収集されたデータを使用して、特定の買い物客セットをターゲットにしたプロモーションやキャンペーンを作成できます。 Storefront イベントデータには、シンプルで設定可能な製品のみが含まれています。

>[!NOTE]
>
>すべてのストアフロントイベントには、 [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) フィールドに含まれます。これには、買い物客の電子メールアドレス（利用可能な場合）と ECID が含まれます。 このプロファイルデータを各イベントに含めることで、Adobe Commerceから別のユーザーアカウントをインポートする必要がなくなります。

### addToCart

| 説明 | XDM イベント名 |
|---|---|
| 製品が買い物かごに追加されたとき、または買い物かご内の製品の数量が増加したときにトリガーされます。 | `commerce.productListAdds` |

#### addToCart から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `commerce.productListAdds` | 製品が買い物かごに追加されたかどうかを示します。 値： `1` は、製品が追加されたことを示します。 |
| `commerce.cart.cartID` | 顧客の買い物かごを識別する一意の ID。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |
| `productListItems` | 買い物かごに追加された製品の配列。 |
| `productListItems.SKU` | 在庫管理単位。 商品の一意の ID。 |
| `productListItems.name` | 製品の表示名または人間が読み取り可能な名前。 |
| `productListItems.priceTotal` | 製品品目の合計価格。 |
| `productListItems.quantity` | 買い物かご内の製品単位数。 |
| `productListItems.discountAmount` | 適用される割引額を示します。 |
| `productListItems.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `productListItems.productImageUrl` | 商品のメイン画像 URL。 |
| `productListItems.selectedOptions` | 設定可能な製品に使用するフィールド。 |
| `productListItems.selectedOptions.attribute` | 設定可能な製品の属性（例： ）を識別します。 `size` または `color`. |
| `productListItems.selectedOptions.value` | 属性の値を次のように指定します。 `small` または `black`. |

### openCart

| 説明 | XDM イベント名 |
|---|---|
| 新しい買い物かごが作成されたとき（製品が空の買い物かごに追加されたとき）にトリガーされます。 | `commerce.productListOpens` |

#### openCart から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `commerce.productListOpens` | 買い物かごが作成されたかどうかを示します。 値： `1` は、買い物かごが作成されたことを示します。 |
| `commerce.cart.cartID` | 顧客の買い物かごを識別する一意の ID。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |
| `productListItems` | 買い物かごに追加された製品の配列。 |
| `productListItems.SKU` | 在庫管理単位。 商品の一意の ID。 |
| `productListItems.name` | 製品の表示名または人間が読み取り可能な名前。 |
| `productListItems.priceTotal` | 製品品目の合計価格。 |
| `productListItems.quantity` | 買い物かご内の製品単位数。 |
| `productListItems.discountAmount` | 適用される割引額を示します。 |
| `productListItems.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `productListItems.productImageUrl` | 商品のメイン画像 URL。 |
| `productListItems.selectedOptions` | 設定可能な製品に使用するフィールド。 |
| `productListItems.selectedOptions.attribute` | 設定可能な製品の属性（例： ）を識別します。 `size` または `color`. |
| `productListItems.selectedOptions.value` | 属性の値を次のように指定します。 `small` または `black`. |

### removeFromCart

| 説明 | XDM イベント名 |
|---|---|
| 製品が削除されるたびに、または買い物かご内の製品の数量が減らされるたびにトリガーされます。 | `commerce.productListRemovals` |

#### removeFromCart から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `commerce.productListRemovals` | 製品が買い物かごから削除されたかどうかを示します。 値： `1` 製品が買い物かごから削除されたことを示します。 |
| `commerce.cart.cartID` | 顧客の買い物かごを識別する一意の ID。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |
| `productListItems` | 買い物かごに追加された製品の配列。 |
| `productListItems.SKU` | 在庫管理単位。 商品の一意の ID。 |
| `productListItems.name` | 製品の表示名または人間が読み取り可能な名前。 |
| `productListItems.priceTotal` | 製品品目の合計価格。 |
| `productListItems.quantity` | 買い物かご内の製品単位数。 |
| `productListItems.discountAmount` | 適用される割引額を示します。 |
| `productListItems.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `productListItems.productImageUrl` | 商品のメイン画像 URL。 |
| `productListItems.selectedOptions` | 設定可能な製品に使用するフィールド。 |
| `productListItems.selectedOptions.attribute` | 設定可能な製品の属性（例： ）を識別します。 `size` または `color`. |
| `productListItems.selectedOptions.value` | 属性の値を次のように指定します。 `small` または `black`. |

### shoppingCartView

| 説明 | XDM イベント名 |
|---|---|
| 買い物かごのページが読み込まれたときにトリガーされます。 | `commerce.productListViews` |

#### shoppingCartView から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `commerce.productListViews` | 製品リストが表示されたかどうかを示します。 |
| `commerce.cart.cartID` | 顧客の買い物かごを識別する一意の ID。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |
| `productListItems` | 買い物かごに追加された製品の配列。 |
| `productListItems.SKU` | 在庫管理単位。 商品の一意の ID。 |
| `productListItems.name` | 製品の表示名または人間が読み取り可能な名前。 |
| `productListItems.priceTotal` | 製品品目の合計価格。 |
| `productListItems.quantity` | 買い物かご内の製品単位数。 |
| `productListItems.discountAmount` | 適用される割引額を示します。 |
| `productListItems.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `productListItems.productImageUrl` | 商品のメイン画像 URL。 |
| `productListItems.selectedOptions` | 設定可能な製品に使用するフィールド。 |
| `productListItems.selectedOptions.attribute` | 設定可能な製品の属性（例： ）を識別します。 `size` または `color`. |
| `productListItems.selectedOptions.value` | 属性の値を次のように指定します。 `small` または `black`. |

### pageView

| 説明 | XDM イベント名 |
|---|---|
| ページが読み込まれたときにトリガーされます。 | `web.webpagedetails.pageViews` |

#### pageView から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `web.webPageDetails.pageViews` | ページが読み込まれたかどうかを示します。 A `value` / `1` ページが読み込まれたことを示します。 |
| `web.webPageDetails.URL` | Web ページの基準となる URL または通常の URL。 これは、ページに到達するために使用される実際の URL にすることができます。この URL は、 `Web Link`. |
| `web.webPageDetails.name` | Web ページの基準となる名前。 この名前は、必ずしもページタイトルやページコンテンツに直接関連付けられるわけではありませんが、分類目的でサイトのページを整理するために使用されます。 |
| `web.webReferrer.URL` | 買い物客がサイトへのリンクをクリックする前に訪問した Web ページの URL。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |

### productPageView

| 説明 | XDM イベント名 |
|---|---|
| 製品ページが読み込まれたときにトリガーされます。 | `commerce.productViews` |

#### productPageView から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `commerce.productViews` | 製品が表示されたかどうかを示します。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |
| `productListItems` | 買い物かごに追加された製品の配列。 |
| `productListItems.SKU` | 在庫管理単位。 商品の一意の ID。 |
| `productListItems.name` | 製品の表示名または人間が読み取り可能な名前。 |
| `productListItems.priceTotal` | 製品品目の合計価格。 |
| `productListItems.quantity` | 買い物かご内の製品単位数。 |
| `productListItems.discountAmount` | 適用される割引額を示します。 |
| `productListItems.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `productListItems.productImageUrl` | 商品のメイン画像 URL。 |
| `productListItems.selectedOptions` | 設定可能な製品に使用するフィールド。 |
| `productListItems.selectedOptions.attribute` | 設定可能な製品の属性（例： ）を識別します。 `size` または `color`. |
| `productListItems.selectedOptions.value` | 属性の値を次のように指定します。 `small` または `black`. |

### startCheckout

| 説明 | XDM イベント名 |
|---|---|
| 買い物客がチェックアウトボタンをクリックしたときにトリガーされます。 | `commerce.checkouts` |

#### startCheckout から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `commerce.checkouts` | チェックアウトプロセス中にアクションが発生したかどうかを示します。 |
| `commerce.cart.cartID` | 顧客の買い物かごを識別する一意の ID。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |
| `productListItems` | 買い物かごに追加された製品の配列。 |
| `productListItems.SKU` | 在庫管理単位。 商品の一意の ID。 |
| `productListItems.name` | 製品の表示名または人間が読み取り可能な名前。 |
| `productListItems.priceTotal` | 製品品目の合計価格。 |
| `productListItems.quantity` | 買い物かご内の製品単位数。 |
| `productListItems.discountAmount` | 適用される割引額を示します。 |
| `productListItems.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `productListItems.productImageUrl` | 商品のメイン画像 URL。 |
| `productListItems.selectedOptions` | 設定可能な製品に使用するフィールド。 |
| `productListItems.selectedOptions.attribute` | 設定可能な製品の属性（例： ）を識別します。 `size` または `color`. |
| `productListItems.selectedOptions.value` | 属性の値を次のように指定します。 `small` または `black`. |

### completeCheckout

| 説明 | XDM イベント名 |
|---|---|
| 買い物客が注文したときにトリガーされます。 | `commerce.order` |

#### completeCheckout から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `commerce.purchases` | 注文が受け入れられたかどうかを示します。 |
| `commerce.order` | 1 つ以上の製品の注文に関する情報が含まれます。 |
| `commerce.order.purchaseID` | 販売者がこの購入または契約に割り当てた一意の ID。 ID が一意であるという保証はありません。 |
| `commerce.order.payments` | この注文の支払いのリスト。 |
| `commerce.order.payments.paymentTransactionID` | この支払トランザクションの一意の ID。 |
| `commerce.order.payments.paymentAmount` | 支払の値。 |
| `commerce.order.payments.paymentType` | この注文の支払い方法。 オプションは次のとおりです。 `cash`, `credit_card`, `debit_card`, `gift_card`, `check`, `paypal`, `wire_transfer`, `credit_card_reference`, `other`. |
| `commerce.order.payments.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `commerce.order.taxAmount` | 最終支払いの一環として購入者が支払った税額。 |
| `commerce.order.discountAmount` | 注文全体に適用される割引額を示します。 |
| `commerce.order.createdDate` | コマースシステムで新しい注文が作成された日時。 例： `2022-10-15T20:20:39+00:00`. |
| `commerce.shipping` | 1 つ以上の製品の出荷の詳細。 |
| `commerce.shipping.shippingMethod` | 顧客が選択した送料方法（標準配送、即時配送、店頭受け取りなど）。 |
| `commerce.shipping.shippingAmount` | 顧客が送料を支払う必要があった金額。 |  | `shipping` | 1 つ以上の製品の出荷の詳細。 |
| `commerce.shipping.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |
| `personalEmail` | 個人の電子メールアドレス。 |
| `personalEmail.address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているとおりです。 |
| `productListItems` | 買い物かごに追加された製品の配列。 |
| `productListItems.SKU` | 在庫管理単位。 商品の一意の ID。 |
| `productListItems.name` | 製品の表示名または人間が読み取り可能な名前。 |
| `productListItems.priceTotal` | 製品品目の合計価格。 |
| `productListItems.quantity` | 買い物かご内の製品単位数。 |
| `productListItems.discountAmount` | 適用される割引額を示します。 |
| `productListItems.productImageUrl` | 商品のメイン画像 URL。 |
| `productListItems.selectedOptions` | 設定可能な製品に使用するフィールド。 |
| `productListItems.selectedOptions.attribute` | 設定可能な製品の属性（例： ）を識別します。 `size` または `color`. |
| `productListItems.selectedOptions.value` | 属性の値を次のように指定します。 `small` または `black`. |

## プロファイルイベント

プロファイルイベントには、 `signIn`, `signOut`, `createAccount`、および `editAccount`. このデータは、セグメントをより適切に定義したり、マーケティングキャンペーンを実行したりするために必要な顧客の主要な詳細情報を入力するのに役立ちます。例えば、ニューヨークに住む買い物客をターゲットに設定する場合などです。

### signIn

| 説明 | XDM イベント名 |
|---|---|
| 買い物客がログインしようとしたときにトリガーされます。 | `userAccount.login` |

>[!NOTE]
>
> このイベントは、特定のアクションが試行されるとトリガーされます。 アクションが成功したことは示されません。

#### signIn から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `person` | 個々のアクター、連絡先、または所有者。 |
| `person.accountID` | ユーザーアカウント ID をキャプチャします。 |
| `person.accountType` | ユーザーアカウントタイプをキャプチャします（例： ）。 `Personal` または `Company`（該当する場合） |
| `person.personalEmailID` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているとおりです。 |
| `personalEmail` | 連絡先の詳細をキャプチャします — 電子メールと関連情報。 |
| `personalEmail.address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているとおりです。 |
| `userAccount` | ロイヤリティの詳細、環境設定、ログインプロセス、その他のアカウント環境設定を示します。 |
| `userAccount.login` | 訪問者がログインしようとしたかどうかを示します。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |

### signOut

| 説明 | XDM イベント名 |
|---|---|
| 買い物客がサインアウトを試みたときにトリガーされます。 | `userAccount.logout` |

>[!NOTE]
>
> このイベントは、特定のアクションが試行されるとトリガーされます。 アクションが成功したことは示されません。

#### signOut から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `userAccount` | ロイヤリティの詳細、環境設定、ログインプロセス、その他のアカウント環境設定を示します。 |
| `userAccount.logout` | 訪問者がログアウトしようとしたかどうかを示します。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |

### createAccount

| 説明 | XDM イベント名 |
|---|---|
| 買い物客がアカウントを作成しようとしたときにトリガーされます。 | `userAccount.createProfile` |

>[!NOTE]
>
> このイベントは、特定のアクションが試行されるとトリガーされます。 アクションが成功したことは示されません。

#### createAccount から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `person` | 個々のアクター、連絡先、または所有者。 |
| `person.accountID` | ユーザーアカウント ID をキャプチャします。 |
| `person.accountType` | ユーザーアカウントタイプをキャプチャします（例： ）。 `Personal` または `Company`（該当する場合） |
| `person.personalEmailID` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているとおりです。 |
| `personalEmail` | 連絡先の詳細をキャプチャします — 電子メールと関連情報。 |
| `personalEmail.address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているとおりです。 |
| `userAccount` | ロイヤリティの詳細、環境設定、ログインプロセス、その他のアカウント環境設定を示します。 |
| `userAccount.updateProfile` | ユーザーがアカウントプロファイルを更新したかどうかを示します。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |

### editAccount

| 説明 | XDM イベント名 |
|---|---|
| 買い物客がアカウントを編集しようとしたときにトリガーされます。 | `userAccount.updateProfile` |

>[!NOTE]
>
> このイベントは、特定のアクションが試行されるとトリガーされます。 アクションが成功したことは示されません。

#### editAccount から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `person` | 個々のアクター、連絡先、または所有者。 |
| `person.accountID` | ユーザーアカウント ID をキャプチャします。 |
| `person.accountType` | ユーザーアカウントタイプをキャプチャします（例： ）。 `Personal` または `Company`（該当する場合） |
| `person.personalEmailID` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているとおりです。 |
| `personalEmail` | 連絡先の詳細をキャプチャします — 電子メールと関連情報。 |
| `personalEmail.address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているとおりです。 |
| `userAccount` | ロイヤリティの詳細、環境設定、ログインプロセス、その他のアカウント環境設定を示します。 |
| `userAccount.updateProfile` | ユーザーがアカウントプロファイルを更新したかどうかを示します。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |

## イベントを検索

検索イベントは、買い物客の意図に関連するデータを提供します。 買い物客の意図をインサイトすることで、買い物客が品目、クリックしたもの、最終的に購入または放棄をどのように検索しているかを知ることができます。 このデータの使用例は、トップ商品を検索しても商品を購入しない既存の買い物客をターゲットにしたい場合です。

以下を使用します。 `searchRequest.id` および `searchResponse.id` 両方の `searchRequestSent` および `searchResponseReceived` イベントを使用して、検索リクエストを対応する検索応答に相互参照できます。

### searchRequestSent

| 説明 | XDM イベント名 |
|---|---|
| 「入力時に検索」ポップオーバーで、次のイベントによってトリガーされます。<br><br>[Enter] を押し、をクリックします。 _すべて表示_<br><br>&#x200B;検索結果ページの次のイベントによってトリガーされます。<br><br>フィルターを選択し、並べ替え順を変更します (_並べ替え基準_)、並べ替え方向（昇順または降順）を変更、ページごとの結果数を変更 (_1 ページあたりの数を表示_)、次のページに移動、前のページに移動、別のページに移動 | `searchRequest` |

>[!NOTE]
>
>B2B 拡張機能がインストールされているAdobe Commerce Enterprise Edition では、検索イベントはサポートされていません。

#### searchRequestSent から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `searchRequest` | 検索リクエストが送信されたかどうかを示します。 |
| `searchRequest.id` | この特定の検索リクエストの一意の ID。 |
| `searchRequest.value` | リクエストの定量化可能な値。 |
| `siteSearch` | 検索に関する情報が含まれます。 |
| `siteSearch.filter` | 検索結果を制限するためにフィルターが適用されたかどうかを示します。 |
| `siteSearch.filter.attribute` （フィルター） | 項目を検索結果に含めるかどうかを決定するために使用される項目のファセット。 |
| `siteSearch.filter.isRange` | true の場合、値は許容可能な値の範囲の終点を示します。 |
| `siteSearch.filter.value` | 検索結果に含まれる項目を決定するために使用される属性値。 |
| `siteSearch.sort` | 検索結果の並べ替え方法を示します。 |
| `siteSearch.sort.attribute` （並べ替え） | 検索結果内の項目の並べ替えに使用する属性。 |
| `siteSearch.sort.order` | 検索結果を返す順序。 |
| `siteSearch.query` | 検索された用語。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |

### searchResponseReceived

| 説明 | XDM イベント名 |
|---|---|
| 「入力時に検索」ポップオーバーまたは検索結果ページの結果がライブ検索で返された場合にトリガーされます。 | `searchResponse` |

>[!NOTE]
>
>B2B 拡張機能がインストールされているAdobe Commerce Enterprise Edition では、検索イベントはサポートされていません。

#### searchResponseReceived から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `searchResponse` | 検索応答が受信されたかどうかを示します。 |
| `searchResponse.id` | この特定の検索応答の一意の ID。 |
| `searchResponse.value` | 応答の定量化可能な値。 |
| `siteSearch.numberOfResults` | 返された製品の数。 |
| `siteSearch.suggestions` | カタログに存在し、検索クエリに類似する製品とカテゴリの名前を含む文字列の配列。 |
| `productListItems` | 買い物かごに追加された製品の配列。 |
| `productListItems.SKU` | 在庫管理単位。 商品の一意の ID。 |
| `productListItems.name` | 製品の表示名または人間が読み取り可能な名前。 |
| `productListItems.productImageUrl` | 商品のメイン画像 URL。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |

## B2B イベント

![Adobe Commerce用 B2B](../assets/b2b.svg) B2B 商人の場合は、 [install](install.md#install-the-b2b-extension) の `experience-platform-connector-b2b` 拡張機能を使用して、これらのイベントを有効にします。

B2B イベントには、 [購買依頼リスト](https://experienceleague.adobe.com/docs/commerce-admin/b2b/requisition-lists/requisition-lists.html) 情報（購買依頼リストが作成、追加、削除された場合など）。 購買依頼リストに固有のイベントを追跡することで、顧客が頻繁に購入する製品を確認し、そのデータに基づいてキャンペーンを作成できます。

### createRequisitionList

| 説明 | XDM イベント名 |
|---|---|
| 買い物客が購入依頼リストを作成したときにトリガーされます。 | `commerce.requisitionListOpens` |

#### createReqisitionList から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `commerce.requisitionListOpens` | 新しい購買依頼リストの初期化を示します。 |
| `commerce.requisitionList` | 顧客が作成した購買依頼リストのプロパティ。 |
| `commerce.requisitionList.ID` | 購買依頼リストの一意の ID。 |
| `commerce.requisitionList.name` | 顧客が指定した購買依頼リストの名前。 |
| `commerce.requisitionList.description` | 顧客が指定した購買依頼リストの説明。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |

### addToRequisitionList

| 説明 | XDM イベント名 |
|---|---|
| 買い物客が既存の購買依頼リストに製品を追加したとき、またはリストの作成中にトリガーされます。 | `commerce.requisitionListAdds` |

#### addToRequisitionList から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `commerce.requisitionListAdds` | 購買依頼リストに 1 つ以上の製品を追加することを示します。 |
| `commerce.requisitionList` | 顧客が作成した購買依頼リストのプロパティ。 |
| `commerce.requisitionList.ID` | 購買依頼リストの一意の ID。 |
| `commerce.requisitionList.name` | 顧客が指定した購買依頼リストの名前。 |
| `commerce.requisitionList.description` | 顧客が指定した購買依頼リストの説明。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |
| `productListItems` | 購買依頼リストに追加された製品の配列。 |
| `productListItems.SKU` | 在庫管理単位。 商品の一意の ID。 |
| `productListItems.name` | 製品の表示名または人間が読み取り可能な名前。 |
| `productListItems.priceTotal` | 製品品目の合計価格。 |
| `productListItems.quantity` | 買い物かご内の製品単位数。 |
| `productListItems.discountAmount` | 適用される割引額を示します。 |
| `productListItems.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `productListItems.selectedOptions` | 設定可能な製品に使用するフィールド。 |
| `productListItems.selectedOptions.attribute` | 設定可能な製品の属性（例： ）を識別します。 `size` または `color`. |
| `productListItems.selectedOptions.value` | 属性の値を次のように指定します。 `small` または `black`. |

### removeFromRequisitionList

| 説明 | XDM イベント名 |
|---|---|
| 買い物客が購買依頼リストから製品を削除した場合にトリガーされます。 | `commerce.requisitionListRemovals` |

#### removeFromRequisitionList から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `commerce.requsitionListRemovals` | 1 つ以上の製品を購買依頼リストから削除することを示します。 |
| `commerce.requisitionList` | 顧客が作成した購買依頼リストのプロパティ。 |
| `commerce.requisitionList.ID` | 購買依頼リストの一意の ID。 |
| `commerce.requisitionList.name` | 顧客が指定した購買依頼リストの名前。 |
| `commerce.requisitionList.description` | 顧客が指定した購買依頼リストの説明。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |
| `productListItems` | 購買依頼リストに追加された製品の配列。 |
| `productListItems.SKU` | 在庫管理単位。 商品の一意の ID。 |
| `productListItems.name` | 製品の表示名または人間が読み取り可能な名前。 |
| `productListItems.priceTotal` | 製品品目の合計価格。 |
| `productListItems.quantity` | 買い物かご内の製品単位数。 |
| `productListItems.discountAmount` | 適用される割引額を示します。 |
| `productListItems.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `productListItems.selectedOptions` | 設定可能な製品に使用するフィールド。 |
| `productListItems.selectedOptions.attribute` | 設定可能な製品の属性（例： ）を識別します。 `size` または `color`. |
| `productListItems.selectedOptions.value` | 属性の値を次のように指定します。 `small` または `black`. |

## バックオフィスイベント

バックオフィスイベントには、注文が発行されたか、キャンセルされたか、返金されたか、発送されたか、完了したかなど、注文の状態に関する情報が含まれます。 これらのサーバー側イベントが収集するデータは、買い物客の注文を 360 ビュー表示します。 マーチャントがマーケティングキャンペーンを開発する際に、オーダーステータス全体をより適切にターゲティングまたは分析できるようになります。 例えば、ある製品カテゴリの傾向を、年の異なる時期に好調に推移している項目で見分けることができます。 例えば、寒い数ヶ月の間により良く売れる冬の服や、買い物客が長年興味を持つ特定の製品の色。 また、注文ステータスデータは、以前の注文に基づいてコンバージョンする買い物客の傾向を把握することで、全期間顧客価値の計算に役立ちます。

>[!NOTE]
>
>すべてのバックオフィスイベントには、 [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) フィールドに格納されます。 このプロファイルデータを各イベントに含めることで、Adobe Commerceから別のユーザーアカウントをインポートする必要がなくなります。

### orderPlaced

| 説明 | XDM イベント名 |
|---|---|
| 買い物客が注文したときにトリガーされます。 | `commerce.backofficeOrderPlaced` |

#### orderPlaced から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `commerce.order` | オーダーに関する情報が含まれます。 |
| `commerce.order.purchaseID` | 販売者がこの購入または契約に割り当てた一意の ID。 ID が一意であるという保証はありません。 |
| `commerce.order.payments` | この注文の支払いのリスト。 |
| `commerce.order.payments.paymentTransactionID` | この支払トランザクションの一意の ID。 |
| `commerce.order.payments.paymentAmount` | 支払の値。 |
| `commerce.order.payments.paymentType` | この注文の支払い方法。 カウント済み、カスタム値を使用可能 |
| `commerce.order.payments.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `commerce.order.taxAmount` | 最終支払いの一環として購入者が支払った税額。 |
| `commerce.order.discountAmount` | 注文全体に適用される割引額を示します。 |
| `commerce.order.createdDate` | コマースシステムで新しい注文が作成された日時。 例： `2022-10-15T20:20:39+00:00`. |
| `commerce.order.currencyCode` | 注文の合計に使用される ISO 4217 通貨コード。 |
| `commerce.shipping` | 1 つ以上の製品の出荷の詳細。 |
| `commerce.shipping.shippingMethod` | 顧客が選択した送料方法（標準配送、即時配送、店頭受け取りなど）。 |
| `commerce.shipping.shippingAmount` | 顧客が送料を支払う必要があった金額。 |
| `commerce.shipping.currencyCode` | 送料合計に使用する ISO 4217 通貨コード。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |
| `commerce.billing.address` | 請求先住所。 |
| `commerce.billing.address.street1` | プライマリの番地の情報、アパート番号、番地、および番地 |
| `commerce.billing.address.street2` | 番地レベル情報の追加フィールド。 |
| `commerce.billing.address.city` | 市区町村の名前。 |
| `commerce.billing.address.state` | 州の名前。 これは自由形式のフィールドです。 |
| `commerce.billing.address.postalCode` | 場所の郵便番号。 一部の国では、郵便番号が使用できません。 一部の国では、郵便番号の一部のみが含まれます。 |
| `commerce.billing.address.country` | 政府が管理する領土の名前。 次の値以外： `xdm:countryCode`の場合、任意の言語で国名を付けることができる自由形式のフィールドです。 |
| `personalEmail` | 個人の電子メールアドレス。 |
| `personalEmail.address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているとおりです。 |
| `productListItems` | 注文内の製品の配列。 |
| `productListItems.id` | この製品エントリの品目識別子。 |
| `productListItems.SKU` | 在庫管理単位。 商品の一意の ID。 |
| `productListItems.name` | 製品の表示名または人間が読み取り可能な名前。 |
| `productListItems.priceTotal` | 製品品目の合計価格。 |
| `productListItems.quantity` | 買い物かご内の製品単位数。 |
| `productListItems.discountAmount` | 適用される割引額を示します。 |
| `productListItems.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `productListItems.selectedOptions` | 設定可能な製品に使用するフィールド。 |
| `productListItems.selectedOptions.attribute` | 設定可能な製品の属性（例： ）を識別します。 `size` または `color`. |
| `productListItems.selectedOptions.value` | 属性の値を次のように指定します。 `small` または `black`. |
| `productListItems.categories` | 製品のカテゴリに関する情報が含まれます。 |
| `productListItems.categories.id` | カテゴリの一意の ID。 |
| `productListItems.categories.name` | カテゴリの名前。 |
| `productListItems.categories.path` | カテゴリへのパス。 |
| `productListItems.productImageUrl` | 商品のメイン画像 URL。 |

### orderInvoiled

| 説明 | XDM イベント名 |
|---|---|
| 商人が請求書を送信して支払を要求する際にトリガーされます。 | `commerce.backofficeOrderInvoiced` |

#### orderInviled から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `commerce.order` | オーダーに関する情報が含まれます。 |
| `commerce.order.purchaseID` | 販売者がこの購入または契約に割り当てた一意の ID。 ID が一意であるという保証はありません。 |
| `commerce.order.priceTotal` | すべての割引と税金が適用された後の、この注文の合計価格。 |
| `commerce.order.currencyCode` | 注文の合計に使用される ISO 4217 通貨コード。 |
| `commerce.order.purchaseOrderNumber` | 購入者がこの購入または契約に割り当てた一意の ID。 |
| `commerce.order.payments` | この注文の支払いのリスト。 |
| `commerce.order.payments.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `commerce.order.payments.paymentType` | この注文の支払い方法。 カウント済み、カスタム値を使用可能 |
| `commerce.order.payments.paymentAmount` | 支払の値。 |
| `commerce.shipping` | 1 つ以上の製品の出荷の詳細。 |
| `commerce.shipping.shippingMethod` | 顧客が選択した送料方法（標準配送、即時配送、店頭受け取りなど）。 |
| `commerce.shipping.shippingAmount` | 顧客が送料を支払う必要があった金額。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |
| `personalEmail` | 個人の電子メールアドレス。 |
| `personalEmail.address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているとおりです。 |
| `productListItems` | 注文内の製品の配列。 |
| `productListItems.id` | この製品エントリの品目識別子。 |
| `productListItems.SKU` | 在庫管理単位。 商品の一意の ID。 |
| `productListItems.name` | 製品の表示名または人間が読み取り可能な名前。 |
| `productListItems.priceTotal` | 製品品目の合計価格。 |
| `productListItems.quantity` | 買い物かご内の製品単位数。 |
| `productListItems.discountAmount` | 適用される割引額を示します。 |
| `productListItems.categories` | 製品のカテゴリに関する情報が含まれます。 |
| `productListItems.categories.id` | カテゴリの一意の ID。 |
| `productListItems.categories.name` | カテゴリの名前。 |
| `productListItems.categories.path` | カテゴリへのパス。 |

### orderItemsShipped

| 説明 | XDM イベント名 |
|---|---|
| 注文が発送されたときにトリガーされます。 | `commerce.backofficeOrderItemsShipped` |

#### orderItemsShipped から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `commerce.order` | オーダーに関する情報が含まれます。 |
| `commerce.order.purchaseID` | 販売者がこの購入または契約に割り当てた一意の ID。 ID が一意であるという保証はありません。 |
| `commerce.order.payments` | この注文の支払いのリスト。 |
| `commerce.order.payments.paymentTransactionID` | この支払トランザクションの一意の ID。 |
| `commerce.order.payments.paymentAmount` | 支払の値。 |
| `commerce.order.payments.paymentType` | この注文の支払い方法。 カウント済み、カスタム値を使用可能 |
| `commerce.order.payments.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `commerce.order.priceTotal` | すべての割引と税金が適用された後の、この注文の合計価格。 |
| `commerce.order.purchaseOrderNumber` | 購入者がこの購入または契約に割り当てた一意の ID。 |
| `commerce.order.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `commerce.order.lastUpdatedDate` | コマースシステムで特定の注文レコードが最後に更新された時刻。 |
| `commerce.shipping` | 1 つ以上の製品の出荷の詳細。 |
| `commerce.shipping.shippingMethod` | 顧客が選択した送料方法（標準配送、即時配送、店頭受け取りなど）。 |
| `commerce.shipping.shippingAmount` | 顧客が送料を支払う必要があった金額。 |
| `commerce.shipping.address` | 実際の配送先住所。 |
| `commerce.shipping.address.street1` | プライマリの番地の情報、アパート番号、番地、および番地。 |
| `commerce.shipping.address.street2` | 2 行目（オプション） |
| `commerce.shipping.address.city` | 市区町村の名前。 |
| `commerce.shipping.address.state` | 都道府県の名前。 これは自由形式のフィールドです。 |
| `commerce.shipping.address.postalCode` | 場所の郵便番号。 一部の国では、郵便番号が使用できません。 一部の国では、郵便番号の一部のみが含まれます。 |
| `commerce.shipping.address.country` | 政府が管理する領土の名前。 次の値以外： `xdm:countryCode`の場合、任意の言語で国名を付けることができる自由形式のフィールドです。 |
| `commerce.shipping.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `commerce.shipping.trackingNumber` | 発注品目の出荷に対して出荷業者が提供する追跡番号。 |
| `commerce.shipping.trackingURL` | 注文項目の発送ステータスを追跡する URL。 |
| `commerce.shipping.shipDate` | 1 つ以上の注文品が出荷された日付。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |
| `commerce.billing.address` | 請求先住所。 |
| `commerce.billing.address.street1` | プライマリの番地の情報、アパート番号、番地、および番地 |
| `commerce.billing.address.street2` | 番地レベル情報の追加フィールド。 |
| `commerce.billing.address.city` | 市区町村の名前。 |
| `commerce.billing.address.state` | 州の名前。 これは自由形式のフィールドです。 |
| `commerce.billing.address.postalCode` | 場所の郵便番号。 一部の国では、郵便番号が使用できません。 一部の国では、郵便番号の一部のみが含まれます。 |
| `commerce.billing.address.country` | 政府が管理する領土の名前。 次の値以外： `xdm:countryCode`の場合、任意の言語で国名を付けることができる自由形式のフィールドです。 |
| `personalEmail` | 個人の電子メールアドレス。 |
| `personalEmail.address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているとおりです。 |
| `productListItems` | 注文内の製品の配列。 |
| `productListItems.SKU` | 在庫管理単位。 商品の一意の ID。 |
| `productListItems.name` | 製品の表示名または人間が読み取り可能な名前。 |
| `productListItems.priceTotal` | 製品品目の合計価格。 |
| `productListItems.quantity` | 買い物かご内の製品単位数。 |
| `productListItems.discountAmount` | 適用される割引額を示します。 |
| `productListItems.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `productListItems.selectedOptions` | 設定可能な製品に使用するフィールド。 |
| `productListItems.selectedOptions.attribute` | 設定可能な製品の属性（例： ）を識別します。 `size` または `color`. |
| `productListItems.selectedOptions.value` | 属性の値を次のように指定します。 `small` または `black`. |
| `productListItems.categories` | 製品のカテゴリに関する情報が含まれます。 |
| `productListItems.categories.id` | カテゴリの一意の ID。 |
| `productListItems.categories.name` | カテゴリの名前。 |
| `productListItems.categories.path` | カテゴリへのパス。 |

### orderCancelled

| 説明 | XDM イベント名 |
|---|---|
| 買い物客が注文をキャンセルした場合にトリガーされます。 | `commerce.backofficeOrderCancelled` |

#### orderCancelled から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `commerce.order` | オーダーに関する情報が含まれます。 |
| `commerce.order.purchaseID` | 販売者がこの購入または契約に割り当てた一意の ID。 ID が一意であるという保証はありません。 |
| `commerce.order.purchaseOrderNumber` | 購入者がこの購入または契約に割り当てた一意の ID。 |
| `commerce.order.cancelDate` | 買い物客が注文をキャンセルした日時。 |
| `commerce.order.lastUpdatedDate` | コマースシステムで特定の注文レコードが最後に更新された時刻。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |
| `personalEmail` | 個人の電子メールアドレス。 |
| `personalEmail.address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているとおりです。 |

### orderLineItemRefunded

| 説明 | XDM イベント名 |
|---|---|
| 返された品目に対して買い物客が払い戻された場合にトリガーされます。 | `commerce.backofficeCreditMemoIssued` |

#### orderLineItemRefunded から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `commerce.order` | オーダーに関する情報が含まれます。 |
| `commerce.order.purchaseID` | 販売者がこの購入または契約に割り当てた一意の ID。 ID が一意であるという保証はありません。 |
| `commerce.order.lastUpdatedDate` | コマースシステムで特定の注文レコードが最後に更新された時刻。 |
| `commerce.order.purchaseOrderNumber` | 購入者がこの購入または契約に割り当てた一意の ID。 |
| `commerce.refunds` | この注文の返金のリスト。 |
| `commerce.refunds.transactionID` | この返金の一意の ID。 |
| `commerce.refunds.refundAmount` | 払い戻しの値。 |
| `commerce.refunds.refundPaymentType` | この注文の支払い方法。 カウント済み、カスタム値を使用可能 |
| `commerce.refunds.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `personalEmail` | 個人の電子メールアドレス。 |
| `personalEmail.address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているとおりです。 |
| `productListItems` | 注文内の製品の配列。 |
| `productListItems.SKU` | 在庫管理単位。 商品の一意の ID。 |
| `productListItems.name` | 製品の表示名または人間が読み取り可能な名前。 |
| `productListItems.priceTotal` | 製品品目の合計価格。 |
| `productListItems.quantity` | 買い物かご内の製品単位数。 |
| `productListItems.discountAmount` | 適用される割引額を示します。 |
| `productListItems.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `productListItems.selectedOptions` | 設定可能な製品に使用するフィールド。 |
| `productListItems.selectedOptions.attribute` | 設定可能な製品の属性（例： ）を識別します。 `size` または `color`. |
| `productListItems.selectedOptions.value` | 属性の値を次のように指定します。 `small` または `black`. |
| `productListItems.categories` | 製品のカテゴリに関する情報が含まれます。 |
| `productListItems.categories.id` | カテゴリの一意の ID。 |
| `productListItems.categories.name` | カテゴリの名前。 |
| `productListItems.categories.path` | カテゴリへのパス。 |

### orderItemsReturnInitiated

| 説明 | XDM イベント名 |
|---|---|
| 買い物客が品目の返却をリクエストした場合にトリガーされます。 | `commerce.backofficeOrderItemsReturnInitiated` |

#### orderItemsReturnInitiated から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `commerce.order` | オーダーに関する情報が含まれます。 |
| `commerce.order.purchaseID` | 販売者がこの購入または契約に割り当てた一意の ID。 ID が一意であるという保証はありません。 |
| `commerce.order.returns` | この受注の RMA(Return Murchandise Authorization) 情報。 |
| `commerce.order.returns.returnID` | この RMA の一意の ID(Return Murchandise Authorization)。 |
| `commerce.order.returns.returnStatus` | RMA のステータス (Return Murchandise Authorization)。保留、クローズなど。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |
| `personalEmail` | 個人の電子メールアドレス。 |
| `personalEmail.address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているとおりです。 |
| `productListItems` | 注文内の製品の配列。 |
| `productListItems.SKU` | 在庫管理単位。 商品の一意の ID。 |
| `productListItems.name` | 製品の表示名または人間が読み取り可能な名前。 |
| `productListItems.quantity` | 買い物かご内の製品単位数。 |
| `productListItems.selectedOptions` | 設定可能な製品に使用するフィールド。 |
| `productListItems.selectedOptions.attribute` | 設定可能な製品の属性（例： ）を識別します。 `size` または `color`. |
| `productListItems.selectedOptions.value` | 属性の値を次のように指定します。 `small` または `black`. |
| `productListItems.categories` | 製品のカテゴリに関する情報が含まれます。 |
| `productListItems.categories.id` | カテゴリの一意の ID。 |
| `productListItems.categories.name` | カテゴリの名前。 |
| `productListItems.categories.path` | カテゴリへのパス。 |
| `productListItems.returnItem` | この品目の RMA(Return Murchandise Authorization) 情報。 |
| `productListItems.returnItem.returnStatus` | 返される項目のステータス（保留中、承認済みなど）。 |
| `productListItems.returnItem.returnReason` | この項目の返品が要求された理由。 |
| `productListItems.returnItem.returnItemCondition` | 返品が要求された品目の条件。 |
| `productListItems.returnItem.returnResolution` | 返金、交換など、返品されるアイテムの要求された解決。 |
| `productListItems.returnItem.returnQuantityRequested` | 買い物客が返すように要求したこの項目の数。 |
| `productListItems.returnItem.returnQuantityAuthorized` | 返却を許可されたこの項目の数。 |
| `productListItems.returnItem.eturnQuantityReceived` | 返された項目の数。 |
| `productListItems.returnItem.returnQuantityApproved` | 完全に完了し、承認されたこの項目の数。 |

### orderItemReturnCompleted

| 説明 | XDM イベント名 |
|---|---|
| 買い物客が返品をリクエストした品目が完了したときにトリガーされます。 | `commerce.backofficeOrderItemsReturnCompleted` |

#### orderItemReturnCompleted から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `commerce.order` | オーダーに関する情報が含まれます。 |
| `commerce.order.purchaseID` | 販売者がこの購入または契約に割り当てた一意の ID。 ID が一意であるという保証はありません。 |
| `commerce.order.returns` | この受注の RMA(Return Murchandise Authorization) 情報。 |
| `commerce.order.returns.returnID` | この RMA の一意の ID(Return Murchandise Authorization)。 |
| `commerce.order.returns.returnStatus` | RMA のステータス (Return Murchandise Authorization)。保留、クローズなど。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |
| `personalEmail` | 個人の電子メールアドレス。 |
| `personalEmail.address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているとおりです。 |
| `productListItems` | 注文内の製品の配列。 |
| `productListItems.SKU` | 在庫管理単位。 商品の一意の ID。 |
| `productListItems.name` | 製品の表示名または人間が読み取り可能な名前。 |
| `productListItems.selectedOptions` | 設定可能な製品に使用するフィールド。 |
| `productListItems.selectedOptions.attribute` | 設定可能な製品の属性（例： ）を識別します。 `size` または `color`. |
| `productListItems.selectedOptions.value` | 属性の値を次のように指定します。 `small` または `black`. |
| `productListItems.categories` | 製品のカテゴリに関する情報が含まれます。 |
| `productListItems.categories.id` | カテゴリの一意の ID。 |
| `productListItems.categories.name` | カテゴリの名前。 |
| `productListItems.categories.path` | カテゴリへのパス。 |
| `productListItems.returnItem` | この品目の RMA(Return Murchandise Authorization) 情報。 |
| `productListItems.returnItem.returnStatus` | 返される項目のステータス（保留中、承認済みなど）。 |
| `productListItems.returnItem.returnReason` | この項目の返品が要求された理由。 |
| `productListItems.returnItem.returnItemCondition` | 返品が要求された品目の条件。 |
| `productListItems.returnItem.returnResolution` | 返金、交換など、返品されるアイテムの要求された解決。 |
| `productListItems.returnItem.returnQuantityRequested` | 買い物客が返すように要求したこの項目の数。 |
| `productListItems.returnItem.returnQuantityAuthorized` | 返却を許可されたこの項目の数。 |
| `productListItems.returnItem.eturnQuantityReceived` | 返された項目の数。 |
| `productListItems.returnItem.returnQuantityApproved` | 完全に完了し、承認されたこの項目の数。 |

### orderShipmentCompleted

| 説明 | XDM イベント名 |
|---|---|
| 出荷が完了したときにトリガーされます。 | `commerce.backofficeOrderShipmentCompleted` |

#### orderShipmentCompleted から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `commerce.order` | オーダーに関する情報が含まれます。 |
| `commerce.order.purchaseID` | 販売者がこの購入または契約に割り当てた一意の ID。 ID が一意であるという保証はありません。 |
| `commerce.order.payments` | この注文の支払いのリスト。 |
| `commerce.order.payments.paymentTransactionID` | この支払トランザクションの一意の ID。 |
| `commerce.order.payments.paymentAmount` | 支払の値。 |
| `commerce.order.payments.paymentType` | この注文の支払い方法。 カウント済み、カスタム値を使用可能 |
| `commerce.order.payments.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `commerce.order.taxAmount` | 最終支払いの一環として購入者が支払った税額。 |
| `commerce.order.createdDate` | コマースシステムで新しい注文が作成された日時。 例： `2022-10-15T20:20:39+00:00`. |
| `commerce.shipping` | 1 つ以上の製品の出荷の詳細。 |
| `commerce.shipping.shippingMethod` | 顧客が選択した送料方法（標準配送、即時配送、店頭受け取りなど）。 |
| `commerce.shipping.shippingAmount` | 顧客が送料を支払う必要があった金額。 |
| `commerce.shipping.shipDate` | 1 つ以上の注文品が出荷された日付。 |
| `commerce.shipping.address` | 実際の配送先住所。 |
| `commerce.shipping.address.street1` | プライマリの番地の情報、アパート番号、番地、および番地。 |
| `commerce.shipping.address.street2` | 2 行目（オプション） |
| `commerce.shipping.address.city` | 市区町村の名前。 |
| `commerce.shipping.address.state` | 都道府県の名前。 これは自由形式のフィールドです。 |
| `commerce.shipping.address.postalCode` | 場所の郵便番号。 一部の国では、郵便番号が使用できません。 一部の国では、郵便番号の一部のみが含まれます。 |
| `commerce.shipping.address.country` | 政府が管理する領土の名前。 次の値以外： `xdm:countryCode`の場合、任意の言語で国名を付けることができる自由形式のフィールドです。 |
| `commerce.billing.address` | 請求先住所。 |
| `commerce.billing.address.street1` | プライマリの番地の情報、アパート番号、番地、および番地 |
| `commerce.billing.address.street2` | 番地レベル情報の追加フィールド。 |
| `commerce.billing.address.city` | 市区町村の名前。 |
| `commerce.billing.address.state` | 州の名前。 これは自由形式のフィールドです。 |
| `commerce.billing.address.postalCode` | 場所の郵便番号。 一部の国では、郵便番号が使用できません。 一部の国では、郵便番号の一部のみが含まれます。 |
| `commerce.billing.address.country` | 政府が管理する領土の名前。 次の値以外： `xdm:countryCode`の場合、任意の言語で国名を付けることができる自由形式のフィールドです。 |
| `personalEmail` | 個人の電子メールアドレス。 |
| `personalEmail.address` | 技術的な住所（例： ）。 `name@domain.com` RFC2822 以降の標準で一般的に定義されているとおりです。 |
| `productListItems` | 注文内の製品の配列。 |
| `productListItems.SKU` | 在庫管理単位。 商品の一意の ID。 |
| `productListItems.name` | 製品の表示名または人間が読み取り可能な名前。 |
| `productListItems.priceTotal` | 製品品目の合計価格。 |
| `productListItems.quantity` | 買い物かご内の製品単位数。 |
| `productListItems.discountAmount` | 適用される割引額を示します。 |
| `productListItems.currencyCode` | The [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 使用する通貨コード（例： ） `USD` または `EUR`. |
| `productListItems.selectedOptions` | 設定可能な製品に使用するフィールド。 |
| `productListItems.selectedOptions.attribute` | 設定可能な製品の属性（例： ）を識別します。 `size` または `color`. |
| `productListItems.selectedOptions.value` | 属性の値を次のように指定します。 `small` または `black`. |
| `productListItems.categories` | 製品のカテゴリに関する情報が含まれます。 |
| `productListItems.categories.id` | カテゴリの一意の ID。 |
| `productListItems.categories.name` | カテゴリの名前。 |
| `productListItems.categories.path` | カテゴリへのパス。 |
