---
title: セールスメールテンプレート
description: 店舗受取注文の受取プロセス中に、顧客および店舗管理者とのコミュニケーションのためのトランザクション電子メールテンプレートを設定します。
role: Admin
level: Intermediate
feature: Shipping/Delivery, Communications, Configuration
exl-id: 688732e3-06f0-4613-a589-2d465597eb28
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '1202'
ht-degree: 0%

---


# セールスメールテンプレート

「Store Fulfilment」は、注文ワークフローと達成ワークフローをサポートする、トランザクション E メールテンプレートの拡張セットを提供します。 チャネル間で一貫性のある自動通信とメッセージを提供します。顧客と店舗の管理者に対して、注文ステータスの変更や店舗での受け取り注文の指示などを通知します。

「フルフィルメントの保存」の電子メールテンプレートは、デフォルトのメッセージおよび設定で構成されます。 Adobe Commerceのマーチャント管理者は、設定を管理および変更でき、様々なシナリオで顧客とコミュニケーションを取るための電子メールテンプレートを選択できます。 管理者は、テンプレートの設定とカスタマイズもおこなえます。

管理者からセールスメールテンプレートを設定します。 **[!UICONTROL Stores > Configuration > Sales > Sales Emails]**.

## 電子メール — 一般設定

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
<td><strong>非同期送信</strong></td>
<td>この機能を無効にします。 非同期電子メール送信はサポートされていません。 Store Pickup の最速の通信と応答時間を得るには、バッチ処理の代わりにメールを直ちに送信してください。 </td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
</tbody></table>

## 店舗での受け取り準備完了

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
<td><strong>有効</strong></td>
<td>店舗の関連付けが注文のピッキングを完了したときに、この E メールが顧客に送信されます。 電子メール通知を無効にするには、「No」に設定します。 電子メールテンプレートが無効になっている場合、注文がストアの関連者によって選択されるのを防ぐことはできません。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>受け取りメール送信者の注文準備ができました</strong></td>
<td>E メール通知の送信時に使用する送信者 ID。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>受け取り用メールテンプレートのオーダー準備完了</strong></td>
<td>登録済み顧客に通知するために使用する電子メールメッセージテンプレート。 統合環境にはデフォルトのテンプレートが用意されています。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<td><strong>ゲスト用のピックアップメールテンプレートのオーダー準備ができました</strong></td>
<td>ゲスト顧客に通知するために使用される電子メールメッセージテンプレート。 統合環境にはデフォルトのテンプレートが用意されています。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>代替ピックアップ連絡先用のピックアップメールテンプレートのオーダー準備完了</strong></td>
<td>注文内で名前が付けられた追加の連絡先に通知するために使用される電子メールメッセージテンプレート。 統合環境にはデフォルトのテンプレートが用意されています。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>受け取り用のメールコピーを次に送信：</strong></td>
<td>各通知のコピーを送信する電子メールアドレスのコンマ区切りリストです。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>受け取り用メールコピーメソッドの注文準備ができました</strong></td>
<td>使用する E メールコピー方法 (CCC)。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
</tbody></table>


## 注文がストアで取得されました

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
<td><strong>有効</strong></td>
<td>この電子メールは、ストアから注文を受け取ったことを確認するために顧客に送信されます。 電子メール通知を無効にするには、「No」に設定します。 E メールテンプレートが無効になっている場合、注文が顧客によって受け取られるのを防ぐことはできません。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>注文はメール送信者に取得されました</strong></td>
<td>E メール通知の送信時に使用する送信者 ID。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>注文はメールテンプレートを取得済みです</strong></td>
<td>登録済み顧客に通知するために使用する電子メールメッセージテンプレート。 統合によって提供されるデフォルトのテンプレート</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<td><strong>注文はゲスト用のメールテンプレートを取得しました</strong></td>
<td>ゲスト顧客に通知するために使用される電子メールメッセージテンプレート。 統合環境にはデフォルトのテンプレートが用意されています。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>送信先のメールコピーが取得されました</strong></td>
<td>各通知のコピーを送信する電子メールアドレスのコンマ区切りリストです。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>送信はメールコピーメソッドを取得済みです</strong></td>
<td>使用する E メールコピー方法 (CCC)。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
</tbody></table>

## 注文遅延

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
<td><strong>有効</strong></td>
<td>この E メールは顧客に送信され、商店店での注文の処理や選択の遅れを通知します。 電子メール通知を無効にするには、「No」に設定します。 電子メールテンプレートが無効になっている場合、この機能では注文が遅延するのを防ぐことはできません。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>注文遅延メール送信者
</strong></td>
<td>E メール通知の送信時に使用する送信者 ID。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>注文遅延メールテンプレート</strong></td>
<td>登録済み顧客に通知するために使用する電子メールメッセージテンプレート。 統合環境にはデフォルトのテンプレートが用意されています。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<td><strong>ゲスト用の注文遅延メールテンプレート</strong></td>
<td>ゲスト顧客に通知するために使用される電子メールメッセージテンプレート。 統合環境にはデフォルトのテンプレートが用意されています。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>注文遅延メールコピーの送信先</strong></td>
<td>各通知のコピーを送信する電子メールアドレスのコンマ区切りリストです。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>Send Order Delayed Copy メソッド</strong></td>
<td>使用する E メールコピー方法 (CCC)。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
</tbody></table>



## オーダーがキャンセルされました

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
<td><strong>有効</strong></td>
<td>この電子メールは顧客に送信され、マーチャントストアで注文がキャンセルされたことが通知されます。 をに設定します。 <code>No</code> 電子メール通知を無効にする。 電子メールテンプレートが無効になっている場合は、注文がキャンセルされることを防ぐことはできません。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>注文がキャンセルされたメール送信者
</strong></td>
<td>E メール通知の送信時に使用する送信者 ID。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>注文キャンセル済みメールテンプレート</strong></td>
<td>登録済み顧客に通知するために使用する電子メールメッセージテンプレート。 統合環境にはデフォルトのテンプレートが用意されています。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<td><strong>ゲスト用にキャンセルされた注文</strong></td>
<td>ゲスト顧客に通知するために使用される電子メールメッセージテンプレート。 統合環境にはデフォルトのテンプレートが用意されています。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>注文キャンセル済みメールコピーの送信先</strong></td>
<td>各通知のコピーを送信する電子メールアドレスのコンマ区切りリストです。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>注文キャンセル済みコピーメソッドの送信</strong></td>
<td>使用する E メールコピー方法 (CCC)。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
</tbody></table>


## 一部キャンセル済みの注文

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
<td><strong>有効</strong></td>
<td>この電子メールは顧客に送信され、商店店で注文の一部がキャンセルされたことが通知されます。 をに設定します。 <code>No</code> 電子メール通知を無効にする。 E メールテンプレートが無効になっている場合は、注文が一部キャンセルされるのを防ぐことはできません。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>注文の一部がキャンセルされたメール送信者
</strong></td>
<td>E メール通知の送信時に使用する送信者 ID。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>注文の一部がキャンセルされたメールテンプレート</strong></td>
<td>登録済み顧客に通知するために使用する電子メールメッセージテンプレート。 統合環境にはデフォルトのテンプレートが用意されています。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<td><strong>代替ピックアップ連絡先の一部取り消されたメールテンプレートの注文</strong></td>
<td>注文内で名前が付けられた追加の連絡先に通知するために使用される電子メールメッセージテンプレート。 統合環境にはデフォルトのテンプレートが用意されています。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>ゲストの注文が一部キャンセルされました</strong></td>
<td>ゲスト顧客に通知するために使用される電子メールメッセージテンプレート。 統合環境にはデフォルトのテンプレートが用意されています。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>注文の一部キャンセル済みメールコピーの送信先</strong></td>
<td>各通知のコピーを送信する電子メールアドレスのコンマ区切りリストです。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>注文の一部キャンセルされたコピーメソッドを送信</strong></td>
<td>使用する E メールコピー方法 (CCC)。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
</tbody></table>

## 出荷先ストア

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
<td><strong>注文は商品を出荷して保存する E メール送信者です</strong></td>
<td>指定した商人の担当者に、在庫が利用可能になるまで商店店で採用できないすべてのオープン注文の集計レポートとして送信された電子メール。 </br></br> マーチャントはこのレポートを使用して、店舗間在庫移動または補充を開始および管理できます。 </br></br>この通知は、 [!DNL Ship-to-Store] 機能が有効になっている。
</br></br>このラベルは、選択した配送業者または使用可能な配送方法のラベルには影響しません。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>発送先ストアのメール受信者</strong></td>
<td>各通知のコピーを送信する電子メールアドレスのコンマ区切りリストです。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>メールテンプレート</strong></td>
<td>受信者に通知するために使用する電子メールメッセージテンプレート。 統合環境にはデフォルトのテンプレートが用意されています。</td>
<td>ストア表示</td>
<td>いいえ</td>
</tr>
</tbody></table>

>[!NOTE]
>
>バックオーダーを許可する場合、これらのオーダーに関する通知を受け取るには、管理者の電子メールアドレスを指定する必要があります。 アドレスを次の設定に追加します。 **[!UICONTROL Send Order Delayed Email Copy To]** （内） [注文遅延](#order-delayed) テンプレート、および [!UICONTROL Ship To Store Email Recipients] （内） [出荷先ストア](#ship-to-store) テンプレート。



