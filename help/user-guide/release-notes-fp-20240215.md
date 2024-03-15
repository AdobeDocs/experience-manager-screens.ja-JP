---
title: Screens 機能パック 20240215 のリリースノート
description: 2024年2月15日（PT）にリリースされた AEM Screens 機能パック 20240215 については、このページを参照してください。
feature: Feature Pack
role: Developer
level: Intermediate
source-git-commit: d5b94814df33f00e23fcd22e85e50d6f02947d45
workflow-type: ht
source-wordcount: '155'
ht-degree: 100%

---

# 機能パック 20240215 のリリースノート {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>最新バージョンの 6.5 Adobe Experience Manager（AEM 6.5）にアップグレードすることをお勧めします。最新バージョンの情報は、[こちら](https://experienceleague.adobe.com/docs/experience-manager-65/content/release-notes/release-notes.html?lang=ja)から入手できます

## 入手方法 {#availability}

AEM Screens は、AEM 6.5 機能パック 11.3 をリリースしました。

Adobe ID を使用して、AEM Screens 6.5.11.3 リリースの最新の機能パックを[ソフトウェア配布ポータル](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)からダウンロードできます。「**Adobe Experience Manager**」タブに移動し、「**Screens**」を検索して「**AEM 6.5 Screens FP11.3**」というタイトルが付いた最新の機能パックを入手します。

## リリース日 {#release-date}

AEM Screens 機能パック 20240215 のリリース日は 2024年2月15日（PT）です。

### 新機能 {#what-is-new}

このリリースにはセキュリティ修正のみ含まれています。

### バグの修正 {#bug-fixes}

* `libs/screens/dcc/components/clientlibs/actions/cq.screens.dcc.openLink.js` の XSS 用に FP11.1 で以前に提供された修正から切替スイッチのチェックを削除しました。（SCRNS-3459）

* `libs/screens/dcc/components/clientlibs/columnviewnavigatorshim.js` での XSS の問題。（SCRNS-3973）
