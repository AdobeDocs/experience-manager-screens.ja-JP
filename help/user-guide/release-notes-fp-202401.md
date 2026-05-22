---
title: Screens 機能パック 202401 のリリースノート
description: 2024年1月2日（PT）にリリースされた AEM Screens 機能パック 202401 について説明します。
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: 9879f339-e70f-446d-acd3-380016269f27
TQID: https://experienceleague.adobe.com/b6ZM04Vl6ozehx8E-y9iV1KAo-FI7DZSpDcHvhudkMI
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 248
ht-degree: 91%

---

# 機能パック 202401 のリリースノート {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>最新バージョンの 6.5 Adobe Experience Manager（AEM 6.5）にアップグレードすることをお勧めします。 最新バージョンの情報は、[こちら](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/release-notes/release-notes)から入手できます。

## 入手方法 {#availability}

AEM Screens は、AEM 6.5 機能パック 11.1 をリリースしました。

AEM Screensの最新の機能パック 6.5.11.1 リリースは、[Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/ja/aem.html)からAdobe IDを使用してダウンロードできます。 「**Adobe Experience Manager**」タブに移動し、「**Screens**」を検索して、**AEM 6.5 Screens FP11.1** というタイトルが付いた最新の機能パックを入手します。

## リリース日 {#release-date}

AEM Screens 機能パック 202204 のリリース日は 2024年1月2日（PT）です。

### 新機能 {#what-is-new}

このリリースにはセキュリティ修正のみ含まれています。

### バグ修正 {#bug-fixes}

* AEM Screens デバイスの「アイドルテキスト」フィールドでの XSS の問題。 （SCRNS-2614）

* `Clear cache` アクションダイアログを介した `screens/dashboard/device.html` での XSS の問題。 （SCRNS-2632）

* `libs/screens/player/browser/firmware.html` の Screens Player 設定での XSS の問題。 （SCRNS-2652）

* デバイスのタイトルに保存された XSS は、デバイスを削除するとトリガーされます。 （SCRNS-2653）

* `/libs/screens/core/components/device/info.json.html` での XSS の問題。 （SCRNS-2659）

* `/screens/register-device-wizard.html` でパラメーター `item` を使用した XSS が反映されました。 （SCRNS-2670）

* `returnPage` パラメーターを介して `screens/dashboard/device.html` に XSS が反映されました。 （SCRNS-3056）

* assign-device-wizard.html でリダイレクトが開かれます。 （SCRNS-3444）

* デバイスダッシュボードでリダイレクトが開かれます。 （SCRNS-3443）

* `libs/screens/dcc/components/clientlibs/actions/cq.screens.dcc.openLink.js` での XSS の問題。 （SCRNS-3459）

* 「繰り返しスケジュール」ボタンと「スケジュールを追加」ボタンが見つからない、というチャネルスケジュールで検出された問題を修正しました。 （SCRNS-2739）
