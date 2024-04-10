---
title: 機能パック 202008 のリリースノート
description: 2020 年 9 月 3 日にリリースされたAEM Screens機能パック 202008 の詳細情報。
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: bd466576-a6d3-494c-82e5-c5326b6e0aca
source-git-commit: 1e8beb9dfaf579250138d4a41eeec88cc81f2d39
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 70%

---

# 機能パック 202008 のリリースノート {#release-notes-for-feature-pack}

>[!CAUTION]
>
>最新バージョンの Adobe Experience Manager（AEM）にアップグレードすることをお勧めします。AEM Screensは、AEM 6.3 Screens プラットフォームのメンテナンスサポートを提供します。

## 入手方法 {#availability}

AEM Screens は、AEM 6.5 機能パック 5 をリリースしました。

Adobe ID を使用して、AEM Screens 6.5.5 リリースの最新の機能パックを[ソフトウェア配布ポータル](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)からダウンロードできます。「**Adobe Experience Manager**」タブに移動し、「**Screens**」を検索して最新の機能パックを入手します。

## リリース日 {#release-date}

AEM Screens 機能パック 202008 のリリース日は 2020 年 9 月 3 日です。

### 新機能 {#what-is-new}

* **スケジュールダッシュボードでのタイムライン表示**

  タイムライン表示を使用すると、チャネルに割り当てられたスケジュールを表示ダッシュボードから参照できます。

  詳しくは、[タイムライン表示](/help/user-guide/channel-assignment-latest-fp.md#timeline-view)を参照してください。

* **繰り返しスケジュール**

  繰り返しスケジュールを使用すると、チャネルに繰り返しスケジュールを設定できます。 1 つのチャネルに対して、複数の繰り返しスケジュールを設定します。

  詳しくは、「[繰り返しスケジュール](/help/user-guide/channel-assignment-latest-fp.md#recurrence-schedule)」を参照してください。

* **AEM Screens の音声認識機能**

  音声認識機能を使用すると、音声操作によって駆動される AEM Screens チャネルのコンテンツを変更できます。

  コンテンツ作成者は、ディスプレイを音声対応となるよう設定できます。この機能の目的は、お客様がディスプレイを操作する方法として音声を使用できるようにすることです。

  詳しくは、[音声認識](voice-recognition.md)を参照してください。

### 既知の問題と修正点 {#known-issues}

AEM Screens 6.5.5 Service Pack を使用している場合は、Windows または Android™ プレーヤーの環境を設定します。

AEM オーサーインスタンスおよびパブリッシュインスタンスの **Adobe Experience Manager Web コンソール設定**&#x200B;で、**login-token cookies の SameSite 属性**&#x200B;を **Lax** から **None** に設定します。

* 詳しくは、[Windows 10 プレーヤーの実装](implementing-windows-player.md#fp-environment-setup)を参照してください。

* 参照： [Android™ プレーヤーの実装](implementing-android-player.md#fp-environment-setup) を参照してください。

### リリースされている AEM Screens Player

AEM Screens でリリースされた AEM 6.5 機能パック 5 向けに、次の AEM Screens Player がリリースされています。

* Chrome OS
* Windows
* Android™

#### AEM Screens Player のダウンロード 

最新のAEM Screens Player のダウンロードとバグ修正について詳しくは、以下を参照してください。 **[AEM Screens Player のダウンロード](https://download.macromedia.com/screens/index.html)**.
