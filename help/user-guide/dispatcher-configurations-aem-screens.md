---
title: AEM画面のディスパッチャー設定
seo-title: AEM画面のディスパッチャー設定
description: このページでは、AEM Screensプロジェクトのディスパッチャーを設定する際のガイドラインに焦点を当てます。
seo-description: このページでは、AEM Screensプロジェクトのディスパッチャーを設定する際のガイドラインに焦点を当てます。
uuid: ec5219b7-73f9-4026-99e5-e4a02201b128
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: administering
discoiquuid: 1b1a36a4-4f95-41e3-b0a8-74249efb0119
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# AEM画面のディスパッチャー設定{#dispatcher-configurations-for-aem-screens}

Dispatcher は、Adobe Experience Manager のキャッシュやロードバランシングを管理するツールです。

次のページでは、AEM Screensプロジェクトのディスパッチャーを設定する際のガイドラインを示します。

## 前提条件 {#pre-requisites}

AEM Screensプロジェクト用にディスパッチャーを設定する前に、ディスパッチャーに関する事前の知識が必要です。

詳しくは、「** [Dispatcher](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html)**の設定」を参照してください。

## Dispatcher の設定 {#configuring-dispatcher}

次の手順に従って、AEM Screensプロジェクトのディスパッチャーを設定します。

### 手順1:クライアントヘッダーの設定 {#step-configuring-client-headers}

セクションに次の内容を追 `/clientheaders`加します。

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
