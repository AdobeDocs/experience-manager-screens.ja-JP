---
title: ビデオレンディション
description: AEM Screens プロジェクトのフル HD レンディションの生成について説明します。
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 752c74d7-5d6d-4363-97ef-b96e97d2f6b1
TQID: https://experienceleague.adobe.com/4xxCtO5lD71kiS-dSbTjTgycZDiWkQlHPdJOCVDrv38
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2:
  - id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 424
ht-degree: 89%

---

# ビデオレンディション {#video-renditions}

>[!IMPORTANT]
>このコンテンツは、AEM オンプレミス/AMS （AEM 6.5LTSおよびAEM 6.5）に対して有効です。 AEM as a Cloud Service Screensの内容については、[AEM as a Cloud Service ガイド &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)を参照してください。

手動および自動のフル HD レンディションを生成できます。 次の節では、アセットにレンディションを追加するワークフローについて説明します。

## フル HD レンディションの自動生成 {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>AEM Screens のビデオレンディションがデバイスで最適に再生されない場合は、ハードウェアのベンダーにビデオの仕様を問い合わせてください。 これにより、デバイスで最高のパフォーマンスを得ることができます。 これは、レンディションを生成するための FFMPEG に適したパラメーターを提供する、独自のカスタムビデオプロファイルを作成する場合に役立ちます。 次に、次の手順を使用して、カスタムビデオプロファイルをプロファイルのリストに追加します。
>
>また、チャネルで再生されるビデオをデバッグおよびトラブルシューティングするには、[ビデオのトラブルシューティング](troubleshoot-videos.md)を参照してください。

フル HD レンディションを自動で生成するには、次の手順に従います。

1. Adobe Experience Manager リンク（左上）をクリックし、ハンマーアイコンをクリックすると、**ワークフロー**&#x200B;がクリックできます。

   **モデル**&#x200B;をクリックします。

   ![screen_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. ワークフローモデル管理で、**DAM Update Asset** モデルをクリックし、アクションバーから「**編集**」をクリックします。

   ![step5_-_edit_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. **DAM Update Asset** ウィンドウで、**FFmpeg でのトランスコード**&#x200B;ステップをダブルクリックします。

   ![screen_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. 「**プロセス**」タブをクリックします。
1. **引数**&#x200B;のリストへ、フル HD プロファイルを次のように入力します。
   ***`,profile:fullhd-bp,profile:fullhd-hp`***
1. 「**OK**」をクリックします。

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. **DAM Update Asset**&#x200B;画面の左上にある「**保存**」をクリックします。

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. **Assets** に移動し、新しいビデオをアップロードします。 ビデオをクリックして、レンディションサイドパネルを開きます。 2 つのフル HD ビデオに注目します。

   ![step10_-_open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. サイドレールから「**レンディション**」を開きます。

   ![step11_-_open_therenditionssiderail](assets/step11_-_open_therenditionssiderail.png)

1. 2 つの新しいフル HD レンディションが表示されます。

   ![step12_-_2_new_renditionsareaddedtothevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## フル HD レンディションの手動生成 {#manually-generating-full-hd-renditions}

フル HD レンディションを手動で生成するには、次の手順に従います。

1. Adobe Experience Manager リンク（左上）をクリックし、ハンマーアイコンをクリックするとツールをクリックできるようになるので、次に「**ワークフロー**」をクリックします。

   **モデル**&#x200B;をクリックします。

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. ワークフローモデル管理で、**スクリーン更新アセット**&#x200B;モデルをクリックし、**ワークフローを開始**&#x200B;をクリックして&#x200B;**ワークフローを実行**&#x200B;ダイアログボックスを開きます。

   ![step5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. 「**ペイロード**」で目的のビデオをクリックし、「**実行**」をクリックします。

   ![step6_-_select_thedesiredvideo](assets/step6_-_select_thedesiredvideo.png)

1. **Assets** に移動し、アセットまでドリルダウンしてクリックします。

   ![step7_-_open_thevideoasset](assets/step7_-_open_thevideoasset.png)

1. **レンディション**&#x200B;サイドパネルを開きます。 新しいフル HD レンディションに注目してください。

   ![step8_-_open_therenditionssiderail](assets/step8_-_open_therenditionssiderail.png)

