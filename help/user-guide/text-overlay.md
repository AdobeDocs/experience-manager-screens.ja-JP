---
title: テキストオーバーレイ
description: AEM Screens のテキストオーバーレイについて説明します。これを使用すると、画像の上にタイトルや説明を重ねて表示して、シーケンスチャネルに魅力的なエクスペリエンスを作成できます。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: bbc719df-24a7-4cfb-9786-1c3496f9f082
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: tm+mt
source-wordcount: '775'
ht-degree: 63%

---

# テキストオーバーレイ {#text-overlay}

ここでは、以下のトピックについて説明します。

* **概要**
* **テキストオーバーレイの使用**
* **テキストオーバーレイのプロパティについて**
* **テキストオーバーレイでの ContextHub 値の使用**

>[!CAUTION]
>
>**テキストオーバーレイ**&#x200B;機能は、AEM 6.3 機能パック 5 または AEM 6.4 機能パック 3 がインストールされている場合にのみ使用できます。

## 概要 {#overview}

テキストオーバーレイは、AEM Screensで利用できる機能です。 画像の上にオーバーレイされるタイトルや説明を提供することで、シーケンスチャネルで魅力的なエクスペリエンスを作成できます。

独自のカスタムコンポーネントの作成方法については、**AEM Screens コンポーネントの拡張**&#x200B;を参照してください。

この節では、ポスターコンポーネントをAEM Screens プロジェクトで使用および適用する方法のみを示します。 また、シーケンスチャネルの 1 つでテキストオーバーレイとして使用することも紹介します。

## テキストオーバーレイの使用 {#using-text-overlay}

この節では、AEM Screens プロジェクトでのテキストオーバーレイの使用について説明します。

**前提条件**

この機能を実装する前に、テキストオーバーレイの実装を開始するための前提条件として、プロジェクトをセットアップしておく必要があります。次に例を示します。

* AEM Screens プロジェクト（この例では **TextOverlayDemo**）を作成する

* というタイトルのシーケンスチャネルの作成 **TextSample** の下 **チャネル** フォルダー

* **TextSample** チャネルにコンテンツを追加する

次の画像は、 **TextOverlayDemo** を使用したプロジェクト **TextSample** 内のチャネル **チャネル** フォルダー。

![screen_shot_2018-12-16at75908pm](assets/screen_shot_2018-12-16at75908pm.png)

次の手順に従って、AEM Screens チャネルでテキストオーバーレイを使用します。

1. **TextOverlayDemo**／**チャネル**／**TextSample** に移動して、アクションバーから「**編集**」をクリックします。

   ![screen_shot_2018-12-16at80017pm](assets/screen_shot_2018-12-16at80017pm.png)

1. 画像をクリックし、 **設定** （レンチアイコン）をクリックして、「プロパティ」ダイアログボックスを開きます。

   ![screen_shot_2018-12-16at80221pm](assets/screen_shot_2018-12-16at80221pm.png)

1. 「」をクリックします **テキストオーバーレイ** 次の図に示すように、ダイアログボックスのナビゲーションバーのオプション。

   ![screen_shot_2018-12-16at80424pm](assets/screen_shot_2018-12-16at80424pm.png)

### テキストオーバーレイのプロパティについて {#understanding-text-overlay-properties}

テキストオーバーレイのプロパティを使用すると、Screens プロジェクトの任意のコンポーネントにテキストを追加できます。この節では、「テキストオーバーレイ」タブで使用できるプロパティの概要を説明します。

![text](assets/text.gif)

テキストボックスにテキストを追加し、太字、斜体、下線など、書式に強調を追加できます。

**カラーバリアント**：このオプションを選択すると、テキストは「暗い色」（黒のテキスト）または「明るい色」（白のテキスト）になります。

**サイズと位置の設定**&#x200B;このオプションで、テキストを水平または垂直方向に揃えることができます。または、テキストの位置揃えには詳細設定ツールを使用します。

>[!NOTE]
>
>詳細設定ツールを使用する場合は、「px」をサフィックスとして使用して、正しい位置をピクセル単位で指定する必要があります。例えば、「200px」とすると、 この式の結果は、開始点から 200 ピクセルになります。

## テキストオーバーレイでの ContextHub 値の使用 {#using-text-overlay-context-hub}

次の節では、データストアの値の使用方法について説明します。例えば、テキストオーバーレイコンポーネントでの google sheets などです。

**前提条件**

AEM Screens プロジェクトの ContextHub 設定を設定します。

データストアを使用してデータ駆動型アセットの変更を設定および管理する方法については、[AEM Screens での ContextHub の設定](https://experienceleague.adobe.com/ja/docs/experience-manager-screens/user-guide/developing/configuring-context-hub)を参照してください。

プロジェクトに必要な設定を行ったら、次の手順に従って Google Sheets の値を使用します。

1. に移動します。 **TextOverlayDemo** > **チャネル** > **TextSample** をクリックして、 **プロパティ** アクションバーから。

1. 「」をクリックします **Personalization** タブをクリックして、ContextHub 設定をセットアップします。

   1. 「」をクリックします **ContextHub パス** as **libs** > **設定** > **cloudsettings** > **default** > **ContextHub 設定** をクリックして、 **を選択**.

   1. 「」をクリックします **セグメントのパス** as **conf** > **スクリーン** > **設定** > **wcm** > **セグメント** をクリックして、 **を選択**.

   1. 「**保存して閉じる**」をクリックします。

      >[!NOTE]
      >
      >ContextHub 設定とセグメントを最初に保存した場所で、Context Hub とセグメントのパスを使用します。

      ![image1](/help/user-guide/assets/text-overlay/text-overlay8.png)

1. **TextOverlayDemo**／**チャネル**／**TextSample** に移動して、アクションバーから「**編集**」をクリックします。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay1.png)

1. の説明に従って、画像およびテキストオーバーレイコンポーネントを画像に追加します [テキストオーバーレイの使用](/help/user-guide/text-overlay.md#using-text-overlay) このページのセクション。

1. 「**構成**」（レンチアイコン）をクリックして、「**画像**」ダイアログボックスを開きます。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay4.png)

1. **画像**&#x200B;ダイアログボックスから「**ContextHub**」タブに移動します。「**追加**」をクリックします。

   >[!NOTE]
   >ContextHub 設定を行っていない場合、このオプションはプロジェクトで無効になります。

1. **プレースホルダー**&#x200B;フィールドに&#x200B;**値**&#x200B;を入力します。Google シートから値を取得する行をクリックします。 **ContextHub 変数**. この場合、値は Google Sheets の行 2 と列 1 から取得されます。次に、 **デフォルト値** as **20**、次の図に示します。 完了したら、チェックマークをクリックします。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay5.png)

   >[!NOTE]
   >参照用に、次の図は Google Sheets から取得される値を示しています。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay6.png)

1. 次の図に示すように、画像ダイアログボックスから&#x200B;**テキストオーバーレイ**&#x200B;タブに戻り、「*Current Temperature {Value}*」というテキストを追加します。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay7.png)

1. **プレビュー**&#x200B;をクリックします。

   ![image1](/help/user-guide/assets/text-overlay/text-overlay10.png)
