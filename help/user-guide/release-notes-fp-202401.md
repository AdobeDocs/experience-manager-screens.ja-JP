---
title: Screens 機能パック 202401 のリリースノート
description: 2024 年 1 月 2 日（PT）にリリースされたAEM Screens機能パック 202401 について説明します。
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: 9879f339-e70f-446d-acd3-380016269f27
source-git-commit: 10c168cd00b79964d229e3d2a14049e799d89d77
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 85%

---

# 機能パック 202401 のリリースノート {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>Adobeでは、最新バージョンの 6.5 Adobe Experience Manager（AEM 6.5）にアップグレードすることをお勧めします。 から最新のバージョン情報を取得します [こちら](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/release-notes/release-notes)

## 入手方法 {#availability}

AEM Screens では、AEM 6.5 機能パック 11.1 をリリースしました。

Adobe ID を使用して、AEM Screens 6.5.11.1 リリースの最新の機能パックを[ソフトウェア配布ポータル](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)からダウンロードできます。「**Adobe Experience Manager**」タブに移動し、「**Screens**」を検索して「**AEM 6.5 Screens FP11.1**」というタイトルが付いた最新の機能パックを入手します。

## リリース日 {#release-date}

AEM Screens 機能パック 202204 のリリース日は 2024年1月2日（PT）です。

### 新機能 {#what-is-new}

このリリースにはセキュリティ修正のみ含まれています。

### バグの修正 {#bug-fixes}

* AEM Screens デバイスの「アイドルテキスト」フィールドでの XSS の問題。（SCRNS-2614）

* `Clear cache` アクションダイアログ経由の `screens/dashboard/device.html` での XSS の問題。（SCRNS-2632）

* `libs/screens/player/browser/firmware.html` の Screens Player 設定での XSS の問題。（SCRNS-2652）

* デバイスのタイトルに保存された XSS は、デバイスを削除するとトリガーされます。（SCRNS-2653）

* `/libs/screens/core/components/device/info.json.html` での XSS の問題。（SCRNS-2659）

* `/screens/register-device-wizard.html` でパラメーター `item` を使用した XSS が反映されました。（SCRNS-2670）

* `returnPage` パラメーター経由で `screens/dashboard/device.html` に XSS が反映されました。（SCRNS-3056）

* assign-device-wizard.html でリダイレクトが開かれます。（SCRNS-3444）

* デバイスダッシュボードでリダイレクトが開かれます。（SCRNS-3443）

* `libs/screens/dcc/components/clientlibs/actions/cq.screens.dcc.openLink.js` での XSS の問題。（SCRNS-3459）

* 「繰り返しスケジュール」ボタンと「スケジュールを追加」ボタンが見つからない、というチャネルスケジュールで検出された問題を修正しました。（SCRNS-2739）
