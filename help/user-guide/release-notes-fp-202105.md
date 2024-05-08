---
title: 機能パック 202105 のリリースノート
description: 2021 年 6 月 4 日（PT）にリリースされたAEM Screens機能パック 202105 について説明します。
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: fc210d9d-5fac-4147-849d-182ffbaf0a5e
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 35%

---

# 機能パック 202105 のリリースノート {#release-notes-for-feature-pack}

>[!CAUTION]
>Adobeでは、最新バージョンのAdobe Experience Manager（AEM）にアップグレードすることをお勧めします。 AEM Screensは、AEM 6.3 Screens プラットフォームのメンテナンスサポートを提供します。

## 入手方法 {#availability}

AEM Screens は、AEM 6.5 機能パック 8 をリリースしました。

AEM Screens 6.5.8 リリースの最新の機能パックは、からダウンロードできます。 [ソフトウェア配布ポータル](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) Adobe IDを使用する。 に移動します。 **Adobe Experience Manager** タブで「」を検索 **スクリーン** というタイトルの最新の機能パックを取得するには **AEM 6.5 Screens FP8**.

>[!IMPORTANT]
>パッケージのインストール後に AMS コネクタを動作させるには、最小バージョンのAEM 6.5 機能パック 8 をインストールします `screens-cloud-ams-pkg-0.0.20`, `screens-cloud-ams-pkg-0.0.16`、および `screens core bundles`.

## リリース日 {#release-date}

AEM Screens 機能パック 202105 のリリース日は 2021 年 6 月 4 日（PT）です。

### 新機能 {#what-is-new}

* **AEM Screens チャネルでのページのロック**

  AEM Screens では、AEM Sites で既に実装されているように、*ページのロック*&#x200B;をサポートするようになりました。Adobe Experience Manager（AEM）を使用すると、他のユーザーがコンテンツを編集できないようにページをロックできます。 この機能は、ある特定のページで大量の編集作業を行う場合や、短期間ページを凍結する必要がある場合に便利です。

* **AEM Screens Player デバイスの命名**

  AEM Screens Player で、デバイス名を Adobe Experience Manager（AEM）に送信できるようになりました。デフォルトでは、一括登録を使用してデバイスを登録すると、システムで生成されたユーザー名が「タイトル」フィールドに入力されます。 あるいは、顧客がアセットタグやその他のわかりやすい名前を使用することもできます。この場合は、その名前が AEM に表示され、適切なコンテンツを割り当てやすくなります。

  サポート対象の各オペレーティングシステムで名前を設定する方法については、次のドキュメントを参照してください。

   * [Android](/help/user-guide/implementing-android-player.md#name-android)
   * [Windows](/help/user-guide/implementing-windows-player.md#name-windows)
   * [Tizen](/help/user-guide/tizen-player.md#name-tizen)
   * [Chrome OS](/help/user-guide/implementing-chrome-os-player.md#name-chrome)

* **マニフェストの生成**

  チャネルマニフェストの生成が迅速化されたほか、サーバー上に割り当てられるリソースの削減など、パフォーマンスが向上しました。

### バグの修正 {#bug-fixes}

* 動的埋め込みシーケンスを含むチャネルに切り替えると、プレーヤーの画面が黒くなっていました。
* Screens Player で、破損したチャネルへの切り替えがブロックされるようになりました。これにより、それ以降の 404 エラーやエラーメッセージを含むページの表示を回避できます。

### リリースされている AEM Screens Player

AEM Screens 6.5 機能パック 8 向けに、次の AEM Screens Player がリリースされています。

* Chrome OS
* Windows
* Tizen
* Android™
* Linux®

#### AEM Screens Player のダウンロード 

最新のAEM Screens Player のダウンロードとバグ修正について詳しくは、以下を参照してください。 **[AEM Screens Player のダウンロード](https://download.macromedia.com/screens/index.html)**.
