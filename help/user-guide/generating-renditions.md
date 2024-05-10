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
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 17%

---

# ビデオレンディション {#video-renditions}

手動および自動のフル HD レンディションを生成できます。 次の節では、アセットにレンディションを追加するワークフローについて説明します。

## フル HD レンディションの自動生成 {#automatically-generating-full-hd-renditions}

>[!NOTE]
>
>AEM Screensのビデオレンディションがデバイスで最適に再生されない場合は、ハードウェアのベンダーにビデオの仕様を問い合わせてください。 これにより、デバイスで最高のパフォーマンスを得ることができます。 これは、レンディションを生成するための FFMPEG に適したパラメーターを提供する独自のカスタムビデオプロファイルを作成する場合に役立ちます。 次に、次の手順を使用して、カスタムビデオプロファイルをプロファイルのリストに追加します。
>
>また、を参照してください。 [トラブルシューティングビデオ](troubleshoot-videos.md) チャネルで再生されるビデオをデバッグおよびトラブルシューティングする。

フル HD レンディションを自動的に生成するには、次の手順に従います。

1. Adobe Experience Manager リンク（左上）をクリックし、ハンマーアイコンをクリックして、 **ワークフロー**.

   クリック **モデル**.

   ![screen_shot_2018-02-01at123407pm](assets/screen_shot_2018-02-01at123407pm.png)

1. ワークフローモデル管理で、 **DAM アセットの更新** モデル化してクリック **編集** アクションバーから。

   ![step5_-_edit_thedamupdateassetmodel](assets/step5_-_edit_thedamupdateassetmodel.png)

1. が含まれる **DAM アセットの更新** ウィンドウで、 **FFmpeg トランスコーディング** ステップ。

   ![screen_shot_2018-02-01at124454pm](assets/screen_shot_2018-02-01at124454pm.png)

1. 「」をクリックします **プロセス** タブ。
1. で、フル HD プロファイルのリストへの入力 **引数** を次のように設定します。
   ***`,profile:fullhd-bp,profile:fullhd-hp`***
1. 「**OK**」をクリックします。

   ![screen_shot_2018-02-02at103340am](assets/screen_shot_2018-02-02at103340am.png)

1. クリック **保存** の左上に **DAM アセットの更新** 画面。

   ![screen_shot_2018-02-02at101830am](assets/screen_shot_2018-02-02at101830am.png)

1. **Assets** に移動し、新しいビデオをアップロードします。ビデオをクリックして、レンディション サイドパネルを開きます。 2 つのフル HD ビデオに注目してください。

   ![step10_-_open_thevideoasset](assets/step10_-_open_thevideoasset.png)

1. サイドレールから「**レンディション**」を開きます。

   ![step11_-_open_therenditionssiderail](assets/step11_-_open_therenditionssiderail.png)

1. 2 つの新しいフル HD レンディションがあります。

   ![step12_-_2_new_renditionsareaddedtothevideo](assets/step12_-_2_new_renditionsareaddedtothevideo.png)

## フル HD レンディションの手動生成 {#manually-generating-full-hd-renditions}

フル HD レンディションを手動で生成するには、次の手順に従います。

1. Adobe Experience Manager リンク（左上）をクリックし、ハンマーアイコンをクリックして、ツールをクリックし、 **ワークフロー**.

   クリック **モデル**.

   ![screen_shot_2018-02-01at123407pm-1](assets/screen_shot_2018-02-01at123407pm-1.png)

1. ワークフローモデル管理で、 **Screens アセットの更新** モデルを作成し、 **ワークフローを開始** を開きます **ワークフローを実行** ダイアログが表示されます。

   ![step5_-_start_a_newscreensupdateassetworkflow](assets/step5_-_start_a_newscreensupdateassetworkflow.png)

1. 目的のビデオをクリックします。 **ペイロード** をクリックして、 **実行**.

   ![step6_-_select_thedesiredvideo](assets/step6_-_select_thedesiredvideo.png)

1. **Assets** に移動し、アセットまでドリルダウンしてクリックします。

   ![step7_-_open_thevideoasset](assets/step7_-_open_thevideoasset.png)

1. を開きます **レンディション** サイドレール。 新しいフル HD レンディションに注目してください。

   ![step8_-_open_therenditionssiderail](assets/step8_-_open_therenditionssiderail.png)
