---
title: AEM Screens プロジェクトでの ContextHub の設定
description: データストアを定義してデータトリガーコンテンツを変更できるターゲティングエンジンの ContextHub について説明します。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 04072107-d6be-4030-bb79-1f1a7609f37e
source-git-commit: 2b865165793b1c0f90f1351518e41096a57ea2ff
workflow-type: tm+mt
source-wordcount: '1453'
ht-degree: 47%

---

# AEM Screens プロジェクトでの ContextHub の設定 {#configuring-contexthub-in-aem-screens}

ここでは、データストアを使用したデータ主導型アセット変更の作成と管理について重点的に説明します。

## キーワード {#key-terms}

AEM Screensプロジェクトで在庫主導型チャネルを作成および管理する方法の詳細に立ち入る前に、様々なシナリオに関する主な用語をいくつか学習してください。

**ブランド**  — プロジェクトの概要。

**面グラフ** - AEM Screensプロジェクト名（Digital Ad Signage など）

**アクティビティ**  — 在庫主導型、天候主導型、部門稼働状況主導型などのカテゴリルールを定義します。

**対象ユーザ**  — ルールを定義します。

**セグメント**  — 特定のルールで再生するアセットのバージョン。 例えば、温度が華氏 50 度を下回る場合、画面には熱い飲み物の画像が表示され、それ以外の場合は冷たい飲み物が表示されます。

以下の図は、ContextHub 設定がアクティビティ、オーディエンス、チャネルと一致する様子を視覚的に示しています。

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## 前提条件 {#preconditions}

AEM Screens プロジェクト用に Context Hub の設定を開始する前に、（デモ用に）Google シートをセットアップする必要があります。

>[!IMPORTANT]
>
>次の例では、値の取得先となるサンプルデータベースシステムとして Google シートを使用していますが、この Google シートはあくまで教育用のものです。アドビでは、実稼動環境への Google シートの使用はお勧めしません。
>
>詳しくは、Google ドキュメントの [Get an API Key](https://developers.google.com/maps/documentation/javascript/get-api-key) を参照してください。

## 手順 1：データストアのセットアップ {#step-setting-up-a-data-store}

データストアは、ローカル I/O イベントまたはローカルデータベースイベントとして設定できます。

次のアセットレベルのデータトリガーの例は、ContextHub 設定とAEM Screensチャネルへのセグメントパスを使用できる Excel シートなどのデータストアを設定するローカルデータベースイベントを示しています。

次の設定が完了したら、 `google` シートが正しく表示されるようになります。

![画像](/help/user-guide/assets/context-hub/context-hub1.png)

次の検証は、2 つの値を入力して接続を確認すると表示される検証です。 `*google sheet ID*` および `*API key*` を次の形式で入力します。

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![画像](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
>
>次の例は、値が 100 を超える、または 50 未満の場合にアセットが変更されることをトリガーするデータストアとしての Google シートを示しています。

## 手順 2：ストア設定のセットアップ {#step-setting-store-configurations}

1. **ContextHub に移動する**

   AEM インスタンスに移動し、左側のサイドバーにあるツールアイコンをクリックします。クリック **Sites** > **ContextHub**（下の図を参照）。

   ![画像](/help/user-guide/assets/context-hub/context-hub3.png)

1. **ContextHub ストア設定の作成**

   1. 「**screens**」という設定コンテナに移動します。

   1. 選択 **作成** > **設定コンテナを作成** 「タイトル」に「 **ContextHubDemo**.

      ![画像](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **ContextHubDemo**／**作成**／**ContextHub 設定**&#x200B;に&#x200B;**移動**&#x200B;し、「**保存**」をクリックします。

      >[!NOTE]
      > 次を選択した後： **保存**&#x200B;に含まれている場合、 **ContextHub 設定** 画面。

   1. 次から： **ContextHub 設定** 画面、選択 **作成** > **ContentHub ストアの設定**

   ![画像](/help/user-guide/assets/context-hub/context-hub5.png)

   >[!CAUTION]
   >
   >AEM 6.5 機能パック 4 または AEM 6.4 機能パック 8 の一部として、`/conf/screens/settings/cloudsettings` を `sling:Folder` に更新する必要があります。
   >
   >次の手順に従います。
   >
   >1. CRXDE Lite に移動してから`/conf/screens/settings/cloudsettings`に移動します。
   >1. `cloudsettings jcr:primaryType` が `sling:Folder` にあるかどうかを確認します。`jcr:primaryType` が `sling:folder` にない場合は、次の手順に進みます。
   >1. 右クリック `/conf/screens/settings` を使用して、 *名前* as **cloudsettings1** および *タイプ* as **sling:Folder** 変更を保存します。
   >1. `/conf/screens/settings/cloudsettings` の下のすべてのノードを `cloudsettings1` に移動します。
   >1. `cloudsettings` を削除して保存します。
   >1. `cloudsettings1` を `cloudsettings` に名前変更して保存します。
   >1. ご覧ください `/conf/screens/settings/cloudsettings` 次に該当 `jcr:primaryType` as `sling:Folder`.
   >
   >アップグレードの前または後に、オーサーとパブリッシュで示されている以下の手順に従います。

   1. 「**タイトル**」に「**Google Sheets**」、「**ストア名**」に「**googlesheets**」、「**ストアの種類**」に「**contexthub.generic-jsonp**」と、それぞれ入力して、「**次へ**」をクリックします。

      >[!CAUTION]
      >Adobe Experience Manager（AEM）6.4 を使用している場合は、「**構成タイトル**」を「**googlesheets**」、「**ストアタイプ**」を「**contexthub.generic-jsonp**」として入力します。

      ![画像](/help/user-guide/assets/context-hub/context-hub6.png)

   1. 固有の JSON 設定を入力します。例えば、次の JSON をデモ用に使用し、「 」を選択します。 **保存**. 「 」という名前のストア設定が表示されます。 **Google Sheets** （ContextHub 設定内）

      >[!IMPORTANT]
      >必ず、 `*<Sheet ID>*` および `*<API Key>*`を取得し、Google Sheet のセットアップ時に取得した

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
      >上記のサンプルコードでは、 **pollInterval** は、値の更新頻度をミリ秒単位で定義します。
      >
      >を `*<Sheet ID>*` および `*<API Key>*`を取得し、Google Sheet のセットアップ時に取得した

      >[!CAUTION]
      >
      >Googleシートのストア設定をグローバルフォルダー以外（例えば、独自のプロジェクトフォルダー内など）で作成した場合、ターゲティングは初期設定では機能しません。

1. **ストアのセグメント化の設定**

   1. に移動します。 **ContentHub ストアの設定** AEM Screens設定コンテナで別のストア設定を作成し、 **タイトル** as **segmentation-contexthub**, **ストア名** as **セグメント化** および **ストアの種類** as **aem.segmentation**.

      ![画像](/help/user-guide/assets/context-hub/context-hub7.png)

   1. 「**次へ**」、「**保存**」の順にクリックします。

      >[!NOTE]
      >json を定義するプロセスをスキップし、空白のままにします。


## 手順 3：オーディエンスのセグメントのセットアップ {#setting-up-audience}

1. **オーディエンスにセグメントを作成する**

   1. AEM インスタンスで、**パーソナライゼーション**／**オーディエンス**／**Screens** に移動します。

   1. **作成**／**Context Hub セグメントを作成**&#x200B;をクリックします。**新しい ContextHub セグメント**&#x200B;ダイアログボックスが開きます。

   1. 次を入力します。 **タイトル** as `**Higherthan50**` をクリックします。 **作成**. 同様に、というタイトルの別のセグメントを作成します。 `**Lowerthan50**`.

      ![画像](/help/user-guide/assets/context-hub/context-hub11.png)

   1. セグメントを選択 `**Higherthan50**` をクリックします。 **プロパティ** をクリックします。
      ![画像](/help/user-guide/assets/context-hub/context-hub12.png)

   1. **セグメントプロパティ**&#x200B;から「**パーソナライゼーション**」タブを選択します。次の図に示すように、「**ContextHub のパス**」を `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations`、「**セグメントのパス**」を `/conf/screens/settings/wcm/segments` に設定し、「**保存**」をクリックします。

   ![画像](/help/user-guide/assets/context-hub/context-hub13.png)

   1. 同様に、 **ContextHub のパス** および **セグメントのパス** 対象： `**Lowerthan50**` セグメントに追加します。

## 手順 4：ブランドと領域の設定 {#setting-brand-area}

次の手順に従って、アクティビティにブランドを作成し、ブランドの下の領域にブランドを作成します。

1. **アクティビティにブランドを作成する**

   1. AEMインスタンスからに移動します。 **パーソナライズ** > **アクティビティ**.

   1. 選択 **作成** > **ブランドを作成**.

   1. **ページを作成**&#x200B;ウィザードから「**ブランド**」を選択し、「**次へ**」をクリックします。

   1. 「**タイトル**」に「**ScreensBrand**」と入力し、「**作成**」をクリックします。これで、以下のようにブランドが作成されました。

      ![画像](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      >
      >既知の問題：
      >領域を追加するには、URL からプライマリを削除します（例： ）。
      >`http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`。

1. **ブランドに領域を作成する**

   以下の手順に従って、ブランドに領域を作成します。

   1. 選択 **作成** その後 **領域を作成**.

      ![画像](/help/user-guide/assets/context-hub/context-hub9.png)

   1. 選択 **面グラフ** から **ページを作成** ウィザードと選択 **次へ**.

   1. 次を入力します。 **タイトル** as **ScreensValue** を選択し、 **作成**.
ブランドに領域が作成されます。

## 手順 5：アクティビティのセグメントの作成 {#step-setting-up-audience-segmentation}

データストアを設定し、アクティビティ（ブランドと領域）を定義したら、以下の手順に従ってアクティビティにセグメントを作成します。

1. **アクティビティにセグメントを作成する**

   1. AEM インスタンスで、**パーソナライゼーション**／**アクティビティ**／**ScreensBrand**／**ScreensValue** に移動します。

   1. 選択 **作成** > **アクティビティを作成します。**&#x200B;をクリックします。**アクティビティの設定**&#x200B;ウィザードが開きます。

   1. 「**タイトル**」に「**ValueCheck50**」、「**名前**」に「**valuecheck50**」と入力します。を選択します。 **ターゲティングエンジン** as **ContextHub (AEM)** ドロップダウンから、「 」を選択します。 **次へ**.

      ![画像](/help/user-guide/assets/context-hub/context-hub14.png)

   1. 選択 **エクスペリエンスを追加** から `**Configure Activity**` ウィザード。

   1. 次から： **オーディエンス**&#x200B;を選択し、 `**Higherthan50**` を選択し、 **エクスペリエンスを追加** をクリックし、 **タイトル** as `**higherthan50**` **名前** as `**higherthan50**`. 選択 **OK**.

   1. 次から： **オーディエンス**&#x200B;を選択し、 `**Lowerthan50**` を選択し、 **エクスペリエンスを追加** をクリックし、 **タイトル** as `**lowerthan50**` **名前** as `**lowerthan50**`. 選択 **OK**.

   ![画像](/help/user-guide/assets/context-hub/context-hub15.png)

   1. 選択 **次へ** その後 **保存**. `**ValueCheck50**` アクティビティが作成され、設定されました。

      ![画像](/help/user-guide/assets/context-hub/context-hub16.png)

## 手順 5：オーディエンスのセグメントの編集{#editing-audience-segmentation}

1. **セグメントを編集する**

   1. AEM インスタンスで、**パーソナライゼーション**／**オーディエンス**／**Screens** に移動します。

   1. セグメントを選択 `**Higherthan50**`をクリックし、次を選択します。 **編集** をクリックします。

   1. **比較：プロパティ - 値**&#x200B;コンポーネントをエディターにドラッグ＆ドロップします。

   1. レンチアイコンをクリックして、 **プロパティと値の比較** ダイアログボックス。

   1. 「**プロパティ名**」のドロップダウンから「**googlesheets/value/1/0**」を選択します。

      >[!NOTE]
      > The **googlesheets/value/1/0** は、 `google` シートを次の図に示します。

      ![画像](/help/user-guide/assets/context-hub/context-hub17.png)

   1. 「**演算子**」のドロップダウンメニューから「**次よりも大きい**」を選択します。

   1. 「**値**」に「**70**」を入力します。

      >[!NOTE]
      >
      >AEM で Google シートのデータが検証されると、セグメントが緑色で表示されます。

      ![画像](/help/user-guide/assets/context-hub/context-hub18.png)

   同様に、プロパティ値を `**Lowerthan50**`.

   1. **比較：プロパティ - 値**&#x200B;コンポーネントをエディターにドラッグ＆ドロップします。

   1. レンチアイコンを選択します。

   1. Adobe Analytics の **プロパティと値の比較** ダイアログボックスで、次の項目を選択します。 **googlesheets/value/1/0** 次に示すドロップダウンから **プロパティ名**.

   1. 「**演算子**」のドロップダウンメニューから「**次よりも小さい**」を選択します。

   1. 「**値**」に「**50**」と入力します。


## チャネルでのターゲティングの有効化 {#step-enabling-targeting-in-channels}

以下の手順に従って、チャネルでターゲティングを有効にします。

1. いずれかのAEM Screensチャネルに移動します。 以下の手順は、AEM Screens チャネルに作成した **DataDrivenChannel** を使用してターゲティングを有効にする方法を示しています。

1. **TargetChannel** チャネルを選択し、アクションバーの「**プロパティ**」をクリックします。

   ![画像](/help/user-guide/assets/context-hub/context-hub19.png)

1. を選択します。 **パーソナライズ** 」タブに移動して、ContextHub 設定をセットアップできます。

   1. 「**ContextHub パス**」を `/conf/screens/settings/wcm/segments` に設定、「**セグメントパス**」を `/conf/screens/settings/wcm/segments` に設定します。
   1. ドロップダウンからブランドを **ScreensBrand**、「**エリア参照を設定**」を **ScreensValue** に設定します。

   1. 「**保存して閉じる**」をクリックします。

      >[!NOTE]
      >
      >ContextHub 設定とセグメントをそれぞれ最初に保存した、Context Hub とセグメントのパスを使用します。

      ![画像](/help/user-guide/assets/context-hub/context-hub20New.png)

   1. **TargetChannel** チャネルに移動して選択し、アクションバーの「**編集**」をクリックします。

      >[!NOTE]
      >
      >すべてを正しく設定している場合は、 **ターゲット設定** 」オプションを選択します（下図を参照）。

      ![画像](/help/user-guide/assets/context-hub/context-hub21.png)

## 詳細情報：使用例 {#learn-more-example-use-cases}

AEM Screens プロジェクトに ContextHub を設定したら、以下の様々な使用例を通じて、データでトリガーされるアセットが様々な業界でいかに重要な役割を果たしているかを理解できます。

1. **[小売店向けの在庫に応じたアクティベーション](retail-inventory-activation.md)**
1. **[旅行センター向けの気温に応じたアクティベーション](local-temperature-activation.md)**
1. **[接客業向けの予約状況に応じたアクティベーション](hospitality-reservation-activation.md)**
