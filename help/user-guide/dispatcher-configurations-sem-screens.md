---
title: AEM Screens プロジェクトの Dispatcher の設定
seo-title: AEM Screens プロジェクトの Dispatcher の設定
description: 'null'
seo-description: 'null'
page-status-flag: never-activated
uuid: ea68ca72-bbe7-42d5-9043-97aea7edcd6e
contentOwner: jsyal
discoiquuid: 046ec5ae-600d-422f-aa59-c39f16cf71de
docset: aem65
translation-type: tm+mt
source-git-commit: dbc20693481e6f6f379eb93bbf40ed9961589d00

---


# AEM Screens プロジェクトの Dispatcher の設定{#dispatcher-configurations-for-aem-screens}

Dispatcher は、Adobe Experience Manager のキャッシュやロードバランシングを管理するツールです。

ここでは、AEM Screens プロジェクトの Dispatcher を設定する際のガイドラインを示します。

>[!NOTE]
>ディスパッチャーが使用可能な場合は、ディスパッチャールールでフィルタリングすることで、登録サーブレットへの接続を防ぐことができます。
>ディスパッチャーがない場合は、OSGiコンポーネントリストで登録サーブレットを無効にします。

## 前提条件 {#pre-requisites}

AEM Screens プロジェクトの Dispatcher を設定する前に、Dispatcher に関する事前の知識が必要です。

詳しくは、[Dispatcher の設定](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html)を参照してください。

## Dispatcher の設定 {#configuring-dispatcher}

以下の手順に従って、AEM Screens プロジェクトの Dispatcher を設定します。

### 手順 1：クライアントヘッダーの設定 {#step-configuring-client-headers}

`/clientheaders` セクションに次の内容を追加します。

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### 手順 2：Screens フィルターの設定 {#step-configuring-screens-filters}

Screens フィルターを設定するには、以下の内容を ***/filter ***に追加します。

```
## AEM Screens Filters
## # Login, Ping and Device Configurations
/0200 { /type "allow" /method "POST" /url "/libs/granite/core/content/login.validate/j_security_check" }
/0201 { /type "allow" /method "GET" /url "/content/screens/svc.json" }
/0202 { /type "allow" /method "GET" /url "/content/screens/svc.ping.json" }
/0203 { /type "allow" /method "GET" /url "/content/screens/svc.config.json" }
## # Device Dashboard Configurations
/0204 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.preferences.json" }
/0205 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.logs.json" }
/0206 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.statusinfo.json" }
/0207 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.screenshot.json" }
## # Content Configurations
/0208 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*" }
/0209 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*/jcr:content/*/offline-config_*.zip" }
/0210 { /type "allow" /method '(GET|HEAD)' /url '/var/contentsync/content/screens/.+/jcr:content/.+/offline-config_.*\.[0-9]+\.zip' }
```

### 手順 3：Dispatcher キャッシュの無効化 {#step-disabling-dispatcher-cache}

***/content/screens パス&#x200B;***の Dispatcher キャッシュを無効にします。
