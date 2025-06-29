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
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 98%

---

# ディスプレイの作成と管理 {#creating-and-managing-displays}

ディスプレイとは Screens の仮想グループのことで、隣り合って配置されます。ディスプレイは、インストールに関して永続的です。これは作成者が作業するオブジェクトコンテンツであり、物理的なディスプレイではなく常に論理的なディスプレイとして参照されます。

ロケーションを作成したら、ロケーションのディスプレイを作成する必要があります。

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
1. ロケーションフォルダーをクリックし、アクションバーのプラス記号アイコンの横にある「**作成**」をクリックします。
1. **作成**&#x200B;ウィザードで「**ディスプレイ**」をクリックし、「**次へ**」をクリックします。
1. ディスプレイのロケーションの「**名前**」と「**タイトル**」を入力します。
1. 「**ディスプレイ**」タブで、レイアウトの詳細を選択します。目的の「**解像度**」（「**フル HD**」など）を選択します。水平方向と垂直方向のデバイスの数を選択します。
1. 「**作成**」をクリックします。

ディスプレイ（*StoreDisplay*）が作成され、ロケーション（*SanJose*）に追加されます。

![display](assets/display.gif)

ディスプレイを配置したら、次は、その特定のディスプレイのデバイス設定を作成します。

>[!NOTE]
>
>**次のステップ**：
>
>ロケーションにディスプレイを作成したら、コンテンツを使用するためにディスプレイにチャネルを割り当てます。
>
>ディスプレイにチャネルを割り当てる方法については、[チャネルの割り当て](channel-assignment.md)の節を参照してください。

## 新しいデバイス設定の作成 {#creating-a-new-device-config}

デバイス設定は、まだインストールされていない実際のデジタルサイネージデバイスのプレースフォルダーとして機能します。

1. 該当するディスプレイ（例：`http://localhost:4502/screens.html/content/screens/TestProject/locations/newlocation`）に移動します。
1. ディスプレイフォルダーをクリックし、アクションバーの「**ダッシュボードを表示**」をクリックします。
1. **デバイス**&#x200B;パネルの右上にある「**+ デバイス設定を追加**」をクリックします。

1. 必要なテンプレートとして **デバイス設定** をクリックし、「**次へ**」をクリックします。

1. 必要に応じてプロパティを入力し、「**作成**」をクリックします。

デバイス設定が作成され、現在のディスプレイに追加されます（以下のデモでは、この新しいデバイス設定は *DeviceConfig* です）。

![deviceconfig](assets/deviceconfig.gif)

>[!NOTE]
>
>デバイス設定がロケーションのディスプレイに設定されたら、次は、ディスプレイにチャネルを割り当てます。
>
>次の図に示すように、特定のデバイス設定にチャネルが割り当てられていない場合、デバイス設定が&#x200B;**デバイス**&#x200B;パネルに未割り当てとして表示されます。
>
>チャネルの作成や管理について事前に理解しておく必要があります。詳しくは、[チャネルの作成と管理](managing-channels.md)を参照してください。

![chlimage_1-9](assets/chlimage_1-9.png)

## ディスプレイダッシュボード {#display-dashboard}

ディスプレイダッシュボードには、ディスプレイデバイスを管理するための様々なパネルが用意されています。また、デバイスを設定することもできます。

![screen_shot_2018-08-23at42810pm](assets/screen_shot_2018-08-23at42810pm.png)

>[!NOTE]
>
>各アイテムを個別に処理するのではなく、ダッシュボードリストをクリックして、複数のアイテムに対して一括アクションをトリガーできます。
>
>例えば、ディスプレイダッシュボードから複数のチャネルをクリックする方法を次の図に示します。

![cqdoc9456](assets/cqdoc9456.gif)

### ディスプレイの情報パネル {#display-information-panel}

**ディスプレイ情報**&#x200B;パネルは、ディスプレイのプロパティを表示します。

**ディスプレイ情報**&#x200B;パネルの右上隅にある（**...**）をクリックすると、プロパティを表示し、ディスプレイをプレビューできます。


#### プロパティの表示 {#viewing-properties}

「**プロパティ**」をクリックすると、ディスプレイのプロパティを表示または変更できます。

また「**ディスプレイ**」タブで、インタラクティブチャネルのイベントタイマー値を調節できます。デフォルト値は *300 秒*&#x200B;に設定されています。

**CRXDE Lite** を使用して、**idleTimeout** プロパティ（`http://localhost:4502/crx/de/index.jsp#/content/screens/we-retail/locations/demo/flagship/single/jcr%3Acontent/channels`）にアクセスします。


### 割り当て済みチャネルパネル {#assigned-channels-panel}

**チャネルの割り当て**&#x200B;パネルには、このデバイスに割り当てられたチャネルが表示されます。


### デバイスパネル {#devices-panel}

**デバイス**&#x200B;パネルには、デバイス設定の情報が表示されます。

**デバイス**&#x200B;パネルの右上隅の「（**...**）」をクリックすると、デバイス設定を追加して、デバイスを更新できます。

また、デバイス設定をクリックすると、プロパティの表示、デバイスの割り当て、またはデバイスの完全削除を行うことができます。

![chlimage_1-13](assets/chlimage_1-13.png)

#### 次の手順 {#the-next-steps}

場所のディスプレイの作成が完了したら、ディスプレイにチャネルを割り当てます。

詳しくは、[チャネルの割り当て](channel-assignment.md)を参照してください。
