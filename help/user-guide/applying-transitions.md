---
title: トランジションの適用
description: AEM Screens プロジェクトにトランジションを適用する方法を説明します。
contentOwner: jsyal
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 757e6751-8008-487f-be89-9f53ac898928
TQID: https://experienceleague.adobe.com/t4JTCyQhe7kb5v-dveK4Np9dAAGLBeatCN2kyTM6ELc
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2:
  - id: e8696a6a-4caa-4059-b0b2-3fbb66f5ab7e
  - id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 276
ht-degree: 100%

---

# トランジションの適用 {#applying-transitions}

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
>**TestTransition** チャネルを持つ AEM Screens プロジェクト **TestProject** を作成します。 また、出力を表示する場所とディスプレイをセットアップします。

1. **TestTransition** チャネルに移動し、アクションバーの「**編集**」をクリックします。

   ![image1](assets/transitions1.png)

   >[!NOTE]
   >
   >**TestTransition** チャネルには、既にいくつかのアセット（画像やビデオ）が含まれています。 例えば、以下の例では、3 つの画像と 2 つのビデオが **TestTransition** チャネルに含まれています。

   ![image2](assets/transitions2.png)


1. **切り替え**&#x200B;コンポーネントをエディターにドラッグ＆ドロップします。

   >[!CAUTION]
   >
   >チャネル内のアセットにトランジションを追加する前に、シーケンスチャネルの最初のアセットの前にトランジションを追加しないようにしてください。 チャネルの最初のアイテムは、切り替えではなくアセットにする必要があります。

   ![image3](assets/transitions3.png)

   >[!NOTE]
   >
   >デフォルトでは、トランジションコンポーネントのプロパティは、例えば、「**タイプ**」は「**フェード**」に、「**デュレーション**」は「*1600 ミリ秒*」に設定されています。 また、適用先のアセットより長いトランジションデュレーションを設定することはお勧めしません。

1. また、**埋め込みシーケンス**&#x200B;コンポーネント（シーケンスチャネルを含む）をこのチャンネルエディターに追加すると、末尾にトランジションコンポーネントを追加できます。 これにより、次の画像に示すように、コンテンツが正しい順序で再生されます。

   ![image3](assets/transitions5.png)
