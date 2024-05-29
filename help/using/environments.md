---
title: '[!UICONTROL AEM Screens] の環境'
description: AEM Screens プロジェクトの環境について説明します。
source-git-commit: f7653d8b386c02f510eb7a770cf3cdc22c41a5fb
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 93%

---


# 環境 {#environments}

*開発*&#x200B;と&#x200B;*デプロイメント*&#x200B;の両方に使用することをクライアントが想定している、クライアントに既存の AEM 環境を事前に決定します。

>[!NOTE]
>
>AEM Screens では、プロジェクトが機能するために複数のパッケージが必要です。すべての環境で同じバージョンの Adobe Experience Manager を実行する必要があります。

AEM Screens プロジェクトの環境を設定するには、次のガイドラインに従います。

1. お使いのバージョンの Adobe Experience Manager に対応する、次のパッケージの最新バージョンを実行します。

   * **AEM サービスパック**
   * **Screens 機能パック**
   * **AEM 累積修正パック**

1. 必要な開発用パッケージ（WCM コアコンポーネントなど）やサードパーティ製ツールキット（SAP Hybris など）を特定します。

1. ローカル開発環境に同じソフトウェアパッケージをインストールします。

1. QA サーバー、ステージサーバー、実稼動サーバーのすべてで同じ設定を使用するように、クライアントに指示します。サーバー設定が一致しないと、デプロイ時およびテスト時に問題が発生します。
