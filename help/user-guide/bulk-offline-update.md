---
title: オフライン一括更新
description: すべてのチャネルを一括で更新する方法を説明します。
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
noindex: true
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: d0a0b065-798e-4108-86ac-0a1f4e211cfc
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 67%

---

# オフライン一括更新 {#bulk-offline-update}

ここでは、オフライン一括更新に関する以下のトピックについて説明します。

* **概要**
* **オフライン一括更新の使用**

<!-- OBSOLETE VERSIONS
>[!CAUTION]
>
>This AEM Screens functionality is only available, if you have installed AEM 6.3 Feature Pack 3 or AEM 6.4 Screens Feature Pack 1.
>
>To get access to this Feature Pack, contact Adobe Support and request access. When you have permissions you can download it from Package Share. -->

## 概要 {#overview}

オフライン一括更新：すべてのチャネルを一括で更新できます。 特定のチャネルに移動してコンテンツを更新する手間が省けます。代わりに、ある特定のプロジェクトのチャネルに含まれているすべてのコンテンツを一度に更新できます。

また、ネットワークトラフィックが少ない時間帯に、このアクティビティをスケジュールすることもできます。

>[!NOTE]
>
>オフライン一括更新機能は、変更されたチャネルのみを更新するように最適化されています。

## オフライン一括更新の使用 {#using-bulk-offline-update}

ユーザーインターフェイス（UI）からオフライン一括更新を手動で使用することも、OSGi サービスから一括更新をスケジュールすることもできます。

### AEM Screens のユーザーインターフェイスを使用する場合 {#using-aem-screens-user-interface}

次の手順に従って、AEM Screens プロジェクトでオフライン一括更新を使用します。

1. AEM Screens プロジェクトに移動します。
1. プロジェクトを選択してから、を選択します。 **オフラインコンテンツを更新** アクションバーので、チャネルコンテンツを手動で更新できます。

   ![screen_shot_2018-04-24at122256pm](assets/screen_shot_2018-04-24at122256pm.png)

### Adobe Experience Manager の Web コンソール設定を使用する場合 {#adobe-experience-manager-web-console-configuration}

次の手順に従って、AEM Screens プロジェクトでオフライン一括更新を使用します。

1. Adobe Experience Manager の Web コンソール設定を開きます。
1. オフライン一括更新サービスを検索します。

   ![screen_shot_2018-04-24at121428pm](assets/screen_shot_2018-04-24at121428pm.png)

1. 以下のプロパティを追加します。

   **プロジェクトパス**：AEM Screens プロジェクトのパスを指定します。パスは通常、`/content/screens/<Name of your project>` です。

   *例えば*、`/content/screens/we-retail` などとなります。このパスを URL で見つけるには、AEM Screensの下でプロジェクトを選択します（アイコンを選択しないでください）。

   >[!NOTE]
   >
   >チャネルからの相対的なプロジェクトパスを指定します。

   **スケジュール頻度** このサービスがオフラインコンテンツを更新する時刻（例：午後 5:00 または 17:00）を指定します。

1. を選択 **保存** をクリックして設定を保存します。 コンテンツは指定した時間に更新されます。
