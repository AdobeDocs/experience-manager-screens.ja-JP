---
title: '[!UICONTROL AEM Screens] の環境'
description: AEM Screens プロジェクトの環境の詳細を説明します。
source-git-commit: 3c4b37b3b9f268b500562fa4ce3782b7be1e7d74
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 61%

---


# 環境 {#environments}

クライアントが所有し、使用を想定しているAEM環境を、事前に特定します（以下の両方を行う場合） *開発* および *配置*.

>[!NOTE]
>
>AEM Screensでは、プロジェクトを機能させるために複数のパッケージが必要です。 すべての環境で同じバージョンの Adobe Experience Manager を実行する必要があります。

AEM Screens プロジェクトの環境を設定するには、次のガイドラインに従います。

1. お使いのバージョンの Adobe Experience Manager に対応する、次のパッケージの最新バージョンを実行します。

   * **AEM サービスパック**
   * **Screens 機能パック**
   * **AEM 累積修正パック**

1. 必要な開発用パッケージ（WCM コアコンポーネントなど）やサードパーティ製ツールキット（SAP Hybris など）を特定します。

1. ローカル開発環境に同じソフトウェアパッケージをインストールします。

1. QA サーバー、ステージサーバー、実稼働サーバーのすべてで同じ設定を使用するように、クライアントに指示します。サーバー設定が一致しないと、デプロイおよびテスト時に問題が発生します。
