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
TQID: https://experienceleague.adobe.com/XwcKgrrDLuCYSLfTk4VyliKQdTn5O2HH8CUvwCJr9Pc
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 669
ht-degree: 80%

---

# ファイルをソースとする新しいプロジェクトインポーター {#new-project-importer-from-file}

ここでは、CSV／XLS スプレッドシートから AEM Screens プロジェクトに一連のロケーションを一括で読み込む機能について説明します。

## はじめに {#introduction}

>[!IMPORTANT]
>このコンテンツは、AEM オンプレミス/AMS （AEM 6.5LTSおよびAEM 6.5）に対して有効です。 AEM as a Cloud Service Screensの内容については、[AEM as a Cloud Service ガイド ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)を参照してください。

AEM Screens プロジェクトを組織で初めて設定する場合は、すべてのロケーションも作成します。 プロジェクトに多数のロケーションが含まれる場合は、UI で何回も選択したり待機したりする退屈なタスクが多く発生します。

この機能は、プロジェクトのセットアップに要する時間を短縮して、予算の問題を解決することを目的としています。

この機能では、作成者が入力ファイルとしてスプレッドシートを提供でき、システムがバックエンドにロケーションツリーを自動的に作成できるので、以下のメリットがあります。

* *UI を使用して手動で選択するよりも、はるかに優れたパフォーマンスを実現します*
* *顧客は既存のロケーションを独自のシステムから書き出して、直接 AEM に簡単に読み込むことができます*

このプロセスにより、初回のプロジェクトセットアップ時または既存の AEM Screens プロジェクトを新しいロケーションに拡張する際に、時間と費用の両方を節約できます。

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

* **パス{string}** - インポートする場所のパス。パスのルートはプロジェクトの場所フォルダーです（つまり、*`/foo`*&#x200B;は&#x200B;*`/content/screens/<project>/locations/foo`*&#x200B;にインポートされます）
* **テンプレート{string}** – 新しい場所に使用するテンプレート。現在許可されている値は「location」のみですが、この値は今後のすべての`Screens` テンプレートに拡張されます（`display`、`sequencechannel`など）
* **[./*] {string}** – 場所に設定する任意のオプションのプロパティ （つまり、`./jcr:title`、`./jcr:description`、`./foo, ./bar`）。 現在のリリースではフィルタリングはできません。

>[!NOTE]
>
>上記の条件に一致しない列は無視されます。 例えば、シート（CSV/XLS）ファイルで&#x200B;**パス**、**テンプレート**、**タイトル**、および&#x200B;**説明**&#x200B;以外の列が定義されている場合、これらのフィールドは無視されます。 また、**プロジェクトインポーター**&#x200B;では、プロジェクトを AEM Screens プロジェクトに読み込むための追加フィールドを検証しません。

## プロジェクトインポーターの使用 {#using-project-importer}

この節では、AEM Screens プロジェクトでのプロジェクトインポーターの使用方法について説明します。

>[!CAUTION]
>
>制限事項：
>
>* CSV／XLS／XLSX 拡張子以外のファイルは、現在のリリースではサポートされていません。
>* 読み込んだファイルに対してプロパティのフィルタリングは存在せず、「。/」で始まるものは読み込まれます。
>

### 前提条件 {#prerequisites}

* **DemoProjectImport** というタイトルのプロジェクトを作成します。

* 読み込む必要があるサンプル CSV または Excel ファイルを使用します。

デモ用に次の Excel ファイルをダウンロードできます。

[ファイルの取得](assets/minimal-file.xls)

### 最低限必要なフィールドを含んだファイルの読み込み {#importing-the-file-with-minimum-required-fields}

最小限の必須フィールドを含むファイルをロケーションフォルダーに読み込むには、以下の手順に従います。

>[!NOTE]
>
>次の例は、プロジェクトへの読み込みに最低限必要な 4 つのフィールドを示しています。

![screen_shot_2019-05-14at21523pm](assets/screen_shot_2019-05-14at21523pm.png)

1. AEM Screens プロジェクト（**DemoProjectImport**）に移動します。

   ![screen_shot_2019-05-12at52651am](assets/screen_shot_2019-05-12at52651am.png)

1. サイドバーの **DemoProjectImporter**／**作成**／**ロケーションを読み込む**をクリックします。

   ![screen_shot_2019-05-12at52433am](assets/screen_shot_2019-05-12at52433am.png)

1. **読み込み**&#x200B;ウィザードが表示されます。 ロケーションを含むプロジェクトのファイルをクリックするか、*前提条件*&#x200B;の節でダウンロードした ***minimal-file.xls*** ファイルをクリックします。

   ファイルを選択したら、「**次へ**」をクリックします。

   ![screen_shot_2019-05-15at113718am](assets/screen_shot_2019-05-15at113718am.png)

1. 読み込みウィザードでファイル（ロケーション）の内容を確認し、「**読み込み**」をクリックします。

   ![screen_shot_2019-05-12at53131am](assets/screen_shot_2019-05-12at53131am.png)

1. その結果、プロジェクトに読み込まれたすべての場所が表示されるようになります。

   ![screen_shot_2019-05-12at53450am](assets/screen_shot_2019-05-12at53450am.png)
