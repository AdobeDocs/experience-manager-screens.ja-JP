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
ht-degree: 100%

---

# プロジェクトの作成と管理 {#creating-and-managing-projects}

Adobe Experience Manager のリンク（左上）を選択し、「Screens」を選択すると、AEM Screens にアクセスできます。

または、`http://localhost:4502/screens.html/content/screens` から直接アクセスすることもできます

>[!NOTE]
>**ナビゲーションの説明：**
>カーソルキーを使用しても、AEM 内の様々なフォルダーを移動できます。さらに、特定のエンティティをクリックし、スペースバーを押すと、その特定のフォルダーのプロパティを編集または表示できます。

## 新しい Screens プロジェクトの作成

1. AEM インスタンスから「**Screens**」をクリックします。
1. 「**Screens プロジェクトを作成**」をクリックします。
1. タイトルに「**TestScreens**」と入力し、「**保存**」をクリックします。

プロジェクトが作成され、Screens プロジェクトコンソールに戻ります。これでプロジェクトをクリックできるようになりました。

下の図に示すように、プロジェクトには 5 種類のフォルダーがあります。

* **スケジュール**
* **ロケーション**
* **アプリ管理**
* **デバイス**
* **チャネル**

![player1](assets/create-project.gif)

>[!NOTE]
>
>デフォルトの初期構造には、**スケジュール**、**ロケーション**、**アプリケーション**、**チャネル**&#x200B;および&#x200B;**デバイス**&#x200B;の各プライマリページが含まれていますが、この構造は必要に応じて手動で調整できます。使用可能なオプションがプロジェクトに関係ない場合は、そのオプションを削除できます。


## プロパティの表示 {#viewing-properties}

Screens プロジェクトを作成したら、プロジェクトをクリックし、アクションバーの「**プロパティ**」をクリックして、プロジェクトのプロパティを編集できます。

次のオプションで、**TestScreens** のプロパティを編集または変更できます。

![画像](assets/create-project2.png)

## カスタムフォルダーの作成 {#creating-a-custom-folder}

プロジェクトで使用可能な&#x200B;**スケジュール**、**ロケーション**、**アプリケーション**、**チャネル**&#x200B;および&#x200B;**デバイス**&#x200B;の各プライマリページの下に独自のカスタムフォルダーを作成することもできます。

カスタムフォルダーを作成するには：

1. プロジェクトをクリックし、アクションバーのプラスアイコンの横にある「**作成**」をクリックします。
1. **作成**&#x200B;ウィザードが開いたら、適切なオプションをクリックします。
1. 「**次へ**」をクリックします。
1. プロパティを入力し、「**作成**」をクリックします。

以下の手順では、**TestScreens** の&#x200B;**アプリケーション**&#x200B;プライマリページでアプリケーションフォルダーを作成する方法を説明します。

![player2-1](assets/create-project3.gif)

### 次の手順 {#the-next-steps}

独自のプロジェクトを作成したら、[チャネル管理](managing-channels.md)を参照して、チャネルのコンテンツを作成および管理します。
