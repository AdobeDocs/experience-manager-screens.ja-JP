---
title: トランジションの適用
seo-title: トランジションの適用
description: ここでは、Screens プロジェクトにトランジションを適用する方法について説明します。
seo-description: ここでは、Screens プロジェクトにトランジションを適用する方法について説明します。
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: 389a44e3f6175e0a43a6e99edd3048f2b8455d0b

---


# トランジションの適用 {#applying-transitions}

ここでは、チャネル内の様々なアセット（画像やビデオ）および埋め込みシーケンスの間に&#x200B;**トランジション**&#x200B;コンポーネントを適用する方法について説明します。


>[!CAUTION]
>
>**トランジション**&#x200B;コンポーネントのプロパティについて詳しくは、[トランジション](adding-components-to-a-channel.md#transition)を参照してください。

## チャネル内のアセットへのトランジションコンポーネントの追加 {#adding-transition}

AEM Screens プロジェクトにトランジションコンポーネントを追加するには、以下の手順に従います。

>[!NOTE]
>
>**前提条件**
> ：**TestTransition** チャネルを持つ AEM Screens プロジェクト **TestProject** を作成します。さらに、出力を表示するロケーションとディスプレイをセットアップします。

1. **TestTransition** チャネルに移動し、アクションバーの「**編集**」をクリックします。

   ![image1](assets/transitions1.png)

   >[!NOTE]
   >
   >**TestTransition** チャネルには、既にいくつかのアセット（画像やビデオ）が含まれています。例えば、以下の例では、3 つの画像と 2 つのビデオが **TestTransition** チャネルに含まれています。

   ![image2](assets/transitions2.png)


1. **トランジション**&#x200B;コンポーネントをエディターにドラッグ＆ドロップします。
   >[!CAUTION]
   >
   >チャネル内のアセットにトランジションを追加する前に、シーケンスチャネルの最初のアセットの前にトランジションを追加しないことを確認します。チャネルの最初のアイテムは、トランジションではなくアセットにする必要があります。

   ![image3](assets/transitions3.png)

   > [!NOTE]
   >
   >By default, the properties of the transition component such as **Type** is set to **Fade** and the **Duration** is set to *1600 ms*.  また、適用先のアセットより長いトランジションデュレーションを設定することはお勧めしません。

1. さらに、（シーケンスチャネルを含む）**埋め込みシーケンス**&#x200B;コンポーネントをこのチャネルエディターに追加する場合は、最後にトランジションコンポーネントを追加して、コンテンツが順に再生されるようにすることができます（下図を参照）。

   ![image3](assets/transitions5.png)

