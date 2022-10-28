---
title: 製品のRecommendations Administrator Development
description: 製品のRecommendationsアーキテクチャと開発機能の概要です。
source-git-commit: 81ab2e22b0ec81e97d27ee135c88b50731a3986d
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# 製品のRecommendations Administrator Development

製品Recommendationsは、コンバージョンの増加、売上高の増加、買い物客のエンゲージメントの促進に使用できる強力なマーケティングツールです。 製品Recommendationsは、「この製品を閲覧したお客様も閲覧した」、「この製品を購入したお客様も購入した」、「お勧め」などの単位でストアフロントに表示されます。 Adobe Commerce Product Recommendationsの主な機能は [Adobe Sensei](https://www.adobe.com/sensei.html)：人工知能と機械学習アルゴリズムを使用して、集計した買い物客データを深く分析します。 このデータをコマースカタログと組み合わせると、買い物客のエクスペリエンスを非常に魅力的で関連性が高く、パーソナライズされたデータにすることができます。

>[!NOTE]
>
>ストアフロントがPWA Studioを使用して実装されている場合は、 [PWA文書](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). React や Vue JS などのカスタムフロントエンドテクノロジーを使用する場合は、ユーザーガイドを参照して、製品Recommendationsを [頭のない](headless.md) 環境。

## アーキテクチャの概要

高レベルでは、Commerce Product Recommendationsは SaaS としてデプロイされます。 コマース側には、イベントコレクターとレコメンデーションのレイアウトテンプレートを含むストアフロントと、Data Services、SaaS 書き出しモジュール、Admin UI を含むバックエンドが含まれています。 Adobe Senseiインテリジェンスサービスは、SaaS 側で利用されます。

![製品レコメンデーションのアーキテクチャ図](assets/arch-diag-sensei.svg)

レコメンデーションモジュールがインストールされ、設定されると、ストアフロントで行動データの収集が開始されます。 Adobe Senseiは、この行動データをカタログデータと共に処理し、recommendations サービスで利用される製品の関連付けを計算します。 この時点で、商人は、製品レコメンデーションユニットを作成、管理、ストアフロントへのデプロイを、管理 UI から直接おこなうことができます。

## データのタイプ

製品Recommendationsには次のデータが必要です。

- **行動**  — サイトでの買い物客のエンゲージメントからのデータ（製品表示、買い物かごに追加された項目、購入など）。 コマースおよびAdobe Senseiは、個人を特定できる情報を収集しません。

- **カタログ**  — 製品メタデータ（名前、価格、在庫など）。

をインストールする際に、 `magento/product-recommendations` モジュールの場合、Adobe Senseiは行動データとカタログデータを集計し、各レコメンデーションタイプに対して製品Recommendationsを作成します。 次に、Product Recommendationsサービスによって、これらのレコメンデーションがストアフロントにデプロイされます。

## 次の手順

次のトピックを読んで、製品のRecommendationsの基本を学んでください。

- [製品の実装方法Recommendations](implementation-workflow.md)

- [製品Recommendationsのインストールと設定](install-configure.md)

- [製品を作成Recommendations](create.md)
