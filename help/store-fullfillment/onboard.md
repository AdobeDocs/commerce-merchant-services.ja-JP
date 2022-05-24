---
title: 「 」をオンボード[!DNL Store Fulfillment]"
description: コマースインスタンスを [!DNL Store Fulfillment Manager] サービスを使用するには、いくつかのオンボーディング手順を完了します。
role: User, Admin
level: Intermediate
source-git-commit: f3148d575088fff3b4178f3c03e9d45ce461fbe2
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 1%

---


# ウォルマート・テクノロジーズによるオンボード・ストアのフルフィルメント

コマースインスタンスに拡張機能をインストールし、API 接続を設定することで、Onboard Store のフルフィルメントを実行します。 これらの接続を使用すると、コマースインスタンス、在庫管理用のサードパーティシステム、Store Assist アプリ間の通信とデータの同期が可能になります。

オンボーディングが完了したら、コマース管理者からソリューションを設定および管理します

![[!DNL Store Fulfillment Service] 管理ビューの設定](assets/store-fulfillment-admin-home.png)

## オンボーディングの概要

1. Adobe Commerceの Store Fulfilment by Walmart Technologies 拡張機能をインストールします。

1. 管理者から、ソリューションを有効にし、統合の一般的な設定とアクティブな機能を完了し、オンボーディング取得フォームに入力してフルフィルメントサービスに接続します。

1. 配信方法を設定します。

1. ソースを物理ストアとして設定し、カタログで製品を設定します。

1. オンラインでの購入、店頭 (BOPIS) トランザクションに関する顧客のコミュニケーションを管理する電子メールテンプレートを選択および設定します。

1. Store Assist アプリのユーザーとロールを作成します。

1. バックグラウンドプロセスでデータをフルフィルメントサービスに同期するスケジュールを設定します。

## 前提条件

* **コマースアカウント情報** — インストール [!DNL Store Fulfillment by Walmart Technologies] にはが必要です [コマースアカウント](https://docs.magento.com/user-guide/magento/magento-account.html){target=&quot;_blank&quot;}。 に対する所有者または管理者アクセス権を持つアカウント ID と資格情報が必要です [!DNL Adobe Commerce] または [!DNL Magento Open Source] インスタンス。

* の場合 [!DNL Adobe Commerce] クラウドインフラストラクチャプロジェクトでは、ソフトウェアインストーラーは、 [!DNL Commerce] インスタンス：

   * クラウドプロジェクトへのスーパーユーザーアクセス
   * 特定の環境への管理者アクセス
   * An [!DNL Adobe Commerce] または [!DNL Magento Open Source] Composer リポジトリにアクセスする権限を持つアカウント

      詳しくは、 [ユーザーアクセスを管理](https://devdocs.magento.com/cloud/project/user-admin.html).

* **Store Fulfilment by Walmart Technologies ソフトウェアアーカイブ（.zip ファイル）にアクセスして、Adobe Commerceインスタンスに Store Fulfilment ソリューションをインストールします** — お客様のアカウント担当者が、拡張機能のインストールファイルへのアクセス権を提供できます。

* **Composer と[!DNL Commerce CLI]**  — 参照 [一般的な CLI のインストール](https://devdocs.magento.com/extensions/install/){target=&quot;_blank&quot;}」を参照してください。 [!DNL Adobe Commerce] および [!DNL Magento Open Source] プラットフォーム。

* [!DNL Inventory Management] Adobe Commerce andMagento Open Sourceの拡張

   Inventory management拡張機能をAdobe CommerceおよびMagento Open Sourceインスタンスにインストールし、有効にする必要があります。 通常、この拡張機能は、Adobe CommerceおよびMagento Open Source2.3.x 以降にインストールされ、デフォルトで有効になります。 詳しくは、 [Inventory managementのインストール](https://devdocs.magento.com/extensions/inventory-management/) ( Adobe Commerce開発者向けドキュメント )。

## 要件

ストアフルフィルメントソリューションは、Adobe CommerceおよびMagento Open Sourceのお客様が利用できます。 このソリューションをインストール、導入、使用するには、次のシステムおよびビジネス要件を満たす必要があります。

### 必要システム構成

Store Fulfilment by Walmart Technologies 拡張機能は、次のソフトウェアバージョンとの互換性がテストされています。

**ソフトウェアの互換性**

| **ソフトウェア** | **最小バージョン** | **最大バージョン** |
|----------------|---------------------|---------------------|
| Adobe Commerce | 2.4.0 | 2.4.4 |
| コンポーザー | 1.x | 2.x |
| MariaDB | 10.2 | 10.4 |
| MySQL | 5.7 | 8.0 |
| PHP | 7.4 | 8.1 |

詳細な要件については、 Adobe Commerceを確認してください [必要システム構成](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) （開発者向けドキュメント）を参照してください。

### ビジネス要件

店舗フルフィルメントソリューションを実装するには、お客様のビジネスが次の最低基準を満たしている必要があります。

* 米国を拠点とするビジネス

* B2C 小売業者、CPG メーカーが D2C を販売、または D2C を販売しているか、中小企業に販売しているディストリビューター

* 少なくとも 1 つの物理ストアまたは倉庫

* Inventory management for Commerce （旧 MSI）で製品の在庫を管理します

* マーチャント在庫のシンジケート機能

* Wi-Fi の可用性を、ストアフルフィルメントソリューションをサポートするすべての場所に保存

* 店舗および倉庫関連者は、個人または商人が提供するiOSまたは Android モバイルデバイスの勤務中にアクセスできます

* Store Fulfilment ソリューションを使用して管理される製品には、SKU または UPC 製品を含む製品属性が必要です。

### サポートされるプラットフォーム

* Adobe Commerce on Cloud (ECE) :2.4.x
* Adobe Commerceオンプレミス (EE) :2.4.x
* Magento Open Source2.4.x
