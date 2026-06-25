---
title: マルチゾーンからシングルゾーンへのトランジションの使用例
description: このページでは、マルチゾーンからシングルゾーンへのトランジションの使用例について説明します。
contentOwner: Jyotika Syal
feature: Authoring Screens
role: Developer, User
level: Intermediate
exl-id: 15632f31-1e92-40e5-b567-8705e27bdc93
TQID: https://experienceleague.adobe.com/MTRkmtP5J3PL13VZWm9nalthBX-03nu-Z2OsbnMO1Q4
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a5fd0e22-1a77-4f49-a6af-7a57fff19aed
subfeature_v2: id: f5973e90-a5a3-4b84-8602-ee120d4ce9b1
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
source-git-commit: d4664dd5678eaccabe656398c437dca264d4675e
workflow-type: tm+mt
source-wordcount: 467
ht-degree: 90%

---

# マルチゾーンからシングルゾーンへのトランジション {#multizone-to-singlezone-use-case}

## ユースケースの説明 {#use-case-description}

>[!IMPORTANT]
>このコンテンツは、AEM オンプレミス/AMS （AEM 6.5LTSおよびAEM 6.5）に対して有効です。 AEM as a Cloud Service Screensの内容については、[AEM as a Cloud Service ガイド ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)を参照してください。

ここでは、シングルゾーンレイアウトのチャネルに切り替わるマルチゾーンレイアウトのチャネルをセットアップする方法に重点を置いた使用例について説明します。 このマルチゾーンチャネルには一連の画像／ビデオアセットがあり、マルチゾーンとシングルゾーンの間で切り替わるプロジェクトをセットアップする方法を示しています。

### 前提条件 {#preconditions}

この使用例を開始する前に、以下の方法を理解しておく必要があります。

* **[チャネルの作成と管理](managing-channels.md)**
* **[ロケーションの作成と管理](managing-locations.md)**
* **[スケジュールの作成と管理](managing-schedules.md)**
* **[デバイスの登録](device-registration.md)**

### 主要なアクター {#primary-actors}

コンテンツ作成者

## プロジェクトのセットアップ {#setting-up-the-project}

次の手順に従って、プロジェクトをセットアップします。

1. **TakeoverLoop** という名前の AEM Screens プロジェクトを作成します（下図を参照）。

   ![アセット](assets/mz-to-sz1.png)


1. **マルチゾーン Screens チャネルの作成**

   1. **Channels** フォルダーを選択し、アクションバーの「**作成**」をクリックして、ウィザードを開き、チャネルを作成します。
   1. ウィザードで「**左 L バー型分割画面チャネル**」をクリックし、**MultiZoneLayout** というタイトルのチャネルを作成します。
   1. このチャネルにコンテンツを追加します。 各ゾーンにアセットをドラッグ＆ドロップします。 次の例は、ビデオ、画像、（埋め込みシーケンス内の）テキストバナーで構成される **MultiZoneLayout** チャネルを示しています（下図を参照）。

   ![アセット](assets/mz-to-sz2.png)

   >[!NOTE]
   >
   >チャネルでのマルチゾーンレイアウトの作成について詳しくは、[マルチゾーンレイアウト](multi-zone-layout-aem-screens.md)を参照してください。


1. **TakeoverChannel** というタイトルの別のチャネルを&#x200B;**チャネル**&#x200B;フォルダーに作成します。

   ![アセット](assets/mz-to-sz3.png)

1. アクションバーの「**編集**」をクリックすると、このチャネルにコンテンツを追加できます。 このチャネルに&#x200B;**チャネル**&#x200B;コンポーネントと切り替え先の画像アセットを追加します（下図を参照）。

   ![アセット](assets/mz-to-sz4.png)

1. チャネルコンポーネントの設定を開き、*手順 2* で作成した **MultiZoneLayout** チャネルを指すように設定します。

   ![アセット](assets/mz-to-sz5.png)

1. **シーケンス**&#x200B;フィールドのデュレーションを **10000 ミリ秒**&#x200B;に設定します。

   ![アセット](assets/mz-to-sz6.png)

1. 同様に、画像（追加したアセット）の設定を開き、「**シーケンス**」フィールドのデュレーションを **3000 ミリ秒**&#x200B;に設定します。

   ![アセット](assets/mz-to-sz7.png)

## プレビューを確認する {#checking-the-preview}

目的の出力は、プレーヤーで表示するか、エディターで「**プレビュー**」を選択して表示することができます。

出力は、マルチゾーンレイアウトが *10000 ミリ秒*&#x200B;間どのように再生されるかを示しています。 次に、再生時間が *3000 ミリ秒*&#x200B;の単一のゾーンレイアウトに切り替わります。 最後に、マルチゾーンレイアウトに戻ります。

>[!VIDEO](https://video.tv.adobe.com/v/30366)

>[!NOTE]
>
>（マルチゾーンレイアウトとシングルゾーンレイアウトの間の）チャネルトランジションは、必要に応じてカスタマイズできます。
