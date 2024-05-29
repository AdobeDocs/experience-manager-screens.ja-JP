---
title: 小売店向けの在庫に応じたアクティベーション
description: 3 種類のカラーのスウェットシャツの小売在庫在庫を表示する、この AEM Screens のユースケースについて説明します。
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: use-case-examples
docset: aem65
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 926f529b-f3cf-471d-83b4-6ccb628cf160
source-git-commit: ce8340f24d116b4268a6ed15dd4e9f626bad1ef6
workflow-type: ht
source-wordcount: '577'
ht-degree: 100%

---

# 小売店向けの在庫に応じたアクティベーション {#retail-inventory-targeted-activation}

次の使用例では、Google シートの値に応じた 3 種類の画像の表示方法を示しています。

## 説明 {#description}

このユースケースは、3 種類のカラートレーナーの小売在庫を表示します。Google シートに記録されているトレーナーの在庫数に応じて、最も数が多いトレーナー（赤、緑、青のいずれか）の画像が表示されます。

購入可能なセーターの最大数に基づいて、赤、緑、青のセーターが表示されます。

## 前提条件 {#preconditions}

小売店向けの在庫に応じたアクティベーションの実装を開始する前に、AEM Screens プロジェクトで&#x200B;***データストア***、***オーディエンスのセグメント化***&#x200B;のセットアップおよび&#x200B;***チャネルのターゲティングの有効化***&#x200B;を行う方法を理解しておきます。

詳しくは、[AEM Screens での ContextHub の設定](configuring-context-hub.md)を参照してください。

## 基本フロー {#basic-flow}

「小売店向けの在庫に応じたアクティベーション」の使用例を実装するには、以下の手順に従います。

1. **Google シートにデータを入力する**

   1. ContextHubDemo Google シートに移動します。
   1. 3 種類のトレーナーに対応する値を格納する 3 つの列（Red、Green、Blue）を追加します。

   ![screen_shot_2019-05-06at101755am](assets/screen_shot_2019-05-06at101755am.png)

1. **要件に従ってオーディエンスを設定する**

   1. オーディエンスのセグメントに移動します（詳しくは、**[AEM Screens での ContextHub の設定](configuring-context-hub.md)**&#x200B;ページの&#x200B;***手順 2：オーディエンスのセグメント化の設定***&#x200B;を参照してください）。

   1. 3 つの新しいセグメント **For_Red**、**For_Green**、**For_Blue** を追加します。

   1. 「**For_Red**」をクリックし、アクションバーの「**編集**」をクリックします。

   1. **比較：プロパティ - プロパティ**&#x200B;コンポーネントをエディターにドラッグ＆ドロップします。
   1. **設定**&#x200B;アイコンをクリックします。
   1. **1 番目のプロパティ名**&#x200B;のドロップダウンから **googlesheets/value/1/2** をクリックします。
   1. **演算子**&#x200B;のドロップダウンメニューから「**次よりも大きい**」をクリックします。
   1. 「**データタイプ**」として「**数値**」をクリックします。
   1. **2 番目のプロパティ名**&#x200B;のドロップダウンから **googlesheets/value/1/1** をクリックします。
   1. **別の比較：プロパティ - プロパティ**&#x200B;をエディターにドラッグ＆ドロップし、**設定**&#x200B;アイコンをクリックします。
   1. **1 番目のプロパティ名**&#x200B;のドロップダウンから **googlesheets/value/1/2** をクリックします。
   1. **演算子**&#x200B;のドロップダウンメニューから「**次よりも大きい**」をクリックします。
   1. 「**データタイプ**」として「**数値**」をクリックします。
   1. **2 番目のプロパティ名**&#x200B;のドロップダウンから **googlesheets/value/1/0** をクリックします。

   ![screen_shot_2019-05-06at102600am](assets/screen_shot_2019-05-06at102600am.png)

   同様に、**For_Blue** セグメントにプロパティ比較ルールを追加し編集します（下図を参照）。

   ![screen_shot_2019-05-06at103728am](assets/screen_shot_2019-05-06at103728am.png)

   同様に、**For_Green** セグメントにプロパティ比較ルールを追加し編集します（下図を参照）。

   ![screen_shot_2019-05-06at103418am](assets/screen_shot_2019-05-06at103418am.png)

   >[!NOTE]
   >
   >Google シートの値どおり、現時点では最初の比較のみ有効なので、セグメント **For_Blue** および **For_Green** については、データをエディターで解決できません。

1. **DataDrivenRetail** チャネル（シーケンスチャネル）に移動してクリックします。
1. アクションバーの「**編集**」をクリックします。

   ![screen_shot_2019-05-06at104257am](assets/screen_shot_2019-05-06at104257am.png)

   >[!CAUTION]
   >
   >チャネルの&#x200B;**プロパティ**／**パーソナライズ機能**&#x200B;タブを使用して&#x200B;**ContextHub** **設定**&#x200B;をセットアップしておいてください。

   ![screen_shot_2019-05-06at105214am](assets/screen_shot_2019-05-06at105214am.png)

   >[!NOTE]
   >
   >ターゲティングプロセスを開始したときにアクティビティが正しく一覧表示されるように、「**ブランド**」と「**領域**」の両方をクリックします。

1. **デフォルト画像を追加する**

   1. チャネルにデフォルト画像を追加し、「**ターゲティング**」をクリックします。
   1. 「**ブランド**」と「**アクティビティ**」のドロップダウンメニューからクリックし、「**ターゲット設定を開始**」をクリックします。
   1. 「**ターゲティングを開始**」をクリックします。

   ![screen_shot_2019-05-06at121253pm](assets/screen_shot_2019-05-06at121253pm.png)

   >[!NOTE]
   >
   >ターゲティングを開始する前に、サイドレールの「**+ エクスペリエンスのターゲットを追加**」をクリックして、セグメント（**For_Green**、**For_Red**、**For_Blue**）を追加します（下図を参照）。

   ![screen_shot_2019-05-06at123554pm](assets/screen_shot_2019-05-06at123554pm.png)

1. 以下に示すように、3 つの異なるシナリオすべてに画像を追加します。

   ![retail_targeting](assets/retail_targeting.gif)

1. **プレビューを確認する**

   1. 「**プレビュー**」をクリックします。また、Google シートを開き、値を更新します。
   1. 3 つの異なる列すべての値を変更します。インベントリ内の最大値に応じてディスプレイの画像が更新されます。

   ![retail_result](assets/retail_result.gif)
