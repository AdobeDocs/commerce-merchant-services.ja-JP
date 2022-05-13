---
title: ライブ検索ガイドの概要
description: Adobe Commerceのライブ検索は、驚くほど高速で、超関連性が高く、直感的な検索エクスペリエンスを提供します。
exl-id: 11e2ed97-ce80-4826-b914-71688dd29e4b
source-git-commit: 2676c363182d0b7cb02d15d1093066b1ad4e7b87
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---

# ライブ検索ガイドの概要

[!DNL Live Search] Adobe Commerceからは、Adobe Commerceでの迅速で超関連性の高い直感的な検索エクスペリエンスを、追加料金なしで提供します。 [!DNL Live Search] を使用 [Adobe Sensei](https://www.adobe.com/sensei.html) は、人工知能と機械学習アルゴリズムを使用して、集計された訪問者データを深く分析します。 このデータをAdobe Commerceカタログと組み合わせると、魅力的で関連性が高く、パーソナライズされたショッピングエクスペリエンスが得られます。 スピード、関連性、使いやすさに重点を置いて [!DNL Live Search] 買い物客と商人の両方にとって、大きな変革となる。

ライブ検索には、管理者向けの次の 3 つの領域があります。

* ストアフロント：CSS スタイルを使用した [!DNL storefront popover].
* 管理者：この領域を使用して、設定と設定にアクセスします。
* コマンドラインインターフェイス：このツールを使用して、インストールおよびバックエンドの設定タスクを実行します。

## その他のドキュメント

| ガイド | 説明 |
|--- |--- |
| Adobe Commerce 2.4 ユーザーガイド | Adobe CommerceとMagento Open Sourceの両方に関するマーチャント中心のドキュメント |
| Adobe Commerce 2.4 開発者ガイド | Adobe CommerceまたはMagento Open Sourceの構築とカスタマイズに使用する開発者向けドキュメント |

## サポート

このガイドに記載されていない情報や質問がある場合は、次のリソースを使用してください。

[ヘルプセンター](https://support.magento.com/hc/en-us)  — ライブ検索に関するトラブルシューティング記事を参照してください。
[サポートチケット](https://support.magento.com/hc/en-us/articles/360000913794#submit-ticket)  — 追加のヘルプを受け取るには、チケットを送信します。

サポートチケットを送信する前に、コマンドラインから次のコマンドを実行して、現在インストールされているライブ検索のバージョンを確認します。

```bash
composer show magento/module-live-search | grep version
```
