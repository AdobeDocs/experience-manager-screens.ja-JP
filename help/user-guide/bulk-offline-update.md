---
title: オフライン一括更新
description: すべてのチャネルを一括更新する方法について説明します。
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: d0a0b065-798e-4108-86ac-0a1f4e211cfc
TQID: https://experienceleague.adobe.com/PxlKWiWPvedqs2krdj3UH5Chshni2X3RaTmZI1wW2-Q
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2:
  - id: ba4275ba-c29a-4197-90dc-5a633402ca3c
  - id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 336
ht-degree: 77%

---

# オフライン一括更新 {#bulk-offline-update}

>[!IMPORTANT]
>このコンテンツは、AEM オンプレミス/AMS （AEM 6.5LTSおよびAEM 6.5）に対して有効です。 AEM as a Cloud Service Screensの内容については、[AEM as a Cloud Service ガイド &#x200B;](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)を参照してください。

ここでは、オフライン一括更新に関する以下のトピックについて説明します。

* **概要**
* **オフライン一括更新の使用**

<!--
OBSOLETE VERSIONS
>[!CAUTION]
>
>This AEM Screens functionality is only available, if you have installed AEM 6.3 Feature Pack 3 or AEM 6.4 Screens Feature Pack 1.
>
>To get access to this Feature Pack, contact Adobe Support and request access. When you have permissions you can download it from Package Share.
-->

## 概要 {#overview}

オフライン一括更新を使用すると、すべてのチャネルを一括更新できます。 特定のチャネルに移動してコンテンツを更新する手間が省けます。 代わりに、ある特定のプロジェクトのチャネルに含まれているすべてのコンテンツを一度に更新できます。

また、ネットワークトラフィックが少ない時間帯に、このアクティビティをスケジュールすることもできます。

>[!NOTE]
>
>オフライン一括更新機能は、変更されたチャネルのみを更新するように最適化されています。

## オフライン一括更新の使用 {#using-bulk-offline-update}

ユーザーインターフェイス（UI）からオフライン一括更新を手動で使用することも、OSGi サービスから一括更新をスケジュールすることもできます。

### AEM Screens のユーザーインターフェイスを使用する場合 {#using-aem-screens-user-interface}

次の手順に従って、AEM Screens プロジェクトでオフライン一括更新を使用します。

1. AEM Screens プロジェクトに移動します。
1. プロジェクトをクリックし、アクションバーの「**オフラインコンテンツを更新**」をクリックすると、チャネルコンテンツを手動で更新できます。

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Adobe Experience Manager の Web コンソール設定を使用する場合 {#adobe-experience-manager-web-console-configuration}

次の手順に従って、AEM Screens プロジェクトでオフライン一括更新を使用します。

1. Adobe Experience Manager の Web コンソール設定を開きます。
1. オフライン一括更新サービスを検索します。

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. 以下のプロパティを追加します。

   **プロジェクトのパス** - AEM Screens プロジェクトのパスを指定します。 パスは通常、`/content/screens/<Name of your project>` です。

   *例えば*、`/content/screens/we-retail` などとなります。 AEM Screens で任意のプロジェクトを選択すれば（アイコンをクリックしないでください）、URL にこのパスが含まれていることがわかります。

   >[!NOTE]
   >
   >チャネルからの相対的なプロジェクトパスを指定します。

   **スケジュール頻度** – このサービスがオフライン コンテンツを更新する必要がある時間（例：午後5:00または17:00）を指定します。

1. 「**保存**」をクリックして、設定を保存します。 コンテンツは指定した時間に更新されます。
