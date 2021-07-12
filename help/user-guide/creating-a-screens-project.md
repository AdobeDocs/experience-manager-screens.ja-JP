---
title: プロジェクトの作成と管理
seo-title: プロジェクトの作成
description: ここでは、新しい Screens プロジェクトの作成について説明します。
seo-description: ここでは、新しい Screens プロジェクトの作成について説明します。
uuid: c73126ca-18d0-45b4-bdde-a3653082bfc4
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 00ea321c-3f79-4aa5-83cc-3fa2fe9e35d9
feature: Screens のオーサリング
role: Admin, Developer
level: Intermediate
exl-id: d98b449f-6b7d-4c08-b507-a64dece84ba8
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 100%

---

# プロジェクトの作成と管理 {#creating-and-managing-projects}

Adobe Experience Manager のリンク（左上）を選択し、「Screens」を選択すると、AEM Screens にアクセスできます。

または、`http://localhost:4502/screens.html/content/screens` から直接アクセスすることもできます


>[!NOTE]
>**ナビゲーションのヒント：**
>カーソルキーを使用しても、AEM 内の様々なフォルダーを移動できます。さらに、特定のエンティティを選択し、スペースバーを押すと、その特定のフォルダーのプロパティを編集または表示できます。

## 新しい Screens プロジェクトの作成 {#creating-a-new-screens-project}

以下の手順に従って、新しい Screens プロジェクトを作成します。

1. AEM インスタンスから「**Screens**」を選択します。

1. 「**Screens プロジェクトを作成**」をクリックします。

1. タイトルに「**TestScreens**」と入力し、「**保存**」をクリックします。

プロジェクトが作成され、Screens プロジェクトコンソールに戻ります。これでプロジェクトを選択できます。

下の図に示すように、プロジェクトには 5 種類のフォルダーがあります。

* **スケジュール**
* **ロケーション**
* **アプリ管理**
* **デバイス**
* **チャネル**

![player1](assets/create-project.gif)

>[!NOTE]
>
>初期構造には、デフォルトで、**スケジュール**、**ロケーション**、**アプリケーション**、**チャネル**、**デバイス**&#x200B;の各マスターページが含まれていますが、必要に応じて手動で調整できます。使用可能なオプションがプロジェクトに関係ない場合は、そのオプションを削除できます。


## プロパティの表示 {#viewing-properties}

Screens プロジェクトを作成したら、プロジェクトを選択し、アクションバーの「**プロパティ**」をクリックして、プロジェクトのプロパティを編集します。

次のオプションで、**TestScreens** のプロパティを編集または変更できます。

![画像](assets/create-project2.png)


## カスタムフォルダーの作成 {#creating-a-custom-folder}

プロジェクトで使用可能な&#x200B;**スケジュール**、**ロケーション**、**アプリケーション**、**チャネル**、**デバイス**&#x200B;の各マスターページの下に独自のカスタムフォルダーを作成することもできます。

カスタムフォルダーを作成するには：

1. プロジェクトを選択し、アクションバーのプラスアイコンの横にある「**作成**」をクリックします。
1. **作成**&#x200B;ウィザードが開いて、適切なオプションを選択します。
1. 「**次へ**」をクリックします。
1. プロパティを入力して、「**作成**」をクリックします。

以下の手順では、**TestScreens** で&#x200B;**アプリケーション**&#x200B;マスターページにアプリケーションフォルダーを作成します。

![player2-1](assets/create-project3.gif)

### 次の手順 {#the-next-steps}

独自のプロジェクトを作成したら、[チャネル管理](managing-channels.md)を参照して、チャネルのコンテンツを作成および管理します。
