---
title: MDM または EMM を使用した Android プレーヤーの一括プロビジョニング
seo-title: EMM または MDM を使用した Android プレーヤーの一括プロビジョニング
description: このページでは、EMM または MDM を使用した Android プレーヤーの一括プロビジョニングについて説明します。
translation-type: ht
source-git-commit: 793507b266b99051544b377e4a7effb92dc6feb6
workflow-type: ht
source-wordcount: '334'
ht-degree: 100%

---


# エンタープライズモビリティ管理を使用した Android プレーヤーの一括プロビジョニング {#bulk-provisioning}

Android プレーヤーを一括デプロイする場合、プレーヤーを 1 つずつ手動で AEM に登録するのは非常に面倒です。VMWare Airwatch、MobileIron、Samsung Knox などの EMM（エンタープライズモビリティ管理）ソリューションを使用して、デプロイメントのプロビジョニングと管理をリモートでおこなうことを強くお勧めします。AEM Screens Android プレーヤーでは、業界標準の EMM AppConfig をサポートしているので、リモートプロビジョニングが可能です。

## エンタープライズモビリティ管理を使用した Android プレーヤーの一括プロビジョニングの実装 {#implementation}

Android プレーヤーの一括プロビジョニングを可能にするには、次の手順に従います。

1. お使いの Android デバイスが Google Play サービスをサポートしていることを確認します。
1. AppConfig をサポートしているお気に入りの EMM ソリューションに、お使いの Android プレーヤーデバイスを登録します。
1. EMM コンソールにログインし、Google Play から AEM Screens Player アプリケーションを入手します。
1. 管理された設定（または関連オプション）を選択します。
1. これで、設定可能なプレーヤーオプション（サーバーや一括登録コードなど）のリストが表示されます。
1. これらのパラメーターを設定して保存し、ポリシーをデバイスにデプロイします。

   >[!NOTE]
   >デバイスは、アプリケーションと設定を同時に受信し、選択した設定を持つ正しい AEM サーバーを参照します。一括登録コードを設定することを選択し、AEM に設定した値と同じにしておくと、プレーヤーは自動的に登録されるはずです。デフォルトディスプレイを設定した場合は、一部のデフォルトコンテンツをダウンロードして表示することもできます（このコンテンツは後で都合に合わせて変更できます）。

また、AppConfig のサポートについては、EMM ベンダーに確認してください。中でも、[VMWare Airwatch](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm)、[Mobile Iron](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm)、[SOTI](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm)、[Blackberry UEM](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm)、[IBM Maas360](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm)、[Samsung Knox](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm) などの最も一般的なものは、この業界標準をサポートしています。


