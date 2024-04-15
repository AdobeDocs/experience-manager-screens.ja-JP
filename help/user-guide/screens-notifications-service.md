---
title: AEM Screens 通知サービス
description: AEM Screensのデバイスアクティビティを監視する方法について説明します。
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 205235d7-e621-4134-975c-257ae60939bc
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 16%

---

# AEM Screens 通知サービス{#aem-screens-notifications-service}

<!--removed from metadata: admitteddomains: @adobe.com;@caesars.com-->

***AEM Screens通知サービス*** デバイスの監視アクティビティを表します。

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

***AEM Screens通知サービス*** 設定可能な時間AEM Screens player が ping を送信しなかった場合、それを知らせるメールを管理者に送信します。

このサービスは OSGi Web コンソールで設定できます。

## メールの設定 {#configuring-email-settings}

メール通知を設定するには、次の手順に従います。

1. **Adobe Experience Manager Web コンソール設定**&#x200B;が開きます。
1. **Screens Device Email Monitoring Service** を開きます。

   ![screen_shot_2018-04-26at44602pm](assets/screen_shot_2018-04-26at44602pm.png)

1. メールの設定を指定できるように、次のフィールドを定義します。

   **デバイスのパス** 監視する Screens プロジェクトのパスを入力します。 パスは通常、`/home/users/screens/<Name of your project>` です。

   例えば、プロジェクトが **`We.Retail`**。プロジェクトパスをとして使用します ***/home/users/screens/we-retail***.

   >[!NOTE]
   >
   >デバイスユーザーがアクセスするプロジェクトパスを指定します。

   **スケジュール頻度**  – このモニターがメールを送信する時刻（例：午後 5 時または 17 時）または頻度（時間単位、例：1）を指定します。

   **Ping タイムアウト**  – これは、デバイスが到達不能と見なされるまでの間隔を分単位で指定します。

   **SMTP サーバー** - メールの送信に使用する SMTP サーバーを指定します。

   **SMTP ポート** - SMTP ポートを入力します。

   **TLS を使用** - Transport Layer Security （TLS）を使用すると、SMTP サーバーとの安全な通信を使用できます。

   Adobeでは、企業のメールサーバーへの安全な接続に TLS を使用することをお勧めします。 適切な値については、メール管理者に確認してください。

   **ユーザー名** - メールを送信するユーザー名を指定します。

   **password** - メールを送信する際のパスワードを指定します。

   **受信者**  – 受信者のメールアドレスを指定します。

   >[!NOTE]
   >
   >入力できるメールアドレスは 1 つだけです。一括メールを送信するには、関連するユーザーとグループまたは配布リストを作成します。

1. を選択 **保存** 使用しているAEM Screens デバイスにメールを送信して監視アクティビティを設定します。

## メール通知 {#email-notification}

メール通知の設定をおこなうと、無操作状態が報告された実際のデバイスへのリンクを含むメール通知が届きます。

そのリンクにアクセスすると、デバイスのダッシュボードに直接移動します。

メールは、指定された ping タイムアウトに対して ping を送信せず、メールの生成時にまだ ping を送信していないデバイスが 1 つ以上ある場合にのみ送信されます。

### 使用例 {#example-use-cases}

次の例では、Screens デバイスメール監視サービスからプロパティを設定するための参照用シナリオをいくつか説明します。

**シナリオ 1**

スケジュールの頻度を午前 1 時、ping タイムアウトを 60 に設定します。 この場合、AEM Screens デバイスが午後 12:00 から午後 1:00 まで ping を送信しなければ、デバイスが無操作状態であることを知らせるメール通知が届きます。

**シナリオ 2**

スケジュールの頻度を 1 に、ping タイムアウトを 60 に設定します。 次に、AEM Screens デバイスが 1 回から 1 回までの ping を送信しなかった場合は、デバイスが無操作状態であることを確認するメール通知が届きます。
