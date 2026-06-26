---
title: サポート監視
description: AEM Screens のサポート監視のベストプラクティスガイドについて説明します。
exl-id: b9d6f713-e26d-4f56-bedb-2d419a19a05c
TQID: https://experienceleague.adobe.com/uqtkwa1zcJ58tJOxWT0gWkOhAM-C-5zEdcFLjrHa1-Q
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 266
ht-degree: 82%

---

# サポート監視 {#support-monitoring}

>[!IMPORTANT]
>このコンテンツは、AEM オンプレミス/AMS （AEM 6.5LTSおよびAEM 6.5）に対して有効です。 AEM as a Cloud Service Screensの内容については、[AEM as a Cloud Service ガイド ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)を参照してください。

ここでは、デジタルサイネージプロジェクトにおけるデバイスとコンテンツの異常の管理に関するベストプラクティスを紹介します。

「サポートと監視」には次のものがあります。

* **デバイス監視**
* **コンテンツ監視**

## コンテンツ監視 {#content-monitoring}

コンテンツ監視を利用すると、画面に正しく表示されないコンテンツに関する問題のトラブルシューティングを行うことができます。

1. 画面に何も表示されないという問題が発生した場合：

   * *プレビュー*&#x200B;を調べて、チャネルに黒い画面が表示されているかどうかを確認します。
   * ノートパソコンの&#x200B;*ローカル Chrome プレーヤー*（拡張機能）をそのディスプレイに登録し、黒い画面が表示されるか確認してください。
   * 右クリックし、*該当するログ*&#x200B;を調べて確認します。

   また、この問題がローカルプレイヤーで発生せず、デバイスでのみ発生する場合は、次の手順を実行します。

   * そのデバイスで問題が発生する可能性のある&#x200B;*メディアタイプ*（使用中のもの）を調べ、コンテンツがローカルに正常にダウンロードされたかどうかを確認します（Admin UI でチャネルのキャッシュをクリア）。
   * すばやくトラブルシューティングをおこなうため、すべての&#x200B;*デバイスログ*&#x200B;をチケットに含めます。
   * AEM からデバイスの&#x200B;*ログを収集*&#x200B;します。

## デバイス監視 {#device-monitoring}

画面に何も表示されないという問題が発生した物理デバイスの監視に関連するデバイス監視は、次のとおりです。

1. 画面に何も表示されないという問題が発生した場合：

   * *ディスプレイ*&#x200B;の電源が入っているかどうかを確認します。
   * *コンピューター*&#x200B;の電源が入っていて信号が送信されているかどうかを確認します。
   * 右クリックし、*該当するログ*&#x200B;を調べて確認します。

