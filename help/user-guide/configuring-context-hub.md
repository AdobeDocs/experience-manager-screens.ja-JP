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
source-git-commit: 9b54b153676852742859b704ac9aedf908fceecf
workflow-type: tm+mt
source-wordcount: '1531'
ht-degree: 100%

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
>
>次の例は、値が 100 を超えるか 50 未満の場合にアセットの変更をトリガーするデータストアとしての Google シートを示しています。

## 手順 2：ストア設定のセットアップ {#step-setting-store-configurations}

1. **ContextHub に移動する**

   AEM インスタンスに移動し、左側のサイドバーにあるツールアイコンをクリックします。**サイト**／**ContextHub** をクリックします（下図を参照）。

   ![画像](/help/user-guide/assets/context-hub/context-hub3.png)

1. **新しい ContextHub ストア設定の作成**

   1. 「**screens**」という設定コンテナに移動します。

   1. **作成**／**設定コンテナを作成**&#x200B;をクリックし、タイトルに「**ContextHubDemo**」と入力します。

      ![画像](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **ContextHubDemo**／**作成**／**ContextHub 設定**&#x200B;に&#x200B;**移動**&#x200B;し、「**保存**」をクリックします。

      >[!NOTE]
      >
      > 「**保存**」をクリックすると、**ContextHub 設定**&#x200B;画面が開きます。

   1. **ContextHub 設定**&#x200B;画面で、**作成**／**ContentHub ストア設定**&#x200B;をクリックします。

      ![画像](/help/user-guide/assets/context-hub/context-hub5.png)

      >[!CAUTION]
      >
      >AEM 6.5 機能パック 4 または AEM 6.4 機能パック 8 の一部として、`/conf/screens/settings/cloudsettings` を `sling:Folder` に更新する必要があります。
      >
      >その場合は、次の手順に従います。
      >
      >1. CRXDE Lite に移動してから`/conf/screens/settings/cloudsettings`に移動します。
      >1. `cloudsettings jcr:primaryType` が `sling:Folder` にあるかどうかを確認します。`jcr:primaryType` が `sling:folder` にない場合は、次の手順に進みます。
      >1. `/conf/screens/settings` を右クリックし、「*名前*」が「**cloudsettings1**」、「*タイプ*」が「**sling:Folder**」の新しいノードを作成して、変更内容を保存します。
      >1. `/conf/screens/settings/cloudsettings` の下のすべてのノードを `cloudsettings1` に移動します。
      >1. `cloudsettings` を削除して保存します。
      >1. `cloudsettings1` を `cloudsettings` に名前変更して保存します。
      >1. これで、/conf/screens/settings/cloudsettings に `jcr:primaryType` が `sling:Folder` として含まれるようになります。
      >
      >アップグレードの前後に、オーサーとパブリッシュで以上の手順を実行する必要があります。

   1. 「**タイトル**」に「**Google Sheets**」、「**ストア名**」に「**googlesheets**」、「**ストアの種類**」に「**contexthub.generic-jsonp**」と、それぞれ入力して、「**次へ**」をクリックします。

      >[!CAUTION]
      >
      >Adobe Experience Manager（AEM）6.4 を使用している場合は、「**構成タイトル**」を「**googlesheets**」、「**ストアタイプ**」を「**contexthub.generic-jsonp**」として入力します。

      ![画像](/help/user-guide/assets/context-hub/context-hub6.png)

   1. 固有の JSON 設定を入力します。例えば、次の JSON をデモ用に使用し、「**保存**」をクリックすると、ContextHub 設定に「**Google Sheets**」という名前のストア設定が表示されます。

      >[!IMPORTANT]
      >
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
      >
      >上記のサンプルコードで、**pollInterval** は、値が更新される頻度をミリ秒単位で定義します。
      >上記の JSON コードの該当するプレースホルダーを、Google シートのセットアップ時に取得した実際の *&lt;シート ID>* と *&lt;API キー>* に置き換えます。

      >[!CAUTION]
      >
      >Google シートのストア設定をグローバルフォルダー以外（例えば、独自のプロジェクトフォルダー内など）で作成した場合、ターゲティングは初期状態では機能しません。


1. **ストアのセグメント化の設定**

   1. 「**ContentHub ストア設定**」に移動して、screens 設定コンテナで別のストア設定を作成し、「**タイトル**」に「**segmentation-contexthub**」、「**ストア名**」に「**segmentation**」、「**ストアの種類**」に「**aem.segmentation**」と入力します。

      ![画像](/help/user-guide/assets/context-hub/context-hub7.png)

   1. 「**次へ**」、「**保存**」の順にクリックします。

      >[!NOTE]
      >
      >json を定義するプロセスをスキップし、空白のままにしておく必要があります。


## 手順 3：オーディエンスのセグメントのセットアップ {#setting-up-audience}

1. **オーディエンスにセグメントを作成する**

   1. AEM インスタンスで、**パーソナライゼーション**／**オーディエンス**／**Screens** に移動します。

   1. **作成**／**Context Hub セグメントを作成**&#x200B;をクリックします。**新しい ContextHub セグメント**&#x200B;ダイアログボックスが開きます。

   1. 「**タイトル**」に「**Higherthan50**」と入力し、「**作成**」をクリックします。同様に、「**Lowerthan50**」というタイトルの別のセグメントを作成します。

      ![画像](/help/user-guide/assets/context-hub/context-hub11.png)

   1. **Higherthan50** セグメントを選択し、アクションバーの「**プロパティ**」をクリックします。

      ![画像](/help/user-guide/assets/context-hub/context-hub12.png)

   1. **セグメントプロパティ**&#x200B;から「**パーソナライゼーション**」タブを選択します。次の図に示すように、「**ContextHub のパス**」を `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations`、「**セグメントのパス**」を `/conf/screens/settings/wcm/segments` に設定し、「**保存**」をクリックします。

      ![画像](/help/user-guide/assets/context-hub/context-hub13.png)

   1. 同様に、**Lowerthan 50** セグメントの「**ContextHub のパス**」と「**セグメントのパス**」を設定します。

## 手順 4：ブランドと領域の設定 {#setting-brand-area}

次の手順に従って、アクティビティにブランドを、ブランドの下に領域を作成します。

1. **アクティビティにブランドを作成する**

   1. AEM インスタンスで、**パーソナライゼーション**／**アクティビティ**&#x200B;に移動します。

   1. **作成**／**ブランドを作成**&#x200B;をクリックします。

   1. **ページを作成**&#x200B;ウィザードから「**ブランド**」を選択し、「**次へ**」をクリックします。

   1. 「**タイトル**」に「**ScreensBrand**」と入力し、「**作成**」をクリックします。これで、以下のようにブランドが作成されました。

      ![画像](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      >
      >既知の問題：

領域を追加するには、URL（例えば下記）から「master」を削除します。
      `http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`

1. **ブランドに領域を作成する**

   以下の手順に従って、ブランドに領域を作成します。

   1. 「**作成**」、「**領域を作成**」を順にクリックします。

      ![画像](/help/user-guide/assets/context-hub/context-hub9.png)

   1. **ページを作成**&#x200B;ウィザードから「**領域**」を選択し、「**次へ**」をクリックします。

   1. 「**タイトル**」に「**ScreensValue**」と入力し、「**作成**」をクリックします。これで、ブランドに領域が作成されます。

## 手順 5：アクティビティのセグメントの作成 {#step-setting-up-audience-segmentation}

データストアを設定し、アクティビティ（ブランドと領域）を定義したら、次の手順に従ってアクティビティにセグメントを作成します。

1. **アクティビティにセグメントを作成する**

   1. AEM インスタンスで、**パーソナライゼーション**／**アクティビティ**／**ScreensBrand**／**ScreensValue** に移動します。

   1. **作成**／**アクティビティを作成**&#x200B;をクリックします。**アクティビティの設定**&#x200B;ウィザードが開きます。

   1. 「**タイトル**」に「**ValueCheck50**」、「**名前**」に「**valuecheck50**」と入力します。「**ターゲットエンジン**」ドロップダウンから「**ContextHub(AEM)**」を選択し、「**次へ**」をクリックします。

      ![画像](/help/user-guide/assets/context-hub/context-hub14.png)

   1. **アクティビティを設定**&#x200B;ウィザードで「**エクスペリエンスを追加**」をクリックします。

   1. 「**オーディエンス**」から「**Higherthan50**」を選択し、「**エクスペリエンスを追加**」をクリック、「**タイトル**」に「**higherthan50**」、「**名前**」に「**higherthan50**」と入力します。「**OK**」をクリックします。

   1. 「**オーディエンス**」から「**Lowerthan50**」を選択し、「**エクスペリエンスを追加**」をクリック、「**タイトル**」に「**lowerthan50**」、「**名前**」に「**lowerthan50**」と入力します。「**OK**」をクリックします。

      ![画像](/help/user-guide/assets/context-hub/context-hub15.png)

   1. 「**次へ**」、「**保存**」の順にクリックします。**ValueCheck50** アクティビティが作成され、設定されました。

      ![画像](/help/user-guide/assets/context-hub/context-hub16.png)

## 手順 5：オーディエンスのセグメントの編集{#editing-audience-segmentation}

1. **セグメントを編集する**

   1. AEM インスタンスで、**パーソナライゼーション**／**オーディエンス**／**Screens** に移動します。

   1. **Higherthan50** セグメントを選択し、アクションバーの「**編集**」をクリックします。

   1. **比較 : プロパティ - 値**&#x200B;コンポーネントをエディターにドラッグ＆ドロップします。

   1. レンチアイコンをクリックして、**プロパティと値の比較**&#x200B;ダイアログボックスを開きます。

   1. 「**プロパティ名**」のドロップダウンから「**googlesheets/value/1/0**」を選択します。

      >[!NOTE]
      >
      >**googlesheets/value/1/0** は、下図のように、Google シートの 1 列目の 2 行目に入力された値を参照します。

      ![画像](/help/user-guide/assets/context-hub/context-hub17.png)

   1. 「**演算子**」のドロップダウンメニューから「**次よりも大きい**」を選択します。

   1. 「**値**」に「**70**」を入力します。

      >[!NOTE]
      >
      >AEM で Google シートのデータが検証されると、セグメントが緑色で表示されます。

      ![画像](/help/user-guide/assets/context-hub/context-hub18.png)
   同様に、プロパティ値を **Lowerthan50** へと編集します。

   1. **比較 : プロパティ - 値**&#x200B;コンポーネントをエディターにドラッグ＆ドロップします。

   1. レンチアイコンをクリックして、**プロパティと値の比較**&#x200B;ダイアログボックスを開きます。

   1. 「**プロパティ名**」のドロップダウンから「**googlesheets/value/1/0**」を選択します。

   1. 「**演算子**」のドロップダウンメニューから「**次よりも小さい**」を選択します。

   1. 「**値**」に「**50**」と入力します。



## チャネルでのターゲティングの有効化 {#step-enabling-targeting-in-channels}

以下の手順に従って、チャネルでターゲティングを有効にします。

1. AEM Screens チャネルのいずれかに移動します。以下の手順は、AEM Screens チャネルに作成した **DataDrivenChannel** を使用してターゲティングを有効にする方法を示しています。

1. **TargetChannel** チャネルを選択し、アクションバーの「**プロパティ**」をクリックします。

   ![画像](/help/user-guide/assets/context-hub/context-hub19.png)

1. 「**パーソナライズ機能**」タブを選択して、ContextHub 設定をセットアップします。

   1. 「**ContextHub パス**」を `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` に設定、「**セグメントパス**」を `/conf/screens/settings/wcm/segments` に設定して、「**保存**」をクリックします。

   1. 「**保存して閉じる**」をクリックします。

      >[!NOTE]
      >
      >ContextHub 設定とセグメントをそれぞれ最初に保存した、Context Hub とセグメントのパスを使用します。

      ![画像](/help/user-guide/assets/context-hub/context-hub20.png)

   1. **TargetChannel** チャネルに移動して選択し、アクションバーの「**編集**」をクリックします。

      >[!NOTE]
      >
      >すべてを正しくセットアップしたら、下図に示すように、エディターのドロップダウンに「**ターゲティング**」オプションが表示されます。

      ![画像](/help/user-guide/assets/context-hub/context-hub21.png)

## 詳細情報：使用例 {#learn-more-example-use-cases}

AEM Screens プロジェクトに ContextHub を設定したら、以下の様々な使用例を通じて、データでトリガーされるアセットが様々な業界でいかに重要な役割を果たしているかを理解できます。

1. **[小売店向けの在庫に応じたアクティベーション](retail-inventory-activation.md)**
1. **[旅行センター向けの気温に応じたアクティベーション](local-temperature-activation.md)**
1. **[接客業向けの予約状況に応じたアクティベーション](hospitality-reservation-activation.md)**
