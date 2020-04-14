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
source-git-commit: 358c22018bf933e5b5418f202eb70b1a39a49783

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

>[!IMPORTANT]
>
>次の例では、値の取得先となるサンプルデータベースシステムとして Google シートを使用していますが、この Google シートはあくまで教育用のものです。アドビでは、実稼働環境への Google シートの使用はお勧めしません。
>
>詳しくは、Google ドキュメントの [Get an API Key](https://developers.google.com/maps/documentation/javascript/get-api-key) を参照してください。

## 手順 1：データストアのセットアップ {#step-setting-up-a-data-store}

データストアは、ローカル I/O イベントまたはローカルデータベースイベントとして設定できます。

次のアセットレベルのデータトリガーの例は、AEM Screens チャネルへの ContextHub 設定とセグメントパスを使用できる Excel シートなどのデータストアを設定するローカルデータベースイベントを示しています。

Google シートが正しく設定されると、次のように表示されます。

![画像](/help/user-guide/assets/context-hub/context-hub1.png)

次の検証は、接続を確認する際に、次の形式で *Google シート ID* と *API キー*&#x200B;の 2 つの値を入力すると表示されます。

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![画像](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
> 次の例は、値が 100 を超えるか 50 未満の場合にアセットの変更をトリガーするデータストアとしての Google シートを示しています。

## 手順2:ストア設定の設定 {#step-setting-store-configurations}

1. **ContextHub に移動する**

   AEM インスタンスに移動し、左側のサイドバーにあるツールアイコンをクリックします。**サイト**／**ContextHub** をクリックします（下図を参照）。

   ![画像](/help/user-guide/assets/context-hub/context-hub3.png)

1. **新しい ContextHub ストア設定の作成**

   1. 「**screens**」という設定コンテナに移動します。

   1. **作成**／**設定コンテナを作成**&#x200B;をクリックし、タイトルに「**ContextHubDemo**」と入力します。

      ![画像](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **ContextHubDemo**／**作成**／**ContextHub 設定**&#x200B;に&#x200B;**移動**&#x200B;し、「**保存**」をクリックします。

      >[!NOTE]
      > 「**保存**」をクリックすると、**ContextHub 設定**&#x200B;画面が開きます。

   1. **ContextHub 設定**&#x200B;画面で、**作成**／**ContentHub ストア設定**&#x200B;をクリックします。

      ![画像](/help/user-guide/assets/context-hub/context-hub5.png)

   1. 「**タイトル**」に「**Google Sheets**」、「**ストア名**」に「**googlesheets**」、「**ストアの種類**」に「**contexthub.generic-jsonp**」と、それぞれ入力して、「**次へ**」をクリックします。
      ![画像](/help/user-guide/assets/context-hub/context-hub6.png)

   1. 固有の JSON 設定を入力します。例えば、次の JSON をデモ用に使用し、「**保存**」をクリックすると、ContextHub 設定に「**Google Sheets**」という名前のストア設定が表示されます。

      >[!IMPORTANT]
      >上記の JSON コードの該当するプレースホルダーを、Google シートのセットアップ時に取得した実際の *&lt;シート ID>* と *&lt;API キー>* に必ず置き換えてください。

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
      Google シートのストア設定をグローバルフォルダー以外（例えば、独自のプロジェクトフォルダー内など）で作成した場合、ターゲティングは初期状態では機能しません。

1. **ストアセグメントの設定**

   1. 「 **ContentHub Store Configuration」に移動します。** 画面設定コンテナで別のストア設定を作成し、 **Segmentation** - **contexthub** Name **as** segmentationStore **Store** title as ******** SegmentationStore Store Title aem.

      ![画像](/help/user-guide/assets/context-hub/context-hub7.png)

   1. Click **Next** and then **Save**.

      >[!NOTE]
jsonを定義するプロセスをスキップし、空白のままにする必要があります。


## 手順3:セグメントの設定オーディエンス {#setting-up-audience}

1. **オーディエンスにセグメントを作成する**

   1. AEM インスタンスで、**パーソナライゼーション**／**オーディエンス**／**スクリーン**&#x200B;に移動します。

   1. **作成**／**Context Hub セグメントを作成**&#x200B;をクリックします。**新しい ContextHub セグメント**&#x200B;ダイアログボックスが開きます。

   1. Enter the **Title** as **Higherthan50** and click **Create**. Similarly, create another segment titled as **Lowerthan50**.

      ![画像](/help/user-guide/assets/context-hub/context-hub11.png)

   1. Select the segment **Higherthan50** and click **Properties** from the action bar.
      ![画像](/help/user-guide/assets/context-hub/context-hub12.png)

   1. セグメントプロ **パティ** から「パーソナライゼ **ーション」タブを選択しま**&#x200B;す。 次の図に示すよ **うに、** ContextHub `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` パスを **「パス」と「セグメントパス」に設定し、「保** 存 `/conf/screens/settings/wcm/segments`****」をクリックして、「保存」をクリックします。

      ![画像](/help/user-guide/assets/context-hub/context-hub13.png)

   1. 同様に、 **ContextHub Pathと** Segments Path **for** Lowerthan **** 50セグメントも設定します。

## 手順4:ブランドとエリアの設定 {#setting-brand-area}

次の手順に従って、ブランドをブランドの下のアクティビティと領域に作成します。

1. **アクティビティにブランドを作成する**

   1. AEM インスタンスで、**パーソナライゼーション**／**アクティビティ**&#x200B;に移動します。。

   1. Click **Create** > **Create Brand**.

   1. Select **Brand** from the **Create Page** wizard and click **Next**.

   1. Enter the **Title** as **ScreensBrand** and click **Create**. これで、以下のようにブランドが作成されました。

      ![画像](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      既知の問題：領域を追加するには、URLからマスターを削除します。例えば、
      `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master` です。

1. **ブランドに領域を作成する**

   以下の手順に従って、ブランドに領域を作成します。

   1. 「**作成**」、「**領域を作成**」を順にクリックします。。

      ![画像](/help/user-guide/assets/context-hub/context-hub9.png)

   1. Select **Area** from the **Create Page** wizard and click **Next**.

   1. Enter the **Title** as **ScreensValue** and click **Create**.
ブランドに領域が作成されます。

## 手順5:セグメントのアクティビティ {#step-setting-up-audience-segmentation}

データストアを設定し、アクティビティ（ブランドとエリア）を定義したら、次の手順に従ってアクティビティでセグメントを作成します。

1. **セグメントの作成アクティビティ**

   1. Navigate from your AEM instance to **Personalization** > **Activities** > **ScreensBrand** >**ScreensValue**.

   1. Click **Create** > **Create Activity.** [ **アクティビティの設定** ]ウィザード

   1. タイトルを **ValueCheck50** 、名前 **をvaluecheck50****と******&#x200B;して入力します。 ドロップダ **ウンから** ContextHub(AEM) **としてターゲットエンジンを選択し、「次へ」をクリッ** クします ****。

      ![画像](/help/user-guide/assets/context-hub/context-hub14.png)

   1. 「エクスペリエ **追加ンスを設定」ウィザ** ードで「アクティビティ」をクリックしま ****&#x200B;す。

   1. オーディエンス **** 500より高い値を選択し、「 **Experience** 」をクリックし、「TitleTitle」を「 **TitleTitle」に入力します。** Name **************** 0より高い値をHigherExperienceS500」を選択します。 「**OK**」をクリックします。

   1. オーディエンス **** 50より小さい名前を選択し、「 **50****」をクリックして、「エクスペリエンスのタイトル」を「5」と入力します。「5」を「5」を「5」を「5」「5」「5」を「5」「5」「5」を「****************** 5」 「**OK**」をクリックします。

      ![画像](/help/user-guide/assets/context-hub/context-hub15.png)

   1. Click **Next** and then **Save**. **ValueCheck50アクティビティが作成され** 、設定されました。

      ![画像](/help/user-guide/assets/context-hub/context-hub16.png)

## 手順5:セグメントの編集オーディエンス{#editing-audience-segmentation}

1. **セグメントを編集する**

   1. AEM インスタンスで、**パーソナライゼーション**／**オーディエンス**／**スクリーン**&#x200B;に移動します。

   1. Select the segment **Higherthan50**, and click **Edit** from the action bar.

   1. **比較 : プロパティ - 値**&#x200B;コンポーネントをエディターにドラッグ＆ドロップします。

   1. レンチアイコンをクリックして、**プロパティと値の比較**&#x200B;ダイアログボックスを開きます。

   1. 「**プロパティ名**」のドロップダウンから「**googlesheets/value/1/0**」を選択します。

      >[!NOTE]
Googlesheets **/value/1/0は** 、下図のGoogleシートに入力された行2と列を参照します。

      ![画像](/help/user-guide/assets/context-hub/context-hub17.png)

   1. Select the **Operator** as **greater-than** from the drop-down menu.

   1. 「**値**」に「**70**」を入力します。

      >[!NOTE]
      AEM で Google シートのデータが検証されると、セグメントが緑色で表示されます。

      ![画像](/help/user-guide/assets/context-hub/context-hub18.png)
   同様に、プロパティ値を50より小さい値に **編集します**。

   1. **比較 : プロパティ - 値**&#x200B;コンポーネントをエディターにドラッグ＆ドロップします。

   1. レンチアイコンをクリックして、**プロパティと値の比較**&#x200B;ダイアログボックスを開きます。

   1. 「**プロパティ名**」のドロップダウンから「**googlesheets/value/1/0**」を選択します。

   1. Select the **Operator** as **less-than** from the drop-down menu.

   1. 「**値**」に「**50**」を入力します。



## Enabling Targeting in Channels {#step-enabling-targeting-in-channels}

以下の手順に従って、チャネルでターゲティングを有効にします。

1. AEM Screens チャネルのいずれかに移動します。The following steps demonstrate how to enable targeting by using **DataDrivenChannel** created in an AEM Screens Channel.

1. Select the channel **TargetChannel** and click **Properties** from the action bar.

   ![画像](/help/user-guide/assets/context-hub/context-hub19.png)

1. 「**パーソナライゼーション**」タブを選択して、ContextHub 設定をセットアップします。

   1. ContextHubパスを **Pathに設定し、** Segments Pathを `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` Save **（保存）をク** リッ `/conf/screens/settings/wcm/segments`****&#x200B;クして選択します。

   1. 「**保存して閉じる**」をクリックします。

      >[!NOTE]
      ContextHub 設定とセグメントをそれぞれ最初に保存した、Context Hub とセグメントのパスを使用します。

      ![画像](/help/user-guide/assets/context-hub/context-hub20.png)

   1. Navigate and select the **TargetChannel** channel and click **Edit** from the action bar.

      >[!NOTE]
      すべてを正しくセットアップしたら、下図に示すように、エディターのドロップダウンに「**ターゲティング**」オプションが表示されます。

      ![画像](/help/user-guide/assets/context-hub/context-hub21.png)

## 詳細情報：使用例 {#learn-more-example-use-cases}

AEM Screens プロジェクトに ContextHub を設定したら、以下の様々な使用例を通じて、データでトリガーされるアセットが様々な業界でいかに重要な役割を果たしているかを理解できます。

1. **[小売店向けの在庫に応じたアクティベーション](retail-inventory-activation.md)**
1. **[旅行センター向けの気温に応じたアクティベーション](local-temperature-activation.md)**
1. **[接客業向けの予約状況に応じたアクティベーション](hospitality-reservation-activation.md)**
