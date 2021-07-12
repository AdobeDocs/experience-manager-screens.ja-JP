---
title: 切り替えの適用
seo-title: 切り替えの適用
description: ここでは、Screens プロジェクトに切り替えを適用する方法について説明します。
seo-description: ここでは、Screens プロジェクトに切り替えを適用する方法について説明します。
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
feature: Screens のオーサリング
role: Admin, Developer
level: Intermediate
exl-id: 757e6751-8008-487f-be89-9f53ac898928
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 100%

---

# 切り替えの適用 {#applying-transitions}

ここでは、チャネル内の様々なアセット（画像やビデオ）および埋め込みシーケンスの間に&#x200B;**切り替え**&#x200B;コンポーネントを適用する方法について説明します。


>[!CAUTION]
>
>**切り替え**&#x200B;コンポーネントのプロパティについて詳しくは、[切り替え](adding-components-to-a-channel.md#transition)を参照してください。

## チャネル内のアセットへの切り替えコンポーネントの追加 {#adding-transition}

AEM Screens プロジェクトに切り替えコンポーネントを追加するには、以下の手順に従います。

>[!NOTE]
>
>**前提条件**
>
>**TestTransition** チャネルを持つ AEM Screens プロジェクト **TestProject** を作成します。さらに、出力を表示するロケーションとディスプレイをセットアップします。

1. **TestTransition** チャネルに移動し、アクションバーの「**編集**」をクリックします。

   ![image1](assets/transitions1.png)

   >[!NOTE]
   >
   >**TestTransition** チャネルには、既にいくつかのアセット（画像やビデオ）が含まれています。例えば、以下の例では、3 つの画像と 2 つのビデオが **TestTransition** チャネルに含まれています。

   ![image2](assets/transitions2.png)


1. **切り替え**&#x200B;コンポーネントをエディターにドラッグ＆ドロップします。
   >[!CAUTION]
   >
   >チャネル内のアセットに切り替えを追加する前に、シーケンスチャネルの最初のアセットの前に切り替えを追加しないことを確認します。チャネルの最初のアイテムは、切り替えではなくアセットにする必要があります。

   ![image3](assets/transitions3.png)

   >[!NOTE]
   >
   >デフォルトでは、切り替えコンポーネントのプロパティは、例えば、「**タイプ**」は「**フェード**」に、「**デュレーション (ms)**」は「*1600*」に設定されています。また、適用先のアセットより長い切り替えのデュレーションを設定することはお勧めしません。

1. さらに、（シーケンスチャネルを含む）**埋め込みシーケンス**&#x200B;コンポーネントをこのチャネルエディターに追加する場合は、最後に切り替えコンポーネントを追加して、コンテンツが順に再生されるようにすることができます（下図を参照）。

   ![image3](assets/transitions5.png)
