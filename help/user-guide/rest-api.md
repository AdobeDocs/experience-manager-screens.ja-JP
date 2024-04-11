---
title: REST API
description: AEM Screensが Siren 仕様に準拠したシンプルな RESTful API を提供する方法について説明します。 また、コンテンツ構造内を移動する方法や、環境内のデバイスにコマンドを送信する方法についても説明します。
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: ac01935a-c3ff-485a-b60e-227fb94c75b0
source-git-commit: 43e89ddc3eb6baffca75d730a978e60e234aaee4
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 57%

---

# REST API{#rest-apis}

AEM Screens には、[Siren](https://github.com/kevinswiber/siren) の仕様に準拠するシンプルな RESTful API が用意されています。コンテンツ構造内を移動したり、環境内のデバイスにコマンドを送信したりできます。

この API には、[*http://localhost:4502/api/screens.json*](http://localhost:4502/api/screens.json) からアクセスできます。

## コンテンツ構造内での移動 {#navigating-content-structure}

API 呼び出しから返される JSON コードには、現在のリソースに関連するエンティティのリストが記述されています。リストに表示されたセルフリンクの後、これらの各エンティティは、REST リソースとして再びアクセスできます。

例えば、デモのフラッグシップの場所のディスプレイにアクセスするには、次を呼び出します。

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship.json HTTP/1.1
Host: http://localhost:4502
```

または、次のように curl を使用します。

```xml
curl -u admin:admin http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship.json
```

結果は以下のようになります。

```xml
{
  "class": [
    "aem-io/screens/location"
  ],
  "links": [
    {
      "rel": [
        "self"
      ],
      "href": "http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship.json"
    },
    {
      "rel": [
        "parent"
      ],
      "href": "http://localhost:4502/api/screens/content/screens/we-retail/locations/demo.json"
    }
  ],
  "properties": {…},
  "entities": [
    {
      "class": [
        "aem-io/screens/display"
      ],
      "links": [
        {
          "rel": [
            "self"
          ],
          "href": "http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json"
        }
      ],
      "rel": [
        "child"
      ],
      "properties": {
        "title": "Single Screen Display",
        "height": 1440,
        "description": "Demo location of a single screen display.",
        "name": "single",
        "width": 2560,
        "idletimeout": 300,
        "layoutrows": 1,
        "layoutcols": 1
      }
    },
    …
  ]
}
```

その後、単一のスクリーンディスプレイにアクセスするには、次の呼び出しをおこないます。

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502
```

## リソースに対するアクションの実行 {#executing-actions-on-the-resource}

API 呼び出しで返される JSON コードには、リソースに対して使用可能なアクションのリストを含めることができます。

例えば、このディスプレイでは、割り当てられているすべてのデバイスへのコマンド送信を許可する *broadcast-command* アクションがリストされています。

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502
```

または、次のように curl を使用します。

```xml
curl -u admin:admin http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json
```

***結果:***

```xml
{
  "class": [
    "aem-io/screens/display"
  ],
  "links": […],
  "properties": {…},
  "entities": […],
  "actions": [
    {
      "title": "",
      "name": "broadcast-command",
      "method": "POST",
      "href": "/api/screens/content/screens/we-retail/locations/demo/flagship/single",
      "fields": [
        {
          "name": ":operation",
          "value": "broadcast-command",
          "type": "hidden"
        },
        {
          "name": "msg",
          "type": "text"
        }
      ]
    }
  ]
}
```

このアクションをトリガーするには、以下を呼び出します。

```xml
POST /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502

:operation=broadcast-command&msg=reboot
```

または、次のように curl を使用します。

```xml
curl -u admin:admin -X POST -d ':operation=broadcast-command&msg=reboot' http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json
```
