---
title: データトリガーを使用したオーサリング
seo-title: データトリガーを使用したオーサリング
description: データトリガーを使用して作成する方法については、このページを参照してください。
translation-type: tm+mt
source-git-commit: 24fda825220c6c2863fd76098a2f06209d9e0190

---


# データトリガーを使用したオーサリング {#authoring-with-data-triggers}

ここでは、チャネルでターゲット設定を有効にする方法について説明します。

>>[!I重要]:AEM Screensチャネルでデータトリガーをサポートする最小バージョンは、AEM 6.4.3機能パック3です。
>

## 前提条件 {#prereqs}

チャネルでのターゲット設定を有効にするには、次の手順に従う前に、「AEM Screensでの設定」の「主な用語」で、AEM Screensでの [ContextHubとターゲット設定を理解するために](configuring-context-hub.md) 「AEM Screensでの設定」を参照してください。

>[!I重要な]
> AEM Screensチャネルでターゲット設定を有効にする前に、ContextHubの設定を理解し、設定することをお勧めします。

詳しくは、次のリンクを参照してください。

1. **[データストアの設定](configuring-context-hub.md)**
1. **[オーディエンスセグメントの設定](configuring-context-hub.md)**

上記の手順を完了したら、チャネルでターゲット設定を有効にする準備が整いました。

## Data Triggersを使用したオーサリングの概要 {#author-targeting}

>[!VIDEO](https://video.tv.adobe.com/v/31921)

## AEM Screensチャネルでのターゲティングの有効化 {#enabling-targeting}

以下の手順に従って、チャネルでターゲティングを有効にします。

1. AEM Screens チャネルのいずれかに移動します。The following steps demonstrate how to enable targeting by using **DataDrivenRetail** *(sequence channel)* created in an AEM Screens Channel.

1. **DataDrivenRetail** チャネルを選択し、アクションバーの「**プロパティ**」をクリックします。

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. 「**パーソナライゼーション**」タブを選択して、ContextHub 設定をセットアップします。

   1. 「**ContextHub のパス**」として **libs**/**settings**/**cloudsettings**/**default**/**ContextHub Configurations** を選択し、「**選択**」をクリックします。

   1. 「**セグメントのパス**」として **conf**/**we-retail**/**settings**/**wcm**/**segments** を選択し、「**選択**」をクリックします。

   1. 「**保存して閉じる**」をクリックします。
   >[!NOTE]
   ContextHub 設定とセグメントをそれぞれ最初に保存した、Context Hub とセグメントのパスを使用します。

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. **DataDrivenAssets**／**チャネル**&#x200B;に移動して「**DataDrivenRetail**」を選択し、アクションバーの「**編集**」をクリックします。

   >[!NOTE]
   すべてを正しくセットアップしたら、下図に示すように、エディターのドロップダウンに「**ターゲティング**」オプションが表示されます。

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

   >[!NOTE]
   チャネルの ContextHub 設定を完了したら、以下のすべての使用例に従う場合は、他の 3 つのシーケンスチャネルについても必ず上記の手順 1～4 に従ってください。

### 詳細情報：使用例 {#learn-more-example-use-cases}

AEM Screens プロジェクトに ContextHub を設定したら、以下の様々な使用例を通じて、データでトリガーされるアセットが様々な業界でいかに重要な役割を果たしているかを理解できます。

1. **[小売店向けの在庫に応じたアクティベーション](retail-inventory-activation.md)**
1. **[旅行センター向けの気温に応じたアクティベーション](local-temperature-activation.md)**
1. **[接客業向けの予約状況に応じたアクティベーション](hospitality-reservation-activation.md)**

