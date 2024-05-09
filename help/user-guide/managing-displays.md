---
title: ディスプレイの作成と管理
description: AEM Screens でのディスプレイとデバイス設定の作成について説明します。また、ディスプレイダッシュボードについて学びます。
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: c55dc128-208d-4379-95a8-60a39d495dc0
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 53%

---

# ディスプレイの作成と管理 {#creating-and-managing-displays}

ディスプレイとは Screens の仮想グループのことで、隣り合って配置されます。ディスプレイは、インストールに関して永続的です。これは、コンテンツ作成者がと連携し、物理的なカウンター部分ではなく常に論理表示としてを参照するオブジェクトです。

場所を作成する場合は、場所用のディスプレイを作成する必要があります。

ここでは、Screens プロジェクトのディスプレイの作成と管理について説明します。

**前提条件**：

* [Screens の設定とデプロイ](configuring-screens-introduction.md)
* [Screens プロジェクトの作成と管理](creating-a-screens-project.md)
* [チャネルの作成と管理](managing-channels.md)
* [ロケーションの作成と管理](managing-locations.md)

## 新しいディスプレイの作成 {#creating-a-new-display}

>[!NOTE]
>
>ディスプレイを作成する前に、場所を作成します。詳しくは、[場所の作成と管理](managing-locations.md)を参照してください。

1. 該当するロケーション（例：`http://localhost:4502/screens.html/content/screens/TestProject`）に移動します。
1. 場所フォルダーをクリックし、 **作成** これは、アクションバーのプラスアイコンの横にあります。
1. クリック **表示** から **作成** ウィザードで、 **次**.
1. を入力 **名前** および **タイトル** ディスプレイの場所の場合。
1. 「**ディスプレイ**」タブで、レイアウトの詳細を選択します。目的の「**解像度**」（「**フル HD**」など）を選択します。水平方向と垂直方向のデバイスの数を選択します。
1. 「**作成**」をクリックします。

ディスプレイ（*StoreDisplay*）が作成され、ロケーション（*SanJose*）に追加されます。

![display](assets/display.gif)

ディスプレイを配置したら、次に、その特定のディスプレイのデバイス設定を作成します。

>[!NOTE]
>
>**次のステップ**:
>
>ロケーション用のディスプレイを作成する場合は、コンテンツを使用するためにディスプレイにチャネルを割り当てます。
>
>を参照してください。 [チャネルの割り当て](channel-assignment.md) ディスプレイにチャネルを割り当てる方法については、この節を参照してください。

## 新しいデバイス設定の作成 {#creating-a-new-device-config}

デバイス設定は、まだインストールされていない実際のデジタルサイネージデバイスのプレースフォルダーとして機能します。

1. 該当するディスプレイ（例：`http://localhost:4502/screens.html/content/screens/TestProject/locations/newlocation`）に移動します。
1. 表示フォルダーをクリックし、 **ダッシュボードの表示** アクションバーに表示されます。
1. クリック **+ デバイス設定を追加** の右上に **デバイス** パネル。

1. 「」をクリックします **デバイス設定** 必要なテンプレートとしてを使用し、をクリックします **次**.

1. 必要に応じてプロパティを入力し、 **作成**.

デバイス設定が作成され、現在のディスプレイに追加されます（以下のデモでは、この新しいデバイス設定は *DeviceConfig* です）。

![deviceconfig](assets/deviceconfig.gif)

>[!NOTE]
>
>の場所でディスプレイにデバイス設定を設定したら、次にディスプレイにチャネルを割り当てます。
>
>次の図に示すように、特定のデバイス設定にチャネルが割り当てられていない場合、デバイス設定が&#x200B;**デバイス**&#x200B;パネルに未割り当てとして表示されます。
>
>チャネルの作成と管理に関する知識が必要です。 詳しくは、[チャネルの作成と管理](managing-channels.md)を参照してください。

![chlimage_1-9](assets/chlimage_1-9.png)

## ディスプレイダッシュボード {#display-dashboard}

表示ダッシュボードには、表示デバイスを管理するための様々なパネルが用意されています。 また、デバイスを設定することもできます。

![screen_shot_2018-08-23at42810pm](assets/screen_shot_2018-08-23at42810pm.png)

>[!NOTE]
>
>各項目を個別に確認する代わりに、ダッシュボードリストをクリックしたり、項目に対して一括アクションをトリガーしたりできます。
>
>例えば、次の画像は、表示ダッシュボードから複数のチャネルをクリックする方法を示しています。

![cqdoc9456](assets/cqdoc9456.gif)

### ディスプレイの情報パネル {#display-information-panel}

**ディスプレイ情報**&#x200B;パネルは、ディスプレイのプロパティを表示します。

**ディスプレイ情報**&#x200B;パネルの右上隅にある（**...**）をクリックすると、プロパティを表示し、ディスプレイをプレビューできます。


#### プロパティの表示 {#viewing-properties}

「**プロパティ**」をクリックすると、ディスプレイのプロパティを表示または変更できます。

また、インタラクティブチャネルのイベントタイマーの値は、の下で調整できます **表示** タブ。 デフォルト値は *300 秒*&#x200B;に設定されています。

使用方法 **CRXDE Lite**&#x200B;にアクセスします。 **idleTimeout** プロパティ。つまり、 `http://localhost:4502/crx/de/index.jsp#/content/screens/we-retail/locations/demo/flagship/single/jcr%3Acontent/channels`.


### 割り当て済みチャネルパネル {#assigned-channels-panel}

**チャネルの割り当て**&#x200B;パネルには、このデバイスに割り当てられたチャネルが表示されます。


### デバイスパネル {#devices-panel}

この **デバイス** パネルには、デバイス設定に関する情報が表示されます。

クリック （**...**）を選択します。 **デバイス** パネルを使用すると、デバイス設定を追加し、デバイスを更新できます。

また、デバイス設定をクリックすると、プロパティの表示、デバイスの割り当て、またはデバイスの完全削除を行うことができます。

![chlimage_1-13](assets/chlimage_1-13.png)

#### 次の手順 {#the-next-steps}

場所のディスプレイの作成が完了したら、ディスプレイにチャネルを割り当てます。

詳しくは、[チャネルの割り当て](channel-assignment.md)を参照してください。
