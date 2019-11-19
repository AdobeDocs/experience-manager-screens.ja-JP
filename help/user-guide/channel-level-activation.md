---
title: チャネルレベルのアクティブ化 — 単一イベントの再生
seo-title: チャネルレベルのアクティブ化 — 単一イベントの再生
description: このガイドでは、単一のイベント再生を使用したチャネルレベルのアクティブ化について説明します。
seo-description: このガイドでは、単一のイベント再生を使用したチャネルレベルのアクティブ化について説明します。
uuid: 87230344-5f9a-42a4-a7a8-ae4203303612
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
content-type: reference
discoiquuid: c28fd669-f23e-4d53-bec1-a2911274567d
noindex: true
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# チャネルレベルのアクティブ化 — 単一イベントの再生 {#channel-level-activation-single-event-playback}

チャネルレベルのアクティブ化の使用に関するトピックを次に示します。

* 概要
* チャネルレベルのアクティブ化を単一のイベント再生として使用する

## 概要 {#overview}

***チャネルレベルの有効化*** (Channel Level Activation)を使用すると、特定の設定スケジュールの後にチャネルを切り替えることができます。 1つのイベントチャネルは、設定されたスケジュールの後にメインチャネルを置き換え、メインチャネルが再びコンテンツを再生するまで、特定の時間再生します。

次の例は、次のキーワードに焦点を当てた解決策を示しています。

* グロー ***バルシーケンスの*** 、主シーケンスチャネル
* 1回のイ ***ベントチャネル*** （設定された時間に1回だけ実行される）
* メイン ***シーケンスチャネル内で発生する*** 、単一の再生イベントに対して設定されたスケジュールと優先順位

## チャネルレベルのアクティブ化の使用 {#using-channel-level-activation}

次の節では、AEM Screensプロジェクト用のチャネル内での単一のイベント再生の作成について説明します。

### 前提条件 {#prerequisites}

この機能の実装を開始する前に、チャネルレベルのアクティブ化の実装を開始するための次の前提条件が満たされていることを確認してください。

* AEM Screensプロジェクトを作成します。この例では、チャネルレベルのアクテ **ィブ化を行います。**

* Channelsフォルダーの下にMainAdChannelと **して** 、チャネルを **作成**

* Channelsフォルダーの下にTargetedSinglePlayとして別 **のチャネル** を **作成**

* 両方のチャネルに関連するアセットを追加

次の画像は、MainAdChannelを使用する **Channel Level Activation** Projectで、Channels folder内のTargetedSinglePlay **Channelを使用して********** います。

![screen_shot_2018-11-27at104500am](assets/screen_shot_2018-11-27at104500am.png)

>[!NOTE]
>
>プロジェクトの作成方法とシーケンスチャネルの作成方法に関する詳細は、以下のリソースを参照してください。
>
>* [プロジェクトの作成と管理](creating-a-screens-project.md)
   >
   >
* [チャネルの管理](managing-channels.md)
>



### 実装 {#implementation}

AEM Screensプロジェクトにチャネルレベルのアクティブ化を実装するには、次の3つの主なタスクが必要です。

1. **チャネル、場所、表示を含むプロジェクト分類の設定**
1. **表示するチャネルの割り当て**
1. **スケジュールと優先度の設定**

次の手順に従って機能を実装します。

1. **場所の作成**

   AEM Screensプロジェクトの **Locations** フォルダーに移動し、「地域」として場所を作成 **します**。

   ![screen_shot_2018-11-27at112112am](assets/screen_shot_2018-11-27at112112am.png)

   >[!NOTE]
   >
   >場所の作成方法については、「場所の作成と管理」を **[参照してください](managing-locations.md)**。

1. **場所の下に表示を作成**

   1. チャネルレベ **ルの有効化** /ロケーション **/地域に移** 動します ****。
   1. Select **Region** and click **+ Create** from the action bar.
   1. ウィザー **ドで** 「Display」を選択し、「RegionDisplay」という名前の表示を作成 **します。**
   ![screen_shot_2018-11-27at112216am](assets/screen_shot_2018-11-27at112216am.png)

1. **表示するチャネルの割り当て**

   MainAdChannel **の場合：**

   1. Channel Level Activation **/** Locations **/** Region **/** RegionRegionに移動します。Channel Level Activation/ **Locations****** /RegionDisplayDisplayDisplayDisplayDisplayDisplayDisplayActionBarに移動します。
   1. **チャネル割り当て**&#x200B;ダイアログボックスが開きます。
   1. Select **Reference Channel**.. by path.
   1. [チャネルパス] **を[チャネル** Level Activation **] —&gt; [チャネル** ] —&gt; [メインadChannel] ************&#x200B;を選択します。
   1. チャネル **の役割は** 、mainadchannelとして設定 **されます**。
   1. 優先度を **** 1に **します**。
   1. Select the **Supported Events** as **Initial Load** and **Idle Screen**.
   1. 「**保存**」をクリックします。
   ![screen_shot_2018-11-27at124626pm](assets/screen_shot_2018-11-27at124626pm.png)

   >[!NOTE]
   >
   >表示ダッシュボードからチャネルを割り当てるには、[ **Channel Level Activation** —&gt;場所 **—&gt;場所** —&gt;地域クリック地域ダッシュボードアクションバーのダッシュボードクリック地域に移動し ************ ます。 [割り当て **られたチャネル** &amp;スケジュール]パネルで[ **+チャネルの割り当て** ]をクリックします。

   同様に、チャネルTargetedSinglePlay **をdisplay** **に割り当てます。

   1. [チャネルレベルのアクテ **ィブ化** ] **—&gt;** —&gt; **Region** —&gt; **Region —領域クリックアクションバーからチャネルのディスプレ****** イを割り当てる] [チャネルレベルのアクティブ化]に移動します。
   1. **チャネル割り当て**&#x200B;ダイアログボックスが開きます。
   1. Select **Reference Channel**.. by path.
   1. [チャネル **パス** ]を[チャネ **ルレベルのアクティブ化*** —&gt;チャネル ***—&gt;ターゲッ*********&#x200B;トのSinglePlay ]として選択します。
   1. チャネ **ルの役割は** 、対象となるSingleplayとして **設定されます**。
   1. [優先度] **を** 2に設 **定します**。
   1. 図に示すように、 **Supported Eventsを** Initial ****、 **Idle Screen** Timer **Load、およびTimer** Loadとして選択します。
   1. アクティブな日付 **を** 2018年11月27日午後11時59分から選択し、アクティブな日付を2018年11 **月** 28日午前12時5分まで選択します。
   1. 「**保存**」をクリックします。
   >[!CAUTION]
   TargetedSinglePlayチャネルの優先度を **MainAdSegment** チャネルよりも高く設定する必要が **あります** 。

   ![screen_shot_2018-11-27at31206pm](assets/screen_shot_2018-11-27at31206pm.png)

   >[!NOTE]
   同じ日を選択するには、次の日を選択し、手動で同じ日付を後で編集する必要があります。 これにより、ユーザーが過去の日付を選択するのを制限します。 以下の例を参照してください。

   ![new1](assets/new1.gif)

## 結果の表示 {#viewing-the-results}

チャネルの設定と表示が完了したら、AEM Screensプレーヤーを起動してコンテンツを表示してください。

プレイヤーが **MainAdChannelのコンテンツを表示し、(スケジュールに設定されたとおりに** )午後11時59分に、 **TargetedSinglePlay** チャネルはコンテンツを午前12時5分まで表示し、その後 **MainAdChannelは再びコンテンツの再生を再開します** 。

>[!NOTE]
AEM Screen playerについて詳しくは、次のリソースを参照してください。
* [AEM Screens playerのダウンロード](https://download.macromedia.com/screens/)
* [AEM Screens playerの操作](working-with-screens-player.md)

