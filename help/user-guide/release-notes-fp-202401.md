---
title: Screens 機能パック202401のリリースノート
description: 2024 年 1 月 2 日にリリースされたAEM Screens機能パック202401について説明します。
feature: Feature Pack
role: Developer
level: Intermediate
source-git-commit: e172d2a4a3d2c1f3b555edc8f8ea41b663fc0a30
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 7%

---

# 機能パック 202401 のリリースノート {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>最新バージョンの 6.5 Adobe Experience Manager(AEM 6.5) にアップグレードすることをお勧めします。 最新バージョンの情報は、次の場所から入手できます： [ここ](https://experienceleague.adobe.com/docs/experience-manager-65/content/release-notes/release-notes.html?lang=en)

## 入手方法 {#availability}

AEM Screensは、 AEM 6.5 機能パック 11.1 をリリースしました。

AEM Screens 6.5.11.1リリースの最新の機能パックは、 [ソフトウェア配布ポータル](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) Adobe IDを使用して に移動します。 **Adobe Experience Manager** タブと検索 **Screens** というタイトルの最新の機能パックを取得するには **AEM 6.5 Screens FP11.1**.

## リリース日 {#release-date}

AEM Screens機能パック202204のリリース日は 2024 年 1 月 2 日です。

### 新機能 {#what-is-new}

このリリースには、セキュリティの修正のみが含まれています。

### バグの修正 {#bug-fixes}

* AEM Screensデバイスの「Idle text」フィールドで XSS 問題が発生。 (SCRNS-2614)

* XSS の問題： `screens/dashboard/device.html` 経由 `Clear cache` アクションダイアログ。 (SCRNS-2632)

* 次の Screens Player 設定の XSS 問題 `libs/screens/player/browser/firmware.html`. (SCRNS-2652)

* デバイスの削除時に、XSS をデバイスのタイトルトリガーに格納しました。 (SCRNS-2653)

* XSS の問題： `/libs/screens/core/components/device/info.json.html`. (SCRNS-2659)

* XSS がパラメーターで反映されました `item` 時刻 `/screens/register-device-wizard.html`. (SCRNS-2670)

* での XSS の反映 `screens/dashboard/device.html` 経由 `returnPage` パラメーター。 (SCRNS-3056)

* assign-device-wizard.html でリダイレクトを開きます。 (SCRNS-3444)

* デバイスダッシュボードでリダイレクトを開きます。 (SCRNS-3443)

* XSS の問題： `libs/screens/dcc/components/clientlibs/actions/cq.screens.dcc.openLink.js`. (SCRNS-3459)

* 「繰り返しスケジュール」および「スケジュールを追加」ボタンの不足を修正しました：チャネルスケジュールで問題が見つかりました。 (SCRNS-2739)

#### AEM Screens Player のダウンロード   {#aem-screens-player-downloads}

最新のAEM Screens Player をダウンロードするには、 **[AEM Screens Player のダウンロード](https://download.macromedia.com/screens/index.html)**.
