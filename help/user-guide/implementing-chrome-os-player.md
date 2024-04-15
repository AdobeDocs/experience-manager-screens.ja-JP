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
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '867'
ht-degree: 61%

---

# Chrome OS プレーヤーの実装  {#implementing-chrome-os-player}

ここでは、Chrome 管理コンソールを使用した Chrome OS プレーヤーの実装方法を説明します。

## Chrome 管理コンソールの使用 {#using-chrome-management-console}

Chrome 管理コンソールを設定するには、次の手順を実行します。

1. Chrome 管理コンソールを登録します。Chrome 管理コンソールのライセンスを取得する必要があります。 Chrome のデバイス設定の管理について詳しくは、[Google サポート](https://support.google.com/chrome/a/answer/1375678?hl=ja&amp;ref_topic=2935995)にお問い合わせください。
1. Chrome OS デバイスをドメインに登録し、デバイスが Chrome 管理コンソールと同期するまで 15 分間待ちます。Chrome デバイスの登録について詳しくは、[ここ](https://support.google.com/chrome/a/answer/1360534?hl=ja)をクリックしてください。
1. Chrome プレーヤーは、Chrome ウェブストアで入手できます。

>[!NOTE]
>
>Chrome OS デバイスのデプロイメントおよび管理には、Chrome 管理コンソールなどのデバイス管理ソリューションをお勧めします。このドキュメントでは Chrome 管理コンソールの実装を示していますが、同様の機能を提供すると主張するベンダーは他にもあります。 デバイス管理ソフトウェアのベンダーにお問い合わせください。

## Chrome OS プレーヤーの命名 {#name-chrome}

ユーザーにわかりやすいデバイス名を Chrome プレーヤーに割り当てて、割り当てられたデバイス名をAdobe Experience Manager（AEM）に送信することができます。 この機能により、Chrome プレーヤーに名前を付けるだけでなく、適切なコンテンツを簡単に割り当てることもできます。

>[!NOTE]
>プレーヤー名は、登録にのみ選択できます。プレーヤーの登録後は、プレーヤー名を変更できなくなります。

Chrome プレーヤーに名前を設定するには、次の手順に従います。

1. オプションで、エンタープライズ登録の一環としてオーディオ/ビデオインテグレーターまたは IT 管理者がアセット ID および場所を設定できるようにすることができます。

   ![画像](/help/user-guide/assets/chrome-device/chrome1.png)

1. デバイスを登録できる場合は、オプションが表示されます。

   ![画像](/help/user-guide/assets/chrome-device/chrome2.jpg)

1. アセット ID は、エンタープライズ登録の一環として、また Chrome 管理コンソールで設定できます。

   ![画像](/help/user-guide/assets/chrome-device/chrome3.png)

   >[!NOTE]
   >Chrome プレーヤーをエンタープライズ登録で登録し、Chrome 管理コンソールでデプロイする必要があります。そうしないと、返されるアセット ID が空白になります（例えば、chrome を拡張子として）。 デバイス名は登録時にのみ記録されます。それ以降の変更は、Adobe Experience Manager（AEM）には反映されません。

### キオスクモードの有効化 {#enabling-kiosk-mode}

キオスクモードを有効にするには、次の手順に従います。

1. Chrome Developer コンソールにログインします。

   ![screen_shot_2017-12-08at20303pm](assets/screen_shot_2017-12-08at20303pm.png)

1. **Device management**／**Chrome Management**／**Device Settings** を参照します。
1. 「**Kiosk Settings**」にスクロールダウンして、「**Manage Kiosk Applications**」をクリックします。

   ![kiosk](assets/kiosk.png)

1. Chrome Web Store から AEM Screens Player を選択します。

   >[!NOTE]
   >
   >最近公開されたアプリがこのリストに表示されるまで、約 15 分かかります。

1. 「**Auto Launch Kiosk App**」ドロップダウンから「**AEM Screens Player**」を選択します。

   ネットワークによっては、変更が反映されるまで数分かかることがあります。再起動することをお勧めします。

#### リモートデバイスのステータスの確認 {#checking-remote-device-status}

1. Chrome Developer コンソールにログインします。
1. **Device management**／**Chrome Devices** を参照し、制御したいデバイスを選択します。
1. 「**System Activity and troubleshooting**」をクリックします。
1. デバイスの **Reboot Device** および **Screen Capture** プロパティを確認します。また、デバイスステータスおよびヘルス情報も確認できます。

>[!NOTE]
>
>これらの設定は、デバイスが登録されてから数分後に有効にすることができます。 各オプションは、時間の経過と共に有効にすることができます。

### Chrome OS プレーヤーのリモート設定の設定 {#configuring-remote-configuration-of-chrome-os-players}

AEM Screens Player は、キオスク対応アプリケーションです。Chrome OS プレーヤーのリモートポリシー設定にも対応しています。

プレーヤーの様々なオプションを設定するには、次の手順を実行します。

1. Chrome 管理コンソールにログインします。
1. **Device management**／**Chrome Management**／**App Management** をクリックします。AEM Screens Player がリストに表示されます。
1. **AEM Screens Player** アプリケーションをクリックします。
1. クリック **キオスク設定** 組織を選択します（*テスト環境を使用する場合*）に設定します。
1. クリック **設定ファイルをアップロード** を作成し、設定ポリシー（*JSon ファイル*）に設定します。
1. 「**保存**」をクリックします。デバイスを再起動して、ポリシーを同期します。

>[!NOTE]
>
>デバイスを再起動して、ポリシーの変更を同期します。

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
| enableActivityUI | を有効にすると、ダウンロードや同期など、アクティビティの進行状況を表示できます。 トラブルシューティング用に有効にしておき、設定が完了して実稼働になったら無効にします。 |
| cloudMode | Chrome プレーヤーから Screens as a Cloud Service に接続する場合は、true に設定します。AMS またはオンプレミス AEMに接続する場合は、false に設定します。 |
| cloudToken | Screens as a Cloud Service に登録するための登録トークン。 |

>[!NOTE]
>
>ポリシー設定は厳格に適用されます。プレーヤーの Admin UI で、手動で上書きされることはありません。特定のポリシーに対して手動のプレーヤー設定を許可する場合、 ***ポリシー設定***. 例えば、再起動スケジュールの手動設定を許可する場合は、キーを指定しないでください ***rebootSchedule*** をポリシー設定で使用できます。

### Screens リモート制御の使用 {#using-remote-control}

AEM Screens には、リモート制御機能が用意されています。この機能について詳しくは、[Screens リモート制御](implementing-remote-control.md)を参照してください
