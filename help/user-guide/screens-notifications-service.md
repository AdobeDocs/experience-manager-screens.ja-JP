---
title: AEM Screens 通知サービス
description: AEM Screens のデバイスアクティビティを監視する方法について説明します。
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 205235d7-e621-4134-975c-257ae60939bc
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 95%

---

# AEM Screens 通知サービス{#aem-screens-notifications-service}

<!--removed from metadata: admitteddomains: @adobe.com;@caesars.com-->

***AEM Screens 通知サービス***&#x200B;は、デバイスアクティビティの監視について説明します。

ここでは、以下のトピックについて説明します。

* **概要**
* **メールの設定**
* **メール通知**
* **使用例**

<!-- OBSOLETE NOTE>
>[!CAUTION]
>
>This AEM Screens functionality is only available, if you have installed AEM 6.3.2 Feature Pack 3 or AEM 6.4.1 Screens Feature Pack 1.
>
>To get access to this Feature Pack, contact Adobe Support and request access. After you have permissions you can download it from Package Share. -->

## 概要 {#overview}

***AEM Screens通知サービス*** 設定可能な期間AEM Screens Player が ping を送信しなかった場合、それを知らせるメールを管理者に送信します。

このサービスは OSGi Web コンソールで設定できます。

## メールの設定 {#configuring-email-settings}

メール通知を設定するには、以下の手順に従います。

1. **Adobe Experience Manager Web コンソール設定**&#x200B;が開きます。
1. **Screens Device Email Monitoring Service** を開きます。

   ![screen_shot_2018-04-26at44602pm](assets/screen_shot_2018-04-26at44602pm.png)

1. 以下のフィールドを定義して、メールの設定を指定します。

   **デバイスパス**：監視する Screens プロジェクトへのパスを入力します。パスは通常、`/home/users/screens/<Name of your project>` です。

   例えば、プロジェクトが **`We.Retail`** の場合、プロジェクトのパスは ***/home/users/screens/we-retail*** になります。

   >[!NOTE]
   >
   >デバイスユーザーがアクセスするプロジェクトパスを指定します。

   **スケジュールの頻度**：このモニターがメールを送信する時刻（例：午後 5 時または 17 時）または頻度（時間単位、例：1）を指定します。

   **ping タイムアウト**：デバイスが到達不能と見なされるまでの経過時間を分単位で指定します。

   **SMTP サーバー**：メールの送信に使用する SMTP サーバーを指定します。

   **SMTP ポート**：SMTP ポートを入力します。

   **TLS を使用**：TLS（Transport Layer Security）を使用すると、SMTP サーバーとの安全な通信を行えます。

   会社のメールサーバーとの安全な接続には、TLS を使用することをお勧めします。適切な値については、メール管理者に確認してください。

   **ユーザー名**：メールを送信する際のユーザー名を指定します。

   **パスワード**：メールを送信する際のパスワードを指定します。

   **受信者**：受信者のメールアドレスを指定します。

   >[!NOTE]
   >
   >入力できるメールアドレスは 1 つだけです。一括メールを送信するには、該当するユーザーのグループつまり配布リストを作成します。

1. 「**保存**」をクリックして、AEM Screens デバイスのメールを使用した監視アクティビティを設定します。

## メール通知 {#email-notification}

メール通知の設定を行うと、無操作状態が報告された実際のデバイスへのリンクを記載したメール通知が届きます。

このリンクにアクセスすると、デバイスのダッシュボードに直接移動します。

指定した ping タイムアウトの時間内に ping を送信せず、メールの生成時にもまだ ping を送信していないデバイスが 1 つ以上ある場合にのみ、メールが送信されます。

### 使用例 {#example-use-cases}

次の例では、Screens Device Email Monitoring Service のプロパティを設定するシナリオを参考までにいくつか示します。

**シナリオ 1**

スケジュールの頻度を午前 1 時、ping タイムアウトを 60 に設定します。次に、AEM Screens デバイスが午後 12:00 から午後 1:00 まで ping を送信しなければ、デバイスが無操作状態であることを知らせるメール通知が届きます。

**シナリオ 2**

スケジュールの頻度を 1 に、ping タイムアウトを 60 に設定します。次に、AEM Screens デバイスが 1 日の間の特定の時間に 1 回も ping を送信しなかった場合は、デバイスが無操作状態であることを確認するメール通知が届きます。
