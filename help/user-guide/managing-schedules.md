---
title: スケジュールの作成と管理
description: チャネルを再利用可能なグループに整理して、個別に割り当てを繰り返す必要がないようにするスケジュールについて説明します。
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: dc9c5413-3b03-4f1f-bac5-aa599443254a
TQID: https://experienceleague.adobe.com/FJomd-Wz-r8vJZK7PH6wgL4LY3zRmOucBhIbTdjUmQ4
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2:
  - id: ba4275ba-c29a-4197-90dc-5a633402ca3c
  - id: cf6d61d1-acb6-4411-ad1b-25fb57e94db6
  - id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 416
ht-degree: 65%

---

# スケジュールの作成と管理 {#creating-and-managing-schedules}

>[!IMPORTANT]
>このコンテンツは、AEM オンプレミス/AMS （AEM 6.5LTSおよびAEM 6.5）に対して有効です。 AEM as a Cloud Service Screensの内容については、[AEM as a Cloud Service ガイド &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)を参照してください。

AEM Screen の&#x200B;**スケジュール**&#x200B;では、チャネルを再利用可能なグループに整理できます。 つまり、コンテンツを表示するディスプレイごとに割り当てを個別に繰り返す必要はありません。

スケジュールを&#x200B;***日分割***&#x200B;と組み合わせると、1 日の特定の時間に実行される複数のチャネルでグローバルスケジュールを設定でき、また一度にすべてのディスプレイでその設定を再使用できます。

>[!NOTE]
>
>この AEM Screens 機能は、AEM 6.3 Sites 機能パック 1 がインストールされている場合にのみ使用できます。 この機能パックにアクセスするには、アドビサポートに連絡してアクセス権をリクエストします。 必要な権限を取得したら、Package Share から機能パックをダウンロードできます。

## スケジュールの作成 {#creating-a-schedule}

ユースケースのすべてのアクティビティを管理する Screens プロジェクトのスケジュールを作成できます。

以下の手順に従って、チャネルのスケジュールを作成します。

1. Adobe Experience Manager リンク（左上）をクリックし、「Screens」をクリックします。 または、`http://localhost:4502/screens.html/content/screens` に直接アクセスすることもできます。
1. Screens プロジェクトに移動し、「**スケジュール**」をクリックします。
1. アクションバーの「**作成**」をクリックします。
1. **作成**&#x200B;ウィザードで「**スケジュール**」をクリックし、「**次へ**」をクリックします。

1. 「**名前**」と「**タイトル**」を入力し、「**作成**」をクリックします。

プロジェクトに指定した名前とタイトルのスケジュールフォルダーが表示されます。


## ダッシュボードを見る {#viewing-dashboard}

プロジェクトにスケジュールフォルダーを作成したら、スケジュールダッシュボードから詳細を表示できます。

下の手順に従って、スケジュールダッシュボードを表示します。 次の例では、`We.Retail` プロジェクトのダッシュボードが表示されています。

1. Screens（`We.Retail` など）プロジェクトの&#x200B;**スケジュール**&#x200B;フォルダーに移動します。

   ![chlimage_1](assets/chlimage_1.png)

1. アクションバーで「**ダッシュボード**」をクリックします。

   **スケジュール情報**、**割り当てられたチャネル**、**割り当てられたディスプレイ** の 3 つのパネルが表示されます。

   ![chlimage_1-1](assets/chlimage_1-1.png)

   **スケジュール情報パネル** - スケジュール情報パネルの右上隅にある「プロパティ」をクリックして、スケジュールのプロパティを表示または変更します。

   **割り当て済みチャンネルパネル** – 割り当て済みチャンネルパネルの右上隅にある「+チャネルを割り当て」をクリックして、チャネル割り当てダイアログボックスを開きます。

   **割り当て済みディスプレイ パネル** – 割り当て済みディスプレイ パネルの任意のディスプレイをクリックして、ディスプレイ ダッシュボードを開きます。

