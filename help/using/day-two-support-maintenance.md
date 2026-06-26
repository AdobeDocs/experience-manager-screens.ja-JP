---
title: Day 2 のサポートおよびメンテナンス
description: AEM Screens の Day 2 のサポートとメンテナンスについて説明します
exl-id: 2b5511ff-c8f4-4ea3-8a65-f17f3a1ec39b
TQID: https://experienceleague.adobe.com/IMuRCxE7v8DyK-T4Q3lehhclfgGtu0VIHyIsODOpEzA
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 186
ht-degree: 75%

---

# Day 2 のプラットフォームサポートおよびメンテナンス {#day-two-support-maintenance}

>[!IMPORTANT]
>このコンテンツは、AEM オンプレミス/AMS （AEM 6.5LTSおよびAEM 6.5）に対して有効です。 AEM as a Cloud Service Screensの内容については、[AEM as a Cloud Service ガイド ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)を参照してください。

AEM Screens では、プロジェクトが機能するために複数のパッケージが必要です。 すべての環境で同じバージョンの Adobe Experience Manager を実行する必要があります。

プロジェクト開発フェーズの Day 2 のサポートとメンテナンスのガイドラインに従います。

1. お使いのバージョンの Adobe Experience Manager に対応する、次のパッケージの最新バージョンを実行します。

   * **AEM サービスパック**
   * **Screens 機能パック**
   * **AEM 累積修正パック**

1. 必要な開発用パッケージ（WCM コアコンポーネントなど）やサードパーティ製ツールキット（SAP Hybris など）を特定します。

1. 同じソフトウェアパッケージをローカルの開発環境にインストールします。

1. QA サーバー、ステージサーバー、実稼動サーバーのすべてで同じ設定を使用するように、クライアントに指示します。 サーバー設定が一致しないと、デプロイ時およびテスト時に問題が発生します。

