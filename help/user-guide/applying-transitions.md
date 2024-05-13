---
title: 切り替えの適用
description: AEM Screens プロジェクトにトランジションを適用する方法を説明します。
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 757e6751-8008-487f-be89-9f53ac898928
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 59%

---

# 切り替えの適用 {#applying-transitions}

ここでは、チャネル内の様々なアセット（画像やビデオ）および埋め込みシーケンスの間に&#x200B;**トランジション**&#x200B;コンポーネントを適用する方法について説明します。

>[!CAUTION]
>
>**トランジション**&#x200B;コンポーネントのプロパティについて詳しくは、[トランジション](adding-components-to-a-channel.md#transition)を参照してください。

## チャネル内のアセットへの切り替えコンポーネントの追加 {#adding-transition}

AEM Screens プロジェクトに切り替えコンポーネントを追加するには、以下の手順に従います。

>[!NOTE]
>
>**前提条件**
>
>**TestTransition** チャネルを持つ AEM Screens プロジェクト **TestProject** を作成します。また、出力を表示する場所とディスプレイを設定します。

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
   >デフォルトでは、トランジションコンポーネントのプロパティは次のようになります **タイプ** はに設定されています。 **フェード** および **期間** はに設定されています。 *1600 ミリ秒*. また、適用先のアセットよりも長い移行期間を設定することはお勧めしません。

1. また、 **埋め込みシーケンス** コンポーネント（シーケンスチャネルを含む）このチャネルエディターの最後にトランジションコンポーネントを追加できます。 これにより、次の画像に示すように、コンテンツが正しい順序で再生されます。

   ![image3](assets/transitions5.png)
