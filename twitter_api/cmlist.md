# Create and manage lists

<!-- @import "[TOC]" {cmd="toc" depthFrom=2 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

* [lists/list](#listslist)
	* [接口资源信息](#接口资源信息)
	* [参数信息](#参数信息)
	* [响应内容](#响应内容)
* [lists/members](#listsmembers)
	* [接口资源信息](#接口资源信息-1)
	* [参数信息](#参数信息-1)
	* [响应内容](#响应内容-1)
* [lists/members/show](#listsmembersshow)
	* [接口资源信息](#接口资源信息-2)
	* [参数信息](#参数信息-2)
	* [响应内容](#响应内容-2)
* [lists/memberships](#listsmemberships)
	* [接口资源信息](#接口资源信息-3)
	* [参数信息](#参数信息-3)
	* [响应内容](#响应内容-3)
* [lists/ownerships](#listsownerships)
	* [接口资源信息](#接口资源信息-4)
	* [参数信息](#参数信息-4)
	* [响应内容](#响应内容-4)
* [lists/show](#listsshow)
	* [接口资源信息](#接口资源信息-5)
	* [参数信息](#参数信息-5)
	* [响应内容](#响应内容-5)
* [lists/statuses](#listsstatuses)
	* [接口资源信息](#接口资源信息-6)
	* [参数信息](#参数信息-6)
	* [响应内容](#响应内容-6)
* [lists/subscribers](#listssubscribers)
	* [接口资源信息](#接口资源信息-7)
	* [参数信息](#参数信息-7)
	* [响应内容](#响应内容-7)
* [lists/subscribers/show](#listssubscribersshow)
	* [接口资源信息](#接口资源信息-8)
	* [参数信息](#参数信息-8)
	* [响应内容](#响应内容-8)
* [lists/subscriptions](#listssubscriptions)
	* [接口资源信息](#接口资源信息-9)
	* [参数信息](#参数信息-9)
	* [响应内容](#响应内容-9)
* [lists/create](#listscreate)
	* [接口资源信息](#接口资源信息-10)
	* [参数信息](#参数信息-10)
	* [响应内容](#响应内容-10)
* [lists/destroy](#listsdestroy)
	* [接口资源信息](#接口资源信息-11)
	* [参数信息](#参数信息-11)
	* [响应内容](#响应内容-11)
* [lists/update](#listsupdate)
	* [接口资源信息](#接口资源信息-12)
	* [参数信息](#参数信息-12)
	* [响应内容](#响应内容-12)

<!-- /code_chunk_output -->

## lists/list

返回认证用户拥有的和订阅的所有list。使用`user_id`或`screen_name`参数来指明用户。如果没指明用户，则返回认证信息的用户。

一次调用最多返回100条结果。订阅的list返回优先级高于用户所拥有的list。那就意味着如果一个用户订阅了90个list且拥有20个list，调用这一接口将会返回90个订阅以及10个拥有的list。`reverse`参数则是用来反转返回优先级的，所以设置`reverse=true`，则将会返回20个拥有的以及80个订阅的list。如果你是只想要获得用户的所拥有的list或是只想要获得用户的所订阅的list，则使用[GET lists/ownerships](#listsownerships)或是[GET lists/subscriptions](#listssubscriptions)。

官方文档地址：
https://developer.twitter.com/en/docs/accounts-and-users/create-manage-lists/api-reference/get-lists-list

### 接口资源信息

|URL|https://api.twitter.com/1.1/lists/list.json|
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
|user_id|可选|获取list的用户id。当用户id与昵称相同时，有助于消除歧义||
|screen_name|可选|获取list的用户昵称。当用户id与昵称相同时，有助于消除歧义||
|reverse|可选|优先级反转<br/>默认订阅优先，当`reverse=true`时拥有的list优先||

### 响应内容

指定用户所订阅以及所拥有的全部list详细信息(JSON数组)。
```
[
  {
    "slug": "meetup-20100301",
    "name": "meetup-20100301",
    "created_at": "Sat Feb 27 21:39:24 +0000 2010",
    "uri": "/twitterapi/meetup-20100301",
    "subscriber_count": 147,
    "id_str": "8044403",
    "member_count": 116,
    "mode": "public",
    "id": 8044403,
    "full_name": "@twitterapi/meetup-20100301",
    "description": "Guests attending the Twitter meetup on 1 March 2010 at the @twoffice",
    "user": {
      "profile_background_tile": true,
      "profile_sidebar_border_color": "C0DEED",
      "name": "Twitter API",
      "profile_sidebar_fill_color": "DDEEF6",
      "location": "San Francisco, CA",
      "created_at": "Wed May 23 06:01:13 +0000 2007",
      "profile_image_url": "http://a0.twimg.com/profile_images/2284174872/7df3h38zabcvjylnyfe3_normal.png",
      "is_translator": false,
      "id_str": "6253282",
      "profile_link_color": "0084B4",
      "follow_request_sent": false,
      "favourites_count": 25,
      "contributors_enabled": true,
      "url": "",
      "default_profile": false,
      "profile_image_url_https": "https://si0.twimg.com/profile_images/2284174872/7df3h38zabcvjylnyfe3_normal.png",
      "utc_offset": -28800,
      "profile_banner_url": "https://si0.twimg.com/profile_banners/6253282/1347394302",
      "id": 6253282,
      "profile_use_background_image": true,
      "listed_count": 11201,
      "profile_text_color": "333333",
      "protected": false,
      "lang": "en",
      "followers_count": 1444739,
      "description": "The Real Twitter API. I tweet about API changes, service issues and happily answer questions about Twitter and our API. Don't get an answer? It's on my website.",
      "notifications": false,
      "geo_enabled": true,
      "verified": true,
      "time_zone": "Pacific Time (US & Canada)",
      "profile_background_color": "C0DEED",
      "profile_background_image_url_https": "https://si0.twimg.com/profile_background_images/656927849/miyt9dpjz77sc0w3d4vj.png",
      "statuses_count": 3367,
      "friends_count": 33,
      "default_profile_image": false,
      "profile_background_image_url": "http://a0.twimg.com/profile_background_images/656927849/miyt9dpjz77sc0w3d4vj.png",
      "following": true,
      "screen_name": "twitterapi"
    },
    "following": false
  },
  {
    "slug": "team",
    "name": "team",
    "created_at": "Wed Nov 04 01:24:28 +0000 2009",
    "uri": "/twitterapi/team",
    "subscriber_count": 277,
    "id_str": "2031945",
    "member_count": 20,
    "mode": "public",
    "id": 2031945,
    "full_name": "@twitterapi/team",
    "description": "",
    "user": {
      "profile_background_tile": true,
      "profile_sidebar_border_color": "C0DEED",
      "name": "Twitter API",
      "profile_sidebar_fill_color": "DDEEF6",
      "location": "San Francisco, CA",
      "created_at": "Wed May 23 06:01:13 +0000 2007",
      "profile_image_url": "http://a0.twimg.com/profile_images/2284174872/7df3h38zabcvjylnyfe3_normal.png",
      "is_translator": false,
      "id_str": "6253282",
      "profile_link_color": "0084B4",
      "follow_request_sent": false,
      "favourites_count": 25,
      "contributors_enabled": true,
      "url": "",
      "default_profile": false,
      "profile_image_url_https": "https://si0.twimg.com/profile_images/2284174872/7df3h38zabcvjylnyfe3_normal.png",
      "utc_offset": -28800,
      "profile_banner_url": "https://si0.twimg.com/profile_banners/6253282/1347394302",
      "id": 6253282,
      "profile_use_background_image": true,
      "listed_count": 11201,
      "profile_text_color": "333333",
      "protected": false,
      "lang": "en",
      "followers_count": 1444739,
      "description": "The Real Twitter API. I tweet about API changes, service issues and happily answer questions about Twitter and our API. Don't get an answer? It's on my website.",
      "notifications": false,
      "geo_enabled": true,
      "verified": true,
      "time_zone": "Pacific Time (US & Canada)",
      "profile_background_color": "C0DEED",
      "profile_background_image_url_https": "https://si0.twimg.com/profile_background_images/656927849/miyt9dpjz77sc0w3d4vj.png",
      "statuses_count": 3367,
      "friends_count": 33,
      "default_profile_image": false,
      "profile_background_image_url": "http://a0.twimg.com/profile_background_images/656927849/miyt9dpjz77sc0w3d4vj.png",
      "following": true,
      "screen_name": "twitterapi"
    },
    "following": true
  }
]
```

## lists/members

返回指定的list所有成员。__私有list必须为其拥有者才有权利查看该list。__

官方文档地址：
https://developer.twitter.com/en/docs/accounts-and-users/create-manage-lists/api-reference/get-lists-members

### 接口资源信息

|URL|https://api.twitter.com/1.1/lists/members.json|
|:------|:-----|
|Method|GET|
|响应格式|JSON|
|是否需要认证|是|
|是否有访问限制|是|
|请求次数/15-min (user auth)|900|
|请求次数/15-min (app ahth)|75|

### 参数信息

|参数名称|必要性|描述|默认值|
|:------|:------|:------|:------|
|list_id|必要|list的数字ID。(`list_id`&#124;`slug`二选一即可)||
|slug|必要|list的slug。如果使用此参数，必须再使用`owner_id`或`owner_screen_name`去指明其拥有者||
|owner_screen_name|可选|list拥有者的账号名称||
|owner_id|可选|list拥有者的账号ID||
|count|可选|指定每页返回的结果数。默认20，最大值为5000|20|
|cursor|半可选|对list中的成员按指定的页面大小(由参数`count`设定)进行分页。如果`cursor`没设定，则默认为`-1`，显示首页。<br/>API的响应内容中将会包含`previous_cursor`和`next_cursor`来帮助我们来回翻页。|-1|
|include_entities|可选|是否包含`entities`信息。<br/>可以通过设置`include_entities=false` 来取消包含`entities`信息。|true|
|skip_status|可选|用户对象中不包含status信息。<br/>当被设置为`true`、`t`或`1`时，用户对象中将不包含status信息|false|

### 响应内容

包含用于翻页的上下页游标以及该页内的成员详细信息（JSON格式）。
```
{
  "previous_cursor": 0,
  "previous_cursor_str": "0",
  "next_cursor": 0,
  "users": [
    {
      "profile_sidebar_fill_color": "bedcfa",
      "expanded_url": null,
      "profile_sidebar_border_color": "85add6",
      "name": "Sharon Ly",
      "profile_background_tile": false,
      "location": "",
      "profile_image_url": "http://a2.twimg.com/profile_images/1359867172/image_normal.jpg",
      "created_at": "Sun May 25 00:29:44 +0000 2008",
      "follow_request_sent": null,
      "is_translator": false,
      "profile_link_color": "955ea6",
      "id_str": "14895163",
      "entities": {
        "urls": [

        ],
        "hashtags": [

        ],
        "user_mentions": [

        ]
      },
      "default_profile": false,
      "favourites_count": 63,
      "contributors_enabled": false,
      "url": null,
      "id": 14895163,
      "utc_offset": -28800,
      "profile_image_url_https": "https://si0.twimg.com/profile_images/1359867172/image_normal.jpg",
      "profile_use_background_image": true,
      "listed_count": 43,
      "lang": "en",
      "profile_text_color": "4c58a3",
      "followers_count": 784,
      "protected": false,
      "profile_background_color": "312040",
      "geo_enabled": true,
      "description": "",
      "time_zone": "Pacific Time (US & Canada)",
      "verified": false,
      "profile_background_image_url_https": "https://si0.twimg.com/profile_background_images/257176598/hydrangeas_94_68830.jpg",
      "notifications": null,
      "friends_count": 188,
      "statuses_count": 325,
      "profile_background_image_url": "http://a1.twimg.com/profile_background_images/257176598/hydrangeas_94_68830.jpg",
      "default_profile_image": false,
      "status": {
        "coordinates": null,
        "truncated": false,
        "created_at": "Tue Jul 05 03:46:03 +0000 2011",
        "favorited": false,
        "id_str": "88091240503058432",
        "in_reply_to_user_id_str": "748353",
        "contributors": null,
        "text": "@kmonkeyjam Oh no... I don't know where that bone is but that sounds terribly painful. How are you still tweeting? Get better!",
        "id": 88091240503058432,
        "retweet_count": 0,
        "in_reply_to_status_id_str": "87979906226597888",
        "geo": null,
        "retweeted": false,
        "in_reply_to_user_id": 748353,
        "source": "Twitter for iPhone",
        "in_reply_to_screen_name": "kmonkeyjam",
        "place": null,
        "in_reply_to_status_id": 87979906226597888
      },
      "display_url": null,
      "screen_name": "onesnowclimber",
      "show_all_inline_media": true,
      "following": null
    }
  ],
  "next_cursor_str": "0"
}
```

## lists/members/show

检查指定用户是否为特定list的成员。

官方文档地址：
https://developer.twitter.com/en/docs/accounts-and-users/create-manage-lists/api-reference/get-lists-members-show

### 接口资源信息

|URL|https://api.twitter.com/1.1/lists/members/show.json|
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
|list_id|必要|list的数字ID。(`list_id`&#124;`slug`二选一即可)||
|slug|必要|list的slug。如果使用此参数，必须再使用`owner_id`或`owner_screen_name`去指明其拥有者||
|user_id|必要|指定用户id。当用户id与昵称相同时，有助于消除歧义||
|screen_name|必要|指定用户昵称。当用户id与昵称相同时，有助于消除歧义||
|owner_screen_name|可选|list拥有者的账号名称||
|owner_id|可选|list拥有者的账号ID||
|include_entities|可选|是否包含`entities`信息。<br/>每条推文都会包含一个名为`entities`的JSON对象，<br/>此对象提供了关于这条推文的各种元数据，包括：`user_mentions`,`urls`和`hashtags`。<br/>`entities`目前在时间轴上选择加入，但它们将在未来成为输出的默认组成部分。查看[Tweet Entities](https://developer.twitter.com/overview/api/tweets)获取更多详细信息||
|skip_status|可选|用户对象中不包含status信息。<br/>当被设置为`true`、`t`或`1`时，用户对象中将不包含status信息|false|

### 响应内容

如果list的成员中不包含该用户，则响应`404`状态码。
如果list的成员中包含该用户，则返回该用户的详细信息(JSON格式)。
```
{
  "id": "657693",
  "id_str": "657693",
  "is_translator": false,
  "default_profile": false,
  "entities": {
    "url": {
      "urls": [
        {
          "url": "http://t.co/jtb0IaGT",
          "indices": [
            0,
            20
          ],
          "display_url": "afroginthevalley.com",
          "expanded_url": "http://afroginthevalley.com/"
        }
      ]
    },
    "description": {
      "urls": []
    }
  },
  "show_all_inline_media": false,
  "profile_use_background_image": false,
  "profile_text_color": "999999",
  "utc_offset": -18000,
  "listed_count": 302,
  "name": "Sylvain Carle",
  "notifications": false,
  "profile_sidebar_border_color": "87CB00",
  "geo_enabled": true,
  "follow_request_sent": false,
  "url": "http://t.co/jtb0IaGT",
  "lang": "en",
  "profile_image_url_https": "https://si0.twimg.com/profile_images/1532782858/sylvaincarle-2011-profile-480_normal.png",
  "created_at": "Thu Jan 18 00:10:45 +0000 2007",
  "protected": false,
  "followers_count": 4281,
  "profile_background_image_url_https": "https://si0.twimg.com/profile_background_images/228591248/bg-14.png",
  "screen_name": "froginthevalley",
  "profile_background_tile": true,
  "friends_count": 2367,
  "profile_sidebar_fill_color": "333333",
  "description": "Developer Advocate at Twitter. Internet, opensource, media & geo/local geek. See also @sylvaincarle for LANG=FR.",
  "time_zone": "Eastern Time (US & Canada)",
  "default_profile_image": false,
  "location": "San Francisco",
  "profile_image_url": "http://a0.twimg.com/profile_images/1532782858/sylvaincarle-2011-profile-480_normal.png",
  "favourites_count": 1790,
  "following": false,
  "profile_background_color": "000000",
  "verified": false,
  "statuses_count": 8191,
  "status": {
    "entities": {
      "urls": [
        {
          "url": "http://t.co/GtBxX0IW",
          "indices": [
            54,
            74
          ],
          "display_url": "example.com",
          "expanded_url": "http://www.example.com"
        },
        {
          "url": "http://t.co/2E5hDjME",
          "indices": [
            94,
            114
          ],
          "display_url": "example.com",
          "expanded_url": "http://example.com"
        }
      ],
      "hashtags": [],
      "user_mentions": [
        {
          "name": "VO5",
          "indices": [
            0,
            6
          ],
          "screen_name": "MyVO5",
          "id": "485879570",
          "id_str": "485879570"
        }
      ]
    },
    "geo": null,
    "place": null,
    "in_reply_to_screen_name": "MyVO5",
    "in_reply_to_user_id": 485879570,
    "retweeted": false,
    "in_reply_to_status_id": 243404113679888400,
    "created_at": "Wed Sep 05 17:45:14 +0000 2012",
    "possibly_sensitive": false,
    "in_reply_to_status_id_str": "243404113679888385",
    "contributors": null,
    "favorited": false,
    "source": "YoruFukurou",
    "in_reply_to_user_id_str": "485879570",
    "retweet_count": 0,
    "id": "< Unable to parse in Javascript >",
    "id_str": "243404435752099841",
    "coordinates": null,
    "truncated": false,
    "text": "@MyVO5 make sure you configure your domain correctly, http://t.co/GtBxX0IW is not the same as http://t.co/2E5hDjME (also, refresh cache)."
  },
  "contributors_enabled": false,
  "profile_background_image_url": "http://a0.twimg.com/profile_background_images/228591248/bg-14.png",
  "profile_link_color": "009DFF"
}
```

## lists/memberships

返回包含指定用户的list详细信息。如果未指定`user_id`和`screen_name`，则返回包含身份验证用户的list详细信息。

官方文档地址：
https://developer.twitter.com/en/docs/accounts-and-users/create-manage-lists/api-reference/get-lists-memberships

### 接口资源信息

|URL|https://api.twitter.com/1.1/lists/memberships.json|
|:------|:-----|
|Method|GET|
|响应格式|JSON|
|是否需要认证|是|
|是否有访问限制|是|
|请求次数/15-min (user auth)|75|
|请求次数/15-min (app ahth)|75|

### 参数信息

|参数名称|必要性|描述|默认值|
|:------|:------|:------|:------|
|user_id|可选|用户id。当用户id与昵称相同时，有助于消除歧义||
|screen_name|可选|用户昵称。当用户id与昵称相同时，有助于消除歧义||
|count|可选|指定每页返回的结果数。默认20，最大值为1000|20|
|cursor|可选|将结果分页。<br/>`-1`为首页，响应内容中提供`next_cursor`和`previous_cursor`支持来回翻页。接口支持的情况下推荐使用`cursor`，查看[Cursoring](https://developer.twitter.com/en/docs/basics/cursoring)获取更多详细内容||
|filter_to_owned_lists|可选|仅返回自己的list。当值为`true`、`t`、`1`时，将仅返回接口身份认证用户自己的list中包含指定用户的list||

### 响应内容

包含用于翻页的上下页游标以及该页内所有list的详细信息（JSON格式）。
```
{
  "previous_cursor": 0,
  "lists": [
    {
      "name": "Digital Marketing",
      "slug": "digital-marketing",
      "uri": "/pointcg/digital-marketing",
      "id_str": "49260625",
      "subscriber_count": 1,
      "member_count": 46,
      "mode": "public",
      "id": 49260625,
      "full_name": "@pointcg/digital-marketing",
      "description": "",
      "user": {
        "profile_sidebar_border_color": "447DBC",
        "profile_background_tile": false,
        "profile_sidebar_fill_color": "447DBC",
        "name": "Chris Greco",
        "created_at": "Wed Feb 28 01:05:01 +0000 2007",
        "location": "",
        "profile_image_url": "http://a1.twimg.com/profile_images/1331628329/chris_2_normal.jpg",
        "follow_request_sent": false,
        "profile_link_color": "0000FF",
        "is_translator": false,
        "id_str": "799757",
        "default_profile": false,
        "favourites_count": 2,
        "contributors_enabled": false,
        "url": null,
        "id": 799757,
        "profile_image_url_https": "https://si0.twimg.com/profile_images/1331628329/chris_2_normal.jpg",
        "utc_offset": -18000,
        "profile_use_background_image": true,
        "listed_count": 4,
        "lang": "en",
        "followers_count": 66,
        "profile_text_color": "000000",
        "protected": false,
        "profile_background_color": "0F5B5F",
        "verified": false,
        "time_zone": "Eastern Time (US & Canada)",
        "profile_background_image_url_https": "https://si0.twimg.com/images/themes/theme1/bg.png",
        "description": "",
        "notifications": false,
        "geo_enabled": false,
        "statuses_count": 122,
        "default_profile_image": false,
        "friends_count": 80,
        "profile_background_image_url": "http://a0.twimg.com/images/themes/theme1/bg.png",
        "following": false,
        "screen_name": "pointcg",
        "show_all_inline_media": false
      },
      "following": false
    },
    {
      "name": "vanessa williams",
      "slug": "vanessa-williams",
      "uri": "/Barbis_doll/vanessa-williams",
      "id_str": "49270287",
      "subscriber_count": 0,
      "member_count": 1,
      "mode": "public",
      "id": 49270287,
      "full_name": "@Barbis_doll/vanessa-williams",
      "description": "former ms. america, talented dancer, singer and actress",
      "user": {
        "profile_sidebar_border_color": "C0DEED",
        "name": "Debbie M.",
        "profile_background_tile": false,
        "profile_sidebar_fill_color": "DDEEF6",
        "location": null,
        "profile_image_url": "http://a3.twimg.com/sticky/default_profile_images/default_profile_4_normal.png",
        "created_at": "Tue Jun 28 00:50:43 +0000 2011",
        "is_translator": false,
        "profile_link_color": "0084B4",
        "id_str": "325263705",
        "follow_request_sent": null,
        "url": null,
        "favourites_count": 0,
        "contributors_enabled": false,
        "default_profile": true,
        "utc_offset": null,
        "id": 325263705,
        "profile_image_url_https": "https://si0.twimg.com/sticky/default_profile_images/default_profile_4_normal.png",
        "listed_count": 0,
        "profile_use_background_image": true,
        "protected": false,
        "followers_count": 2,
        "lang": "en",
        "profile_text_color": "333333",
        "time_zone": null,
        "profile_background_image_url_https": "https://si0.twimg.com/images/themes/theme1/bg.png",
        "notifications": null,
        "geo_enabled": false,
        "description": null,
        "profile_background_color": "C0DEED",
        "verified": false,
        "default_profile_image": true,
        "friends_count": 11,
        "statuses_count": 6,
        "profile_background_image_url": "http://a0.twimg.com/images/themes/theme1/bg.png",
        "following": null,
        "screen_name": "Barbis_doll",
        "show_all_inline_media": false
      },
      "following": false
    },
  ],
  "previous_cursor_str": "0",
  "next_cursor": 1373407125131783107,
  "next_cursor_str": "1373407125131783107"
}
```

## lists/ownerships

返回指定Twitter用户所拥有的全部list。__私有list仅拥有者自己可以查看。__

官方文档地址：
https://developer.twitter.com/en/docs/accounts-and-users/create-manage-lists/api-reference/get-lists-ownerships

### 接口资源信息

|URL|https://api.twitter.com/1.1/lists/ownerships.json|
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
|user_id|可选|用户id。当用户id与昵称相同时，有助于消除歧义||
|screen_name|可选|用户昵称。当用户id与昵称相同时，有助于消除歧义||
|count|可选|指定每页返回的结果数。默认20，最大值为1000|20|
|cursor|可选|将结果分页。<br/>`-1`为首页，响应内容中提供`next_cursor`和`previous_cursor`支持来回翻页。接口支持的情况下推荐使用`cursor`，查看[Cursoring](https://developer.twitter.com/en/docs/basics/cursoring)获取更多详细内容||

### 响应内容

包含用于翻页的上下页游标以及该页内所有list的详细信息（JSON格式）。
```
{
  "next_cursor":46541288,
  "next_cursor_str":"46541288",
  "previous_cursor":0,
  "previous_cursor_str":"0",
  "lists":[
    {
      "id":84839422,
      "id_str":"84839422",
      "name":"Official Twitter accts",
      "uri":"/twitter/official-twitter-accts",
      "subscriber_count":20,
      "member_count":0,
      "mode":"public",
      "description":"Accounts managed by Twitter, Inc. ",
      "slug":"official-twitter-accts",
      "full_name":"@twitter/official-twitter-accts",
      "created_at":"Tue Feb 05 18:14:21 +0000 2013",
      "following":false,
      "user":{
        "id":783214,
        "id_str":"783214",
        "name":"Twitter",
        "screen_name":"twitter",
        "location":"San Francisco, CA",
        "description":"Your official source for news, updates and tips from Twitter, Inc.",
        "url":"http://blog.twitter.com/",
        "entities":{
          "url":{
            "urls":[
              {
                "url":"http://blog.twitter.com/",
                "expanded_url":null,
                "indices":[
                  0,
                  24
                ]
              }
            ]
          },
          "description":{
            "urls":[

            ]
          }
        },
        "protected":false,
        "followers_count":17214319,
        "friends_count":120,
        "listed_count":76232,
        "created_at":"Tue Feb 20 14:35:54 +0000 2007",
        "favourites_count":22,
        "utc_offset":-28800,
        "time_zone":"Pacific Time (US & Canada)",
        "geo_enabled":true,
        "verified":true,
        "statuses_count":1563,
        "lang":"en",
        "contributors_enabled":false,
        "is_translator":false,
        "profile_background_color":"ACDED6",
        "profile_background_image_url":"...",
        "profile_background_image_url_https":"...",
        "profile_background_tile":true,
        "profile_image_url":"...",
        "profile_image_url_https":"...",
        "profile_banner_url":"https://si0.twimg.com/profile_banners/783214/1347405327",
        "profile_link_color":"038543",
        "profile_sidebar_border_color":"EEEEEE",
        "profile_sidebar_fill_color":"F6F6F6",
        "profile_text_color":"333333",
        "profile_use_background_image":true,
        "default_profile":false,
        "default_profile_image":false,
        "following":true,
        "follow_request_sent":false,
        "notifications":false
      }
    },
    {
      "id":46541288,
      "id_str":"46541288",
      "name":"D9",
      "uri":"/twitter/d9",
      "subscriber_count":340,
      "member_count":327,
      "mode":"public",
      "description":"D9 attendees with a Twitter account",
      "slug":"d9",
      "full_name":"@twitter/d9",
      "created_at":"Tue May 31 16:29:35 +0000 2011",
      "following":false,
      "user":{
        "id":783214,
        "id_str":"783214",
        "name":"Twitter",
        "screen_name":"twitter",
        "location":"San Francisco, CA",
        "description":"Your official source for news, updates and tips from Twitter, Inc.",
        "url":"http://blog.twitter.com/",
        "entities":{
          "url":{
            "urls":[
              {
                "url":"http://blog.twitter.com/",
                "expanded_url":null,
                "indices":[
                  0,
                  24
                ]
              }
            ]
          },
          "description":{
            "urls":[

            ]
          }
        },
        "protected":false,
        "followers_count":17214319,
        "friends_count":120,
        "listed_count":76232,
        "created_at":"Tue Feb 20 14:35:54 +0000 2007",
        "favourites_count":22,
        "utc_offset":-28800,
        "time_zone":"Pacific Time (US & Canada)",
        "geo_enabled":true,
        "verified":true,
        "statuses_count":1563,
        "lang":"en",
        "contributors_enabled":false,
        "is_translator":false,
        "profile_background_color":"ACDED6",
        "profile_background_image_url":"...",
        "profile_background_image_url_https":"...",
        "profile_background_tile":true,
        "profile_image_url":"...",
        "profile_image_url_https":"...",
        "profile_banner_url":"https://si0.twimg.com/profile_banners/783214/1347405327",
        "profile_link_color":"038543",
        "profile_sidebar_border_color":"EEEEEE",
        "profile_sidebar_fill_color":"F6F6F6",
        "profile_text_color":"333333",
        "profile_use_background_image":true,
        "default_profile":false,
        "default_profile_image":false,
        "following":true,
        "follow_request_sent":false,
        "notifications":false
      }
    }
  ]
}
```

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
|请求次数/15-min (user auth)|75|
|请求次数/15-min (app ahth)|75|

### 参数信息

|参数名称|必要性|描述|默认值|
|:------|:------|:------|:------|
|list_id|必要|list的数字ID。(`list_id`&#124;`slug`二选一即可)||
|slug|必要|list的slug。如果使用此参数，必须再使用`owner_id`或`owner_screen_name`去指明其拥有者||
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
|list_id|必要|list的数字ID。(`list_id`&#124;`slug`二选一即可)||
|slug|必要|list的slug。如果使用此参数，必须再使用`owner_id`或`owner_screen_name`去指明其拥有者||
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

## lists/subscribers

返回指定list的所有订阅用户详细信息。__私有list只有其拥有者才能查看其订阅用户。__

官方文档地址：
https://developer.twitter.com/en/docs/accounts-and-users/create-manage-lists/api-reference/get-lists-subscribers

### 接口资源信息

|URL|https://api.twitter.com/1.1/lists/subscribers.json|
|:------|:-----|
|Method|GET|
|响应格式|JSON|
|是否需要认证|是|
|是否有访问限制|是|
|请求次数/15-min (user auth)|180|
|请求次数/15-min (app ahth)|15|

### 参数信息

|参数名称|必要性|描述|默认值|
|:------|:------|:------|:------|
|list_id|必要|list的数字ID。(`list_id`&#124;`slug`二选一即可)||
|slug|必要|list的slug。如果使用此参数，必须再使用`owner_id`或`owner_screen_name`去指明其拥有者||
|owner_screen_name|可选|list拥有者的账号名称||
|owner_id|可选|list拥有者的账号ID||
|count|可选|指定每页返回的结果数。默认20，最大值为5000|20|
|cursor|可选|将结果分页。<br/>`-1`为首页，响应内容中提供`next_cursor`和`previous_cursor`支持来回翻页。接口支持的情况下推荐使用`cursor`，查看[Using cursors to navigate collections](https://developer.twitter.com/en/docs/basics/cursoring)获取更多详细内容|-1|
|include_entities|可选|是否包含`entities`信息。<br/>每条推文都会包含一个名为`entities`的JSON对象，<br/>此对象提供了关于这条推文的各种元数据，包括：`user_mentions`,`urls`和`hashtags`。<br/>`entities`目前在时间轴上选择加入，但它们将在未来成为输出的默认组成部分。查看[Tweet Entities](https://developer.twitter.com/overview/api/tweets)获取更多详细信息|true|
|skip_status|可选|用户对象中不包含status信息。<br/>当被设置为`true`、`t`或`1`时，用户对象中将不包含status信息|false|

### 响应内容

包含用于翻页的上下页游标以及该页内所有订阅用户详细信息(JSON格式)。
```
{
  "previous_cursor": 0,
  "previous_cursor_str": "0",
  "next_cursor": 1357643166637635702,
  "users": [
    {
      "profile_background_tile": false,
      "profile_sidebar_fill_color": "DDEEF6",
      "name": "Almissen665",
      "profile_sidebar_border_color": "C0DEED",
      "location": null,
      "profile_image_url": "http://a0.twimg.com/sticky/default_profile_images/default_profile_1_normal.png",
      "created_at": "Mon Jun 27 09:17:15 +0000 2011",
      "follow_request_sent": false,
      "is_translator": false,
      "profile_link_color": "0084B4",
      "id_str": "324841714",
      "url": null,
      "default_profile": true,
      "contributors_enabled": false,
      "favourites_count": 0,
      "id": 324841714,
      "utc_offset": null,
      "profile_image_url_https": "https://si0.twimg.com/sticky/default_profile_images/default_profile_1_normal.png",
      "profile_use_background_image": true,
      "listed_count": 0,
      "lang": "en",
      "profile_text_color": "333333",
      "followers_count": 6,
      "protected": false,
      "profile_background_image_url_https": "https://si0.twimg.com/images/themes/theme1/bg.png",
      "notifications": false,
      "geo_enabled": false,
      "description": null,
      "profile_background_color": "C0DEED",
      "time_zone": null,
      "verified": false,
      "statuses_count": 1,
      "friends_count": 27,
      "profile_background_image_url": "http://a0.twimg.com/images/themes/theme1/bg.png",
      "default_profile_image": true,
      "screen_name": "bonasser789",
      "following": false,
      "show_all_inline_media": false
    },
    {
      "profile_sidebar_fill_color": "E6F6F9",
      "profile_sidebar_border_color": "DBE9ED",
      "name": "GR Syber-Space",
      "profile_background_tile": true,
      "location": "Grand Rapids, MI",
      "profile_image_url": "http://a2.twimg.com/profile_images/1322547748/images__97__normal.jpg",
      "created_at": "Thu Sep 30 23:05:38 +0000 2010",
      "profile_link_color": "CC3366",
      "id_str": "197218370",
      "follow_request_sent": false,
      "is_translator": false,
      "url": "http://www.wix.com/castlesportsgr/myj",
      "default_profile": false,
      "favourites_count": 2,
      "contributors_enabled": false,
      "id": 197218370,
      "utc_offset": -18000,
      "profile_image_url_https": "https://si0.twimg.com/profile_images/1322547748/images__97__normal.jpg",
      "profile_use_background_image": true,
      "listed_count": 268,
      "lang": "en",
      "profile_text_color": "333333",
      "followers_count": 2628,
      "protected": true,
      "notifications": false,
      "geo_enabled": true,
      "profile_background_color": "DBE9ED",
      "description": "Welcome to Teen Gossip 411. Celebrity Gossip, Teens fashion trends for the summer 2011, Hollywood Gossip, Hotest music, Teen Websites, and more.",
      "time_zone": "Quito",
      "verified": false,
      "profile_background_image_url_https": "https://si0.twimg.com/profile_background_images/237705957/images__97_.jpg",
      "default_profile_image": false,
      "friends_count": 2846,
      "profile_background_image_url": "http://a2.twimg.com/profile_background_images/237705957/images__97_.jpg",
      "statuses_count": 7463,
      "show_all_inline_media": true,
      "screen_name": "GRSYBERSPACE",
      "following": false
    }
  ],
  "next_cursor_str": "1357643166637635702"
}
```

## lists/subscribers/show

检查指定用户是否为特定list的订阅者。若是，则返回该用户的详细信息。

官方文档地址：
https://developer.twitter.com/en/docs/accounts-and-users/create-manage-lists/api-reference/get-lists-subscribers-show

### 接口资源信息

|URL|https://api.twitter.com/1.1/lists/subscribers/show.json|
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
|list_id|必要|list的数字ID。(`list_id`&#124;`slug`二选一即可)||
|slug|必要|list的slug。如果使用此参数，必须再使用`owner_id`或`owner_screen_name`去指明其拥有者||
|user_id|必要|指定用户id。当用户id与昵称相同时，有助于消除歧义||
|screen_name|必要|指定用户昵称。当用户id与昵称相同时，有助于消除歧义||
|owner_screen_name|可选|list拥有者的账号名称||
|owner_id|可选|list拥有者的账号ID||
|include_entities|可选|是否包含`entities`信息。<br/>每条推文都会包含一个名为`entities`的JSON对象，<br/>此对象提供了关于这条推文的各种元数据，包括：`user_mentions`,`urls`和`hashtags`。<br/>`entities`目前在时间轴上选择加入，但它们将在未来成为输出的默认组成部分。查看[Tweet Entities](https://developer.twitter.com/overview/api/tweets)获取更多详细信息||
|skip_status|可选|用户对象中不包含status信息。<br/>当被设置为`true`、`t`或`1`时，用户对象中将不包含status信息|false|

### 响应内容

如果list的订阅者中不包含该用户，则响应`404`状态码。
如果list的订阅者中包含该用户，则返回该用户的详细信息(JSON格式)。
```
{
  "id": "819797",
  "id_str": "819797",
  "is_translator": false,
  "default_profile": false,
  "entities": {
    "url": {
      "urls": [
        {
          "url": "http://t.co/Lxw7upbN",
          "indices": [
            0,
            20
          ],
          "display_url": "rebelmouse.com/episod/",
          "expanded_url": "http://www.rebelmouse.com/episod/"
        }
      ]
    },
    "description": {
      "urls": []
    }
  },
  "show_all_inline_media": true,
  "profile_use_background_image": true,
  "profile_text_color": "D20909",
  "utc_offset": -28800,
  "listed_count": 341,
  "name": "Taylor Singletary",
  "notifications": false,
  "profile_sidebar_border_color": "000000",
  "geo_enabled": true,
  "follow_request_sent": false,
  "url": "http://t.co/Lxw7upbN",
  "lang": "en",
  "profile_image_url_https": "https://si0.twimg.com/profile_images/2574556418/dk93ji5e3w4rwscaabt3_normal.png",
  "created_at": "Wed Mar 07 22:23:19 +0000 2007",
  "protected": false,
  "followers_count": 7180,
  "profile_background_image_url_https": "https://si0.twimg.com/profile_background_images/643655842/hzfv12wini4q60zzrthg.png",
  "screen_name": "episod",
  "profile_background_tile": true,
  "friends_count": 5452,
  "profile_sidebar_fill_color": "FBFBFB",
  "description": "Reality Technician, Twitter API team, synthesizer enthusiast; a most excellent adventure in timelines. Missive commander.",
  "time_zone": "Pacific Time (US & Canada)",
  "default_profile_image": false,
  "location": "San Francisco, CA",
  "profile_image_url": "http://a0.twimg.com/profile_images/2574556418/dk93ji5e3w4rwscaabt3_normal.png",
  "profile_banner_url": "https://si0.twimg.com/profile_banners/819797/1346803502",
  "favourites_count": 16076,
  "following": true,
  "profile_background_color": "000000",
  "verified": false,
  "statuses_count": 18132,
  "status": {
    "entities": {
      "urls": [
        {
          "url": "http://t.co/4mdAn0tF",
          "indices": [
            16,
            36
          ],
          "display_url": "youtube.com/watch?v=pPkNtg…",
          "expanded_url": "http://www.youtube.com/watch?v=pPkNtg3Fvwk&feature=youtube_gdata_player"
        }
      ],
      "hashtags": [],
      "user_mentions": []
    },
    "geo": null,
    "place": null,
    "in_reply_to_screen_name": null,
    "in_reply_to_user_id": null,
    "retweeted": false,
    "in_reply_to_status_id": null,
    "created_at": "Wed Sep 05 15:57:09 +0000 2012",
    "possibly_sensitive": false,
    "in_reply_to_status_id_str": null,
    "contributors": null,
    "favorited": false,
    "source": "YouTube on iOS",
    "in_reply_to_user_id_str": null,
    "retweet_count": 0,
    "id": "< Unable to parse in Javascript >",
    "id_str": "243377236902821888",
    "coordinates": null,
    "truncated": false,
    "text": "Current status  http://t.co/4mdAn0tF"
  },
  "contributors_enabled": false,
  "profile_background_image_url": "http://a0.twimg.com/profile_background_images/643655842/hzfv12wini4q60zzrthg.png",
  "profile_link_color": "C71818"
}
```

## lists/subscriptions

返回指定Twitter用户所订阅的全部list。默认情况下每页__20__条list，不包含其拥有的list。

官方文档地址：
https://developer.twitter.com/en/docs/accounts-and-users/create-manage-lists/api-reference/get-lists-subscriptions

### 接口资源信息

|URL|https://api.twitter.com/1.1/lists/subscriptions.json|
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
|user_id|可选|用户id。当用户id与昵称相同时，有助于消除歧义||
|screen_name|可选|用户昵称。当用户id与昵称相同时，有助于消除歧义||
|count|可选|指定每页返回的结果数。默认20，最大值为1000|20|
|cursor|可选|将结果分页。<br/>`-1`为首页，响应内容中提供`next_cursor`和`previous_cursor`支持来回翻页。接口支持的情况下推荐使用`cursor`，查看[Cursoring](https://developer.twitter.com/en/docs/basics/cursoring)获取更多详细内容||

### 响应内容

包含用于翻页的上下页游标以及该页内所有list的详细信息（JSON格式）。
```
{
  "previous_cursor": 0,
  "lists": [
    {
      "slug": "team",
      "name": "team",
      "uri": "/TwitterEng/team",
      "created_at": "Mon Oct 03 02:48:07 +0000 2011",
      "subscriber_count": 131,
      "id_str": "55932616",
      "member_count": 324,
      "mode": "public",
      "id": 55932616,
      "full_name": "@TwitterEng/team",
      "description": "",
      "user": {
        "profile_sidebar_border_color": "C6E2EE",
        "profile_sidebar_fill_color": "DAECF4",
        "profile_background_tile": false,
        "expanded_url": null,
        "name": "Twitter Engineering",
        "location": "San Francisco, CA",
        "created_at": "Sat Jun 16 00:14:36 +0000 2007",
        "profile_image_url": "http://a2.twimg.com/profile_images/1262149685/twitter_newbird_boxed_blueonwhite_normal.png",
        "is_translator": false,
        "profile_link_color": "1F98C7",
        "follow_request_sent": null,
        "id_str": "6844292",
        "entities": {
          "urls": [

          ],
          "hashtags": [

          ],
          "user_mentions": [

          ]
        },
        "url": "http://engineering.twitter.com",
        "default_profile": false,
        "favourites_count": 0,
        "contributors_enabled": true,
        "id": 6844292,
        "utc_offset": -14400,
        "profile_image_url_https": "https://si0.twimg.com/profile_images/1262149685/twitter_newbird_boxed_blueonwhite_normal.png",
        "profile_use_background_image": true,
        "listed_count": 1493,
        "profile_text_color": "663B12",
        "lang": "en",
        "followers_count": 132674,
        "protected": false,
        "profile_background_image_url_https": "https://si0.twimg.com/images/themes/theme2/bg.gif",
        "verified": true,
        "geo_enabled": true,
        "notifications": null,
        "time_zone": "Atlantic Time (Canada)",
        "description": "The official account for Twitter Engineering.",
        "profile_background_color": "C6E2EE",
        "profile_background_image_url": "http://a1.twimg.com/images/themes/theme2/bg.gif",
        "default_profile_image": false,
        "statuses_count": 61,
        "friends_count": 0,
        "display_url": null,
        "screen_name": "TwitterEng",
        "following": null,
        "show_all_inline_media": true
      },
      "following": false
    },
    {
      "slug": "the-brain-trust",
      "name": "The Brain Trust",
      "uri": "/LTRK140/the-brain-trust",
      "created_at": "Sun Mar 06 20:01:50 +0000 2011",
      "subscriber_count": 24,
      "id_str": "37396827",
      "member_count": 148,
      "mode": "public",
      "id": 37396827,
      "full_name": "@LTRK140/the-brain-trust",
      "description": "Twitter Artists, Ascii, Unicode Art.",
      "user": {
        "profile_sidebar_border_color": "080000",
        "profile_sidebar_fill_color": "",
        "profile_background_tile": true,
        "name": "﹅█▄▀█▀ █▀▐━▀▄ ▌◢▌██﹅",
        "location": "Toronto",
        "created_at": "Fri Jun 04 16:48:39 +0000 2010",
        "profile_image_url": "http://a1.twimg.com/profile_images/1315622089/Cool_Daddy_normal.png",
        "is_translator": false,
        "profile_link_color": "080000",
        "follow_request_sent": false,
        "id_str": "151938348",
        "url": "http://twitter.com/KREWZO",
        "favourites_count": 10,
        "contributors_enabled": false,
        "default_profile": false,
        "id": 151938348,
        "utc_offset": -28800,
        "profile_image_url_https": "https://si0.twimg.com/profile_images/1315622089/Cool_Daddy_normal.png",
        "profile_use_background_image": true,
        "listed_count": 131,
        "profile_text_color": "000000",
        "lang": "en",
        "followers_count": 838,
        "protected": false,
        "profile_background_image_url_https": "https://si0.twimg.com/profile_background_images/285103295/ltrk140.JPG",
        "verified": false,
        "geo_enabled": true,
        "notifications": false,
        "time_zone": "Pacific Time (US & Canada)",
        "description": "▓⁄─⁄⁄﹅█▄▀█▀ █▀▐━▀▄ ▌◢▌██﹅⁄─⁄⁄▓  rn  •140•ASCII•UNICODE•ART• BY OZ MELO   •  I LIVE & WORK IN #YYZ.     ★★ MOST TWEETS ARE BEST VIEWED AS A STATUS PAGE ★★   █♥█",
        "profile_background_color": "030003",
        "profile_background_image_url": "http://a1.twimg.com/profile_background_images/285103295/ltrk140.JPG",
        "default_profile_image": false,
        "statuses_count": 1006,
        "friends_count": 139,
        "screen_name": "LTRK140",
        "following": false,
        "show_all_inline_media": true
      },
      "following": false
    },
    {
      "slug": "twoutside-lands",
      "name": "Twoutside Lands",
      "uri": "/dannyhertz/twoutside-lands",
      "created_at": "Fri Aug 12 07:21:25 +0000 2011",
      "subscriber_count": 12,
      "id_str": "52270561",
      "member_count": 25,
      "mode": "public",
      "id": 52270561,
      "full_name": "@dannyhertz/twoutside-lands",
      "description": "Tweeps @ Outside Lands 2011",
      "user": {
        "profile_sidebar_border_color": "4685e3",
        "profile_sidebar_fill_color": "c7dced",
        "profile_background_tile": false,
        "expanded_url": "http://www.dannyhertz.com",
        "name": "Danny Hertz",
        "location": "San Francisco",
        "created_at": "Sat Nov 15 02:26:09 +0000 2008",
        "profile_image_url": "http://a0.twimg.com/profile_images/1546221308/6153868543_d7ab87737a_b_normal.jpeg",
        "is_translator": true,
        "profile_link_color": "005082",
        "follow_request_sent": false,
        "id_str": "17400516",
        "entities": {
          "urls": [

          ],
          "hashtags": [

          ],
          "user_mentions": [

          ]
        },
        "url": "http://t.co/90RtgWI",
        "favourites_count": 243,
        "contributors_enabled": false,
        "default_profile": false,
        "id": 17400516,
        "utc_offset": -28800,
        "profile_image_url_https": "https://si0.twimg.com/profile_images/1546221308/6153868543_d7ab87737a_b_normal.jpeg",
        "profile_use_background_image": true,
        "listed_count": 52,
        "profile_text_color": "000000",
        "lang": "en",
        "followers_count": 2684,
        "protected": false,
        "profile_background_image_url_https": "https://si0.twimg.com/profile_background_images/331345358/pamperedpuppy20091103.jpeg",
        "verified": false,
        "geo_enabled": true,
        "notifications": false,
        "time_zone": "Pacific Time (US & Canada)",
        "description": "Software Engineer on the User Services team at Twitter and lead singer for the rock band Journey.",
        "profile_background_color": "ffffff",
        "profile_background_image_url": "http://a0.twimg.com/profile_background_images/331345358/pamperedpuppy20091103.jpeg",
        "default_profile_image": false,
        "statuses_count": 2318,
        "friends_count": 261,
        "display_url": "dannyhertz.com",
        "screen_name": "dannyhertz",
        "following": false,
        "show_all_inline_media": true
      },
      "following": false
    },
    {
      "slug": "july-6-curators",
      "name": "July 6 curators",
      "uri": "/townhall/july-6-curators",
      "created_at": "Mon Jul 04 20:37:28 +0000 2011",
      "subscriber_count": 58,
      "id_str": "49286494",
      "member_count": 8,
      "mode": "public",
      "id": 49286494,
      "full_name": "@townhall/july-6-curators",
      "description": "Curators helping for the Town Hall at the White House on July 6th at 2pm ET",
      "user": {
        "profile_sidebar_border_color": "C0DEED",
        "profile_sidebar_fill_color": "DDEEF6",
        "profile_background_tile": true,
        "name": "Town Hall",
        "location": "",
        "created_at": "Tue May 31 01:50:52 +0000 2011",
        "profile_image_url": "http://a2.twimg.com/profile_images/1419432899/avatar_normal.png",
        "is_translator": false,
        "profile_link_color": "0084B4",
        "follow_request_sent": null,
        "id_str": "308230587",
        "url": "http://askobama.twitter.com",
        "default_profile": false,
        "favourites_count": 0,
        "contributors_enabled": true,
        "id": 308230587,
        "utc_offset": -28800,
        "profile_image_url_https": "https://si0.twimg.com/profile_images/1419432899/avatar_normal.png",
        "profile_use_background_image": true,
        "listed_count": 517,
        "profile_text_color": "333333",
        "lang": "en",
        "followers_count": 24456,
        "protected": false,
        "profile_background_image_url_https": "https://si0.twimg.com/profile_background_images/280500767/bg.jpg",
        "verified": true,
        "geo_enabled": false,
        "notifications": null,
        "time_zone": "Pacific Time (US & Canada)",
        "description": "Official account for Twitter hosted town halls. Our first on July 6th, 2PM ET. ",
        "profile_background_color": "C0DEED",
        "profile_background_image_url": "http://a0.twimg.com/profile_background_images/280500767/bg.jpg",
        "default_profile_image": false,
        "statuses_count": 100,
        "friends_count": 2,
        "screen_name": "townhall",
        "following": null,
        "show_all_inline_media": true
      },
      "following": false
    },
    {
      "slug": "streaming-music-industry",
      "name": "Streaming Music Industry ",
      "uri": "/meetmarshall/streaming-music-industry",
      "created_at": "Thu Mar 31 04:04:10 +0000 2011",
      "subscriber_count": 193,
      "id_str": "41857276",
      "member_count": 1,
      "mode": "public",
      "id": 41857276,
      "full_name": "@meetmarshall/streaming-music-industry",
      "description": "A custom list created by adding, subtracting or filtering existing lists (made using @formulists)",
      "user": {
        "profile_sidebar_border_color": "C0DEED",
        "profile_sidebar_fill_color": "DDEEF6",
        "profile_background_tile": false,
        "name": "Marshall Kirkpatrick",
        "location": "",
        "created_at": "Mon Mar 28 20:18:47 +0000 2011",
        "profile_image_url": "http://a3.twimg.com/sticky/default_profile_images/default_profile_0_normal.png",
        "is_translator": false,
        "profile_link_color": "0084B4",
        "follow_request_sent": false,
        "id_str": "273602749",
        "url": "http://twitter.com/marshallk",
        "default_profile": true,
        "favourites_count": 0,
        "contributors_enabled": false,
        "id": 273602749,
        "utc_offset": -28800,
        "profile_image_url_https": "https://si0.twimg.com/sticky/default_profile_images/default_profile_0_normal.png",
        "profile_use_background_image": true,
        "listed_count": 3,
        "profile_text_color": "333333",
        "lang": "en",
        "followers_count": 29,
        "protected": false,
        "profile_background_image_url_https": "https://si0.twimg.com/images/themes/theme1/bg.png",
        "verified": false,
        "geo_enabled": false,
        "notifications": false,
        "time_zone": "Pacific Time (US & Canada)",
        "description": "I just came for the lists.",
        "profile_background_color": "C0DEED",
        "profile_background_image_url": "http://a0.twimg.com/images/themes/theme1/bg.png",
        "default_profile_image": true,
        "statuses_count": 3,
        "friends_count": 146,
        "screen_name": "meetmarshall",
        "following": false,
        "show_all_inline_media": false
      },
      "following": false
    }
  ],
  "previous_cursor_str": "0",
  "next_cursor": 1364811190668631091,
  "next_cursor_str": "1364811190668631091"
}
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
|list_id|必要|list数字ID。(`list_id`&#124;`slug`二选一即可)||
|slug|必要|list的slug。如果使用此参数，必须再使用`owner_id`或`owner_screen_name`去指明其拥有者||

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
|list_id|必要|list的数字ID。(`list_id`&#124;`slug`二选一即可)||
|slug|必要|list的slug。如果使用此参数，必须再使用`owner_id`或`owner_screen_name`去指明其拥有者||
|name|可选|list的新名称||
|mode|可选|list新访问权限(public&#124;private)||
|description|可选|list的新描述||
|owner_screen_name|可选|list拥有者的账号名称||
|owner_id|可选|list拥有者的账号ID||

### 响应内容