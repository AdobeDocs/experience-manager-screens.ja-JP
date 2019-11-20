---
title: トランジションの適用
seo-title: トランジションの適用
description: このページでは、画面プロジェクトにトランジションを適用する方法について説明します。
seo-description: このページでは、画面プロジェクトにトランジションを適用する方法について説明します。
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: 02acf7ffc447c92efb75d756071d2cd5f4aaf104

---


# トランジションの適用 {#applying-transitions}

ここでは、 **Transition** コンポーネントでScreensプロジェクトにトランジションを追加する方法について説明します。


>[!CAUTION]
>
>トランジションコンポーネントのプロパティの詳細については、「トランジション」を参照してくだ [さい](adding-components-to-a-channel.md#transition)

## 摺り付けコンポーネントを追加する {#adding-transition}

次の手順に従って、AEM Screensプロジェクトにトランジションコンポーネントを追加します。

>[!NOTE]
>
>**前提条件**
> チャネルTestTransitionを使用してAEM Screensプロジ **ェクト** TestProjectを作 **成します**。 さらに、出力を表示する場所と表示を設定します。

1. Channel testTransitionに移動し、アクシ **ョンバーで** 「 **Edit** 」をクリックします。



   >[!NOTE]
   >
   >TestTransitionチャ **ンネルには** 、既にほとんどアセット（画像やビデオ）が含まれていません。 例えば、次に示すよう **に** 、TestTransitionチャネルには5つの画像と1つのビデオが含まれます。



1. トランジションコンポーネント **をエディタ** にドラッグ&amp;ドロップします。

   > [!NOTE]
   >
   >デフォルトでは、トランジションコンポーネントは **Normalに設定され** 、 **Durationは** 600 *msに設定されます*。


   >[!CAUTION]
   >
   >チャネル内のアセットにトランジションを追加する前に、次の点を確認します。順次チャネル内の最初のアセットの前にトランジションを追加することはありません。 チャネルの最初の項目は、トランジションではなくアセットである必要があります。
