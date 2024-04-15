---
title: AEM Screens プロジェクトでの ContextHub の設定
description: データトリガーのコンテンツの変更用にデータストアを定義できるように、ターゲティングエンジンの ContextHub について説明します。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
content-type: reference
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 04072107-d6be-4030-bb79-1f1a7609f37e
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '1445'
ht-degree: 36%

---

# AEM Screens プロジェクトでの ContextHub の設定 {#configuring-contexthub-in-aem-screens}

この節では、データストアを使用したデータ駆動型アセットの変更の作成と管理に重点を置いて説明します。

## キーワード {#key-terms}

AEM Screens プロジェクトでの在庫駆動型チャネルの作成と管理の詳細を説明する前に、様々なシナリオに対する重要な用語の一部を学びます。

**ブランド**  – 大まかなプロジェクト説明。

**領域** - デジタル広告サイネージなど、AEM Screens プロジェクトの名前

**Activity**  – 在庫主導、天候主導、部門可用性主導などのカテゴリルールを定義します。

**対象読者**  – 規則を定義します。

**セグメント**  – 指定されたルールで再生されるアセットのバージョン。 例えば、温度が華氏 50 度を下回る場合、画面には温かい飲み物、それ以外の場合は冷たい飲み物の画像が表示されます。

以下の図は、ContextHub 設定がアクティビティ、オーディエンス、チャネルと一致する様子を視覚的に示しています。

![screen_shot_2019-05-29at53729pm](assets/screen_shot_2019-05-29at53729pm.png)

## 前提条件 {#preconditions}

AEM Screens プロジェクトの Context Hub 設定の指定を開始する前に、Google Sheets を設定します（デモ用）。

>[!IMPORTANT]
>
>次の例では、値の取得先となるサンプルデータベースシステムとして Google シートを使用していますが、この Google シートはあくまで教育用のものです。アドビでは、実稼動環境への Google シートの使用はお勧めしません。
>
>詳しくは、を参照してください [API キーを取得](https://developers.google.com/maps/documentation/javascript/get-api-key) （Google ドキュメント）。

## 手順 1：データストアのセットアップ {#step-setting-up-a-data-store}

データストアは、ローカル I/O イベントまたはローカルデータベースイベントとして設定できます。

次のアセットレベルのデータトリガーの例では、ContextHub 設定を使用し、AEM Screens チャネルへのパスをセグメント化できる Excel シートなどのデータストアを設定するローカルデータベースイベントを示しています。

を設定したら、 `google` 次の例に示すように、正しくシート化します。

![画像](/help/user-guide/assets/context-hub/context-hub1.png)

次の検証は、2 つの値を入力して接続を確認する場合に表示するものです。 `*google sheet ID*` および `*API key*` 以下の形式で指定します。

`https://sheets.googleapis.com/v4/spreadsheets/<your sheet id>/values/Sheet1?key=<your API key>`

![画像](/help/user-guide/assets/context-hub/context-hub2.png)

>[!NOTE]
>
>次の具体的な例では、値が 100 より大きい場合または 50 未満の場合にアセットの変更をトリガーするデータストアとしての Google Sheets を示しています。

## 手順 2：ストア設定のセットアップ {#step-setting-store-configurations}

1. **ContextHub に移動する**

   AEM インスタンスに移動し、左サイドバーのツールアイコンを選択します。 を選択 **Sites** > **ContextHub**&#x200B;を参照してください（下図を参照）。

   ![画像](/help/user-guide/assets/context-hub/context-hub3.png)

1. **ContextHub ストア設定の作成**

   1. 「**screens**」という設定コンテナに移動します。

   1. を選択 **作成** > **設定コンテナの作成** タイトルに「」と入力します **ContextHubDemo**.

      ![画像](/help/user-guide/assets/context-hub/context-hub4.png)

   1. **移動** 対象： **ContextHubDemo** > **作成** **ContentHub 設定** を選択して、 **保存**.

      >[!NOTE]
      > を選択した後 **保存**&#x200B;が表示されます **ContextHub 設定** 画面。

   1. から **ContextHub 設定** 画面、選択 **作成** > **ContentHub ストアの設定**

   ![画像](/help/user-guide/assets/context-hub/context-hub5.png)

   >[!CAUTION]
   >
   >AEM 6.5 機能パック 4 または AEM 6.4 機能パック 8 の一部として、`/conf/screens/settings/cloudsettings` を `sling:Folder` に更新する必要があります。
   >
   >次の手順に従います。
   >
   >1. CRXDE Lite に移動してから`/conf/screens/settings/cloudsettings`に移動します。
   >1. `cloudsettings jcr:primaryType` が `sling:Folder` にあるかどうかを確認します。`jcr:primaryType` が `sling:folder` にない場合は、次の手順に進みます。
   >1. 右クリック `/conf/screens/settings` を使用してノードを作成します。 *名前* as **`cloudsettings1`** および *タイプ* as **`sling:Folder`** 変更を保存します。
   >1. `/conf/screens/settings/cloudsettings` の下のすべてのノードを `cloudsettings1` に移動します。
   >1. `cloudsettings` を削除して保存します。
   >1. `cloudsettings1` を `cloudsettings` に名前変更して保存します。
   >1. をご覧ください `/conf/screens/settings/cloudsettings` が `jcr:primaryType` as `sling:Folder`.
   >
   >オーサーとパブリッシュで、アップグレードの前または後に次の手順に従います。

   1. を入力 **タイトル** as **Google シート**, **ストア名** as **`googlesheets`**、および **ストアタイプ** as **c`ontexthub.generic-jsonp`** を選択して、 **次**.

      >[!CAUTION]
      >Adobe Experience Manager（AEM） 6.4 を使用している場合は、 **設定のタイトル** as **`googlesheets`** および **ストアタイプ** as **c`ontexthub.generic-jsonp`**.

      ![画像](/help/user-guide/assets/context-hub/context-hub6.png)

   1. 固有の JSON 設定を入力します。例えば、以下の json をデモ目的に使用し、以下を選択できます。 **保存**. という名前のストア設定が表示されます。 **Google シート** （ContextHub 設定内）。

      >[!IMPORTANT]
      >必ずコードを `*<Sheet ID>*` および `*<API Key>*`Google シートの設定中に取得した。

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
      >上記のサンプルコードでは、 **pollInterval** 値が更新される頻度をミリ秒単位で定義します。
      >
      >コードをに置き換えます `*<Sheet ID>*` および `*<API Key>*`Google シートの設定中に取得した。

      >[!CAUTION]
      >
      >Google Sheets で、グローバルフォルダーの外部（例えば、独自のプロジェクトフォルダー内）に設定を保存する場合、ターゲティングは標準では機能しません。

1. **ストアのセグメント化の設定**

   1. に移動します。 **ContentHub ストアの設定** さらに、AEM Screens設定コンテナに別のストア設定を作成し、 **タイトル** as **segmentation-contexthub**, **ストア名** as **セグメント化** および **ストアタイプ** as **aem.segmentation**.

      ![画像](/help/user-guide/assets/context-hub/context-hub7.png)

   1. を選択 **次** その後 **保存**.

      >[!NOTE]
      >JSON を定義するプロセスはスキップし、空白のままにします。


## 手順 3：オーディエンスのセグメントのセットアップ {#setting-up-audience}

1. **オーディエンスにセグメントを作成する**

   1. AEM インスタンスで、**パーソナライゼーション**／**オーディエンス**／**Screens** に移動します。

   1. を選択 **作成** > **Context Hub セグメントを作成します。**&#x200B;をクリックします。**新しい ContextHub セグメント**&#x200B;ダイアログボックスが開きます。

   1. を入力 **タイトル** as `**Higherthan50**` を選択して、 **作成**. 同様に、というタイトルの別のセグメントを作成します `**Lowerthan50**`.

      ![画像](/help/user-guide/assets/context-hub/context-hub11.png)

   1. セグメントを選択 `**Higherthan50**` を選択して、 **プロパティ** アクションバーから。
      ![画像](/help/user-guide/assets/context-hub/context-hub12.png)

   1. **セグメントプロパティ**&#x200B;から「**パーソナライゼーション**」タブを選択します。を **ContextHub パス** 対象： `/conf/screens/settings/cloudsettings/ContextHubDemo/contexthub configurations` および **セグメントのパス** 対象： `/conf/screens/settings/wcm/segments` を選択して、 **保存**&#x200B;を参照してください（下図を参照）。

   ![画像](/help/user-guide/assets/context-hub/context-hub13.png)

   1. 同様に、 **ContextHub パス** および **セグメントのパス** （用） `**Lowerthan50**` セグメントも。

## 手順 4：ブランドと領域の設定 {#setting-brand-area}

アクティビティおよびブランドの下の領域にブランドを作成するには、次の手順に従います。

1. **アクティビティにブランドを作成する**

   1. AEM インスタンスからに移動します。 **Personalization** > **アクティビティ**.

   1. を選択 **作成** > **ブランドを作成**.

   1. を選択 **ブランド** から **ページを作成** ウィザードと選択 **次**.

   1. を入力 **タイトル** as **ScreensBrand** を選択して、 **作成**. これで、以下のようにブランドが作成されました。

      ![画像](/help/user-guide/assets/context-hub/context-hub8.png)


      >[!CAUTION]
      >
      >既知の問題：
      >領域を追加するには、次のように URL からプライマリを削除します
      >`http://localhost:4502/libs/cq/personalization/touch-ui/content/v2/activities.html/content/campaigns/screensbrand/master`。

1. **ブランドに領域を作成する**

   以下の手順に従って、ブランドに領域を作成します。

   1. を選択 **作成** その後 **エリアを作成**.

      ![画像](/help/user-guide/assets/context-hub/context-hub9.png)

   1. を選択 **領域** から **ページを作成** ウィザードと選択 **次**.

   1. を入力 **タイトル** as **ScreensValue** を選択して、 **作成**.
ブランドにエリアが作成されます。

## 手順 5：アクティビティのセグメントの作成 {#step-setting-up-audience-segmentation}

データストアの設定とアクティビティ（ブランドと領域）の定義が完了したら、次の手順に従ってアクティビティでセグメントを作成します。

1. **アクティビティにセグメントを作成する**

   1. AEM インスタンスで、**パーソナライゼーション**／**アクティビティ**／**ScreensBrand**／**ScreensValue** に移動します。

   1. を選択 **作成** > **アクティビティを作成。**&#x200B;をクリックします。**アクティビティの設定**&#x200B;ウィザードが開きます。

   1. 「**タイトル**」に「**ValueCheck50**」、「**名前**」に「**valuecheck50**」と入力します。「」を選択します **ターゲティングエンジン** as **ContextHub （AEM）** ドロップダウンからを選択します。 **次**.

      ![画像](/help/user-guide/assets/context-hub/context-hub14.png)

   1. を選択 **エクスペリエンスを追加** から `**Configure Activity**` ウィザード。

   1. から **オーディエンス**&#x200B;を選択し、 `**Higherthan50**` を選択して、 **エクスペリエンスを追加** を入力し、 **タイトル** as `**higherthan50**` **名前** as `**higherthan50**`. を選択 **Ok**.

   1. から **オーディエンス**&#x200B;を選択し、 `**Lowerthan50**` を選択して、 **エクスペリエンスを追加** を入力し、 **タイトル** as `**lowerthan50**` **名前** as `**lowerthan50**`. を選択 **Ok**.

   ![画像](/help/user-guide/assets/context-hub/context-hub15.png)

   1. を選択 **次** その後 **保存**. `**ValueCheck50**` これで、アクティビティの作成と設定が完了しました。

      ![画像](/help/user-guide/assets/context-hub/context-hub16.png)

## 手順 5：オーディエンスのセグメントの編集{#editing-audience-segmentation}

1. **セグメントを編集する**

   1. AEM インスタンスで、**パーソナライゼーション**／**オーディエンス**／**Screens** に移動します。

   1. セグメントを選択 `**Higherthan50**`を選択し、 **編集** アクションバーから。

   1. **比較：プロパティ - 値**&#x200B;コンポーネントをエディターにドラッグ＆ドロップします。

   1. レンチ アイコンを選択すると、 **プロパティと値の比較** ダイアログが表示されます。

   1. 「**プロパティ名**」のドロップダウンから「**googlesheets/value/1/0**」を選択します。

      >[!NOTE]
      > この **google シート/値/1/0** で入力された行 2 と列を指します `google` 下図のシート

      ![画像](/help/user-guide/assets/context-hub/context-hub17.png)

   1. 「**演算子**」のドロップダウンメニューから「**次よりも大きい**」を選択します。

   1. 「**値**」に「**70**」を入力します。

      >[!NOTE]
      >
      >AEM で Google シートのデータが検証されると、セグメントが緑色で表示されます。

      ![画像](/help/user-guide/assets/context-hub/context-hub18.png)

   同様に、プロパティ値をに編集します `**Lowerthan50**`.

   1. **比較：プロパティ - 値**&#x200B;コンポーネントをエディターにドラッグ＆ドロップします。

   1. レンチ アイコンを選択します。

   1. が含まれる **プロパティと値の比較** ダイアログ ボックスで、を選択します。 **google シート/値/1/0** のドロップダウンから **プロパティ名**.

   1. 「**演算子**」のドロップダウンメニューから「**次よりも小さい**」を選択します。

   1. 「**値**」に「**50**」と入力します。


## チャネルでのターゲティングの有効化 {#step-enabling-targeting-in-channels}

以下の手順に従って、チャネルでターゲティングを有効にします。

1. AEM Screens チャネルのいずれかに移動します。 以下の手順は、AEM Screens チャネルに作成した **DataDrivenChannel** を使用してターゲティングを有効にする方法を示しています。

1. チャネルを選択 **TargetChannel** を選択して、 **プロパティ** アクションバーから。

   ![画像](/help/user-guide/assets/context-hub/context-hub19.png)

1. 「」を選択します **Personalization** タブをクリックして、ContextHub 設定をセットアップします。

   1. 「**ContextHub パス**」を `/conf/screens/settings/wcm/segments` に設定、「**セグメントパス**」を `/conf/screens/settings/wcm/segments` に設定します。
   1. ドロップダウンからブランドを **ScreensBrand**、「**エリア参照を設定**」を **ScreensValue** に設定します。

   1. 「**保存して閉じる**」を選択します。

      >[!NOTE]
      >
      >ContextHub 設定とセグメントをそれぞれ最初に保存した、Context Hub とセグメントのパスを使用します。

      ![画像](/help/user-guide/assets/context-hub/context-hub20New.png)

   1. に移動してフォルダーを選択します **TargetChannel** チャネルと選択 **編集** アクションバーから。

      >[!NOTE]
      >
      >すべてが正しく設定されていれば、次のように表示されます **ターゲティング** エディターのドロップダウンの「」オプション（下図を参照）。

      ![画像](/help/user-guide/assets/context-hub/context-hub21.png)

## 詳細情報：使用例 {#learn-more-example-use-cases}

AEM Screens プロジェクトに ContextHub を設定したら、以下の様々な使用例を通じて、データでトリガーされるアセットが様々な業界でいかに重要な役割を果たしているかを理解できます。

1. **[小売店向けの在庫に応じたアクティベーション](retail-inventory-activation.md)**
1. **[旅行センター向けの気温に応じたアクティベーション](local-temperature-activation.md)**
1. **[接客業向けの予約状況に応じたアクティベーション](hospitality-reservation-activation.md)**
