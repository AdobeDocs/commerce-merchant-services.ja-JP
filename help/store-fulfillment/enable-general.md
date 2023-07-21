---
title: 一般設定
description: 有効にする一般設定を構成します [!DNL Store Fulfillment] お客様のストアの グローバル拡張機能の設定、ログのシステム設定、データの同期、セキュリティを設定します。 Adobe Commerceとストアフルフィルメントサービスの統合を可能にするための主要なデータを提供します。
role: Admin
level: Intermediate
exl-id: 51dcfc95-3dd6-40d9-bd26-d8409a25f3c8
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '2419'
ht-degree: 0%

---

# ストアサービスとセールスの設定

有効にする [!DNL Store Fulfillment] からの拡張 [!DNL Commerce] 管理者は、拡張機能の設定、Store Assist アプリユーザーのセキュリティ設定、配信方法のオプションを設定します。

>[!IMPORTANT]
>
>ストアフルフィルメントサービスの設定は、Adobe Commerceインスタンスと [!DNL Store Fulfillment] アプリを使用します。 詳しくは、 [ストアの達成を接続](connect-set-up-service.md).

## ストアフルフィルメントサービス設定の管理

次からストアフルフィルメントサービスの設定を管理 [!DNL Commerce Admin Store Configuration] メニュー

- 拡張機能を有効にし、グローバル設定を指定し、Store Assist アプリのユーザー接続とアカウントのセキュリティオプションを指定するには、次を選択します。 **[!UICONTROL Stores > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies]**.

  ![ストアのフルフィルメント用の管理ストアサービス構成](assets/store-services-admin-sf-config.png)

- 選択による配信方法の設定 **[!UICONTROL Store > Configuration > Sales > Delivery Methods > In-Store Pickup]**.

  ![ストアのフルフィルメントの管理ストアの販売構成](assets/store-sales-admin-sf-deliver-config.png)

## 基本設定

<table>
<thead>
<tr>
<td><strong>フィールド</strong></td>
<td><strong>説明</strong></td>
<td><strong>範囲</strong></td>
<td><strong>必須</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Price]</strong></td>
<td>店舗での受け取りに対して顧客に請求する価格。 デフォルトは 0 です。</td>
<td>Web サイト</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>[!UICONTROL Search Radius]</strong></td>
<td>買い物客がストアフロントチェックアウトでストアのピックアップの場所を検索する際に使用する半径（キロメートル単位）。 検索結果は、指定した検索半径内にあるストアのみを返します。</td>
<td>Web サイト</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>[!UICONTROL Displayed error message]</strong></td>
<td>顧客が店舗でのピックアップに使用できない品目に対して店舗でのピックアップを選択したときに表示されるメッセージ。 必要に応じて、デフォルトのテキストをカスタマイズできます。
</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>この [!UICONTROL Search Radius] 設定は、 [ストアの場所とマッピングの設定](store-location-map-provider-setup.md) Adobe Commerce

## ストアフルフィルメントソリューションを有効にする

を有効にします。 [!DNL Store Fulfillment] Adobe Commerceストアフロントのショッピングエクスペリエンスやチェックアウトエクスペリエンスに、店舗内およびカーブサイドのピックアップ機能を追加するソリューションです。

<table>
<thead>
<tr>
<td><strong>フィールド</strong></td>
<td><strong>説明</strong></td>
<td><strong>範囲</strong></td>
<td><strong>必須</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL Enabled]</strong></td>
<td>ソリューションを有効または無効にします。 有効な場合は、ストアフルフィルメント機能を設定および使用し、Adobe Commerceストアと [!DNL Store Fulfillment] サービス。 無効にすると、すべてのストアフルフィルメント機能が無効になり、Adobe Commerceとストアフルフィルメントサービス間の通信が行われなくなります。 注文情報を処理または受け取ることができません。</td>
<td>Web サイト</td>
<td>はい</td>
</tr>
</tbody>
</table>

## アカウント資格情報を追加

<table>
<tr>
<td><strong>フィールド</strong></td>
<td><strong>説明</strong></td>
<td><strong>範囲</strong></td>
<td><strong>必須</strong></td>
</tr>
<tr>
<td><strong>[!UICONTROL Environment]</strong></td>
<td>次のいずれかを選択 <i>[!UICONTROL Sandbox]</i> または <i>[!UICONTROL Production]</i><br></br>選択 [!UICONTROL Sandbox] テスト環境でフルフィルメントサービスとの通信を可能にします。<br></br>選択 [!UICONTROL Production] は、実稼働環境でフルフィルメントサービスとの通信を可能にします。<br></br>各環境に対して一連の資格情報が提供され、同じインストールで両方のセットを管理できます。 <br></br>接続を検証する前に、資格情報を保存します。</td>
<td>グローバル</td>
<td>はい</td>
</tr>
<tr>
<td><strong>[!UICONTROL API Server URL]</strong></td>
<td>Walmart Store Fulfilment API エンドポイントへの URL。 値は、オンボーディングプロセス中に提供される完全修飾 URL である必要があります。 ストアフルフィルメントのお客様は、サンドボックス URL と実稼動 URL の両方を受け取ります。 値を追加する場合は、完全な URL（末尾のスラッシュ「/」を含む）をコピーして貼り付けます。</td>
<td>グローバル</td>
<td>はい</td>
</tr>
<tr>
<td><strong>[!UICONTROL Token Auth Server URL]</strong></td>
<td>Walmart Store Fulfilment Authentication エンドポイントへの URL。 値は、オンボーディングプロセス中に提供される完全修飾 URL である必要があります。 サンドボックス URL と実稼動 URL の両方を受け取ります。 値を追加する場合は、完全な URL（末尾のスラッシュ「/」を含む）をコピーして貼り付けます。</td>
<td>グローバル</td>
<td>はい</td>
</tr>
<tr>
<td><strong>[!UICONTROL Merchant Id]</strong></td>
<td>オンボーディングプロセス中に提供された一意のマーチャント（テナント） ID。 この ID は、マーチャントストアが確実に注文を受け取るようにルーティングするために使用されます。</td>
<td>グローバル</td>
<td>はい</td>
</tr>
<tr>
<td><strong>[!UICONTROL Consumer Id]</strong></td>
<td>オンボーディングプロセス中に提供された一意の統合 ID。 この ID は、Adobe Commerceとストアフルフィルメントサービス間のすべての通信を認証するために使用されます</td>
<td>グローバル</td>
<td>はい</td>
</tr>
<tr>
<td><strong>[!UICONTROL Consumer Secret]</strong></td>
<td>オンボーディングプロセス中に提供される一意の統合キー。 このキーは、Adobe Commerceとストアフルフィルメントサービス間のすべての通信を認証するために使用されます。</td>
<td>グローバル</td>
<td>はい</td>
</tr>
</table>

設定後、 [!UICONTROL Account Credentials]を選択します。 <strong>[!UICONTROL Validate Credentials]</strong> を使用して、初めてストアフルフィルメントサービスへの接続を確認し、確立します。

## ログの設定

ストアフルフィルメントサービスのログはログファイルで使用できます `var/log/walmart-bopis.log`.

API 関連の例外がファイアウォールまたはキャッシュを通じて取り込めるように、例外の処理を許可するように環境を設定するようにシステム管理者に依頼します。

アプリケーション・ログ・ファイルは迅速に拡張できるため、必要に応じて短時間のみログを有効にします。例えば、 [!DNL Commerce] 注文。 この設定により、大きなログファイルが原因で発生する、実稼動環境での応答時間の問題を防ぐことができます。

>[!TIP]
>
>Adobe Commerceのオンプレミスでのインストールの場合は、システム管理者に、 `var/log/walmart-bopis.log` ファイルのサイズを最小限に抑えます。 Adobe Commerceのオンプレミスでのインストールについては、 [対数の回転](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html#server-settings) 内 _Adobe Commerce Installation Guide_. Adobe Commerce on cloud infrastructure プロジェクトについては、 [ログの表示と管理](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html).

<table>
<thead>
<tr>
<td><strong>フィールド</strong></td>
<td><strong>説明</strong></td>
<td><strong>範囲</strong></td>
<td><strong>必須</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Debug Mode]</strong></td>
<td>デバッグモードは、統合内のログに記録されるアクティビティを増やすために使用します。 無効にした場合、デバッグ情報はログに記録されません。 有効にすると、すべてのデバッグ情報がログに記録されます <br></br>ログに記録されたすべてのデータは、次のファイルにあります。 <pre>var/log/walmart-bopis.log</pre>
<td>グローバル</td>
<td>いいえ</td>
</tr>
</tbody>
</table>

## 注文の同期の管理

注文の同期のエラー処理を管理する設定、注文の選択中にバーコードスキャンに使用するカタログ属性、ストアの達成キューの注文バッチサイズを構成する設定を構成します。

オーダーの同期操作の詳細は、管理者の「ストア履行キュー管理」ダッシュボード (
<strong>[!UICONTROL System > Tools > Store Fulfillment Queue]</strong>) をクリックします。

### 同期エラー管理

<table>
<tr>
<td><strong>フィールド</strong></td>
<td><strong>説明</strong></td>
<td><strong>範囲</strong></td>
<td><strong>必須</strong></td>
</tr>
<tr>
<td><strong>[!UICONTROL Retry Critical Error]</strong></td>
<td>重大なエラーが発生した後のレコードの同期操作の再試行を指定します。<br></br>統合が達成サービスから肯定的な応答を受け取れない場合は、重大なエラーが発生します。 これらの問題は、サービスが停止した場合、または送信される注文データにエラーがある場合に発生します。<br></br>再試行のしきい値に達すると、項目はキューに残りますが、再処理はおこなわれません。 エラーが発生したすべての項目を表示 <strong>[!UICONTROL System > Tools > Store Fulfillment Queue]</strong> 管理者での管理。 一貫して失敗する項目のトラブルシューティングをおこなうには、担当のアカウントマネージャーにお問い合わせください。</td>
<td>グローバル</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Error Notification Email]</strong></td>
<td>エラー通知を有効にして、 [!UICONTROL Retry Critical Error Threshold] が注文に達しました。 通知には、エラーに関する利用可能な詳細が含まれます。</td>
<td>グローバル</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>[!UICONTROL Send Error Notification Email To]</strong></td>
<td>エラー通知用の受信者の E メールアドレスのコンマ区切りリスト。</td>
<td>グローバル</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>[!UICONTROL Order Sync Exception Email Template]</strong></td>
<td>注文の同期エラーを受信者に通知するために使用する電子メールテンプレートを指定します。 デフォルトのテンプレートが提供されます。 カスタマイズはサポートされていません。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
</table>

### 注文の同期

<table>
<thead>
<tr>
<td><strong>フィールド</strong></td>
<td><strong>説明</strong></td>
<td><strong>範囲</strong></td>
<td><strong>必須</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Barcode Source]</strong></td>
<td>マーチャントロケーション内の対応する品目のスキャン可能コードを保存するカタログ属性。<br></br>既存のマーチャントロケーションが 1 つだけの場合は、UPC コードを使用し、e コマースチャネルでは SKU ごとに製品が識別される可能性があります。 このシナリオでは、UPC コードを含むカタログ属性を選択します。<br></br>この設定により、店舗リスト項目に送信される注文が正しい識別子で保証され、店舗がピッキングプロセス中に品目を正確にスキャンできるようになります。<br></br>不明な場合は、送付する属性を決定するために、配送およびピッキング部門の顧客に確認してください。 属性が現在データベースに含まれていない場合は、属性をAdobe Commerce製品属性セットに追加できます。</td>
<td>Web サイト</td>
<td>はい</td>
</tr>
<tr>
<td><strong>[!UICONTROL Barcode Type]</strong></td>
<td>マーチャントロケーションの対応する品目のバーコードソースを保存する catalog 属性。<br></br>この設定により、店舗リスト項目に送信される注文が正しい識別子で保証され、店舗はピッキングプロセス中に品目を正確にスキャンできます。 オプションには、SKU、UPC、GTIN、UPCA、EAN13、UPCE0、DISA、UAB、CODABAR、Price Embedded UPC が含まれます。<br></br>不明な場合は、 [!UICONTROL Barcode Source] 属性。 店舗の関連付けは、選択リストから手動で項目を照合できます。</td>
<td>Web サイト</td>
<td>はい</td>
</tr>
<tr>
<td><strong>[!UICONTROL Max Number of Items]</strong></td>
<td>一度にストアフルフィルメントキューから送信する項目の最大数。<br></br>BOPIS オーダーは、一定の間隔で、バッチでフルフィルメントサービスに送信されます。 この設定を使用すると、バッチのサイズを制御できます。<br></br>デフォルト値は 100 項目です。 注文量と処理能力に応じて、最大値を上下に調整できます。</td>
<td>グローバル</td>
<td>いいえ</td>
</tr>
</tbody>
</table>

## 店舗フルフィルメント配送オプションの有効化

Adobe Commerceストアの店頭受け取りと宅配オプションの可用性を決定する「店舗フルフィルメント配送オプション」を設定します。

### 出荷先ストア

<table>
<thead>
<tr>
<td><strong>フィールド</strong></td>
<td><strong>説明</strong></td>
<td><strong>範囲</strong></td>
<td><strong>必須</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Enable Ship To Store]</strong></td>
<td>出荷先店舗の設定は、既存の出荷先店舗機能に基づいています。 Inventory managementを使用する場合、または店舗間在庫移動を通じて在庫なしの商店ロケーションで注文を受け入れ、履行できる場合は、このオプションを「はい」に設定します。<br></br>出荷先店舗オプションをサポートできない場合や提供したくない場合は、「いいえ」に設定します。 無効にした場合、商店の在庫がゼロのカタログ内の項目、または [!DNL Out of Stock Threshold] その場所では、は店舗でのピックアップオプションでは提供されません。<br></br>この設定の値は、商人の場所ごとに調整できます。</td>
<td>グローバル</td>
<td>いいえ</td>
</tr>
</tbody>
</table>

### 出荷元ストア

<table>
<thead>
<tr>
<td><strong>フィールド</strong></td>
<td><strong>説明</strong></td>
<td><strong>範囲</strong></td>
<td><strong>必須</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong></td>
<td>マーチャントストアでの「ホーム配信」オプションを有効または無効にします。 有効にすると、マーチャントストアの場所は、Web サイトに関連付けられた在庫内の他の割り当てられたソースと集計されて考慮されます。<br></br>標準のInventory managementサービスでは、 [!DNL Ship from Store] はオプション固有で、無効にできません。 Store Fulfilment ソリューションでは、オン/オフを切り替えることができます。<br></br>この設定は、商人の場所と製品ごとに調整できます。</td>
<td>グローバル</td>
<td>いいえ</td>
</tr>
</tbody>
</table>


## ストアフルフィルメントアプリの管理アカウントと権限の使用

Store Fulfilment App のユーザーアカウントとパスワードセキュリティおよび 2 要素認証の設定を構成します。

### アプリのセキュリティ

<table>
<thead>
<tr>
<td><strong>フィールド</strong></td>
<td><strong>説明</strong></td>
<td><strong>範囲</strong></td>
<td><strong>必須</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL User Session Lifetime]</strong></td>
<td>ストア関連ユーザーセッションが自動ログアウト前にアクティブなままになる時間（秒）。 有効な値の範囲は 60 ～ 31536000です。</td>
<td>グローバル</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>[!UICONTROL Maximum Login Failures to Lockout Account]</strong></td>
<td>ストアの関連付けがアカウントからロックアウトされるまでに、ログイン試行に失敗した回数を指定します。<br></br>アカウントのロックアウトを無効にするには、値を 0 に設定します。</td>
<td>グローバル</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>[!UICONTROL Lockout Time (minutes)]</strong></td>
<td>ログイン失敗後にアカウントをロックする時間（分）。</td>
<td>グローバル</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>[!UICONTROL Force Password Change]</strong></td>
<td><em>[!UICONTROL Yes]</em>:アカウントの設定後にユーザーにパスワードの変更を求める。<br></br><em>[!UICONTROL No]</em>:アカウントの設定後にユーザーがパスワードを変更することをお勧めします。</td>
<td>グローバル</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>[!UICONTROL Password Lifetime]</strong></td>
<td>パスワードが必要な変更までに、パスワードが有効である日数を示します。 このオプションを無効にするには、空のままにします。</td>
<td>グローバル</td>
<td>いいえ</td>
</tr>
</tbody>
</table>

## 配信方法

ネイティブのAdobe Commerceを拡張することで、ストアの達成が機能 [!DNL In-Store Delivery] 機能 拡張機能をインストールした後、管理者に追加された次の拡張設定を使用して、ストア内配信方法を設定できます。

- **店内受け取り** — チェックアウトプロセス中の店舗配信用オファーオプションこれらの設定は、BOPIS 注文で最も一般的な配信シナリオを設定します。

- **[!UICONTROL Curbside pick up]** — 店舗に駐車し、店舗の関係者から受け渡しを受け付ける顧客向けのオファーオプション。

管理者から、以下の設定を選択してください。 <strong>[!UICONTROL Stores > Configuration > Sales > Delivery Methods > In-Store Pickup]</strong>.

>[!NOTE]
>
>ストア内配信オプションの設定について詳しくは、 [ストア内配信](https://docs.magento.com/user-guide/shipping/shipping-in-store-delivery.html) 内 _Adobe Commerce User Guide_.


### 配信メソッド設定

店舗での配信方法を使用すると、顧客は、チェックアウト時にピックアップ場所として使用するソースを選択できます。

<table>
<thead>
<tr>
<td><strong>フィールド</strong></td>
<td><strong>説明</strong></td>
<td><strong>範囲</strong></td>
<td><strong>必須</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL Enable In-Store Pickup]</strong></td>
<td>店舗ピックアップを選択した顧客のチェックアウト時に使用できる店舗ピックアップオプションを有効または無効にします。 店舗でのピックアップが無効な場合、このオプションは表示されません。<br></br>このグローバル設定は、すべての小売店の場所に適用されます。 有効にした場合、小売ストアの場所で選択的に無効にできます。</td>
<td>Web サイト</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Curbside Pickup]</strong></td>
<td>店舗受取を選択した顧客のチェックアウトプロセス中に、カーブサイド受取オプションを有効または無効にします。<br></br>このグローバル設定は、すべての小売店の場所に適用されます。 有効にした場合、小売ストアの場所で選択的に無効にできます。</td>
<td>Web サイト</td>
<td>いいえ</td>
</tr>
</tbody>
</table>

### 配信方法のタイトル設定

<table>
<thead>
<tr>
<th><strong>フィールド</strong></th>
<th><strong>説明</strong></th>
<th><strong>範囲</strong></th>
<th><strong>必須</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>ホーム配信のタイトル</strong></td>
<td>製品、買い物かご、チェックアウト領域の「ホーム配信」オプションに対して表示するタイトルを指定します。 宅配は、Adobe Commerceの標準的な配送能力を指します。倉庫から、運送業者によって、または顧客が指定した配送先住所に直接送付されます。 </br></br>このラベルは、選択した配送業者の発送方法ラベルには影響しません。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>宅配の説明</strong></td>
<td>顧客にホーム配信のタイトルが表示されるたびに表示される説明（オプション）。 ほとんどの場合、説明は、配信プロミスを伝えるための静的なメッセージです。 次に例を示します。</br><code>Same-day shipping on orders by 4</code></br></br><code>Ships within 2 business days</code></td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>受け取りのタイトルを保存</strong></td>
<td>顧客に配信オプションが提示され、店頭でのピックアップが可能になると、このラベルが表示されます。 </br></br>このラベルは、製品、買い物かご、チェックアウト領域に表示されるようにカスタマイズできます。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<td><strong>店舗ピックアップの説明</strong></td>
<td>ストアピックアップのタイトルが表示される場所に、オプションで説明を含めることができます。 この静的メッセージは、ストアの受け取り操作に関連する顧客とのコミュニケーションを改善するのに役立ちます。 次に例を示します。</br></br><code>Get it today for free!</code></br></br><code>Ready for pickup in an hour!</code></td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>店内ピックアップのタイトル</strong></td>
<td>「店頭での集荷」が有効な場合、このタイトルが「集荷の保存」配信オプションとして顧客に表示されます。 ラベルをカスタマイズできます。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<tr>
<td><strong>カーブサイドピックアップのタイトル</strong></td>
<td>カーブサイドピックアップが有効な場合、このオプションは「ピックアップを保存」配信オプションのタイプとして顧客に表示されます。 ここでラベルをカスタマイズできます。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>店舗での受け取り手順</strong></td>
<td>小売店で注文を受け取る準備が整うと、顧客に E メールで通知が送信されます。 顧客が [!DNL In-Store Pickup] チェックアウト時に、ここでピックアップの手順をカスタマイズできます。 </br></br>これらの手順はグローバルに設定され、すべての小売ストアの場所に適用されます。 また、小売ストアの場所レベルで手順をカスタマイズすることもできます。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>カーブ側ピックアップの手順</strong></td>
<td>カスタマーメール通知に含める、カスタマイズされた受注情報を指定します。受注情報は、受注を制限するために送信されます。 </br></br>これらの手順はグローバルに設定され、すべての小売ストアの場所に適用されます。 また、小売ストアの場所レベルで手順をカスタマイズすることもできます。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>推定ピックアップリードタイム</strong></td>
<td>注文を受信し、満たされ、取得する準備が整うまでに必要な分数。 この情報は、顧客が「受け取り商品の小売店舗の場所」の配信オプションを選択する際に表示されます。 この設定は、すべての小売店舗の場所に適用されます。 リードタイムは、小売店舗の場所レベルでカスタマイズすることもできます。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>推定ピックアップ時間ラベル</strong></td>
<td>注文が顧客の受け取りに使用可能になるまでの推定時間を表示します。 この情報は、顧客が [!DNL In-Store Pickup] 配信オプション。 </br></br>このラベルをカスタマイズする場合は、コードを使用できます <code>%1</code> を <strong>推定ピックアップリードタイム</strong>. 例：</br></br><code>Ready for Pickup in %1 minutes.</code></br></br>この設定は、すべての小売店舗の場所に適用されます。 リードタイムは、小売店舗の場所レベルでカスタマイズすることもできます。</td>
<td>ストア表示</td>
<td>いいえ</td>
<tr>
<td><strong>ピックアップ時間免責事項</strong></td>
<td>製品ページに表示される、営業時間、休日、予期しない閉鎖などを示すツールチップのコンテンツ</td>
<td>ストア表示
</td>
<td>いいえ
</td>
</tr>
</tbody></table>

### 在庫品目設定

<table>
<thead>
<tr>
<th><strong>フィールド</strong></th>
<th><strong>説明</strong></th>
<th><strong>範囲</strong></th>
<th><strong>必須</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>在庫</strong></td>
<td>顧客が小売店舗ロケーターを使用している場合、現在の品目の在庫状況が各場所に表示されます。 </br></br>次の項目をカスタマイズできます： <em>[!UICONTROL in-stock]</em> ステータスラベルをここに入力します。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>在庫切れ</strong></td>
<td>顧客が小売店舗ロケーターを使用している場合、現在の品目の在庫状況が各場所に表示されます。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>一部在庫</strong></td>
<td>顧客が小売店舗ロケーターを使用している場合、現在の品目の在庫可用性は各場所で表示されます。 </br></br>次の項目をカスタマイズできます： <em>[!UICONTROL partially in-stock]</em> ステータスラベルをここに入力します。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
</tbody></table>

