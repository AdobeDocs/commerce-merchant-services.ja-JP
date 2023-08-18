---
title: 受け渡し要件を保存
description: のプロビジョニングとオンボーディングの要件 [!DNL Store Fulfillment solution].
role: Leader, Admin, Developer
level: Intermediate
feature: Shipping/Delivery, Install
exl-id: f9e05049-5904-4f6c-b45d-9f81fbc76b69
source-git-commit: 78b09113e72382053b01d6016276bae3aa545fa3
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# Adobe Commerceの達成要件の保存

以下の節では、Adobe Commerceの Store Fulfilment ソリューションをインストールして有効にするための技術要件とビジネス要件について説明します。

## プラットフォームとソフトウェアのバージョンの要件

The [!DNL Store Fulfillment] ソリューションは、次のプラットフォームでAdobe Commerceのお客様が利用できます。

- Adobe Commerce on cloud infrastructure (ECE)
- Adobe Commerceオンプレミス (EE)

インストールまたはアップグレードを行う前に、リリースノートとAdobe Commerceの必要システム構成を確認して、インストールまたはアップグレードの要件に影響を与える可能性のあるバージョンの互換性、更新、変更に関する最新情報を入手してください。

- [フルフィルメントリリースノートを保存](release-notes.md)

- [Adobe Commerceリリースノート](https://experienceleague.adobe.com/docs/commerce-operations/release/versions.html) （内） *Adobe Commerceリリース情報*.

- [Adobe Commerceの必要システム構成](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html) （内） *Adobe Commerce Installation Guide*.


## Store Assist アプリの要件

店舗の受け取り注文を管理するエンドツーエンドのプロセスは、モバイルデバイスにインストールされた Store Assist アプリを通じて管理されます。 これらのデバイス（小売業者または店舗従業員が個人用スマートフォンを使用して提供）は、次の要件を満たす必要があります。

**オペレーティングシステムの最小要件**

- Android 6
- iOS 12

**最小ハードウェア要件**

- 1 GB RAM
- 600 MB の空きディスク容量

## ビジネス要件

ストアフルフィルメントソリューションを実装するには、お客様のビジネスが次の最小基準を満たしている必要があります。

- 米国を拠点とする企業のみ

- B2C（消費者向け）小売業者、消費者パッケージ商品 (CPG) 消費者に直接販売する製造業者 (D2C)、または消費者や中小企業に直接販売する販売業者

- 少なくとも 1 つの物理ストアまたは倉庫

- Inventory management for Adobe Commerce(MSI) で製品インベントリを管理

- マーチャント在庫のシンジケート機能

- Wi-Fi の可用性をストアフルフィルメントソリューションをサポートするすべての場所に保存する：最低 3 Mbps のインターネット速度

- 店舗および倉庫関連者は、個人または商人が提供するiOSまたは Android モバイルデバイスに、勤務中にアクセスできます

- Store Fulfilment ソリューションを使用して管理される製品には、SKU または UPC 製品コードを含む製品属性が必要です
