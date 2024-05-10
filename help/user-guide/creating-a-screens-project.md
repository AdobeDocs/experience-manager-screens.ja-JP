---
title: プロジェクトの作成と管理
description: Adobe Experience Manager Screens プロジェクトの作成について説明します。
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: d98b449f-6b7d-4c08-b507-a64dece84ba8
source-git-commit: 6b4fc934c31640168528fa3e72cf634773f4f8e6
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 34%

---

# プロジェクトの作成と管理 {#creating-and-managing-projects}

Adobe Experience Manager のリンク（左上）を選択し、「Screens」を選択すると、AEM Screens にアクセスできます。

または、`http://localhost:4502/screens.html/content/screens` から直接アクセスすることもできます

>[!NOTE]
>**ナビゲーションのヒント：**
>カーソルキーを使用しても、AEM 内の様々なフォルダーを移動できます。また、特定のエンティティをクリックした後、スペースバーを押すと、その特定のフォルダーのプロパティを編集または表示できます。

## 新しい Screens プロジェクトの作成

1. クリック **スクリーン** AEM インスタンスから。
1. 「**Screens プロジェクトを作成**」をクリックします。
1. タイトルに「**TestScreens**」と入力し、「**保存**」をクリックします。

プロジェクトが作成され、Screens プロジェクトコンソールに戻ります。これで、プロジェクトをクリックできます。

プロジェクトには 5 種類のフォルダーがあります（下図を参照）。

* **スケジュール**
* **ロケーション**
* **アプリ管理**
* **デバイス**
* **チャネル**

![player1](assets/create-project.gif)

>[!NOTE]
>
>デフォルトでは、最初の構造にはが含まれています **スケジュール**, **場所**, **アプリケーション**, **チャネル**、および **デバイス** プライマリページ。ただし、この構造は必要に応じて手動で調整できます。 使用可能なオプションがプロジェクトに関連しない場合は、オプションを削除できます。


## プロパティの表示 {#viewing-properties}

Screens プロジェクトを作成したら、プロジェクトをクリックし、 **プロパティ** アクションバーから編集する：プロジェクトのプロパティ。

次のオプションで、**TestScreens** のプロパティを編集または変更できます。

![画像](assets/create-project2.png)

## カスタムフォルダーの作成 {#creating-a-custom-folder}

以下に、独自のカスタムフォルダーを作成することもできます。 **スケジュール**, **場所**, **アプリケーション**, **チャネル**、および **デバイス** プロジェクトで使用可能なプライマリページ。

カスタムフォルダーを作成するには：

1. プロジェクトをクリックし、 **作成** アクションバーのプラスアイコンの横。
1. この **作成** ウィザードが開き、適切なオプションをクリックします。
1. 「**次へ**」をクリックします。
1. プロパティを入力し、 **作成**.

以下の手順は、に対するアプリケーションフォルダーの作成を示しています **アプリケーション** のプライマリページ **TestScreen**.

![player2-1](assets/create-project3.gif)

### 次の手順 {#the-next-steps}

独自のプロジェクトを作成したら、次を参照してください [チャネル管理](managing-channels.md) でチャネル内のコンテンツを作成および管理します。
