---
title: データトリガーを使用したオーサリング
seo-title: データトリガーを使用したオーサリング
description: データトリガーを使用して作成する方法については、このページを参照してください。
feature: Screens のオーサリング
role: Admin, Developer
level: Intermediate
exl-id: c95da2e9-a216-4d0a-85d0-a0fb895a8d8a
source-git-commit: acf925b7e4f3bba44ffee26919f7078dd9c491ff
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 100%

---

# データトリガーを使用したオーサリング {#authoring-with-data-triggers}

ここでは、チャネルでターゲティングを有効にする方法について説明します。

>[!IMPORTANT]
>
>AEM Screens チャネルでデータトリガーをサポートする最小バージョンは、AEM 6.5.3 機能パック 3 です。

## 前提条件 {#prereqs}

チャネルでのターゲティングを有効にするには、次の手順に従う前に、AEM Screens での ContextHub とターゲティングを理解するために「[AEM Screens の設定における主な用語](configuring-context-hub.md)」を参照してください。

>[!IMPORTANT]
>
>AEM Screens チャネルでターゲティングを有効にする前に、ContextHub の設定を理解し、設定することをお勧めします。

詳しくは、次のリンクを参照してください。

1. **[データストアの設定](configuring-context-hub.md)**
1. **[オーディエンスのセグメント化の設定](configuring-context-hub.md)**

上記の手順を完了したら、チャネルでターゲティングを有効にする準備が整いました。

## データトリガーを使用したオーサリングの概要 {#author-targeting}

>[!VIDEO](https://video.tv.adobe.com/v/31921)

## AEM Screens チャネルでのターゲティングの有効化 {#enabling-targeting}

以下の手順に従って、チャネルでターゲティングを有効にします。

1. AEM Screens チャネルのいずれかに移動します。以下の手順は、AEM Screens チャネルで作成した **DataDrivenRetail** *（シーケンスチャネル）*&#x200B;を使用してターゲティングを有効にする方法を示しています。

1. **DataDrivenRetail** チャネルを選択し、アクションバーの「**プロパティ**」をクリックします。

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. 「**パーソナライズ機能**」タブを選択して ContextHub 設定を設定し、ContextHub とセグメントのパスを選択します。

   1. 「**ContextHub のパス**」として **libs**/**settings**/**cloudsettings**/**default**/**ContextHub 設定** を選択し、「**選択**」をクリックします。

   1. 「**セグメントのパス**」として **conf**/**We.Retail**/**settings**/**wcm**/**segments** を選択し、「**選択**」をクリックします。

   1. 「**保存して閉じる**」をクリックします。
   >[!NOTE]
   >
   >ContextHub 設定とセグメントをそれぞれ最初に保存した、Context Hub とセグメントのパスを使用します。

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. **DataDrivenAssets**／**チャネル**&#x200B;に移動して「**DataDrivenRetail**」を選択し、アクションバーの「**編集**」をクリックします。チャンネルエディターでアセットをドラッグ&amp;ドロップします。

   >[!NOTE]
   >
   >すべてを正しくセットアップしたら、下図に示すように、エディターのドロップダウンに「**ターゲティング**」オプションが表示されます。

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

1. 「**ターゲティング**」をクリック

1. 「**ブランド**」と「**アクティビティ**」のドロップダウンメニューから選択し、「**ターゲティングを開始**」をクリックします。

### 詳細情報：使用例 {#learn-more-example-use-cases}

AEM Screens プロジェクトに ContextHub を設定したら、以下の様々な使用例を通じて、データでトリガーされるアセットが様々な業界でいかに重要な役割を果たしているかを理解できます。

1. **[小売店向けの在庫に応じたアクティベーション](retail-inventory-activation.md)**
1. **[旅行センター向けの気温に応じたアクティベーション](local-temperature-activation.md)**
1. **[接客業向けの予約状況に応じたアクティベーション](hospitality-reservation-activation.md)**
