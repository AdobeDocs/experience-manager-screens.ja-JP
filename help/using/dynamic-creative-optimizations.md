---
title: データトリガー
description: AEM Screens のデータトリガーについて説明します。
exl-id: 23c4268e-48be-4c84-b5eb-c96152b166f7
TQID: https://experienceleague.adobe.com/oeJ7C6Rt8-Z9sFnEP1S1tn0VW4PuiKkXkeDYaz8Vd4s
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: eb3ad9f8-54a2-45f3-abb1-d3976415a718
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 307
ht-degree: 85%

---

# Dynamic Creative Optimizations {#dynamic-creative}

>[!IMPORTANT]
>このコンテンツは、AEM オンプレミス/AMS （AEM 6.5LTSおよびAEM 6.5）に対して有効です。 AEM as a Cloud Service Screensの内容については、[AEM as a Cloud Service ガイド ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)を参照してください。

>[!NOTE]
>
>このアクティビティの典型的な関係者は、AEM 実装担当者です。

**Dynamic Creative Optimization**（DCO）は、特定の時点での特定の場所における特定のユーザーに固有の状況を反映したデジタルサイネージエクスペリエンスを作成する場合に使用します。

この使用法は、コンテンツのクライアント側フラット化とも呼ばれます。

その理由は、各プレーヤーデバイスまたはエンドポイントがデータセットを使用して、様々な異なる要因に基づいて自動的に再生する最適なコンテンツを決定できるようにするためです。

この機能により、コンテンツのオーサリング時に人が常に介入する必要がなくなります。 また、ネットワークを運用するための総所有コストの削減にも役立ち、より関連性が高く、コンテキストに応じた、より効果的なデジタルエクスペリエンスを実現します。

以下に例を示します。

* お買い得商品の最新の在庫レベルの使用
* 屋外の気温または天気
* 地元のメディア広告キャンペーンの存在
* 顧客が商品を選んで調べるときなどに発生する Web トラフィックやローカルイベント

これらすべての例やあらゆる情報を使用して、より高いレベルのコンテキストとパーソナライゼーションを提供できます。

DCO を含む視覚的マーチャンダイジング戦略を採用すると、ネットワーク閲覧者数を大幅に増やすことができます。

データトリガーには主に次の 2 種類があります。

* **ローカルデータトリガー**：デバイス上でローカルに発生するデータトリガーです。 例えば、画面をタッチすると、センサーが作動し、ローカルデータアセットまたはチャネルの切り替えがトリガーされます。
* **リモートデータトリガー**：Web サービス API から返された値に基づいて、チャネルまたはアセットの切り替えがトリガーされます。
