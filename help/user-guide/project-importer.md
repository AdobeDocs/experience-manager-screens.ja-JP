---
title: ファイルをソースとする新しいプロジェクトインポーター
description: この機能を使用すると、CSV/XLS スプレッドシートから AEM Screens プロジェクトに一連の場所を一括で読み込むことができます。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
docset: aem65
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 3bff9ef3-0d6f-41d8-a8ef-bcc5a795990e
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '619'
ht-degree: 85%

---

# ファイルをソースとする新しいプロジェクトインポーター {#new-project-importer-from-file}

ここでは、CSV／XLS スプレッドシートから AEM Screens プロジェクトに一連のロケーションを一括で読み込む機能について説明します。

## はじめに {#introduction}

組織で初めてAEM Screens プロジェクトを設定する場合は、すべての場所も作成します。 プロジェクトに多くの場所が含まれる場合、UI での多くの選択や待機を伴う面倒なタスクになります。

この機能は、プロジェクトのセットアップに要する時間を短縮して、予算の問題を解決することを目的としています。

この機能では、作成者が入力ファイルとしてスプレッドシートを提供でき、システムがバックエンドにロケーションツリーを自動的に作成できるので、以下のメリットがあります。

* *UI から手動で選択する場合よりも優れたパフォーマンスを実現*
* *顧客が既存のロケーションを独自のシステムから書き出して、直接 AEM に簡単に読み込むことができます。*

これにより、初回のプロジェクトセットアップ時または既存の AEM Screens プロジェクトを新しいロケーションに拡張する際に、時間と費用の両方を節約できます。

## アーキテクチャの概要 {#architectural-overview}

プロジェクトインポーター機能のアーキテクチャの概要を次の図に示します。

![screen_shot_2019-05-14at20618pm](assets/screen_shot_2019-05-14at20618pm.png)

### データモデル {#data-model}

プロジェクトインポーターのデータモデルを以下で説明します。

>[!NOTE]
>
>現在のリリースでは、ロケーションの読み込みのみサポートしています。

| **プロパティ** | **説明** |
|---|---|
| ***`path {string*}`*** | ロケーションのリソースパス |
| ***`[./jcr:title] {string*}`*** | 使用するテンプレートの名前（*screens/core/templates/location* の場合は location） |
| ***`template {string}`*** | ページに使用するタイトル（オプション） |
| ***`[./jcr:description] {string}`*** | ページに使用する説明（オプション） |

したがって、スプレッドシート（CSV/XLS）ファイルには次の列が必要です。

* **path {string}**：読み込む場所のパス。プロジェクトの場所フォルダーをルートとします（つまり、*`/foo`* は *`/content/screens/<project>/locations/foo`* に読み込まれます）。
* **template {string}**：新しい場所に使用するテンプレート。今のところ、使用可能な値は「location」だけですが、今後、すべての Screens テンプレート（`display`、`sequencechannel` など）に拡張される予定です。
* **[。/*] {string}**：場所（つまり、`./jcr:title`、`./jcr:description`、`./foo, ./bar`）に設定する任意のオプションプロパティ。現在のリリースではフィルタリングはできません。

>[!NOTE]
>
>上記の条件に一致しない列は無視されます。例えば、シート（CSV/XLS）ファイルで&#x200B;**パス**、**テンプレート**、**タイトル**、および&#x200B;**説明**&#x200B;以外の列が定義されている場合、これらのフィールドは無視されます。また、**プロジェクトインポーター**&#x200B;では、プロジェクトを AEM Screens プロジェクトに読み込むための追加フィールドを検証しません。

## プロジェクトインポーターの使用 {#using-project-importer}

この節では、AEM Screens プロジェクトでのプロジェクトインポーターの使用方法について説明します。

>[!CAUTION]
>
>制限事項：
>
>* CSV／XLS／XLSX 拡張子以外のファイルは、現在のリリースではサポートされていません。
>* 読み込まれるファイルに対してプロパティのフィルタリングは行われず、「./」で始まるものはすべて読み込まれます。
>

### 前提条件 {#prerequisites}

* **DemoProjectImport** というタイトルのプロジェクトを作成します。

* 読み込む必要があるサンプル CSV または Excel ファイルを使用します。

デモ用に次の Excel ファイルをダウンロードできます。

[ファイルを入手](assets/minimal-file.xls)

### 最低限必要なフィールドを含んだファイルの読み込み {#importing-the-file-with-minimum-required-fields}

最小限の必須フィールドを含むファイルを場所フォルダーに読み込むには、以下の手順に従います。

>[!NOTE]
>
>次の例は、プロジェクトへの読み込みに最低限必要な 4 つのフィールドを示しています。

![screen_shot_2019-05-14at21523pm](assets/screen_shot_2019-05-14at21523pm.png)

1. AEM Screens プロジェクト（**DemoProjectImport**）に移動します。

   ![screen_shot_2019-05-12at52651am](assets/screen_shot_2019-05-12at52651am.png)

1. プロジェクト DemoProjectImporter をクリック**ます。 **>** 作成 **>** サイドバーから**場所を読み込みます。

   ![screen_shot_2019-05-12at52433am](assets/screen_shot_2019-05-12at52433am.png)

1. **読み込み**&#x200B;ウィザードが表示されます。場所を含むプロジェクトのファイルをクリックするか、ファイル（***minimal-file.xls***）からダウンロードしました *前提条件* セクション。

   ファイルを選択したら、 **次**.

   ![screen_shot_2019-05-15at113718am](assets/screen_shot_2019-05-15at113718am.png)

1. 読み込みウィザードでファイル（ロケーション）の内容を確認し、「**読み込み**」をクリックします。

   ![screen_shot_2019-05-12at53131am](assets/screen_shot_2019-05-12at53131am.png)

1. その結果、プロジェクトに読み込まれたすべての場所が表示されるようになります。

   ![screen_shot_2019-05-12at53450am](assets/screen_shot_2019-05-12at53450am.png)
