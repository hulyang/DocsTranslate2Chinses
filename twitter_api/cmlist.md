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
* [lists/show](#listsshow)
	* [接口资源信息](#接口资源信息-4)
	* [参数信息](#参数信息-4)
	* [响应内容](#响应内容-4)
* [lists/statuses](#listsstatuses)
	* [接口资源信息](#接口资源信息-5)
	* [参数信息](#参数信息-5)
	* [响应内容](#响应内容-5)
* [lists/create](#listscreate)
	* [接口资源信息](#接口资源信息-6)
	* [参数信息](#参数信息-6)
	* [响应内容](#响应内容-6)
* [lists/destroy](#listsdestroy)
	* [接口资源信息](#接口资源信息-7)
	* [参数信息](#参数信息-7)
	* [响应内容](#响应内容-7)
* [lists/update](#listsupdate)
	* [接口资源信息](#接口资源信息-8)
	* [参数信息](#参数信息-8)
	* [响应内容](#响应内容-8)

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
|include_entities|可选|是否包含`entities`信息。<br/>API1.1中默认为开启状态。<br/>每条推文都会包含一个名为`entities`的JSON对象，<br/>此对象提供了关于这条推文的各种元数据，包括：`user_mentions`,`urls`和`hashtags`。<br/>`entities`目前在时间轴上选择加入，但它们将在未来成为输出的默认组成部分。查看[Tweet Entities](https://developer.twitter.com/overview/api/tweets)获取更多详细信息||
|skip_status|可选|用户对象中不包含status信息。<br/>当被设置为`true`、`t`或`1`时，用户对象中将不包含status信息|false|

### 响应内容

如果list中不包含该用户，则响应`404`状态码。
如果list中包含该用户，则返回该用户的详细信息(JSON格式)。
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