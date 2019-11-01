---
title: '[!UICONTROL AEM Screens] の環境'
seo-title: '[!UICONTROL AEM Screens] の環境'
description: ここでは、AEM Screens プロジェクトの環境について説明します。
seo-description: ここでは、AEM Screens プロジェクトの環境について重点的に説明します。
translation-type: ht
source-git-commit: 0d91aa653508969cf1f4ccfba23a570e22e6414c

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

1. 同じソフトウェアパッケージをローカルの開発環境にインストールします。

1. QA サーバー、ステージサーバー、実稼働サーバーのすべてで同じ設定を使用するように、クライアントに指示します。サーバー設定が一致しないと、デプロイ時およびテスト時に問題が発生します。
