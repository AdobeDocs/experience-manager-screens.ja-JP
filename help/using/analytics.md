---
title: AEM Screens での分析
description: Adobe Experience Manager Screens での Adobe Analytics の利用について説明します。
exl-id: cfb47e94-9f65-43f3-b197-07222f3f6424
TQID: https://experienceleague.adobe.com/i7B7E5Kyno2U-ZTxEOPfhrr9W7fqYTWTV5vvcteRicY
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: eb30f47f-d87a-400f-8f78-63ce7979ff56
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 289
ht-degree: 76%

---

# AEM Screens での分析 {#analytics-screens}

>[!IMPORTANT]
>このコンテンツは、AEM オンプレミス/AMS （AEM 6.5LTSおよびAEM 6.5）に対して有効です。 AEM as a Cloud Service Screensの内容については、[AEM as a Cloud Service ガイド ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)を参照してください。

>[!NOTE]
>
>このアクティビティの典型的な関係者は、マーケティング／ビジネスストラテジストです。

AEM Screens では、各プレイヤーデバイスで実行されるすべての追跡可能なイベントをローカルにキャプチャできます。 このデータは、処理用にクラウドにアップロードできるようになるまで、ローカルに保存されます。 すべてのイベントデータに加えて、デバイス ID とタイムスタンプも追加されます。 この機能により、あるプレーヤーのデータを別のプレーヤーと区別できるようになります。 また、必要に応じて、1 日の様々な時間に実行されたデータを個別に評価できます。

このデータを取得した方がよい理由は基本的に 2 つあります。

1 つ目は&#x200B;**フィードバックループと機械学習**&#x200B;に関する理由、もう 1 つは人が使用するための&#x200B;**グラフ、ダッシュボード、レポートの作成**&#x200B;に関する理由です。

フィードバックのループの使用例では、視覚的なレポートやダッシュボードに関心を向ける必要はなく、AEM でコンテンツ変更のために実行できるルールを定義します。 特定期間のすべての Screens プレイヤーイベントデータを消費し処理することで、画像 1 と画像 2 の有効性を評価するルールを定義できます。 AEM は販売データと再生データを組み合わせることで、販売に対する画像 1 の影響の方が大きいと判断し、画像 1 を使用するようすべてのプレイヤーに自動的に指示することができます。

Analyticsを使用する2つ目のユースケースは、レポートとダッシュボードを介して、再生イベントと使用状況データを人間が使用するために処理することです。
このデータを使用して、インタラクティブなエクスペリエンスのヒートマップを作成し、アプリケーション内で優先ジャーニーマップを決定できます。また、消費者がアプリケーションを操作する回数を視覚的に把握できるダッシュボードを作成することもできます。
