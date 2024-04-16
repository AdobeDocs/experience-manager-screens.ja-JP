---
title: 画像再生時間
description: AEM Screensでの画像再生時間について説明します。
contentOwner: jsyal
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 53%

---


# 画像再生時間 {#image-playback-duration}

## 概要 {#overview}

シーケンスチャネルを作成してそのチャネルに画像を追加すると、デフォルトでは、すべての画像の再生時間がチャネルレベル設定で定義されたものになります。 それでも、個々の画像でこのデフォルトを上書きし、異なる再生時間にすることはできます。それには、特定の画像コンポーネントの再生時間を編集します。

### 前提条件 {#prerequisites}

この機能を実装する前に、この機能の実装を開始するための前提条件としてプロジェクトが設定されていることを確認してください。 例：

1. AEM Screens プロジェクト（この例では **ChannelLevelPlayback**）を作成する
1. **チャネル**&#x200B;フォルダーの下に **PlaybackChannel** というシーケンスチャネルを作成する
1. **PlaybackChannel** にコンテンツを追加する

## チャネルレベル画像再生時間の割り当ての編集 {#editing-channel-level-image-playback-duration-assignment}

以下の節では、AEM Screens チャネルのコンテンツの再生時間を編集する方法について説明します。

### チャネル内の画像の再生時間を更新する方法 {#updating-the-playback-duration-for-images-in-a-channel}

チャネルレベルの画像再生時間の割り当てを更新するには、以下の手順に従います。

1. シーケンスチャネル **PlaybackChannel** に移動します。

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. クリック **編集** アクションバーから。

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. チャネルエディターで画像を 2 つ以上追加します（次の図を参照）。

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. チャネル内のすべての画像をクリックし、左上のレンチ アイコンをクリックします（下図を参照）。 チャネルレベルの設定ダイアログボックスが開きます。

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. **ページ**&#x200B;ダイアログボックスが開きます。

   >[!NOTE]
   >
   >デフォルトでは、チャネル内の画像は再生時間が 8 秒に設定されています。

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   を編集する **期間** 8000 （ミリ秒）～3000 （ミリ秒）、つまり 3 秒です。 右上のチェックマークをクリックします **ページ** ダイアログボックスが開き、変更を保存できます。

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### 結果の表示 {#viewing-the-result}

チャネル再生時間（この例では 3 つの画像すべて）を更新すると、画像が 8 秒（デフォルト値）ではなく 3 秒間再生されることに注意してください。

![channel_preview](assets/channel_preview.gif)

