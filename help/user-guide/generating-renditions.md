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
source-git-commit: a89aec16bb36ecbde8e417069e9ed852363acd82
workflow-type: ht
source-wordcount: '367'
ht-degree: 100%

---

# ビデオレンディション {#video-renditions}

手動および自動のフル HD レンディションを生成できます。次の節では、アセットにレンディションを追加するワークフローについて説明します。

## フル HD レンディションの自動生成 {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>AEM Screens のビデオレンディションがデバイスで最適に再生されない場合は、ハードウェアのベンダーにビデオの仕様を問い合わせてください。これにより、デバイスで最高のパフォーマンスを得ることができます。これは、レンディションを生成するための FFMPEG に適したパラメーターを提供する、独自のカスタムビデオプロファイルを作成する場合に役立ちます。次に、次の手順を使用して、カスタムビデオプロファイルをプロファイルのリストに追加します。
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
1. **引数**のリストへ、フル HD プロファイルを次のように入力します。
   ***`,profile:fullhd-bp,profile:fullhd-hp`***
1. 「**OK**」をクリックします。

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. **DAM Update Asset**&#x200B;画面の左上にある「**保存**」をクリックします。

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. **Assets** に移動し、新しいビデオをアップロードします。ビデオをクリックして、レンディションサイドパネルを開きます。2 つのフル HD ビデオに注目します。

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

1. **レンディション**&#x200B;サイドパネルを開きます。新しいフル HD レンディションに注目してください。

   ![step8_-_open_therenditionssiderail](assets/step8_-_open_therenditionssiderail.png)
