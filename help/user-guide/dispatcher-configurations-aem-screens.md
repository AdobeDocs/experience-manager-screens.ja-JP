---
title: AEM Screens プロジェクトの Dispatcher の設定
seo-title: AEM Screens プロジェクトの Dispatcher の設定
description: ここでは、AEM Screens プロジェクトの Dispatcher を設定する際のガイドラインについて説明します。
seo-description: ここでは、AEM Screens プロジェクトの Dispatcher を設定する際のガイドラインについて説明します。
feature: Screens の管理
role: Developer, User
level: Intermediate
exl-id: 8b281488-f54d-4f8a-acef-ca60fa2315ed
source-git-commit: 7e4d3c5ed7299d6439bf9be6d49ec9224dcf71ed
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 68%

---

# AEM Screens プロジェクトの Dispatcher の設定{#dispatcher-configurations-for-aem-screens}

Dispatcher は、Adobe Experience Manager のキャッシュやロードバランシングを管理するツールです。

ここでは、AEM Screens プロジェクトの Dispatcher を設定する際のガイドラインを示します。

>[!NOTE]
>
>Dispatcher が使用可能な場合は、Dispatcher ルールでフィルタリングすることで、登録サーブレットへの接続を防ぐことができます。
>
>Dispatcher がない場合は、OSGi コンポーネントリストで登録サーブレットを無効にします。

## 前提条件 {#prerequisites}

>[!IMPORTANT]
>AEM Screens プロジェクトの Dispatcher を設定する前に、Dispatcher に関する事前の知識が必要です。
>詳しくは、[Dispatcher の設定](https://docs.adobe.com/content/help/ja-JP/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html)を参照してください。

## Dispatcher の設定 {#configuring-dispatcher}

>[!IMPORTANT]
>次のDispatcher設定は、マニフェストバージョンv2にのみ適用されます。 マニフェストバージョンV3については、 [マニフェストバージョンv3]{#configuring-dispatcherv3}のDispatcher設定を参照してください。

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

1 つのディスパッチャーを経由して 1 つのパブリッシュインスタンスを使用する場合、ディスパッチャーでスティッキーセッションを有効にしても、ロードバランサーが各リクエストをディスパッチャーに送信してしまうため、役に立ちません。この場合、次の図に示すように、「**Stckiness**」フィールドの「**Enable**」をクリックして、ロードバランサーレベルで有効にします。

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

## マニフェストバージョンv3用のDispatcherの設定{#configuring-dispatcherv3}

Screensを機能させるには、パブリッシュインスタンスの前にあるDispatcherで、これらのフィルターとキャッシュルールを必ず許可してください。

## マニフェストバージョンv3の前提条件{#prerequisites3}

AEM Screens用のDispatcherを設定する前に、次の2つの前提条件に従ってください。

* `v3 manifests`を使用していることを確認します。 `https://<server:port>/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag`に移動し、`Enable ContentSync Cache`がオフになっていることを確認します。

* パブリッシュインスタンスの`/etc/replication/agents.publish/dispatcher1useast1Agent`にDispatcherフラッシュエージェントが設定されていることを確認します。

   ![画像](/help/user-guide/assets/dispatcher/dispatcher-1.png)

### フィルター  {#filter-v3}

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
#/0221 { /type "allow" /method '(GET|HEAD)' /url "/content/experience-fragments/*" } ## uncomment this, if you're using experience-fragments
/0222 { /type "allow" /extension '(css|eot|gif|ico|jpeg|jpg|js|gif|pdf|png|svg|swf|ttf|woff|woff2|html|mp4|mov|m4v)' /path "/content/dam/*" } ## add any other formats required for your project here
 
## # Enable clientlibs proxy servlet
/0230 { /type "allow" /method "GET" /url "/etc.clientlibs/*" }
```

### キャッシュルール {#cache-rules-v3}

* `/allowAuthorized "1"`を`publish_farm.any`の`/cache`セクションに追加します。

* すべてのScreensプレーヤーは、認証済みセッションを使用してAEM（オーサー/パブリッシュ）に接続します。 標準のDispatcherは、これらのURLをキャッシュしないので、これらを有効にする必要があります。

* `publish_farm.any`の`statfileslevel "10"`を`/cache`セクションに追加します。
これにより、すべてを無効化するのではなく、キャッシュドキュメントルートから最大10レベルのキャッシュをサポートし、コンテンツが公開されたときにそれに応じて無効化します。 コンテンツ構造の深さに基づいて、このレベルを自由に変更できます。

* 以下を`/invalidate section in publish_farm.any`に追加します。

```
/0003 {
    /glob "*.json"
    /type "allow"
}
```

`publish_farm.any`の`/rules`セクションまたは`publish_farm.any`からインクルードされるファイルに、次のルールを`/cache`セクションに追加します。

```
## Don't cache CSRF login tokens
/0001
    {
    /glob "/libs/granite/csrf/token.json"
    /type "deny"
    }
## Allow Dispatcher Cache for Screens channels
/0002
    {
        /glob "/content/screens/*.html"
        /type "allow"
    }
## Allow Dispatcher Cache for Screens offline manifests
/0003
    {
    /glob "/content/screens/*.manifest.json"
    /type "allow"
    }
## Allow Dispatcher Cache for Assets
/0004
    {
  
    /glob "/content/dam/*"
    /type "allow"
    }
## Disable Dispatcher Cache for Screens devices json
/0005
    {
    /glob "/home/users/screens/*.json"
    /type "deny"
    }
## Disable Dispatcher Cache for Screens svc json
/0006
    {
    /glob "/content/screens/svc.json"
    /type "deny"
    }
```
