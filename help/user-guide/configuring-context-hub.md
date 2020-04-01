---
title: AEM Screens プロジェクトでの ContextHub の設定
seo-title: AEM Screens プロジェクトでの ContextHub の設定
description: ここでは、データでトリガーされるコンテンツ変更のためのデータストアを定義するターゲティングエンジンの ContextHub について説明します。
seo-description: ここでは、データでトリガーされるコンテンツ変更のためのデータストアを定義するターゲティングエンジンの ContextHub について説明します。
uuid: be06bda8-7de9-40d6-a84b-5ed8d8b3d180
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
discoiquuid: 9a26b5cd-b957-4df7-9b5b-f57e32b4196a
docset: aem65
translation-type: tm+mt
source-git-commit: 65a94a5301e4f15979d198f90a2ffc75c8e34a8a

---


# AEM Screens プロジェクトでの ContextHub の設定 {#configuring-contexthub-in-aem-screens}

ここでは、データストアを使用したデータ主導型アセット変更の作成と管理について重点的に説明します。

## キーワード {#key-terms}

AEM Screens プロジェクトの在庫主導型チャネルを作成および管理する方法の詳細に立ち入る前に、様々なシナリオに関連する重要なキーワードをいくつか理解しておく必要があります。

**ブランド**：プロジェクトの概要を指します。

**領域**：「Digital Ad Signage」などの AEM Screens プロジェクト名を指します。

**アクティビティ**：在庫主導型、天候主導型、部門稼働状況主導型などのルールカテゴリを定義します。

**オーディエンス**：ルールを定義します。

**セグメント**：温度が華氏 50 度を下回った場合はスクリーンにホットコーヒーの画像を表示し、それ以外の場合は冷たい飲み物の画像を表示するといった一定のルールで再生するアセットのバージョンを指します。

以下の図は、ContextHub 設定がアクティビティ、オーディエンス、チャネルと一致する様子を視覚的に示しています。

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## 前提条件 {#preconditions}

AEM Screens プロジェクト用に Context Hub の設定を開始する前に、（デモ用に）Google シートをセットアップする必要があります。

>[!CAUTION]
>
>次の例では、値の取得先となるサンプルデータベースシステムとして Google シートを使用していますが、この Google シートはあくまで教育用のものです。アドビでは、実稼働環境への Google シートの使用はお勧めしません。
>
>詳しくは、Google ドキュメントの [Get an API Key](https://developers.google.com/maps/documentation/javascript/get-api-key) を参照してください。


## 手順 1：データストアのセットアップ {#step-setting-up-a-data-store}

データストアは、ローカル I/O イベントまたはローカルデータベースイベントとして設定できます。

次のアセットレベルのデータトリガーの例は、AEM ScreensチャネルへのContextHub設定とセグメントパスを使用できるExcelシートなどのデータストアを設定するローカルデータベースイベントを示しています。

次に示すように、Googleシートを正しく設定します。

![画像](/help/user-guide/assets/context-hub/context-hub1.png)

次の検証は、接続を確認する際に、次の形式で *googleシートIDと* APIキーの2つの値を入力すると ** 表示されます。

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![画像](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
> 次の例は、値が100を超えるか50を超える場合にアセットの変更をトリガーするデータストアとしてGoogleシートを示しています。

## 手順2:GoogleシートのAEMインスタンスへの接続 {#step-connecting-aem-instance}

1. **ContextHub に移動する**

   AEM インスタンスに移動し、左側のサイドバーにあるツールアイコンをクリックします。**サイト**／**ContextHub** をクリックします（下図を参照）。

   ![画像](/help/user-guide/assets/context-hub/context-hub3.png)

1. **新しい ContextHub ストア設定の作成**

   1. 「画面」という設定コンテナに移動 **します**。

   1. Click **Create** > **Create Configuration Container** and enter the title as **ContextHubDemo**.

      ![画像](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **ContextHubDemo** /CreateContentContentConfiguration **** Save **** Hubをクリックし、 **Save****** Hubをクリックします。

      >[!NOTE]
      > 「保存」をク **リック** すると、 **ContextHub設定画面が開きます** 。

   1. ContextHub設定画面 **で** 、作成/ **** ContentHub Store設定 **をクリックします。**

      ![画像](/help/user-guide/assets/context-hub/context-hub5.png)

   1. **Title** as Google Sheets **,** Google Sheets **,** Store Store Type Store **Store Type Store Type Store Name** Generic-jup Sonp ************ClickClickNameと入力します。
      ![画像](/help/user-guide/assets/context-hub/context-hub6.png)

   1. 固有の JSON 設定を入力します。例えば、次のJSONをデモ用に使用し、「保存」をクリックすると **、ContextHub設定の「** Google Sheets **** 」という名前のストア設定が表示されます。

      >[!IMPORTANT]
      >Make sure to replace the code with your *&lt;Sheet ID>* and *&lt;API Key>*, that you fetched while setting up the Google Sheets.

      ```
       {
        "service": {
        "host": "sheets.googleapis.com",
        "port": 80,
        "path": "/v4/spreadsheets/<your google sheets id>/values/Sheet1",
        "jsonp": false,
        "secure": true,
        "params": {
        "key": "<your Google API key>"
       }
      },
      "pollInterval": 10000
      }
      ```

      >[!NOTE]
      上記のサンプルコードで、**pollInterval** は、値が更新される頻度をミリ秒単位で定義します。上記の JSON コードの該当するプレースホルダーを、Google シートのセットアップ時に取得した実際の *&lt;シート ID>* と *&lt;API キー>* に置き換えます。

      >[!CAUTION]
      Googleシートを作成してグローバルフォルダの外部（独自のプロジェクトフォルダなど）に設定を保存する場合、ターゲット設定は初期状態では機能しません。
   >In case, you want to configure the Google Sheets store configurations outside the global folder, then you should must set the **Store Name** as **segmentation** and **Store Type** as **aem.segmentation**. さらに、上記の JSON 設定を定義する手順をスキップする必要があります。

1. **アクティビティにブランドを作成する**

   1. AEM インスタンスで、**パーソナライゼーション**／**アクティビティ**&#x200B;に移動します。

   1. **作成**／**ブランドを作成**&#x200B;をクリックします。

   1. **ページを作成**&#x200B;ウィザードから「**ブランド**」を選択し、「**次へ**」をクリックします。

   1. 「**タイトル**」に「**ContextHubDemo**」と入力し、「**作成**」をクリックします。これで、以下のようにブランドが作成されました。
   ![screen_shot_2019-05-05at44305pm](assets/screen_shot_2019-05-05at44305pm.png)


   >[!CAUTION]
   既知の問題：
   領域を追加するには、URL（例えば下記）から「master」を削除します。
   `https://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/contexthubdemo/master`

1. **ブランドに領域を作成する**

   以下の手順に従って、ブランドに領域を作成します。

   1. 「**作成**」、「**領域を作成**」を順にクリックします。

   1. **ページを作成**&#x200B;ウィザードから「**領域**」を選択し、「次へ」をクリックします。

   1. 「**タイトル**」に「**GoogleSheets**」と入力し、「**作成**」をクリックします。これで、アクティビティに領域が作成されます。

## 手順 2：オーディエンスのセグメント化のセットアップ {#step-setting-up-audience-segmentation}

データストアをセットアップし、ブランドを定義したら、以下の手順に従ってオーディエンスセグメントをセットアップします。

1. **オーディエンスにセグメントを作成する**

   1. Navigate from your AEM instance to **Personalization** > **Audiences** > **screens**.

   1. **作成**／**Context Hub セグメントを作成**&#x200B;をクリックします。**新しい ContextHub セグメント**&#x200B;ダイアログボックスが開きます。

   1. 「**タイトル**」に「**SheetA1 1**」と入力し、「**作成**」をクリックします。同様に、「**SheetA2 2**」というタイトルの別のセグメントを作成します。

1. **セグメントを編集する**

   1. Select the segment **Sheets A1 1**, and click **Edit** from the action bar.

   1. **比較 : プロパティ - 値**&#x200B;コンポーネントをエディターにドラッグ＆ドロップします。
   1. レンチアイコンをクリックして、**プロパティと値の比較**&#x200B;ダイアログボックスを開きます。
   1. 「**プロパティ名**」のドロップダウンから「**googlesheets/value/1/0**」を選択します。

   1. 「**演算子**」のドロップダウンメニューから「**次と等しい**」を選択します。

   1. 「**値**」に「**1**」を入力します。
   >[!NOTE]
   AEM で Google シートのデータが検証されると、セグメントが緑色で表示されます。

   ![screen_shot_2019-04-23at20142pm](assets/screen_shot_2019-04-23at20142pm.png)

   同様に、「**SheetA2 2**」セグメントのプロパティ値を編集します。

   1. **比較 : プロパティ - 値**&#x200B;コンポーネントをエディターにドラッグ＆ドロップします。
   1. レンチアイコンをクリックして、**プロパティと値の比較**&#x200B;ダイアログボックスを開きます。
   1. 「**プロパティ名**」のドロップダウンから「**googlesheets/value/1/0**」を選択します。

   1. 「**演算子**」のドロップダウンメニューから「**次と等しい**」を選択します。

   1. 「**値**」に「**2**」を入力します。




## 手順 3：チャネルでのターゲティングの有効化 {#step-enabling-targeting-in-channels}

以下の手順に従って、チャネルでターゲティングを有効にします。

1. AEM Screens チャネルのいずれかに移動します。以下の手順は、AEM Screens チャネルに作成した **DataDrivenRetail** を使用してターゲティングを有効にする方法を示しています。

1. **DataDrivenRetail** チャネルを選択し、アクションバーの「**プロパティ**」をクリックします。

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. 「**パーソナライゼーション**」タブを選択して、ContextHub 設定をセットアップします。

   1. 「**ContextHub のパス**」として **libs**/**settings**/**cloudsettings**/**default**/**ContextHub Configurations** を選択し、「**選択**」をクリックします。

   1. 「**セグメントのパス**」として **conf**/**we-retail**/**settings**/**wcm**/**segments** を選択し、「**選択**」をクリックします。

   1. 「**保存して閉じる**」をクリックします。
   >[!NOTE]
   ContextHub 設定とセグメントをそれぞれ最初に保存した、Context Hub とセグメントのパスを使用します。

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. **DataDrivenAssets**／**チャネル**&#x200B;に移動して「**DataDrivenRetail**」を選択し、アクションバーの「**編集**」をクリックします。

   >[!NOTE]
   すべてを正しくセットアップしたら、下図に示すように、エディターのドロップダウンに「**ターゲティング**」オプションが表示されます。

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

   >[!NOTE]
   チャネルの ContextHub 設定を完了したら、以下のすべての使用例に従う場合は、他の 3 つのシーケンスチャネルについても必ず上記の手順 1～4 に従ってください。

## 詳細情報：使用例 {#learn-more-example-use-cases}

AEM Screens プロジェクトに ContextHub を設定したら、以下の様々な使用例を通じて、データでトリガーされるアセットが様々な業界でいかに重要な役割を果たしているかを理解できます。

1. **[小売店向けの在庫に応じたアクティベーション](retail-inventory-activation.md)**
1. **[旅行センター向けの気温に応じたアクティベーション](local-temperature-activation.md)**
1. **[接客業向けの予約状況に応じたアクティベーション](hospitality-reservation-activation.md)**
