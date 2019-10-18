---
title: '[!UICONTROL AEM Screensの環境]'
seo-title: '[!UICONTROL AEM Screensの環境]'
description: このページでは、AEM Screensプロジェクトの環境について説明します。
seo-description: このページでは、AEM Screensプロジェクトの環境について説明します。
translation-type: tm+mt
source-git-commit: 0d91aa653508969cf1f4ccfba23a570e22e6414c

---


# 環境 {#environments}

開発とデプロイの両方で、クライアントが使用するAEM環境と使用する予定のAEM環境を事前に *決定* し *ます*。

>[!NOTE]
>
>AEM Screensでは、プロジェクトが機能するために複数のパッケージが必要です。 すべての環境で同じバージョンのAdobe Experience Managerを実行する必要があります。

AEM Screensプロジェクトの環境を設定するには、次のガイドラインに従います。

1. お使いのバージョンのAdobe Experience Manager用に、次のパッケージの最新バージョンを実行します。

   * **AEM Service Pack**
   * **画面機能パック**
   * **AEM Cumulative Fix Pack**

1. 必要な開発パッケージ（WCM coreコンポーネントなど）やサードパーティのツールキット（SAP Hybrisなど）を特定します。

1. ローカル開発環境に同じソフトウェアパッケージをインストールします。

1. すべてのQA、Stage、実稼働サーバーで同じ設定を採用するようにクライアントに指示します。 サーバー設定が一致しない場合は、展開およびテスト時に問題が発生します。
