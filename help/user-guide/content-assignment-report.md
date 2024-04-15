---
title: コンテンツ割り当てレポート
description: コンテンツ割り当てレポートはAEM Screensに関連するので、ダウンロードと使用について説明します。
feature: Authoring Screens
role: Developer
level: Intermediate
exl-id: 7397aa99-97fc-45c2-a157-c1bd7b1700b5
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 30%

---

# コンテンツ割り当てレポート {#content-assignment-report}

コンテンツ割り当てレポート機能を使用すると、AEM Screens 管理者または作成者は、*コンテンツ割り当てレポート*&#x200B;をスプレッドシート形式で書き出すことができます。

## コンテンツ割り当てレポートの使用 {#using-content-assignment-report}

コンテンツ割り当てレポートを使用すると、AEM Screens作成者または管理者は、AEM Screens プロジェクトで作成されたすべてのチャネルの画像、ビデオなどのすべてのアセットを含んだレポートをダウンロードできます。 また、指定されたすべてのディスプレイに割り当てられたチャネル全体の情報と、その後、指定されたディスプレイに割り当てられたすべてのデバイスの情報も含まれます。

コンテンツ割り当てレポートを使用すると、選択したAEM Screens プロジェクトのすべてのチャネル、アセット、ディスプレイ、デバイスのプレビューが可能になるだけでなく、プロジェクトの構造の概要も提供されます。


### 前提条件 {#pre-reqs}

コンテンツ割り当てレポートをダウンロードする前に、チャネル、場所、デバイスでAEM Screens プロジェクトを設定していることを確認してください。
詳しくは、次のリソースを参照してください。

1. [プロジェクトの作成と管理](/help/user-guide/creating-a-screens-project.md)
1. [チャネルの作成と管理](/help/user-guide/managing-channels.md)
1. [ロケーションの作成と管理](/help/user-guide/managing-locations.md)
1. [ディスプレイの作成と管理](/help/user-guide/managing-displays.md)
1. [デバイスの作成](/help/user-guide/managing-devices.md)
1. [チャネルの割り当て](/help/user-guide/channel-assignment-latest-fp.md)


## コンテンツ割り当てレポートのダウンロード {#downloading-content-assignment-report-fp}

上記の手順に示すようにAEM Screens プロジェクトを設定し、各ロケーションにディスプレイを割り当てたら、コンテンツ割り当てレポートをダウンロードします。

>[!NOTE]
>コンテンツ割り当てレポート機能には、プロジェクトレベルでのみアクセスできます。

コンテンツ割り当てレポートをダウンロードするには、次の手順に従います。

1. AEM Screens プロジェクトに移動し、**DemoScreens** プロジェクトを選択します。

1. クリック **コンテンツ割り当てレポート** アクションバーから。

   ![画像](/help/user-guide/assets/content-assignment-report/can-download.png)

1. ダウンロードしたスプレッドシートは、「**ロケーション**」と「**コンテンツ**」の 2 つのタブで構成されています。「場所」タブには、次のような 4 つの列が表示されます **場所**, **ディスプレイ**, **チャネル**、および **デバイス** を使用すると、AEM Screens プロジェクトに関する 4 つのエンティティをさらに調査できます。

   ![画像](/help/user-guide/assets/content-assignment-report/report-sheet1.png)

   >[!NOTE]
   >スプレッドシートに表示されるデータは、読みやすい形式でアルファベット順に並べ替えられています。

1. いずれかのチャネルをクリックする **チャネル** 列を開くと、 **コンテンツ** タブ。 次に、そのチャネルに直接移動し、その特定のチャネルに関連付けられたアセット（画像とビデオ）に関する情報を提供します。

   ![画像](/help/user-guide/assets/content-assignment-report/report-sheet2.png)
