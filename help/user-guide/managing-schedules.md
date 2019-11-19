---
title: スケジュールの作成と管理
seo-title: スケジュールの管理
description: このページに従って、スケジュールについて学んでください。これによりチャネルを再使用可能なグループに編成でき、コンテンツを表示するそれぞれのディスプレイに、個別に繰り返してチャネルを割り当てる必要がなくなります。
seo-description: このページに従って、スケジュールについて学んでください。これによりチャネルを再使用可能なグループに編成でき、コンテンツを表示するそれぞれのディスプレイに、個別に繰り返してチャネルを割り当てる必要がなくなります。
uuid: c05328a0-620a-4597-b7b3-f4433e78d4e9
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 75ed3c42-4be9-42ae-9d76-e0343af81516
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# スケジュールの作成と管理 {#creating-and-managing-schedules}

AEM Screens で&#x200B;**スケジュール**&#x200B;を使用すると、複数のチャネルを再使用可能なグループに編成できるので、コンテンツを表示する各ディスプレイに個別に割り当てをおこなう必要がなくなります。

Schedules when combined with ***Dayparting***, allows you to set a global schedule with multiple channels running at specific times of the day, and re-use that setup for all your displays at once.

>[!NOTE]
>
>この AEM Screens 機能は、AEM 6.3 Sites 機能パック 1 がインストールされている場合にのみ使用できます。この機能パックにアクセスするには、アドビサポートに連絡してアクセス権をリクエストする必要があります。アクセス権が付与されると、パッケージ共有から機能パックをダウンロードできるようになります。

## スケジュールの作成 {#creating-a-schedule}

ユーズケースのすべてのアクティビティを管理するスクリーンプロジェクトのスケジュールを作成できます。

下の手順に従って、チャネルのスケジュールを作成します。

1. Adobe Experience Manager リンク（左上）を選択し、「スクリーン」を選択します。Alternatively, you can ﻿go directly to: `http://localhost:4502/screens.html/content/screens`.
1. Navigate to Screens project and click **Schedules**.
1. アクションバーから「**作成**」をクリックします。
1. 「**スケジュール**」を&#x200B;**作成**&#x200B;ウィザードから選択し、「**次へ**」をクリックします。

1. **名前**&#x200B;と&#x200B;**タイトル**&#x200B;に情報を入力し、「**作成**」をクリックします。

プロジェクトに指定された名前とタイトルでスケジュールフォルダーが表示されます。

![chlimage_1](assets/chlimage_1.gif)

## ダッシュボードの表示 {#viewing-dashboard}

プロジェクトの中にスケジュールフォルダーを作成したら、スケジュールダッシュボードから詳細を表示できます。

下の手順に従ってスケジュールダッシュボードを表示します。次の例では、We.Retail プロジェクトのダッシュボードが示されています。

1. スクリーン（We.Retail など）プロジェクト&#x200B;**スケジュール**&#x200B;フォルダーに移動します。

   ![chlimage_1](assets/chlimage_1.png)

1. アクションバーから「**ダッシュボード**」をクリックして、スケジュールのダッシュボードを開きます。

   **スケジュール情報**、**割り当てられたチャネル**、**割り当てられたディスプレイ** の 3 つのパネルが表示されます。

   ![chlimage_1-1](assets/chlimage_1-1.png)

   **[集計情報]パネル** [集計情報]パネルの右上隅にある[プロパティ]をクリックして、集計表のプロパティを表示/変更します。

   **[割り当てられたチャネル** ]パネル[割り当てられたチャネル]パネルの右上隅にある[チャネルを割り当て]をクリックして、[チャネル割り当て]ダイアログボックスを開きます。 詳しくは、「チャネルの割り当て」を参照してください。

   **[割り当て済み表示パネル** ] [割り当て済み表示パネル]から任意の表示を選択し、表示ダッシュボードを開きます。

