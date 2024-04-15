---
title: デバイスの管理
description: AEM Screensでのデバイスの割り当てと管理について説明します。
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 10749ff2-9128-44e7-9f10-c8e783a6f695
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 57%

---

# デバイスの管理 {#managing-devices}

このページでデバイス割り当てを説明します。

デバイス コンソールを使用すると、デバイスマネージャーにアクセスしてデバイスをディスプレイに割り当てることができます。

>[!CAUTION]
>
>デバイスを割り当てる前に、登録します。 参照： [デバイスの登録](device-registration.md).

## デバイスの割り当て {#device-assignment}

以下の手順に従って、デバイスをディスプレイに割り当てます。

1. プロジェクト（例えば下記）のデバイスフォルダーに移動します。

   `http://localhost:4502/screens.html/content/screens/TestProject`

   ![chlimage_1-32](assets/chlimage_1-32.png)

1. **デバイス**&#x200B;フォルダーを選択し、アクションバーの「**デバイスマネージャー**」をタップまたはクリックします。割り当て済みと未割り当てデバイスが表示されます。

   ![chlimage_1-33](assets/chlimage_1-33.png)

1. リストから未割り当てデバイスを選択し、アクションバーの「**デバイスを割り当て**」をタップまたはクリックします。

   ![chlimage_1-34](assets/chlimage_1-34.png)

1. デバイスの割り当て先となるディスプレイをリストから選択し、 **割り当て**.

   ![chlimage_1-35](assets/chlimage_1-35.png)

1. 「**完了**」をタップまたはクリックして、割り当てプロセスを完了します。


   ディスプレイダッシュボードの「**デバイス**」パネルに割り当て済みのデバイスが表示されます。

   ![chlimage_1-37](assets/chlimage_1-37.png)

   「」（**...**）を選択します。 **デバイス** パネルを開いて、デバイス設定を追加するか、デバイスを更新します。

   ![chlimage_1-38](assets/chlimage_1-38.png)

>[!NOTE]
>
>初めてのデバイスが新しい Screens プロジェクトに追加されるたびに、ユーザーグループが作成されます。
>例えば、プロジェクトノード名が *we-retail* である場合、ユーザーグループ名は *screens-we-retail-devices* になります。
>このグループは、 **投稿者** グループ化します（下図を参照）。

![chlimage_1-39](assets/chlimage_1-39.png)

### 次の手順 {#the-next-steps}

ディスプレイへのチャネルの割り当てに詳しくは、[監視とトラブルシューティング](monitoring-screens.md).
