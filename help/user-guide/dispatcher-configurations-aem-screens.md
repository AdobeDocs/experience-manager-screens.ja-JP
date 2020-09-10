---
title: AEM Screens プロジェクトの Dispatcher の設定
seo-title: AEM Screens プロジェクトの Dispatcher の設定
description: ここでは、AEM Screens プロジェクトの Dispatcher を設定する際のガイドラインについて説明します。
seo-description: ここでは、AEM Screens プロジェクトの Dispatcher を設定する際のガイドラインについて説明します。
translation-type: tm+mt
source-git-commit: 4a1fb81fa343983093590c36ccb6a4fd110cdad2
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 88%

---


# AEM Screens プロジェクトの Dispatcher の設定{#dispatcher-configurations-for-aem-screens}

Dispatcher は、Adobe Experience Manager のキャッシュやロードバランシングを管理するツールです。

ここでは、AEM Screens プロジェクトの Dispatcher を設定する際のガイドラインを示します。

>[!NOTE]
>
>Dispatcher が使用可能な場合は、Dispatcher ルールでフィルタリングすることで、登録サーブレットへの接続を防ぐことができます。
>
>Dispatcher がない場合は、OSGi コンポーネントリストで登録サーブレットを無効にします。

## 前提条件 {#pre-requisites}

AEM Screens プロジェクトの Dispatcher を設定する前に、Dispatcher に関する事前の知識が必要です。

詳しくは、[Dispatcher の設定](https://docs.adobe.com/content/help/ja-JP/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html)を参照してください。

## Dispatcher の設定 {#configuring-dispatcher}

以下の手順に従って、AEM Screens プロジェクトの Dispatcher を設定します。

### スティッキーセッションの有効化 {#enable-sticky-session}

ディスパッチャーと共に複数の発行インスタンスを使用する場合は、 `dispatcher.any` ファイルを更新する必要があります。

```xml
/stickyConnections {
  /paths
  {
    "/content/screens"
    "/home/users/screens"
    "/libs/granite/csrf/token.json"
  }
}
```

### 手順 1：クライアントヘッダーの設定 {#step-configuring-client-headers}

`/clientheaders` セクションに次の内容を追加します。

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### 手順 2：Screens フィルターの設定 {#step-configuring-screens-filters}

Screens フィルターを設定するには、以下の内容を ***/filter*** に追加します。

```
## AEM Screens Filters
## # Login, Ping and Device Configurations
/0200 { /type "allow" /method "POST" /url "/libs/granite/core/content/login.validate/j_security_check" }
/0201 { /type "allow" /method "GET" /url "/libs/granite/csrf/token.json" }
/0202 { /type "allow" /method "GET" /url "/content/screens/svc.json" }
/0203 { /type "allow" /method "GET" /url "/content/screens/svc.ping.json" }
/0204 { /type "allow" /method "GET" /url "/content/screens/svc.config.json" }
## # Device Dashboard Configurations
/0210 { /type "allow" /method '(GET|POST)' /url "/home/users/screens/*/devices/*/profile_screens.preferences.json" }
/0211 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.logs.json" }
/0212 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.statusinfo.json" }
/0213 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.screenshot.json" }
## # Content Configurations
/0220 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*" }
/0221 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*/jcr:content/*/offline-config_*.zip" }
/0222 { /type "allow" /method '(GET|HEAD)' /url '/var/contentsync/content/screens/.+/jcr:content/.+/offline-config_.*\.[0-9]+\.zip' }
```

### 手順 3：Dispatcher キャッシュの無効化 {#step-disabling-dispatcher-cache}

***/content/screens パス***&#x200B;の Dispatcher キャッシュを無効にします。

Screens プレーヤーは認証済みセッションを使用するので、Dispatcher は、`channels/assets` に対する Screens プレーヤーのリクエストをキャッシュしません。

アセットを Dispatcher のキャッシュから提供するために、アセットのキャッシュを有効にするには、次の操作をおこなう必要があります。

* `/allowAuthorization 1` を `/cache` セクションに追加
* Add the below rules to `/rules` section of `/cache`

```xml
/0000
    {
        /glob "*"
        /type "allow"
    }   

/0001
    {
        # Disable Dispatcher Cache for Screens channels
        /glob "/content/screens/*.html"
        /type "deny" 
    }

/0002
    {
    # Disable Dispatcher Cache for Screens offline manifests
    /glob "/content/screens/*.json"
    /type "deny"
    }

/0003
    { # Disable Dispatcher Cache for Screens devices json 
    /glob "/home/users/screens/*.json"
    /type "deny"
    }
```
