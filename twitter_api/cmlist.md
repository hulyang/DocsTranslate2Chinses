# Create and manage lists
* [lists/show](#listsshow)
	* [接口资源信息](#接口资源信息)
	* [参数信息](#参数信息)
	* [响应内容](#响应内容)
* [lists/statuses](#listsstatuses)
	* [接口资源信息](#接口资源信息-1)
	* [参数信息](#参数信息-1)
	* [响应内容](#响应内容-1)
* [lists/create](#listscreate)
	* [接口资源信息](#接口资源信息-2)
	* [参数信息](#参数信息-2)
	* [响应内容](#响应内容-2)
* [lists/destroy](#listsdestroy)
	* [接口资源信息](#接口资源信息-3)
	* [参数信息](#参数信息-3)
	* [响应内容](#响应内容-3)
* [lists/update](#listsupdate)
	* [接口资源信息](#接口资源信息-4)
	* [参数信息](#参数信息-4)
	* [响应内容](#响应内容-4)

## lists/show

返回指定的list信息。__私有list必须为其拥有者才有权利查看该list。__

官方文档地址：
https://developer.twitter.com/en/docs/accounts-and-users/create-manage-lists/api-reference/get-lists-show

### 接口资源信息

|URL|https://api.twitter.com/1.1/lists/show.json|
|:------|:-----|
|Method|GET|
|响应格式|JSON|
|是否需要认证|是|
|是否有访问限制|是|
|请求次数/15-min|75|

### 参数信息

|参数名称|必要性|描述|默认值|
|:------|:------|:------|:------|
|list_id|必要|list的数字ID||
|slug|必要|list的slug(`list_id`&#124;`slug`二选一即可)||
|owner_screen_name|可选|list拥有者的账号名称||
|owner_id|可选|list拥有者的账号ID||

### 响应内容

指定list的详细信息（JSON格式）。
```
{
  "created_at": "Wed Sep 23 01:18:01 +0000 2009",
  "slug": "team",
  "name": "Team",
  "full_name": "@twitter/team",
  "description": "",
  "mode": "public",
  "following": false,
  "user": {
    "geo_enabled": true,
    "profile_background_image_url_https": "https://si0.twimg.com/images/themes/theme18/bg.gif",
    "profile_background_color": "ACDED6",
    "protected": false,
    "listed_count": 66019,
    "profile_background_tile": false,
    "created_at": "Tue Feb 20 14:35:54 +0000 2007",
    "friends_count": 695,
    "name": "Twitter",
    "profile_sidebar_fill_color": "F6F6F6",
    "notifications": false,
    "utc_offset": -28800,
    "profile_image_url_https": "https://si0.twimg.com/profile_images/1124040897/at-twitter_normal.png",
    "description": "Always wondering what's happening. ",
    "display_url": null,
    "following": false,
    "verified": true,
    "favourites_count": 16,
    "profile_sidebar_border_color": "EEEEEE",
    "followers_count": 6619092,
    "profile_image_url": "http://a0.twimg.com/profile_images/1124040897/at-twitter_normal.png",
    "default_profile_image": false,
    "contributors_enabled": true,
    "deactivated_bit": false,
    "statuses_count": 1218,
    "profile_use_background_image": true,
    "location": "San Francisco, CA",
    "id_str": "783214",
    "default_profile": false,
    "show_all_inline_media": true,
    "profile_text_color": "333333",
    "screen_name": "twitter",
    "follow_request_sent": false,
    "profile_background_image_url": "http://a1.twimg.com/images/themes/theme18/bg.gif",
    "url": "http://blog.twitter.com/",
    "expanded_url": null,
    "is_translator": false,
    "time_zone": "Pacific Time (US & Canada)",
    "profile_link_color": "038543",
    "id": 783214,
    "entities": {
      "urls": [],
      "user_mentions": [],
      "hashtags": []
    },
    "suspended": false,
    "lang": "en"
  },
  "member_count": 643,
  "id_str": "574",
  "subscriber_count": 76779,
  "id": 574,
  "uri": "/twitter/team"
}
```

## lists/statuses

展示指定的list中所有成员的推文时间轴，默认情况下包含转发，可通过`include_rts=false`参数来设置不包含转发。

官方文档地址：
https://developer.twitter.com/en/docs/accounts-and-users/create-manage-lists/api-reference/get-lists-show

### 接口资源信息

|URL|https://api.twitter.com/1.1/lists/statuses.json|
|:------|:-----|
|Method|GET|
|响应格式|JSON|
|是否需要认证|是|
|是否有访问限制|是|
|请求次数/15-min|900|

### 参数信息

|参数名称|必要性|描述|默认值|
|:------|:------|:------|:------|
|list_id|必要|list的数字ID||
|slug|必要|list的slug(`list_id`&#124;`slug`二选一即可)||
|owner_screen_name|可选|list拥有者的账号名称||
|owner_id|可选|list拥有者的账号ID||
|since_id|可选|返回推文ID最小值。<br/>返回ID大于指定的ID。<br/>API可返回的推文数量有限，如果数量超过上限，`since_id`将被强制设置成可获得的小ID<br>通俗来说就是会返回最新的那几条推文||
|max_id|可选|返回推文ID最大值。<br/>返回ID小于或等于指定的ID||
|count|可选|指定返回的结果数||
|include_entities|可选|是否包含`entities`信息。<br/>API1.1中默认为开启状态。<br/>每条推文都会包含一个名为`entities`的JSON对象，<br/>此对象提供了关于这条推文的各种元数据，包括：`user_mentions`,`urls`和`hashtags`。<br/>可以通过设置`include_entities=false` 来取消包含`entities`信息。||
|include_rts|可选|是否包含转发。<br/>当被设置为`true`,`t`或`1`时，会包含转发内容|true|

### 响应内容

指定ID范围 (`since_id`, `max_id`] 内的的所有推文时间轴(JSON数组格式)。
```
[
  {
    "coordinates": null,
    "created_at": "Mon Sep 10 14:04:58 +0000 2012",
    "truncated": false,
    "favorited": false,
    "id_str": "245160944223793152",
    "in_reply_to_user_id_str": null,
    "entities": {
      "urls": [
        {
          "expanded_url": "http://bit.ly/MuCCDo",
          "url": "http://t.co/W2tON3OK",
          "indices": [
            41,
            61
          ],
          "display_url": "bit.ly/MuCCDo"
        }
      ],
      "hashtags": [
        {
          "text": "TorontoFC",
          "indices": [
            87,
            97
          ]
        },
        {
          "text": "MLS",
          "indices": [
            98,
            102
          ]
        }
      ],
      "user_mentions": [
        {
          "name": "Team Up Foundation",
          "id_str": "210844741",
          "id": 210844741,
          "indices": [
            76,
            86
          ],
          "screen_name": "TeamUpFdn"
        }
      ]
    },
    "text": "Create your own TFC ESQ by Movado Watch: http://t.co/W2tON3OK in support of @TeamUpFdn #TorontoFC #MLS",
    "contributors": null,
    "id": 245160944223793152,
    "retweet_count": 0,
    "in_reply_to_status_id_str": null,
    "geo": null,
    "retweeted": false,
    "possibly_sensitive": false,
    "in_reply_to_user_id": null,
    "in_reply_to_screen_name": null,
    "source": "TweetDeck",
    "user": {
      "profile_sidebar_fill_color": "EB1D31",
      "profile_background_tile": false,
      "profile_sidebar_border_color": "FFFFFF",
      "name": "Toronto FC",
      "profile_image_url": "http://a0.twimg.com/profile_images/1827235104/TorontoFC1_normal.jpg",
      "created_at": "Fri Sep 11 15:42:26 +0000 2009",
      "location": "Toronto, ON",
      "follow_request_sent": false,
      "is_translator": false,
      "id_str": "73412535",
      "profile_link_color": "000000",
      "entities": {
        "url": {
          "urls": [
            {
              "expanded_url": null,
              "url": "http://www.torontofc.ca",
              "indices": [
                0,
                23
              ],
              "display_url": null
            }
          ]
        },
        "description": {
          "urls": [

          ]
        }
      },
      "favourites_count": 2,
      "url": "http://www.torontofc.ca",
      "default_profile": false,
      "contributors_enabled": false,
      "profile_image_url_https": "https://si0.twimg.com/profile_images/1827235104/TorontoFC1_normal.jpg",
      "utc_offset": -18000,
      "id": 73412535,
      "listed_count": 1078,
      "profile_use_background_image": true,
      "followers_count": 28281,
      "protected": false,
      "profile_text_color": "000000",
      "lang": "en",
      "profile_background_color": "BC1228",
      "verified": true,
      "time_zone": "Eastern Time (US & Canada)",
      "profile_background_image_url_https": "https://si0.twimg.com/profile_background_images/603424485/k9py0fm18qrjr8l22qlp.jpeg",
      "notifications": false,
      "description": "Official Toronto FC Twitter by @AsifinToronto & @JonSinden. Follow us for the latest club news, links, pics & videos. Join us during matches for #TFClive",
      "geo_enabled": false,
      "default_profile_image": false,
      "friends_count": 13947,
      "profile_background_image_url": "http://a0.twimg.com/profile_background_images/603424485/k9py0fm18qrjr8l22qlp.jpeg",
      "statuses_count": 10774,
      "screen_name": "torontofc",
      "following": true,
      "show_all_inline_media": false
    },
    "place": null,
    "in_reply_to_status_id": null
  }
]
```

## lists/create

创建一个新的list，__每个账号最多创建1000个。__

官方文档地址：
https://developer.twitter.com/en/docs/accounts-and-users/create-manage-lists/api-reference/post-lists-create

### 接口资源信息

|URL|https://api.twitter.com/1.1/lists/create.json|
|:------|:-----|
|Method|POST|
|响应格式|JSON|
|是否需要认证|是|
|是否有访问限制|是|

### 参数信息

|参数名称|必要性|描述|默认值|
|:------|:------|:------|:------|
|name|必要|list的名称||
|mode|可选|list访问权限(public&#124;private)|public||
|description|可选|list描述||

### 响应内容

所创建的list详细信息（JSON格式）。

```
{
   "created_at":"Fri Nov 04 21:22:36 +0000 2011",
   "slug":"goonies",
   "name":"Goonies",
   "full_name":"@kurrik/goonies",
   "description":"For life",
   "mode":"public",
   "following":false,
   "user":{
      "geo_enabled":true,
      "profile_background_image_url_https":"https://si0.twimg.com/profile_background_images/342542280/background7.png",
      "profile_background_color":"8fc1ff",
      "protected":false,
      "default_profile":false,
      "listed_count":127,
      "profile_background_tile":true,
      "created_at":"Thu Jul 19 15:58:07 +0000 2007",
      "friends_count":291,
      "name":"Arne Roomann-Kurrik",
      "profile_sidebar_fill_color":"c7e0ff",
      "notifications":false,
      "utc_offset":-28800,
      "profile_image_url_https":"https://si0.twimg.com/profile_images/24229162/arne001_normal.jpg",
      "description":"Developer Advocate at Twitter, practitioner of dark sandwich arts. ",
      "display_url":"roomanna.com",
      "following":false,
      "verified":false,
      "favourites_count":190,
      "profile_sidebar_border_color":"6baeff",
      "followers_count":1705,
      "profile_image_url":"http://a2.twimg.com/profile_images/24229162/arne001_normal.jpg",
      "default_profile_image":false,
      "contributors_enabled":false,
      "deactivated_bit":false,
      "statuses_count":1935,
      "profile_use_background_image":true,
      "location":"Scan Francesco",
      "id_str":"7588892",
      "show_all_inline_media":false,
      "profile_text_color":"000000",
      "screen_name":"kurrik",
      "follow_request_sent":false,
      "profile_background_image_url":"http://a2.twimg.com/profile_background_images/342542280/background7.png",
      "url":"http://t.co/SSiVavc4",
      "expanded_url":"http://roomanna.com",
      "is_translator":false,
      "time_zone":"Pacific Time (US & Canada)",
      "profile_link_color":"0084B4",
      "id":7588892,
      "entities":{
         "urls":[

         ],
         "user_mentions":[

         ],
         "hashtags":[

         ]
      },
      "suspended":false,
      "lang":"en"
   },
   "member_count":0,
   "id_str":"58300198",
   "subscriber_count":0,
   "id":58300198,
   "uri":"/kurrik/goonies"
}
```

## lists/destroy

删除指定list。__必须为list的拥有者才有权利删除该list。__

官方文档地址：
https://developer.twitter.com/en/docs/accounts-and-users/create-manage-lists/api-reference/post-lists-destroy

### 接口资源信息

|URL|https://api.twitter.com/1.1/lists/destroy.json|
|:------|:-----|
|Method|POST|
|响应格式|JSON|
|是否需要认证|是|
|是否有访问限制|是|

### 参数信息

|参数名称|必要性|描述|默认值|
|:------|:------|:------|:------|
|owner_screen_name|可选|list拥有者的账号名称||
|owner_id|可选|list拥有者的账号ID||
|list_id|必要|list数字ID||
|slug|必要|list的slug(`list_id`&#124;`slug`二选一即可)||

### 响应内容

所删除的list详细信息（JSON格式）。
```
{
   "created_at":"Fri Nov 04 21:22:36 +0000 2011",
   "slug":"goonies",
   "name":"Goonies",
   "full_name":"@kurrik/goonies",
   "description":"For life",
   "mode":"public",
   "following":false,
   "user":{
      "geo_enabled":true,
      "profile_background_image_url_https":"https://si0.twimg.com/profile_background_images/342542280/background7.png",
      "profile_background_color":"8fc1ff",
      "protected":false,
      "default_profile":false,
      "listed_count":127,
      "profile_background_tile":true,
      "created_at":"Thu Jul 19 15:58:07 +0000 2007",
      "friends_count":291,
      "name":"Arne Roomann-Kurrik",
      "profile_sidebar_fill_color":"c7e0ff",
      "notifications":false,
      "utc_offset":-28800,
      "profile_image_url_https":"https://si0.twimg.com/profile_images/24229162/arne001_normal.jpg",
      "description":"Developer Advocate at Twitter, practitioner of dark sandwich arts. ",
      "display_url":"roomanna.com",
      "following":false,
      "verified":false,
      "favourites_count":190,
      "profile_sidebar_border_color":"6baeff",
      "followers_count":1705,
      "profile_image_url":"http://a2.twimg.com/profile_images/24229162/arne001_normal.jpg",
      "default_profile_image":false,
      "contributors_enabled":false,
      "deactivated_bit":false,
      "statuses_count":1935,
      "profile_use_background_image":true,
      "location":"Scan Francesco",
      "id_str":"7588892",
      "show_all_inline_media":false,
      "profile_text_color":"000000",
      "screen_name":"kurrik",
      "follow_request_sent":false,
      "profile_background_image_url":"http://a2.twimg.com/profile_background_images/342542280/background7.png",
      "url":"http://t.co/SSiVavc4",
      "expanded_url":"http://roomanna.com",
      "is_translator":false,
      "time_zone":"Pacific Time (US & Canada)",
      "profile_link_color":"0084B4",
      "id":7588892,
      "entities":{
         "urls":[

         ],
         "user_mentions":[

         ],
         "hashtags":[

         ]
      },
      "suspended":false,
      "lang":"en"
   },
   "member_count":0,
   "id_str":"58300198",
   "subscriber_count":0,
   "id":58300198,
   "uri":"/kurrik/goonies"
}
```

## lists/update

修改指定list。必须为list的拥有者才有权利修改该list。

官方文档地址：
https://developer.twitter.com/en/docs/accounts-and-users/create-manage-lists/api-reference/post-lists-update

### 接口资源信息

|URL|https://api.twitter.com/1.1/lists/update.json|
|:------|:-----|
|Method|POST|
|响应格式|JSON|
|是否需要认证|是|
|是否有访问限制|是|

### 参数信息

|参数名称|必要性|描述|默认值|
|:------|:------|:------|:------|
|list_id|必要|list的数字ID||
|slug|必要|list的slug(`list_id`&#124;`slug`二选一即可)||
|name|可选|list的新名称||
|mode|可选|list新访问权限(public&#124;private)||
|description|可选|list的新描述||
|owner_screen_name|可选|list拥有者的账号名称||
|owner_id|可选|list拥有者的账号ID||

### 响应内容