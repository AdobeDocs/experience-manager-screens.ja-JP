---
title: MDMまたはEMMを使用したAndroid Playerの一括プロビジョニング
seo-title: EMMまたはMDMを使用したAndroid Playerの一括プロビジョニング
description: EMMまたはMDMを使用したAndroid Playerの一括プロビジョニングについて学習するには、このページに従ってください
translation-type: tm+mt
source-git-commit: f94eac66b6372e9f3e4cfc28693c4ba61d1b9ab1
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---


# Enterprise Mobility Managementを使用したAndroid Playerの一括プロビジョニング{#bulk-provisioning}

Androidプレーヤーを一括してデプロイする場合、すべてのプレーヤーをAEMに手動で登録するのは面倒です。 VMWare Airwatch、MobileIron、Samsung KnoxなどのEMM(Enterprise Mobility Management)ソリューションを使用して、展開のプロビジョニングと管理をリモートで行うことを強くお勧めします。 AEM ScreensAndroidプレイヤーは、業界標準のEMM Appconfigをサポートし、リモートプロビジョニングを可能にします。 プレイヤーの一括プロビジョニングを行うには、次の手順に従ってください。

## Enterprise Mobility Managementを使用したAndroid Playerの一括プロビジョニングの実装{#implementation}

次の手順に従って、Android Playerで一括プロビジョニングを許可します。

1. お使いのAndroidデバイスがGoogle Playサービスをサポートしていることを確認します。
1. Appconfigをサポートするお気に入りのEMMソリューションにAndroidプレイヤーデバイスを登録します。
1. EMMコンソールにログインし、Google PlayからAEM Screensプレイヤーアプリケーションを取り込みます。
1. 管理された設定（または関連するオプション）を選択します。
1. これで、設定可能なプレイヤーオプションのリスト（サーバーや一括登録コードなど）が表示されます。
1. これらのパラメーターを設定し、ポリシーを保存してデバイスに展開します。

   >[!NOTE]
   >デバイスは、設定と共にアプリケーションを受け取り、選択した設定を持つ正しいAEMサーバーを指し示す必要があります。 一括登録コードの設定を選択し、AEMでの設定と同じにすると、プレイヤーは自動的に登録できるはずです。 デフォルトディスプレイを設定した場合は、一部のデフォルトコンテンツをダウンロードして表示することもできます（後で利便性に応じて変更できます）。

また、AppConfigのサポートについては、EMMベンダーにお問い合わせください。 [VMWare Airwatch](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm)、[Mobile Iron](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm)、[SOTI](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm)、[Blackberry UEM](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm)、[IBM Maas360](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm)、aなど、最も人気のあるもの10/>Samsung Knox](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm)は、この業界標準をサポートしています。[


