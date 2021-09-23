---
title: コンテンツ割り当てレポート
description: このページでは、コンテンツ割り当てレポートのダウンロードと使用方法について説明します。
feature: Authoring Screens
role: Developer
level: Intermediate
exl-id: 7397aa99-97fc-45c2-a157-c1bd7b1700b5
source-git-commit: 9e750b874253a5d1786e5ef78fc41d96e72b702d
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 72%

---

# コンテンツ割り当てレポート {#content-assignment-report}

コンテンツ割り当てレポート機能を使用すると、AEM Screens 管理者または作成者は、*コンテンツ割り当てレポート*&#x200B;をスプレッドシート形式で書き出すことができます。

## コンテンツ割り当てレポートの使用 {#using-content-assignment-report}

コンテンツ割り当てレポートを使用すると、AEM Screens の作成者または管理者は、AEM Screens プロジェクトで作成されたすべてのチャネルの画像、ビデオなど、すべてのアセットを含むレポートをダウンロードできます。また、指定されたすべてのディスプレイに割り当てられているチャネル全体、および指定されたディスプレイに割り当てられているすべてのデバイスに関する情報も含まれます。

コンテンツの割り当てレポートは、選択した AEM Screens プロジェクト内のすべてのチャネル、アセット、表示、デバイスをプレビューできるだけでなく、プロジェクトの高レベルな構造を提供します。


### 前提条件 {#pre-reqs}

コンテンツの割り当てレポートをダウンロードする前に、チャネル、場所、デバイスを含む AEM Screens プロジェクトが設定されていることを確認してください。
詳しくは、次のリソースを参照してください。

1. [プロジェクトの作成と管理](/help/user-guide/creating-a-screens-project.md)
1. [チャネルの作成と管理](/help/user-guide/managing-channels.md)
1. [ロケーションの作成と管理](/help/user-guide/managing-locations.md)
1. [ディスプレイの作成と管理](/help/user-guide/managing-displays.md)
1. [デバイスの作成](/help/user-guide/managing-devices.md)
1. [チャネルの割り当て](/help/user-guide/channel-assignment-latest-fp.md)


## コンテンツ割り当てレポートのダウンロード {#downloading-content-assignment-report-fp}

前の手順に示すように、AEM Screens プロジェクトをセットアップし、各場所に表示を割り当てたら、コンテンツ割り当てレポートをダウンロードする準備が整います。

>[!NOTE]
>コンテンツ割り当てレポート機能には、プロジェクトレベルでのみアクセスできます。

コンテンツ割り当てレポートをダウンロードするには、次の手順に従います。

1. AEM Screens プロジェクトに移動し、**DemoScreens** プロジェクトを選択します。

1. アクションバーの&#x200B;**コンテンツ割り当てレポート**&#x200B;をクリックします。

   ![画像](/help/user-guide/assets/content-assignment-report/can-download.png)

1. ダウンロードしたスプレッドシートは、「**場所**」および「**コンテンツ**」などの2つのタブで構成されます。 「場所」タブには、「**ロケーション**」、「**ディスプレイ**」、「**チャネル**」、「**デバイス**」の4つの列が表示され、AEM Screensプロジェクトに関する4つのエンティティをさらに調査できます。

   ![画像](/help/user-guide/assets/content-assignment-report/report-sheet1.png)

   >[!NOTE]
   >スプレッドシートに表示されるデータは、読みやすい形式でアルファベット順に並べ替えられます。

1. 「**チャネル**」列の任意のチャネルをクリックして「**コンテンツ**」タブを開くと、そのチャネルに直接移動し、そのチャネルに関連付けられたアセット（画像とビデオ）に関する情報が表示されます（下図を参照）。

   ![画像](/help/user-guide/assets/content-assignment-report/report-sheet2.png)
