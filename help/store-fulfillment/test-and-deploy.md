---
title: ストアのフルフィルメントのテストとデプロイ
description: テスト計画を作成して、店舗フルフィルメント機能を検証します。 テストでは、在庫同期 API、取り消された注文のエンドツーエンドのフルフィルメントワークフロー、ストアフルフィルメントアプリのユーザー管理、および顧客チェックインエクスペリエンスをカバーします。
role: User, Admin
level: Intermediate
feature: Shipping/Delivery, User Account, Roles/Permissions
exl-id: 77285a66-5161-407b-94cd-b3f412d7949d
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '2660'
ht-degree: 0%

---

# Adobe Commerceのストアフルフィルメントのテストとデプロイ

開発環境でオンボーディングプロセスを完了したら、プロセスを開始して、実稼動環境にストアフルフィルメントソリューションをテストし、デプロイできます。

**前提条件**

情報、店舗または注文をテストまたは同期する前に、次のタスクを完了していることを確認します。

- 完了： [一般設定](enable-general.md) （ストアフルフィルメントサービス用）

- [サンドボックスと実稼動環境のアカウント資格情報と接続の詳細を追加および検証します](connect-set-up-service.md#configure-store-fulfillment-account-credentials)

- を確認します。 [Adobe Commerce統合](connect-set-up-service.md#configure-store-fulfillment-account-credentials) ストアフルフィルメントソリューションは、利用可能で承認済みです。

## テストの準備

テストオーダーを作成したり統合テストを実行したりする前に、接続設定を完了しておく必要があります。 テストをおこなう前に、ストアデータが同期されていることを確認する必要があります。

1. ストア達成ソースを同期します。

   - に移動します。 **[!UICONTROL Stores > Sources]**.

   - 選択 **[!UICONTROL Synchronize Store Fulfillment Sources]**.

1. ストアグリッドから、ストアが `Synced` テスト注文を作成する前に。

## サンプルのテスト計画

小売業者は、導入の構成およびテストフェーズで、店舗フルフィルメントソリューションの基本機能を検証します。 このサンプルテスト計画は、テストの出発点となります。 要件に応じてシナリオを追加します。

>[!NOTE]
>
>ストアフルフィルメントソリューションの初期オンボーディングを完了した後、または既存のインストールを更新した後は、実稼動環境にデプロイする前に、必ず非実稼動環境でアプリケーションをテストしてください。

このテスト計画例では、次の機能領域を扱います。

| 機能領域 | 関数 | 役割 |
|-------------------------------------|------------------------------------------|----------------------------------|
| 在庫と注文の同期 | 在庫 API の同期 | Adobe Commerce Admin |
| エンドツーエンド | 注文取消ワークフロー | 顧客、管理者、ストア関連付け |
| 管理者 | フルフィルメントアプリの権限を保存 | 管理者 |
| Adobe Commerce Frontend | 製品タイプ | 顧客、管理者 |
| フロントエンドチェックアウト</br>チェックインフォーム | チェックインエクスペリエンス | 顧客、管理者 |
| ストアアシストアプリ | 注文</br>選択</br>ステージ</br>と引き渡し | ストアの関連付け |

### 在庫 API の同期

テスト計画のこのセクションでは、在庫と注文の同期をカバーして、ピックアップソースと在庫の更新がAdobe Commerceと Store Fulfilment ソリューションの間で正しく同期されていることを確認します。

**機能領域**：在庫と注文の同期</br>
**役割：** 管理者</br>
**テストタイプ：** すべての正数

<table>
<thead>
<tr>
<th>関数</th>
<th>シナリオをテスト</th>
<th>期待される結果</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>ピックアップ在庫ソースを追加</strong></td>
<td>新しいピックアップ在庫ソースを保存します。</td>
<td>リアルタイム同期では、ソースの詳細が 5 分以内にウォルマートGIFサービスに送信されます。</td>
</tr>
<tr>
<td><strong>既存のピックアップ在庫ソースを更新します</strong></td>
<td>既存のピックアップ在庫ソースに対する更新を保存します。</td>
<td>リアルタイム同期操作では、5 分以内に詳細がウォルマートGIFに送信されます</td>
</tr>
<tr>
<td><strong>ピックアップの在庫ソース</br><code>Is Synced</code> ステータス</strong></td>
<td>既存のピックアップ在庫ソースに対する更新を保存します。</td>
<td>操作が正常に完了した後、 <code>Is Synced</code> ソースを管理ページの更新元の列 <code>No</code> から <code>Yes</code>.</td>
</tr>
<tr>
<td><strong>変更された在庫予約プロセス</strong></td>
<td>製品の新しい注文を作成して送信します。</td>
<td>商品の販売可能量は、それに応じて減少します。</td>
</tr>
<tr>
<td><strong>新規注文プッシュ、API 同期 — 顧客注文</strong></td>
<td>顧客が店舗受取注文を送信します。</td>
<td><ul><li>管理順序ビューで、 <strong>Adobe Commerce管理者ユーザー</strong> 注文同期ステータスがに更新されたことを確認します。 <code>Sent</code></li><li>注文の詳細ログには、メッセージが含まれます <code>Order was sent to BOPIS solution for sync, it's not yet acknowledged yet.</code></li></ul></td>
</tr>
<tr>
<td><strong>新規注文プッシュ、API 同期 — 管理者が注文を送信</strong></td>
<td>Adobe Commerce <strong>管理者</strong> は、ピックアップオーダーを送信します。</td>
<td><ul><li>注文管理ビューで、注文の同期ステータスが <code>Sent</code>.</li><li>注文の詳細ログには、メッセージが含まれます <code>Order was sent to BOPIS solution for sync, it's not yet acknowledged yet.</code></li></ul></td>
</tr>
<tr>
<td><strong>新規受注プッシュ、例外キュー<strong></td>
<td>Adobe Commerce Admin で、Adobe Commerceを通じて満たすことができ、Fulfilment Service(FaaS) とのインタラクションを必要とせずに、仮想およびダウンロード可能な製品をいくつか特定します。</td>
<td>これらの製品は、FaaS との下流の競合を防ぐために、エクスポートで適切に削除またはフラグ付けされます。</td>
</tr>
</tbody>
</table>

### 注文キャンセルワークフロー

テスト計画のこのセクションには、Adobe Commerceを通じてキャンセルされた注文に対してエンドツーエンドのワークフローをテストするシナリオが含まれています。

**機能領域：** Adobe Commerce Admin</br>
**役割：** エンドツーエンド（管理者、ストア関連、顧客）</br>
**テスト結果のタイプ：** すべてのシナリオに対して肯定的

<table style="table-layout:fixed">
<tr>
<th>関数</th>
<th>シナリオ</th>
<th>期待される結果</th>
</tr>
<tr>
<td><strong>完全な注文のキャンセル</strong></td>
<td><ol>
<li>発注。</li>
<li>オーダーが同期されるまで待ちます。</li>
<li>請求書メールの請求書作成（承認および取得の場合）の受領書を検証します。</li>
<li>請求書ビューで発注されたすべての商品を含むクレジット・メモを作成します。</li>
</ol>
</td>
<td>
<ul>
<li>注文履歴を次で更新： <code>We refunded $X online. Transaction ID: transactionID</code> および <code>Received Cancel acknowledgment from the BOPIS solution.</code></li>
<li>注文ステータス： <code>Closed</code>. （今すぐ PAYMENT REVIEW を設定しました。）</li>
<li>Adobe Commerceで作成されたクレジットメモ。 （cron が動作するまで待ちます）。</li>
<li>すべての項目が選択された場合は、E メールの受け取り準備が整います <code>DISPLAY COMMENT HISTORY</code> 表示 <code>Order is ready for pickup</code> (<code>CUSTOMER NOTIFIED</code> フラグが <code>true</code>.)</li>
<li>すべての項目が選択されていない場合は、キャンセルメールと DISPLAY COMMENT HISTORY が表示されます <code>Order has been canceled - all items were not available</code></li>
<li><code>CUSTOMER NOTIFIED</code> フラグが <code>true</code>.)</li>
</ul>
</td>
</tr>
<tr><td><strong>一部注文の取消<strong></td>
<td>
<ol>
<li>少なくとも 2 つの製品を含む発注。</li>
<li>オーダーが同期されるまで待ちます。</li>
<li>請求書が作成され（承認および取り込みの場合）、および受け取った請求書の電子メールが受け取られたことを確認します。</li>
<li>取引決済が行われるまで 2 時間待ちます。</li>
<li>請求書ビューから受注した製品の一部のみを含むクレジット・メモを作成します。</li>
</td>
<td>
<ul>
<li>注文履歴の更新： <code>We refunded $X online. Transaction ID: transactionID</code></li>
<li>注文履歴の更新： <code>Order notified as partly canceled at: Date and Hour</code></li>
<li>注文返金メールの受け取り： <code>$x amount was refunded</code></li>
<li>注文ステータス： <code>Processing</code>.</li>
<li>Adobe Commerceで作成されたクレジットメモ（cron が機能するまでお待ちください）。</li>
<li>一部の品目が選択されていない場合は、 [!UICONTROL Ready for Pickup] nil pick または refund セクションを含む e メールが表示されます。 <code>DISPLAY COMMENT HISTORY</code> 表示 <code>Order is ready for pickup, but some items not available.</code>.</li>
<li><code>CUSTOMER NOTIFIED</code> フラグが <code>true</code>.</li>
</ul>
</td>
</tr>
<td><strong>ピックアップの準備完了</br></br>完全なキャンセル</br>（すべての製品は、0 数量のピッキング済みとして設定されます）</strong></td>
<td>
<ol>
<li>注文を行います。</li>
<li>オーダーが同期されるまで待ちます。</li>
<li>請求書が作成され（承認および取り込みの場合）、および受け取った請求書の電子メールが受け取られたことを確認します。</li>
<li>Postmanに移動し、すべての製品をに設定して、ピックアップ準備完了リクエストを実行します。 <code>picked</code> 次を使用 <code>0 qty</code>.</li>
</ol>
</td>
<td>
<ul>
<li>注文履歴が更新されました： <code>We refunded $X offline</code></li>
<li>オーダーのステータスは <code>CLOSED</code>.
<li>クレジット・メモが作成されます。 （cron が動作するまで待ちます）。</li>
<li>受け取った返金メール： <code>$x amount was refunded</code></li>
<li>注文のキャンセルメールが送信されました。</li>
</ul>
</td>
</tr>
<tr>
<td><strong>ピックアップの準備完了 — 部分キャンセル</strong></br></br><strong>( 一部の製品はピッキングされ、一部は <code>0 qty</code>)</strong>
</td>
<td>
<ol>
<li>注文を行います。</li>
<li>オーダーが同期されるまで待ちます。</li>
<li>請求書が作成され（承認および取り込みの場合）、および受け取った請求書の電子メールが受け取られたことを確認します。</li>
<li>Postmanに移動し、0 数量でピックされた製品と残りの製品の一部をピックアップ済みとして、「ピックアップ準備完了」要求を実行します。</li>
</ol>
</td>
<td>
<ul>
<li><code>Your order is ready for pickup</code> 次を使用 [!UICONTROL Ready for Pickup Items] および [!UICONTROL Canceled Items] テーブル。 </li>
<li>受注ステータスは「受注準備完了」です。 </li>
<li>注文履歴が更新されました： <code>We refunded $X offline.</code>
<li>注文履歴が更新されました： <code>Order notified as partly canceled at: Date and hour</code>
<li>受け取った返金メール： <code>$x amount was refunded</code>
<li>クレジットメモが作成されます。 （cron が動作するまで待ちます）。</li>
</ul>
</td>
</tr>
<tr>
<td><strong>ピックアップの準備完了 — 部分キャンセル</br></br>一部の製品はピッキングされ、一部は <code>0 qty</code>)</strong>
</td>
<td><ol>
<li>注文を行います。</li>
<li>オーダーが同期されるまで待ちます。</li>
<li>請求書が作成され（承認および取り込みの場合）、および受け取った請求書の電子メールが受け取られたことを確認します。</li>
<li>Postmanに移動し、0 数量でピックされた製品と残りの製品の一部をピックアップ済みとして、「ピックアップ準備完了」要求を実行します。</li>
</ol>
</td>
<td><ul>
<li><code>Your order is ready for pickup</code> 次を使用 [!UICONTROL Ready for Pickup Items] および [!UICONTROL Canceled Items] テーブル。 </li>
<li>受注ステータスは「受注準備完了」です。 </li>
<li>注文履歴が更新されました： <code>We refunded $X offline.</code>
<li>注文履歴が更新されました： <code>Order notified as partly canceled at: Date and hour</code>
<li>受け取った返金メール： <code>$x amount was refunded</code>
<li>クレジットメモが作成されます。 （cron が動作するまで待ちます）。</li>
</ul>
</td>
</tr>
<tr>
<td><strong>分注済み（分注中） </br></br>完全キャンセル（すべての製品が却下済みとして設定されます）</strong>
</td>
<td>
<ol>
<li>注文を行います。</li>
<li>オーダーが同期されるまで待ちます。</li>
<li>請求書が作成され（承認および取り込みの場合）、および受け取った請求書の電子メールが受け取られたことを確認します。</li>
<li>Postmanに移動し、すべての製品を選択済みとして、「ピックアップ準備完了」リクエストを実行します。</li>
<li>メールボックスを開き、[ ピックアップの準備完了 ] メールを探します。 次に、「**」をクリックします[!UICONTROL Confirm Arrival]**.</li>
<li>チェックインします。</li>
<li>Postmanに移動し、却下済みとして設定されたすべての製品でディスペンス済みリクエストを実行します。</li>
</ol>
<td><ul>
<li>注文履歴が更新されました： <code>We refunded $X offline.</code></li>
<li>受け取った返金メール： <code>$x amount was refunded</code></li>
<li>ステータスがに設定されました <code>CLOSED</code>.</li>
<li>クレジットメモが作成されました。 （cron が動作するまで待ちます）。</li>
</ul>
</td>
</tr>
<tr>
<td><strong>分注済み（分注中）</br></br>部分キャンセル</br>（一部の製品は配布され、一部は拒否されます）。</strong>
</td>
<td>
<ol>
<li>注文を行います。</li>
<li>オーダーが同期されるまで待ちます。</li>
<li>請求書が作成され（承認および取り込みの場合）、および受け取った請求書の電子メールが受け取られたことを確認します。</li>
<li>Postmanに移動し、すべての製品を選択済みとして、「ピックアップ準備完了」リクエストを実行します。</li>
<li>メールボックスを開きます。 [ ピックアップの準備 ] メールを探し、[ ] を選択します。 <code>Confirm Arrival</code>.</li>
<li>チェックインします。</li>
<li>Postmanに移動し、配布する製品と却下する製品を使用して、配布済みリクエストを実行します</li>
</ol>
</td>
<td>
<li>注文履歴が更新されました： <code>We refunded $X offline</code></li>
<li><code>Order notified as partly canceled at: Date and Hour</code>
<li>受け取った返金メール： <code>$x amount was refunded</code>
<li>注文ステータスが「 」に設定されている <code>Ready for pickup Dispensed</code>
<li>クレジットメモが作成されました。 （cron が動作するまで待ちます）。</li>
</td>
</tr>
<tr>
<td> <strong>返品後の新規 RMA（フル）</strong>
</td>
<td>
<ol>
<li>注文を行います。</li>
<li>オーダーが同期されるまで待ちます。</li>
<li>「承認および取得」オプションが設定されている場合は、請求書が作成され、顧客が請求書の電子メールを受け取ったことを確認します。</li>
<li>Postmanのすべての製品を選択します。</li>
<li>チェックインします。</li>
<li>ディスペンスを作る。</li>
<li>オーダーに移動し、「 」を選択します。<strong>[!UICONTROL Create returns]=
<li>RMA を作成します。</li>
</ol>
</td>
<td>
<ul>
<li>RMA が作成され、次の図の下に表示されます。 <strong>[!UICONTROL Returns]</b> 」タブをクリックします。</li>
<li>お客様が RMA 確認 E メールを受け取りました。</li>
</ul>
</td>
</tr>
<tr>
<td><strong>返品後の新規 RMA：一部</strong>
</td>
<td>
<ol>
<li>注文を行います。</li>
<li>オーダーが同期されるまで待ちます。</li>
<li>請求書が作成され（承認および取り込みの場合）、および受け取った請求書の電子メールが受け取られたことを確認します。</li>
<li>Postmanのすべての製品を選択します。</li>
<li>チェックインします。</li>
<li>ディスペンスを作る。</li>
<li>オーダーに移動し、「 」を選択します。  <strong>[!UICONTROL Create returns]</strong></li>
<li>受注した製品の一部を含む RMA を作成します。</li>
</ol>
<td>
<ul>
<li>RMA が作成され、下に表示されます。 <strong>[!UICONTROL Returns]</strong> 」タブをクリックします。</li>
<li>お客様が RMA 確認 E メールを受け取りました。</li>
<li>RMA の作成後、RMA 認証を取得します。管理者から、に移動します。 <strong>[!UICONTROL Sales > Returns]</strong>. 作成して承認した RMA を選択します。</li>
<li>お客様が RMA 承認確認 E メールを受け取ったことを確認します。</li>
<li>払い戻しがトランザクションと注文履歴に追加されたことを確認します。</li>
</ul>
</td>
</tr>
</table>


### フルフィルメントアプリの権限を保存

このテストプランのこのセクションでは、ストアフルフィルメントアプリユーザーのアカウント管理について説明します。

- Store Associate が、Adobe Commerce Admin から作成された新しいユーザーアカウントで認証できることを確認します。
- 既存のアカウントへの更新が正常に適用されたことを確認します。

**機能領域：** Adobe Commerce Admin</br>
**役割：** 管理者、ストアの関連付け</br>
**テストタイプ：** すべて正

<table style="table-layout:auto">
<tr>
<th>関数</th>
<th>シナリオ</th>
<th>期待される結果</th>
</tr>
<tr>
<td><strong>ユーザーアカウント管理 — アカウントの作成</strong></br></br>
</td>
<td>
<ol>
<li><strong>管理者</strong> — Adobe Commerce Admin にログインします。</li>
<li>に移動します。 <strong>[!UICONTROL System] &gt; フルフィルメントアプリの保存権限 &gt; すべてのストアフルフィルメントアプリのユーザー</strong></li>
<li><strong>新しいユーザーを追加します。</strong></li>
</ol>
<td>
<ul>
<li>アカウントが正常に作成されました。</li>
<li>新しいユーザーアカウントが [!UICONTROL Store Fulfillment Users] ダッシュボード。</li>
<li><strong>ストアの関連付け</strong> 新しいユーザーアカウントで Store Assist アプリにログインします。</li>
</ul>
</td>
</tr>
<tr>
<td><strong>ユーザーアカウント管理 — 既存のユーザーアカウントを更新</strong>
</td>
<td>
<ol>
<li>管理者ユーザーアカウントでAdobe Commerce Admin にログインします。</li>
<li>に移動します。 <strong>[!UICONTROL System] &gt; フルフィルメントアプリの保存権限 &gt; すべてのストアフルフィルメントアプリのユーザー</strong>.</li>
<li>[ ユーザーアカウント ] の一覧で、既存のアクティブなユーザーアカウントを開くには、 <strong>[!UICONTROL Edit]</strong>.
<li>次を変更してアカウントを無効にする <strong>[!UICONTROL Is Active]</strong> から <strong>いいえ</strong>.</li>
</ol>
</td>
<td>
<ul>
<li>次の日： <strong>[!UICONTROL Store Fulfillment App Users]</strong> ダッシュボードに表示される更新済みアカウントのステータスが次の値に変更されました： <strong>[!UICONTROL Inactive]</strong>.</li>
<li>Store Associate は、非アクティブなアカウントの資格情報を使用して Store Assist アプリにログインできません。</li>
</ul>
</td>
</tr>
</table>

## Adobe Commerceの製品タイプ

Adobe Commerceの製品タイプのテストシナリオでは、顧客が様々な製品タイプの正しい製品、在庫、配信方法情報を表示することを確認します。

- [!UICONTROL Configurable]
- [!UICONTROL Grouped]
- [!UICONTROL Virtual]
- [!UICONTROL Bundle products] Adobe Commerce店の

**機能領域：** Adobe Commerce Frontend</br>
**役割：** Store Assist App ユーザー (Store Associate)</br>
**テストタイプ：** すべて正

<table style="table-layout:auto">
<tr>
<th>関数</th>
<th>シナリオ</th>
<th>コメント</th>
</tr>
<tr>
<td><strong>設定可能な製品</strong>
</td>
<td>
<ul>
<li>ユーザーが、有効なソース、在庫が割り当てられ、在庫に項目が含まれていることを確認し、子製品を確認します。</li>
<li>別のストアを選択する際に、使用できないオプションがクロスアウトされて表示されることを確認します。</li>
<li>ユーザーが別のストアを選択した場合、設定可能なオプションが選択解除されることを確認します。</li>
<li>設定可能な製品が既に買い物かごに入っていて、ユーザーが別のストアを選択した場合、製品が在庫切れとして表示されることを確認します。</li>
</ul>
</td>
<td></td>
</td>
</tr>
<tr>
<td><strong>グループ化された製品</strong>
</td>
<td>
<ul>
<li>配信方法および [!UICONTROL Add to cart] すべての子製品が
<code>qty</code> に設定 <code>0</code>.</li>
<li>少なくとも 1 つの子製品に <code>qty</code> に設定 <code>0.</code></li>
<li>を確認します。 [!UICONTROL Store Pickup Delivery] メソッドは、 [!UICONTROL Available for Store Pickup] 有効。 （子製品を確認します。）</li>
</ul>
</td>
<td></td>
</tr>
<tr>
<td><strong>仮想製品</strong>
</td>
<td>
仮想製品が  [!UICONTROL In-store Pickup] 配信方法。
<td></td>
</td>
</tr>
<tr>
<td><strong>製品のバンドル</strong>
</td>
<td>
<ul>
<li>少なくとも 1 つの子製品に [!UICONTROL Available for Store Pickup] 無効の場合、「ピックアップを保存」配信オプションは顧客には使用できません。</li>
<li>少なくとも 1 つの子製品に [!UICONTROL Available for Home Delivery] 無効に設定されている場合、「ホーム配信」オプションはお客様には使用できません。</li>
<li>バンドル内の子製品の少なくとも 1 つが在庫切れであるかどうかを確認し、バンドル（親製品）も次のように表示されます。 [!UICONTROL Out of stock].</li>
</ul>
</td>
<td></td>
</tr>
<tbody>
</table>

## チェックインエクスペリエンス

このテスト計画のこの節では、次の機能について、店舗受取注文のチェックインエクスペリエンスを扱います。

- 代替ピックアップ連絡先 — 追加するワークフローを確認します。 [!UICONTROL Alternate Pickup Contact] および選択 [!UICONTROL Preferred Contact] 店舗受取注文。

- 「チェックインフォーム」(Check-in form) — 店舗受取注文のチェックイン要求を送信するワークフローを検証します。

**機能領域：** 買い物かごのチェックアウト、受け取り注文のチェックインフォーム</br>
**役割：** 管理者、顧客、ストア関連付け</br>
**テストタイプ：** すべて正

### 代替ピックアップ連絡先


**機能領域：** 買い物かごのチェックアウト</br>
**役割：** 顧客</br>
**テストタイプ：** すべて正

<table style="table-layout:auto">
<tr>
<th>関数</th>
<th>シナリオ</th>
<th>期待される結果</th>
</tr>
<tr>
<td><strong>代替ピックアップ連絡先</br>
チェックイン<strong>
</td>
<td>
顧客が店頭受取オプションを使用して注文を送信します。</td>
<td>チェックアウトプロセス中に、顧客が [!UICONTROL Alternate Pickup Contact] 「発送」ステップの「 」オプション。
</td>
</tr>
<tr>
<td><strong>代替ピックアップ優先連絡先、チェックイン</strong>
<td>
顧客が店頭受取オプションを使用して注文を送信します。 チェックアウト時に、顧客が [!UICONTROL Alternate Pickup Contact].</td>
<td>チェックアウトプロセス中に、顧客が [!UICONTROL Preferred Contact] オプションを選択します。</td>
</td>
</tr>
<tr>
<td><strong>代替ピックアップ連絡先の詳細、チェックイン</strong>
</td>
<td>
顧客が店頭受取オプションを使用して注文を送信します。 チェックアウト時に、顧客が [!UICONTROL Alternate Pickup Contact] をクリックします。
</td>
<td>連絡先の詳細を入力するための入力オプションが表示されます。 [!UICONTROL First name], [!UICONTROL Last name], [!UICONTROL Phone]、および [!UICONTROL Email].</td>
</tr>
<tr>
<td><strong>代替ピックアップ、メールのチェックイン</strong>
</td>
<td>顧客が店頭受取オプションを使用して注文を送信します。 チェックアウト時に、顧客が [!UICONTROL Alternate Pickup Contact] 発送ステップで、連絡先詳細を追加し、注文を発行します。</td>
<td>顧客と代替担当者の両方が、注文のチェックインメールを受け取ります。</td>
</tr>
<td><strong>代替ピックアップ、注文の詳細</strong></td>
<td>顧客が店頭受取オプションを使用して注文を送信します。 チェックアウト時に、顧客が [!UICONTROL Alternate Pickup Contact] 発送ステップで、連絡先詳細を追加し、注文を発行します。</td>
<td>管理者は、保存された注文に関する追加の連絡先情報を確認します。</td>
</tr>
<tr>
<td><strong>代替ピックアップ連絡先、ストア関連注文ビュー</strong>
</td>
<td>顧客が店頭受取オプションを使用して注文を送信します。 チェックアウト時に、顧客が [!UICONTROL Alternate Pickup Contact] 発送ステップで、連絡先詳細を追加し、注文を発行します。</td>
<td>Store Associate は、FaaS/ChaaS での注文に関する追加の連絡先情報を確認できます。</td>
</td>
</tr>
</tbody>
</table>

### チェックインフォーム


**機能領域：** チェックインフォーム</br>
**役割：** 顧客</br>
**テストタイプ：** すべて正

<table style="table-layout:auto">
<tr>
<th>関数</th>
<th>シナリオ</th>
<th>期待される結果</th>
</tr>
<tr>
<td><strong>チェックイン処理 — リクエストを送信</strong>
</td>
<td>チェックインフォームで、顧客がすべての必須フィールドに入力し、リクエストを送信します。</td>
<td>顧客が成功応答を受け取る。</td>
</tr>
<tr>
<td><strong>「アクションのチェックイン」(Check in Action) — リクエストの詳細を表示します。</strong></td>
<td>顧客がチェックインリクエストを正常に送信しました。</td>
<td>FaaS システムで注文ステータスが更新され、Store Associate が FaaS でチェックイン要求の詳細を確認できます。
</td>
</tr>
<tr>
<td><strong>「チェックイン・アクション」 — 要求を 1 回だけ送信します。</strong></td>
<td>注文のチェックインリクエストを送信した後、顧客がリンクを選択して再度チェックインします。</td>
<td>チェックインフォームでは、顧客はフォームを編集または再送信するオプションを表示しません。</td>
</tr>
<tr>
<td><strong>チェックイン処理 — 到着を確認</strong></td>
<td>店舗でのピックアップの準備ができたとマークされた FaaS。 顧客が「ピックアップ準備完了」の E メールを受け取り、を選択します。 [!UICONTROL Confirm Arrival].</td>
<td>顧客に注文のチェックインフォームが表示されます。</td>
</tr>
</tbody>
</table>

## ストアアシストアプリ

テスト計画のこの節では、Store Assist App での順序、選択、およびハンドオフのテストワークフローに関するシナリオを説明します。

**機能領域：** ストアアシストアプリ</br>
**役割：** ストアの関連付け</br>
**テストタイプ：** すべて正

<table style="table-layout:auto">
<tr>
<th>関数</th>
<th>シナリオ</th>
<th>期待される結果</th>
</tr>
<tr>
<td>
<strong>単一注文ピッキング — ハッピーパス、カーブサイドピックアップ</strong></td>
<td>単数品目と複数数量品目を選択します。 nil の選択はなく、（ステージングを含む）カーブサイドピックアップも行いません。
</td>
<td>
</td>
</tr>
<tr>
<td><strong>複数注文ピッキング — ハッピーパス、カーブサイドピックアップ</strong></td>
<td>単一品目と複数品目。 nil ピックがなく、カーブサイドピックアップ（ステージングを使用）</td>
<td></td>
</tr>
<tr>
<td><strong>単一注文ピッキング — ハッピーパスの店内ピックアップ</strong></td>
<td>単一品目と複数品目。 nil ピックがない場合、および店内ピックアップ（ステージングを使用）</td>
<td>
</td>
</tr>
<tr>
<td><strong>複数注文ピッキング — ハッピーパス、店舗でのピックアップ</strong></td>
<td>単数品目と複数数量品目を選択します。 nil の選択はなく、（ステージングを含む）カーブサイドピックアップも行いません。</td>
<td></td>
</tr>
<tr>
<td><strong>単一注文ピッキング — ハッピーパスではなく、店内ピックアップ</strong></td>
<td>一部ピックアップと日付ピックアップと店舗ピックアップを含む単一品目と複数数量品目をピックします（ステージングを含む）。</td>
</td>
<td></td>
</tr>
<td><strong>複数注文ピッキング：パスカーブサイドピックアップが不適切</strong></td>
<td>一部ピックアップと日付ピックアップと店舗ピックアップを含む単一品目と複数数量品目をピックします（ステージングを含む）。</td>
<td></td>
</tr>
<td><strong>単一注文ピッキング：ハッピーパスではなく、カーブサイドピックアップ</strong></td>
<td>一部ピックアップおよび非選択ピックアップおよびカーブサイドピックアップを含む単一および複数数量の品目をピックします（ステージングを含む）</strong></td>
</td>
<td></td>
</tr>
<tr><td><strong>発注済 — ピッキング前にキャンセル済</strong></td>
<td></td>
<td></td>
</tr>
<tr>
<td><strong>注文が完了しました — ハンドオフ前にキャンセルされました</strong></td>
<td></td>
<td></td>
</tr>
<tr>
<td><strong>発注済み — 注文内検索モジュール</strong></td>
<td></td>
<td></td>
</tr>
<tr><td><strong>発注済み — ハンドオフの検索と手動チェックイン</strong></td>
<td></td>
<td></td>
</tr>
<tr><td><strong>発注済み — ピッカーでマークされたすべての品目が未選択または使用不可</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>バンドル項目 — ピッキングおよびハンドオフと共に発注</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>発注済み — 却下を含む手渡し</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>発注済み — すべての品目の却下を含むハンドオフ</strong></td>
<td></td>
<td></td></tr>
</tbody>
</table>

## デプロイ

ソリューションが設定され、仕様に合わせてテストされたことを確認したら、ステージングから実稼動にデプロイする準備が整います。

導入とテストは、インフラストラクチャと機能によって異なります。

>[!TIP]
>
>クラウドインフラストラクチャプロジェクト上のAdobe Commerceのデプロイメントのガイドライン、チェックリスト、ベストプラクティスについては、 [ストアをデプロイ](https://devdocs.magento.com/cloud/live/stage-prod-live.html) ( Adobe Commerce開発者向けドキュメント )。
