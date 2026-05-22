---
title: Screens 機能パック 20250327 のリリースノート
description: 2025年3月27日（PT）にリリースされた AEM Screens 機能パック 20250327 について説明します。
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: cadd83cd-fe64-436d-b3fd-6d72b9565885
TQID: https://experienceleague.adobe.com/q6KAClMHbAULOEumQlx5-FdaaVmAcMOCL8m6KWIB458
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 270
ht-degree: 39%

---

# 機能パック 20250327 のリリースノート {#release-notes-for-screens-feature-pack}

>[!CAUTION]
>最新バージョンの 6.5 Adobe Experience Manager（AEM 6.5）にアップグレードすることをお勧めします。 最新バージョンの情報は、[こちら](https://experienceleague.adobe.com/ja/docs/experience-manager-65/content/release-notes/release-notes)から入手できます
>Adobeでは、SP （servicepack） >= 21でFP11.6を使用することをお勧めします。

## 入手方法 {#availability}

AEM Screens は、AEM 6.5 機能パック 11.6 をリリースしました。

AEM Screensの最新の機能パック 6.5.11.6 リリースは、[Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/ja/aem.html)からAdobe IDを使用してダウンロードできます。 **Adobe Experience Manager** タブに移動し、**Screens**&#x200B;を検索して、**AEM 6.5 Screens FP11.6**&#x200B;というタイトルの最新の機能パックを取得します。

## リリース日 {#release-date}

AEM Screens 機能パック 20250327 のリリース日は 2025年3月27日です。

### 新機能 {#what-is-new}

* このリリースでは、Service Pack 21以降でユーザーが直面するパッケージの競合が修正されています。

* このリリースでは、SP22以降のカードビューの問題を修正します。

* **AEM Screens Playersの更新**
   * Linux ベースのAEM Screens Playerは正式に廃止されました。 AEM Screensがサポートする別のオペレーティングシステムに移行することをお勧めします。
   * Android ベースのAEM Screens Playerに対して、これ以上の更新や機能強化は行われません。 AEM Screensがサポートする別のオペレーティングシステムに移行することをお勧めします。

### バグ修正 {#bug-fixes}

* Service Pack 21およびScreens機能パックとのパッケージの競合。 （SCRNS-4638）

* Screensダッシュボードが機能しない。 （SCRNS-4749）

* XSSの問題（/libs/screens/dcc/components/dashboard/clientlibs/device-clear-cache.js）（SCRNS-4761）
