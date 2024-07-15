---
title: コンテンツ割り当てレポート
description: AEM Screens に関連するコンテンツ割り当てレポートのダウンロードと使用法について説明します。
feature: Authoring Screens
role: Developer
level: Intermediate
exl-id: 7397aa99-97fc-45c2-a157-c1bd7b1700b5
source-git-commit: f7653d8b386c02f510eb7a770cf3cdc22c41a5fb
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 100%

---

# コンテンツ割り当てレポート {#content-assignment-report}

コンテンツ割り当てレポート機能を使用すると、AEM Screens 管理者または作成者は、*コンテンツ割り当てレポート*&#x200B;をスプレッドシート形式で書き出すことができます。

## コンテンツ割り当てレポートの使用 {#using-content-assignment-report}

コンテンツ割り当てレポートを使用すると、AEM Screens の作成者または管理者は、AEM Screens プロジェクトで作成されたすべてのチャネルの画像、ビデオなど、すべてのアセットを含むレポートをダウンロードできます。また、指定されたすべてのディスプレイに割り当てられているチャネル全体、および指定されたディスプレイに割り当てられているすべてのデバイスに関する情報も含まれます。

コンテンツの割り当てレポートは、選択した AEM Screens プロジェクト内のすべてのチャネル、アセット、表示、デバイスをプレビューできるだけでなく、プロジェクトの大まかな構造を提供します。


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

前の手順に示すように、AEM Screens プロジェクトをセットアップし、各場所に表示を割り当てたら、コンテンツ割り当てレポートをダウンロードします。

>[!NOTE]
>コンテンツ割り当てレポート機能には、プロジェクトレベルでのみアクセスできます。

コンテンツ割り当てレポートをダウンロードするには、次の手順に従います。

1. AEM Screens プロジェクトに移動し、**DemoScreens** プロジェクトをクリックします。

1. アクションバーの「**コンテンツ割り当てレポート**」をクリックします。

   ![画像](/help/user-guide/assets/content-assignment-report/can-download.png)

1. ダウンロードしたスプレッドシートは、「**ロケーション**」と「**コンテンツ**」の 2 つのタブで構成されています。「ロケーション」タブには、「**ロケーション**」、「**ディスプレイ**」、「**チャネル**」、「**デバイス**」の 4 つの列が表示され、AEM Screens プロジェクトに関するこれら 4 つのエンティティを調査するために使用できます。

   ![画像](/help/user-guide/assets/content-assignment-report/report-sheet1.png)

   >[!NOTE]
   >スプレッドシートに表示されるデータは、読みやすい形式でアルファベット順に並べ替えられています。

1. 「**チャネル**」列からいずれかのチャネルを選択すると、「**コンテンツ**」タブが開きます。次に、そのチャネルに直接移動すると、その特定のチャネルに関連付けられたアセット（画像とビデオ）に関する情報が表示されます。

   ![画像](/help/user-guide/assets/content-assignment-report/report-sheet2.png)
