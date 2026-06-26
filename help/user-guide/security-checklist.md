---
title: セキュリティチェックリスト
description: AEM Screens の主要なセキュリティ領域に関する質問と検討事項のチェックリストについて説明します。
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 3d2835c8-d844-46fd-b35a-30feaced9dd8
TQID: https://experienceleague.adobe.com/ES-ciW55PF5Zzh9zqRYGu-kWbOym8XkLInXmmqga524
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 536
ht-degree: 16%

---

# AEM Screens セキュリティチェックリスト {#security-checklist}

>[!IMPORTANT]
>このコンテンツは、AEM オンプレミス/AMS （AEM 6.5LTSおよびAEM 6.5）に対して有効です。 AEM as a Cloud Service Screensの内容については、[AEM as a Cloud Service ガイド &#x200B;](https://experienceleague.adobe.com/ja/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction)を参照してください。

AEM Screens セキュリティチェックリストページでは、主要なセキュリティ領域に関する質問と検討事項のチェックリストが説明されています。

## チェックリストテーブル {#checklist-table}

| **セキュリティ領域** | **チェックリスト** | **はい／いいえ／NA** |
|---|---|---|
| **AEM および Screens のソフトウェアのアップデート** | **a.** *最新のAdobe Experience Manager （AEM） サービスパックが適用されていますか？* <br>**b.** *最新のAEM Screens機能パックが適用されていますか？* <br>**c.** *最新の利用可能なAEM Screens Player ソフトウェア（[AEM Screens Player Downloads](https://download.macromedia.com/screens/)）を使用していますか？* | |
| **物理的セキュリティ** | **a.** *不要なポートをすべて無効にしましたか？* <br>**b.** *ケーブルとハードウェアを保護しましたか？* <br>**c.** *該当する場合、コンテナを使用していますか？* | |
| **ネットワークセキュリティ** | **a.** *サイネージデバイスに分離されたサブネットを使用していますか？* <br>**b.** *分離されたサブネットは、AEM、Adobe Analytics、またはその他の必要なサービスを含む必要なエンドポイントへのアクセスを許可しますか？* <br>**c.** *エンタープライズ版のベストプラクティスを使用してWi-Fiを保護しましたか？* <br>**d.** *同期再生を使用している場合、プライマリデバイスでのみWebSocketのTCP 24503を許可しましたか？* <br>**e.** *承認されたデバイスのみがオーサリングインスタンスの登録サービスにアクセスできるように、プレーヤーのデバイスのIP アドレスの範囲をブロック解除しましたか？* | |
| **オペレーティングシステムのセキュリティ** | **a.** *最新バージョンのオペレーティング システムにアップグレードし、必要なすべてのセキュリティ パッチを適用しましたか？* <br>**b.** *不要なサービスをすべて無効にし、不要なアプリケーションを削除しましたか？* <br>**c.** *エンタープライズポリシーを適用するために、デバイスをデバイス管理に登録しましたか？* <br>**d.** *1つのアプリケーション （プレーヤー） キオスクにデバイスをロックしましたか？* <br>**e.** *OSのセキュリティ更新プログラムを長期にわたってインストールするための標準操作手順（SOP）はありますか？*<br>**f.*** マルウェア対策ソフトウェア、管理者以外のユーザーなど、使用中のオペレーティングシステムのセキュリティに関するベストプラクティスに従っていますか？* | |
| **アプリケーションセキュリティ** | **a.** *実稼動用の管理UI、チャネルスイッチャー、およびアクティビティ UIを無効にしましたか？* <br>**b.** *本番環境のログレベルを最小化しましたか？* <br>**c.** *AEMへの接続にhttpsを使用していますか？* <br>**d.** *CA署名済み証明書またはエンタープライズ PKIを使用していますか？ （自己署名証明書ではありません）*<br>**e.***SSL v3ではなくTLSを使用していますか？*<br>**f.** *登録時にデバイスとAEMで登録トークンを検証していますか？*<br> **g.** *使用中のデータを分類しました。デバイスにPIIまたはPHIが存在しません。*<br> **h.** *使用中のデータを分類しました。デバイスに個人を特定できる情報（PII）または保護された健康情報（PHI）が存在しません。*<br> **i.** *電子メールの監視を設定しましたか？ 監視メールへの対応と非送信デバイスの処理に関する SOP が整備されているか。* | |
| **アクセス制御** | **a.** *ロールベースのアクセス制御（RBAC）が社内で識別および管理されていますか？* <br>**b.** *Adobeのベストプラクティスを使用して、作成者、管理者、プレーヤーにアクセス権を付与する際に、最小権限の原則に従っていますか？* | |

### セキュリティチェックリストをダウンロード {#download-checklist}

AEM Screens セキュリティチェックリストをダウンロードするには、[こちら](/help/user-guide/assets/AEMScreens-SecurityChecklist.pdf)をクリックします。

