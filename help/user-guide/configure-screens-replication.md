---
title: Screens レプリケーションエージェントの設定
description: このページでは、Screens レプリケーションエージェントの設定方法について説明します。
role: Developer
level: Intermediate
source-git-commit: 137480ddaf6d7b73452c26402d56588230aa8c30
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 7%

---


# Screens レプリケーションエージェントの設定 {#configuring-screens-replication-agent}

ここでは、Screens レプリケーションエージェントの設定方法について説明します。

## 目的 {#objective}

Screens レプリケーションエージェントは、パブリッシュからオーサーに ping データを取り込みます。 作成者がデバイス ping を表示できるように設定する必要があります。

>[!NOTE]
>Screens レプリケーションエージェントについて詳しくは、 [Screens レプリケーションエージェントとコマンド](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/administering/author-publish/author-publish-architecture-overview.html?lang=en#screens-replication-agents-and-commands).

Screens レプリケーションエージェントの設定を完了するには、次の両方の節を完了する必要があります。

1. [ユーザーの有効化とパスワードの更新](#enable-users)
1. [Screens レプリケーションエージェント設定の更新](#replicate-agent)

## ユーザーの有効化とパスワードの更新 {#enable-users}

次の手順に従って、ユーザーを有効にし、screens-receiver-user のパスワードを更新します。

>[!NOTE]
>セキュリティ上の理由から、screens-receiver-user に admin パスワードを使用しないことをお勧めします。

1. AEM インスタンスに移動します。

1. ツール/ **セキュリティ** —> **ユーザー**.

   ![画像](/help/user-guide/assets/screens-replication/screens-replication1.png)

1. を検索 **screens-receiver-user**.

1. を選択します。 **screens-receiver-user** をクリックし、 **有効にする** をクリックします。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication2.png)

1. クリック **OK** をクリックして確定します。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication3.png)

   ユーザーを有効にすると、 **screens-receiver-user** as **有効** の下に **ステータス** フィールドに入力します。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication4.png)

1. を選択します。 **screens-receiver-user** をクリックし、 **プロパティ** をクリックします。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication5.png)

1. クリック **パスワードを変更** under **アカウント設定** から **詳細** 」タブに表示されます。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication6.png)

1. 新しいパスワードを **パスワードを変更** ダイアログボックスを開き、 **保存**.

   >[!NOTE]
   >次を入力してください： **admin** in **パスワード** フィールドに入力します。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication7.png)

1. クリック **保存して閉じる**.

1. を選択します。 **screens-receiver-user** をクリックし、 **有効化** をクリックします。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication8.png)

1. クリック **OK** をクリックして確定します。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication9.png)

1. を選択します。 **screens-receiver-user** をクリックし、 **無効にする** をクリックします。

   >[!IMPORTANT]
   > 無効化 **screens-receiver-user** は、このユーザーをオーサーインスタンスから無効にするだけで、パブリッシュインスタンスのすべてのユーザーはアクティブなままです。 クリックしない **無効化** アクティベートを解除すると、ユーザーがパブリッシュインスタンスからも削除されるので、アクションバーから。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication10.png)

1. クリック **OK** をクリックして確定します。

## Screens レプリケーションエージェント設定の更新 {#replicate-agent}

以下の節に従って、Screens レプリケーションエージェントの設定を更新します。

1. AEM インスタンスに移動します。

1. ツール/ **導入** —> **レプリケーション**.

   ![画像](/help/user-guide/assets/screens-replication/screens-replication1a.png)

1. クリック **作成者のエージェント**.

   ![画像](/help/user-guide/assets/screens-replication/screens-replication1b.png)

1. 次の図に示すように、オーサー環境で Screens レプリケーションエージェントを検索し、リンクをクリックします。

   >[!NOTE]
   >レターで Screens レプリケーションエージェントを検索します。 **S** 作成者の名前に含まれます。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication1c.png)

1. **編集**&#x200B;をクリックします。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication1d.png)

1. チェック **有効** から **設定** タブをクリックします。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication1e.png)

1. に移動します。 **輸送** タブ **エージェント設定** ダイアログボックスに入力し、 [ユーザーの有効化とパスワードの更新](#enable-users). 「**OK**」をクリックします。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication1f.png)

1. 上記の手順を完了したら、「 **接続をテスト** 接続を確認します。

   ![画像](/help/user-guide/assets/screens-replication/screens-replication1g.png)

   接続の検証が成功した場合は、Screens レプリケーションエージェントの設定を完了しています。