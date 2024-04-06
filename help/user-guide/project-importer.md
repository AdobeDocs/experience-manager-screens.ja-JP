---
title: ファイルをソースとする新しいプロジェクトインポーター
description: この機能を使用すると、CSV／XLS スプレッドシートから AEM Screens プロジェクトに一連のロケーションを一括で読み込むことができます。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
docset: aem65
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 3bff9ef3-0d6f-41d8-a8ef-bcc5a795990e
source-git-commit: 2b865165793b1c0f90f1351518e41096a57ea2ff
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 51%

---

# ファイルをソースとする新しいプロジェクトインポーター {#new-project-importer-from-file}

ここでは、CSV／XLS スプレッドシートから AEM Screens プロジェクトに一連のロケーションを一括で読み込む機能について説明します。

## はじめに {#introduction}

組織で初めてAEM Screensプロジェクトをセットアップする場合は、すべてのロケーションも作成する必要があります。 プロジェクトに多くの場所が含まれる場合は、UI での多くのクリックや待ち時間を伴う退屈な作業になります。

この機能は、プロジェクトのセットアップに要する時間を短縮して、予算の問題を解決することを目的としています。

この機能では、作成者が入力ファイルとしてスプレッドシートを提供でき、システムがバックエンドにロケーションツリーを自動的に作成できるので、以下のメリットがあります。

* *は、UI を使用して手動でクリックするよりも、はるかにパフォーマンスが優れています。*
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

したがって、スプレッドシート (CSV/XLS) ファイルには次の列が必要です。

* **パス {string}**  — 読み込む場所のパス。パスのルートはプロジェクトの場所フォルダー ( *`/foo`* 次にインポート： *`/content/screens/<project>/locations/foo`*)
* **テンプレート {string}**  — 新しい場所に使用するテンプレート（現時点では、許可されている値は「location」のみです）。ただし、これは、将来すべての Screens テンプレートに拡張されます (`display`, `sequencechannel`など )
* **[。/*] {string}**  — ロケーションに設定する任意のオプションプロパティ ( `./jcr:title`, `./jcr:description`, `./foo, ./bar`) をクリックします。 現在のリリースではフィルタリングは使用できません。

>[!NOTE]
>
>上記の条件に一致しない列は無視されます。 例えば、シート (CSV/XLS) ファイルに定義されている列の中に、 **パス**, **テンプレート**, **タイトル**、および **説明** ファイル内では、これらのフィールドは無視されます。 そして、 **プロジェクトインポーター** では、プロジェクトをAEM Screensプロジェクトに読み込むための、これらの追加フィールドは検証されません。

## プロジェクトインポーターの使用 {#using-project-importer}

この節では、AEM Screens プロジェクトでのプロジェクトインポーターの使用方法について説明します。

>[!CAUTION]
>
>制限事項：
>
>* CSV／XLS／XLSX 拡張子以外のファイルは、現在のリリースではサポートされていません。
>* 読み込まれたファイルおよび「 」で始まるすべてに対して、プロパティのフィルタリングは存在しません。/」が読み込まれます。
>

### 前提条件 {#prerequisites}

* というタイトルのプロジェクトを作成します。 **DemoProjectImport**

* 読み込む必要があるサンプル CSV または Excel ファイルを使用します。

デモ用に次の Excel ファイルをダウンロードできます。

[ファイルを入手](assets/minimal-file.xls)

### 最低限必要なフィールドを含んだファイルの読み込み {#importing-the-file-with-minimum-required-fields}

最低限必要なフィールドを含んだ場所フォルダーにファイルを読み込むには、以下の手順に従います。

>[!NOTE]
>
>次の例は、プロジェクトへの読み込みに最低限必要な 4 つのフィールドを示しています。

![screen_shot_2019-05-14at21523pm](assets/screen_shot_2019-05-14at21523pm.png)

1. AEM Screens プロジェクト（**DemoProjectImport**）に移動します。

   ![screen_shot_2019-05-12at52651am](assets/screen_shot_2019-05-12at52651am.png)

1. プロジェクトを選択します。** DemoProjectImporter **>** 作成 **>** ロケーションを読み込みま**。

   ![screen_shot_2019-05-12at52433am](assets/screen_shot_2019-05-12at52433am.png)

1. The **インポート** ウィザードが表示されます。 プロジェクトのロケーションを含むファイルを選択するか、ファイル (***minimal-file.xls***) を *前提条件* 」セクションに入力します。

   ファイルを選択したら、「**次へ**」をクリックします。

   ![screen_shot_2019-05-15at113718am](assets/screen_shot_2019-05-15at113718am.png)

1. 読み込みウィザードでファイル（ロケーション）の内容を確認し、「**読み込み**」をクリックします。

   ![screen_shot_2019-05-12at53131am](assets/screen_shot_2019-05-12at53131am.png)

1. その結果、プロジェクトに読み込まれたすべてのロケーションが表示されるようになりました。

   ![screen_shot_2019-05-12at53450am](assets/screen_shot_2019-05-12at53450am.png)
