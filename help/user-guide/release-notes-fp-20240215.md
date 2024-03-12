---
title: Screens 機能パック 20240215 のリリースノート
description: 2024 年 2 月 15 日にリリースされたAEM Screens機能パック20240215について説明します。
feature: Feature Pack
role: Developer
level: Intermediate
source-git-commit: d5b94814df33f00e23fcd22e85e50d6f02947d45
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 58%

---

# 機能パック 20240215 のリリースノート {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>最新バージョンの 6.5 Adobe Experience Manager（AEM 6.5）にアップグレードすることをお勧めします。最新バージョンの情報は、[こちら](https://experienceleague.adobe.com/docs/experience-manager-65/content/release-notes/release-notes.html?lang=ja)から入手できます

## 入手方法 {#availability}

AEM Screens では、AEM 6.5 機能パック 11.3 をリリースしました。

Adobe ID を使用して、AEM Screens 6.5.11.3 リリースの最新の機能パックを[ソフトウェア配布ポータル](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)からダウンロードできます。に移動します。 **Adobe Experience Manager** タブと検索 **Screens** というタイトルの最新の機能パックを取得するには **AEM 6.5 Screens FP11.3**.

## リリース日 {#release-date}

AEM Screens機能パック20240215のリリース日は 2024 年 2 月 15 日です。

### 新機能 {#what-is-new}

このリリースにはセキュリティ修正のみ含まれています。

### バグの修正 {#bug-fixes}

* XSS の FP11.1 で前述した修正から、トグルチェックを削除しました。 `libs/screens/dcc/components/clientlibs/actions/cq.screens.dcc.openLink.js`. （SCRNS-3459）

* `libs/screens/dcc/components/clientlibs/columnviewnavigatorshim.js` での XSS の問題。（SCRNS-3973）
