---
title: 在庫主導型チャネル
seo-title: 在庫主導型チャネル
description: 'null'
seo-description: 'null'
page-status-flag: never-activated
uuid: a7e7aa08-8f9e-4458-bdce-225cf29a6da4
contentOwner: jsyal
discoiquuid: 9989ef4c-9fdd-4bf2-9f7c-0c74a9cc4e7f
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# 在庫主導型チャネル{#inventory-driven-channel}

## 在庫主導型チャネルの使用の手引き {#getting-started-with-inventory-driven-channels}

ここでは、Googleシートを使用したデータ駆動型アセットの変更の作成と管理に重点を置いた使用例について説明します。

### 前提条件 {#preconditions}

この使用事例を開始する前に、以下の方法を理解しておく必要があります。

* **[チャネルの作成と管理](managing-channels.md)**
* **[場所の作成と管理](managing-locations.md)**
* **[スケジュールの作成と管理](managing-schedules.md)**
* **[デバイスの登録](device-registration.md)**

### 主役 {#primary-actors}

コンテンツ作成者

### 用語 {#terminolgies}

以下の用語に従って、様々な用途でのプロジェクトの理解と設定に重要な役割を果たします。

**「アクティビティ** 」はカテゴリを指します。

**Area** Projectメイン

**Audience** Location of the data

**ブランド** ・ブランドの参照

**セグメント** セグメントは、ターゲット設定を行うアセットのコンテナを指します。

### 基本フロー：プロジェクトの設定 {#basic-flow-setting-up-the-project}

>[!NOTE]
>
>**前提条件：**
>
>プロジェクトでのデータ主導型アセットの変更の設定と使用に関する詳細を確認する前に、シーケンスチャネルを含むAEM Screensプロジェクトを作成してください。 デモ用に、 **DataDrivenAssetというプロジェクトを作成し、** DataDrivenRestarant **DataDrivenTextRestarant**、 ************ DataDrivenTextOverlay、DataDataDrivenTextOverlay、WeatherDerivenDataDedDedProjectは小売りプロジェクトを表として、以下に設計画とします。
>
>4つの異なるチャネルを作成するのは、デモ目的と、異なるチャネルで4つの異なる使用例を表示する目的でのみ使用できます。 必要に応じて1つの使用事例のみをフォローする場合は、1つのシーケンスチャネルのみを自由に作成してください。

![screen_shot_2019-05-01at42043pm](assets/screen_shot_2019-05-01at42043pm.png)

AEM ScreensプロジェクトでGoogleシートを使用したデータ駆動型アセットの変更の作成と管理について、以下の節に従ってサンプルプロジェクトを作成します。

## 手順1:データベースの設定 {#step-setting-up-database}

>[!CAUTION]
>
>Googleシートは、値が取得されたデータベースシステムの例で使用されており、ここからは教育目的でのみ使用されます。 アドビでは、実稼働環境でのGoogleシートの使用は推奨しません。
>
>詳しくは、Googleドキュメントの [Get API keyを参照](https://developers.google.com/maps/documentation/javascript/get-api-key) してください。

1. Googleドキュメントにログインします。

   >[!NOTE]
   >
   >新しいGoogleシートを作成する前に、Googleドライブにアカウントが必要です。

1. 新しい空白のスプレッドシートを開始します。 Googleシートにコンテンツを追加して保存します。 デモ用に、Googleシートの名前はContextHubDemoになって **います**。
1. Googleシ **ートの右上隅にある「共有** 」をクリックして、「他のユーザーと共 **有** 」ダイアログボックスを開きます。 下図に **示すように** 、「詳細」オプションをク ****&#x200B;リックし、設定を「オン — リンクを持つ任意のユーザー」に変更します。

   この手順では、Googleシートの値にアクセスできます。

   ![screen_shot_2019-04-22at115829am](assets/screen_shot_2019-04-22at115829am.png)

1. 前の手順で「 **保存** 」をクリックすると、Googleシートのリンクが表示されます。 後で参照するためにクリックを保存し、「完了」をクリ **ックしま**&#x200B;す。

   ![screen_shot_2019-04-22at120242pm](assets/screen_shot_2019-04-22at120242pm.png)

>[!CAUTION]
>
>次の例では、Googleシートを学習目的で使用しています。 アドビでは、実稼働環境でのGoogleシートの使用は推奨しません。

## 手順2:GoogleシートREST APIの有効化 {#step-enabling-the-google-sheets-rest-apis}

Googleシートを設定したら、Google Sheet REST APIを有効にして値にアクセスする必要があります。

GoogleシートでREST APIを有効にする方法については、Google APIのドキュメントを参照してください。

1. 「 [Google API Console」に移動します](https://console.developers.google.com/apis/credentials)。 Click **CREATE** to create a new project.

   ![screen_shot_2019-04-22at125028pm](assets/screen_shot_2019-04-22at125028pm.png)

1. プロジェクト **名をAssetChangeと入力し** 、 **「作成** 」をクリ **ックします**。
1. プロジェクトを作成したら、APIキーを設定する必要があります。 「資格 **情報を作成** 」をクリックし、「**APIキー**」を選択して、プロジェクトのAPIキーを生成します。 APIキーを保存して、今後の参照用にします。

   >[!NOTE]
   >
   >このデモプロジェクトでは、無料のGoogle APIキーを使用します。 詳しくは、GoogleのWebサイト **Get API keyの価格と制限を参照** してください。

### Googleシートの設定の確認 {#verifying-the-setup-of-google-sheets}

```
Verify the data in your Google Sheets using the steps below
```

[https://sheets.googleapis.com/v4/spreadsheets/](https://sheets.googleapis.com/v4/spreadsheets/)&lt;your sheet id&gt;/values/Sheet1?key=&lt;your API key&gt;

次に例を示します。

「** Google Sheets**」リンクが次のような場合： **

`https://docs.google.com/spreadsheets/d/1Ksd125lAsDd0_wnMWgLNUiEpKOUPaok7xfh64s-VO7M/edit?usp=sharing`、

**シートID** : `1Ksd125lAsDd0_wnMWgLNUiEpKOUPaok7xfh64s-VO7M`

**APIキーは** : `AIzaSyAfoANOeLkFCCyohjL8cOdJLhrhGefqEy8`

上記の構文に両方の値を追加します。

`https://sheets.googleapis.com/v4/spreadsheets/1Ksd125lAsDd0_wnMWgLNUiEpKOUPaok7xfh64s-VO7M/values/Sheet1?key=AIzaSyAfoANOeLkFCCyohjL8cOdJLhrhGefqEy8`

これで、シート内のデータを表示できるようになります。

## 手順2:Googleシートのコンテンツを取得するためのAEMの設定 {#step-configuring-aem-to-fetch-the-content-of-the-google-sheets}

次の節では、Googleシートからコンテンツを取得するようにAdobe Experience Manager(AEM)を設定する方法について説明します。

1. AEMインスタンスに移動し、左側のサイドバーにあるツールアイコンをクリックします。 下の図 **に示すように** 、Sites **—&gt;** ContextHubをクリックします。

   ![screen_shot_2019-04-22at53222pm](assets/screen_shot_2019-04-22at53222pm.png)

1. **新しいContextHubストア設定の作成**

   1. グローバル/ **デフォ** ルト **/** ContextHub設定に移 **動します**。

   1. **作成/設定コンテナをクリックし **、タイトルをContextHubDemo*** *と入力します。

   1. **** ContextHubDemo **/****** ContentHub Store Configurationに移動します。構成ウィザードを **開くには**
   1. Titleを **Google Sheets** , **Name**&#x200B;として入力します **。** Google Sheets **********, Nameとして入力します。**
   1. 「**次へ**」をクリックします。
   1. 特定のJSON設定を入力します。 例えば、デモ用に次のJSONを使用できます。
   1. 「**保存**」をクリックします。

   ```
   {
     "service": {
       "host": "sheets.googleapis.com",
       "port": 80,
       "path": "/v4/spreadsheets/<your sheet it>/values/Sheet1",
       "jsonp": false,
       "secure": true,
       "params": {
         "key": "<your API key>"
       }
     },
     "pollInterval": 3000
   }
   ```

   >[!NOTE]
   >
   >上記のサンプルコードで **は** 、pollIntervalは値が更新される頻度をミリ秒単位で定義します。
   >
   >
   >手順1から取得した *&lt;シートID&gt;* お *よび&lt;APIキー&gt;*&#x200B;のコードを置き換 **えます。データベースの設定を参照してください。**

   >[!CAUTION]
   Googleシートを作成して既存のフォルダーの外部（例えば、独自のプロジェクトフォルダー内）に設定を保存した場合、ターゲット設定は初期状態では機能しません。
   Googleシートストアの設定をグローバルレガシーフォルダーの外に設定する場合は、 **Store Nameを** Segmentation **and** Store Typeに **aem.segmentationPoliteとして設定する必要があり******&#x200B;ます。 さらに、上記の定義に従ってjsonを定義するプロセスをスキップする必要があります。

1. **アクティビティでのブランドの作成**

   1. AEMインスタンスからパーソナライゼーション **/アクティビティに移****動します**

   1. **作成**/ブランドを作成をク **リックします**

   1. Select **Brand** from the **Create Page** wizard and click **Next**

   1. Enter the **Title** as **ContextHubDemo** and click **Create**. これで、以下に示すようにブランドが作成されました。
   ![screen_shot_2019-05-05at44305pm](assets/screen_shot_2019-05-05at44305pm.png)

1. 

>[!CAUTION]
既知の問題：
領域を追加するには、URLからマスターを削除します。例えば、
[https://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/contexthubdemo/master](https://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/contexthubdemo/master)

1. ブランドのエリアの作成**

   1. Click **Create** &gt; **Create Area**

   1. Select **Area** from the** Create Page** wizard and click Next

   1. Enter the **Title** as **GoogleSheets** and click **Create**. アクティビティに領域が作成されます。

1. **オーディエンスでのセグメントの作成**

   1. AEMインスタンスから **Personalization** / **Audiences** / **We.Retailに移動します**。
   1. 作成/ **Context** Hubセ **グメントを作成をクリックします**。 新しいContextHubセグメントダイアログボックスが開きます。
   1. Enter the **Title** as **SheetA1 1** and click **Create**. 同様に、「 **SheetA2 2」という名前の別のセグメントを作成します**。

1. **セグメントの編集**

   1. セグメント **Sheets A1 1** （手順5で作成）を選択し、アクションバーの「編集 **** 」をクリックします。

   1. 比較をドラッグ&amp;ドロ **ップ：プロパティ** — エディターの値コンポーネント。
   1. レンチアイコンをクリックして、「 **Comparing a property with value** 」ダイアログボックスを開きます。
   1. 「プ **ロパティ名」のドロップダウンから「googlesheets/value/1/0** 」を選 **択します**。

   1. ドロップダ **ウンメニューから** 「演算子」を「**等しい**」として選択します。

   1. 「値」に **1を入力****します**。
   >[!NOTE]
   AEMは、セグメントを緑色で表示することで、Googleシートのデータを検証します。

   ![screen_shot_2019-04-23at20142pm](assets/screen_shot_2019-04-23at20142pm.png)

   同様に、プロパティ値を **Sheets A1 2に編集します**。

   1. 比較をドラッグ&amp;ドロ **ップ：プロパティ** — エディターの値コンポーネント。
   1. レンチアイコンをクリックして、「 **Comparing a property with value** 」ダイアログボックスを開きます。
   1. 「プ **ロパティ名」のドロップダウンから「googlesheets/value/1/0** 」を選 **択します**。

   1. ドロップダ **ウンメニューから** 「演算子」を「**等しい**」として選択します。

   1. 「値」に **2を入力し** ます ****。
   >[!NOTE]
   前述の手順で適用したルールは、以下の使用例を実装するためのセグメントの設定方法の例に過ぎません。

## 手順3:AEM ScreensチャネルでのContext Hub設定の設定 {#step-setting-up-context-hub-configurations-in-aem-screens-channel}

次の手順に従って、AEM ScreensチャネルへのContextHub設定とセグメントパスを設定します。

1. 前提条件として作成したAEM Screensチャネル(**DataDrivenRetail**)の1つに移動します。
1. チャネル(**DataDrivenRetail**)を選択し、アクションバ **ーで** 「プロパティ」をクリックします。

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. 「パーソナライ **ゼーション** 」タブを選択して、ContextHub設定を設定します。

   1. ContextHub As **** libs **&gt; settings** &gt; settings **settings** &gt; settings **&gt;************** settingsDefault Context Context Click Hub Click Hub Select selectHub Select Select Hubsを選択します。

   1. 「 **Segments Path** as **conf** &gt; **We Retail **&gt; settings &gt; cm **cm** cm &gt; **settings」を選択し、「Segments Path as** conf ********&gt; **We Retail **&gt; settings」を選択します。

   1. 「**保存して閉じる**」をクリックします。
   >[!NOTE]
   コンテキストハブの設定とセグメントを最初に保存したContextHubとセグメントパスを使用します。

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

   >[!NOTE]
   上のダイアログボックスで「 **Targeting Configuration** 」の下の「 **Brand** 」を選択しない場合は、ターゲット設定のプロセスを開始する際に、「Brand」と「Activity」を選択する必要があります。

1. DataDrivenAssetsからDataDrivenRetailに移動し **て選択** /**チャネル**を選択し、アクシ **ョンバーの「編集****** 」をクリックします。

   >[!NOTE]
   すべてを正しく設定した場合は、次の図に示すように、エディターのドロップダウンに **** 「ターゲット設定」オプションが表示されます。

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

   >[!NOTE]
   チャネルにContextHub設定を設定したら、以下のすべての使用例に従う場合は、1 ～ 4の前述の手順に従ってください。他の3つのシーケンスチャネルも同様に設定します。

## 使用例1:小売在庫の有効化 {#use-case-retail-inventory-activation}

次の使用例は、Googleシートの値に基づいて3つの異なる画像を示しています。

### 説明 {#description}

この使用例は、3種類の色付きシャツの小売在庫を示します。 Googleシートに記録されている在庫にあるスウェットシャツの数に応じて、最も多い数の画像（赤、緑、青のスウェットシャツ）が画面に表示されます。

この使用事例では、利用可能なセーターの数が最も多いことに基づいて、赤、緑、青のセーターが画面に表示されます。

### 手順 {#procedure}

小売在庫の有効化の使用例を実装するには、次の手順に従います。

1. **Googleシートの入力**

   1. ContextHubDemo googleシートに移動します。
   1. 3種類のスウェートシャツに対応する値を持つ3つの列（赤、緑、青）を追加します。
   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **要件に従ったオーディエンスの設定**

   1. 手順2の手順(5)で作成したオーディエンスのセグメントに移 ***動します。Googleシートのコンテンツを取得するようにAEMを設定する***)。
   1. 3つの新しいセグ **メントFor_Red**、 **For_Green**、 **For_Blueを追加します**。

   1. 「 **For_Red」を選択し、アク** ションバー **で「編集** 」をクリックします。

   1. 比較をドラッグ&amp;ドロ **ップします。「プロパティ** 」 — プロパティをエディタに追加し、設定アイコンをクリックしてプロパティを編集します。
   1. 「 **First Property name」のドロップダウンから** 「googlesheets/value/1/2」を **選択します。**

   1. ドロップダウ **ンメニューから** 「**より大きい**」を選択します。

   1. 「 **Data Type** 」を「 **number」として選択**

   1. 「 **Second Property name」のドロップダウンから** 「googlesheets/value/1/1」を **選択します。**

   1. **別の比較をドラッグ&amp;ドロップ：プロパティ — プロパティ**をエディタに追加し、設定アイコンをクリックして、プロパティを編集します。
   1. 「 **First Property name」のドロップダウンから** 「googlesheets/value/1/2」を **選択します。**

   1. ドロップダウ **ンメニューから** 「**より大きい**」を選択します。

   1. 「 **Data Type** 」を「 **number」として選択**

   1. 「 **Second Property name」のドロップダウンから** 「googlesheets/value/1/0」を **選択します。**
   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   同様に、次の図に示すように、比較プロパティ **ルールを編集し** 、For_Blueセグメントに追加します。

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   同様に、以下の図に示すように、比較プロパティルールを編集して、** For_Green **segmentに追加します。

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   セグメント **For_Green** と **For_Green**&#x200B;は、Googleシートの値に基づいて、現時点では最初の比較のみが有効なので、データをエディターに読み込むことはできません。

1. **DataDrivenRetail **channel（シーケンスチャネル）に移動して選択し、アクションバーの「 **編集** 」をクリックします。

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   ContextHub設定は、channel **Properties** — **Personalization** **Tabを使用して設定しま****** す。

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   プロジェクトの **ContextHub** Configurations **(上の図を参照)の設定中に「** Targeting ************ （ターゲット設定）」の下にブランドを追加しない場合は、次の手順でブランド設定を選択し、次の手順で開始アクティビティ設定を選択する必要があります。

1. **デフォルト画像の追加**

   1. チャネルにデフォルトの画像を追加し、「ターゲット設定」をクリ **ックしま**&#x200B;す。
   1. ドロップ **ダウンメニューから「ブ** ランド **」と「アクティビティ** 」を選択し、「ターゲット設定を開始」を **クリックします**。

   1. 「**ターゲット設定を開始**」をクリックします。
   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   ターゲット設定を開始する前に、図に示すように、「****+ Experience Targeting **Add Side rail from the side rail」をクリックして、セグメント(** For_Green **、For_Red**、および **For_Blue** )を追加する必要があります。

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. 以下に示すように、画像を3つの異なるスクリーンすべてに追加します。

   ![retail_targeting](assets/retail_targeting.gif)

1. **プレビューの確認**

   1. Click **Preview.** また、Googleシートを開き、値を更新します。
   1. 3つの異なる列の値をすべて変更すると、在庫の最も高い値に応じて表示画像が更新されます。
   ![retail_result](assets/retail_result.gif)

## 使用例2:トラベルセンターの天気有効化 {#use-case-travel-center-weather-activation}

次の使用例は、Googleシートの値に基づいて2つの異なる画像を示しています。

### 説明 {#description-1}

この使用例では、Googleシートの値が50未満の場合、ホットドリンクのある画像が表示され、値が50以上の場合はコールドドリンクのある画像が表示されます。 他の値が存在する場合や値が存在しない場合は、プレーヤーはデフォルトの画像を表示します。

### 手順 {#procedure-1}

以下の手順に従って、AEM Screensプロジェクト用のトラベルセンターの天候アクティブ化の使用例を実装します。

1. **Googleシートの入力**

   1. ContextHubDemo googleシートに移動します。
   1. 温度に対応する値を **持つ列を** Heading1に追加します。
   ![screen_shot_2019-05-08at112911am](assets/screen_shot_2019-05-08at112911am.png)

1. **要件に従って、オーディエンスでのセグメントの設定**

   1. 手順2の手順(5)で作成したオーディエンスのセグメントに移 ***動します。Googleシートのコンテンツを取得するようにAEMを設定する***)。
   1. [シートA1 1 **]を選択し、[編集** ]をクリッ **クします**。

   1. 比較プロパティを選択し、設定アイコンをクリックして、プロパティを編集します。
   1. [プ **ロパティ名]のドロップダウンから** [Googlesheets/value/1/0]を選 **択します。**

   1. ドロッ **プダウン** ・メニューから「演算子」を「**より大きいか等しい**」から選択します。

   1. 値を **** 50と入力 **する**

   1. 同様に、[**シートA1 2 **]を選択し、[編集]をクリック **します**。

   1. 比較プロパティを選択し、設定アイコンをクリックして、プロパティを編集します。
   1. [プ **ロパティ名]のドロップダウンから** [Googlesheets/value/1/0]を選 **択します。**

   1. ドロップダ **ウンメニューから** 「演算子」を「**より小さい**」として選択します。

   1. 値を **** 50と入力 **する**

1. チャネルに移動して選択し()、アクションバ **ーの** 「編集」をクリックします。 次の例では、 **DataDrivenWeather**、順次チャネルを使用して機能を紹介しています。

   >[!NOTE]
   チャネルに既にデフォルトの画像が存在し、手順(3)の説明に従ってオーディエンスが事前設定されている必要があります。

   ![screen_shot_2019-05-08at113022am](assets/screen_shot_2019-05-08at113022am.png)

   >[!CAUTION]
   ContextHub設定は、channel **Properties** — **Personalization** **Tabを使用して設定しま****** す。

   ![screen_shot_2019-05-08at114106am](assets/screen_shot_2019-05-08at114106am.png)

   >[!NOTE]
   プロジェクトの **ContextHub** Configurations **(上の図を参照)の設定中に「** Targeting ************ （ターゲット設定）」の下にブランドを追加しない場合は、次の手順でブランド設定を選択し、次の手順で開始アクティビティ設定を選択する必要があります。

1. エディター **から「ターゲティング** 」を選択し、ドロップダウンメニューから「ブラ **ンド** 」と「アクティビティ」を選択して、「ターゲット設定を開始」をクリ ********&#x200B;ックします。

   >[!NOTE]
   プロジェクトの **ContextHub設定の設定中に****Targeting Configurations** （ターゲット設定）にブランドを追加した場合は、この手順でBrand ActivityとActivityを選択する必要はあ ************ りません。

   ![new_activity3](assets/new_activity3.gif)

1. プレビューの確認

   1. Click **Preview.** また、Googleシートを開き、値を更新します。
   1. この値を50未満に変更すると、夏の飲み物の画像が表示されます。 Googleシートの値が50以上の場合は、ホットドリンクの画像を表示できます。
   ![result3](assets/result3.gif)

## 使用例3:接客予約有効化 {#use-case-hospitality-reservation-activation}

次の使用例は、Googleシートに適用される値と数式に基づいて、2つの異なる画像を示します。

### 説明 {#description-2}

この使用例では、Googleシートに2つのレストラン **Restarant1** と **Restarant2の予約の割合が入力されます**。 Restarant1とRestarant2の値に基づいて数式が適用され、その数式に基づいて、AdTarget列に値1または2が割り当てら **れます** 。

**Restarant1** / **Restarant2**、それ以外の場合は **AdTarget** valueが1、AdTarget ad assigned valueが2と **** なります。 値1はステーキフ *ード* ( *Stake food* )オプションを生成し、値2はタイフフード(Thai food)オプションを表示画面に表示します。

### 手続き型アプローチ {#procedural-approach}

次の手順に従って、AEM Screensプロジェクトにホスピタリティーの予約有効化の使用例を実装します。

1. Googleシートに入力し、数式を追加します。

   例えば、次の図に示すように、3列目の **AdTarget**&#x200B;に数式を適用します。

   ![screen_shot_2019-04-29at94132am](assets/screen_shot_2019-04-29at94132am.png)

1. **要件に従って、オーディエンスでのセグメントの設定**

   1. 手順2の手順(5)で作成したオーディエンスのセグメントに移 ***動します。Googleシートのコンテンツを取得するようにAEMを設定する***)。
   1. [シートA1 1 **]を選択し、[編集** ]をクリッ **クします**。

   1. 比較プロパティを選択し、設定アイコンをクリックして、プロパティを編集します。
   1. [プ **ロパティ名]のドロップダウンから** [Googlesheets/value/1/2]を選 **択します。**

   1. ドロップダウ **ンメニューから** 「演算子」を「**equal **」として選択します。

   1. 値を **** 1と入 **力**

   1. 同様に、[**シートA1 2 **]を選択し、[編集]をクリック **します**。

   1. 比較プロパティを選択し、設定アイコンをクリックして、プロパティを編集します。
   1. [プ **ロパティ名]のドロップダウンから** [Googlesheets/value/1/2]を選 **択します。**

   1. 演算子を **2とし** て選 **択**

1. チャネルに移動して選択し()、アクションバ **ーの** 「編集」をクリックします。 次の例では、DataDrivenRestarantとい **う順次チャネルを使用して**、機能を紹介しています。

   >[!NOTE]
   チャネルには既にデフォルトの画像が存在し、手順(3)の説明に従ってオーディエンスが事前に設定されている必要があります。

   ![screen_shot_2019-05-08at14652pm](assets/screen_shot_2019-05-08at14652pm.png)

   >[!CAUTION]
   ContextHub設定は、channel **Properties** — **Personalization** **Tabを使用して設定しま****** す。

   ![screen_shot_2019-05-08at14903pm](assets/screen_shot_2019-05-08at14903pm.png)

   >[!NOTE]
   プロジェクトの **ContextHub** Configurations **(上の図を参照)の設定中に「** Targeting ************ （ターゲット設定）」の下にブランドを追加しない場合は、次の手順でブランド設定を選択し、次の手順で開始アクティビティ設定を選択する必要があります。

1. エディター **から「ターゲティング** 」を選択し、ドロップダウンメニューから「ブラ **ンド** 」と「アクティビティ」を選択して、「ターゲット設定を開始」をクリ ********&#x200B;ックします。
1. プレビューの確認

   1. Click **Preview.** また、Googleシートを開き、値を更新します。
   1. 「Restarant1」 &gt; 「Restarant2」の値を変更します。ステーキの画像が表示され、「Restarant1 &lt; Restaurant12」が表示されたら、タイ料理の画像が表示画面に表示されます。
   ![result5](assets/result5.gif)

## 使用例4:デジタルメニューボードテキストオーバーレイ {#use-case-digital-menu-board-text-overlay}

以下の使用例は、レストランやファストフードのジョイントで一般的なデジタルメニューボードの使用例を示しています。

### 説明 {#description-3}

次の使用例では、順次チャネルでのテキストオーバーレイの使用方法、およびGoogleシートで価格の値が更新され、テキストオーバーレイコンポーネントの更新で更新がトリガーされる方法について説明します。

### 手続き型アプローチ {#procedural-approach-1}

AEM Screensプロジェクトにテキストオーバーレイの使用例を含むデジタルメニューボードを実装するには、次の手順に従います。

1. **Googleシートの入力**

   1. Googleシートに移動します。
   1. 下の図に示すように、ユースケースの価格設定値を含む列を追加します。
   ![screen_shot_2019-05-05at11344am](assets/screen_shot_2019-05-05at111344am.png)

1. **シーケンスチャネルへの画像の追加**

   1. チャネル(**DataDrivenAssets** —&gt; **Channels** —&gt; **DataDrivenTextOverlay**)に移動して選択します。

   1. アクションバーから「**編集**」をクリックして、エディターを開きます。
   1. Appleの円グラフ画像をエディターにドラッグ&amp;ドロップします。
   ![screen_shot_2019-05-05at112933am](assets/screen_shot_2019-05-05at112933am.png)

1. **画像へのテキストオーバーレイの追加**

   1. エディターで画像を選択し、「設定」をクリックします。
   1. 「テキストオーバ **ーレイ** 」タブに移動し、テキストオーバーレイを画像に追加します。 Googleシートから値を取得するには、値が波線で囲まれていることを確認します。 例えば、価格はGoogleシートから取得され、テキストオーバーレイの定義時に **{price}** と表記されます。

   1. 「 **ContextHub** 」タブに移動し、以下の図に示すように、Googleシートから取得する値を設定します。
   ![textoverlay_result](assets/textoverlay_result.gif)

1. **プレビューの確認**

   <!-- Edit text in steps below. wonky-->

   1. Click **Preview**.  また、Googleシートを開き、値を更新します。
   1. 「価格」の下の値 **を変更すると** 、次の図に示すように、テキストオーバーレイで使用されている値がそれに応じて更新されます。
   ![textoverlay_result-1](assets/textoverlay_result-1.gif)
