---
title: チャネル割り当て — 最新FP
seo-title: チャネル割り当て — 最新FP
description: チャネルの割り当てと日分割については、このページを参照してください。
translation-type: tm+mt
source-git-commit: f5d80f3765993277c552b64685d12244658915bb
workflow-type: tm+mt
source-wordcount: '1488'
ht-degree: 45%

---


# チャネル割り当て {#channel-assignment}

>[!IMPORTANT]
>この節では、AEM 6.5.5 Screens機能パック以降用のチャネルのチャネル割り当てとスケジュールについて説明します。

ディスプレイを設定したら、コンテンツを表示するために、ディスプレイにチャネルを割り当てる必要があります。

このページでは、表示にチャネルを割り当てる方法、チャネルのプロパティを理解する方法、および日分割を示します。

>[!NOTE]
>1つのディスプレイに複数のチャネルを割り当てることができます。


## チャネルの割り当て {#assign-a-channel-new-release}

以下のセクションに従って、AEM Screensプロジェクトを作成し、チャネルをディスプレイに割り当てます。

### AEM Screensプロジェクトとチャネルの作成 {#creating-project}

次の手順に従って、プロジェクトとチャネルを設定します。

1. Create an AEM Screens Project titled as **DemoScreens**.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp1.png)

   >[!NOTE]
   >AEM Screensプロジェクトの作成方法については、 [「プロジェクトの作成と管理](creating-a-screens-project.md) 」を参照してください。

1. 「 **Cafeteria** 」という名前のシーケンスチャネルーを **** チャネルフォルダーに作成します。

1. Select the channel and click **Edit** from the action bar to add content to your channel.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp2.png)

   例えば、 **Cafeteria** チャネルには次の画像が表示されるようになりました。

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp3.png)

1. 「 **SanJose** 」という名前の場所を作成し、「 **Lobby**」と表示します。

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp4.png)

### Assigning Channel to a Display {#assigning-channel-to-display}

プロジェクトの設定が完了したら、チャネルを表示に割り当てて、コンテンツを表示する必要があります。

1. Navigate to the required display, for example, **DemoScreens** --> **Locations** --> **SanJose** --> **Lobby**.

1. Tap/click **Assign Channel** from the action bar.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   または、

   アクションバーの **ダッシュボードをタップまたはクリックし** 、「割り当てられたチャネルとスケジュール **」パネルの「チャネルの割り当て****** 」をクリックします。

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp6.png)

1. The **Channel Assignment** dialog box opens.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

1. 「 **設定****」オプションから、** 「名前別パス別チャネル」または「名前別チャネル別」を選択して、「ロール **イベント」を入力し、「優先度******************」を入力し、「サポートされている」を入力します。 また、このダイアログボックスで引き付けツールチップを有効にすることもできます。

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

   >[!NOTE]
   >チャネル割り当てプロパティの詳細については、「 [チャネルのプロパティ](#channel-properties) 」の節を参照してください。

1. 「 **スケジュール** 」オプションから、「 **参照タイムゾーン**」、「 **アクティベーションウィンドウ** 」、「 ****繰り返しスケジュール」の順に選択します。
   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)

   >[!NOTE]
   >チャネル割り当てプロパティの詳細については、「 [チャネルのプロパティ](#channel-properties) 」の節を参照してください。

1. 環境設定を行ったら、 **「保存** 」をクリックします。

### Viewing the Content in Chrome Player {#viewing-content-output}

この例は、Chrome Playerの出力を示します。 ディスプレイにチャネルを割り当てたら、そのデバイスをプレイヤーに登録する必要があります。

デバイスを [AEM Screensプレイヤに登録する方法については、Device Registration](device-registration.md) （デバイス登録）を参照してください。

選択したプレーヤーに次の出力を表示します。

![new1](assets/channel-assignment/channel-assign-output.gif)

## Timeline View {#timeline-view}

ディスプレイにチャネルを割り当て、繰り返しスケジュールを設定したら、[ **割り当て済みチャネルとスケジュール** ]パネルからタイムラインを表示できます。

次の手順に従って、タイムライン表示に移動します。

1. Navigate to the required display, for example, **DemoScreens** --> **Locations** --> **SanJose** --> **Lobby**.

1. Tap/click **Assign Channel** from the action bar.

   ![image](/help/user-guide/assets/channel-assignment/channel-assign-fp5.png)

   または、

   「 **ダッシュボード** 」をタップまたはクリックし、「 **割り当てられたチャネルとスケジュール** 」パネルで「タイムライン **** 」をクリックします。

1. 保留中の画像（修正予定）

## Understanding Channel Properties from Channel Assignment Dialog Box {#channel-properties}

次のプロパティは、[ **チャネルの割り当て** ]ダイアログボックスの[ **設定** ]オプションで設定します。

![image](/help/user-guide/assets/channel-assignment/channel-assign-fp7.png)

### チャネルを選択 {#select-channel}

チャネルを選択すると、チャネル名またはチャネルパスで、目的のチャネルへの参照を指定できます。

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

* **今すぐ**：スケジュールがアクティブになったり、アップデートを受け取った場合は、再生を停止し、すぐに新しいコンテンツを再生更新またはできます
* **現在のアイテムの最後**：新しいスケジュールがアクティブになったり、アップデートを受け取った場合は、シーケンス内の現在のアイテムの再生が終了するのを待ち、その後新しいコンテンツを更新または再生するオプションがあります
   >[!NOTE]
   >このオプションはデフォルトで選択されています。
* **シーケンスの最後**：新しいスケジュールがアクティブになったり、アップデートを受け取った場合は、シーケンス全体が終了するのを待ち、目的のシーケンスの直前に、最初の要素に戻り、新しいコンテンツを更新または再生するオプションがあります

   >[!NOTE]
   >2 番目または 3 番目のオプションを使用すると、割り当てで定義されたスケジュール時間が少し遅れる場合があります。これは、プレイヤーが更新する前に、アイテムまたはシーケンスの終了を（指定された時間後に）待機するためです。遅延は、アイテムの再生時間に依存します。


次のプロパティは、[ **チャネルの割り当て** ]ダイアログボックスの[ **スケジュール** ]オプションで設定します。

### リファレンスタイムゾーン {#reference-timezone}

参照タイムゾーンを使用すると、コンテンツ表示のタイムゾーンを選択できます。

### アクティベーションウィンドウ {#activation-window}

アクティベーションウィンドウでは、 **開始日** と **** 終了日を選択して、コンテンツを表示できます。

### 繰り返しスケジュール {#recurrence-schedule}

繰り返しスケジュールを使用すると、コンテンツの定期的なスケジュールを設定できます。 [ **+スケジュール** ]をクリックして、チャネルに繰り返しスケジュールを追加します。

![image](/help/user-guide/assets/channel-assignment/channel-assign-fp8.png)


>[!NOTE]
>チャネルには、複数の定期スケジュールを追加できます。
>Recurrence Schedules introduces *DayParting*, that allows you to set a global schedule with multiple channels running at specific times of the day, and re-use that setup for all your displays at once.

次のオプションを設定できます。

* **名前**:繰り返しスケジュールのタイトル。
* **繰り返し**:スケジュールを **日別**、 **週別**、月別 ********、年別のいずれで実行するかを選択します。
* **開始**:スケジュールの開始時間。
* **終了**:スケジュールの終了時間。 次の方法で設定できます。
* **時間**:スケジュールは指定した時刻に終了します。
* **期間**:スケジュールは、特定の期間（時間または分単位）実行されます。

### DayParting {#dayparting}

時間帯区分は、1 日を複数の時間帯に分けて、必要な時間にどのコンテツを再生するかを指定することを意味します。AEM Screensでは、必要に応じて1日、1週間、または1か月内の日分割に関するチャネルをスケジュールできます。

次の例では、3つの異なるシナリオのチャネルでの日分割について説明します。

#### 1 日のコンテンツ再生を複数の時間帯に分割 {#playing-content-on-a-single-day-divided-into-multiple-time-slots}

この例は、RestaurantがDayPartingを使用して、毎日朝食、昼食、夕食のメニューを見せる方法を示します。

ここでは、毎日の時間を異なる時間帯に分割し、チャネルのコンテンツが指定した時間に合わせて再生されるようにします。 チャネルがこの使用例に従ってコンテンツを再生できるように、[繰り返しスケジュール]の次のプロパティを設定します。

| **名前** | **繰り返し** | **Start** | **End** |
|---|---|---|---|
| モーニング | 毎日 | 6:00 AM | 11:00 AM |
| ランチ | 毎日 | 11:02 AM | 3:00 PM |
| ディナー | 毎日 | 3:01 PM | 8:00 PM |

#### コンテンツを特定の曜日に再生 {#playing-content-on-a-particular-day-of-the-week}

次の例は、ライブイベントが毎週週末8時から午後10時まで発生するカジノでDayPartingを実装し、午後10時から午前1時の間に特別なメニューを使用してディナーメニューを作成する場合の例です。

| **名前** | **繰り返し** | **Start** | **End** |
|---|---|---|---|
| 週末 | 毎週 | 8:00 PM | 10:00 PM |
| 特別 | 毎日 | 10:00 PM | 1:00 AM |

>[!NOTE]
>
>さらに、チャネルごとに&#x200B;***優先度***&#x200B;を定義できます。例えば、2 つのチャネルを同じ日時または同じ月に設定する場合は、優先度の高いチャネルが最初に再生されます。優先度の最小値は 0 として設定できます。

