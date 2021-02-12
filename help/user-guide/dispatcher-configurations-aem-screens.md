---
title: AEM Screens プロジェクトの Dispatcher の設定
seo-title: AEM Screens プロジェクトの Dispatcher の設定
description: ここでは、AEM Screens プロジェクトの Dispatcher を設定する際のガイドラインについて説明します。
seo-description: ここでは、AEM Screens プロジェクトの Dispatcher を設定する際のガイドラインについて説明します。
translation-type: ht
source-git-commit: 43aca405707625fe5a132beaed82dbb9a4513129
workflow-type: ht
source-wordcount: '391'
ht-degree: 100%

---


# AEM Screens プロジェクトの Dispatcher の設定 {#dispatcher-configurations-for-aem-screens}

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

AEM Screens プレーヤー／デバイスは、パブリッシュインスタンスのリソースにもアクセスする際にも、認証済みセッションを使用します。したがって、複数のパブリッシュインスタンスがある場合、AEM Screens のプレーヤー／デバイスから送られるすべてのリクエストで認証済みセッションが有効になるよう、常に同じパブリッシュインスタンスにリクエストを送信する必要があります。

以下の手順に従って、AEM Screens プロジェクトの Dispatcher を設定します。

### スティッキーセッションの有効化 {#enable-sticky-session}

1 つのディスパッチャーを経由して複数のパブリッシュインスタンスを使用する場合は、`dispatcher.any` ファイルを更新してスティッキーセッションを有効にする必要があります

```xml
/stickyConnections {
  /paths
  {
    "/"
  }
 }
```

1　つのディスパッチャーを経由して 1　つのパブリッシュインスタンスを使用する場合、ディスパッチャーでスティッキーセッションを有効にしても、ロードバランサーが各リクエストをディスパッチャーに送信してしまうため、役に立ちません。この場合、次の図に示すように、「**Stckiness**」フィールドの「**Enable**」をクリックして、ロードバランサーレベルで有効にします。

![画像](/help/user-guide/assets/dispatcher/dispatcher-enable.png)

例えば、AWS ALB を使用している場合、ALB レベルでのスティッキーセッションの有効化については、[アプリケーションロードバランサーのターゲットグループ](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html)を参照してください。1 日間、スティッキーセッションを有効にします。

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
* `/cache` の `/rules` セクションに以下の規則を追加

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
