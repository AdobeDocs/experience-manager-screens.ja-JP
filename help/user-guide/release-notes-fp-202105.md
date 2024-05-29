---
title: 機能パック 202105 のリリースノート
description: 2021年6月4日（PT）にリリースされた AEM Screens 機能パック 202105 について説明します。
feature: Feature Pack
role: Developer
level: Intermediate
exl-id: fc210d9d-5fac-4147-849d-182ffbaf0a5e
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: ht
source-wordcount: '400'
ht-degree: 100%

---

# 機能パック 202105 のリリースノート {#release-notes-for-feature-pack}

>[!CAUTION]
>最新バージョンの Adobe Experience Manager（AEM）にアップグレードすることをお勧めします。AEM Screens では、AEM 6.3 Screens プラットフォームのメンテナンスサポートを提供しています。

## 入手方法 {#availability}

AEM Screens は、AEM 6.5 機能パック 8 をリリースしました。

Adobe ID を使用して、AEM Screens 6.5.8 リリースの最新機能パックを[ソフトウェア配布ポータル](https://experience.adobe.com/#/downloads/content/software-distribution/ja/aem.html)からダウンロードできます。「**Adobe Experience Manager**」タブに移動し、「**Screens**」を検索して「**AEM 6.5 Screens FP8**」というタイトルが付いた最新の機能パックを入手します。

>[!IMPORTANT]
>`screens-cloud-ams-pkg-0.0.20`、`screens-cloud-ams-pkg-0.0.16`、`screens core bundles` パッケージをインストールした後で AMS コネクタを動作させるには、最小バージョンの AEM 6.5 機能パック 8 をインストールします。

## リリース日 {#release-date}

AEM Screens 機能パック 202105 のリリース日は 2021 年 6 月 4 日（PT）です。

### 新機能 {#what-is-new}

* **AEM Screens チャネルでのページのロック**

  AEM Screens では、AEM Sites で既に実装されているように、*ページのロック*&#x200B;をサポートするようになりました。Adobe Experience Manager（AEM）では、他のユーザーがコンテンツを編集できないようにページをロックすることができます。この機能は、1 つの特定のページで大量の編集作業を行う場合や、短期間ページを凍結する必要がある場合に便利です。

* **AEM Screens Player デバイスの命名**

  AEM Screens Player で、デバイス名を Adobe Experience Manager（AEM）に送信できるようになりました。デフォルトでは、一括登録を使用してデバイスを登録すると、システムで生成されたユーザー名が「タイトル」フィールドに入力されます。あるいは、顧客がアセットタグやその他のわかりやすい名前を使用することもできます。この場合は、その名前が AEM に表示され、適切なコンテンツを割り当てやすくなります。

  サポートされている各オペレーティングシステムでの名前の設定方法については、次のドキュメントを参照してください。

   * [Android](/help/user-guide/implementing-android-player.md#name-android)
   * [Windows](/help/user-guide/implementing-windows-player.md#name-windows)
   * [Tizen](/help/user-guide/tizen-player.md#name-tizen)
   * [Chrome OS](/help/user-guide/implementing-chrome-os-player.md#name-chrome)

* **マニフェストの生成**

  チャネルマニフェストの生成が迅速化されたほか、サーバー上に割り当てられるリソースの削減など、パフォーマンスが向上しました。

### バグ修正 {#bug-fixes}

* 動的埋め込みシーケンスを含んだチャネルに切り替えると、プレーヤーの画面が黒くなる。
* Screens Player で、破損したチャネルへの切り替えがブロックされるようになり、それ以降の 404 エラーやエラーメッセージが表示されるページを回避できます。

### リリースされている AEM Screens Player

AEM Screens 6.5 機能パック 8 向けに、次の AEM Screens Player がリリースされています。

* Chrome OS
* Windows
* Tizen
* Android™
* Linux®

#### AEM Screens Player のダウンロード

最新の AEM Screens Player のダウンロードとバグ修正について詳しくは、**[AEM Screens Player のダウンロード](https://download.macromedia.com/screens/index.html)**&#x200B;を参照してください。
