---
title: データトリガーを使用したオーサリング
description: AEM Screens チャネルでデータトリガーを使用してオーサリングする方法について詳しく説明します。
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: c95da2e9-a216-4d0a-85d0-a0fb895a8d8a
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 67%

---

# データトリガーを使用したオーサリング {#authoring-with-data-triggers}

ここでは、チャネルでターゲティングを有効にする方法について説明します。

>[!IMPORTANT]
>
>AEM Screens チャネルでデータトリガーをサポートする最小バージョンは、AEM 6.5.3 機能パック 3 です。

## 前提条件 {#prereqs}

チャネルでターゲティングを有効にするには、次の手順に従う前に [AEM Screensでのの設定の主な用語](configuring-context-hub.md) AEM Screensの ContextHub とターゲティングを理解するために必要です。

>[!IMPORTANT]
>
>AEM Screens チャネルでターゲティングを有効にする前に、ContextHub の設定を理解し、設定することをお勧めします。

詳しくは、次のリンクを参照してください。

1. **[データストアの設定](configuring-context-hub.md)**
1. **[オーディエンスのセグメント化の設定](configuring-context-hub.md)**

上記の手順を完了すると、チャネルでのターゲティングを有効にする準備が整います。

## データトリガーを使用したオーサリングの概要 {#author-targeting}

>[!VIDEO](https://video.tv.adobe.com/v/31921)

## AEM Screens チャネルでのターゲティングの有効化 {#enabling-targeting}

以下の手順に従って、チャネルでターゲティングを有効にします。

1. AEM Screens チャネルのいずれかに移動します。 以下の手順は、AEM Screens チャネルで作成した **DataDrivenRetail** *（シーケンスチャネル）*&#x200B;を使用してターゲティングを有効にする方法を示しています。

1. **DataDrivenRetail** チャネルを選択し、アクションバーの「**プロパティ**」をクリックします。

   ![screen_shot_2019-05-01at43332pm](assets/screen_shot_2019-05-01at43332pm.png)

1. 「」を選択します **Personalization** タブをクリックして、ContextHub 設定をセットアップし、ContextHub とセグメントのパスを選択します。

   1. 「**ContextHub のパス**」として **libs**/**settings**/**cloudsettings**/**default**/**ContextHub 設定** を選択し、「**選択**」をクリックします。

   1. 「」を選択します **セグメントのパス** as **conf** > **`We.Retail`** > **設定** > **wcm** > **セグメント** をクリックして、 **を選択**.

   1. 「**保存して閉じる**」をクリックします。

   >[!NOTE]
   >
   >ContextHub 設定とセグメントをそれぞれ最初に保存した、Context Hub とセグメントのパスを使用します。

   ![screen_shot_2019-05-01at44030pm](assets/screen_shot_2019-05-01at44030pm.png)

1. **DataDrivenAssets**／**チャネル**&#x200B;に移動して「**DataDrivenRetail**」を選択し、アクションバーの「**編集**」をクリックします。チャンネルエディターでアセットをドラッグ&amp;ドロップします。

   >[!NOTE]
   >
   >すべてが正しく設定されていれば、次のように表示されます **ターゲティング** エディターのドロップダウンの「」オプション（下図を参照）。

   ![screen_shot_2019-05-01at44231pm](assets/screen_shot_2019-05-01at44231pm.png)

1. 「**ターゲティング**」をクリック

1. 「**ブランド**」と「**アクティビティ**」のドロップダウンメニューから選択し、「**ターゲティングを開始**」をクリックします。

### 詳細情報：使用例 {#learn-more-example-use-cases}

AEM Screens プロジェクトに ContextHub を設定したら、以下の様々な使用例を通じて、データでトリガーされるアセットが様々な業界でいかに重要な役割を果たしているかを理解できます。

1. **[小売店向けの在庫に応じたアクティベーション](retail-inventory-activation.md)**
1. **[旅行センター向けの気温に応じたアクティベーション](local-temperature-activation.md)**
1. **[接客業向けの予約状況に応じたアクティベーション](hospitality-reservation-activation.md)**
