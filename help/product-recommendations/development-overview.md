---
title: Product Recommendations管理者向けの開発
description: Product Recommendationsのアーキテクチャと開発機能の概要です。
exl-id: caef5e0c-dd69-4846-8f85-b1c5e1c6a28f
source-git-commit: 4a5c3550b03651279c24de6b6361ffa6dc28776e
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# Product Recommendations管理者向けの開発

Product Recommendationsは、コンバージョンを増やし、売上高を増やし、買い物客のエンゲージメントを促進するために使用できる強力なマーケティングツールです。 商品Recommendationsは、「この商品を見た方も見ていただいた」「この商品を購入されたお客様も買っていただいた」「お勧め」など、お客様の目に触れる形で店頭に表示されます。 Adobe Commerce Product Recommendationsは、人工知能と機械学習アルゴリズムを使用して集計した買い物客データのディープ分析を実行する ](https://www.adobe.com/sensei.html)0}Adobe Sensei} を活用しています。 [このデータをCommerce カタログと組み合わせると、買い物客にとって非常に魅力的で関連性が高く、パーソナライズされたエクスペリエンスが得られます。

>[!NOTE]
>
>ストアフロントがPWA Studioを使用して実装されている場合は、[PWAドキュメント ](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/) を参照してください。 React や Vue JS などのカスタムフロントエンドテクノロジーを使用している場合は、ユーザーガイドを参照して、製品Recommendationsを [ ヘッドレス ](headless.md) 環境に統合する方法を確認してください。 ヘッドレスインスタンスでは、製品レコメンデーションワークスペースを強化するためにイベンティングを実装する必要があります。

## アーキテクチャの概要

大まかに言えば、Commerce Product Recommendationsは SaaS としてデプロイされます。 Commerce側には、イベントコレクターおよび Recommendations レイアウトテンプレートを含むストアフロント、およびデータサービス、SaaS エクスポートモジュール、管理 UI を含むバックエンドが含まれます。 Adobe Senseiのインテリジェンスサービスは、SaaS 側で利用されます。

![Product Recommendations のアーキテクチャ図 ](assets/arch-diag-sensei.svg)

レコメンデーションモジュールがインストールされて設定されると、ストアフロントで行動データの収集が開始されます。 Adobe Senseiは、カタログデータと共にこの行動データを処理し、recommendations サービスで活用される商品の関連付けを計算します。 この時点で、マーチャントは、管理 UI から直接製品レコメンデーションユニットを作成、管理およびストアフロントにデプロイできます。

## 次の手順

製品Recommendationsの基本を学ぶには、次のトピックを参照してください。

- [製品Recommendationsの実装方法](implementation-workflow.md)

- [製品Recommendationsのインストールと設定](install-configure.md)

- [製品Recommendationsを作成](create.md)
