---
title: AEM画面のディスパッチャー設定
seo-title: AEM画面のディスパッチャー設定
description: 'null'
seo-description: 'null'
page-status-flag: never-activated
uuid: ea68ca72-bbe7-42d5-9043-97aea7edcd6e
contentOwner: jsyal
discoiquuid: 046ec5ae-600d-422f-aa59-c39f16cf71de
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# AEM画面のディスパッチャー設定{#dispatcher-configurations-for-aem-screens}

Dispatcher は、Adobe Experience Manager のキャッシュやロードバランシングを管理するツールです。

次のページでは、AEM Screensプロジェクトのディスパッチャーを設定する際のガイドラインを示します。

## 前提条件 {#pre-requisites}

AEM Screensプロジェクト用にディスパッチャーを設定する前に、ディスパッチャーに関する事前の知識が必要です。

Refer to **[Configuring Dispatcher](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html)** for more details.

## Dispatcher の設定 {#configuring-dispatcher}

次の手順に従って、AEM Screensプロジェクトのディスパッチャーを設定します。

### 手順1:クライアントヘッダーの設定 {#step-configuring-client-headers}

次をセクションに追加しま `/clientheaders` す。

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### 手順2:画面フィルタの設定 {#step-configuring-screens-filters}

画面フィルターを設定するには、 ***/filterに次を追加します***。

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

### 手順3:ディスパッチャーキャッシュの無効化 {#step-disabling-dispatcher-cache}

/content/screensパスのディスパッチ ***ャーキャッシュを無効にします***。
