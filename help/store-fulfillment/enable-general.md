---
title: 一般設定
description: 有効にする一般設定を構成します [!DNL Store Fulfillment] お客様のストアの グローバル拡張機能の設定、ログのシステム設定、データの同期、セキュリティを設定します。 Adobe Commerceとストアフルフィルメントサービスの統合を可能にするための主要なデータを提供します。
role: User, Admin
level: Intermediate
exl-id: 51dcfc95-3dd6-40d9-bd26-d8409a25f3c8
source-git-commit: 556cbf803a0f8569e8561d2b33b7a976065ae814
workflow-type: tm+mt
source-wordcount: '2413'
ht-degree: 0%

---

# 一般設定

Adobeコマース管理で、一般的な設定を構成して [!DNL Store Fulfillment] ストアのサービス、グローバル拡張機能の設定、および統合用の主要データの提供には、 [!UICONTROL Account Credentials].

統合は、ストアフルフィルメントサービスに接続する必要があります。 また、ストアフルフィルメントの一般設定を構成し、組織の機能と運用要件に基づいてストアフルフィルメントサービスを有効にし、カスタマイズします。

の一般的な設定 [!DNL Store Fulfillment] には、次の設定が含まれます。

- [ソリューションを有効にする](#enable-the-store-fulfillment-solution)
- [ストアフルフィルメントサービスに接続するためのアカウント資格情報を管理](#account-credentials)
- [ログの設定](#configure-logging)
- [オーダーとエラーの同期操作を管理するオプションを設定します](#order-synchronization)
- [店舗フルフィルメント配送オプションの有効化](#enable-store-fullment-shipping-options)
- [ストアフルフィルメントアプリのセキュリティと認証の設定を構成する](#store-fulfillment-app)
- [配信方法の可用性とメッセージング設定を設定](#in-store-delivery-methods)

## ストアフルフィルメントソリューションを有効にする

| **フィールド** | **説明** | **範囲** | **必須** |
|--------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Enabled]** | ソリューションを有効または無効にします。 有効な場合は、ストアフルフィルメント機能を設定および使用し、Adobe Commerceストアとストアフルフィルメントサービス間の接続を確立します。 無効にすると、すべてのストアフルフィルメント機能が無効になり、Adobe Commerceとストアフルフィルメントサービス間の通信が行われなくなります。 注文情報を処理または受け取ることができません。 | グローバル | はい |

この設定を完了するには、 **「店舗」>「構成」>「サービス」>「ウォルマート・コマース・テクノロジーによるフルフィルメントの保存」**.

## アカウント資格情報の追加

| **フィールド** | **説明** | **範囲** | **必須** |
|----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Environment]** | 選択可能 *サンドボックス* または *実稼動*:</br> サンドボックスは、テストの達成サービスと通信します。</br>実稼動環境は、実稼動環境と通信します。 用途 **のみ** 実稼動環境で</br>各環境に対して一連の資格情報が与えられ、同じインストールで両方のセットを管理できます。 </br></br>接続を検証する前に資格情報を保存します。 | グローバル | はい |
| **[!UICONTROL API Server URL]** | Walmart Store Fulfilment API エンドポイントへの URL。 これは、オンボーディングプロセス中に提供される完全修飾 URL である必要があります。 ストアフルフィルメントのお客様は、サンドボックス URL と実稼動 URL の両方を受け取ります。 完全な URL（末尾のスラッシュ「/」を含む）をコピー/貼り付けてください。 | グローバル | はい |
| **[!UICONTROL Token Auth Server URL]** | Walmart Store Fulfilment Authentication エンドポイントへの URL。 値は、オンボーディングプロセス中に提供される完全修飾 URL である必要があります。 サンドボックス URL と実稼動 URL の両方を受け取ります。 完全な URL（末尾のスラッシュを含む）をコピー/貼り付けてください `/`&quot;. | グローバル | はい |
| **[!UICONTROL Merchant Id]** | オンボーディングプロセス中に提供された一意のマーチャント（テナント） ID です。 ID は、注文をルーティングし、マーチャントストアが確実に注文を受け取るようにするために使用されます。 | グローバル | はい |
| **[!UICONTROL Consumer Id]** | 一意の統合 ID。 これは、オンボーディングプロセス中に提供されます。 変化はありません。 フルフィルメントサービスとのすべての通信を認証するために使用されます。 | グローバル | はい |
| **[!UICONTROL Consumer Secret]** | 一意の統合キー。 これは、オンボーディングプロセス中に提供されます。 フルフィルメントサービスとのすべての通信を認証するために使用されます。 | グローバル | はい |

アカウント資格情報を設定したら、 **[!UICONTROL Validate Credentials]** ：フルフィルメント web サービスへの接続を初めて確認および確立する場合。

## ログの設定

ログが有効になっている場合、ログファイルをすばやく展開できます。 実稼動環境での応答時間の問題を防ぐには、ログの有効化に注意し、必要に応じて短時間のみ有効にします。

API 関連の例外がファイアウォールまたはキャッシュを通じて取り込めるように、例外の処理を許可するように環境を設定するようにシステム管理者に依頼します。 また、このファイルのログローテーションを設定してサイズを最小限に抑えるよう、システム管理者に依頼することもできます。

| **フィールド** | **説明** | **範囲** | **必須** |
|----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **デバッグモード** | デバッグモードは、統合内のログに記録されるアクティビティを増やすために使用します。 無効にした場合、デバッグ情報はログに記録されません。 有効にすると、すべてのデバッグ情報がログに記録されます。</br> ログに記録されたすべてのデータは、次のファイルにあります。 `var/log/walmart-bopis.log` | グローバル | いいえ |

## 注文の同期の管理

注文の同期のエラー処理を管理する設定、注文の選択中にバーコードスキャンに使用するカタログ属性、ストアの達成キューの注文バッチサイズを構成する設定を構成します。

オーダーの同期操作の詳細は、管理者の「ストア履行キュー管理」ダッシュボード (
**[!UICONTROL System > Tools > Store Fulfillment Queue]**) をクリックします。

### 同期エラー管理

| **フィールド** | **説明** | **範囲** | **必須** |
|-----------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|--------------|
| **再試行重大なエラー** | 重大なエラーが発生した後のレコードの同期操作の再試行を指定します。</br></br>統合が達成サービスから肯定的な応答を受け取れない場合は、重大なエラーが発生します。 これは、サービスが停止している場合や、送信される注文データにエラーがある場合に発生する可能性があります。</br></br>再試行のしきい値に達すると、項目はキューに残りますが、再処理はおこなわれません。 エラーが発生したすべての項目を表示 **[!UICONTROL System > Tools > Store Fulfillment Queue]** 管理者での管理。 一貫して失敗する項目のトラブルシューティングをおこなうには、担当のアカウントマネージャーにお問い合わせください。 | グローバル | いいえ |
| **エラー通知メールの有効化** | エラー通知を有効にして、 [!UICONTROL Retry Critical Error Threshold] が注文に達しました。 通知には、エラーに関する利用可能な詳細が含まれます。 | グローバル | いいえ |
| **エラー通知メールの送信先** | エラー通知用の受信者の E メールアドレスのコンマ区切りリスト。 | グローバル | いいえ |
| **注文同期例外メールテンプレート** | 注文の同期エラーを受信者に通知するために使用する電子メールテンプレートを指定します。 デフォルトのテンプレートが提供されます。 カスタマイズはサポートされていません。 | ストア表示 | いいえ |

### 注文の同期

| **フィールド** | **説明** | **範囲** | **必須** |
|--------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Barcode Source]** | マーチャントロケーション内の対応する品目のスキャン可能コードを保存するカタログ属性。</br></br>既存のマーチャントロケーションが 1 つだけの場合は、UPC コードを使用し、e コマースチャネルでは SKU ごとに製品が識別される可能性があります。 これがシナリオの場合は、UPC コードを含むカタログ属性を選択します。</br></br>この設定により、マーチャントに送信された注文で、正しい識別子でリスト項目が保存され、店舗の関連付けがピッキングプロセス中に項目を正確にスキャンできるようになります。</br></br>不明な場合は、送付する属性を決定するために、配送およびピッキング部門の顧客に確認してください。 属性が現在データベースに含まれていない場合は、Adobe Commerce製品属性セットに適切な属性を追加する必要が生じる場合があります。 | Web サイト | はい |
| **[!UICONTROL Barcode Type]** | マーチャントロケーションの対応する品目のバーコードソースを保存する catalog 属性。</br></br>この設定により、マーチャントに送信された注文で、正しい識別子でリスト項目が保存され、店舗の関連付けがピッキングプロセス中に項目を正確にスキャンできるようになります。 オプションには、SKU、UPC、GTIN、UPCA、EAN13、UPCE0、DISA、UAB、CODABAR、Price Embedded UPC が含まれます。</br></br>不明な場合は、 [!UICONTROL Barcode Source] 属性。 店舗の関連付けは、選択リストから手動で項目を照合できます。 | Web サイト | はい |
| **[!UICONTROL Max Number of Items]** | 一度にストアフルフィルメントキューから送信する項目の最大数。</br></br>BOPIS オーダーは、一定の間隔で、バッチでフルフィルメントサービスに送信されます。 この設定を使用すると、バッチのサイズを制御できます。</br></br>デフォルト値は 100 項目です。 ご注文の量と処理能力に応じて、この値を上下に調整する必要が生じる場合があります。 | グローバル | いいえ |


## 店舗フルフィルメント配送オプションの有効化

Adobe Commerceストアの店頭受け取りと宅配オプションの可用性を決定する「店舗フルフィルメント配送オプション」を設定します。

### 出荷先ストア

| **フィールド** | **説明** | **範囲** | **必須** |
|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Enable Ship To Store]** | この出荷先設定では、既存の出荷先店舗機能が利用されます。 Inventory managementを使用する場合、または店舗間在庫移動を通じて在庫なしの商店ロケーションで注文を受け入れ、履行できる場合は、このオプションをに設定します。 `Yes`.</br></br>出荷先店舗オプションをサポートできない場合や提供したくない場合は、をに設定します。 `No`. 無効にした場合、商店の在庫がゼロのカタログ内の項目、またはその場所の下にある項目 [!DNL Out of Stock Threshold]、は、店舗でのピックアップオプションでは提供されません。</br></br>これは、マーチャントの場所ごとに調整できるグローバル設定です。 | グローバル | いいえ |

### 出荷元ストア

| **フィールド** | **説明** | **範囲** | **必須** |
|-----------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Enable Ship From Store]** | マーチャントストアでの「ホーム配信」オプションを有効または無効にします。 有効にすると、マーチャントストアの場所は、Web サイトに関連付けられた在庫内の他の割り当てられたソースと集計されて考慮されます。</br></br>標準のInventory managementサービスでは、 [!DNL Ship from Store] はオプション固有で、無効にできません。 Store Fulfilment ソリューションでは、これをオンまたはオフにするオプションがあります。</br></br>これはグローバル設定です。 また、マーチャントの場所や製品ごとにこの設定を調整することもできます。 | グローバル | いいえ |


## ストアフルフィルメントアプリの管理アカウントと権限の使用

Store Fulfilment App のユーザーアカウントとパスワードセキュリティおよび 2 要素認証の設定を構成します。

### アプリのセキュリティ

| **フィールド** | **説明** | **範囲** | **必須** |
|------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL User Session Lifetime]** | ストア関連ユーザーセッションが自動ログアウト前にアクティブなままになる時間（秒）。 有効な値の範囲は 60 ～ 31536000です。 | グローバル | いいえ |
| **[!UICONTROL Maximum Login Failures to Lockout Account]** | ストアの関連付けがアカウントからロックアウトされるまでに、ログイン試行に失敗した回数を指定します。</br></br>アカウントのロックアウトを無効にするには、値を 0 に設定します。 | グローバル | いいえ |
| **[!UICONTROL Lockout Time (minutes)]** | ログイン失敗後にアカウントをロックする時間（分）。 | グローバル | いいえ |
| **[!UICONTROL Force Password Change]** | ユーザーのパスワードの変更が必要かどうかを決定します。</br></br>`Yes`:アカウントの設定後にユーザーにパスワードの変更を求める。</br>`No`:アカウントの設定後にユーザーがパスワードを変更することをお勧めします。 | グローバル | いいえ |
| **パスワードの有効期間** | パスワードが必要な変更までに、パスワードが有効である日数を示します。 このオプションを無効にするには、空のままにします。 | グローバル | いいえ |

### 二段階認証

| **フィールド** | **説明** | **範囲** | **必須** |
|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **アプリユーザー 2FA** | ストア関連の二段階認証を有効または無効にします。 有効にすると、ストアの関連付けは、認証プロバイダーによって生成された 1 回限りのパスワードの入力を求められます。 | グローバル | いいえ |
| **APP 2FA ポリシー** | 2 要素認証の実施ポリシーを設定します。</br></br>**[!UICONTROL Optional]**:プロバイダーが設定されていない場合、ストアアソシエートは、2 要素認証をバイパスできます。</br></br>**[!UICONTROL Mandatory]**:ストア関連付けは、2 要素認証を完了するために必要です。 | グローバル | いいえ |
| **2FA プロバイダ** | ストア関連付けを提供する 1 つ以上の認証プロバイダーサービスを選択します。 2 要素認証と認証を設定するには、ストア担当者がモバイルデバイスにインストールされている利用可能なプロバイダーの 1 つから認証アプリをインストールする必要があります。 | グローバル | いいえ |

### 配信方法

ネイティブのAdobe Commerceを拡張することで、ストアの達成が機能 [!DNL In-Store Delivery] 機能
拡張機能をインストールすると、追加の管理者設定オプションをストア内配信方法で使用できるようになります。 管理者から、以下の追加オプションを設定します。 **[!UICONTROL Stores > Configuration > Sales > Delivery Methods > In-Store Pickup]**.

「店舗達成」設定では、店舗受注に対して次の配信方法を設定できます。

- **店内受け取り** — チェックアウトプロセス中の店舗配信用オファーオプション BOPIS 注文で最も一般的な配信シナリオです。

- **カーブサイドピックアップ** — 店舗に駐車し、店舗の関係者から受け渡しを受け付ける顧客向けのオファーオプション。

#### 配信メソッド設定

<!---
In-store pickup, says its global setting, but scope is Website.  How do you configure the in-store pickup options at the retail level?
--->

| **フィールド** | **説明** | **範囲** | **必須** |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Enable In-Store Pickup]** | 店舗受取を選択した顧客のチェックアウト時に使用できる店舗受取オプションを有効または無効にします。 店舗でのピックアップが無効な場合、このオプションは表示されません。</br></br>このグローバル設定は、すべての小売店の場所に適用されます。 有効にした場合、小売ストアの場所で選択的に無効にできます。 | Web サイト | いいえ |
| **カーブサイドピックアップの有効化** | 店舗受取を選択した顧客のチェックアウトプロセス中に、カーブサイド受取オプションを有効または無効にします。</br></br>このグローバル設定は、すべての小売店の場所に適用されます。 有効にした場合、小売ストアの場所で選択的に無効にできます。 | Web サイト | いいえ |

選択した小売店舗の場所での配信方法のカスタマイズについて詳しくは、 **小売ストアの設定**.

#### 配信方法のタイトル設定

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
<td>製品、買い物かご、チェックアウト領域の「ホーム配信」オプションに対して表示するタイトルを指定します。 宅配は、Adobe Commerceの標準的な配送機能を指し、倉庫から配送業者が、お客様が指定した配送先住所に直接アクセスします。</br></br>このラベルは、選択した配送業者または使用可能な配送方法のラベルには影響しません。</td>
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
<td>顧客に配信オプションが提示され、店頭でのピックアップが可能になると、このラベルが表示されます。</br></br>このラベルは、製品、買い物かご、チェックアウト領域に表示されるようにカスタマイズできます。</td>
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
<td>小売店で注文を受け取る準備が整うと、顧客に E メールで通知が送信されます。 顧客が [!DNL In-Store Pickup] チェックアウト時に、ここでピックアップの手順をカスタマイズできます。</br></br>これは、すべての小売店舗の場所に適用されるグローバル設定です。 また、小売ストアの場所レベルで手順をカスタマイズすることもできます。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>カーブ側ピックアップの手順</strong></td>
<td>顧客電子メール通知に含める、カスタマイズされた受注受注指示を指定します。</br></br>これは、すべての小売店舗の場所に適用されるグローバル設定です。 また、小売ストアの場所レベルで手順をカスタマイズすることもできます。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>推定ピックアップリードタイム</strong></td>
<td>注文を受信し、満たされ、取得する準備が整うまでに必要な分数。 この情報は、顧客が「受け取り商品の小売店舗の場所」の配信オプションを選択する際に表示されます。</br></br>これはグローバル設定で、すべての小売店舗の場所に適用されます。 リードタイムは、小売店舗の場所レベルでカスタマイズすることもできます。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>推定ピックアップ時間ラベル</strong></td>
<td>注文が顧客の受け取りに使用可能になるまでの推定時間を表示します。 この情報は、顧客が「受け取り商品」配信オプションで小売店舗の場所を選択する際に表示されます。</br></br>このラベルをカスタマイズする場合は、コードを使用できます <code>%1</code> を <strong>推定ピックアップリードタイム</strong>例：</br></br><code>Ready for Pickup in %1 minutes.</code></br></br>これは、すべての小売店舗の場所に適用されるグローバル設定です。 リードタイムは、小売店舗の場所レベルでカスタマイズすることもできます。</br></br><code>Ready for Pickup in %1 minutes.</code></br></br></td>
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

#### 在庫品目設定

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
<td>顧客が小売店舗ロケーターを使用している場合、現在の品目の在庫状況が各場所に表示されます。</br></br>ここで「在庫中」ステータスラベルをカスタマイズできます。</td>
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
<td>顧客が小売店舗ロケーターを使用している場合、現在の品目の在庫可用性は各場所で表示されます。</br></br>ここで、「一部在庫あり」ステータスラベルをカスタマイズできます。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
</tbody></table>
