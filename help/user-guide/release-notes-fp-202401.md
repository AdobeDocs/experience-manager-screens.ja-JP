---
title: Screens 機能パック 202401 のリリースノート
description: 2024 年 1 月 2 日（PT）にリリースされたAEM Screens機能パック 202401 について説明します。
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: 9879f339-e70f-446d-acd3-380016269f27
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 58%

---

# 機能パック 202401 のリリースノート {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>Adobeでは、最新バージョンの 6.5 Adobe Experience Manager（AEM 6.5）にアップグレードすることをお勧めします。 から最新のバージョン情報を取得します [こちら](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/release-notes/release-notes).

## 可用性 {#availability}

AEM Screens は、AEM 6.5 機能パック 11.1 をリリースしました。

AEM Screens 6.5.11.1 リリースの最新の機能パックは、からダウンロードできます。 [ソフトウェア配布ポータル](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) Adobe IDを使用する。 に移動します。 **Adobe Experience Manager** タブで「」を検索 **スクリーン** というタイトルの最新の機能パックを取得するには **AEM 6.5 Screens FP11.1**.

## リリース日 {#release-date}

AEM Screens 機能パック 202204 のリリース日は 2024年1月2日（PT）です。

### 新機能 {#what-is-new}

このリリースにはセキュリティ修正のみ含まれています。

### バグの修正 {#bug-fixes}

* AEM Screens デバイスの「アイドルテキスト」フィールドでの XSS の問題。（SCRNS-2614）

* での XSS の問題 `screens/dashboard/device.html` 経由 `Clear cache` アクションダイアログ。 （SCRNS-2632）

* `libs/screens/player/browser/firmware.html` の Screens Player 設定での XSS の問題。（SCRNS-2652）

* デバイスのタイトルに保存された XSS は、デバイスを削除するとトリガーされます。（SCRNS-2653）

* `/libs/screens/core/components/device/info.json.html` での XSS の問題。（SCRNS-2659）

* `/screens/register-device-wizard.html` でパラメーター `item` を使用した XSS が反映されました。（SCRNS-2670）

* XSS の反映先 `screens/dashboard/device.html` 経由 `returnPage` パラメーター。 （SCRNS-3056）

* assign-device-wizard.html でリダイレクトが開かれます。（SCRNS-3444）

* デバイスダッシュボードでリダイレクトが開かれます。（SCRNS-3443）

* `libs/screens/dcc/components/clientlibs/actions/cq.screens.dcc.openLink.js` での XSS の問題。（SCRNS-3459）

* 「繰り返しスケジュール」ボタンと「スケジュールを追加」ボタンが見つからない、というチャネルスケジュールで検出された問題を修正しました。（SCRNS-2739）