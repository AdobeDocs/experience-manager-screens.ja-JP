---
title: エクスペリエンスフラグメントの使用
description: AEM Screens でのエクスペリエンスフラグメントの使用について説明します。
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
docset: aem65
feature: Authoring Screens, Experience Fragments
role: Admin, Developer
level: Intermediate
exl-id: 13c0d75e-435f-433e-8886-f451df863517
TQID: https://experienceleague.adobe.com/hsBfnZKyaM96INkVmC94M2t39u-TzUIDPgdmHjjCHRc
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2: id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 1155
ht-degree: 83%

---

# エクスペリエンスフラグメントの使用 {#using-experience-fragments}

>[!IMPORTANT]
>このコンテンツは、AEM オンプレミス/AMS （AEM 6.5LTSおよびAEM 6.5）に対して有効です。 AEM as a Cloud Service Screensの内容については、[AEM as a Cloud Service ガイド ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)を参照してください。

ここでは、以下のトピックについて説明します。

* **概要**
* **AEM Screens でのエクスペリエンスフラグメントの使用**
* **ページへの変更の反映**

## 概要 {#overview}

***エクスペリエンスフラグメント***&#x200B;は、ページ内で参照できるコンテンツおよびレイアウトを含む 1 つ以上のコンポーネントのグループです。 エクスペリエンスフラグメントには、任意のコンポーネントを含めることができます。 例えば、1 つまたは複数のコンポーネントを含め、そのコンポートに完全なエクスペリエンスで参照される、または 3 番目のエンドポイントによって要求される段落システム内のあらゆるものを含めることができます。


## AEM Screens でのエクスペリエンスフラグメントの使用 {#using-experience-fragments-in-aem-screens}

>[!NOTE]
>次の例では、**`We.Retail`** をデモプロジェクトとして使用し、**Sites** ページのエクスペリエンスフラグメントを AEM Screens プロジェクトに利用します。

例えば、以下のワークフローは、`We.Retail` のエクスペリエンスフラグメントを Sites で使用する方法を示しています。 Web ページを選択し、そのコンテンツをプロジェクトの 1 つの AEM Screens チャネルで使用できます。

### 前提条件 {#pre-requisites}

**チャネルを含んだデモプロジェクトの作成**

***プロジェクトの作成***

1. プロジェクトを作成するには、「**Screens プロジェクトの作成**」をクリックします。
1. タイトルに「**DemoProject**」と入力します。
1. 「**保存**」をクリックします。

**DemoProject** が AEM Screens に追加されます。

***チャネルの作成***

1. 作成した **DemoProject** プロジェクトに移動し、**チャネル**&#x200B;フォルダーをクリックします。

1. アクションバーの「**作成**」をクリックして、ウィザードを開きます。
1. ウィザードで「**シーケンスチャネル**」テンプレートを選択し、「**次へ**」をクリックします。

1. 「**タイトル**」に「**TestChannel**」と入力し、「**作成**」をクリックします。

**TestChannel** が **DemoProject** に追加されます。\
![screen_shot_2019-07-29at105101am](assets/screen_shot_2019-07-29at105101am.png)


### エクスペリエンスフラグメントの作成 {#creating-an-experience-fragment}

**DemoProject** の **TestChannel** に **`We.Retail`** のコンテンツを適用するには、以下の手順に従います。

1. **We.Retail の Sites ページへの移動**

   1. Sites に移動し、**`We.Retail`**／**United States**／**English**／**Equipment** をクリックし、このページをクリックすると、Screens チャネルのエクスペリエンスフラグメントとして使用できます。

   1. アクションバーの「**編集**」をクリックして、Screens チャネルのエクスペリエンスフラグメントとして使用するページを開きます。

1. **コンテンツの再利用**

   1. チャネルに含めるフラグメントをクリックします。
   1. 右側の最後のアイコンをクリックして、**エクスペリエンスフラグメントに変換**&#x200B;ダイアログボックスを開きます。

   ![screen_shot_2019-07-29at105314am](assets/screen_shot_2019-07-29at105314am.png)

1. **エクスペリエンスフラグメントの作成**

   1. 「**アクション**」として「**新しいエクスペリエンスフラグメントを作成**」を選択します。

   1. 「**親パス**」をクリックします。
   1. 「**テンプレート**」をクリックします。 ここでは、「**エクスペリエンスフラグメント - 画面のバリエーション**」テンプレート（このフィールドの `/libs/settings/screens/experience-fragments/templates/experience-fragment-template-screens` 値）を選択します。

   1. 「**フラグメントのタイトル**」に「**ScreensFragment**」と入力します。

   1. 新しいエクスペリエンスフラグメントの作成を完了するには、チェックマークをクリックします。

   ![screen_shot_2019-07-29at105918am](assets/screen_shot_2019-07-29at105918am.png)

   より簡単なオプションを選択するには、フィールドの右側のチェックマークをクリックして、選択ダイアログボックスを開きます。

1. **エクスペリエンスフラグメントのライブコピーの作成**

   1. AEM ホームページに移動します。
   1. 「**エクスペリエンスフラグメント**」をクリックし、「**ScreensFragment**」をハイライト表示して、「**バリエーションをライブコピーとして**」をクリックします（下図を参照）。

   ![screen_shot_2019-07-29at110443am](assets/screen_shot_2019-07-29at110443am.png)

   c. **ライブコピーの作成** ウィザードの&#x200B;**ScreensFragment**&#x200B;をクリックし、**次へ**&#x200B;をクリックします。

   d. **タイトル**&#x200B;と&#x200B;**名前**&#x200B;を&#x200B;**Screens**&#x200B;として入力します。

   e. 「**作成**」をクリックすると、ライブコピーを作成できます。

   f. **完了**&#x200B;をクリックして、**ScreensFragment** ページに戻ります。

   ![screen_shot_2019-07-29at110616am](assets/screen_shot_2019-07-29at110616am.png)

   >[!NOTE]
   >
   >Screens フラグメントを作成したら、フラグメントのプロパティを編集できます。 フラグメントをクリックし、アクションバーの「**プロパティ**」をクリックします。

   **Screens フラグメントのプロパティの編集**

   1. （前の手順で作成した）**ScreensFragment** に移動し、アクションバーの「**プロパティ**」をクリックします。

   1. 「**オフライン設定**」タブをクリックします（下図を参照）。

   エクスペリエンスフラグメントに&#x200B;**クライアント側ライブラリ**（Java™ および CSS）と&#x200B;**静的ファイル**&#x200B;を追加できます。

   次の例は、クライアント側ライブラリのほか、フォントを静的ファイルの一部としてエクスペリエンスフラグメントに追加する場合を示しています。  ![fragment](assets/fragment.gif)

1. **Screens チャネルでのコンポーネントとしてのエクスペリエンスフラグメントの使用**

   1. **Screens** フラグメントを使用する Screens チャネルに移動します。
   1. 「**TestChannel**」をクリックし、アクションバーの「**編集**」を選択します。

   1. サイドタブのコンポーネントアイコンをクリックします。
   1. チャネルに「**エクスペリエンスフラグメント**」をドラッグ＆ドロップします。

   ![screen_shot_2019-07-29at123115pm](assets/screen_shot_2019-07-29at123115pm.png)

   e. **エクスペリエンスフラグメント** コンポーネントをクリックし、左上（レンチ）アイコンをクリックして、**エクスペリエンスフラグメント** ダイアログボックスを開きます。

   f. **パス**&#x200B;の&#x200B;*手順3*&#x200B;で作成したフラグメントの&#x200B;**Screens** ライブコピーをクリックします。

   ![screen_shot_2019-07-26at82650pm](assets/screen_shot_2019-07-26at82650pm.png)

   f. **エクスペリエンスフラグメント**&#x200B;の&#x200B;*手順3*&#x200B;で作成したフラグメントの&#x200B;**Screens** ライブコピーをクリックします。

   ![screen_shot_2019-07-26at82509pm](assets/screen_shot_2019-07-26at82509pm.png)

   h. **期間**&#x200B;にミリ秒単位で入力します。

   私は。 **エクスペリエンスフラグメント** ダイアログボックスの&#x200B;**オフライン設定**&#x200B;をクリックして、クライアントサイドライブラリと静的ファイルを定義できるようにします。

   >[!NOTE]
   >
   >前述の手順 4 で設定した内容に加えて、クライアント側ライブラリや静的ファイルを追加するには、**エクスペリエンスフラグメント**&#x200B;ダイアログボックスの「**オフライン設定**」タブで追加できます。

   ![screen_shot_2019-07-26at82844pm](assets/screen_shot_2019-07-26at82844pm.png)

   j. チェックマークをクリックすると、プロセスを完了できます。

### 結果の検証 {#validating-the-result}

前述の手順が完了したら、次の手順で **ChannelOne** 内のエクスペリエンスフラグメントを検証できます。

1. **TestChannel** に移動します。
1. アクションバーの「**プレビュー**」をクリックします。

チャネル内の **Sites** ページ（エクスペリエンスフラグメントのライブコピー）のコンテンツが表示されます（下図を参照）。\
![screen_shot_2018-06-08at120739pm](assets/screen_shot_2018-06-08at120739pm.png)

## ページへの変更の反映 {#propagating-changes-from-the-master-page}

***ライブコピー***&#x200B;とは、ロールアウト設定で定義された同期アクションによって維持管理される（ソースの）コピーのことです。

作成したエクスペリエンスフラグメントは **Sites** ページのライブコピーであり、その特定のフラグメントはプライマリページから変更するため、変更内容がチャネルに表示されます。 または、エクスペリエンスフラグメントの使用先が表示されます。

>[!NOTE]
>
>ライブコピーについて詳しくは、「コンテンツの再利用：マルチサイトマネージャーとライブコピー」を参照してください。

プライマリチャネルから目的のチャネルに変更を反映するには、以下の手順に従います。

1. **Sites**（プライマリ）ページでエクスペリエンスフラグメント、鉛筆アイコンの順にクリックすると、エクスペリエンスフラグメント内の項目を編集できます。

   ![screen_shot_2018-06-08at122655pm](assets/screen_shot_2018-06-08at122655pm.png)

1. エクスペリエンスフラグメントを選択し、レンチアイコンをクリックすると、画像編集用のダイアログボックスを開くことができます。

   ![screen_shot_2018-06-08at25031pm](assets/screen_shot_2018-06-08at25031pm.png)

1. **商品グリッド**&#x200B;ダイアログボックスが開きます。

   ![screen_shot_2018-06-08at25306pm](assets/screen_shot_2018-06-08at25306pm.png)

1. 任意の画像を編集できます。 例えば、ここでは、このフラグメントの最初の画像が置き換えられます。

   ![screen_shot_2018-06-08at25608pm](assets/screen_shot_2018-06-08at25608pm.png)

1. エクスペリエンスフラグメントをクリックし、ロールアウトアイコンをクリックすると、チャネルで使用されているフラグメントに変更を反映できます。

   ![screen_shot_2018-06-08at31352pm](assets/screen_shot_2018-06-08at31352pm.png)

1. 「ロールアウト」をクリックします。

   変更がロールアウトされます。

   ![screen_shot_2018-06-08at32148pm](assets/screen_shot_2018-06-08at32148pm.png)

### 変更の検証 {#validating-the-changes}

チャネルでの変更内容を確認するには、以下の手順に従います。

1. **Screens**／**Channels**／**TestChannel** に移動します。

1. アクションバーの「**プレビュー**」をクリックします。

次の画像は、**TestChannel** に反映された変更を示しています。\
![screen_shot_2018-06-08at33351pm](assets/screen_shot_2018-06-08at33351pm.png)
