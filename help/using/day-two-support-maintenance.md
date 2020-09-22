---
title: Day 2 のサポートおよびメンテナンス
seo-title: AEM Screens の Day 2 のサポートおよびメンテナンス
description: ここでは、Day 2 のサポートおよびメンテナンスについて説明します
seo-description: ここでは、Day 2 のサポートおよびメンテナンスについて説明します
translation-type: ht
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: ht
source-wordcount: '155'
ht-degree: 100%

---


# Day 2 のプラットフォームサポートおよびメンテナンス {#day-two-support-maintenance}

AEM Screens では、プロジェクトが機能するために複数のパッケージが必要です。すべての環境で同じバージョンの Adobe Experience Manager を実行する必要があります。

ガイドラインに従って、プロジェクト開発フェーズ Day 2 の「サポートおよびメンテナンス」を実行します。

1. お使いのバージョンの Adobe Experience Manager に対応する、次のパッケージの最新バージョンを実行します。

   * **AEM サービスパック**
   * **Screens 機能パック**
   * **AEM 累積修正パック**

1. 必要な開発用パッケージ（WCM コアコンポーネントなど）やサードパーティ製ツールキット（SAP Hybris など）を特定します。

1. 同じソフトウェアパッケージをローカルの開発環境にインストールします。

1. QA サーバー、ステージサーバー、実稼働サーバーのすべてで同じ設定を使用するように、クライアントに指示します。サーバー設定が一致しないと、デプロイ時およびテスト時に問題が発生します。
