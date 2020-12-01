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

コンテンツ割り当てレポート機能を使用すると、AEM Screens管理者や作成者は、 *コンテンツ割り当てレポートをスプレッドシート形式で書き出すことができます* 。

## コンテンツ割り当てレポートの使用 {#using-content-assignment-report}

コンテンツ割り当てレポートを使用すると、AEM Screensの作成者または管理者は、AEM Screensプロジェクトで作成されたすべてのチャネルの画像、ビデオなど、すべてのアセットを含むレポートをダウンロードできます。 また、指定されたすべてのディスプレイに割り当てられているチャネル全体、および指定されたディスプレイに割り当てられているすべてのデバイスに関する情報も含まれます。

コンテンツの割り当てレポートは、選択したAEM Screensプロジェクト内のすべてのチャネル、アセット、表示、デバイスをプレビューできるだけでなく、プロジェクトの高レベルな構造を提供します。

### コンテンツ割り当てレポートの使用 {#downloading-content-assignment-report-fp}

#### プロジェクトのセットアップ {#setting-up-project}

次の手順に従って、AEM Screensプロジェクトからコンテンツ割り当てレポートをダウンロードします。

1. Create an AEM Screens titled as **DemoScreens**.

   ![画像](/help/user-guide/assets/content-assignment-report/car-1.png)

1. DemoScreensで、ChannelOne **とChannelTwoのような2つのシーケンスチャネルーを作成し** ます ********。

   ![画像](/help/user-guide/assets/content-assignment-report/car-2.png)

1. Select **ChannelOne** and click **Edit** from the action bar. このチャネルに追加対するアセット（画像/ビデオ）は少数です。 同様に、ChannelTwoにアセットを追加し **ます**。

1. LocationsフォルダーにScreens **—>** Demoを **開き** 、SanJose Dublin Dublin Dublin San Francisco Locationsという名前で3つの場所を **作成します。Locationsフォルダに移動し**********&#x200B;ます。

   ![画像](/help/user-guide/assets/content-assignment-report/car-3.png)

1. 各場所に移動し、各場所に対して表示を作成します。例えば、SanJoseMain **Under SanJoseSanJose** MainLocationDublinMainLocation **San Francisco DublinLactionの下のSanJoseSanSanDDDDDDDDDDDDuDDDDDu** SuDuSiSSiSSinSiSanSanSanDSanDDuSSSDuSSSSSDu **************** DDulinLinLoLocoSLinSSLoLolinSLonSLoLoL

1. 各ディスプレイにデバイスを割り当てます。

   >[!NOTE]
   >To learn about assigning a channel to a display, refer to [Channel Assignment](/help/user-guide/channel-assignment.md).

#### コンテンツ割り当てレポートのダウンロード {#downloading-content-assignment-report}

前の手順に示すように、AEM Screensプロジェクトをセットアップし、各場所に表示を割り当てたら、コンテンツ割り当てレポートをダウンロードする準備が整います。

>[!NOTE]
>コンテンツ割り当てレポート機能には、プロジェクトレベルでのみアクセスできます。

コンテンツ割り当てレポートをダウンロードするには、次の手順に従います。

1. Navigate to your AEM Screens project and select the project **DemoScreens**.

1. アクションバーの「 **コンテンツ割り当てレポート** 」をクリックします。 Excelシートがローカルマシンにダウンロードされます。

   ![画像](/help/user-guide/assets/content-assignment-report/can-download.png)

   >[!NOTE]
   >ダウンロードしたスプレッドシートは、 **チャネル**、 **アセット**、表示、デバイスの4列で構成されます。また、 ******** AEM Screensプロジェクトに関するこれら4つのエンティティをさらに詳しく調べるために使用します。





