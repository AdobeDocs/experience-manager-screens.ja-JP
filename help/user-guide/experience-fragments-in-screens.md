---
title: エクスペリエンスフラグメントの使用
seo-title: エクスペリエンスフラグメントの使用
description: 'このページでは、AEM Screensでのエクスペリエンスフラグメントの使用について説明します。 '
seo-description: 'このページでは、AEM Screensでのエクスペリエンスフラグメントの使用について説明します。 '
uuid: 6ee16a94-3c53-43e0-99d5-c35cb9e01120
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 0e88e9e0-a95b-4acd-98ea-499d4d4e3c99
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# エクスペリエンスフラグメントの使用 {#using-experience-fragments}

このページでは、次のトピックについて説明します。

* **概要**
* **AEM Screens でのエクスペリエンスフラグメントの使用**
* **マスターページからの変更の反映**

## 概要 {#overview}

***エクスペリエンスフラグメント**は、ページ内で参照できるコンテンツおよびレイアウトを含む 1 つ以上のコンポーネントのグループです。*&#x200B;エクスペリエンスフラグメントには、段落システム内に含めることができる 1 つ以上のコンポーネントなど、任意のコンポーネントを含めることができます。完全なエクスペリエンスに参照され、3 番目のエンドポイントによって要求されます。


## AEM Screens でのエクスペリエンスフラグメントの使用 {#using-experience-fragments-in-aem-screens}

>[!NOTE]
>
>次の例では、 **We.Retailをデモプロジェクトとして使用し** 、エクスペリエンスフラグメントをサイトページからAEM **** Screensプロジェクトに活用します。

例として、次のワークフローは、We.RetailのエクスペリエンスフラグメントをSitesで使用する方法を示しています。 Webページを選択し、そのコンテンツをAEM Screensチャネルでプロジェクトの1つで利用できます。

### 前提条件 {#pre-requisites}

**チャネルを使用したデモプロジェクトの作成**

***プロジェクトの作成***

1. Click Screens and select **Create** --&gt; **Create Project **to create a new project.

1. 「**画面**」を「**画面を作成プロジェクト**」ウィザードから選択します。

1. タイトルに "**DemoProject**" と入力します。
1. 「**作成**」をクリックします。

AEM Screensに **DemoProject** が追加されます。  ***チャネルの作成***

1. Navigate to the **DemoProject** you created and select the **Channels** folder.

1. Click **Create** from the action bar (see the figure below). ウィザードが開きます。
1. ウィザードから **「シーケンスチャネル** 」テンプレートを選択し、「次へ」をクリ **ックします**。

1. Enter the **Title** as **TestChannel** and click **Create**.

TestChannel **が** DemoProjectに追加さ **れます**。\
![screen_shot_2019-07-29at105101am](assets/screen_shot_2019-07-29at105101am.png)



### エクスペリエンスフラグメントの作成 {#creating-an-experience-fragment}

次の手順に従って、 **We.Retailから** DemoProjectの **TestChannel** にコンテンツを活用 **します**。

1. **We.Retailのサイトページに移動します。**

   1. 「サイト」に移動し、「**We.Retail **-&gt;** United States **-&gt;**English **」を選択し、「 **Equipment** 」ページを選択して、画面チャネルのエクスペリエンスフラグメントとして使用します。

   1. アクシ **ョンバーで** 「編集」をクリックして、画面チャネルのエクスペリエンスフラグメントとして使用するページを開きます。
   ![screen_shot_2018-06-06at105309am](assets/screen_shot_2018-06-06at105309am.png)

1. **コンテンツの再利用**

   1. チャネルに含めるフラグメントを選択します。
   1. 右側の最後のアイコンをクリックして、エクスペリエンスフラグメ **ントに変換ダイアログボックス** を開きます。
   ![screen_shot_2019-07-29at105314am](assets/screen_shot_2019-07-29at105314am.png)

1. **エクスペリエンスフラグメントの作成**

   1. 「新しいエクスペ **リエンスフラグメ** ントを作成」でアクションを選択します ****。

   1. 親パスを **選択します**。
   1. Select the **Template**. **エクスペリエンスフラグメント — 画面のバリエーション**テンプレートを選択します。

   1. Enter the **Fragment Title **as **ScreensFragment**.

   1. チェックマークをクリックして、新しいエクスペリエンスフラグメントの作成を完了します。
   ![screen_shot_2019-07-29at105918am](assets/screen_shot_2019-07-29at105918am.png)

1. **エクスペリエンスフラグメントのライブコピーの作成**

   1. AEMのホームページに移動します。
   1. 次の図に **示すように、「** Experience Fragments **」を選択し、「** ScreensFragment **」をハイライトし、「** Variation」をライブコピーとしてクリックします。
   ![screen_shot_2019-07-29at110443am](assets/screen_shot_2019-07-29at110443am.png)

   c.「** ScreensFragment from **Create Live Copy**」ウィザードを選択し、「** Next ****」をクリックします。

   d.「タイトル」 **と「名前** 」に「 **画面** 」と入力 **します**。

   e.「作成」 **をクリックし** 、ライブコピーを作成します。

   f.「完了」 **をクリックし** 、「ScreensFragment **** 」ページに戻ります。

   ![screen_shot_2019-07-29at110616am](assets/screen_shot_2019-07-29at110616am.png)

   >[!NOTE]
   >
   >画面フラグメントを作成したら、フラグメントのプロパティを編集できます。 フラグメントを選択し、アクションバー **の「プロパティ** 」をクリックします。

   **画面フラグメントのプロパティの編集**

   1. 「 **ScreensFragment** 」（前の手順で作成した）に移動し、アクションバーの「プ **ロパティ** 」をクリックします。

   1. 下の図に示 **すように** 、「Offline Config」タブを選択します。
   クライアント側ラ **イブラリ** （javaおよびcss）と静的ファイルを **エクスペリエンスフラグメントに追加できます** 。

   次の例は、クライアント側ライブラリとフォントを静的ファイルの一部としてエクスペリエンスフラグメントに追加する方法を示しています。  ![フラグメント](assets/fragment.gif)

1. **画面チャネルでのエクスペリエンスフラグメントのコンポーネントとしての使用**

   1. 画面フラグメントを使用する画面チャネルに移 **動します** 。
   1. 「TestChannel」を選択 **し、アクショ** ンバーで **** 「編集」をクリックします。

   1. 「サイド」タブでコンポーネントアイコンをクリックします。
   1. エクスペリエンスフラグメント **をチャネルに** ドラッグ&amp;ドロップします。
   ![screen_shot_2019-07-29at123115pm](assets/screen_shot_2019-07-29at123115pm.png)

   e.エクスペリエン **スフラグメント** コンポーネントを選択し、左上の（レンチ）アイコンを選択して、エクスペリエンスフラグメント **ダイアログボックスを開きます** 。

   f.手順3 **で作成したフラグメ** ントの「Screens ** 」ライブコピーを「**Path **」フィールドで選択します。

   ![screen_shot_2019-07-26at82650pm](assets/screen_shot_2019-07-26at82650pm.png)

   f.手順3で「 ****エクスペリエンスフラグメント** **」フィールドで、作成したフラグメントの「 ** 画面」ライブコピーを選択します。

   ![screen_shot_2019-07-26at82509pm](assets/screen_shot_2019-07-26at82509pm.png)

   h.「**時間**」フィールドに秒数を入力します。

   i.エクスペリエ **ンスフラグメント** ( **Experience Fragments** )ダイアログボックスで「オフライン設定」を選択し、クライアント側ライブラリと静的ファイルを定義します。

   >[!NOTE]
   >
   >手順(4)で設定した内容に加えて、クライアント側ライブラリまたは静的ファイルを追加する場合は、 **Experience Fragment** ダイアログボックスの「 **Offline Config** 」タブから追加できます。

   ![screen_shot_2019-07-26at82844pm](assets/screen_shot_2019-07-26at82844pm.png)

   j.チェックマークをクリックして、プロセスを完了します。

### 結果の検証 {#validating-the-result}

前述の手順が完了したら、次の方法でChannelOne内のエクスペリエンスフラグメントを検 **証できます** 。

1. TestChannelへのナビゲー **ション**。
1. アクションバ **ーから** 「プレビュー」を選択します。

次の図に示すように、チャネル内の **Sites** （エクスペリエンスフラグメントのライブコピー）ページのコンテンツが表示されます。\
![screen_shot_2018-06-08at120739pm](assets/screen_shot_2018-06-08at120739pm.png)

## マスターページからの変更の反映 {#propagating-changes-from-the-master-page}

***ライブコピーは*** 、（ソースの）コピーを指し、ロールアウト設定で定義された同期アクションによって保持されます。

エクスペリエンスフラグメントは **Sites** ページからのライブコピーで作成されるので、マスターページからその特定のフラグメントに変更を加えた場合は、チャネルまたはエクスペリエンスフラグメントを使用した宛先に変更が表示されます。

>[!NOTE]
>
>ライブコピーについて詳しくは、「コンテンツの再利用：マルチサイトマネージャとライブコピーを参照してください。

マスター・チャネルから宛先チャネルに変更を反映するには、次の手順に従います。

1. サイト **** （マスター）ページから「エクスペリエンスフラグメント」を選択し、鉛筆アイコンをクリックして、エクスペリエンスフラグメント内の項目を編集します。

   ![screen_shot_2018-06-08at122655pm](assets/screen_shot_2018-06-08at122655pm.png)

1. エクスペリエンスフラグメントを選択し、レンチアイコンをクリックしてダイアログボックスを開き、画像を編集します。

   ![screen_shot_2018-06-08at25031pm](assets/screen_shot_2018-06-08at25031pm.png)

1. 「製品グ **リッド** 」(Product Grid)ダイアログボックスが開きます。

   ![screen_shot_2018-06-08at25306pm](assets/screen_shot_2018-06-08at25306pm.png)

1. 任意の画像を編集できます。 例えば、このフラグメントで最初の画像が置き換えられます。

   ![screen_shot_2018-06-08at25608pm](assets/screen_shot_2018-06-08at25608pm.png)

1. エクスペリエンスフラグメントを選択し、ロールアウトアイコンをクリックして、チャネルで使用されているフラグメントに変更を反映します。

   ![screen_shot_2018-06-08at31352pm](assets/screen_shot_2018-06-08at31352pm.png)

1. [ロールアウト]をクリックして変更を確定します。

   変更がロールアウトされます。

   ![screen_shot_2018-06-08at32148pm](assets/screen_shot_2018-06-08at32148pm.png)

### 変更の検証 {#validating-the-changes}

チャネルの変更を確認するには、次の手順に従います。

1. 画面/チャネ **ル** /TestChannel **に移** 動します ****。

1. アクショ **ンバーで** 「プレビュー」をクリックして、変更を確認します。

次の画像は、TestChannelの変更点を示して **います**。\
![screen_shot_2018-06-08at33351pm](assets/screen_shot_2018-06-08at33351pm.png)

