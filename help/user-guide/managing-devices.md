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
TQID: https://experienceleague.adobe.com/BtVUYTZ9GisSxK6-M-QsYRGdykFB51IchqI7CX-vsa8
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2:
  - id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 251
ht-degree: 59%

---

# デバイスの管理 {#managing-devices}

>[!IMPORTANT]
>このコンテンツは、AEM オンプレミス/AMS （AEM 6.5LTSおよびAEM 6.5）に対して有効です。 AEM as a Cloud Service Screensの内容については、[AEM as a Cloud Service ガイド &#x200B;](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)を参照してください。

このページでデバイス割り当てを説明します。

デバイスコンソールでは、デバイスマネージャーにアクセスして、デバイスをディスプレイに割り当てることができます。

>[!CAUTION]
>
>デバイスを割り当てる前に、デバイスを登録します。 [デバイスの登録](device-registration.md)を参照してください。

## デバイスの割り当て {#device-assignment}

以下の手順に従って、デバイスをディスプレイに割り当てます。

1. プロジェクト（例えば下記）のデバイスフォルダーに移動します。

   `http://localhost:4502/screens.html/content/screens/TestProject`

   ![chlimage_1-32](assets/chlimage_1-32.png)

1. **デバイス**&#x200B;フォルダーをクリックし、アクションバーの「**デバイスマネージャー**」をクリックします。 割り当て済みと未割り当てデバイスが表示されます。

   ![chlimage_1-33](assets/chlimage_1-33.png)

1. リストから未割り当てのデバイスをクリックし、アクションバーで「**デバイスを割り当て**」をクリックします。

   ![chlimage_1-34](assets/chlimage_1-34.png)

1. デバイスを割り当てるディスプレイをリストからクリックし、「**割り当て**」をクリックします。

   ![chlimage_1-35](assets/chlimage_1-35.png)

1. 「**完了**」をクリックして、割り当てプロセスを完了します。


   ディスプレイダッシュボードの「**デバイス**」パネルに割り当て済みのデバイスが表示されます。

   ![chlimage_1-37](assets/chlimage_1-37.png)

   （**...**）をクリックします **DEVICES** パネルの右上隅にあるデバイス設定を追加するか、デバイスを更新します。

   ![chlimage_1-38](assets/chlimage_1-38.png)

>[!NOTE]
>
>最初のデバイスが新しいScreens プロジェクトに追加されるたびに、ユーザーグループが作成されます。
>例えば、プロジェクトノード名が&#x200B;*we-retail*&#x200B;の場合、ユーザーグループ名は&#x200B;*screens-we-retail-devices*です。
>このグループは、次の図に示すように、**Contributors** グループのメンバーとして追加されます。

![chlimage_1-39](assets/chlimage_1-39.png)

### 次の手順 {#the-next-steps}

チャネルのディスプレイへの割り当てに慣れたら、[監視とトラブルシューティング](monitoring-screens.md)を参照してください。
