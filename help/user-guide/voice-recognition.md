---
title: AEM Screensでの音声認識
description: このページは、AEM Screensの音声認識機能を説明したものです。
translation-type: tm+mt
source-git-commit: 7f9f72f31d866f142bc9bf11d021583905ee82ea
workflow-type: tm+mt
source-wordcount: '1555'
ht-degree: 13%

---


# AEM Screensでの音声認識 {#voice-recognition}

>[!IMPORTANT]
>
>**プライバシーに関する重要な情報**
>
>音声認識機能を使用する場合は、地域に適用される法的および倫理的なガイドラインに従ってください（プレイヤーが音声認識を使用していることをエンドユーザーに対して表示する通知を含みますが、これに限定されません）。 Adobe Incは、音声関連情報を受け取らず、保存も処理もしません。 AEM Screensプレーヤーは、閲覧エンジンに組み込まれている標準的なWeb音声APIを使用します。 内部では、音声からテキストへの変換のためにGoogleサーバーに音声の波形が送信され、このテキストがプレイヤーによって設定されたキーワードと照合されます。
>
>詳しくは、 [Googleプライバシーに関するホワイトペーパー(Web Speech API](https://www.google.com/chrome/privacy/whitepaper.html#speech) )を参照してください。



音声認識機能を使用すると、音声操作によって駆動されるAEM Screensチャネルのコンテンツを変更できます。

コンテンツ作成者は、ディスプレイを音声対応に設定できます。 この機能の目的は、お客様がディスプレイと対話する方法として音声を利用できるようにすることです。 同様の使用例としては、店舗で商品のレコメンデーションを探す、ディナーやレストランでメニューアイテムを注文するなどがあります。 この機能により、ユーザーのアクセシビリティが向上し、顧客体験を大幅に向上させることができます。

>[!NOTE]
>プレイヤーハードウェアは、マイクなどの音声入力をサポートする必要があります。

## 音声認識の実装 {#implementing}

>[!IMPORTANT]
> 音声認識機能は、Chrome OSおよび電子プレーヤーでのみ使用できます。

AEM Screensプロジェクトで音声認識を実装するには、ディスプレイの音声認識を有効にし、各チャネルを固有のタグに関連付けて、チャネルトランジションをトリガする必要があります。

次の節では、AEM Screensプロジェクトで音声認識機能を有効にして使用する方法について説明します。

プロジェクトは、次の2つのテンプレートのいずれかを使用して設定できます。

* [シーケンスチャネル](#sequence-channel)
* [画面を分割チャネル](#split-channel)

## シーケンスチャネルをテンプレートとして使用 {#sequence-channel}

音声認識機能を使用する前に、プロジェクトと、コンテンツが設定されたチャネルがプロジェクトにあることを確認してください。

1. 次の例では、VoiceDemo **という名前のデモプロジェクトと、** Main **、** ColdDrinks **、HotDrinksの3つのシーケンスチャネルーを示しています。次の図はHotDrinksで******&#x200B;す。

   ![image](assets/voice-recognition/vr-1.png)

   >[!NOTE]
   >
   >チャネルを作成する方法、またはチャネルにコンテンツを追加する方法については、[チャネルの作成と管理](/help/user-guide/managing-channels.md)を参照してください。

1. 各チャネルに移動し、コンテンツを追加します。 例えば、 **VoiceDemo** —> **チャネル** —> **Main** に移動し、チャネルを選択します。 アクションバーの「 **編集** 」をクリックしてエディターを開き、必要に応じてコンテンツ（画像/ビデオ）を追加します。 同様に、ColdDrinks **チャネルーとHotDrinks****** ーの両方にコンテンツを追加します。

   次の図に示すように、チャネルにはアセット（画像）が含まれるようになりました。

   **メイン**:

   ![image](assets/voice-recognition/vr-4.png)

   **ColdDrinks**:

   ![image](assets/voice-recognition/vr-3.png)

   **HotDrinks**:

   ![image](assets/voice-recognition/vr-2.png)


### Setting up Tags for Channels {#setting-tags}

チャネルにコンテンツを追加したら、各チャネルに移動し、音声認識をトリガーする適切なタグを追加する必要があります。

次の手順に従って、チャネルにタグを追加します。

1. 各チャネルに移動し、コンテンツを追加します。 例えば、 **VoiceDemo** —> **チャネル** —> **Main** に移動し、チャネルを選択します。

1. アクションバーの「**プロパティ**」をクリックします。

   ![image](assets/voice-recognition/vr-5.png)

1. 「 **Basics** 」タブに移動し、「 **Tags** （タグ）」フィールドから既存のタグを選択するか、新しいタグを作成します。

   次の図に示すように、新しいタグ名とヒット `return` キーを入力して、新しいタグを作成できます。

   ![image](assets/voice-recognition/vr-6.png)

   または、

   事前にAEMインスタンスからプロジェクト用のタグを作成し、それらも選択できます。 「タグの [作成](#creating-tags)」で説明されている手順に従うと、次の図に示すように、場所からタグを選択し、チャネルに追加できます。

   ![image](assets/voice-recognition/vr-tag1.png)

1. 同様に、「 **hot** 」というタグをHotDrinks **** チャネルに追加します。

1. 完了したら、「 **保存して閉じる** 」をクリックします。


### タグの作成 {#creating-tags}

次の手順に従ってタグを作成します。

1. AEMインスタンスに移動します。

1. ツール/ **タグ付けをクリックします**。
   ![image](assets/voice-recognition/vr-7.png)

1. Click **Create** --> **Create Namespace**.
   ![image](assets/voice-recognition/vr-tag3.png)

1. プロジェクトの名前(例： **VoiceDemo** )を入力し、「 **作成**」をクリックします。
   ![image](assets/voice-recognition/vr-tag2.png)

1. Select the **VoiceDemo** project and click **Create Tag** from the action bar.
   ![image](assets/voice-recognition/vr-tag4.png)

1. タグの名前を入力し、「 **送信**」をクリックします。
   ![image](assets/voice-recognition/vr-tag5.png)

これらのタグをAEM Screensプロジェクトで使用できます。

### ディスプレイにチャネルを割り当て、音声認識を有効にする {#channel-assignment}

1. 下の図に示すように、**ロケーション**&#x200B;フォルダーにディスプレイを作成します。

   ![image](assets/voice-recognition/vr-loc.png)

   >[!NOTE]
   >ディスプレイにチャネルを割り当てる方法については、[ディスプレイの作成と管理](/help/user-guide/managing-displays.md)を参照してください。

1. チャネル **Main**、 **ColdDrinks**、HotDrinksをLobbyDisplay ******** dirknsに割り当てます。

1. チャネルを割り当てる際に、各チャネルに次のプロパティを設定します。

   | **チャネル名** | **優先度** | **サポートされているイベント** |
   |---|---|---|
   | メイン | 2 | 初期読み込み、アイドル画面、タイマー |
   | ホットドリンク | 1 | ユーザーインタラクション |
   | ColdDrinks | 1 | ユーザーインタラクション |

   >[!NOTE]
   >
   >ディスプレイにチャネルを割り当てる方法については、[ディスプレイの作成と管理](/help/user-guide/managing-displays.md)を参照してください。

1. ディスプレイにチャネルを割り当てたら、LobbyDisplayに移動し **て** 、ディスプレイを選択します。 アクションバーから「**プロパティ**」を選択します。

1. 「 **表示** 」タブに移動し、「 **コンテンツ** 」の「音声対応 ****」オプションを有効にします。

   ![image](assets/voice-recognition/vr-disp.png)

   >[!IMPORTANT]
   >ディスプレイから音声認識機能を有効にする必要があります。

### Chrome Playerでのコンテンツの表示 {#viewing-content}

上記の手順が完了したら、Chromeデバイスを登録して出力を表示できます。

>[!NOTE]
>デバイスを [AEM Screensプレイヤに登録する方法については、Device Registration](device-registration.md) （デバイス登録）を参照してください。

この例は、Chrome Playerの出力を示します。

Main **チャネルはコンテンツを再生していますが、キーワードに「** hot」と付けた単語を使用し **て、例えば「hot drink** 」と入力したい場合は、チャネル開始が「hotDrinks」チャネルを再生している ****** を再生しています。

同様に、キーワード **cold** （冷たいものを持たせたいと思う）のように単語をキーワードと共に使うと *、チャネル開始が* ColdDrinks **** チャネルの内容を再生します。

![newimage](assets/voice-recognition/voice-video.gif)


## 画面を分割チャネルをテンプレートとして使用する {#split-channel}

音声認識機能を使用する前に、プロジェクトと、コンテンツが設定されたチャネルがプロジェクトにあることを確認してください。

1. 次の例は、VoiceDemo **という名前のデモプロジェクトと、** Main **Dorkntsという3つのシーケンスチャネルを持つHotDrinksという名前のデモプロジェクトを示しています。HotDrinksは、次の図に示すColdSplitと** ScreenSplitは、Splitは1 ************ Splとし、Splitは1xScreenSplitは、Splitは、Vは、VVは、Vは、Vは、VeVはVはVitは、Vは、VitはVidはVVoVitはVidはVidはVVoVoVitはVinはVeVeVoVoVoVoVoVo

   ![image](assets/voice-recognition/vr-emb-1.png)

   >[!NOTE]
   >
   >チャネルを作成する方法、またはチャネルにコンテンツを追加する方法については、[チャネルの作成と管理](/help/user-guide/managing-channels.md)を参照してください。

1. 各チャネルに移動し、コンテンツを追加します。 例えば、 **VoiceDemo** —> **チャネル** —> **Main** に移動し、チャネルを選択します。 アクションバーの「 **編集** 」をクリックしてエディターを開き、必要に応じてコンテンツ（画像/ビデオ）を追加します。 同様に、ColdDrinks **チャネルーとHotDrinks****** ーの両方にコンテンツを追加します。

   次の図に示すように、チャネルにはアセット（画像）が含まれるようになりました。

   **メイン**:

   ![image](assets/voice-recognition/vr-emb-3.png)


   **ColdDrinks**:
   ![image](assets/voice-recognition/vr-3.png)

   **HotDrinks**:

   ![image](assets/voice-recognition/vr-2.png)

1. SplitScreenに移動し **て** 、2つの埋め込みシーケンスをドラッグ&amp;ドロップし、次の図に示すように、 **ColdDrinks** チャネルとHotDrinks **** の両方にパスを追加します。
   ![image](assets/voice-recognition/vr-emb-6.png)


### Setting up Tags for Channels {#setting-tags-split}

チャネルにコンテンツを追加したら、各チャネルに移動し、音声認識をトリガーする適切なタグを追加する必要があります。

次の手順に従って、チャネルにタグを追加します。

1. 各チャネルに移動し、コンテンツを追加します。 例えば、 **VoiceDemo** —> **チャネル** —> **Main** に移動し、チャネルを選択します。

1. アクションバーの「**プロパティ**」をクリックします。

   ![image](assets/voice-recognition/vr-5.png)

1. 「 **Basics** 」タブに移動し、「 **Tags** （タグ）」フィールドから既存のタグを選択するか、新しいタグを作成します。

   次の図に示すように、新しいタグ名とヒット `return` キーを入力して、新しいタグを作成できます。

   ![image](assets/voice-recognition/vr-6.png)

   または、

   事前にAEMインスタンスからプロジェクト用のタグを作成し、それらも選択できます。 「タグの [作成](#creating-tags)」で説明されている手順に従うと、次の図に示すように、場所からタグを選択し、チャネルに追加できます。

   ![image](assets/voice-recognition/vr-tag1.png)

1. 同様に、「 **hot** 」というタグをHotDrinks **** チャネルに追加します。

1. SplitScreen **** チャネルプロパティのタグ( **hot**&#x200B;と **cold** )は両方とも、

   ![image](assets/voice-recognition/vr-emb-7.png)


1. 完了したら、「 **保存して閉じる** 」をクリックします。

### ディスプレイにチャネルを割り当て、音声認識を有効にする {#channel-assignment-split}

1. 下の図に示すように、**ロケーション**&#x200B;フォルダーにディスプレイを作成します。

   ![image](assets/voice-recognition/vr-loc.png)

   >[!NOTE]
   >ディスプレイにチャネルを割り当てる方法については、[ディスプレイの作成と管理](/help/user-guide/managing-displays.md)を参照してください。

1. チャネル **Main**、ColdDrinks **、HotDrinks****、HotDrinks**、SplitScreenScreenSplitScreen ******** をLobby Displayに割り当てます。

1. チャネルを割り当てる際に、各チャネルに次のプロパティを設定します。

   | **チャネル名** | **優先度** | **サポートされているイベント** |
   |---|---|---|
   | メイン | 2 | 初期読み込み、アイドル画面、タイマー |
   | ホットドリンク | 1 | ユーザーインタラクション |
   | ColdDrinks | 1 | ユーザーインタラクション |
   | SplitScreen | 1 | ユーザーインタラクション |

   >[!NOTE]
   >
   >ディスプレイにチャネルを割り当てる方法については、[ディスプレイの作成と管理](/help/user-guide/managing-displays.md)を参照してください。

1. ディスプレイにチャネルを割り当てたら、 **ロビー** ・ディスプレイに移動し、ディスプレイを選択します。 アクションバーから「**プロパティ**」を選択します。

1. 「 **表示** 」タブに移動し、「 **コンテンツ** 」の「音声対応 ****」オプションを有効にします。

   ![image](assets/voice-recognition/vr-disp.png)

   >[!IMPORTANT]
   >ディスプレイから音声認識機能を有効にする必要があります。


### Chrome Playerでのコンテンツの表示 {#viewing-content-split}

上記の手順が完了したら、Chromeデバイスを登録して出力を表示できます。

>[!NOTE]
>デバイスを [AEM Screensプレイヤに登録する方法については、Device Registration](device-registration.md) （デバイス登録）を参照してください。

この例は、Chrome Playerの出力を示します。

チャネル **Main** チャネルはコンテンツを再生していますが、キーワードhotとhot **を含む単語を使う場合は、例えば** hotとhotと ********** hotを組み合わせて使う場合は、cold werdsのメニューを見たいと思います。cold werdの開始はScreenチャネルのスプリットの内容です。








