---
title: ビデオレンディション
seo-title: ビデオレンディション
description: このページに従って、スクリーンプロジェクトでのフル HD レンディションの生成について学びます。
seo-description: このページに従って、スクリーンプロジェクトでのフル HD レンディションの生成について学びます。
uuid: 0a3b009e-8a97-4396-ad47-97077fe26cde
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 40a182fd-7772-4ef7-b4fd-29ef99390b4a
translation-type: tm+mt
source-git-commit: 209a9a833957d9a8bb7c7ec70ff421514f5b974c

---


# ビデオレンディション {#video-renditions}

手動および自動でフル HD レンディションを生成できます。ここでは、アセットにレンディションを追加するワークフローを説明します。

## フル HD レンディションの自動生成  {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>デバイスで AEM Screens ビデオレンディションが自動的に再生されない場合は、ビデオの仕様についてハードウェアベンダーにお問い合わせください。これは、デバイスで最高のパフォーマンスを得るのに役立ち、これにより、FFMPEG でレンディションを生成するための適切なパラメーターを提供する独自のカスタムビデオプロファイルを作成できます。続いて、次の手順でプロファイルのリストにカスタムビデオプロファイルを追加します。
>
>また、チャネルで再生されているビデオをデバッグおよびトラブルシューティングする方法については、[ビデオのトラブルシューティング](troubleshoot-videos.md)を参照してください。

フル HD レンディションを自動的に生成するには、次の手順に従います。

1. Adobe Experience Manager リンク（左上）を選択し、ツールを選択するためのハンマーアイコンをクリックして、「**ワークフロー**」を選択します。

   Click **Models** to enter the workflow models management.

   ![screen_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. Select the **DAM Update Asset** model and click Edit from the action bar to open the **DAM Update Asset** window.

   ![step5_edit_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. **FFmpeg トランスコーディング**&#x200B;のステップをダブルクリックします。

   ![screen_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. 「**プロセス**」タブを選択し、プロセスの引数を編集します。Enter the full HD profiles to the list in **Arguments** as: ***,profile:fullhd-bp,profile:fullhd-hp*** and click **OK**.

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. **DAM アセットの更新**&#x200B;画面の左上にある「**保存**」をクリックします。

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. **Assets** に移動し、新しいビデオをアップロードします。ビデオをクリックし、レンディションサイドレールを開くと、2つのフルHDビデオが表示されます。

   ![step10_-_open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. Open **Renditions** from the side rail.

   ![step11_-_open_therenditionssiderail](assets/step11_-_open_therenditionssiderail.png)

1. 2 つの新しいフル HD レンディションが表示されます。

   ![step12_-_2_new_renditionsareadedtothevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## フル HD レンディションの手動生成 {#manually-generating-full-hd-renditions}

フル HD レンディションを手動で生成するには、次の手順に従います。

1. Adobe Experience Manager リンク（左上）を選択し、ツールを選択するためのハンマーアイコンをクリックして、「**ワークフロー**」を選択します。

   Click **Models** to enter the workflow models management.

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. Select the **Screens Update Asset** model, and click the **Start Workflow** to open the **Run Workflow** dialog box.

   ![手順5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. Select the desired video in the **Payload** and click **Run**.

   ![step6_-_select_thedesiredvideo](assets/step6_-_select_thedesiredvideo.png)

1. **Assets** に移動し、アセットまでドリルダウンしてクリックします。

   ![step7-_open_thevideoasset](assets/step7_-_open_thevideoasset.png)

1. **レンディション**&#x200B;サイドレールを開くと、新しいフル HD レンディションが表示されます。

   ![step8_-_open_therenditionssiderail](assets/step8_-_open_therenditionssiderail.png)

