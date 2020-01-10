---
title: 無期限の持ち越しチャネル
seo-title: 無期限の持ち越しチャネル
description: 永続テイクオーバーチャネルを作成する場合は、次の使用例に従います。
seo-description: 特定の日時を通じて継続的に再生する永続的なテイクオーバーチャネルを作成するプロジェクトを設定する場合は、この使用例に従ってください。
contentOwner: jsyal
translation-type: tm+mt
source-git-commit: ba7086ec041f6cfe41d8847b97e97948526cc205

---


# 無期限の持ち越しチャネル {#perpetual-takeover-channel}

次のページでは、特定の日時を通じて継続的に再生する永続的なテイクオーバーチャネルの作成方法に関するプロジェクトの設定を重視する使用例を紹介します。

## 使用例の説明 {#use-case-description}

この使用例は、ディスプレイまたはディスプレイのグループに対し *て通常再生する* チャネルを引き継ぐチャネルを作成する方法を説明します。 買収は、特定の日と時間が絶え間なく行われます。
例えば、毎週金曜日の午前9時から午前10時まで再生する無期限のテイクオーバーチャネルがあります。 この間、他のチャネルは再生されません。 次の例は、継続的なテイクオーバーチャネルを作成して再生し、コンテンツを毎週水曜日の午後2時から午後4時まで2時間再生できるようにします。

### 前提条件 {#preconditions}

この使用例を開始する前に、以下をおこなう方法を理解しておく必要があります。

* **[チャネルの作成と管理](managing-channels.md)**
* **[ロケーションの作成と管理](managing-locations.md)**
* **[スケジュールの作成と管理](managing-schedules.md)**
* **[デバイスの登録](device-registration.md)**

### 主要なアクター {#primary-actors}

コンテンツ作成者

## Setting up the Project {#setting-up-the-project}

次の手順に従って、プロジェクトを設定します。

**チャネルと表示の設定**

1. Create an AEM Screens Project titled as **PerpetualTakeOver**, as shown below.

   ![アセット](assets/p_usecase1.png)

1. Channelsフォルダ **ーに** MainAdChannelを **作成します** 。

   ![アセット](assets/p_usecase2.png)

1. Select the **MainAdChannel** and click **Edit** from the action bar. 一部のアセット（画像、ビデオ、埋め込みシーケンス）をチャンネルにドラッグ&amp;ドロップします。

   ![アセット](assets/p_usecase3.png)


   >[!NOTE]
   >この例 **のMainAdChannelは** 、コンテンツを連続再生するシーケンスチャネルを示します。

1. MainAdChannel内のコンテ **ンツを引き継ぎ****** 、毎週水曜日の午後2時から4時に再生するTakeOverチャネルを作成します。

1. Select the the **TakeOver** and click **Edit** from the action bar. 一部のアセットをチャネルにドラッグ&amp;ドロップします。 次の例は、このチャネルに追加された1つのゾーンイメージを示しています。

   ![アセット](assets/p_usecase4.png)

1. チャネルの場所と表示を設定します。 例えば、次の場所MainLobby **とdisplay mainLobbyDisplayがこのプロ****** ジェクトに設定されます。

   ![アセット](assets/p_usecase5.png)

**ディスプレイへのチャネルの割り当て**

1. 場所フォルダーか **ら表示MainLobbyDisplay** を選 **択します** 。 アクショ **ンバーで[チャネルの割り当て** ]をクリックし、[チャネルの割り当て **** ]ダイアログボックスを開きます。

   >[!NOTE]
   >ディスプレイにチャネルを割り当てる方法については、「チャネルの割り当て」を参 **[照してくださ](channel-assignment.md)**い。

1. チャネル割り当てダイアログボックスに&#x200B;**Save** Assign **Main** Assign Main **Main Assign Main Priority DisplayにChannel Main Priority Ad Supported Events************** Channel Path, Priority, and Supported Events

   * **チャネルパス**:MainAdChannelチャネルへのパスを選 **択**
   * **優先度**:このチャネルの優先順位を1に設定します。
   * **サポートされるイベント**:「 **Initial Load** and **Idle Screen」を選択します**。
   ![アセット](assets/p_usecase6.png)

1. 場所フォルダーから **表示「TakeOver** 」を **選択します** 。 アクショ **ンバーで** [チャネルの割り当て]をクリックして、テイクオーバーチャネルを割り当てます。

1. スケジュールされ **た時刻にTakeOver** チャネルをディスプレイに割り当て、 **Channel Assignment** （チャネルの割り当て）ダイアログボックスから次のフィールドに入力し、「 **Save（保存）」をクリックします**。

   * **チャネルパス**:TakeOverチャネルへのパスを選 **択**
   * **優先度**:このチャネルの優先順位をMainAdChannelよりも大きく設定 **します**。 例えば、この例で設定される優先順位は8です。
   * **サポートされるイベント**:「アイドル画 **面** 」と「タイマー」 **を選択します**。
   * **スケジュール**:このチャネルで表示を実行するスケジュールのテキストを入力します。 この例で説明し **ている** Scheduleのテキストは、14:00 *の後、16:00の前の水曜日です*。
      [!NOTE]
      > スケジュールに追加できる式の詳細については ****、以下の「式の例 [」を参照](#example-expressions) してください。
   * **アクティブ**:開始日時。
   * **アクティブ**:終了日時。
   例えば、 **Schedule** and **active from** and **** active until日時のテキストでは、コンテンツを毎週水曜日の午後2時から午後4時まで再生できます。


   ![アセット](assets/p_usecase7.png)

   次に示すように、 **TakeOver** —> Locations **—>** MainLobby **—> MainMain** DisplayDisplayDashboard **Dashboard** Channelsを優先度を割り当てたチャネルを表示するTakeOver **** —> Locations —> main mainMainLobolobies> Main Main Main Main MainMainDin DisplayDisDisDisDisDisDisDisDisDisDisDisDisDisDisDisDisDisplayDisDisDisDisDisDisDisplayDisplayDisplayDisDisplayDisplayDisplayDisplayDisplayDisplayDisDisplayDisplay

   >[!NOTE]
   >テイクオーバーチャネルの優先順位を最も高く設定する必要があります。

   ![アセット](assets/p_usecase8.png)Nowでは、 **TakeOver****** チャネルがMainAdChannelを2時に2時間、毎週水曜日の午後4時まで引き継ぎ、2020年1月9日から2020年1月31日までコンテンツを再生します。

### Example Expressions {#example-expressions}

次の表に、チャネルを表示に割り当てる際にスケジュールに追加できる式の例を示します。

| **式** | **解釈** |
|---|---|
| 午前8時前 | 毎日午前8時前にチャンネルが演奏される |
| 午後2時以降 | 毎日午後2時以降にチャンネルが再生される |
| 12:15の後12:45以前 | チャネルは毎日午後12時15分後に30分間再生される |
| 12:15の前と12:45の後 | チャネルは毎日午後12:15より前、午後12:45より後に再生される |
| 1月1日午後2時以降、1月2日午後3時前1月3日も | 1月1日の午後12時45分にチャンネルが再生を開始し、1月2日の午前3時まで1日中再生を続ける |
| 1月1日の午後2時以降の2時から2時の間に、1月2日から3時までの間に | 1月1日の午後12時45分に再生を開始し、1月2日の午前3時まで再生を続け、1月2日の午後12時45分に再開し、1月3日の午前3時まで再生を続けます。 |

午前/午後の表記 _(すなわち_ 2:00pm)の代わりに、時刻の表記(14:00)を使用することもできます。
