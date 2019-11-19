---
title: ファイルからの新しいプロジェクトインポーター
seo-title: ファイルからの新しいプロジェクトインポーター
description: この機能を使用すると、CSV/XLSスプレッドシートからAEM Screensプロジェクトに場所のセットを一括インポートできます。
seo-description: この機能を使用すると、CSV/XLSスプレッドシートからAEM Screensプロジェクトに場所のセットを一括インポートできます。
uuid: e1ad76ae-6925-4d72-80ce-8343a76125ce
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: f1df8d05-bb61-4bc9-aea1-c6af9e3519b4
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# ファイルからの新しいプロジェクトインポーター {#new-project-importer-from-file}

ここでは、CSV/XLSスプレッドシートからAEM Screensプロジェクトに場所のセットを一括インポートする機能について説明します。

## 概要 {#introduction}

AEM Screensプロジェクトを設定する場合は、組織で初めてすべての場所を作成する必要があります。 プロジェクトに多数の場所が含まれる場合は、UIでのクリックや待機に多くの時間がかかる、退屈な作業になります。

この機能の目標は、プロジェクトの設定に要する時間を短縮し、予算の問題を解決することです。

作成者がスプレッドシートを入力ファイルとして提供し、システムがバックエンドにロケーションツリーを自動的に作成できるようにすることで、次の機能が実現します。

* *手動でUIをクリックするよりもパフォーマンスが向上*
* *お客様が所有する場所を独自のシステムから書き出し、AEMに直接簡単に読み込むことができます。*

これにより、初回のプロジェクト設定時または既存のAEM screenを新しい場所に拡張する際に、時間と費用の両方を節約できます。

## アーキテクチャの概要 {#architectural-overview}

次の図は、プロジェクトインポータ機能のアーキテクチャの概要を示しています。

![screen_shot_2019-05-14at20618pm](assets/screen_shot_2019-05-14at20618pm.png)

### データモデル {#data-model}

プロジェクトインポーターのデータモデルを以下に示します。

>[!NOTE]
>
>現在のリリースでは、場所の読み込みのみがサポートされています。

| **プロパティ** | **説明** |
|---|---|
| ***path {string*}** | 場所のリソースパス |
| ***[./jcr:title]{string*}** | 使用するテンプレートの名前( *画面/コア/テンプレート/場所*) |
| ***template {string}*** | ページに使用するオプションのタイトル |
| ***[./jcr:description]{string}*** | ページに使用するオプションの説明 |

スプレッドシート(CSV/XLS)ファイルには、次の列が必要です。

* **path {string}** 、パスのルートがプロジェクトの場所フォルダーである場所のパス(つまり、/foo *が/content/screens/&lt;project&gt;/locations/foo***)

* **template {string}** 、新しい場所に使用するテンプレートです。現在許可されている値は「location」だけですが、将来はすべての画面テンプレート（「display」、「sequenchannel」など）に拡張されます。
* [**./*] {string}**場所に設定する任意のオプションのプロパティ(つまり、./jcr:title, ./jcr:description, ./foo、./bar)。 現在のリリースでは、現時点でフィルタリングは許可されていません

>[!NOTE]
>
>上記の条件に一致しない列は無視されます。 例えば、シートに **path**,template **,** title **,********** title以外の列が定義されている場合、その列は無視され、Importerプロジェクトをインポートしない場合はその追加のCSV/XLSフィールドはプロジェクトに対して検証されます。

## プロジェクトインポーターの使用 {#using-project-importer}

次の節では、AEM Screensプロジェクトでのプロジェクトインポーターの使用方法について説明します。

>[!CAUTION]
>
>制限事項:
>
>* CSV/XLS/XLSX拡張子以外のファイルは、現在のリリースではサポートされていません。
>* 読み込まれたファイルおよび「」で始まるすべてのファイルに対して、プロパティのフィルタリングは存在しません。/"がインポートされます。
>



### 前提条件 {#prerequisites}

* DemoProjectImportという名前の新しいプロジェクトを作成 **します**

* インポートする必要があるサンプルCSVファイルまたはExcelファイルを使用します。

デモ用に、以下のセクションからExcelファイルをダウンロードできます。

[ファイルの取得](assets/minimal-file.xls)

### 最小必須フィールドを含むファイルの読み込み {#importing-the-file-with-minimum-required-fields}

以下の手順に従って、最小限必要なフィールドを含む場所フォルダーにファイルをインポートします。

>[!NOTE]
>
>次の例は、プロジェクトのインポートに必要な最低4つのフィールドを示しています。

![screen_shot_2019-05-14at21523pm](assets/screen_shot_2019-05-14at21523pm.png)

1. AEM Screensプロジェクト(DemoProjectImport ****)に移動します。

   ![screen_shot_2019-05-12at52651am](assets/screen_shot_2019-05-12at52651am.png)

1. サイドバーからプロジェクト「** DemoProjectImporter **—&gt;作成** —&gt;イン **ポート場所**** 」を選択します。

   ![screen_shot_2019-05-12at52433am](assets/screen_shot_2019-05-12at52433am.png)

1. インポー **ト** ・ウィザードが開きます。 場所を持つプロジェクト用のファイルを選択するか、***Prerequisites***（前提条件）セクションからダウンロードしたファイル( *minimal-file.xls* )を選択します。

   ファイルを選択したら、「次へ」をクリッ **クします**。

   ![screen_shot_2019-05-15at113718am](assets/screen_shot_2019-05-15at113718am.png)

1. インポートウィザードでファイル（場所）の内容を確認し、「インポート」をクリッ **クします**。

   ![screen_shot_2019-05-12at53131am](assets/screen_shot_2019-05-12at53131am.png)

1. その結果、プロジェクトに読み込まれたすべての場所を表示できるようになります。

   ![screen_shot_2019-05-12at53450am](assets/screen_shot_2019-05-12at53450am.png)

