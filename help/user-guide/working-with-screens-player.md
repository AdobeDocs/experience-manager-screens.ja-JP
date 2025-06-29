---
title: AEM Screens Player の操作
description: AEM Screens Player、管理 UI およびチャネルスイッチャーでの操作について説明します。
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 4faac090-ad8a-4d7e-a502-6fb63f6b2761
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '1067'
ht-degree: 97%

---

# AEM Screens Player の操作

AEM Screens Player でチャネルコンテンツなどの設定を管理できます。

>[!NOTE]
>
>***Ctrl+Cmd+F*** を押すと、OS X AEM Screens Player のフルスクリーンモードを終了できます。

ディスプレイにチャネルを割り当てると、AEM Screens Player にコンテンツが表示されます。管理 UI の環境設定を使用して（ダッシュボードから）、またはプレーヤー自体から、プレーヤーの設定を行えます。

## デバイスダッシュボードの使用 {#using-the-device-dashboard}

AEM オーサリングインスタンスを介してアクセスできる、デバイスダッシュボードからデバイスの環境設定を設定できます。

1. プロジェクトからデバイスダッシュボードに移動します（例：***テストプロジェクト***／***デバイス***）。

   アクションバーの「**デバイス**」および「**デバイスマネージャー**」をクリックします。

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. デバイスをクリックして、デバイスのダッシュボードを開きます。

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. **環境設定**&#x200B;パネルを確認します。オプションからプレーヤーの「**管理 UI**」と「**チャネルスイッチャー**」の有効／無効を切り替えることができます。

   ![chlimage_1-68](assets/chlimage_1-68.png)

### 管理 UI {#the-admin-ui}

環境設定パネルから「**管理 UI**」を有効にすると、ユーザーは Screens Player から管理者設定を開くことができます。さらに、このオプションをデバイスダッシュボードから無効にすると、ユーザーはプレーヤーから管理 UI を開くことができなくなります。

Screens Player から管理 UI を表示するには、タッチ操作対応の AEM Screens Player またはマウスで左上隅を長押しして、管理メニューを開きます。登録が完了し、チャネルが読み込まれると、情報が表示されます。

>[!NOTE]
>
>また、AEM Screens Player アプリのアップタイムを表示して、アプリの正常性ステータスをチェックできます。

![chlimage_1-3](assets/chlimage_1-3.gif)

#### 設定メニューオプションへのアクセス {#configuration-options}

次の図に示すように、サイドメニューの「**設定**」オプションをクリックすると、設定を更新できます。

![screen_shot_2018-10-15at101257am](assets/screen_shot_2018-10-15at101257am.png)

設定メニューでは、次の設定を変更できます。

* このダイアログボックスから、**ファームウェア**、**環境設定**、または&#x200B;**ファクトリー設定**&#x200B;をリセットします。

* AEM Screens Player に対して保持するログファイルの最大数を、「**保持するログファイルの最大数**」で指定します。

* Screens Player の&#x200B;**管理者メニュー**、**チャネルスイッチャー**、**アクティビティ UI** を有効または無効にします。

  **設定**&#x200B;メニューで&#x200B;**アクティビティ UI** が有効になっている場合、次の図に示すように、AEM Screens Player の右上隅に&#x200B;*プレーヤーアクティビティ通知*&#x200B;が表示されます。

  ![画像](/help/user-guide/assets/activity_ui.png)

>[!NOTE]
>
>「**ファームウェアを更新**」オプションは、Android™ プレーヤーなどの Cordova でのみ機能します。

>[!NOTE]
>
>実稼動デプロイメントでは&#x200B;**管理 UI** を無効にすることをお勧めします。

#### コンテンツキャッシュメニューオプションへのアクセス {#content-cache-options}

AEM Screens Player の管理 UI から、チャネルとアプリケーションのキャッシュをクリアできます。

サイドパネルの「**コンテンツキャッシュ**」をクリックして、キャッシュを更新できるようにします。

![screen_shot_2018-10-15at105717am](assets/screen_shot_2018-10-15at105717am.png)

### チャネルスイッチャー {#the-channel-switcher}

環境設定パネルの「**チャネルスイッチャー**」を有効にすると、Screens Player からチャネル選択設定を開くことができます。

また、このオプションをデバイスダッシュボードから無効にすると、ユーザーは Screens Player からチャネル環境設定を制御できなくなります。

Screens Player からチャネルの設定を切り替えて制御できます。

プレーヤーからチャネルスイッチャーを表示するには、左下隅を長押ししてチャネルスイッチャーを開き、チャネルやその他の機能を切り替えます。

![chlimage_1-69](assets/chlimage_1-69.png)

>[!NOTE]
>
>また、Screens Player から、プレーヤーの管理メニューとチャネルスイッチャーを有効にしたり、無効にしたりすることもできます。
>
>（以下の節で言及されている、*Screens Player からの環境設定を変更*&#x200B;を参照してください）。

### AEM Screens Player からの環境設定の管理

プレーヤー自体からも Admin UI およびチャネルスイッチャーの設定を変更できます。

プレーヤーから環境設定を変更するには、以下を実行します。

1. アイドル状態のチャネルの左上隅を長押しして、管理パネルを開きます。
1. 左のアクションメニューから&#x200B;**設定**&#x200B;に移動します。
1. **Admin UI** または&#x200B;**チャネルスイッチャー**&#x200B;の設定の有効／無効を切り替えます。

![screen_shot_2018-10-15at101257am-1](assets/screen_shot_2018-10-15at101257am-1.png)

## AEM Screens Player のトラブルシューティング

AEM Screens Player に関係する様々な問題をトラブルシューティングすることができます。

| **問題** | **レコメンデーション** |
|---|---|
| プレーヤーのストレージがいっぱいです | 不要なファイルを削除してください |
| プレーヤーのネットワーク接続が途切れました | Cat-5 または Cat-6 ケーブルを使用してください。Wi-Fi の場合は、ルーターからプレーヤーデバイスまでの距離を短くしてください |
| AEM Screens Player がクラッシュしました | AEM Screens Player が常時動作しているようにウォッチドッグアプリを使用することをお勧めします |
| AEM Screens Player の設定がなくなりました | AEM サーバーへの接続を確認してください |
| AEM Screens Player が再起動後に自動起動しません | OS のスタートフォルダーまたは初期化手順を確認してください |
| AEM Screens Player のコンテンツ表示が間違っていたり古かったりします | ネットワーク接続を確認してください |

### AEM Screens Player のアップデート

AEM Screens Player には、次の 2 とおりの更新方法があります。

| **方法** | **詳細** | **リモート経由** | **自動** | **ダウンタイムなし** |
|---|---|---|---|---|
| ファームウェアの更新 | リモートコマンドを使用して、既存のインストール済みプレーヤーに適用されます。更新後、プレーヤーは既存のコンテンツで自動的にリロードされます。 | はい | カスタム | ほぼ 1～3 秒 |
| プレーヤーシェルの更新 | プレーヤーにデプロイされる新しい実行可能ファイル。この機能を使用するには、プレーヤーに新しいバイナリをリモートコピーし、現在実行中のバイナリを停止して、新しいバージョンを起動する必要があります。パッケージのプリロードを再度ダウンロードする必要が生じる場合があります。 | 可（リモートシェル経由） | カスタム | いいえ |

## プレーヤーデバイスのハードウェア選定ガイドライン {#hardware-selection-guidelines-for-player-device}

この節では、Screens プロジェクトのハードウェア選定ガイドラインを示します。

* PC プレーヤーにもディスプレイパネルまたはプロジェクターにも、常に&#x200B;***商用***&#x200B;または&#x200B;***工業用***&#x200B;クラスのコンポーネントを調達します。

* デジタルサイネージマーケットに商品を提供しているベンダーと常に連携します。
* 周囲温度や相対湿度などの環境要因を常に考慮してください。
* 電源要件と電力調整を常に確認します。
* パフォーマンスのニーズとアプリケーションに必要な I/O ポートを慎重に確認します。

AEM Screens プロジェクトの典型的な使用例に対応するハードウェア構成を次の表にまとめます。

<table>
 <tbody>
  <tr>
   <td>プレーヤー設定</td>
   <td>プロセッサー</td>
   <td>メモリ</td>
   <td>ストレージ SSD</td>
   <td>GPU</td>
   <td>ディスプレイ</td>
   <td>I/O</td>
   <td>典型的な使用例</td>
  </tr>
  <tr>
   <td>基本</td>
   <td>デュアルコア、i3 またはエントリーレベルのクアッドコア Intel® Atom プロセッサー</td>
   <td><p>4 GB のメモリ</p> <p>2 MB のキャッシュ</p> </td>
   <td><p>*ChromeOS 32 GB</p> <p>*Windows 128 GB</p> </td>
   <td>オンボード</td>
   <td>1920 x 1080</td>
   <td>DVI <br />イーサネット／ワイヤレス<br /> USB x 2</td>
   <td>
    <ul>
     <li>標準フルスクリーンループ<br /> </li>
     <li>日分割</li>
    </ul> </td>
  </tr>
  <tr>
   <td>標準</td>
   <td>クアッドコア、Intel® Core™ i5 プロセッサー</td>
   <td><p>8 GB のメモリ</p> <p>4 MB のキャッシュ</p> </td>
   <td>128 GB</td>
   <td>オンボード</td>
   <td>3840x2160（<code>4K</code>）</td>
   <td>DVI、HDMI<br /> イーサネット／ワイヤレス、<br />USB x 2</td>
   <td>
    <ul>
     <li>単一ソースの動的コンテンツ</li>
     <li>シンプルインタラクティブ</li>
     <li>1～3 ゾーンレイアウト</li>
    </ul> </td>
  </tr>
  <tr>
   <td>アドバンス</td>
   <td>ハイパースレッディング対応クアッドコア、Intel® Core™ i7 プロセッサー</td>
   <td><p>16 GB のメモリ</p> <p>8 MB のキャッシュ</p> </td>
   <td>256 GB</td>
   <td>専用グラフィック GPU</td>
   <td>3840x2160（<code>4K</code>）</td>
   <td>DVI、HDMI<br /> イーサネット／ワイヤレス、<br />USB x 4</td>
   <td>
    <ul>
     <li>4 つ以上のコンテンツゾーン、同時ビデオ再生</li>
     <li>複数ページインタラクティブ</li>
     <li>複数ソースデータトリガー</li>
    </ul> </td>
  </tr>
 </tbody>
</table>
