---
title: 行動イベント
description: 各行動イベントがキャプチャするデータを説明します。
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: a433d970e83792a9f53b2a09afd84c335d980024
workflow-type: tm+mt
source-wordcount: '4496'
ht-degree: 0%

---

# [!DNL Data Connection] 行動イベント

次に、 [!DNL Data Connection] 拡張子。 これらのイベントで収集されたデータは、Adobe Experience Platformに送信されます。 また、 [カスタムイベント](custom-events.md) 標準で提供されていない追加データを収集する場合。

以下のイベントで収集されるデータに加えて、 [その他のデータ](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) Adobe Experience Platform Web SDK によって提供されます。

行動イベントは、サイトを閲覧する買い物客から匿名化された行動データを収集します。 これらのイベントで収集されたデータを使用して、特定の買い物客セットをターゲットにしたプロモーションやキャンペーンを作成できます。

>[!NOTE]
>
>すべての行動イベントには、 [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) フィールドに含まれます。これには、買い物客の電子メールアドレス（利用可能な場合）と ECID が含まれます。

## ストアフロントイベント

ストアフロントイベントは、サイトでの買い物客のインタラクションのデータをキャプチャし、次のようなイベントを含めます。 [`addToCart`](#addtocart), [`pageView`](#pageview), [`createAccount`](#createaccount), [`editAccount`](#editaccount), [`startCheckout`](#startcheckout), [`completeCheckout`](#completecheckout), [`signIn`](#signin), [`signOut`](#signout)など。 Storefront イベントは、シンプルで設定可能な製品にのみ適用されます。

### addToCart

| 説明 | XDM イベント名 |
|---|---|
| 製品が買い物かごに追加されたとき、または買い物かご内の製品の数量が増加したときにトリガーされます。 | `commerce.productListAdds` |

#### addToCart から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `channel` | データのソースに関する情報が含まれます。 両方 `_id` および `_type` 次を含む [名前空間の値](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | チャネルの一意の識別子（例： ） `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | チャネルデータのソースを識別します（例： ）。 `"https://ns.adobe.com/xdm/channel-types/web"`. |
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
| `channel` | データのソースに関する情報が含まれます。 両方 `_id` および `_type` 次を含む [名前空間の値](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | チャネルの一意の識別子（例： ） `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | チャネルデータのソースを識別します（例： ）。 `"https://ns.adobe.com/xdm/channel-types/web"`. |
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
| `channel` | データのソースに関する情報が含まれます。 両方 `_id` および `_type` 次を含む [名前空間の値](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | チャネルの一意の識別子（例： ） `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | チャネルデータのソースを識別します（例： ）。 `"https://ns.adobe.com/xdm/channel-types/web"`. |
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
| `channel` | データのソースに関する情報が含まれます。 両方 `_id` および `_type` 次を含む [名前空間の値](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | チャネルの一意の識別子（例： ） `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | チャネルデータのソースを識別します（例： ）。 `"https://ns.adobe.com/xdm/channel-types/web"`. |
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
| `channel` | データのソースに関する情報が含まれます。 両方 `_id` および `_type` 次を含む [名前空間の値](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | チャネルの一意の識別子（例： ） `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | チャネルデータのソースを識別します（例： ）。 `"https://ns.adobe.com/xdm/channel-types/web"`. |
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
| `channel` | データのソースに関する情報が含まれます。 両方 `_id` および `_type` 次を含む [名前空間の値](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | チャネルの一意の識別子（例： ） `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | チャネルデータのソースを識別します（例： ）。 `"https://ns.adobe.com/xdm/channel-types/web"`. |
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
| `channel` | データのソースに関する情報が含まれます。 両方 `_id` および `_type` 次を含む [名前空間の値](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | チャネルの一意の識別子（例： ） `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | チャネルデータのソースを識別します（例： ）。 `"https://ns.adobe.com/xdm/channel-types/web"`. |
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
| 買い物客が注文したときにトリガーされます。 | `commerce.purchases` |

#### completeCheckout から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `channel` | データのソースに関する情報が含まれます。 両方 `_id` および `_type` 次を含む [名前空間の値](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | チャネルの一意の識別子（例： ） `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | チャネルデータのソースを識別します（例： ）。 `"https://ns.adobe.com/xdm/channel-types/web"`. |
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

## 顧客プロファイルイベント

ストアフロントからキャプチャされるプロファイルイベントには、次のようなアカウント情報が含まれます。 `signIn`, `signOut`, `createAccount`、および `editAccount`. このデータは、セグメントをより適切に定義したり、新規登録の割引オファーの送信や、アカウントの変更確認など、マーケティングキャンペーンを実行するために必要な顧客の主要な詳細情報を入力するのに役立ちます。 次からキャプチャされた類似のプロファイルイベントがあります： [サーバーサイド](events-backoffice.md#customer-profile-events).

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
| `channel` | データのソースに関する情報が含まれます。 両方 `_id` および `_type` 次を含む [名前空間の値](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | チャネルの一意の識別子（例： ） `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | チャネルデータのソースを識別します（例： ）。 `"https://ns.adobe.com/xdm/channel-types/web"`. |
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
| `channel` | データのソースに関する情報が含まれます。 両方 `_id` および `_type` 次を含む [名前空間の値](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | チャネルの一意の識別子（例： ） `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | チャネルデータのソースを識別します（例： ）。 `"https://ns.adobe.com/xdm/channel-types/web"`. |
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
| `channel` | データのソースに関する情報が含まれます。 両方 `_id` および `_type` 次を含む [名前空間の値](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | チャネルの一意の識別子（例： ） `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | チャネルデータのソースを識別します（例： ）。 `"https://ns.adobe.com/xdm/channel-types/web"`. |
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
| `channel` | データのソースに関する情報が含まれます。 両方 `_id` および `_type` 次を含む [名前空間の値](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | チャネルの一意の識別子（例： ） `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | チャネルデータのソースを識別します（例： ）。 `"https://ns.adobe.com/xdm/channel-types/web"`. |
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

検索イベントは、買い物客の意図に関連するデータを提供します。 買い物客の意図をインサイトすることで、買い物客が品目、クリックしたもの、最終的に購入または放棄をどのように検索しているかを知ることができます。 このデータの使用例は、トップ商品を検索しても商品を購入しない既存の買い物客をターゲットにしたい場合です。 次をインストールする必要があります： [[!DNL Live Search]](../live-search/install.md) 拡張機能を使用して、これらのイベントにアクセスできます。

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
| `channel` | データのソースに関する情報が含まれます。 両方 `_id` および `_type` 次を含む [名前空間の値](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | チャネルの一意の識別子（例： ） `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | チャネルデータのソースを識別します（例： ）。 `"https://ns.adobe.com/xdm/channel-types/web"`. |
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
| `channel` | データのソースに関する情報が含まれます。 両方 `_id` および `_type` 次を含む [名前空間の値](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | チャネルの一意の識別子（例： ） `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | チャネルデータのソースを識別します（例： ）。 `"https://ns.adobe.com/xdm/channel-types/web"`. |
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

![Adobe Commerce用 B2B](../assets/b2b.svg) B2B 商人の場合は、 [install](install.md#install-the-b2b-extension) の `experience-platform-connector-b2b` 拡張機能を使用して、これらのイベントにアクセスできます。

B2B イベントには、 [購買依頼リスト](https://experienceleague.adobe.com/docs/commerce-admin/b2b/requisition-lists/requisition-lists.html) 情報（購買依頼リストが作成、追加、削除された場合など）。 購買依頼リストに固有のイベントを追跡することで、顧客が頻繁に購入する製品を確認し、そのデータに基づいてキャンペーンを作成できます。

### createRequisitionList

| 説明 | XDM イベント名 |
|---|---|
| 買い物客が購入依頼リストを作成したときにトリガーされます。 | `commerce.requisitionListOpens` |

#### createReqisitionList から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `channel` | データのソースに関する情報が含まれます。 両方 `_id` および `_type` 次を含む [名前空間の値](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | チャネルの一意の識別子（例： ） `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | チャネルデータのソースを識別します（例： ）。 `"https://ns.adobe.com/xdm/channel-types/web"`. |
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
| `channel` | データのソースに関する情報が含まれます。 両方 `_id` および `_type` 次を含む [名前空間の値](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | チャネルの一意の識別子（例： ） `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | チャネルデータのソースを識別します（例： ）。 `"https://ns.adobe.com/xdm/channel-types/web"`. |
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
| `channel` | データのソースに関する情報が含まれます。 両方 `_id` および `_type` 次を含む [名前空間の値](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | チャネルの一意の識別子（例： ） `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | チャネルデータのソースを識別します（例： ）。 `"https://ns.adobe.com/xdm/channel-types/web"`. |
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

### deleteRequisitionList

| 説明 | XDM イベント名 |
|---|---|
| 買い物客が購入依頼リストを削除した場合にトリガーされます。 | `commerce.requisitionListDeletes` |

#### deleteRequisitionList から収集されたデータ

次の表に、このイベントで収集されるデータを示します。

| フィールド | 説明 |
|---|---|
| `channel` | データのソースに関する情報が含まれます。 両方 `_id` および `_type` 次を含む [名前空間の値](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | チャネルの一意の識別子（例： ） `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | チャネルデータのソースを識別します（例： ）。 `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `commerce.requisitionListDeletes` | 購買依頼リストが削除されたことを示します。 |
| `commerce.requisitionList` | 顧客が作成した購買依頼リストのプロパティ。 |
| `commerce.requisitionList.ID` | 購買依頼リストの一意の ID。 |
| `commerce.requisitionList.name` | 顧客が指定した購買依頼リストの名前。 |
| `commerce.requisitionList.description` | 顧客が指定した購買依頼リストの説明。 |
| `commerce.commerceScope` | イベントが発生した場所を示します（ストア表示、ストア、Web サイトなど）。 |
| `commerce.commerceScope.environmentID` | 環境 ID。 32 桁の英数字 ID で、ハイフンで区切られます。 |
| `commerce.commerceScope.storeCode` | 一意の店舗コード。 Web サイトごとに多くの店舗を持つことができます。 |
| `commerce.commerceScope.storeViewCode` | 一意の店舗ビューコード。 ストアごとに多数のストアビューを持つことができます。 |
| `commerce.commerceScope.websiteCode` | 一意の Web サイトコード。 1 つの環境に多数の Web サイトを持つことができます。 |
