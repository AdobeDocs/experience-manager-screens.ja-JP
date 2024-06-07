---
title: 緊急チャネル
description: 前提条件がある場合にコンテンツ作成者がシーケンスチャネルから切り替えることができる緊急チャネルの作成と管理について説明します。
content-type: example
topic-tags: use-case-examples
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: d409ba46-b48a-44db-b305-27c392cd55de
source-git-commit: 1cf90de7892d051b2b94b4dd57de7135269b1ee8
workflow-type: ht
source-wordcount: '712'
ht-degree: 100%

---

# 緊急チャネル {#emergency-channel}

## ユースケースの説明 {#use-case-description}

この節ではユースケースの例について説明します。前提条件がある場合にコンテンツ作成者がシーケンスチャネルから切り替えることができる、緊急チャネルの作成と管理について重点的に説明します。

### 前提条件 {#preconditions}

この使用例を開始する前に、以下の方法を理解しておく必要があります。

* **[チャネルの作成と管理](managing-channels.md)**
* **[ロケーションの作成と管理](managing-locations.md)**
* **[スケジュールの作成と管理](managing-schedules.md)**
* **[デバイスの登録](device-registration.md)**

### 主要なアクター {#primary-actors}

コンテンツ作成者

## 基本フロー：プロジェクトのセットアップ {#basic-flow-setting-up-the-project}

緊急チャネルをセットアップするには、以下の手順に従います。

1. **EmergencyChannel** という名前の AEM Screens プロジェクトを作成します（下図を参照）。

   >[!NOTE]
   >AEM Screens でのプロジェクトの作成と管理について詳しくは、プロジェクトの作成を参照してください。

   ![screen_shot_2019-02-21at35809pm](assets/screen_shot_2019-02-21at35809pm.png)

1. **シーケンスチャネルを作成する**

   1. **Channels** フォルダーをクリックし、「**作成**」をクリックします。

   1. ウィザードで「**シーケンスチャネル**」をクリックし、**MainAdChannel** というタイトルのチャネルを作成します。

   ![screen_shot_2019-02-21at35932pm](assets/screen_shot_2019-02-21at35932pm.png)

1. **シーケンスチャネルにコンテンツを追加する**

   1. チャネル（**MainAdChannel**）をクリックします。
   1. アクションバーの「**編集**」をクリックします。
   1. チャネルにいくつかのアセットをドラッグ＆ドロップします。

   ![screen_shot_2019-02-21at40053pm](assets/screen_shot_2019-02-21at40053pm.png)

1. **緊急チャネルを作成する**

   1. **Channels** フォルダーをクリックします。
   1. 「**作成**」をクリックします。
   1. ウィザードで「**シーケンスチャネル**」をクリックし、**EmergencyChannel** というタイトルのチャネルを作成します。

   >[!NOTE]
   >
   >通常、緊急チャネルは既存の実稼動プロジェクトに追加されます。

   ![screen_shot_2019-02-21at40151pm](assets/screen_shot_2019-02-21at40151pm.png)

1. **緊急チャネルにコンテンツを追加する**

   1. チャネル（**Emergency Channel**）をクリックします。
   1. アクションバーの「**編集**」をクリックします。
   1. 緊急時に実行するアセットをチャネルにドラッグ＆ドロップします。

   ![screen_shot_2019-02-21at40516pm](assets/screen_shot_2019-02-21at40516pm.png)

1. **ロケーションの作成**

   1. **Locations** フォルダーに移動します。
   1. アクションバーの「**作成**」をクリックし、ウィザードから **Store** というタイトルのロケーションを作成します。

   ![screen_shot_2019-02-22at121638pm](assets/screen_shot_2019-02-22at121638pm.png)

1. **ロケーションにディスプレイを作成する**

   ロケーション（**Store**）に移動し、アクションバーの「**作成**」をクリックします。ウィザードに従って、**StoreFront** および **StoreRear** というタイトルの 2 つの&#x200B;**ディスプレイ**&#x200B;を作成します。

   ![screen_shot_2019-02-22at122556pm](assets/screen_shot_2019-02-22at122556pm.png)

1. **スケジュールの作成**

   1. **スケジュール**&#x200B;フォルダーに移動します。
   1. アクションバーの「**作成**」をクリックします。
   1. ウィザードに従って、**StoreSchedule** というタイトルのスケジュールを作成します。

   ![screen_shot_2019-02-22at122845pm](assets/screen_shot_2019-02-22at122845pm.png)

1. スケジュールに両方のディスプレイを割り当て優先度を設定する

   1. スケジュール（**StoreSchedule**）をクリックし、アクションバーの「**ダッシュボード**」をクリックします。

   1. **割り当てられたチャネル**&#x200B;パネルで「**+ チャネルを割り当て**」をクリックします。

   1. **チャネル割り当て**&#x200B;ダイアログボックスで、次の操作を行います。

      1. **MainAdChannel** へのパスをクリックします。
      1. 「**優先度**」を「2」に設定します。
      1. 「サポートされているイベント」として「**最初の読み込み**」および「**待機中画面**」を設定します。
      1. 「**保存**」をクリックします。

      同様に、同じ手順に従って **EmergencyChannel** を割り当て、その「**優先度**」を設定します。

   >[!NOTE]
   >
   >優先度は、複数の割り当てが再生条件に一致する場合に、割り当ての順序付けを行うために使用します。最も高い値のものが低い値よりも常に優先されます。

   ![screen_shot_2019-03-04at104636am](assets/screen_shot_2019-03-04at104636am.png)

1. **割り当てられたチャネル**&#x200B;パネルで「**+ チャネルを割り当て**」をクリックします。

1. **チャネル割り当て**&#x200B;ダイアログボックスで、次の操作を行います。

   1. **EmergencyChannel** へのパスをクリックします。
   1. 「**優先度**」を「1」に設定します。

   1. 「サポートされているイベント」として、「**最初の読み込み**」、「**待機中画面**」、「**ユーザーインタラクション**」を設定します。

   1. 「**保存**」をクリックします。

   ![screen_shot_2019-03-04at104741am](assets/screen_shot_2019-03-04at104741am.png)

   割り当てられたチャネルを **StoreSchedule** のダッシュボードで確認できます。

   ![screen_shot_2019-02-25at93658pm](assets/screen_shot_2019-02-25at93658pm.png)

1. **各ディスプレイへのスケジュールの割り当て**

   1. 各ディスプレイに移動します（**EmergencyChannel**／**Locations**／**Store**／**StoreFront** など）。

   1. アクションバーで「**ダッシュボード**」をクリックします。
   1. **割り当てられたチャネルとスケジュール**&#x200B;パネルで「**...**」をクリックし、さらに「**+ スケジュールを割り当て**」をクリックします。

   1. スケジュールのパスをクリックします（例：**EmergencyChannel**／**Schedules**／**StoreSchedule**）。

   1. 「**保存**」をクリックします。

   ディスプレイに割り当てられたスケジュールを **StoreSchedule** のダッシュボードで確認できます。
   ![screen_shot_2019-03-04at122003pm](assets/screen_shot_2019-03-04at122003pm.png)

1. **デバイスの登録**

   デバイスの登録プロセスを完了します。登録すると、AEM Screens Player で次の出力が表示されます。

   ![new30](assets/new30.gif)

## 緊急チャネルへの切り替え {#switching-to-emergency-channel}

緊急事態が発生した場合は、次の手順に従います。

1. **EmergencyChannel**／**Schedules**／**StoreSchedule** に移動し、アクションバーの「**ダッシュボード**」をクリックします。

   ![screen_shot_2019-02-25at101112pm](assets/screen_shot_2019-02-25at101112pm.png)

1. **StoreSchedule** のダッシュボードで **EmergencyChannel** をクリックし、「**割り当てを編集**」をクリックします。

   ![screen_shot_2019-02-25at101239pm](assets/screen_shot_2019-02-25at101239pm.png)

1. **チャネル割り当て**&#x200B;ダイアログボックスで、**EmergencyChannel** の「**優先度**」を「**3**」に更新し、「**保存**」をクリックします。

   ![screen_shot_2019-02-25at101622pm](assets/screen_shot_2019-02-25at101622pm.png)

1. チャネルの優先度が更新されると、すべてのAEM Screens Player に **EmergencyChannel** のコンテンツが表示されます。

   ![screen_shot_2019-02-25at101742pm](assets/screen_shot_2019-02-25at101742pm.png)

### まとめ {#conclusion}

コンテンツ作成者が優先度の値を 1 にリセットするまで、引き続き **EmergencyChannel** のコンテンツが表示されます。

コンテンツ作成者は、緊急事態が解除されたという通知を受け取ったら、**MainAdChannel** の優先度を更新する必要があります。その結果、通常の再生が再開されます。
