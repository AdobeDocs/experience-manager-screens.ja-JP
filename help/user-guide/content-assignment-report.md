---
title: コンテンツ割り当てレポート
description: このページでは、コンテンツ割り当てレポートのダウンロードと使用方法について説明します。
feature: Authoring Screens
role: Developer
level: Intermediate
translation-type: ht
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: ht
source-wordcount: '336'
ht-degree: 100%

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

   >[!NOTE]
   >ダウンロードしたスプレッドシートは、**チャネル**、**Assets**、**表示**、**デバイス**&#x200B;の 4 つの列で構成され、AEM Screens プロジェクトに関するこれら 4 つのエンティティをさらに調査できます。

1. Excel シートが、AEM Screens プロジェクト名と同じ名前のプレフィックスが付いたローカルマシンにダウンロードされます。例えば、プロジェクト名が **DemoScreens** の場合、ダウンロードされるファイル名は **demoscreens-content-assignment-report.xlxs** になります。

   ![画像](/help/user-guide/assets/content-assignment-report/car-download1.png)

