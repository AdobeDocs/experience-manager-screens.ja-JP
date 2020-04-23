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
source-git-commit: 14a45b58862477ec6be082ab1c059f991b086755

---


# 画面の起動を使用したコンテンツの更新 {#launches}

コンテンツ作成者は、将来のチャネル（「画面の起動」と呼ばれる）を作成し **て** 、この起動の有効日をさらに設定できます。 これにより、指定したライブ日にコンテンツをデバイスまたはプレーヤーでライブにすることができます。

With the help of **Screens Launches**, authors can preview each channel in the launch and should be able to initiate a request for review. 承認者グループは通知を受け取り、要求を承認または拒否できます。ライブ日付に達すると、コンテンツがデバイスで再生されます。

例えば、作成者が c1 および c2（チャネル）という将来バージョンを作成する場合は、ローンチを作成し、ライブ日付を設定します（例：11 月 10 日午前 8 時 00 分）。コンテンツがさらに更新されると、更新されたコンテンツが、レビューを受けるために送信されます。要求が承認され、ライブ日付（例：11 月 10 日午前 8 時 00 分）になると、このローンチがデバイスまたはプレーヤーでコンテンツを再生します。

## 要件 {#requirements}

AEM Screensプロジェクトで画面の起動を開始する前に、猶予期間の概念とその関連性を理解しておく必要があります。

設定された実稼働日に対してプレイヤー上でエクスペリエンスを実行するには、次の操作を行います。

* 開始の促進（通常、数秒かかります）

* インスタンスを発行するためのリソースの発行(通常は数分かかり、発行する必要のあるチャネルまたはアセットのサイズによって異なります)

* オフラインコンテンツの更新が完了するまでにかかる時間（通常は数分かかります）

* プレーヤーがパブリッシュインスタンスからコンテンツをダウンロードするのにかかる時間（通常、ダウンロードする必要のあるアセットの帯域幅とサイズに応じて、数分かかります）

* サーバーとプレーヤーの時間差

### 猶予時間について {#understanding-grace-period}

設定したライブ日に対してプレイヤーがコンテンツを開始再生できるようにするには、前述のアクティビティをライブ日の前に開始する必要があります。

有効日が *11月24日、午前9:00、猶予期間が* 24時間の場合、上記の一連のアクションは(有効日 — 猶予期間 **)、つまり11月23日、午前9:00に開始されます。 これにより、上記のすべてのアクションを完了するまでに24時間かかり、コンテンツがプレイヤーに届きます。 これは起動コンテンツであることをプレイヤーは認識するので、コンテンツはすぐには再生されませんが、プレイヤーはこのコンテンツを将来のバージョンとして保存し、開始はプレイヤーのタイムゾーンの設定された実稼働日に再生されます。

例えば、サーバーとデバイスのタイムゾーンがそれぞれ PST と EST であるとします（この場合、最大時差は 3 時間です）。また、プロモーションに 1 分、オーサーからパブリッシュへの公開に 10 分、プレーヤーがリソースをダウンロードするのには通常 10～15 分、それぞれかかるとしましょう。猶予時間は、時差（3 時間）+ ローンチの昇格に要する時間（1 分）+ ローンチの公開に要する時間（10 分）+ プレーヤーでのダウンロードに要する時間（10～15 分）+ バッファー（余裕を見て例えば 30 分）= 3 時間 56 分 = 14160 秒になります。したがって、ローンチのライブ日付をスケジュールした場合は、このオフセット分だけ早めに昇格が開始されます。上記の式では、ほとんどの項目に多くの時間はかかりません。サーバーとプレーヤーの間の最大時差がわかれば、このオフセットの妥当な推測をおこなえます。

>[!NOTE]
>Out-of-the-box, the grace period for screens launches is set to 24 hours which means that when we set live date for any launch for the resources under */content/screens*, the promotion will start with this offset.

### Updating out-of-the-box Grace Period {#updating-out-of-the-box-grace-period}

この節では、そのまま使用できる猶予期間を10分に更新する方法について説明します。

1. CRXDE Liteに移動し、に移動します `/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`。
2. 右クリックし、ファイルをコピーします。
3. に移動し、右 `/apps/system/config` クリックして貼り付けます。
4. 重複がCRXDE Liteの `/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config` エディターでファイルをクリックして開きます。 パス/コンテンツ/画面/86400の猶予期 *間を86400として表示する* 必要があります。 この値を **600に変更します**。

これで、テキストファイル内のコンテンツは次のようになります。

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

前の例で猶予期間を10分に設定したので、 */content/screens*（コンテンツ/画面）の下のリソースを起動する際にライブ日を設定すると、プロモーションはこのオフセットで開始します。

例えば、有効日が11月24日午前9時に設定され、猶予期間が600秒の場合、プロモーションジョブは11月24日午前8時50分に開始されます。

## 画面起動の使用 {#using-launches}

以下の節に従って、AEM Screensプロジェクトに起動を実装します。 ここでは、以下のトピックについて説明します。

1. **画面起動の作成**
1. **画面の起動の編集によるライブの日付と範囲の設定**

### Creating a Screens Launch {#creating-a-launch}

次の手順に従って、AEM Screensプロジェクトに起動機能を実装します。

1. Create a sequence channel in your AEM Screens project, for example **LaunchesDemo** --> **Channels** --> **FutureLaunch**, as shown below.

   >[!CAUTION]
   >
   >AEM Screens プロジェクト内の既存のチャネルからローンチを作成する必要があります。

   ![画像](/help/user-guide/assets/launches-images/launches-11.png)

1. Select the channel **FutureLaunch** and click **Create Launch** from the action bar.

   ![画像](/help/user-guide/assets/launches-images/launches-12.png)

1. **ローンチを作成**&#x200B;ウィザードが開きます。ウィザードに既に表示されているチャネルを選択するか、[ **+ 追加チャネル** ]をクリックして起動を作成するチャネルを追加します。


#### 既存のチャネル {#existing-channel-launch}

1. 起動の作成チャネルに既に存在するウィザードを **選択し** 、「次へ」をクリッ **クします**。

   ![画像](/help/user-guide/assets/launches-images/launches-b.png)

1. Select the channel and click **Next** from the action bar.

   >[!NOTE]
   >**「サブページを含める** 」オプションはデフォルトで選択されています。

   ![画像](/help/user-guide/assets/launches-images/launches-b.png)

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

1. ローンチが作成されたことがわかります。「**開く**」をクリックすると、ページがエディターに表示され、「**完了**」をクリックすると、プロジェクトに戻ります。

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   Clicking **Done** allows you to navigate back to your **FutureLaunch** channel.

   ![画像](/help/user-guide/assets/launches-images/launches-16.png)


#### オプション追加の使用 {#add-channel-launch}

1. 「 **+チャネル** 」をクリックして、起動を作成するチャネルを追加します。

   ![画像](/help/user-guide/assets/launches-images/launches-13.png)

   >[!NOTE]
   >起動を **** 追加するために複数のチャネルまたはフォルダを選択しようとすると、「選択」オプションは無効になります。

1. 起動を作成するチャネルに移動し、「選択」をクリックし **ます**。

   ![画像](/help/user-guide/assets/launches-images/launches-14.png)

1. これで、追加したチャネルを選択して起動を作成し、「次へ」をクリックで **きます**。

   ![画像](/help/user-guide/assets/launches-images/launches-15.png)

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

1. ローンチが作成されたことがわかります。「**開く**」をクリックすると、ページがエディターに表示され、「**完了**」をクリックすると、プロジェクトに戻ります。

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   Clicking **Done** allows you to navigate back to your **FutureLaunch** channel.

   ![画像](/help/user-guide/assets/launches-images/launches-16.png)

### ローンチプロパティの編集によるライブ日付と範囲の設定 {#editing-the-launch-properties-to-set-the-live-date-and-scope}

ローンチを作成したら、ローンチプロパティを編集して、ローンチのライブ日付と範囲を設定する必要があります。

ローンチプロパティを編集するには、以下の手順に従います。

1. 次の図に示すように、 **チャネル** FutureLaunch *(* つまり保留中の起動)に移動し、チャネルを選択します。

   ![画像](/help/user-guide/assets/launches-images/launches-17.png)

1. アクションバ **ーで** ダッシュボード **をクリックすると、チャネルダッシュボードに「** PENDING LAUNCHES」パネルが表示されます。

   ![画像](/help/user-guide/assets/launches-images/launches-18.png)

1. 起動を選択し、「 **PENDING LAUNCHES」パネルから目的のアクションをク** リックします。

   ![画像](/help/user-guide/assets/launches-images/launches-19.png)

1. 例えば、「起動プロパティ」をク **リックして** 、「夏のプロモーション」の開始のプロパティを編 **集します**。

   ![画像](/help/user-guide/assets/launches-images/launches-20.png)

1. ランチタイトルを編集 **し、次のフィールド** に値を入力できます。

   * 「**ローンチ日**」を選択します。
   * 「**実稼動準備完了**」をオンにします。
   * 「**範囲**」から「**承認したページを昇格**」を選択します。
   **自動プロモーションの下の起動エントリについて：**

   * 「**ローンチ日**」：ライブ日付を指します。つまり、Screens プレーヤーのタイムゾーンに従ってコンテンツがプレーヤーで再生される日時のことです。
   * 「**実稼動準備完了**」：チャネルの昇格が可能になります。つまり、ローンチの使用準備ができています。
   * 「**範囲**」：ローンチ時に昇格可能なチャネルを指します。
   範囲をセットアップする場合は、次の 3 つのオプションがあります。

   * **すべてのローンチを昇格**：設定したライブ日付でローンチのすべてのチャネルが昇格されます。
   * **変更したページを昇格**：編集されたローンチリソースのみ昇格されます。ローンチのレビューが不要な場合は、このオプションを使用することをお勧めします。ローンチチャネルの変更内容を昇格させることができます。
   * **承認したページを昇格**：設定したライブ日付で承認済みページのみ昇格されます。

      >[!CAUTION]
      >
      >ローンチの昇格では、サーバーのタイムゾーンではなくプレーヤーやデバイスのタイムゾーンに従います。



1. 「**保存して閉じる**」をクリックして、**FutureLaunch** チャネルに戻ります。

