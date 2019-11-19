---
title: AEM Screens Notifications Service
seo-title: AEM Screens Notifications Service
description: デバイスのアクティビティを監視する方法の詳細については、このページに従ってください。
seo-description: デバイスのアクティビティを監視する方法の詳細については、このページに従ってください。
uuid: 9843219d-ed39-4e4f-bef4-e500528ff9f1
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 8879e510-4f0e-46da-87d2-77c5aaacb26e
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# AEM Screens Notifications Service{#aem-screens-notifications-service}

<!--removed from metadata: admitteddomains: @adobe.com;@caesars.com-->

***AEM Screens Notifications Serviceでは***、デバイスのアクティビティを監視できる機能について説明します。

この節では、以下のトピックについて説明します。

* **概要**
* **電子メールの設定**
* **Email Notification**
* **使用例**

>[!CAUTION]
>
>このAEM Screens機能は、AEM 6.3.2 Feature Pack 3またはAEM 6.4.1 Screens Feature Pack 1をインストールしている場合にのみ使用できます。
>
>この機能パックにアクセスするには、アドビサポートに連絡してアクセス権をリクエストする必要があります。アクセス権が付与されると、パッケージ共有から機能パックをダウンロードできるようになります。

## 概要 {#overview}

***AEM Screens Notifications Serviceを使用すると***、AEM Screensプレイヤーが設定可能な期間pingを実行しなかった場合に、管理者が電子メールを受信できます。

このサービスはOSGi webコンソールで設定できます。

## Configuring Email Settings {#configuring-email-settings}

次の手順に従って、電子メール通知を設定します。

1. **Adobe Experience Manager Web Console Configurationを開きます**。
1. 画面デバ **イス電子メール監視サービスを開きます**。

   ![screen_shot_2018-04-26at44602pm](assets/screen_shot_2018-04-26at44602pm.png)

1. 次のフィールドを定義して、電子メールの設定を行います。

   **デバイスパス** ：監視するScreensプロジェクトへのパスを入力します。 通常はパスです `/home/users/screens/<Name of your project>`。

   例えば、プロジェクトが **We.Retailの場合**、プロジェクトパスは ***/home/users/screens/we-retailとして使用します***。

   >[!NOTE]
   >
   >デバイスユーザーが配置されるプロジェクトパスを指定します。

   **スケジュールの頻度** ：このモニターが電子メールを送信する時間（午後5時、午後17時など）または頻度（時間単位）を指定します。

   **Pingタイムアウト** ：デバイスが到達不可と見なされる間隔を分単位で指定します。

   **SMTP Server** ：電子メールの送信に使用するSMTPサーバーを指定します。

   **SMTP Port** SMTPポートを入力します。

   **TLS** Transport Layer Security(TLS)を使用すると、SMTPサーバーとの安全な通信を使用できます。

   会社のメールサーバーとの安全な接続には、TLSを使用することをお勧めします。 適切な値については、メール管理者にお問い合わせください。

   **username** 電子メールを送信するユーザー名を指定します。

   **パスワード** ：電子メールを送信する際のパスワードを指定します。

   **受信者** ：受信者の電子メールアドレスを指定します。

   >[!NOTE]
   >
   >電子メールアドレスは1つだけ入力できます。 一括電子メールを送信するには、関連するユーザーと共にグループまたは配布リストを作成します。

1. 「保存 **** 」をクリックして、AEM Screensデバイスの電子メールを使用した監視アクティビティを設定します。

## Email Notification {#email-notification}

電子メール通知の設定を行うと、無操作状態が報告された実際のデバイスへのリンクを含む電子メール通知が届きます。

このリンクにアクセスすると、デバイスのダッシュボードに直接移動します。

pingが指定されたタイムアウトに対してpingを行わず、電子メールの生成時にpingを行わないデバイスが1つ以上ある場合、電子メールのみが送信されます。

### 使用例 {#example-use-cases}

次の例では、Screens Device Email Monitoring Serviceのプロパティを設定する際に、いくつかのシナリオについて説明します。

**シナリオ 1**:

スケジュールの頻度を午前1時、pingタイムアウトを60時に設定した場合、画面デバイスが午後12時までpingを実行しないと、デバイスが無操作状態であることを確認する電子メール通知が送信されます。

**シナリオ 2**:

スケジュールの頻度を1、pingのタイムアウトを60に設定した場合、画面デバイスが特定の時間に1回間にpingを実行しないと、デバイスが無操作状態であることを確認する電子メール通知を受信します。
