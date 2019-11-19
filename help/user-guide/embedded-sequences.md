---
title: 埋め込みシーケンス
seo-title: 埋め込みシーケンス
description: このページに従って、チャネルの埋め込みシーケンスについて学びます。チャネルの埋め込みシーケンスを使用すると、ユーザーは、親チャネルにコンポーネントを追加したり、様々なチャネルからコンテンツを再利用したり、親チャネルに埋め込んだりできます。
seo-description: このページに従って、チャネルの埋め込みシーケンスについて学びます。チャネルの埋め込みシーケンスを使用すると、ユーザーは、親チャネルにコンポーネントを追加したり、様々なチャネルからコンテンツを再利用したり、親チャネルに埋め込んだりできます。
uuid: 72a8d4e6-e5ce-4069-bf3b-864d03f61585
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: fc13d713-af30-4a54-8408-920f78fd2b2f
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 埋め込みシーケンス {#embedded-sequences}

Using ***Embedded Sequences***, for channels, allows the user to add components in the parent channel and also to re-use the content from a different channel and embed it into the parent channel.

## 埋め込みシーケンスの追加 {#adding-embedded-sequences}

シーケンスチャネルに次のコンポーネントを追加するオプションがあります。

* 埋め込みシーケンス
* 動的埋め込みシーケンス

>[!NOTE]
>
>スクリーンプロジェクトでの他のコンポーネントの使用について詳しくは、[チャネルへのコンポーネントの追加](adding-components-to-a-channel.md)を参照してください。

### 埋め込みシーケンスの追加 {#adding-an-embedded-sequence}

埋め込みシーケンスをチャネルに追加できます。埋め込みシーケンスとは、画像やビデオなどのアセットを含む別のチャネルです。 Adding an embedded sequence allows the user to add the sequence to a channel by ***Channel Path***.

>[!NOTE]
>
>***チャネルパス***チャネルへの明示的な参照を定義します。
>
>*チャネルパス*&#x200B;について詳しくは、画面の作成の[チャネル割り当て](channel-assignment.md)を参照してください。

埋め込みシーケンスをチャネルに追加するには、次の手順に従います。

1. ページを埋め込むチャネルを選択しますFor example, **We.Retail In-Store** --&gt; **Channels** --&gt;** Idle Channel**.

1. Click **Edit** from the action bar to open the channel in the editor mode.
1. 左側のバーのコンポーネントアイコンをクリックして、埋め込まれたページを追加します。Drag and drop the **Embedded Sequence** to the editor.
1. Double-click the **Embedded Sequence** component to add the channel to your original sequence channel.
1. Select the **Channel Path** of the channel.
1. Select the **Duration (ms)** for your embedded channel in the **Sequence** tab. By default, the duration is set to **-1**, that means embedded channel is fully run. ユーザーがデュレーションを指定すると、後続は指定した時間で中断されます（つまり、カットされます）。

1. 「有料再生 **方法」を** 「通常」に **設定します**。

By default, it is set to **normal**. Setting the value to **normal*** (Play all items)* means that the subsequence will run fully on each cycle of the parent sequence. The other possible value is **Play a single item*** (Play a single item)* and that would only show one item of the subsequence on each run (for instance, the 1st item on the first loop, 2nd item on the second loop, and so on.)

>[!NOTE]
>
>**重要:**
>
>（埋め込まれたシーケンスで使用される）チャネルを同じディスプレイに割り当てる必要があります。
>
>上記の手順からチャネルに埋め込みシーケンスを追加した後、次の手順に従います。
>
>1. 表示に移動し、場所フォルダーから表示を選択 **します** 。
>1. アクションバ **ーの「ダッシュボード** 」をクリックして、表示ダッシュボードに移動します。
>1. 「割り当て **済みチャネルと予定パネル** 」から「+チャネルの割り当て **」を選択し、チャネルの割り当て** ダイアログボックスを開きます ****。
   >
   >
1. 「チャネルパス」で、（埋め込まれたシーケンスで使用される）チャネルのパスを **選択します**。
>1. 優先度( **Priority** )がメインチャネルよりも低いことを確認します。
   >
   >
1. 「サポートされるイベント」は選択 **できません**。
>1. Click **Save** once done.
>



次に、埋め込みシーケンス（**Idle Channel - Night**）を既に存在するチャネル（**Idle Channel**）に追加する例を示します。

![new2](assets/new2.gif)

### 動的埋め込みシーケンスの追加 {#adding-a-dynamic-embedded-sequence}

動的埋め込みシーケンスをチャネルに追加できます。動的埋め込みシーケンスは、埋め込みシーケンスと似ていますが、階層に従います。その階層では、あるチャネルに対しておこなわれた変更／更新が、関連する他のチャネルにプロパゲートされます。親子の階層に従い、画像やビデオなどのアセットも含まれます。 動的シーケンスを追加すると、ユーザーは、チャネルロールでチャネルにシーケンスを追加できます。

>[!NOTE]
>
>***チャネルロール***&#x200B;は、ディスプレイのコンテキストを定義します。
>
>*チャネルロール*&#x200B;について詳しくは、画面の作成の[チャネル割り当て](channel-assignment.md)を参照してください。

埋め込みシーケンスをチャネルに追加するには、次の手順に従います。

1. 動的シーケンスを埋め込むチャネルを選択しますFor example, **We.Retail In-Store** --&gt; **Channels** --&gt; **Idle Channel**.

1. Click **Edit** from the action bar to open the channel in the editor mode.
1. 左側のバーのコンポーネントアイコンをクリックして、動的埋め込みシーケンスを追加します。「ダイナミック&#x200B;**な**埋め込みシーケンス** **」をエディターにドラッグ&amp;ドロップします。

1. Double-click the **Dynamic** **Embedded Sequence **component to add the page to your sequence channel.

1. Enter the **Channel Assignment Role**.
1. 「有料再生 **方法」を** 「通常」に **設定します**。 By default, it is set to **normal**. Setting the value to **normal*** (Play all items)* means that the subsequence will run fully on each cycle of the parent sequence. The other possible value is **Play a single item*** (Play a single item)* and that would only show one item of the subsequence on each run (for instance, the 1st item on the first loop, 2nd item on the second loop, and so on.)

1. Select the **Duration (ms)** in **Sequence** tab for your embedded channel in the sequence.

![最新の](assets/latest.gif)

