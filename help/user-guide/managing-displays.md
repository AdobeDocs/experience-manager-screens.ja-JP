---
title: ディスプレイの作成と管理
seo-title: ディスプレイの管理
description: このページに従って、新しいディスプレイおよびデバイスの設定について学びます。さらに、ディスプレイダッシュボードについて学びます。
seo-description: このページに従って、新しいディスプレイおよびデバイスの設定について学びます。さらに、ディスプレイダッシュボードについて学びます。
uuid: dfde0740-5c8b-4e6c-bc83-bf8fbb31a16a
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: f8e2e7a3-f3a1-4c35-b055-166752c3fb86
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# ディスプレイの作成と管理 {#creating-and-managing-displays}

ディスプレイとはスクリーンの仮想グループで、通常は並んで配置されています。ディスプレイのインストールは通常、永続的です。オブジェクトコンテンツの作成者はこれを操作し、常に物理的なディスプレイの代わりに論理的なディスプレイとして参照します。

場所を作成したら、場所のために新しいディスプレイを作成する必要があります。

このページでは、スクリーン用のディスプレイの作成および管理を示します。

**前提条件**:

* [スクリーンの設定および展開](configuring-screens-introduction.md)
* [画面プロジェクトの作成と管理](creating-a-screens-project.md)
* [チャネルの作成と管理](managing-channels.md)
* [場所の作成と管理](managing-locations.md)

## 新しいディスプレイの作成 {#creating-a-new-display}

>[!NOTE]
>
>ディスプレイを作成する前に場所を作成する必要があります。To see how to create a location, see [Create and Manage Locations](managing-locations.md) for more information.

新しいディスプレイを場所に作成するには、次の手順に従います。

1. Navigate to the appropriate location, for example `http://localhost:4502/screens.html/content/screens/TestProject`.
1. 場所フォルダーを選択し、アクションバーのプラス記号アイコンの横にある「**作成**」をタップまたはクリックします。ウィザードが開きます。
1. Select **Display** from the **Create** wizard and click **Next**.

1. Enter **Name** and **Title** for your display location.

1. Under the **Display** tab, choose the details of the Layout. Choose the desired **Resolution** (example as, as **Full HD**). また、デバイスの数を水平方向および垂直方向に選択できます。

1. 「**作成**」をクリックします。

The display (*StoreDisplay*) is created and added to the location (*SanJose*).

![display](assets/display.gif)

ディスプレイを配置したら、次の手順は、その特定のディスプレイのためにデバイス設定を作成することです。下のセクションに従って、新しいデバイス設定を作成します。

>[!NOTE]
>
>**次の手順**：
>
>場所にディスプレイを作成したら、コンテンツを利用するためにチャネルをディスプレイに割り当てる必要があります。
>
>See [Assign Channels](channel-assignment.md) section to learn how to assign a channel to the display.

## 新しいデバイス設定の作成 {#creating-a-new-device-config}

デバイス設定は、まだインストールされていない実際のデジタルサイネージデバイスのプレースフォルダーとして機能します。

下の手順に従って、新しいデバイス設定を作成します。

1. 例えば、適切な表示に移動します `http://localhost:4502/screens.html/content/screens/TestProject/locations/newlocation`。
1. 表示フォルダーを選択し、アクションバーの「**ダッシュボードを表示**」をタップまたはクリックします。
1. Tap/click the **+ Add Device Config** on the top right of the **Devices** panel.

1. Select the **Device Config** as the required template as and tap/click **Next**.

1. 必要に応じてプロパティを入力し、「**作成**」をタップまたはクリックします。

The device config is created and added to the current display (in the following demonstration, the new device config is *DeviceConfig*).

![deviceconfig](assets/deviceconfig.gif)

デバイス設定が場所のディスプレイに設定されたら、次の手順はチャネルをディスプレイに割り当てることです。

>[!NOTE]
>
>デバイス設定が場所のディスプレイに設定されたら、次の手順はチャネルをディスプレイに割り当てることです。
>
>As shown in the figure below, if the device config is displayed as unassigned in the **DEVICES** pannel, if no channel is assigned to that particular device config.
>
>チャネルの作成や管理について事前に理解しておく必要があります。詳しくは [、「チャネルの作成と管理](managing-channels.md) 」を参照してください。

![chlimage_1-9](assets/chlimage_1-9.png)

## ディスプレイダッシュボード {#display-dashboard}

ディスプレイダッシュボードには、ディスプレイデバイス管理デバイスおよびデバイスのデバイス設定用の様々なパネルがあります。

![screen_shot_2018-08-23at42810pm](assets/screen_shot_2018-08-23at42810pm.png)

>[!NOTE]
>
>各アイテムを個別にトリガーする代わりに、ダッシュボードリストを選択して、アイテムのバルクアクションをトリガーできます。
>
>例えば、ディスプレイダッシュボードから複数のチャネルを選択する方法を次の図に示します。

![cqdoc9456](assets/cqdoc9456.gif)

### ディスプレイ情報パネル {#display-information-panel}

**ディスプレイ情報**&#x200B;パネルは、ディスプレイのプロパティを表示します。

Click on the (**...**) in the top right corner in the **DISPLAY INFORMATION **panel to view the properties and preview the display.

![chlimage_1-10](assets/chlimage_1-10.png)

#### プロパティの表示 {#viewing-properties}

「**プロパティ**」をクリックして、ディスプレイのプロパティを表示または変更します。

Additionally, you can adjust the event timer value for your interactive channel in **Idle timeout **property under **Display** tab. デフォルト値は *300 秒*&#x200B;に設定されています。

Use **CRXDE Lite**, to access the **idleTimeout** property, that is, `http://localhost:4502/crx/de/index.jsp#/content/screens/we-retail/locations/demo/flagship/single/jcr%3Acontent/channels` .

![chlimage_1-1](assets/chlimage_1-1.gif)

### 割り当て済みチャネルパネル {#assigned-channels-panel}

**チャネルの割り当て**&#x200B;パネルには、このデバイスに割り当てられたチャネルが表示されます。

![チリメージ_1-11](assets/chlimage_1-11.png)

### デバイスパネル {#devices-panel}

**デバイス**&#x200B;パネルには、デバイス設定の情報が表示されます。

Click on the (**...**) in the top right corner in the **DEVICES **panel to add device configs and update devices.

![チリメージ_1-12](assets/chlimage_1-12.png)

さらに、デバイス設定をクリックして、プロパティを表示したり、デバイスを割り当てたり、完全に削除したりします。

![チリメージ_1-13](assets/chlimage_1-13.png)

#### 次の手順 {#the-next-steps}

場所のためのディスプレイの作成が完了したら、チャネルをディスプレイに割り当てる必要があります。

See [Assign Channels](channel-assignment.md) for more details.
