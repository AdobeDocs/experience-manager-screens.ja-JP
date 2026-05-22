---
title: Screens 機能パック 20240215 のリリースノート
description: 2024年2月15日（PT）にリリースされた AEM Screens 機能パック 20240215 について説明します。
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: e4149f5b-42c0-43c8-b275-ecbe90104a98
TQID: https://experienceleague.adobe.com/yasPGCEV-9sw-TNqKeF0NJo6p1UKi2JvfYyR4D4ID-g
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
source-wordcount: 172
ht-degree: 88%

---

# 機能パック 20240215 のリリースノート {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>最新バージョンの 6.5 Adobe Experience Manager（AEM 6.5）にアップグレードすることをお勧めします。 最新バージョンの情報は、[こちら](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/release-notes/release-notes)から入手できます

## 入手方法 {#availability}

AEM Screens は、AEM 6.5 機能パック 11.3 をリリースしました。

AEM Screensの最新の機能パック 6.5.11.3 リリースは、[Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/ja/aem.html)からAdobe IDを使用してダウンロードできます。 「**Adobe Experience Manager**」タブに移動し、「**Screens**」を検索して、**AEM 6.5 Screens FP11.3** というタイトルが付いた最新の機能パックを入手します。

## リリース日 {#release-date}

AEM Screens 機能パック 20240215 のリリース日は 2024年2月15日（PT）です。

### 新機能 {#what-is-new}

このリリースにはセキュリティ修正のみ含まれています。

### バグ修正 {#bug-fixes}

* `libs/screens/dcc/components/clientlibs/actions/cq.screens.dcc.openLink.js` の XSS 用に FP11.1 で以前に提供された修正から切替スイッチのチェックを削除しました。 （SCRNS-3459）

* `libs/screens/dcc/components/clientlibs/columnviewnavigatorshim.js` での XSS の問題。 （SCRNS-3973）
