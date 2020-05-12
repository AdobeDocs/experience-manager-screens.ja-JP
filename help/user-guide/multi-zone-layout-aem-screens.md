---
title: マルチゾーンレイアウト
seo-title: マルチゾーンレイアウト
description: マルチゾーンレイアウトを使用すると、マルチゾーンコンテンツを作成し、ビデオ、画像およびテキストなどの様々なアセットを使用して、単一のスクリーンに組み合わせることができます。このページでは、この機能について詳しく見ていきます。
seo-description: マルチゾーンレイアウトを使用すると、マルチゾーンコンテンツを作成し、ビデオ、画像およびテキストなどの様々なアセットを使用して、単一のスクリーンに組み合わせることができます。このページでは、この機能について詳しく見ていきます。
uuid: 2ad689ef-700a-4eed-b5e2-fc57f2288388
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 4c073172-d93c-4b73-87ab-0b08789193a3
noindex: true
translation-type: tm+mt
source-git-commit: 052cf1ccde6f18ec72307b14ffbac63be61127b0
workflow-type: tm+mt
source-wordcount: '1189'
ht-degree: 46%

---


# マルチゾーンレイアウト {#multi-zone-layout}

以下では、マルチゾーンレイアウトの使用方法について説明します。取り上げるトピックは次のとおりです。

* 概要
* マルチゾーンレイアウトの作成
* 前提条件
* 1 つ以上のゾーンでの単一アセットの使用
* 1 つ以上のゾーンでのコンテンツシーケンスの使用

## 概要 {#overview}

***マルチゾーンレイアウト***&#x200B;を使用すると、マルチゾーンコンテンツを作成し、ビデオ、画像およびテキストなどの様々なアセットを使用して、単一のスクリーンに組み合わせることができます。画像、ビデオおよびテキスト取り込み、すべてを組み合わせて、直感的なデジタルエクスペリエンスを作成できます。

プロジェクト要件に応じて、1 つのチャネルに複数のゾーンが必要になり、1 つの包括的なユニットとして編集することがあります。例えば、単一チャネルの 3 つの異なるゾーンで動作する関連ソーシャルメディアフィードを含んだ製品シーケンスなどです。


### 前提条件 {#prerequisites}

この機能の実装を開始する前に、次の概念的な知識を確認してください。

* [AEM Screensプロジェクトの作成](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/creating-a-screens-project.html)
* [表示の作成](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/managing-displays.html)
* [ディスプレイにチャネルを割り当てる](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/authoring/setting-up-projects/channel-assignment.html)

## マルチゾーンレイアウトの作成 {#creating-multi-zone-layout}

チャネルを作成する際に、チャネルにゾーンを作成するために、様々なテンプレートを使用できます。1 つの画像、ビデオまたは埋め込みチャンネルを追加して、複数のアセットを 1 つのシーケンスとして表示できます。

**チャネルの作成**

1. Adobe Experience Manager リンク（左上）を選択し、「**Screens**」を選択します。または、`http://localhost:4502/screens.html/content/screens` に直接アクセスすることもできます。
1. **チャネル**&#x200B;フォルダーに移動し、アクションバーの「**作成**」をクリックします。

1. 「 **作成** 」ウィザードから「1x2画面を分割」チャネル **** を選択します。

1. 「**次へ**」をクリックし、「**タイトル**」に「**MultiZone**」と入力します。

1. 「**作成**」をクリックして、チャネルの作成を完了します。

### 1 つ以上のゾーンでの単一アセットの使用 {#using-single-assets-in-one-or-more-zones}

画像やビデオなどの単一アセットを 3 つの異なるゾーンのすべてで使用できます。実装するには、以下の手順に従います。

1. **チャネルにコンテンツを追加する**

   1. **Zones**／**Channels**／**MultiZone** に移動します。
   1. **MultiZone** チャネルを選択し、アクションバーの「**編集**」をクリックして、エディターを開きます。

1. **チャネルに画像を追加する**

   1つの画像またはビデオを2つのゾーンで再生するには、次の図に示すように、チャネルエディターの各ゾーンに画像をドラッグ&amp;ドロップします。

   ![画像](/help/user-guide/assets/multi-zone/multizone-img3.png)

### 1 つ以上のゾーンでのコンテンツシーケンスの使用 {#using-sequenced-content-in-one-or-more-zones}

2つの異なるゾーンにある画像とビデオのシーケンスをゾーンに表示する場合は、次の手順に従って詳細を確認してください。

1. **チャネルフォルダーの作成**

   1. **Zones**／**Channels**／**MultiZone** に移動し、アクションバーの「**作成**」をクリックします。
   1. **作成**&#x200B;ウィザードから「**チャネルフォルダー**」を選択し、「**次へ**」をクリックします。
   1. 「タイトル」に「**EmbeddedChannels**」と入力し、「**作成**」をクリックします。
   ![screen_shot_2018-12-19at125428pm](assets/screen_shot_2018-12-19at125428pm.png)

1. **チャネルフォルダーにさらに 2 つのチャネルを追加する**

   1. **Zones**／**Channels**／**EmbeddedChannels** に移動し、アクションバーの「**作成**」をクリックします。
   1. Select **Sequence Channel** from the **Create** wizard to create a channel titled as **Zone1**.
   1. **Zone1** を選択し、アクションバーの「**編集**」をクリックして、エディターを開きます。
   1. このチャネルに画像をいくつかドラッグ＆ドロップします。
   1. 同様に、**EmbeddedChannels** フォルダーに「**Zone2**」というタイトルの別のシーケンスチャネルを作成します。
   1. ビデオをこのチャネルにドラッグ&amp;ドロップします。
   次の図に、 **Zone1** と **Zone2のチャネルを示します**。

   ![screen_shot_2018-12-19at125930pm](assets/screen_shot_2018-12-19at125930pm.png)

   エディタの **Zone1** sequenceチャネルに追加された画像を次に示します。

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img4.png)

   次に、 **Zone2** sequenceチャネルのエディターに追加されたビデオを示します。

   ![screen_shot_2018-12-19at125930pm](/help/user-guide/assets/multi-zone/multizone-img5.png)

1. **メインチャネル(MultiZone)への埋め込みシーケンス（コンポーネント）の追加**

   1. **Zones**／**Channels**／**MultiZone** に移動します。
   1. アクションバーの「**編集**」をクリックして、エディターを開きます。
   1. 「 **埋め込みシーケンス** 」コンポーネントを両方のゾーンにドラッグ&amp;ドロップします。
   1. いずれかのゾーンの埋め込みシーケンスを選択します。
   1. エディターで、埋め込みシーケンスの&#x200B;**設定**（レンチ）アイコンをクリックします。
   1. 「チャネルパス」として **Zones**／**Channels**／**EmbeddedChannels**／**Zone1** を選択します（下図を参照）。
   1. 同様に、**Zone2** をエディター内の別の埋め込みシーケンスコンポーネントに追加します。

      ![画像](/help/user-guide/assets/multi-zone/multizone-3.png)

### 場所と表示の作成 {#creating-location}

画面プレーヤーでコンテンツを表示する場所と表示を作成する必要があります。 場所と表示を作成するには、次の手順に従います。

1. **ロケーションの作成**

   1. Navigate to **Zones** --> **Locations** folder.
   1. Select the **Locations** folder and click **Create** from the action bar.
   1. **作成**&#x200B;ウィザードから「**ロケーション**」を選択し、「**次へ**」をクリックします。
   1. Enter the **Title** as **SanJose** and click **Create**.

1. **表示の作成**

   1. Navigate to **Zones** --> **Locations** folder.
   1. サンノゼの **場所を選択し、アクションバーの[** 作成 **** ]をクリックします。
   1. **作成**&#x200B;ウィザードから「**ディスプレイ**」を選択し、「**次へ**」をクリックします。
   1. Enter the **Title** as **Lobby** and click **Create**.

### ディスプレイへのチャネルの割り当て {#channel-channel}

コンテンツを表示するには、チャネルを表示に割り当てる必要があります。 次の手順に従って、チャネルを表示に割り当てます。

1. **ディスプレイへのチャネルの割り当て**

   1. [ **Zones** ] —> [ **Locations** ] —> [ **SanJose**] —> [ **** Lobby]に移動します。
   1. [ **Lobby** ]表示を選択し、アクションバーの[ **チャネル** を割り当て]をクリックします。
   1. [ **チャネルパス** ]にMultiZone ****&#x200B;チャネルへのパスを入力します。
   1. **サポートされるイベント** を、 **Initial Load**、 **Idle Screen**、および **** Timerに設定します。
   1. 「**保存**」をクリックします。

      ![画像](/help/user-guide/assets/multi-zone/multizone-img9.png)
   1. 同様に、他の2つの埋め込みチャネル(**Zone1** と **Zone2**)をこの表示に割り当てる必要があります。
   1. 3つのチャネルをすべて **ロビー** 表示に割り当てると、割り当てられたチャネルを表示ダッシュボードから表示できるようになります。

      ![画像](/help/user-guide/assets/multi-zone/multizone-img8.png)


      >[!I重要]
      > メインチャネル(この場合は **MultiZone**)をディスプレイに割り当てると、他の2つの埋め込みチャネル **Zone1** と **Zone2** も同じディスプレイに割り当てる必要があります。

### デバイスの登録 {#registering-device}

場所とディスプレイを設定したら、次の手順に従ってデバイスを登録し、ディスプレイをデバイスに割り当てます。

1. **デバイスの登録**

   1. [ **Zones** ] —> [ **Devices** ]フォルダに移動します。
   1. Select the **Devices** folder and click **Device Manager** from the action bar.
   1. 「 **Device Registration** 」をクリックし、リストから保留中のデバイスを選択します。
      >[!NOTE]
      > デバイスのタイトルは、「**Device Registration** （デバイス登録） **」タブに表示されるデバイストークン(トークン** )と一致する必要があります。
   1. タイトルがデバイストークンと一致する場合は、デバイスを選択し、アクションバーの「 **デバイスを登録** 」をクリックします。
   1. 登録コードが「画面プレーヤーの **デバイス登録** 」タブのコードと一致する場合は、アクションバーの「 **検証** 」をクリックします。
      ![画像](/help/user-guide/assets/multi-zone/multizone-img6.png)
   1. Enter the **Title** as **Chrome-Device1** and click **Register**.
   1. 「 **表示の割り当て** 」を選択し、デバイス設定へのパスを選択します。
   >[!NOTE]
   >画面プレイヤーでコンテンツを表示しようとする場合は、チャネルダッシュボードの「オフラインコンテンツを **更新** 」をクリックしていることを確認してください。

### 結果の表示 {#viewing-the-result}

前述の手順を使用してマルチゾーンレイアウトを実装すると、次の出力が表示されます。

2つの異なるゾーンにコンテンツを表示する出力を表示するには、画面プレイヤーをチェックします。 左ゾーンと右ゾーン（どちらも埋め込みシーケンスをコンポーネントとして使用）。

左ゾーンはシーケンスチャネルであり、右ゾーンはビデオを含む。

![new2-1](/help/user-guide/assets/multi-zone/Multi-gif.gif)


