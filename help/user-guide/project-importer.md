---
title: ファイルをソースとする新しいプロジェクトインポーター
description: この機能を使用すると、CSV/XLS スプレッドシートからAEM Screens プロジェクトに一連の場所を一括読み込みできます。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
docset: aem65
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 3bff9ef3-0d6f-41d8-a8ef-bcc5a795990e
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '619'
ht-degree: 47%

---

# ファイルをソースとする新しいプロジェクトインポーター {#new-project-importer-from-file}

ここでは、CSV／XLS スプレッドシートから AEM Screens プロジェクトに一連のロケーションを一括で読み込む機能について説明します。

## はじめに {#introduction}

組織で初めてAEM Screens プロジェクトを設定する場合は、すべての場所も作成します。 プロジェクトに多数の場所が含まれる場合、UI でのクリックや待機が多くなる面倒なタスクになります。

この機能は、プロジェクトのセットアップに要する時間を短縮して、予算の問題を解決することを目的としています。

この機能では、作成者が入力ファイルとしてスプレッドシートを提供でき、システムがバックエンドにロケーションツリーを自動的に作成できるので、以下のメリットがあります。

* *手動で UI をクリックするよりも大幅にパフォーマンスが向上します*
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

スプレッドシート（CSV/XLS）ファイルには、次の列が必要です。

* **パス {string}** - インポートする場所のパス。パスのルートは、プロジェクトの場所フォルダー（つまり、 *`/foo`* はにインポートされます。 *`/content/screens/<project>/locations/foo`*）
* **template {string}**  – 新しい場所に使用するテンプレート。現時点で許可されている値は「location」ですが、今後、すべての Screens テンプレートに拡張されます（`display`, `sequencechannel`など）。
* **[。/*] {string}**  – その場所に設定する任意のオプションプロパティ（つまり、 `./jcr:title`, `./jcr:description`, `./foo, ./bar`）に設定します。 現在のリリースではフィルタリングはできません。

>[!NOTE]
>
>上記の条件に一致しない列は無視されます。 例えば、シート（CSV/XLS）ファイルで次の以外の列が定義されているとします。 **パス**, **template**, **タイトル**、および **説明** ファイル内のこれらのフィールドは無視されます。 また、 **プロジェクトインポーター** では、プロジェクトをAEM Screens プロジェクトに読み込むための追加フィールドを検証しません。

## プロジェクトインポーターの使用 {#using-project-importer}

この節では、AEM Screens プロジェクトでのプロジェクトインポーターの使用方法について説明します。

>[!CAUTION]
>
>制限事項：
>
>* CSV／XLS／XLSX 拡張子以外のファイルは、現在のリリースではサポートされていません。
>* 読み込んだファイルおよび「」で始まるすべてのファイルに対して、プロパティのフィルタリングは存在しません。/」が読み込まれます。
>

### 前提条件 {#prerequisites}

* というタイトルのプロジェクトの作成 **DemoProjectImport**

* 読み込む必要があるサンプルの CSV または Excel ファイルを使用します。

デモ用に次の Excel ファイルをダウンロードできます。

[ファイルを入手](assets/minimal-file.xls)

### 最低限必要なフィールドを含んだファイルの読み込み {#importing-the-file-with-minimum-required-fields}

最低限必要なフィールドを含んだ場所フォルダーにファイルをインポートするには、次の手順に従います。

>[!NOTE]
>
>次の例は、プロジェクトへの読み込みに最低限必要な 4 つのフィールドを示しています。

![screen_shot_2019-05-14at21523pm](assets/screen_shot_2019-05-14at21523pm.png)

1. AEM Screens プロジェクト（**DemoProjectImport**）に移動します。

   ![screen_shot_2019-05-12at52651am](assets/screen_shot_2019-05-12at52651am.png)

1. プロジェクト ** DemoProjectImporter を選択します。 **>** 作成 **>** サイドバーから**場所を読み込みます。

   ![screen_shot_2019-05-12at52433am](assets/screen_shot_2019-05-12at52433am.png)

1. この **インポート** ウィザードが表示されます。 場所を含むプロジェクトのファイルを選択するか、ファイル（***minimal-file.xls***）からダウンロードしました *前提条件* セクション。

   ファイルを選択したら、 **次**.

   ![screen_shot_2019-05-15at113718am](assets/screen_shot_2019-05-15at113718am.png)

1. 読み込みウィザードでファイル（ロケーション）の内容を確認し、「**読み込み**」をクリックします。

   ![screen_shot_2019-05-12at53131am](assets/screen_shot_2019-05-12at53131am.png)

1. その結果、プロジェクトに読み込まれたすべての場所を表示できるようになりました。

   ![screen_shot_2019-05-12at53450am](assets/screen_shot_2019-05-12at53450am.png)
