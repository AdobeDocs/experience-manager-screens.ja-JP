---
title: コンテンツ割り当てレポート
description: このページでは、コンテンツ割り当てレポートのダウンロードと使用方法について説明します。
translation-type: tm+mt
source-git-commit: b93baeeb26e48b906ee1ddfc034112f8b73615af
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 3%

---


# コンテンツ割り当てレポート {#content-assignment-report}

コンテンツ割り当てレポート機能を使用すると、AEM Screens管理者または作成者は、*コンテンツ割り当てレポート*&#x200B;をスプレッドシート形式で書き出すことができます。

## コンテンツ割り当てレポートの使用{#using-content-assignment-report}

コンテンツ割り当てレポートを使用すると、AEM Screensの作成者または管理者は、AEM Screensプロジェクトで作成されたすべてのチャネルの画像、ビデオなど、すべてのアセットを含むレポートをダウンロードできます。 また、指定されたすべてのディスプレイに割り当てられているチャネル全体、および指定されたディスプレイに割り当てられているすべてのデバイスに関する情報も含まれます。

コンテンツの割り当てレポートは、選択したAEM Screensプロジェクト内のすべてのチャネル、アセット、表示、デバイスをプレビューできるだけでなく、プロジェクトの高レベルな構造を提供します。

### コンテンツ割り当てレポートの使用{#downloading-content-assignment-report-fp}

#### プロジェクトのセットアップ {#setting-up-project}

次の手順に従って、AEM Screensプロジェクトからコンテンツ割り当てレポートをダウンロードします。

1. 「**DemoScreens**」というタイトルのAEM Screensを作成します。

   ![画像](/help/user-guide/assets/content-assignment-report/car-1.png)

1. **DemoScreens**&#x200B;に、**ChannelOne**&#x200B;と&#x200B;**ChannelTwo**&#x200B;のように、2つのシーケンスチャネルーを作成します。

   ![画像](/help/user-guide/assets/content-assignment-report/car-2.png)

1. 「**ChannelOne**」を選択し、アクションバーの「**編集**」をクリックします。 このチャネルに追加対するアセット（画像/ビデオ）は少数です。 同様に、**ChannelTwo**&#x200B;にアセットを追加します。

1. **DemoScreens** —> **場所**&#x200B;から場所フォルダーに移動し、**サンノゼ**、**ダブリン**、**SanFrancisco**&#x200B;の3つの場所を作成します。

   ![画像](/help/user-guide/assets/content-assignment-report/car-3.png)

1. 各場所に移動し、**サンノゼ**&#x200B;の下&#x200B;**サンノゼ**、**ダブリン**&#x200B;の下&#x200B;**ダブリンメイン**、**SanFranciscoMainなどの各場所のディスプレイを作成します。**&#x200B;サンフランシスコ&#x200B;**の**&#x200B;の場所。

1. 各ディスプレイにデバイスを割り当てます。

   >[!NOTE]
   >ディスプレイへのチャネルの割り当てについては、[チャネルの割り当て](/help/user-guide/channel-assignment.md)を参照してください。

#### コンテンツ割り当てレポートのダウンロード{#downloading-content-assignment-report}

前の手順に示すように、AEM Screensプロジェクトをセットアップし、各場所に表示を割り当てたら、コンテンツ割り当てレポートをダウンロードする準備が整います。

>[!NOTE]
>コンテンツ割り当てレポート機能には、プロジェクトレベルでのみアクセスできます。

コンテンツ割り当てレポートをダウンロードするには、次の手順に従います。

1. AEM Screensプロジェクトに移動し、プロジェクト&#x200B;**DemoScreens**&#x200B;を選択します。

1. アクションバーの&#x200B;**コンテンツ割り当てレポート**&#x200B;をクリックします。 Excelシートがローカルマシンにダウンロードされます。

   ![画像](/help/user-guide/assets/content-assignment-report/can-download.png)

   >[!NOTE]
   >ダウンロードしたスプレッドシートは、**チャネル**、**アセット**、**表示**、**デバイス**&#x200B;の4つの列で構成され、AEM Screensプロジェクトに関するこれら4つのエンティティをさらに調査できます。





