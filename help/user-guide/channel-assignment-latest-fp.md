---
title: チャネル割り当て — 最新の FP
seo-title: チャネル割り当て — 最新の FP
description: このページでは、チャネル割り当てと時間帯区分について学びます。
translation-type: tm+mt
source-git-commit: 4ce9bd954a30282d94e30a6868d269b4df0a0f5e
workflow-type: tm+mt
source-wordcount: '1477'
ht-degree: 75%

---


# チャネル割り当て {#channel-assignment}

>[!IMPORTANT]
>この節では、AEM 6.5.5 Screens機能パック以降用のチャネルのチャネル割り当てとスケジュールについて説明します。

ディスプレイの設定が完了したら、チャネルをディスプレイに割り当てて、コンテンツを表示する必要があります。

このページでは、表示にチャネルを割り当てる方法、チャネルのプロパティを理解する方法、および日分割について説明します。

>[!NOTE]
>1 つのディスプレイに複数のチャネルを割り当てることができます。


## チャネルの割り当て {#assign-a-channel-new-release}

以下のセクションに従って、AEM Screens プロジェクトを作成し、チャネルをディスプレイに割り当てます。

### AEM Screens プロジェクトとチャネルの作成 {#creating-project}

次の手順に従って、プロジェクトとチャネルを設定します。

1. 「**DemoScreens**」というタイトルの AEM Screens プロジェクトを作成します。

   ![画像](/help/user-guide/assets/channel-assignment/channel-assign-fp1.png)

   >[!NOTE]
   >AEM Screens プロジェクトの作成方法については、「[プロジェクトの作成と管理](creating-a-screens-project.md)」を参照してください。

1. 「**Cafeteria**」という名前のシーケンスチャネルを&#x200B;**チャネル**&#x200B;フォルダーに作成します。

1. チャネルを選択し、アクションバーの「**編集**」をクリックして、チャネル内のコンテンツを追加します。

   ![画像](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   例えば、**Cafeteria** チャネルには次の画像が表示されるようになりました。

   ![画像](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. 「**SanJose**」という名前の場所と「**Lobby**」というディスプレイを作成します。

   ![画像](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### ディスプレイへのチャネルの割り当て {#assigning-channel-to-display}

プロジェクトの設定が完了したら、チャネルを表示に割り当てて、コンテンツを表示する必要があります。

1. 必要なディスプレイに移動します（例：**DemoProject**／**Locations**／**SanJose**／**StoreDisplay**）。

1. アクションバーで「**チャネルの割り当て**」をタップまたはクリックします。

   ![画像](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   または、

   Tap/click **Dashboard** from the action bar and click **+Assign Channel** from the **ASSIGNED CHANNELS &amp; SCHEDULES** panel.

   ![画像](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. 「**チャネル割り当て**」ダイアログボックスが開きます。

   ![画像](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. From the **Settings** option, you can choose the channel **by path** or **by name**, enter the **Channel Role**, **Priority**, **Supported Events**, and **Interruption Methods**. また、このダイアログボックスで引き付けツールチップを有効にすることもできます。

   ![画像](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >Refer to [Channel Properties](#channel-properties) section to learn more about channel assignment properties.

1. From the **Schedule** option select the **Activation Window** and **Recurrence Schedule**.
   ![画像](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

   >[!NOTE]
   >Refer to [Channel Properties](#channel-properties) section to learn more about channel assignment properties.

1. 環境設定を行ったら、**「保存**」をクリックします。

### Chrome Player でのコンテンツの表示 {#viewing-content-output}

この例は、Chrome Player の出力を示します。ディスプレイにチャネルを割り当てたら、そのデバイスをプレーヤーに登録する必要があります。

デバイスを AEM Screens プレーヤーに登録する方法については、[デバイス登録](device-registration.md)を参照してください。

選択したプレーヤーで次の出力を表示します。

![new1](assets/channel-assignment/channel-assign-output.gif)

## Timeline View {#timeline-view}

ディスプレイにチャネルを割り当て、繰り返しスケジュールを設定したら、[ **割り当て済みチャネルとスケジュール** ]パネルからタイムラインを表示できます。

次の手順に従って、タイムライン表示に移動します。

1. 必要なディスプレイに移動します（例：**DemoProject**／**Locations**／**SanJose**／**StoreDisplay**）。

1. アクションバーで「**チャネルの割り当て**」をタップまたはクリックします。

   ![画像](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   または、

   Tap/click **Dashboard** and click **Timeline** from the **ASSIGNED CHANNELS &amp; SCHEDULES** panel.

1. 保留中の画像（修正予定）

## Understanding Channel Properties from Channel Assignment Dialog Box {#channel-properties}

次のプロパティは、「**チャネルの割り当て**」ダイアログボックスの「**設定**」オプションで設定します。

![画像](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

### チャネルを選択 {#select-channel}

「チャネルを選択」では、目的のチャネルへの参照をチャネル名かチャネルパスのどちらかで指定できます。

* **パス別**：チャネルの絶対パスを使用して明示的な参照を提供します。

* **名前別**：コンテキストにより実際のチャネルを解決するチャネルの名前を入力します。この機能により、場所固有のコンテンツを動的に解決するために、チャネルのローカルバージョンを作成できます。例えば、「*本日のお買い得商品*」という名前のチャネルで、実際のコンテンツは 2 つの都市で異なるものの、すべてのディスプレイでチャネルロールを同じにするといったことができます。

### チャネルロール {#role-channel}

チャネルロールはディスプレイのコンテキストを定義します。ロールは多様なアクションによってターゲットになり、ロールを担う実際のチャネルから独立しています。

### 優先度 {#priority-channel}

優先度は、複数の割り当てが再生条件に一致する場合に、割り当ての順序付けをおこなうために使用します。最高値のものが低い値よりも常に優先されます。例えば、2 つのチャネル A と B がある場合、A の優先度が 1 で B の優先度が 2 であるなら、A より優先度が高いために、チャネル B が表示されます。

>[!NOTE]
>チャネルの優先度は、前述のように、**チャネル割り当て**&#x200B;ダイアログボックスで、数字で設定できます（1 が最小）。また、割り当てられたチャネルは、降順の優先度に基づいて並べ替えられます。

### サポートされているイベント {#supported-events-channel}

* **初期ロード**：プレーヤーが開始するときにチャネルに読み込みます。スケジュールと組み合わせて複数のチャネルに割り当てることができます。
* **待機中画面**：スクリーンがアイドルのときに読み込みます。スケジュールと組み合わせて複数のチャネルに割り当てることができます。
* **タイマー**：スケジュールを指定するときに設定する必要があります。
* **ユーザーインタラクション**：アイドルチャネルのスクリーンのユーザーインタラクション（タッチ）がある場合に、プレーヤーが指定されたチャネルに切り替えて、スクリーンがタッチされたときに読み込みます。

### 中断方法 {#interruption-method-channel}

>[!IMPORTANT]
>
> このオプションは、AEM 6.4 機能パック 8 または AEM 6.5 機能パック 4 でのみ使用できます。

コンテンツ作成者は、重要でないコンテンツを切り取るために、チャネルを中断するタイミングを指定できますが、スケジュールによって再生を中断する前に、重要なコンテンツを完全に再生するオプションを選択することもできます。

**チャネル割り当て**&#x200B;ダイアログボックスで、次の中断方法を設定できるオプションを選択します。

* **今すぐ**：スケジュールがアクティブになった場合や、アップデートを受け取ったりした場合は、再生を停止し、すぐに新しいコンテンツを再生更新またはできます
* **現在のアイテムの最後**：新しいスケジュールがアクティブになった場合や、アップデートを受け取った場合は、シーケンス内の現在のアイテムの再生が終了するのを待ち、その後新しいコンテンツを更新または再生するオプションがあります
   >[!NOTE]
   >このオプションはデフォルトで選択されています。
* **シーケンスの最後**：新しいスケジュールがアクティブになった場合や、アップデートを受け取った場合は、シーケンス全体が終了するのを待ち、目的のシーケンスの直前に、最初の要素に戻り、新しいコンテンツを更新または再生するオプションがあります

   >[!NOTE]
   >2 番目または 3 番目のオプションを使用すると、割り当てで定義されたスケジュール時間が少し遅れる場合があります。これは、プレーヤーが更新する前に、アイテムまたはシーケンスの終了を（指定された時間後に）待機するためです。遅延は、アイテムの再生時間に依存します。


次のプロパティは、「**チャネルの割り当て**」ダイアログボックスの「**スケジュール**」オプションで設定します。

![画像](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

### アクティベーションウィンドウ {#activation-window}

アクティベーションウィンドウでは、**開始日**&#x200B;と&#x200B;**終了日**&#x200B;を選択して、コンテンツを表示できます。

### 繰り返しスケジュール {#recurrence-schedule}

繰り返しスケジュールを使用すると、コンテンツの定期的なスケジュールを設定できます。「**スケジュールを追加**」をクリックして、チャネルに繰り返しスケジュールを追加します。

>[!NOTE]
>チャネルには、複数の繰り返しスケジュールを追加できます。
>Recurrence Schedules introduces *day-parting*, that allows you to set a global schedule with multiple channels running at specific times of the day, and re-use that setup for all your displays at once.

以下のオプションを設定できます。

* **名前**：繰り返しスケジュールのタイトル。
* **繰り返し**：スケジュールを **日別**、**週別**、**月別**、**年別**&#x200B;のどれで実行するかを選択します。
* **開始**：スケジュールの開始時間。
* **終了**：スケジュールの終了時間。時間または期間別に設定できます。
   * **時間**：スケジュールは指定した時刻に終了します。
   * **期間**：スケジュールは、特定の期間（時間または分単位）に実行されます。

### 日分割 {#dayparting}

日分割とは、1日を時間スロットに分割し、目的の時間にどのコンテンツを再生するかを指定することです。 AEM Screens では、必要に応じて日、週、月内の時間帯区分でチャネルのスケジュールを設定できます。

次の例は、3 つのシナリオにおけるチャネルの時間帯区分に関する説明です。

#### 1 日のコンテンツ再生を複数の時間帯に分割 {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

この例は、レストランが日分割を使用して、毎日朝食、昼食、および夕食のメニューを見せる方法を示しています。

ここでは、毎日の時間を異なる時間帯に分割し、チャネルのコンテンツが指定した時間に合わせて再生されるようにします。 チャネルがこの使用例に従ってコンテンツを再生できるように、[繰り返しスケジュール]の次のプロパティを設定します。

| **名前** | **繰り返し** | **開始** | **終了** |
|---|---|---|---|
| 朝食 | 毎日 | 午前 6:00 | 午前 11:00 |
| ランチ | 毎日 | 午前 11:00 | 午後 3:00 |
| ディナー | 毎日 | 午後 3:00 | 午後 8:00 |

#### コンテンツを特定の曜日に再生 {#playing-content-on-a-particular-day-of-the-week}

次の例は、カジノで実装された日分割の例です。カジノでは、毎週週末に8時から午後10時までの間にライブイベントが発生し、午後10時から午前1時の間には特別な料理をディナーメニューに使用できます。

| **名前** | **繰り返し** | **開始** | **終了** |
|---|---|---|---|
| 週末 | 週単位：土曜日、日曜日 | 午後 8:00 | 午後 10:00 |
| スペシャル | 毎日：月～金 | 午後 10:00 | 午前 1:00 |

>[!NOTE]
>
>さらに、チャネルごとに&#x200B;***優先度***&#x200B;を定義できます。例えば、2 つのチャネルを同じ日時または同じ月に設定する場合は、優先度の高いチャネルが最初に再生されます。優先度の最小値は 0 として設定できます。

