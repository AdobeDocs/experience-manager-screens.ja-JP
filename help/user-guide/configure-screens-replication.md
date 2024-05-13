---
title: Screens レプリケーションエージェントの設定
description: Screens レプリケーションエージェントの設定方法について説明します。
role: Developer
level: Intermediate
exl-id: 40877547-5027-41eb-8d66-d4a2d7b9af70
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 86%

---

# Screens レプリケーションエージェントの設定 {#configuring-screens-replication-agent}

ここでは、Screens レプリケーションエージェントの設定方法について説明します。

## 目的 {#objective}

Screens レプリケーションエージェントは、*user*、*password*、*rebootSchedule*、*maxNumberOfLogFilesToKeep* などのコマンドデータをはじめ、さらに多くの値をパブリッシュからオーサーに渡す役目を担います。オーサーがデバイス ping を表示できるように設定する必要があります。

>[!NOTE]
>Screens レプリケーションエージェントについて詳しくは、[Screens レプリケーションエージェントとコマンド](https://experienceleague.adobe.com/ja/docs/experience-manager-screens/user-guide/administering/author-publish/author-publish-architecture-overview#screens-replication-agents-and-commands)を参照してください。

Screens レプリケーションエージェントの設定を完了する場合は、次の両方のセクションを完了してください。

1. [ユーザーの有効化とパスワードの更新](#enable-users)
1. [Screens レプリケーションエージェント設定の更新](#replicate-agent)

## ユーザーの有効化とパスワードの更新 {#enable-users}

次の手順に従って、ユーザーを有効にし、`screens-receiver-user` のパスワードを更新します。

>[!NOTE]
>セキュリティ上の理由から、`screens-receiver-user` に admin パスワードを使用しないことをお勧めします。

1. AEM オーサーインスタンスに移動します。

1. ツール／**セキュリティ**／**ユーザー**&#x200B;をクリックします。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. **`screens-receiver-user`** を検索します。

1. 「」をクリックします **`screens-receiver-user`** をクリックして、 **Enable （有効）** アクションバーから。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. 「**OK**」をクリックして確定します。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication3.png)

   ユーザーを有効にすると、 **`screens-receiver-user`** as **Enabled** の下 **ステータス** フィールド。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. 「」をクリックします **`screens-receiver-user`** をクリックして、 **プロパティ** アクションバーから。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. 次の図に示すように、「**詳細**」タブの「**アカウント設定**」から、「**パスワードを変更**」をクリックします。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. **パスワードを変更**&#x200B;ダイアログボックスに新しいパスワードを入力し、「**保存**」をクリックします。

   >[!NOTE]
   >既存の管理者ユーザーパスワードは、**パスワード**&#x200B;フィールドに入力します。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. 「**保存して閉じる**」をクリックします。

1. 「」をクリックします **`screens-receiver-user`** をクリックして、 **Activate** アクションバーから。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. 「**OK**」をクリックして確定します。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. 「」をクリックします **`screens-receiver-user`** をクリックして、 **無効** アクションバーから。

   >[!IMPORTANT]
   > **`screens-receiver-user`** の無効化は、このユーザーをオーサーインスタンスから無効にするだけで、パブリッシュインスタンスのすべてのユーザーはアクティブなままです。無効化は、ユーザーがパブリッシュインスタンスからも削除されるので、アクションバーから「**無効にする**」をクリックしないようにします。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. 「**OK**」をクリックして確定します。

## Screens レプリケーションエージェント設定の更新 {#replicate-agent}

以下の節に従って、AEM Screens レプリケーションエージェントの設定を更新します。

>[!IMPORTANT]
>既存のすべての AEM Screens レプリケーションエージェントで、次の手順を実行します。

1. AEM インスタンスに移動します。
1. ツール／**導入**／**レプリケーション**&#x200B;をクリックします。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. 「**作成者のエージェント**」をクリックします。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. 次の図に示すように、オーサー環境のすべての AEM Screens レプリケーションエージェントを検索し、リンクをクリックします。

   >[!NOTE]
   >すべての AEM Screens レプリケーションエージェントを検索します。Screens レプリケーションエージェント名には、タイトルに **S** が含まれます。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. 「**編集**」をクリックします。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. 「**設定**」タブから「**有効**」をチェックします。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. **エージェント設定**&#x200B;ダイアログボックスから「**トランスポート**」タブに移動し、**ユーザー**&#x200B;を **`screens-receiver-user`** に更新して、[ユーザーの有効化とパスワードの更新](#enable-users)の手順 (8) で入力したパスワードと同じものを入力します。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication1-f.png)

1. 「**OK**」をクリックします。

1. 上記の手順を完了したら、 **接続をテスト** 接続を確認します。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   接続の検証が成功した場合は、Screens レプリケーションエージェントの設定は完了です。
