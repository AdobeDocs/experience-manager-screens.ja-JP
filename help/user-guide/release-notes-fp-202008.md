---
title: 機能パック 202008 のリリースノート
description: このページでは、機能パック202008のリリースノートについて説明します。
translation-type: tm+mt
source-git-commit: a179b6be273b0b0ca166bae755399f8254091ee6
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 37%

---


# 機能パック 202008 のリリースノート {#release-notes-for-feature-pack}

>[!CAUTION]
>
>最新バージョンの Adobe Experience Manager（AEM）にアップグレードすることをお勧めします。Screens では、AEM 6.3 Screens プラットフォームのメンテナンスサポートを提供しています。

## 利用可能場所 {#availability}

AEM Screensは、AEM 6.5機能パック5をリリースしました。

You can download the latest feature pack for AEM Screens 6.5.5 Release from the [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) using your Adobe ID. 「**Adobe Experience Manager**」タブに移動し、「**Screens**」を検索して最新の機能パックを入手します。

## リリース日 {#release-date}

AEM Screens機能パック202008のリリース日は2020年9月3日です。

### 新機能 {#what-is-new}

* **スケジュールダッシュボードでのタイムライン表示**

   タイムライン表示を使用すると、割り当てられたスケジュールを表示ダッシュボードからチャネルに表示できます。

   詳しくは、 [タイムライン表示](/help/user-guide/channel-assignment-latest-fp.md#timeline-view) (Timeline Timeline Manager)を参照してください。

* **繰り返しスケジュール**

   [繰り返しのスケジュール]では、チャネルの定期的なスケジュールを設定できます。 1つのチャネルに対して、複数の繰り返しスケジュールを設定します。

   詳しくは、「 [繰り返しスケジュール](/help/user-guide/channel-assignment-latest-fp.md#recurrence-schedule) 」を参照してください。

* **AEM Screensの音声認識機能**

   音声認識機能を使用すると、音声操作によって駆動される AEM Screens チャネルのコンテンツを変更できます。

   コンテンツ作成者は、ディスプレイを音声対応となるよう設定できます。この機能の目的は、お客様がディスプレイと対話する方法として音声を利用できるようにすることです。

   詳しくは、「 [音声認識](voice-recognition.md) 」を参照してください。

### 既知の問題と修正点 {#known-issues}

AEM Screens6.5.5 Service Packを使用している場合は、WindowsまたはAndroid Player用の環境を設定する必要があります。

login-token cookieのSameSite属性をLax **から** None **に設定します。この値は、** Adobe Experience ManagerWeb ConsoleConfiguration ******** on all AEM authorおよびpublish instancesに設定します。

* 詳しくは、「Windows 10 Player [の](implementing-windows-player.md#fp-environment-setup) 実装」を参照してください。

* 詳しくは、 [Android Playerの](implementing-android-player.md#fp-environment-setup) 実装（英語）を参照してください。

### リリースされている AEM Screens Player {#released-aem-screens-players}

次のAEM Screensプレイヤーは、AEM ScreensリリースのAEM 6.5機能パック5向けにリリースされています。

* Chrome OS
* Windows
* Android

#### AEM Screens Player のダウンロード {#aem-screens-player-downloads}

最新の AEM Screens Player のダウンロードとバグ修正について詳しくは、**[AEM Screens Player のダウンロード](https://download.macromedia.com/screens/)**&#x200B;を参照してください。
