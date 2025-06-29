---
title: デバイスの管理
description: AEM Screens でのデバイスの割り当てと管理について説明します。
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 10749ff2-9128-44e7-9f10-c8e783a6f695
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 92%

---

# デバイスの管理 {#managing-devices}

このページでデバイス割り当てを説明します。

デバイスコンソールでは、デバイスマネージャーにアクセスして、デバイスをディスプレイに割り当てることができます。

>[!CAUTION]
>
>デバイスを割り当てる前に、デバイスを登録します。[デバイスの登録](device-registration.md)を参照してください。

## デバイスの割り当て {#device-assignment}

以下の手順に従って、デバイスをディスプレイに割り当てます。

1. プロジェクト（例えば下記）のデバイスフォルダーに移動します。

   `http://localhost:4502/screens.html/content/screens/TestProject`

   ![chlimage_1-32](assets/chlimage_1-32.png)

1. **デバイス**&#x200B;フォルダーをクリックし、アクションバーの「**デバイスマネージャー**」をクリックします。割り当て済みと未割り当てデバイスが表示されます。

   ![chlimage_1-33](assets/chlimage_1-33.png)

1. リストから未割り当てのデバイスをクリックし、アクションバーで「**デバイスを割り当て**」をクリックします。

   ![chlimage_1-34](assets/chlimage_1-34.png)

1. デバイスを割り当てるディスプレイをリストからクリックし、「**割り当て**」をクリックします。

   ![chlimage_1-35](assets/chlimage_1-35.png)

1. 「**完了**」をクリックして、割り当てプロセスを完了します。


   ディスプレイダッシュボードの「**デバイス**」パネルに割り当て済みのデバイスが表示されます。

   ![chlimage_1-37](assets/chlimage_1-37.png)

   **デバイス**&#x200B;パネルの右上隅の（**...**）をクリックして、デバイス設定を追加するかデバイスを更新します。

   ![chlimage_1-38](assets/chlimage_1-38.png)

>[!NOTE]
>
>初めてのデバイスが新しい Screens プロジェクトに追加されるたびに、ユーザーグループが作成されます。
>&#x200B;>例えば、プロジェクトノード名が *we-retail* である場合、ユーザーグループ名は *screens-we-retail-devices* になります。
>&#x200B;>このグループは、下の図で示されているように、**寄稿者**&#x200B;グループのメンバーとして追加されます。

![chlimage_1-39](assets/chlimage_1-39.png)

### 次の手順 {#the-next-steps}

チャネルのディスプレイへの割り当てに慣れたら、[監視とトラブルシューティング](monitoring-screens.md)を参照してください。
