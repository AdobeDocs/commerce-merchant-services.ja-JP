---
title: "[!DNL Manage the Data Export extension]"
description: 「をアップグレードする方法を学ぶ [!DNL Data Export] 不要なデータ書き出しサービスを削除または無効にするための、およびの拡張。」
role: Admin, Developer
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---


# SaaS データ書き出し拡張機能の管理

この [!DNL data export] saaS サービスの拡張機能は、Adobe Commerceと接続されたCommerce サービス間のデータ収集と同期を可能にするモジュールの集まりです。

特定のモジュールは、次のようなAdobe Commerce サービス拡張機能のメタパッケージに含まれています [Live Search](/help/live-search/overview.md), [製品のRecommendations](/help/product-recommendations/overview.md)、および [カタログサービス](/help/catalog-service/overview.md). これらのサービスを使用している場合、データの書き出し拡張機能を有効にするために別のインストールは必要ありません。

## Commerceのデータ書き出し機能を削除または無効にする

インストールされているコマースデータ書き出しモジュールが必要ない場合は、を使用します。 `magento:module:disable` CLI コマンドを使用して無効にします。

例えば、 [Categories API](https://developer.adobe.com/commerce/services/graphql/catalog-service/categories/) は、カテゴリ権限フィードデータを内部的に使用します。 この API を使用していない場合は、カテゴリ権限フィードのデータ書き出しを無効にできます。

```shell script
bin/magento module:disable Magento_CategoryPermissionDataExporter Magento_SaaSCategoryPermissions
```

### 特定のバージョンにモジュールを更新する

インストールされているコマースデータ書き出しモジュールは、Composer を使用して更新できます。 例えば、指定したバージョンにモジュールを更新し、必要な依存関係も更新できます。

1. Commerce アプリケーションサーバーにログインします。

1. コマンドラインから、Composer を使用してモジュールを更新します。

   ```bash
   composer require magento/module-saas-price:103.3.1 --with-all-dependencies
   ```

Commerce インスタンスがクラウドインフラストラクチャにデプロイされている場合は、クラウドプロジェクトディレクトリから拡張機能を更新します。 参照： [拡張機能のアップグレード](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions#upgrade-an-extension) が含まれる _クラウドインフラストラクチャー上のAdobe Commerce ガイド_.




