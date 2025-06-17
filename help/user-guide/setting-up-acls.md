---
title: ACL の設定
description: アクセス制御リスト（ACL）を使用してプロジェクトを分離し、個々またはチームが独自のプロジェクトを処理できるようにする方法を説明します。
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: b40bcc9f-307c-422c-8abb-5c15965772d4
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 85%

---

# アクセス制御リスト （ACL）の設定 {#setting-up-acls}

次の節では、アクセス制御リスト（ACL）を使用してプロジェクトを分離し、個々またはチームが独自のプロジェクトを処理できるようにする方法について説明します。

AEM 管理者は、プロジェクトのチームメンバーが他のプロジェクトに干渉しないようにする必要があります。各ユーザーには、プロジェクト要件に応じて特定の役割が割り当てられます。

## 権限の設定 {#setting-up-permissions}

次に、プロジェクト用の ACL の設定手順の概要を示します。

1. AEM にログインして、**ツール**／**セキュリティ**&#x200B;に移動します。

   ![screen_shot_2018-02-16at10156pm](assets/screen_shot_2018-02-16at10156pm.png)

1. 「**グループ**」をクリックして、ID（例：Acme）を入力します。

   または、このリンク（`http://localhost:4502/libs/granite/security/content/groupadmin.html`）を使用します。

   次に、「**保存**」をクリックします。

   ![screen_shot_2018-02-16at12648pm](assets/screen_shot_2018-02-16at12648pm.png)

1. リストの「**寄稿者**」をクリックし、さらにダブルクリックします。

   ![screen_shot_2018-02-18at33938pm](assets/screen_shot_2018-02-18at33938pm.png)

1. **Acme**（作成したプロジェクト）を「**メンバーをグループに追加**」に追加します。「**保存**」をクリックします。

   ![screen_shot_2018-02-18at35630pm](assets/screen_shot_2018-02-18at35630pm.png)

   >[!NOTE]
   >
   >プロジェクトチームメンバーにプレーヤーを登録させる場合（各プレーヤー用のユーザーの作成を伴う）、グループのユーザー管理者を見つけて、ACME グループをユーザー管理者に追加します。

1. **Acme** プロジェクトで作業するすべてのユーザーを **Acme** グループに追加します。

   ![screen_shot_2018-02-18at41320pm](assets/screen_shot_2018-02-18at41320pm.png)

1. この `(http://localhost:4502/useradmin)` を使用して、**Acme** グループの権限を設定します。

   **Acme** グループをクリックして、「**権限**」をクリックします。

   ![screen_shot_2018-02-18at41534pm](assets/screen_shot_2018-02-18at41534pm.png)

### 権限 {#permissions}

次の表に、プロジェクトレベルの権限のパスを示します。

| **パス** | **権限** | **説明** |
|---|---|---|
| `/apps/<project>` | 読み取り | プロジェクトファイルへのアクセス権を付与します（該当する場合）。 |
| `/content/dam/<project>` | すべて | 画像やビデオなどのプロジェクトアセットを DAM に保存するためのアクセス権を付与します。 |
| `/content/screens/<project>` | すべて | /content/screens の下にある他のすべてのプロジェクトへのアクセス権を削除します。 |
| `/content/screens/svc` | 読み取り | 登録サービスへのアクセス権を付与します。 |
| `/libs/screens` | 読み取り | DCC へのアクセス権を付与します。 |
| `/var/contentsync/content/screens/` | すべて | プロジェクトのオフラインコンテンツを更新できます。 |

>[!NOTE]
>
>場合によっては、作成者機能（アセットの管理やチャネルの作成など）を管理者機能（プレーヤーの登録など）から分離することができます。このようなシナリオでは、2 つのグループを作成し、作成者グループを投稿者に、管理者グループを投稿者とユーザー管理者の両方に追加します。

### グループの作成 {#creating-groups}

プロジェクトを作成する場合、基本的な権限が割り当てられたデフォルトのユーザーグループも作成します。AEM Screens で定義された一般的な役割に権限を拡張します。

例えば、次のプロジェクト専用グループを作成できます。

* Screens プロジェクト管理者
* Screens プロジェクトオペレーター（プレーヤーの登録、場所およびデバイスの管理）
* Screens プロジェクトユーザー（チャネル、スケジュールおよびチャネル割り当ての作業）

次の表に、AEM Screens プロジェクト用のグループの説明および権限を示します。

<table>
 <tbody>
  <tr>
   <td><strong>グループ名</strong></td>
   <td><strong>説明</strong></td>
   <td><strong>権限</strong></td>
  </tr>
  <tr>
   <td>Screens 管理者<br /> <em><code>screens-admins</code></em></td>
   <td>AEM Screens 機能に対する管理者レベルのアクセス</td>
   <td>
    <ul>
     <li>寄稿者のメンバー</li>
     <li>ユーザー管理者のメンバー</li>
     <li>ALL /content/screens</li>
     <li>ALL /content/dam</li>
     <li>ALL /content/experience-fragments</li>
     <li>ALL /etc/design/screens</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Screens ユーザー<br /> <em><code>screens-users</code></em></td>
   <td>AEM Screens でチャネルおよびスケジュールを作成および更新し、場所に割り当てる</td>
   <td>
    <ul>
     <li>寄稿者のメンバー</li>
     <li><code>&lt;project&gt; /content/screens</code></li>
     <li><code>&lt;project&gt; /content/dam</code></li>
     <li><code>&lt;project&gt; /content/experience-fragments</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td>Screens オペレーター<br /> <em><code>screens-operators</code></em></td>
   <td>AEM Screens で場所の構造を作成および更新し、プレーヤーを登録する</td>
   <td>
    <ul>
     <li>寄稿者のメンバー</li>
     <li><code>jcr:all /home/users/screens</code></li>
     <li><code>jcr:all /home/groups/screens</code></li>
     <li><code>&lt;project&gt; /content/screens</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td>Screens Player<br /> <em><code>screens-&lt;project&gt;-devices</code></em></td>
   <td>すべてのプレーヤーとすべてのプレーヤー／デバイスは自動的に寄稿者のメンバーになります。</td>
   <td><p> 寄稿者のメンバー</p> </td>
  </tr>
 </tbody>
</table>
