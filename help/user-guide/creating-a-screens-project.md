---
title: プロジェクトの作成と管理
seo-title: プロジェクトの作成
description: このページに従って、新しいスクリーンプロジェクトの作成について学びます。
seo-description: このページに従って、新しいスクリーンプロジェクトの作成について学びます。
uuid: c73126ca-18d0-45b4-bdde-a3653082bfc4
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 00ea321c-3f79-4aa5-83cc-3fa2fe9e35d9
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# プロジェクトの作成と管理 {#creating-and-managing-projects}

AEM Screens には、Adobe Experience Manager のリンク（左上）を選択し、「スクリーン」を選択するとアクセスできます。

または、次の場所に直接移動できます。 `http://localhost:4502/screens.html/content/screens`![クリマージュ_1-14](assets/chlimage_1-14.png)

異なるプロジェクトは、ブランド、デプロイメント、お客様なども異なる場合があります。

![screen_shot_2018-08-23at105748am](assets/screen_shot_2018-08-23at105748am.png)

>[!NOTE]
>
>**ナビゲーションのヒント：**
>
>カーソルキーを使用しても、AEM 内の様々なフォルダーを移動できます。さらに、特定のエンティティを選択し、スペースバーを押すと、その特定のフォルダーのプロパティを編集または表示できます。

## 新しいスクリーンプロジェクトの作成 {#creating-a-new-screens-project}

下の手順に従って、新しいスクリーンプロジェクトを作成します。

1. AEM ダッシュボードから「**スクリーン**」を選択します。
1. Click **Create **--&gt;** Create Project **and **Create Screens Project** wizard will open.

1. Select the **Screens** template and click **Next**.

1. Enter the properties (**Title** and **Name**) as required and click **Create**.

![player1](assets/player1.gif)

>[!NOTE]
>
>By default, the initial structure will contain the **Schedules**, **Locations**, **Applications**, **Channels**, and **Devices** master pages, but this can be manually adjusted if needed. 使用可能なオプションがプロジェクトに関連しない場合は、オプションを削除できます。

プロジェクトが作成され、スクリーンプロジェクトコンソールに戻ります。これでプロジェクトを選択できます。

下の図に示すように、プロジェクトには 4 種類のフォルダーがあります。

* **スケジュール**
* **ロケーション**
* **アプリ管理**
* **チャネル**
* **デバイス**

![screen_shot_2018-08-23at110114am](assets/screen_shot_2018-08-23at110114am.png)

### プロパティの表示 {#viewing-properties}

Once you create the Screens project, click **Properties** on the action bar to edit properties of an exiting AEM Screens project.

![screen_shot_2018-08-23at110211am](assets/screen_shot_2018-08-23at110211am.png)

The following options allow you to edit/change properties of your *DemoProject*.

![screen_shot_2018-08-23at110409am](assets/screen_shot_2018-08-23at110409am.png)

### カスタムフォルダーの作成 {#creating-a-custom-folder}

また、Schedules **、** Locations **、Applications**、Channels、Devices **Master、Devices********** Devicesの各マスターページに、独自のカスタムフォルダを作成することもできます。

カスタムフォルダーを作成するには：

1. Select your project and click on **Create** next to plus icon in the action bar.
1. **作成**&#x200B;ウィザードが開いて、適切なオプションを選択します。
1. 「**次へ**」をクリックします。
1. プロパティを入力して、「**作成**」をクリックします。

次の手順は、DemoProjectの **Applications** マスターページにapplicationsフォルダーを作成する方法を示 *します*。

![player2-1](assets/player2-1.gif)

### 次の手順 {#the-next-steps}

Once you have created your own project, see [Channel Management](managing-channels.md) to create and manage content in your channel.

また、独自のスケジュール、アプリケーション、場所、またはデバイスを作成できます。
