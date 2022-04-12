---
title: 概要
description: Adobe Commerceのライブ検索は、驚くほど高速で、超関連性が高く、直感的な検索エクスペリエンスを提供します。
exl-id: aca0ef19-ead1-4c79-90c3-db5ec48cb3c1
source-git-commit: c71771dde0faa13d4fd4b9b58eefbd6e15c86fd1
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# [!DNL Live Search]

[!DNL Live Search] は、標準のAdobe Commerce検索機能に代わる、Adobe Commerce用のスタンドアロンパッケージのセットです。 この [!DNL Live Search] モジュールは、サーバーのコマンドラインからインストールされ、Adobe Commerceインストールに as a として接続します。 [サービス](../landing/saas.md). プロセスが完了したら、 [!DNL Live Search] が *マーケティング* 下のメニュー *SEO と検索* 内 [!DNL Commerce] *管理者*.

アーキテクチャのAdobe Commerce側には、検索のホストが含まれます *管理者*、カタログデータの同期、クエリサービスの実行を行う。 後 [!DNL Live Search] がインストールおよび設定されると、Adobe Commerceは検索およびカタログデータの SaaS サービスとの共有を開始します。 この時点で、管理者ユーザーは、検索ファセット、シノニムおよびマーチャンダイジングルールを設定、カスタマイズおよび管理できます。

![ライブ検索のアーキテクチャ図](assets/architecture-diagram.svg)
