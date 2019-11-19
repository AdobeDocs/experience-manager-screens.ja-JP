---
title: AEM Screens playerの操作
seo-title: Screens Player での作業
description: このページに従って Screens Player について学習してください。また Admin UI とチャネルスイッチャーについても説明します。
seo-description: このページに従って Screens Player について学習してください。また Admin UI とチャネルスイッチャーについても説明します。
uuid: 93e113ea-fbef-4757-982b-b7dc52fc76a7
contentOwner: jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 4ad51b5e-c628-4440-9f2e-41d17cb10bc3
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Working with AEM Screens Player {#working-with-aem-screens-player}

AEM Screens playerで、チャネルコンテンツやその他の設定を管理できます。

>[!NOTE]
>
>***Ctrl+Cmd+F**を押すと、OS X AEM Screens Player のフルスクリーンモードを終了できます。*

チャネルをディスプレイに割り当てると AEM Screens Player にコンテンツが表示されます。Admin UI の環境設定（ダッシュボード上）を使用して、またはプレーヤー自体からプレーヤーの設定を構成できます。

## Device Dashboard の使用 {#using-the-device-dashboard}

AEM オーサリングインスタンスを介してアクセスできる、Device Dashboard からデバイスの環境設定を構成できます。

1. Navigate to the device dashboard from your project, for example, ***Test Project*** --&gt; ***Devices***.

   Select **Devices** and **Device Manager** from the action bar.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. デバイスをクリックしてデバイスダッシュボードを開きます。

   ![クリメージ_1-67](assets/chlimage_1-67.png)

1. Check the **PREFERENCES** panel. You can enable/disable the **Admin UI** and **Channel Switcher** for your player from these two options.

   ![クリメージ_1-68](assets/chlimage_1-68.png)

### Admin UI {#the-admin-ui}

Enabling the **Admin UI** from the preferences panel allows the user to open the admin settings from the Screens Player. さらに、このオプションをデバイスダッシュボードから無効にすると、ユーザーはプレーヤーから Admin UI を開くことができなくなります。

Screens Player から Admin UI を表示するには、タッチ有効の AEM Screens Player またはマウスを使用して左上角を長押しして、Admin メニューを開きます。登録が完了し、チャネルが読み込まれた後に情報が表示されます。

>[!NOTE]
>
>さらに、AEM Screens Player アプリのアップタイムを表示して、アプリの正常性をチェックできます。

![chlimage_1-3](assets/chlimage_1-3.gif)

サイド・メニューから「 **Configuration** 」オプションを選択した場合は、「 **Firmware**」、「 **Preferences」または「To Factory** To Factory From」ダイアログ・ボックス **** もリセットできます。

また、AEM Screensプレーヤーに対して保持する最大ログファイル数を「最大数」で指 **定できます。 保持するログファイル**。 詳しくは、以下のスクリーンショットを参照してください。

>[!NOTE]
>
>「ファ **ームウェアの更新** 」オプションは、AndroidプレーヤーなどのCordovaでのみ機能します。

![screen_shot_2018-10-15at101257am](assets/screen_shot_2018-10-15at101257am.png)

AEM Screens Player の Admin UI から、チャネルおよびアプリケーションのキャッシュをクリアできます。

サイドレールから「**コンテンツキャッシュ**」を選択して、キャッシュを更新します。

![screen_shot_2018-10-15at105717am](assets/screen_shot_2018-10-15at105717am.png)

### チャネルスイッチャー {#the-channel-switcher}

Enabling the **Channel Switcher** from the preferences panel allows the user to open the channel selection/settings from the Screens Player.

さらに、このオプションをデバイスダッシュボードから無効にすると、ユーザーは、Screens Player からチャネル環境設定を管理できなくなります。

Screens Player からチャネルの設定を切り替えて管理できます。

プレーヤーからチャネルスイッチャーを表示するには、左下角を長押しします。こうするとチャネルスイッチャーが開いて、チャネルなどの機能を切り替えることができます。

![chlimage_1-69](assets/chlimage_1-69.png)

>[!NOTE]
>
>また、Screens player から管理者メニューおよびプレーヤー用のチャネルスイッチャーの有効と無効を切り替えることができます。
>
>（下のセクションで言及されている「*Screens Player からの設定変更*」を参照してください）

### AEM Screens Player からの設定管理 {#managing-preferences-from-the-aem-screens-player}

プレーヤー自体からも Admin UI およびチャネルスイッチャーの設定を変更できます。

以下の手順に従って、プレーヤーから設定を変更します。

1. アイドルチャネルの左上角を長押しして管理者パネルを開きます。
1. Navigate to **Configuration** from the left action menu.
1. Enable/disable configuration for **Admin UI** or **Channel Switcher**.

![screen_shot_2018-10-15at101257am-1](assets/screen_shot_2018-10-15at101257am-1.png)

## AEM Screens Player のトラブルシューティング {#troubleshooting-aem-screens-player}

AEM Screens Player に関係する多様な問題のトラブルシューティングができます。

| **発行** | **推奨事項** |
|---|---|
| プレイヤーの記憶域がいっぱいです | 不要なファイルの排除 |
| プレイヤーがネットワークを失いました | Cat-5/Cat-6ケーブルを使用します。 Wi-Fiの場合は、ルーターからプレーヤーデバイスまでの距離を短くします |
| AEM Screens playerがクラッシュしました | AEM Screens playerが常に実行されることを確認するウォッチドッグアプリを使用することをお勧めします |
| AEM Screens playerの設定が失われました | AEMサーバーへの接続の確認 |
| AEM Screens playerは、Playerの再起動/再起動後に自動的に起動しません。 | OSの開始フォルダーまたは初期化手順を確認する |
| AEM Screens playerに間違った/古いコンテンツが表示される | ネットワーク接続の確認 |

### AEM Screens Player のアップデート {#updates-for-aem-screens-player}

AEM Screens Player には次の 2 種類のアップデートがあります。

| **方法** | **詳細** | **リモート経由** | **自動** | **ダウンタイム0** |
|---|---|---|---|---|
| ファームウェアの更新 | リモートコマンドを使用して、既存のインストール済みプレーヤーに適用されます。 アップデート後に、プレーヤーは既存のコンテンツで自動リロードされます。 | 可 | カスタム | ほぼ1 ～ 3秒 |
| プレイヤーシェルの更新 | これは、プレイヤーに展開する新しい実行可能ファイルです。 これには、新しいバイナリをプレーヤーにリモートコピーして、現在実行中のプレーヤーを停止して、新しいバージョンを起動する必要があります。これには、事前ロードされているパッケージの再ダウンロードが必要なことがあります。 | ○（リモートシェル経由） | カスタム | 不可 |

## プレーヤーデバイスのハードウェア選択のガイドライン {#hardware-selection-guidelines-for-player-device}

次の節では、Screens Projectのハードウェア選択のガイドラインを示します。

* PCプレーヤーとディスプレイ ***パネル********* 、またはプロジェクターの両方に対して、常に商用または工業用品レベルのコンポーネントを提供します。

* 常に、デジタル看板市場を提供するベンダーと提携します。
* 環境温度や相対湿度などの環境要因を常に考慮してください。
* 電源要件と電源コンディショニングを常に確認します。
* アプリケーションに必要なパフォーマンスのニーズとI/Oポートを慎重に確認します。

次の表に、AEM Screensプロジェクトの一般的な使用例に関するハードウェア設定の概要を示します。

<table>
 <tbody>
  <tr>
   <td>プレイヤーの設定</td>
   <td>プロセッサ</td>
   <td>メモリ</td>
   <td>ストレージSSD</td>
   <td>GPU</td>
   <td>表示</td>
   <td>I/O</td>
   <td>一般的な使用例</td>
  </tr>
  <tr>
   <td>基本</td>
   <td>デュアルコア、i3またはエントリーレベルのクアッドコアインテル® Atomプロセッサー</td>
   <td><p>4 GBのメモリ</p> <p>2 MBのキャッシュ</p> </td>
   <td><p>・ChromeOS 32 GB</p> <p>・ Windows 128 GB</p> </td>
   <td>OnBoard</td>
   <td>1,920 x 1,080</td>
   <td>DVI、Ethernet<br /> /ワイヤレス<br /> 、USB x 2</td>
   <td>
    <ul>
     <li>標準フルスクリーンループ<br /> </li>
     <li>日分割</li>
    </ul> </td>
  </tr>
  <tr>
   <td>標準</td>
   <td>クアッドコア、インテル® Core i5プロセッサー</td>
   <td><p>8 GBのメモリ</p> <p>4 MBのキャッシュ</p> </td>
   <td>128GBB</td>
   <td>OnBoard</td>
   <td>3840 x 2160(4K)</td>
   <td>DVI、HDMI<br /> Ethernet/ワイヤレス<br /> 、USB×2</td>
   <td>
    <ul>
     <li>単一ソースの動的コンテンツ</li>
     <li>シンプルインタラクティブ</li>
     <li>1-3ゾーンレイアウト</li>
    </ul> </td>
  </tr>
  <tr>
   <td>アドバンス詳細</td>
   <td>ハイパースレッディング対応クアッドコア、インテル® Core i7プロセッサー</td>
   <td><p>16 GBのメモリ</p> <p>8 MBのキャッシュ</p> </td>
   <td>256 GB</td>
   <td>専用グラフィックGPU</td>
   <td>3840 x 2160(4K)</td>
   <td>DVI、HDMI<br /> Ethernet/ワイヤレス<br /> 、USB×4</td>
   <td>
    <ul>
     <li>4つ以上のコンテンツゾーン、同時ビデオ再生</li>
     <li>複数ページインタラクティブ</li>
     <li>マルチソースデータトリガー</li>
    </ul> </td>
  </tr>
 </tbody>
</table>
