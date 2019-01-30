# Follow, search, and get users

<!-- @import "[TOC]" {cmd="toc" depthFrom=2 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

* [followers/ids](#followersids)
	* [接口资源信息](#接口资源信息)
	* [参数信息](#参数信息)
	* [响应内容](#响应内容)
* [followers/list](#followerslist)
	* [接口资源信息](#接口资源信息-1)
	* [参数信息](#参数信息-1)
	* [响应内容](#响应内容-1)
* [friends/ids](#friendsids)
	* [接口资源信息](#接口资源信息-2)
	* [参数信息](#参数信息-2)
	* [响应内容](#响应内容-2)
* [friends/list](#friendslist)
	* [接口资源信息](#接口资源信息-3)
	* [参数信息](#参数信息-3)
	* [响应内容](#响应内容-3)
* [friendships/incoming](#friendshipsincoming)
	* [接口资源信息](#接口资源信息-4)
	* [参数信息](#参数信息-4)
	* [响应内容](#响应内容-4)
* [friendships/lookup](#friendshipslookup)
	* [接口资源信息](#接口资源信息-5)
	* [参数信息](#参数信息-5)
	* [响应内容](#响应内容-5)
* [friendships/no_retweets/ids](#friendshipsno_retweetsids)
	* [接口资源信息](#接口资源信息-6)
	* [参数信息](#参数信息-6)
	* [响应内容](#响应内容-6)
* [friendships/outgoing](#friendshipsoutgoing)
	* [接口资源信息](#接口资源信息-7)
	* [参数信息](#参数信息-7)
	* [响应内容](#响应内容-7)
* [friendships/show](#friendshipsshow)
	* [接口资源信息](#接口资源信息-8)
	* [参数信息](#参数信息-8)
	* [响应内容](#响应内容-8)
* [users/lookup](#userslookup)
	* [接口资源信息](#接口资源信息-9)
	* [参数信息](#参数信息-9)
	* [响应内容](#响应内容-9)
* [users/search](#userssearch)
	* [接口资源信息](#接口资源信息-10)
	* [参数信息](#参数信息-10)
	* [响应内容](#响应内容-10)
* [users/show](#usersshow)
	* [接口资源信息](#接口资源信息-11)
	* [参数信息](#参数信息-11)
	* [响应内容](#响应内容-11)
* [users/suggestions](#userssuggestions)
	* [接口资源信息](#接口资源信息-12)
	* [参数信息](#参数信息-12)
	* [响应内容](#响应内容-12)
* [users/suggestions/:slug](#userssuggestionsslug)
	* [接口资源信息](#接口资源信息-13)
	* [参数信息](#参数信息-13)
	* [响应内容](#响应内容-13)
* [users/suggestions/:slug/members](#userssuggestionsslugmembers)
	* [接口资源信息](#接口资源信息-14)
	* [参数信息](#参数信息-14)
	* [响应内容](#响应内容-14)

<!-- /code_chunk_output -->

## followers/ids

返回指定用户的所有粉丝ID的集合。并包含游标信息。

目前，返回的结果会按照最新关注的顺序进行排序。但是，这一顺序会受到突然变更以及最终一致性的影响。结果会返回一个5000名用户ID的集合，并且分成多页，你可以使用`next_cursor`去请求下一页。查看[Using cursors to navigate collections](https://developer.twitter.com/en/docs/basics/cursoring)获取更多关于游标(`cursor`)的信息。

此方法搭配[GET users/lookup](#userslookup)使用时则会显得特别强大，该方法支持批量的将用户ID转化为用户的详细信息。

官方文档地址：
https://developer.twitter.com/en/docs/accounts-and-users/follow-search-get-users/api-reference/get-followers-ids

### 接口资源信息

|URL|https://api.twitter.com/1.1/followers/ids.json|
|:------|:-----|
|Method|GET|
|响应格式|JSON|
|是否需要认证|是|
|是否有访问限制|是|
|请求次数/15-min (user auth)|15|
|请求次数/15-min (app ahth)|15|

### 参数信息

|参数名称|必要性|描述|默认值|
|:------|:------|:------|:------|
|user_id|可选|用于获取结果的用户id。||
|screen_name|可选|用于获取结果的用户昵称。||
|cursor|半可选|将结果集进行分页，并且保证每页结果数量不超过5000条。由于会过滤掉请求挂起的用户，所以返回的用户ID数量不能保证有5000条。若未指明`cursor`的值，默认值为`-1`，表示查询首页。<br/>响应的结果中将会包含`previous_cursor`和`next_cursor`以支持我们来回翻页。查看[Using cursors to navigate collections](https://developer.twitter.com/en/docs/basics/cursoring)获取更多关于游标(`cursor`)的信息|-1|
|stringify_ids|可选|字符串类型的ID。<br/>某些程序环境由于其大小，不能处理Twitter ID，提供此选项允许将ID按字符串类型返回。查看[Twitter IDs](https://developer.twitter.com/en/docs/basics/twitter-ids)获取更多相关信息。||
|count|可选|指定返回的ID数量。每次请求最多返回5000条。`count`值为范围会结果数的最大限制。当你在本方法中使用了`count`这一参数时，需保证对统一用户ID集合的所有请求为统一的`count`。推荐最大设置为5000。||

### 响应内容

包含用户ID集合以及相应的游标信息。

```
{
    "ids": [
        455974794,
        947576438684872705,
        850839346009780224,
        958850376630910976,
        889483959943536640,
        966094285119606784,
        1020583045,
        948604640811212801,
        967155179614240768,
        554514802,
        14873932,
        963916668731904000,
        970763391181746178,
        966091392631140358,
        .
        .
        .
        5000 ids later,
        .
        .
        .
        813143846,
        958604886735716353,
        402873729,
        958603486551330817,
        913076424897994753,
        820967329068707840,
        958593574932762624,
        958589381102665728,
        958573223737724929,
        889474485694410752
    ],
    "next_cursor": 1591087837626119954,
    "next_cursor_str": "1591087837626119954",
    "previous_cursor": 0,
    "previous_cursor_str": "0"
}
```

## followers/list

返回指定用户的所有粉丝信息用户信息的集合。并包含游标信息。

目前，返回的结果会按照最新关注的顺序进行排序。但是，这一顺序会受到突然变更以及最终一致性的影响。结果会返回一个20名用户的集合，并且分成多页，你可以使用`next_cursor`去请求下一页。查看[Using cursors to navigate collections](https://developer.twitter.com/en/docs/basics/cursoring)获取更多关于游标(`cursor`)的信息。

官方文档地址：
https://developer.twitter.com/en/docs/accounts-and-users/follow-search-get-users/api-reference/get-followers-list

### 接口资源信息

|URL|https://api.twitter.com/1.1/followers/list.json|
|:------|:-----|
|Method|GET|
|响应格式|JSON|
|是否需要认证|是|
|是否有访问限制|是|
|请求次数/15-min (user auth)|15|
|请求次数/15-min (app ahth)|15|

### 参数信息

|参数名称|必要性|描述|默认值|
|:------|:------|:------|:------|
|user_id|可选|用于获取结果的用户id。||
|screen_name|可选|用于获取结果的用户昵称。||
|cursor|半可选|将结果集进行分页，若未指明`cursor`的值，默认值为`-1`，表示查询首页。<br/>响应的结果中将会包含`previous_cursor`和`next_cursor`以支持我们来回翻页。查看[Using cursors to navigate collections](https://developer.twitter.com/en/docs/basics/cursoring)获取更多关于游标(`cursor`)的信息|-1|
|count|可选|每页返回的结果数量，默认为20条，最大值为200条。|20|
|skip_status|可选|用户对象中不包含status信息。<br/>当被设置为`true`、`t`或`1`时，用户对象中将不包含status信息|false|
|include_user_entities|可选|是否包含用户`entities`信息。<br/>可以通过设置`include_entities=false` 来取消包含`entities`信息。|true|

### 响应内容

包含用户完整信息集合以及相应的游标信息。

```
{
  "users": [
      {user-object},
      {user-object},
      {user-object}
  ],
  "next_cursor": 1489467234237774933,
  "next_cursor_str": "1489467234237774933",
  "previous_cursor": 0,
  "previous_cursor_str": "0"
}
```

## friends/ids

返回指定用户的所有关注账号ID的集合。并包含游标信息。

目前，返回的结果会按照最新关注的顺序进行排序。但是，这一顺序会受到突然变更以及最终一致性的影响。结果会返回一个5000名用户ID的集合，并且分成多页，你可以使用`next_cursor`去请求下一页。查看[Using cursors to navigate collections](https://developer.twitter.com/en/docs/basics/cursoring)获取更多关于游标(`cursor`)的信息。

此方法搭配[GET users/lookup](#userslookup)使用时则会显得特别强大，该方法支持批量的将用户ID转化为用户的详细信息。

官方文档地址：
https://developer.twitter.com/en/docs/accounts-and-users/follow-search-get-users/api-reference/get-friends-ids

### 接口资源信息

|URL|https://api.twitter.com/1.1/friends/ids.json|
|:------|:-----|
|Method|GET|
|响应格式|JSON|
|是否需要认证|是|
|是否有访问限制|是|
|请求次数/15-min (user auth)|15|
|请求次数/15-min (app ahth)|15|

### 参数信息

|参数名称|必要性|描述|默认值|
|:------|:------|:------|:------|
|user_id|可选|用于获取结果的用户id。||
|screen_name|可选|用于获取结果的用户昵称。||
|cursor|半可选|将结果集进行分页，并且保证每页结果数量不超过5000条。由于会过滤掉请求挂起的用户，所以返回的用户ID数量不能保证有5000条。若未指明`cursor`的值，默认值为`-1`，表示查询首页。<br/>响应的结果中将会包含`previous_cursor`和`next_cursor`以支持我们来回翻页。查看[Using cursors to navigate collections](https://developer.twitter.com/en/docs/basics/cursoring)获取更多关于游标(`cursor`)的信息|-1|
|stringify_ids|可选|字符串类型的ID。<br/>某些程序环境由于其大小，不能处理Twitter ID，提供此选项允许将ID按字符串类型返回。查看[Twitter IDs](https://developer.twitter.com/en/docs/basics/twitter-ids)获取更多相关信息。||
|count|可选|指定返回的ID数量。每次请求最多返回5000条。`count`值为范围会结果数的最大限制。当你在本方法中使用了`count`这一参数时，需保证对统一用户ID集合的所有请求为统一的`count`。推荐最大设置为5000。||

### 响应内容

包含用户ID集合以及相应的游标信息。

```
{
  "previous_cursor": 0,
  "ids": [
    657693,
    183709371,
    7588892,
    38895958,
    22891211,
    9019482,
    14488353,
    11750202,
    12249,
    22915745,
    1249881,
    14927800,
    1523501,
    22548447,
    15062340,
    133031077,
    17874544,
    777925,
    4265731,
    27674040,
    26123649,
    9576402,
    821958,
    7852612,
    819797,
    1401881,
    8285392,
    9160152,
    795649,
    3191321,
    783214
  ],
  "previous_cursor_str": "0",
  "next_cursor": 0,
  "next_cursor_str": "0"
}
```

## friends/list

返回指定用户的所有关注账号信息用户信息的集合。并包含游标信息。

目前，返回的结果会按照最新关注的顺序进行排序。但是，这一顺序会受到突然变更以及最终一致性的影响。结果会返回一个20名用户的集合，并且分成多页，你可以使用`next_cursor`去请求下一页。查看[Using cursors to navigate collections](https://developer.twitter.com/en/docs/basics/cursoring)获取更多关于游标(`cursor`)的信息。

官方文档地址：
https://developer.twitter.com/en/docs/accounts-and-users/follow-search-get-users/api-reference/get-friends-list

### 接口资源信息

|URL|https://api.twitter.com/1.1/friends/list.json|
|:------|:-----|
|Method|GET|
|响应格式|JSON|
|是否需要认证|是|
|是否有访问限制|是|
|请求次数/15-min (user auth)|15|
|请求次数/15-min (app ahth)|15|

### 参数信息

|参数名称|必要性|描述|默认值|
|:------|:------|:------|:------|
|user_id|可选|用于获取结果的用户id。||
|screen_name|可选|用于获取结果的用户昵称。||
|cursor|半可选|将结果集进行分页，并且保证每页结果数量不超过5000条。若未指明`cursor`的值，默认值为`-1`，表示查询首页。<br/>响应的结果中将会包含`previous_cursor`和`next_cursor`以支持我们来回翻页。查看[Using cursors to navigate collections](https://developer.twitter.com/en/docs/basics/cursoring)获取更多关于游标(`cursor`)的信息|-1|
|count|可选|每页返回的结果数量，默认为20条，最大值为200条。|20|
|skip_status|可选|用户对象中不包含status信息。<br/>当被设置为`true`、`t`或`1`时，用户对象中将不包含status信息|false|
|include_user_entities|可选|是否包含用户`entities`信息。<br/>可以通过设置`include_entities=false` 来取消包含`entities`信息。|true|

### 响应内容

包含用户完整信息集合以及相应的游标信息。

```
{
"users": [
      {user-object},
      {user-object},
      {user-object}
  ],
  "previous_cursor": 0,
  "previous_cursor_str": "0",
  "next_cursor": 1333504313713126852,
  "next_cursor_str": "1333504313713126852"
}
```

## friendships/incoming

返回对当前认证账号，发起关注请求，但请求仍在处理的用户ID集合。

官方文档地址：
https://developer.twitter.com/en/docs/accounts-and-users/follow-search-get-users/api-reference/get-friendships-incoming

### 接口资源信息

|URL|https://api.twitter.com/1.1/friendships/incoming.json|
|:------|:-----|
|Method|GET|
|响应格式|JSON|
|是否需要认证|是|
|是否有访问限制|是|
|请求次数/15-min (user auth)|15|

### 参数信息

|参数名称|必要性|描述|默认值|
|:------|:------|:------|:------|
|cursor|半可选|将结果集进行分页，并且保证每页结果数量不超过5000条。由于会过滤掉请求通过的用户，所以返回的用户ID数量不能保证有5000条。若未指明`cursor`的值，默认值为`-1`，表示查询首页。<br/>响应的结果中将会包含`previous_cursor`和`next_cursor`以支持我们来回翻页。|-1|
|stringify_ids|可选|字符串类型的ID。<br/>某些程序环境由于其大小，不能处理Twitter ID，提供此选项允许将ID按字符串类型返回。||

### 响应内容

包含用户ID集合以及相应的游标信息。

```
{
  "previous_cursor": 0,
  "ids": [

  ],
  "previous_cursor_str": "0",
  "next_cursor": 0,
  "next_cursor_str": "0"
}
```

## friendships/lookup

返回当前用于与指定至多100名用户（通过英文半角逗号`,`隔开的`screen_name`或`user_id`）之间的关系。响应中字段`connections`的值包含：`following`, `following_requested`, `followed_by`, `none`, `blocking`, `muting`。

官方文档地址：
https://developer.twitter.com/en/docs/accounts-and-users/follow-search-get-users/api-reference/get-friendships-lookup

### 接口资源信息

|URL|https://api.twitter.com/1.1/friendships/lookup.json|
|:------|:-----|
|Method|GET|
|响应格式|JSON|
|是否需要认证|是|
|是否有访问限制|是|
|请求次数/15-min (user auth)|15|

### 参数信息

|参数名称|必要性|描述|默认值|
|:------|:------|:------|:------|
|screen_name|可选|使用英文半角逗号(`,`)隔开的用户昵称集合，单次请求最多提交100个||
|user_id|可选|使用英文半角逗号(`,`)隔开的用户ID集合，单次请求最多提交100个||

### 响应内容

指定用户的简要信息以及与认证账号之间的关系信息(JSON数组)。

```
[
  {
    "name": "andy piper (pipes)",
    "screen_name": "andypiper",
    "id": 786491,
    "id_str": "786491",
    "connections": [
      "following"
    ]
  },
  {
    "name": "λ🥑. 🍞",
    "screen_name": "binary_aaron",
    "id": 165837734,
    "id_str": "165837734",
    "connections": [
      "following",
      "followed_by"
    ]
  },
  {
    "name": "Twitter Dev",
    "screen_name": "TwitterDev",
    "id": 2244994945,
    "id_str": "2244994945",
    "connections": [
      "following"
    ]
  },
  {
    "name": "Emily Sheehan 🏕",
    "screen_name": "happycamper",
    "id": 63046977,
    "id_str": "63046977",
    "connections": [
      "none"
    ]
  },
  {
    "name": "Harrison Test",
    "screen_name": "Harris_0ff",
    "id": 4337869213,
    "id_str": "4337869213",
    "connections": [
      "following",
      "following_requested",
      "followed_by"
    ]
  }
]
```

## friendships/no_retweets/ids

返回当前认证账号所拒收转发请求的账号ID集合。
使用[POST friendships/update](#friendshipsupdate)可以对指定账号设置"不允许转发"当前账号的状态。

官方文档地址：
https://developer.twitter.com/en/docs/accounts-and-users/follow-search-get-users/api-reference/get-friendships-lookup

### 接口资源信息

|URL|https://api.twitter.com/1.1/friendships/no_retweets/ids.json|
|:------|:-----|
|Method|GET|
|响应格式|JSON|
|是否需要认证|是|
|是否有访问限制|是|
|请求次数/15-min (user auth)|15|

### 参数信息

|参数名称|必要性|描述|默认值|
|:------|:------|:------|:------|
|stringify_ids|可选|字符串类型的ID。<br/>某些程序环境由于其大小，不能处理Twitter ID，提供此选项允许将ID按字符串类型返回。查看[Twitter IDs](https://developer.twitter.com/en/docs/basics/twitter-ids)获取更多相关信息。这一参数在JavaScript环境下及其重要。||

### 响应内容

用户账号ID数组。

```
["777925","732321"]
```

## friendships/outgoing

返回当前认证账号，对外发起的关注请求，但请求仍在处理的用户ID集合。

官方文档地址：
https://developer.twitter.com/en/docs/accounts-and-users/follow-search-get-users/api-reference/get-friendships-outgoing

### 接口资源信息

|URL|https://api.twitter.com/1.1/friendships/outgoing.json|
|:------|:-----|
|Method|GET|
|响应格式|JSON|
|是否需要认证|是|
|是否有访问限制|是|
|请求次数/15-min (user auth)|15|

### 参数信息

|参数名称|必要性|描述|默认值|
|:------|:------|:------|:------|
|cursor|半可选|将结果集进行分页，并且保证每页结果数量不超过5000条。由于会过滤掉请求通过的用户，所以返回的用户ID数量不能保证有5000条。若未指明`cursor`的值，默认值为`-1`，表示查询首页。<br/>响应的结果中将会包含`previous_cursor`和`next_cursor`以支持我们来回翻页。查看[Using cursors to navigate collections](https://developer.twitter.com/en/docs/basics/cursoring)获取更多关于游标(`cursor`)的信息|-1|
|stringify_ids|可选|字符串类型的ID。<br/>某些程序环境由于其大小，不能处理Twitter ID，提供此选项允许将ID按字符串类型返回。查看[Twitter IDs](https://developer.twitter.com/en/docs/basics/twitter-ids)获取更多相关信息||

### 响应内容

包含用户ID集合以及相应的游标信息。

```
{
  "previous_cursor": 0,
  "ids": [
    51937528,
    124856868,
    213246307,
    89356977,
    121177351,
    113338333,
    59520091,
    46451699,
    98223312,
    18172433,
    32210115,
    36851055,
    81269257
  ],
  "previous_cursor_str": "0",
  "next_cursor": 0,
  "next_cursor_str": "0"
}
```

## friendships/show

返回任意两个用户之间的详细关系信息。

官方文档地址：
https://developer.twitter.com/en/docs/accounts-and-users/follow-search-get-users/api-reference/get-friendships-show

### 接口资源信息

|URL|https://api.twitter.com/1.1/friendships/show.json|
|:------|:-----|
|Method|GET|
|响应格式|JSON|
|是否需要认证|是|
|是否有访问限制|是|
|请求次数/15-min (user auth)|180|
|请求次数/15-min (app auth)|15|

### 参数信息

|参数名称|必要性|描述|默认值|
|:------|:------|:------|:------|
|source_id|可选|主用户的ID||
|source_screen_name|可选|主用户的昵称||
|target_id|可选|目标用户ID||
|target_screen_name|可选|目标用户昵称||

### 响应内容

主用户与目标用户之间的详细关系信息（JSON格式）。

```
{
  "relationship": {
    "target": {
      "id_str": "12148",
      "id": 12148,
      "screen_name": "ernie",
      "following": false,
      "followed_by": false
    },
    "source": {
      "can_dm": false,
      "blocking": null,
      "muting": null,
      "id_str": "8649302",
      "all_replies": null,
      "want_retweets": null,
      "id": 8649302,
      "marked_spam": null,
      "screen_name": "bert",
      "following": false,
      "followed_by": false,
      "notifications_enabled": null
    }
  }
}
```

## users/lookup

返回指定（通过英文半角逗号`,`分割的`user_id`或`screen_name`）的完整的[用户信息](https://developer.twitter.com/en/docs/tweets/data-dictionary/overview/user-object)集合，单次请求最多返回100个。

此接口配合[GET friends/ids](#friendsids)或[GET followers/ids](#followersids)所返回的用户ID集合去使用时，效果甚佳。

[GET users/show](#usersshow)接口是用来返回单个用户信息的。

调用此接口需要注意以下事项：

- 必须要关注了受保护用户才能看到该用户的推文更新，否则其推文信息将被移除。
- 返回的用户信息顺序与请求中ID或昵称顺序不一定一致。
- 如果请求中的某个用户不存在、被冻结、已删除的话是不会被返回。
- 如果没有满足查询条件的用户信息，则会返回HTTP 404。
- 强烈建议请求信息大的时候使用POST请求

官方文档地址：
https://developer.twitter.com/en/docs/accounts-and-users/follow-search-get-users/api-reference/get-users-lookup

### 接口资源信息

|URL|https://api.twitter.com/1.1/users/lookup.json|
|:------|:-----|
|Method|GET|
|响应格式|JSON|
|是否需要认证|是|
|是否有访问限制|是|
|请求次数/15-min (user auth)|900|
|请求次数/15-min (app auth)|300|

### 参数信息

|参数名称|必要性|描述|默认值|
|:------|:------|:------|:------|
|screen_name|可选|使用英文半角逗号(`,`)隔开的用户昵称集合，单次请求最多100个。请求量大的时候强烈建议使用POST请求||
|user_id|可选|使用英文半角逗号(`,`)隔开的用户ID集合，单次请求最多100个。请求量大的时候强烈建议使用POST请求||
|include_entities|可选|是否包含`entities`节点。可以通过设置`include_entities=false`来取消包含该节点。||
|tweet_mode|可选|推文展示模式（`compat`&#124;`extended`）||

### 响应内容

用户信息集合（JSON数组）。

```
[
  {
    {user-object},
    {user-object}
  }
]
```

## users/search

为Twitter账号提供一个简单的，基于相关性的搜索接口。查询会基于兴趣、昵称、公司名称、位置或一些其他标准。不支持完全匹配搜索。

仅返回前1000条匹配结果。

官方文档地址：
https://developer.twitter.com/en/docs/accounts-and-users/follow-search-get-users/api-reference/get-users-search

### 接口资源信息

|URL|https://api.twitter.com/1.1/users/search.json|
|:------|:-----|
|Method|GET|
|响应格式|JSON|
|是否需要认证|是|
|是否有访问限制|是|
|请求次数/15-min (user auth)|900|

### 参数信息

|参数名称|必要性|描述|默认值|
|:------|:------|:------|:------|
|q|必要|用于账号搜索的关键词||
|page|可选|指定分页页码||
|count|可选|每页返回的账号信息条数，最大值为20||
|include_entities|可选|是否包含`entities`节点。可以通过设置`include_entities=false`来取消包含该节点。||

### 响应内容

匹配到的账号信息集合（JSON数组）

```
[
  {user-object},
  {user-object}
]
```

## users/show

返回参数`user_id`或`screen_name`指定的[用户信息](https://developer.twitter.com/en/docs/tweets/data-dictionary/overview/user-object)，该用户的最新推文也可能包含在内。

[GET users/lookup](#userslookup)可用来批量返回用户信息。

必须要关注了受保护用户才能看到该用户的推文更新，否则其推文信息将被移除。最新的推文不一定会返回。

官方文档地址：
https://developer.twitter.com/en/docs/accounts-and-users/follow-search-get-users/api-reference/get-users-show

### 接口资源信息

|URL|https://api.twitter.com/1.1/users/show.json|
|:------|:-----|
|Method|GET|
|响应格式|JSON|
|是否需要认证|是|
|是否有访问限制|是|
|请求次数/15-min (user auth)|900|
|请求次数/15-min (app auth)|900|

### 参数信息

|参数名称|必要性|描述|默认值|
|:------|:------|:------|:------|
|user_id|必要|用于账号搜索的关键词||
|screen_name|可选|指定分页页码||
|include_entities|可选|是否包含`entities`节点。可以通过设置`include_entities=false`来取消包含该节点。||

### 响应内容

Twitter账号[详细信息](https://developer.twitter.com/en/docs/tweets/data-dictionary/overview/user-object)。

```
{user-object}
```

## users/suggestions

访问Twitter用户推荐列表。将会返回推荐的用户类别集合。这些类别可用来调用[GET users/suggestions/:slug](#users/suggestions/:slug)来获取该类别下的推荐用户信息。

官方文档地址：
https://developer.twitter.com/en/docs/accounts-and-users/follow-search-get-users/api-reference/get-users-suggestions

### 接口资源信息

|URL|https://api.twitter.com/1.1/users/suggestions.json|
|:------|:-----|
|Method|GET|
|响应格式|JSON|
|是否需要认证|是|
|是否有访问限制|是|
|请求次数/15-min (user auth)|15|
|请求次数/15-min (app auth)|15|

### 参数信息

|参数名称|必要性|描述|默认值|
|:------|:------|:------|:------|
|lang|可选|语种。指定建议类别的语种。该语种必须遵循双字母ISO 639-1的规定。可以调用[GET help/languages](https://developer.twitter.com/en/docs/accounts-and-users/follow-search-get-users/api-reference/get-users-suggestions)查看目前支持的语种。不支持的语种将会按英语(en)返回。如果你在此接口中使用了此参数，须确保在调用[GET users/suggestions/:slug](#userssuggestionsslug)时也包含此参数。||

### 响应内容

推荐的分类集合（JSON数组）。

```
[
  {
    "name": "Art & Design",
    "slug": "art-design",
    "size": 20
  },
  {
    "name": "Billboard Music Awards",
    "slug": "billboard-music-awards",
    "size": 20
  },
  {
    "name": "Books",
    "slug": "books",
    "size": 20
  },
  {
    "name": "Business",
    "slug": "business",
    "size": 20
  },
  {
    "name": "CMT Awards",
    "slug": "cmt-awards",
    "size": 20
  },
  {
    "name": "Charity",
    "slug": "charity",
    "size": 20
  },
  {
    "name": "Entertainment",
    "slug": "entertainment",
    "size": 20
  },
  {
    "name": "Faith and Religion",
    "slug": "faith-and-religion",
    "size": 20
  },
  {
    "name": "Family",
    "slug": "family",
    "size": 20
  },
  {
    "name": "Fashion",
    "slug": "fashion",
    "size": 20
  },
  {
    "name": "Food & Drink",
    "slug": "food-drink",
    "size": 20
  },
  {
    "name": "Funny",
    "slug": "funny",
    "size": 20
  },
  {
    "name": "Government",
    "slug": "government",
    "size": 20
  },
  {
    "name": "Health",
    "slug": "health",
    "size": 20
  },
  {
    "name": "MLB",
    "slug": "mlb",
    "size": 20
  },
  {
    "name": "MTV Movie Awards",
    "slug": "mtv-movie-awards",
    "size": 20
  },
  {
    "name": "Music",
    "slug": "music",
    "size": 20
  },
  {
    "name": "NASCAR",
    "slug": "nascar",
    "size": 20
  },
  {
    "name": "NBA",
    "slug": "nba",
    "size": 20
  },
  {
    "name": "NHL",
    "slug": "nhl",
    "size": 20
  },
  {
    "name": "News",
    "slug": "news",
    "size": 20
  },
  {
    "name": "PGA",
    "slug": "pga",
    "size": 20
  },
  {
    "name": "Science",
    "slug": "science",
    "size": 20
  },
  {
    "name": "Sports",
    "slug": "sports",
    "size": 20
  },
  {
    "name": "Staff Picks",
    "slug": "staff-picks",
    "size": 20
  },
  {
    "name": "Technology",
    "slug": "technology",
    "size": 20
  },
  {
    "name": "Television",
    "slug": "television",
    "size": 20
  },
  {
    "name": "Travel",
    "slug": "travel",
    "size": 20
  },
  {
    "name": "Twitter",
    "slug": "twitter",
    "size": 20
  },
  {
    "name": "US Election 2012",
    "slug": "us-election-2012",
    "size": 20
  }
]
```

## users/suggestions/:slug

访问指定类别中的Twitter推荐用户信息。

建议程序缓存此数据的时间不要超过1小时。

官方文档地址：
https://developer.twitter.com/en/docs/accounts-and-users/follow-search-get-users/api-reference/get-users-suggestions-slug

### 接口资源信息

|URL|https://api.twitter.com/1.1/users/suggestions/:slug.json|
|:------|:-----|
|Method|GET|
|响应格式|JSON|
|是否需要认证|是|
|是否有访问限制|是|
|请求次数/15-min (user auth)|15|
|请求次数/15-min (app auth)|15|

### 参数信息

|参数名称|必要性|描述|默认值|
|:------|:------|:------|:------|
|slug|必要|分类的简称||
|lang|可选|语种。指定建议类别的语种。该语种必须遵循双字母ISO 639-1的规定。可以调用[GET help/languages](https://developer.twitter.com/en/docs/accounts-and-users/follow-search-get-users/api-reference/get-users-suggestions)查看目前支持的语种。不支持的语种将会按英语(en)返回。如果你在此接口中使用了此参数，须确保在调用[GET users/suggestions](#userssuggestions)时也包含此参数。||

### 响应内容

该推荐分类的详细信息，包含推荐的用户集合。

```
{
  "name": "Twitter",
  "slug": "twitter",
  "size": 20,
  "users": [
    {user-object},
    {user-object},
    {user-object}
  ]
}
```

## users/suggestions/:slug/members

访问指定类别中的Twitter推荐用户信息，如果该用户不是受保护的用户，则会同时返回其最新的推文信息。

官方文档地址：
https://developer.twitter.com/en/docs/accounts-and-users/follow-search-get-users/api-reference/get-users-suggestions-slug-members

### 接口资源信息

|URL|https://api.twitter.com/1.1/users/suggestions/:slug/members.json|
|:------|:-----|
|Method|GET|
|响应格式|JSON|
|是否需要认证|是|
|是否有访问限制|是|
|请求次数/15-min (user auth)|15|
|请求次数/15-min (app auth)|15|

### 参数信息

|参数名称|必要性|描述|默认值|
|:------|:------|:------|:------|
|slug|必要|分类的简称||

### 响应内容

包含推荐的用户信息集合（JSON数组）。

```
[
  {user-object,
    "status": {tweet-object}
  },
  {user-object,
    "status": {tweet-object}
  }
]
```