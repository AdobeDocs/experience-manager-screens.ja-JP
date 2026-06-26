---
title: デバイスの仕様
description: AEM Screens に関連するデバイス仕様の詳細を説明します。
exl-id: c2e521b3-89f5-4537-a751-0bfa031286c4
TQID: https://experienceleague.adobe.com/nRZXWarHxFk1wgwR5YLLNcxx3OKs-fWKq1U9uB7yeBw
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 258
ht-degree: 82%

---

# デバイス設定 {#device-configurations}

>[!IMPORTANT]
>このコンテンツは、AEM オンプレミス/AMS （AEM 6.5LTSおよびAEM 6.5）に対して有効です。 AEM as a Cloud Service Screensの内容については、[AEM as a Cloud Service ガイド &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)を参照してください。

>[!NOTE]
>
>このアクティビティの典型的な関係者は、オーディオビデオインテグレーターです。

*Day 0* で収集された情報に基づいて、開発を開始する前に以下の情報を確認します。

* 使用される画面の向き、サイズ、解像度

* 場所ごとに設置される画面の数と設定

* ディスプレイデバイスにインストールする必要があるソフトウェアとオペレーティングシステム

* 画面と AEM サーバーを同期するためにプレーヤーにインターネット接続が必要かどうか

* プレーヤー上のコンテンツが更新されるタイミング

* ビデオを実行する場合は、コンテンツが正しく表示されるように、デバイスの仕様を理解しておく。

* 上記の環境上の検討事項に基づいて判断すると、半導体ストレージとハードディスクストレージのどちらが適しているか

* 必要なストレージ容量とストレージパフォーマンスの要件 以下にいくつかの例を示します。
   * ストレージに関する特別な検討事項（複数のドライブ、ブートデバイスか大容量ストレージかなど）
   * 必要な RAM 容量


>[!NOTE]
>
>また、選択したハードウェアの仕様を検証して、開発対象のアプリケーションを確実にサポートできるようにすることも重要です。 例えば、アプリケーションが同時に 5 つの高解像度ビデオを実行することを目的としている場合、ハードウェアはそれに対応していますか？

