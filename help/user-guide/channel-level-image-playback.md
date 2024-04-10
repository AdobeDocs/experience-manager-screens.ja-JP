---
title: チャネルレベルの一括画像再生時間
description: AEM Screensで特定の画像コンポーネントの再生時間を編集する方法について説明します。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 95aa761a-1449-4e18-8115-3b151036dc54
source-git-commit: 02929219a064e3b936440431e77e67e0bf511bf6
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 45%

---

# チャネルレベルの一括画像再生時間 {#channel-level-bulk-image-playback-duration}

## 概要 {#overview}

シーケンスチャネルを作成してそのチャネルに画像を追加すると、デフォルトでは、すべての画像にチャネルレベルの設定で定義された再生時間が適用されます。 それでも、個々の画像でこのデフォルトを上書きし、異なる再生時間にすることはできます。それには、特定の画像コンポーネントの再生時間を編集します。

### 前提条件 {#prerequisites}

この機能の実装を開始する前に、この機能の実装を開始するための前提条件としてプロジェクトが設定されていることを確認してください。 例：

1. AEM Screens プロジェクト（例：**ChannelLevelPlayback**）を作成する。

1. **チャネル**&#x200B;フォルダーの下に **PlaybackChannel** というシーケンスチャネルを作成する。

1. **PlaybackChannel** にコンテンツを追加する。

## チャネルレベル画像再生時間の割り当ての編集 {#editing-channel-level-image-playback-duration-assignment}

以下の節では、AEM Screens チャンネルのコンテンツの再生時間を編集する方法について説明します。

### チャネル内の画像の再生時間を更新する方法 {#updating-the-playback-duration-for-images-in-a-channel}

チャネルレベルの画像再生時間の割り当てを更新するには、以下の手順に従います。

1. シーケンスチャネル **PlaybackChannel** に移動します。

   ![screen_shot_2019-06-24at62818pm](assets/screen_shot_2019-06-24at62818pm.png)

1. クリック **編集** アクションバーから。

   ![screen_shot_2019-06-24at70141pm](assets/screen_shot_2019-06-24at70141pm.png)

1. チャネルエディターで画像を 2 つ以上追加します（次の図を参照）。

   ![screen_shot_2019-06-24at90534pm](assets/screen_shot_2019-06-24at90534pm.png)

1. チャネル内のすべての画像を選択し、左上のレンチアイコン（下図を参照）をクリックして、チャネルレベルの設定ダイアログボックスを開きます。

   ![screen_shot_2019-06-25at95945am](assets/screen_shot_2019-06-25at95945am.png)

1. この **ページ** ダイアログボックスが開きます。

   >[!NOTE]
   >デフォルトでは、チャネル内の画像は再生時間が 8 秒に設定されています。

   ![screen_shot_2019-06-25at100343am](assets/screen_shot_2019-06-25at100343am.png)

   を編集する **期間** 8000 （ミリ秒）～3000 （ミリ秒）、つまり 3 秒です。 右上のチェックマークをクリックします **ページ** ダイアログボックスが開き、変更を保存できます。

   ![screen_shot_2019-06-25at101527am](assets/screen_shot_2019-06-25at101527am.png)

### 結果の表示 {#viewing-the-result}

チャネル再生時間（この例では 3 つの画像すべて）を更新したら、画像が 8 秒（デフォルト値）ではなく 3 秒間再生されることに注意してください。

![channel_preview](assets/channel_preview.gif)
