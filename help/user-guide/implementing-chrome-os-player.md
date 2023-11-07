---
title: Chrome OS プレーヤーの実装
seo-title: Implementing Chrome OS Player
description: このページでは、Chrome 管理コンソールを使用した Chrome OS プレーヤーの実装について説明します。
seo-description: Follow  this page to learn about the implementation of the Chrome OS Player using the Chrome Management Console.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 4f16605b-aec1-45fa-a110-0af6925b74b0
source-git-commit: 970762bb08f19ab07917dd5a21f67a007ec1143f
workflow-type: tm+mt
source-wordcount: '893'
ht-degree: 73%

---

# Chrome OS プレーヤーの実装  {#implementing-chrome-os-player}

ここでは、Chrome 管理コンソールを使用した Chrome OS プレーヤーの実装方法を説明します。

## Chrome 管理コンソールの使用 {#using-chrome-management-console}

Chrome 管理コンソールを設定するには、次の手順を実行します。

1. Chrome 管理コンソールに登録します。 Chrome 管理コンソールのライセンスを取得する必要があります。 Chrome のデバイス設定の管理について詳しくは、[Google サポート](https://support.google.com/chrome/a/answer/1375678?hl=ja&amp;ref_topic=2935995)にお問い合わせください。
1. Chrome OS デバイスをドメインに登録し、デバイスが Chrome 管理コンソールと同期されるまで 15 分待ちます。 Chrome デバイスの登録について詳しくは、 [ここ](https://support.google.com/chrome/a/answer/1360534?hl=ja).
1. Chrome Web ストアで Chrome プレーヤーを利用できるようになります。

>[!NOTE]
>
>Chrome OS デバイスのデプロイメントと管理には、Chrome 管理コンソールなどのデバイス管理ソリューションをお勧めします。 このドキュメントでは Chrome 管理コンソールの実装を提供していますが、他のベンダーも同様の機能を提供すると主張しています。 デバイス管理ソフトウェアのベンダーに問い合わせてください。

## Chrome OS プレーヤーの命名 {#name-chrome}

ユーザーにわかりやすいデバイス名を Chrome プレーヤーに割り当てて、そのデバイス名を Adobe Experience Manager（AEM）に送信することができます。この機能により、Chrome プレーヤーに名前を付けるだけでなく、適切なコンテンツを簡単に割り当てることもできます。

>[!NOTE]
>プレーヤー名は、登録にのみ選択できます。プレーヤーの登録後は、プレーヤー名を変更できなくなります。

Chrome プレーヤーに名前を設定するには、次の手順に従います。

1. オプションで、エンタープライズ登録の一環として AV インテグレーターまたは IT 管理者がアセット ID および場所を設定できるようにすることも可能です。

   ![画像](/help/user-guide/assets/chrome-device/chrome1.png)

1. デバイスを登録できる場合は、オプションが表示されます。

   ![画像](/help/user-guide/assets/chrome-device/chrome2.jpg)

1. アセット ID は、エンタープライズ登録の一環として設定できるほか、Chrome 管理コンソールでも設定できます。

   ![画像](/help/user-guide/assets/chrome-device/chrome3.png)

   >[!NOTE]
   >Chrome プレーヤーをエンタープライズ登録で登録し、Chrome 管理コンソールでデプロイする必要があります。そうしないと、返されるアセット ID が空白になります（例えば、chrome を拡張子として）。デバイス名は登録時にのみ記録されます。それ以降の変更は、Adobe Experience Manager（AEM）には反映されません。

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
1. クリック **システムアクティビティとトラブルシューティング**.
1. 次を確認します。 **デバイスを再起動** および **スクリーンキャプチャ** デバイスのプロパティ。 また、デバイスのステータスとヘルス情報を確認することもできます。

>[!NOTE]
>
>これらの設定は、デバイスが登録されてから数分後に有効になる場合があります。 各オプションは、時間の経過と共に有効になる場合があります。

### Chrome OS プレーヤーのリモート設定の設定 {#configuring-remote-configuration-of-chrome-os-players}

AEM Screens Player は、キオスク対応アプリケーションです。Chrome OS プレーヤーのリモートポリシー設定にも対応しています。

以下の手順に従って、プレーヤーの様々なオプションを設定します。

1. Chrome 管理コンソールにログインします。
1. **Device management**／**Chrome Management**／**App Management** をクリックします。AEM Screens Player がリストに表示されます。
1. アプリケーションをクリックします。 **AEM Screens Player**.
1. クリック **キオスク設定** を選択し、組織 (*テスト環境を使用する場合*) をクリックします。
1. 「**upload configuration file**」をクリックして、設定ポリシー（*Json file*）をアップロードします。
1. 「**保存**」をクリックします。ポリシーを同期するには、デバイスを再起動する必要があります。

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
| server | Adobe Experience Manager(AEM) サーバーへの URL。 |
| registrationKey | 事前共有キーを使用したデバイスの一括登録に使用されます。 |
| resolution | デバイスの解像度。 |
| rebootSchedule | プレーヤーを再起動するスケジュール。 |
| enableAdminUI | サイト上でデバイスを設定するための Admin UI を有効にします。設定が完了して実稼働になったら、false に設定します。 |
| enableOSD | ユーザー用のチャネルスイッチャー UI を有効にし、デバイスのチャネルを切り替えます。設定が完了して実稼働になったら、false に設定することを検討します。 |
| enableActivityUI | ダウンロードや同期などのアクティビティの進行状況を表示できます。 トラブルシューティング用に有効にしておき、設定が完了して実稼働になったら無効にします。 |
| cloudMode | Tizen プレーヤーから Screens as a Cloud Service に接続する場合は、true に設定します。AMS またはオンプレミス AEM に接続する場合は、false に設定します。 |
| cloudToken | Screens as a Cloud Service に登録するための登録トークン。 |

>[!NOTE]
>
>ポリシー設定は厳密に適用され、プレーヤーの管理 UI で手動で上書きされるわけではありません。 特定のポリシーに対して手動のプレーヤー設定を許可する場合は、***ポリシー設定***&#x200B;にポリシーを指定しないでください。例えば、再起動スケジュールの手動設定を許可する場合は、ポリシー設定にキー ***rebootSchedule*** を指定しないでください。

### Screens リモート制御の使用 {#using-remote-control}

AEM Screens には、リモート制御機能が用意されています。この機能について詳しくは、[Screens リモート制御](implementing-remote-control.md)を参照してください。
