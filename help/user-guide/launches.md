---
title: 画面の起動を使用したコンテンツの更新
seo-title: 画面の起動を使用したコンテンツの更新
description: コンテンツ作成者は、「ローンチ」と呼ばれるチャネルの将来バージョンを作成でき、さらに、このローンチのライブ日付を設定することで、デバイスやプレーヤーでコンテンツをライブにすることができます。
seo-description: コンテンツ作成者は、「ローンチ」と呼ばれるチャネルの将来バージョンを作成でき、さらに、このローンチのライブ日付を設定することで、デバイスやプレーヤーでコンテンツをライブにすることができます。
uuid: fb13117c-b99b-48bd-adb6-040dbd13af16
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 9cd8892b-fe5d-4ad3-9b10-10ff068adba6
docset: aem65
translation-type: tm+mt
source-git-commit: 076aeecd353ebf89893fd01ab28192b9145c844a

---


# 画面の起動を使用したコンテンツの更新 {#launches}

コンテンツ作成者は、将来のチャネル（「画面の起動」と呼ばれる）を作成し **て** 、この起動の有効日をさらに設定できます。 これにより、指定したライブ日にコンテンツをデバイスまたはプレーヤーでライブにすることができます。

With the help of ***Screens Launch***, authors can preview each channel in the launch and should be able to initiate a request for review. 承認者グループは通知を受け取り、要求を承認または拒否できます。ライブ日付に達すると、コンテンツがデバイスで再生されます。

例えば、作成者が c1 および c2（チャネル）という将来バージョンを作成する場合は、ローンチを作成し、ライブ日付を設定します（例：11 月 10 日午前 8 時 00 分）。コンテンツがさらに更新されると、更新されたコンテンツが、レビューを受けるために送信されます。

要求が承認され、ライブ日付（例：11 月 10 日午前 8 時 00 分）になると、このローンチがデバイスまたはプレーヤーでコンテンツを再生します。

## 要件 {#requirements}

Before you start leveraging *Screens Launch* in an AEM Screens project, make sure you understand the concept of Grace Period and its relevance.

設定された実稼働日に対してプレイヤー上でエクスペリエンスを実行するには、次の操作を行います。

* 開始の促進（通常、数秒かかります）

* インスタンスを発行するためのリソースの発行(通常は数分かかり、発行する必要のあるチャネルまたはアセットのサイズによって異なります)

* オフラインコンテンツの更新が完了するまでにかかる時間（通常は数分かかります）

* プレーヤーがパブリッシュインスタンスからコンテンツをダウンロードするのにかかる時間（通常、ダウンロードする必要のあるアセットの帯域幅とサイズに応じて、数分かかります）

* サーバーとプレーヤーの時間差

### 猶予時間について {#understanding-grace-period}

設定したライブ日に対してプレイヤーがコンテンツを開始再生できるようにするには、ライブ日の前に前のアクティビティを開始する必要があります。

有効日が *11月24日、午前9:00、猶予期間が* 24時間の場合、上記の一連のアクションは(有効日 — 猶予期間 **)、つまり11月23日、午前9:00に開始されます。 これにより、上記のすべてのアクションを完了するまでに24時間かかり、コンテンツがプレイヤーに届きます。 これは起動コンテンツであることをプレイヤーは認識するので、コンテンツはすぐには再生されませんが、プレイヤーはこのコンテンツを将来のバージョンとして保存し、開始はプレイヤーのタイムゾーンの設定された実稼働日に再生されます。

例えば、サーバーとデバイスのタイムゾーンがそれぞれ PST と EST であるとします（この場合、最大時差は 3 時間です）。また、プロモーションに 1 分、オーサーからパブリッシュへの公開に 10 分、プレーヤーがリソースをダウンロードするのには通常 10～15 分、それぞれかかるとしましょう。猶予時間は、時差（3 時間）+ ローンチの昇格に要する時間（1 分）+ ローンチの公開に要する時間（10 分）+ プレーヤーでのダウンロードに要する時間（10～15 分）+ バッファー（余裕を見て例えば 30 分）= 3 時間 56 分 = 14160 秒になります。

したがって、開始をスケジュールするたびに、プロモーションはこのオフセットまでに開始が早くなります。 上記の式では、ほとんどの項目に多くの時間がかかりません。サーバーと任意のプレーヤーの最大時間差が分かれば、このオフセットに適切な推測値を使用できます。

>[!NOTE]
>Out-of-the-box, the grace period for Screens Launch is set to 24 hours which means that when we set live date for any launch for the resources under */content/screens*, the promotion will start with this offset.

### Updating out-of-the-box Grace Period {#updating-out-of-the-box-grace-period}

この節では、そのまま使用できる猶予期間を10分に更新する方法について説明します。

1. CRXDE Liteに移動し、に移動します `/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`。
2. 右クリックし、ファイルをコピーします。
3. に移動し、右 `/apps/system/config` クリックして貼り付けます。
4. 重複がCRXDE Liteの `/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config` エディターでファイルをクリックして開きます。 パス/コンテンツ/画面/の猶予期間を *86400として表示する* 必要があ **ります**。 この値を **600に変更します**。

これで、テキストファイル内のコンテンツは次のようになります。

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

前の例で猶予期間を10分に設定したので、 */content/screens*（コンテンツ/画面）の下のリソースを起動する際にライブ日を設定すると、プロモーションはこのオフセットで開始します。

例えば、有効日が11月24日午前9時に設定され、猶予期間が600秒の場合、プロモーションジョブは11月24日午前8時50分に開始されます。

## 画面起動の使用 {#using-launches}

この節では、AEM Screensプロジェクトに画面起動を実装する方法を説明します。

### Creating a Screens Launch {#creating-a-launch}

次の手順に従って、AEM Screensプロジェクトに画面起動機能を実装します。

1. Create a sequence channel in your AEM Screens project, for example **LaunchesDemo** --> **Channels** --> **FutureLaunch**, as shown below.

   >[!CAUTION]
   >
   >AEM Screens プロジェクト内の既存のチャネルからローンチを作成する必要があります。

   ![画像](/help/user-guide/assets/launches-images/launches-11.png)

1. Select the channel **FutureLaunch** and click **Create Launch** from the action bar.

   ![画像](/help/user-guide/assets/launches-images/launches-12.png)

1. **ローンチを作成**&#x200B;ウィザードが開きます。ウィザードに既に表示されているチャネルを選択するか、[ **+ 追加チャネル** ]をクリックして起動を作成するチャネルを追加します。

1. 起動の作 **成ウィザー** ドで「次へ **** 」をクリックします。 「サブペ **ージを含める** 」オプションはデフォルトで選択されています。

   ![画像](/help/user-guide/assets/launches-images/launches-d.png)

   >[!NOTE]
   >「 **+チャネル** 」オプションを使用して、起動を作成する別のチャネルを追加できます。

   「 **追加チャネル** 」オプションを使用するには、起動を作成するチャネルに移動し、「選択」をクリック **します**。

   起動を **** 追加するために複数のチャネルまたはフォルダを選択しようとすると、「選択」オプションは無効になります。

   ![画像](/help/user-guide/assets/launches-images/launches-14.png)

   Once you have selected the channel/channels, click **Next**.


1. 「**ローンチタイトル**」に「**SummerPromotions**」と入力します。「**ローンチ日**」を設定する必要はありません（下図を参照）。「**作成**」をクリックします。

   >[!NOTE]
   >
   >「**ソースページのライブデータを継承**」オプションを&#x200B;*オンにする*&#x200B;と、チャネルをライブコピーとしてローンチに作成できます。元のチャネルで変更がおこなわれた場合、その変更はローンチチャネルに自動的に適用されます。
   >
   >
   >「**ソースページのライブデータを継承**」を&#x200B;*オフにする*&#x200B;と、チャネルをライブ関係なしにローンチにコピーできます。したがって、元のチャネルに変更が加えられた場合、その変更はローンチチャネルには適用されません。

   ![画像](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >ライブローンチ日は、この手順で設定することもできますし、ローンチを作成してからプロパティの編集時にセットアップすることもできます。

   **開始プロモーションのスコープについて**

   * **すべてのローンチを昇格**：設定したライブ日付でローンチのすべてのチャネルが昇格されます。
   * **変更されたページのプロモーション**:変更された起動リソースのみが昇格されます。 ローンチのレビューが不要な場合は、このオプションを使用することをお勧めします。
   * **承認されたページのプロモーション**:このオプションを使用するには、起動の承認ワークフローが起動チャネルで実行されます。 承認されたページのみが、設定されたライブ日にプロモーションされます。

      >[!CAUTION]
      >
      >起動の実施日は、サーバーのタイムゾーンではなく、プレーヤー/デバイスのタイムゾーンに従います。

1. ローンチが作成されたことがわかります。「**開く**」をクリックすると、ページがエディターに表示され、「**完了**」をクリックすると、プロジェクトに戻ります。

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   Clicking **Done** allows you to navigate back to your **FutureLaunch** channel.

   ![画像](/help/user-guide/assets/launches-images/launches-16.png)


### Editing the Launch Properties to Set the Live Date and Scope {#editing-the-launch-properties-to-set-the-live-date-and-scope}

起動の作成後、「起動のプロパティ」を使用して、実稼働日、起動タイトル、プロモーションの範囲などのプロパティを更 **新できます**。

* **「起動日**」とは、実稼働日、つまり、プレイヤーのタイムゾーンに従ってコンテンツが画面プレーヤーで再生される日時を指します。
* **Production Readyでは**、これらのプロモーションを実行した後にチャネルを公開できます。この機能は、この機能を有効にしておき、変更する必要はありません。
* **スコープ**。開始プロモーション中にどのチャネルをプロモーションするかを決定します。


ローンチプロパティを編集するには、以下の手順に従います。

1. 次の図に示すように、 **チャネル** FutureLaunch *(* つまり保留中の起動)に移動し、チャネルを選択します。

   ![画像](/help/user-guide/assets/launches-images/launches-17.png)

1. アクションバ **ーで** ダッシュボード **をクリックすると、チャネルダッシュボードに「** PENDING LAUNCHES」パネルが表示されます。

   ![画像](/help/user-guide/assets/launches-images/launches-18.png)

1. 起動を選択し、 **PENDING LAUNCHESパネルで「** Launch Properties **」を** クリックします。

   ![画像](/help/user-guide/assets/launches-images/launches-19.png)

### 画面の起動の編集/追加チャネル {#editing-the-screens-launch-to-add-or-remove-channels}

起動を作成した後、「起動を編集」オプションを使用して、既存の起動にチャネルを追加または削除 **できます** 。

完了したら、「保存」をクリッ **クし** 、FutureLaunchの **チャネルに戻ります** 。

### 画面の起動を手動で促す{#promote-the-screens-launch-manually}

起動を手動で昇格するには、 **PENDING LAUNCHES（保留中の起動）パネルの** 「起動を昇格」オプションを使用 **します** 。

プロモーションの起動ウィザードで、この手動のプロモーションの一部としてプロモーションするリ **ソースを選択できます**。

![画像](/help/user-guide/assets/launches-images/launches-e.png)

1. 実稼動後に起動を削除するオプションを有効または無効にできます。
1. 次のオプションを使 **用して** 、起動のスコープを設定できます。
   1. **すべてのローンチを昇格**：設定したライブ日付でローンチのすべてのチャネルが昇格されます。
   1. **変更されたページのプロモーション**:変更された起動リソースのみが昇格されます。 ローンチのレビューが不要な場合は、このオプションを使用することをお勧めします。
   1. **承認されたページのプロモーション**:このオプションを使用するには、起動の承認ワークフローが起動チャネルで実行されます。 承認されたページのみが、設定されたライブ日にプロモーションされます。
   1. **現在のページを昇格**:このオプションを使用するには、開始承認ワークフローが現在のページに対してのみ実行される必要があります。
1. Promoteの起動 **ウィザード** で「 **Next** 」をクリックします。
1. 「プロモ **ート** 」をクリックして起動をプロモーションします。

### 画面起動の削除 {#deleting-the-screens-launch}

起動は、 **PENDING LAUNCHESパネルの「** Delete Launch **」オプションを使用して削** 除できます。

>[注意]
>この操作により、すべての子孫（ネストされた起動）も削除されます。

