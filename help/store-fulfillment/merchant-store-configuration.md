---
title: マーチャントストアの設定
description: マーチャントストアとしてInventory managementソースを強化しました。
role: User, Admin
level: Intermediate
exl-id: 7c3444d0-5ecb-4ac1-aa81-e48eea290f5d
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '1209'
ht-degree: 0%

---

# マーチャントストア（ソース）の構成

このソリューションは、商人向けの運用指向の機能を備えたストックソースを拡張することで、Inventory managementのネイティブ機能を強化します。

- ストアの場所の地理的座標を追加
- ソースを [!DNL Store Pickup Location] 使用可能な出荷機能（出荷先店舗、出荷元店舗）を指定します。
- 顧客にピックアップの詳細と指示を伝えるために、利用可能なピックアップオプション（店舗またはカーブサイド）、カスタマイズされたピックアップ指示、その他の情報を指定します

用語 _ソース_ および _商店の場所_ は同じ意味で使用されます。 すべてのレコードは在庫ソースですが、設定に応じて、ソースはマーチャントストアの場所にすることもできます。

Merchant Stores の設定を管理者から管理します。 **[!UICONTROL Stores > Inventory > Sources >  Edit Source]**.

>[!NOTE]
>
>設定プロセス中に、ソースを作成した後、または既存のソースを更新した後に、キャッシュをフラッシュする必要が生じる場合があります。

## **一般**

<table>
<tbody>
<tr>
<th>フィールド</th>
<th>説明</th>
<th>範囲</th>
<th>必須</th>
</tr>
<tr>
<td><strong>[!UICONTROL Latitude]</strong></br><code>Base Attribute: latitude</code></td>
<td>商人の店舗の位置の緯度座標。 この必須情報は、ストアフロントエクスペリエンス上のロケーション検索やマップ配置に使用されます。 値は、検証に合格するには、ストアの正確なアドレスと一致する必要があります。</td>
<td>グローバル</td>
<td>はい</td>
</tr>
<tr>
<td><strong>[!UICONTROL Longitude]</strong></br><code>Base Attribute: Longitude</code></td>
<td>商店店舗の位置の長さの座標。 この必須情報は、ストアフロントエクスペリエンス上のロケーション検索やマップ配置に使用されます。 値は、検証に合格するには、ストアの正確なアドレスと一致する必要があります。</td>
<td>グローバル</td>
<td>はい</td>
</tr>
<tr>
<td><strong>[!UICONTROL Use as Pickup Location]</br></strong><code>Base Attribute: is_pickup_location_active</code></td>
<td>ソースを使用可能な受け取り店舗の場所として指定します。 この設定は、ソースを同期して訪問者に表示するかどうかを決定します。</td>
<td>グローバル</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship to Store]</strong><br><code>Extension Attribute: allow_ship_to_store</code></td>
<td>出荷先店舗機能をソースレベルで設定します。 詳しくは、[ 一般設定 ](enable-general.md) オプションを参照してください。 <strong>[!UICONTROL Enable Ship To Store]
</tr>
<tr>
<td><strong>[!UICONTROL Latitude]</strong></br><code>Base Attribute: latitude</code></td>
<td>商人の店舗の位置の緯度座標。 この必須情報は、ストアフロントエクスペリエンス上のロケーション検索やマップ配置に使用されます。 値は、検証に合格するには、ストアの正確なアドレスと一致する必要があります。</td>
<td>グローバル</td>
<td>はい</td>
</tr>
<tr>
<td><strong>[!UICONTROL Longitude]</strong></br><code>Base Attribute: Longitude</code></td>
<td>商店店舗の位置の長さの座標。 この必須情報は、ストアフロントエクスペリエンス上のロケーション検索やマップ配置に使用されます。 値は、検証に合格するには、ストアの正確なアドレスと一致する必要があります。</td>
<td>グローバル</td>
<td>はい</td>
</tr>
<tr>
<td><strong>[!UICONTROL Use as Pickup Location]</br></strong><code>Base Attribute: is_pickup_location_active</code></td>
<td>ソースを使用可能な受け取り店舗の場所として指定します。 この設定は、ソースを同期して訪問者に表示するかどうかを決定します。</td>
<td>グローバル</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship to Store]</strong></br> <code>Extension Attribute: [!DNL allow_ship_to_store]</code></td>
<td>出荷先店舗機能をソースレベルで設定します。 詳しくは、[ 一般設定 ](enable-general.md) オプションを参照してください。 <strong>[!UICONTROL Enable Ship To Store]</strong>.</td>
<td>グローバル</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong></br><code>Extension Attribute: [!DNL use_as_shipping_source]</code></td>
 <td>ソースレベルで出荷元ストア機能を設定します。 詳しくは、[ 一般設定 ](enable-general.md) オプションを参照してください。 [!UICONTROL Enable Ship From Store].</td>
<td>グローバル</td>
<td>いいえ</td>
</tr>
<tr>
<td>グローバル</td>
<td>いいえ</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong><code>Extension Attribute: [!DNL use_as_shipping_source]</code></td><td></td><td></td><td></td></tr></tbody></table>



| **フィールド** | **説明** | **範囲** | **必須** |
|--------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Latitude]**</br>`Base Attribute: latitude` | 商人の店舗の位置の緯度座標。 この必須情報は、ストアフロントエクスペリエンス上のロケーション検索やマップ配置に使用されます。 値は、検証に合格するには、ストアの正確なアドレスと一致する必要があります。 | グローバル | はい |
| **[!UICONTROL Longitude]**</br>`Base Attribute: Longitude` | 商店店舗の位置の長さの座標。 この必須情報は、ストアフロントエクスペリエンス上のロケーション検索やマップ配置に使用されます。 値は、検証に合格するには、ストアの正確なアドレスと一致する必要があります。 | グローバル | はい |
| **[!UICONTROL Use as Pickup Location]**</br>`Base Attribute:[!DNL is_pickup_location_active]` | ソースを使用可能な受け取り店舗の場所として指定します。 この設定は、ソースを同期して訪問者に表示するかどうかを決定します。 | グローバル | いいえ |
| **[!UICONTROL Enable Ship to Store]**</br>`Extension Attribute: [!DNL allow_ship_to_store]` | 出荷先店舗機能をソースレベルで設定します。 詳しくは、 [一般設定](enable-general.md) オプション **[!UICONTROL Enable Ship To Store]**. | グローバル | いいえ |
| **[!UICONTROL Enable Ship From Store]**</br>`Extension Attribute: [!DNL use_as_shipping_source]` | ソースレベルで出荷元ストア機能を設定します。 詳しくは、 [一般設定](enable-general.md) オプション [!UICONTROL Enable Ship From Store] | グローバル | いいえ |

{style=&quot;table-layout:auto&quot;}

## ピックアップの場所の設定

| **フィールド** | **説明** | **範囲** | **必須** |
|-----------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Allow In-Store Pickup]**</br>`Extension Attribute: [!DNL store_pickup_enabled]` | 2 つのピックアップオプションの 1 つ。 [!DNL In-Store Pickup] は、顧客が商店の店舗の場所に入って注文を取得できるようにする機能を指します。 </br></br>有効にすると、このオプションがチェックアウト時に顧客に表示される場合があります。 </br></br>また、このオプションは、グローバル設定を [!UICONTROL Enable In-store Pickup] が [!UICONTROL Delivery Method] 対象 [!UICONTROL In-store Pickup] | グローバル | いいえ |
| **店舗での受け取り手順**</br>`Extension Attribute: store_pickup_instructions` | 顧客に配信されるカスタマイズ可能なメッセージ **店舗での受け取り準備ができた注文** 電子メール通知。 | グローバル | いいえ |
| **カーブサイドを許可**</br>`Extension Attribute: curbside_enabled` | 2 つのピックアップオプションの 1 つ。 カーブサイド配送では、顧客はマーチャントストアの指定された場所に車両を駐車できます。 このシナリオでは、注文は店舗関連者によって顧客に配信されます。 </br></br>有効にすると、このオプションがチェックアウト時に顧客に表示される場合があります。 また、お客様は、チェックインプロセス中に、自分の車両と駐車場の説明を求められる場合もあります。 </br></br>また、このオプションは、グローバル設定を **カーブサイドピックアップの有効化** が **配信方法** 対象 **店内ピックアップ** | グローバル | いいえ |
| **[!UICONTROL Curbside Instructions]**</br>`Extension Attribute: curbside_instructions` | 顧客に配信されるカスタマイズ可能なメッセージ [!UICONTROL Order Ready For Pickup in Store] 電子メール通知。 | グローバル | いいえ |
| **[!UICONTROL Estimated Pickup Lead Time]**</br>`Extension Attribute: pickup_lead_time` | 注文を受け取り、ピックアップし、ピックアップの準備が整うまでに必要な時間（分）。 </br></br>この情報は、Web サイト上の顧客に対する注文受け取りの推定時間を表示するために使用されます。</br></br> このオプションを設定すると、のグローバル設定が上書きされます。 **推定ピックアップリードタイム** 設定済み **配信方法** 内 **店内ピックアップ** 設定。 | グローバル | いいえ |
| **[!UICONTROL Estimated Pickup Time Label]**</br>`Extension Attribute: pickup_time_label` | 注文の受け取り準備が整うまでの時間（分）を表示するラベル。</br></br> このラベルをカスタマイズする場合、コード%1 を使用して **推定ピックアップリードタイム**.</br></br> このオプションを設定すると、のグローバル設定が上書きされます。 [!UICONTROL Estimated Pickup Time Label] 設定済み [!UICONTROL Delivery Method] 内 [!UICONTROL In-store Pickup]. | グローバル | いいえ |

### **営業時間**

| **フィールド** | **説明** | **範囲** | **必須** |
|------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Location Timezone]**</br>`Extension Attribute: timezone` | マーチャントストアの場所のタイムゾーン。 毎日、開始および終了時間を設定します。</br></br>これらの設定は、推定ピックアップ時間の最適化や、フルフィルメントサービスのレポート作成に使用されます。 | グローバル | はい |
| **[!UICONTROL Opening Hours]**</br>`Internal Attribute: inventory_source_opening_hours_dynamic_rows` | 商人の店舗の場所の営業時間。 </br></br>この情報は、推定ピックアップ時間の最適化や、フルフィルメントサービスのレポート作成に使用できます。 | グローバル | はい |

### チェックインエクスペリエンスインターフェイスオプションの設定



| **フィールド** | **説明** | **範囲** | **必須** |
|---------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Use Parking Spots]**</br>`Extension Attribute: parking_spots_enabled` | 商店の店舗の場所に、カーブ側のピックアップ用の指定駐車場があるかどうかを指定します。 </br></br>有効にすると、利用可能な駐車場を設定できます。 | グローバル | いいえ |
| **[!UICONTROL Is Parking Spot a Mandatory Field?]**</br>`Extension Attribute: parking_spot_mandatory` | 買い物中の顧客に駐車場の識別が必要かどうかを指定します。</br></br>有効にすると、顧客は到着時に駐車場を指定するよう求められます。 無効にした場合、顧客はこの入力をスキップできます。 | グローバル | いいえ |
| **[!UICONTROL Parking Spots List]**</br> `Internal Attribute: inventory_source_parking_spot_dynamic_rows` | カーブサイドピックアップのために、この商店の場所で利用可能な駐車場。 提供されたインターフェイスを使用して、各スポットに名前を付けます。</br></br> すべての駐車場に名前を付ける必要はありません。カーブサイド用に指定されたスポットだけを指定します。 例えば、駐車場の行 A～G を利用できますが、行 A の最初の 8 つのスポットのみがカーブサイドピックアップ用に指定されます。 このシナリオでは、8 つのスポットを定義できます。例：A1、A2、A3 など。 | グローバル | いいえ |
| **[!UICONTROL Allow "Other" Parking Spot Field]**</br>`Extension Attribute: custom_parking_spot_enabled` | この設定を有効にすると、チェックイン中に駐車場の説明を行うことができます。 | グローバル | いいえ |
| **[!UICONTROL Use Car Color]**</br>`Extension Attribute: use_car_color` | チェックイン時に、顧客から車両の色のコレクションをサポートするかどうかを指定します。 </br></br> 選択可能な項目 [!UICONTROL Car Color] が管理者で設定されている [チェックインエクスペリエンスのシステム設定](check-in-experience-setup.md). | グローバル | いいえ |
| **[!UICONTROL Is Car Color a Mandatory Field?]**</br>`Extension Attribute: car_color_mandatory` | チェックイン中に、顧客に車両の色を識別する必要があるかどうかを指定します。</br></br>有効にすると、到着時に車両の色を指定するように求められます。 無効にした場合、顧客はこの入力をスキップできます。 | グローバル | いいえ |
| **[!UICONTROL Use Car Make]** </br>`Extension Attribute: use_car_make` | チェックイン中に、顧客からの車両メーカーのコレクションをサポートするかどうかを指定します。</br></br> 選択可能な項目 [!UICONTROL Car Make] が管理者で設定されている [チェックインエクスペリエンスのシステム設定](check-in-experience-setup.md). | グローバル | いいえ |
| **[!UICONTROL Is Car Make a Mandatory Field?]**</br>`Extension Attribute: car_make_mandatory` | チェックイン中に、顧客に対して車両による識別が必要かどうかを指定します。</br></br>有効にすると、顧客は到着時に車両のメーカーを指定するよう求められます。 無効にした場合、顧客はこの入力をスキップできます。 | グローバル | いいえ |
| **[!UICONTROL Use Additional Information]**</br> `Extension Attribute: use_additional_information` | チェックイン時に、顧客からの追加情報の収集をサポートするかどうかを指定します。 | グローバル | いいえ |
| **[!UICONTROL Is Additional Information a Mandatory Field?]**</br>`Extension Attribute: additional_information_mandatory` | チェックイン中に、顧客に追加情報が必要かどうかを指定します。 </br></br>有効にすると、お客様は到着時に追加情報を入力するよう求められます。 無効にした場合、顧客はこの入力をスキップできます。 | グローバル | いいえ |
