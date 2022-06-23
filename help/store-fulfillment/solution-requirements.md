---
title: 達成要件を保存
description: のプロビジョニングとオンボーディングの要件 [!DNL Store Fulfillment solution].
role: User, Admin
level: Intermediate
exl-id: f9e05049-5904-4f6c-b45d-9f81fbc76b69
source-git-commit: 421c90f4c8bd687216cd48c72f30301a32115522
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 2%

---

# Adobe Commerceの達成要件を保存

Adobe Commerceの Store Fulfilment ソリューションをインストールして有効にするには、次の技術要件とビジネス要件を満たす必要があります。

## プラットフォームとソフトウェアのバージョン要件

この [!DNL Store Fulfillment] ソリューションは、次のプラットフォームでAdobe Commerceのお客様が利用できます。

- Adobe Commerce on cloud infrastructure (ECE)
- Adobe Commerceオンプレミス (EE)

Store Fulfilment ソリューションは、次のソフトウェアバージョンと互換性があります。

**ソフトウェアの互換性**

| **ソフトウェア** | **最小バージョン** | **最大バージョン** |
|----------------|---------------------|---------------------|
| Adobe Commerce | 2.4.0 | 2.4.4 |
| コンポーザー | 1.x | 2.x |
| MariaDB | 10.2 | 10.4 |
| MySQL | 5.7 | 8.0 |
| PHP | 7.4 | 8.1 |

詳細な要件については、 Adobe Commerceを確認してください [必要システム構成](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) （開発者向けドキュメント）を参照してください。

## Store Assist アプリの要件

店舗の受け取り注文を管理するエンドツーエンドのプロセスは、モバイルデバイスにインストールされた Store Assist アプリを通じて管理されます。 これらのデバイス（小売業者または店舗従業員が個人用スマートフォンを使用して提供）は、次の要件を満たす必要があります。

**オペレーティングシステムの最小要件**

- Android 6
- iOS 12

**最小ハードウェア要件**

- 1 GB RAM
- 600 MB の空きディスク容量

## ビジネス要件

店舗フルフィルメントソリューションを実装するには、お客様のビジネスが次の最低基準を満たしている必要があります。

- 米国を拠点とする企業のみ

- B2C 小売業者、CPG メーカーが D2C を販売、または D2C を販売する販売業者や中小企業に販売する販売業者

- 少なくとも 1 つの物理ストアまたは倉庫

- Inventory management for Adobe Commerce(MSI) で製品インベントリを管理

- マーチャント在庫のシンジケート機能

- Wi-Fi の可用性を、ストアフルフィルメントソリューションをサポートするすべての場所に保存します。3 Mbps の最小インターネット速度

- 店舗および倉庫関連者は、個人または商人が提供するiOSまたは Android モバイルデバイスの勤務中にアクセスできます

- Store Fulfilment ソリューションを使用して管理される製品には、SKU または UPC 製品コードを含む製品属性が必要です
