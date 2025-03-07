---
title: Day 2 のサポートおよびメンテナンス
description: AEM Screens の Day 2 のサポートとメンテナンスについて説明します
exl-id: 2b5511ff-c8f4-4ea3-8a65-f17f3a1ec39b
source-git-commit: a89aec16bb36ecbde8e417069e9ed852363acd82
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 100%

---

# Day 2 のプラットフォームサポートおよびメンテナンス {#day-two-support-maintenance}

AEM Screens では、プロジェクトが機能するために複数のパッケージが必要です。すべての環境で同じバージョンの Adobe Experience Manager を実行する必要があります。

プロジェクト開発フェーズの Day 2 のサポートとメンテナンスのガイドラインに従います。

1. お使いのバージョンの Adobe Experience Manager に対応する、次のパッケージの最新バージョンを実行します。

   * **AEM サービスパック**
   * **Screens 機能パック**
   * **AEM 累積修正パック**

1. 必要な開発用パッケージ（WCM コアコンポーネントなど）やサードパーティ製ツールキット（SAP Hybris など）を特定します。

1. 同じソフトウェアパッケージをローカルの開発環境にインストールします。

1. QA サーバー、ステージサーバー、実稼動サーバーのすべてで同じ設定を使用するように、クライアントに指示します。サーバー設定が一致しないと、デプロイ時およびテスト時に問題が発生します。
