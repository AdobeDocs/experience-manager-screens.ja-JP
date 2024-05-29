---
title: Chrome OS プレーヤーの実装
description: Chrome 管理コンソールを使用した Chrome OS プレーヤーの実装について説明します。
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 4f16605b-aec1-45fa-a110-0af6925b74b0
source-git-commit: a89aec16bb36ecbde8e417069e9ed852363acd82
workflow-type: ht
source-wordcount: '869'
ht-degree: 100%

---

# Chrome OS プレーヤーの実装 {#implementing-chrome-os-player}

ここでは、Chrome 管理コンソールを使用した Chrome OS プレーヤーの実装方法を説明します。

## Chrome 管理コンソールの使用 {#using-chrome-management-console}

Chrome 管理コンソールを設定するには、次の手順を実行します。

1. Chrome 管理コンソールを登録します。Chrome 管理コンソールのライセンスを取得する必要があります。Chrome のデバイス設定の管理について詳しくは、[Google サポート](https://support.google.com/chrome/a/answer/1375678?hl=ja&amp;ref_topic=2935995)にお問い合わせください。
1. Chrome OS デバイスをドメインに登録し、デバイスが Chrome 管理コンソールと同期するまで 15 分間待ちます。Chrome デバイスの登録について詳しくは、[ここ](https://support.google.com/chrome/a/answer/1360534?hl=ja)をクリックしてください。
1. Chrome プレーヤーは Chrome ウェブストアで入手できます。

>[!NOTE]
>
>Chrome OS デバイスのデプロイメントおよび管理には、Chrome 管理コンソールなどのデバイス管理ソリューションをお勧めします。このドキュメントでは Chrome 管理コンソールの実装を扱いますが、他のベンダーにも同様の機能を提供するものがあります。デバイス管理ソフトウェアのベンダーにお問い合わせください。

## Chrome OS プレーヤーの命名 {#name-chrome}

ユーザーにわかりやすいデバイス名を Chrome プレーヤーに割り当てて、その割り当てたデバイス名を Adobe Experience Manager（AEM）に送信できます。この機能により、Chrome プレーヤーに名前を付けるだけでなく、適切なコンテンツを簡単に割り当てることもできます。

>[!NOTE]
>プレーヤー名は、登録前にのみ選択できます。プレーヤーの登録後は、プレーヤー名を変更できなくなります。

Chrome プレーヤーに名前を設定するには、次の手順に従います。

1. オプションで、エンタープライズ登録の一環としてオーディオ／ビデオインテグレーターまたは IT 管理者がアセット ID および場所を設定できるようにすることも可能です。

   ![画像](/help/user-guide/assets/chrome-device/chrome1.png)

1. デバイスを登録できる場合は、オプションが表示されます。

   ![画像](/help/user-guide/assets/chrome-device/chrome2.jpg)

1. アセット ID は、エンタープライズ登録の一環として設定できるほか、Chrome 管理コンソールでも設定できます。

   ![画像](/help/user-guide/assets/chrome-device/chrome3.png)

   >[!NOTE]
   >Chrome プレーヤーをエンタープライズ登録で登録し、Chrome 管理コンソールでデプロイする必要があります。そうでなければ、アセット ID が空白を返します（例：拡張機能としての Chrome など）。デバイス名は登録時にのみ記録されます。それ以降の変更は、Adobe Experience Manager（AEM）には反映されません。

### キオスクモードの有効化 {#enabling-kiosk-mode}

キオスクモードを有効にするには、次の手順に従います。

1. Chrome Developer Console にログインします。

   ![screen_shot_2017-12-08at20303pm](assets/screen_shot_2017-12-08at20303pm.png)

1. **デバイス管理**／**Chrome 管理**／**デバイス設定**&#x200B;を参照します。
1. 「**Kiosk Settings**」にスクロールダウンして、「**Manage Kiosk Applications**」をクリックします。

   ![kiosk](assets/kiosk.png)

1. Chrome ウェブストアから AEM Screens Player をクリックします。

   >[!NOTE]
   >
   >最近公開されたアプリがこのリストに表示されるまで、約 15 分かかります。

1. **Auto Launch Kiosk App** ドロップダウンから「**AEM Screens Player**」をクリックします。

   ネットワークによっては、変更が反映されるまで数分かかることがあります。再起動することをお勧めします。

#### リモートデバイスのステータスの確認 {#checking-remote-device-status}

1. Chrome Developer Console にログインします。
1. **デバイス管理**／**Chrome デバイス**&#x200B;を参照し、制御したいデバイスをクリックします。
1. 「**System Activity and troubleshooting**」をクリックします。
1. デバイスの **Reboot Device** および **Screen Capture** プロパティを確認します。また、デバイスステータスおよびヘルス情報も確認できます。

>[!NOTE]
>
>これらの設定が有効になるには、デバイスが登録されてから数分後かかる場合があります。各オプションは、時間が経過すると有効になります。

### Chrome OS プレーヤーのリモート設定の設定 {#configuring-remote-configuration-of-chrome-os-players}

AEM Screens Player は、キオスク対応アプリケーションです。Chrome OS プレーヤーのリモートポリシー設定にも対応しています。

プレーヤーの様々なオプションを設定するには、次の手順を実行します。

1. Chrome 管理コンソールにログインします。
1. **デバイス管理**／**Chrome 管理**／**アプリ管理**&#x200B;をクリックします。AEM Screens Player がリストに表示されます。
1. **AEM Screens Player** アプリケーションをクリックします。
1. 「**キオスク設定**」をクリックして、組織（*テスト環境を使用している場合*）をクリックします。
1. 「**設定ファイルをアップロード**」をクリックして、設定ポリシー（*JSON ファイル*）をアップロードします。
1. 「**保存**」をクリックします。ポリシーを同期するには、デバイスを再起動します。

>[!NOTE]
>
>ポリシーの変更を同期するには、デバイスを再起動します。

#### ポリシー JSON ファイルの例 {#example-policy-json-file}

```java
{
  "server": {
    "Value": "https://aemscreensdemo.adobeitc.com"
  },
  "resolution": {
    "Value": "auto"
  },
  "rebootSchedule": {
    "Value": "at 4:00am"
  },
  "enableAdminUI": {
    "Value": true
  },
  "enableOSD": {
    "Value": true
  },
  "enableActivityUI": {
    "Value": true
  }
}
```

### ポリシーの属性と目的 {#policy-attributes-and-purpose}

次の表に、ポリシーとその機能の概要を示します。

| **ポリシー名** | **目的** |
|---|---|
| server | Adobe Experience Manager（AEM）サーバーの URL。 |
| registrationKey | 事前共有キーを使用したデバイスの一括登録に使用されます。 |
| resolution | デバイスの解像度。 |
| rebootSchedule | プレーヤーを再起動するスケジュール。 |
| enableAdminUI | サイト上でデバイスを設定するための Admin UI を有効にします。設定が完了して実稼働になったら、false に設定します。 |
| enableOSD | ユーザー用のチャネルスイッチャー UI を有効にし、デバイスのチャネルを切り替えます。設定が完了して実稼働になったら、false に設定することを検討します。 |
| enableActivityUI | 有効にすると、ダウンロードや同期などのアクティビティの進捗を表示できます。トラブルシューティング用に有効にしておき、設定が完了して実稼働になったら無効にします。 |
| cloudMode | Chrome プレーヤーから Screens as a Cloud Service に接続する場合は、true に設定します。AMS またはオンプレミス AEM に接続する場合は、false に設定します。 |
| cloudToken | Screens as a Cloud Service に登録するための登録トークン。 |

>[!NOTE]
>
>ポリシー設定は厳格に適用され、プレーヤーの管理 UI は手動で上書きされません。特定のポリシーに対して手動のプレーヤー設定を許可するには、***ポリシー設定***&#x200B;でポリシーを指定しないでください。例えば、再起動スケジュールの手動設定を許可する場合は、ポリシー設定で ***rebootSchedule*** キーを指定しないでください。

### Screens リモート制御の使用 {#using-remote-control}

AEM Screens には、リモート制御機能が用意されています。この機能について詳しくは、[Screens リモート制御](implementing-remote-control.md)を参照してください
