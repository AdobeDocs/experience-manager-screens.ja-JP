---
title: '機能パック 202105 のリリースノート '
description: 「2021年6月4日にリリースされたAEM Screens機能パック202105について説明します。」
feature: 機能パック
role: Developer
level: Intermediate
source-git-commit: 444535b38fdf112939fdbf4c0f3f48e1cc28c902
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 46%

---

# 機能パック 202105 のリリースノート {#release-notes-for-feature-pack}

>[!CAUTION]
>最新バージョンの Adobe Experience Manager（AEM）にアップグレードすることをお勧めします。Screens では、AEM 6.3 Screens プラットフォームのメンテナンスサポートを提供しています。

## 入手方法 {#availability}

AEM Screens は、AEM 6.5 機能パック 8 をリリースしました。

Adobe ID を使用して、AEM Screens 6.5.8 リリースの最新の機能パックを[ソフトウェア配布ポータル](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)からダウンロードできます。「**Adobe Experience Manager**」タブに移動し、「**Screens**」を検索して「**AEM 6.5 Screens FP8**」というタイトルが付いた最新の機能パックを入手します。

## リリース日 {#release-date}

AEM Screens機能パック202105のリリース日は2021年6月4日です。

### 新機能 {#what-is-new}

* **AEM Screensチャネルでのページのロック**

   AEM Screensは、AEM Sitesで既に実装されているように、*ページ*&#x200B;のロックをサポートするようになりました。 Adobe Experience Manager(AEM)では、他のユーザーがコンテンツを変更できないように、ページをロックできます。 ページのロックは、1 つの特定のページで大量の編集作業をおこなう場合や、短期間ページを凍結する必要がある場合に便利です。

* **AEM Screens Playerデバイスの命名**

   AEM Screensプレーヤーに、Adobe Experience Manager(AEM)にデバイス名を送信する機能が追加されました。
デフォルトでは、一括登録を使用してデバイスを登録すると、システムで生成されたユーザー名が「タイトル」フィールドに入力されます。 別の方法として、顧客は、アセットタグやその他のわかりやすい名前を使用して、AEMで見やすく、適切なコンテンツを割り当てるのが容易になります。

   サポートされる各オペレーティングシステムでの名前の設定方法については、次のドキュメントを参照してください。

   * [Android](/help/user-guide/implementing-android-player.md#name-android)
   * [Windows](/help/user-guide/implementing-windows-player.md#name-windows)
   * [Tizen](/help/user-guide/tizen-player.md#name-tizen)
   * [Chrome OS](/help/user-guide/implementing-chrome-os-player.md#name-chrome)

* **マニフェストの生成**

   サーバー上で割り当てるリソースの削減など、パフォーマンスの向上により、チャネルマニフェストの生成が高速化されます。

### バグ修正 {#bug-fixes}

* 動的埋め込みシーケンスを含むチャネルに切り替えると、プレーヤーに黒い画面が表示される問題を修正しました。
* Screensプレーヤーは、404エラーやエラーメッセージが表示されるページを回避する、壊れたチャネルへの切り替えをブロックするようになりました。

### リリースされている AEM Screens Player {#released-aem-screens-players}

AEM Screens 6.5 機能パック 8 向けに、次の AEM Screens Player がリリースされています。

* Chrome OS
* Windows
* Tizen
* Android
* Linux

#### AEM Screens Player のダウンロード {#aem-screens-player-downloads}

最新の AEM Screens Player のダウンロードとバグ修正について詳しくは、**[AEM Screens Player のダウンロード](https://download.macromedia.com/screens/index.html)**&#x200B;を参照してください。
