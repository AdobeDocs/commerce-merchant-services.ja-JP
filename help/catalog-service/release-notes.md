---
title: '''[!DNL Catalog Service] リリースノート'''
description: の最新のリリース情報 [!DNL Catalog Service] Adobe Commerce
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
source-git-commit: 72913e0c0b7364e38d37fe1a8279c40a4e849c02
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 2%

---

# [!DNL Catalog Service] リリースノート

{{catalog-service-beta}}

これらのリリースノートでは、の最新バージョンについて説明します [!DNL Catalog Service] およびを含めます。

* ![新規](../assets/new.svg)  — 新機能
* ![修正点](../assets/fix.svg)  — 修正点および改善点
* ![バグ](../assets/bug.svg)  — 既知の問題

## ベータリリース

* ![新規](../assets/new.svg) - `products` および `refineProduct` クエリは次のデータを返します。
   * 定義済み（システム）の製品属性。
   * 動的な製品属性を選択し、役割でフィルターします（製品の表示ページ/製品リストページ）。
   * 製品オプション。
   * 製品画像を使用し、役割 (PDP/PLP) でフィルタリングします。
   * シンプルな製品の特定の価格と、設定可能な製品の価格帯。
   * 顧客グループの価格と価格帯。 顧客グループを持たない買い物客に対して、フォールバックのデフォルト価格が返されます。
   * B2B 顧客固有の価格を使用する製品タイプ。

## 既知の制限事項

* バンドルおよびグループ化された製品はサポートされていません。
* 階層価格はサポートされていません。
* 画像の配列では、最初の画像のみに役割が含まれます。
* バリアントの画像は取得されません。
* 製品またはバリアントがカタログから削除された場合、更新は受け取りません。