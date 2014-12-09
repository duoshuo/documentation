## 获得当前文章的评论接口

### GET `/threads/listPosts.json`
  - `short_name`* `<String>` 站点注册的多说二级域名
  - `thread_key`* `<String>` 当前文章的 `thread-key`
  - `page`* `<String>`
  - `limit`* `<Int>`
  - `order` `<String>` `desc|asc` 返回的评论的排序规则


#### 请求范例
```bash
$ curl -X GET \
  http://api.duoshuo.com/threads/listPosts.json? \
  order      = asc& \
  thread_key = article1& \
  short_name = official& \
  page       = 1& \
  limit      = 10
```

#### 返回范例
```js
{
  "hotPosts": ["1213447420692660281", "1213447420692660271", "1213447420692660261"],
  "thread": {
    "thread_id": "1213447420692660225",
    "title": "我曾经问个不休",
    "created_at": "2014-07-07T15:08:26+08:00",
    "thread_key": "article1",
    "url": "http:\/\/test.com",
    "likes": 1,
    "dislikes": 0,
    "comments": 50,
    "reposts": 0,
    "views": 0,
    "weibo_reposts": 35,
    "qqt_reposts": 0,
    "excerpt": "",
    "agent": "general",
    "user_vote": 1
  },
  "cursor": {
    "total": 31,
    "pages": 31
  },
  "parentPosts": {
    "1213447420692660260": {
      "post_id": "1213447420692660260",
      "thread_id": "1213447420692660225",
      "status": "approved",
      "source": "duoshuo",
      "author_id": 2120851,
      "author_key": null,
      "message": "what?",
      "created_at": "2014-07-07T15:09:18+08:00",
      "likes": 1,
      "reports": 0,
      "privileges": {
        "delete": true,
        "moderate": true
      },
      "type": "",
      "parent_id": 0,
      "root_id": 0,
      "comments": 0,
      "reposts": 0,
      "agent": "Mozilla\/5.0 (Windows NT 6.1; WOW64; rv:30.0) Gecko\/20100101 Firefox\/30.0",
      "parents": [],
      "author": {
        "user_id": "2120851",
        "name": "codegeek",
        "url": "http:\/\/weibo.com\/1891991231",
        "avatar_url": "http:\/\/tp4.sinaimg.cn\/1891991231\/50\/5663654316\/1",
        "threads": 0,
        "comments": 38,
        "social_uid": {
          "weibo": "1891991231"
        }
      },
      "children": [{
        "post_id": "1213447420692660278",
        "thread_id": "1213447420692660225",
        "status": "approved",
        "source": "duoshuo",
        "author_id": 2120851,
        "author_key": null,
        "message": "hello kitty.",
        "created_at": "2014-07-11T12:37:12+08:00",
        "likes": 0,
        "reports": 0,
        "privileges": {
          "delete": true,
          "moderate": true
        },
        "type": "",
        "parent_id": "1213447420692660260",
        "root_id": "1213447420692660260",
        "comments": 0,
        "reposts": 0,
        "agent": "Mozilla\/5.0 (Windows NT 6.1; WOW64) AppleWebKit\/537.36 (KHTML, like Gecko) Chrome\/35.0.1916.153 Safari\/537.36",
        "parents": ["1213447420692660260"],
        "author": {
          "user_id": "2120851",
          "name": "codegeek",
          "url": "http:\/\/weibo.com\/1891991231",
          "avatar_url": "http:\/\/tp4.sinaimg.cn\/1891991231\/50\/5663654316\/1",
          "threads": 0,
          "comments": 38,
          "social_uid": {
            "weibo": "1891991231"
          }
        }
      }],
      "childrenArray": ["1213447420692660278"]
    },
    "1213447420692660278": {
      "post_id": "1213447420692660278",
      "thread_id": "1213447420692660225",
      "status": "approved",
      "source": "duoshuo",
      "author_id": 2120851,
      "author_key": null,
      "message": "hello kitty.",
      "created_at": "2014-07-11T12:37:12+08:00",
      "likes": 0,
      "reports": 0,
      "privileges": {
        "delete": true,
        "moderate": true
      },
      "type": "",
      "parent_id": "1213447420692660260",
      "root_id": "1213447420692660260",
      "comments": 0,
      "reposts": 0,
      "agent": "Mozilla\/5.0 (Windows NT 6.1; WOW64) AppleWebKit\/537.36 (KHTML, like Gecko) Chrome\/35.0.1916.153 Safari\/537.36",
      "parents": ["1213447420692660260"],
      "author": {
        "user_id": "2120851",
        "name": "codegeek",
        "url": "http:\/\/weibo.com\/1891991231",
        "avatar_url": "http:\/\/tp4.sinaimg.cn\/1891991231\/50\/5663654316\/1",
        "threads": 0,
        "comments": 38,
        "social_uid": {
          "weibo": "1891991231"
        }
      }
    },
    "1213447420692660281": {
      "post_id": "1213447420692660281",
      "thread_id": "1213447420692660225",
      "status": "approved",
      "source": "duoshuo",
      "author_id": 8051531,
      "author_key": "0",
      "message": "刚回酒店",
      "created_at": "2014-07-18T15:04:20+08:00",
      "likes": 2,
      "reports": 0,
      "privileges": {
        "delete": true,
        "moderate": true
      },
      "type": "",
      "parent_id": 0,
      "root_id": 0,
      "comments": 0,
      "reposts": 0,
      "agent": "",
      "parents": [],
      "author": {
        "name": "fourblockadmin",
        "avatar_url": null,
        "url": ""
      }
    },
    "1213447420692660271": {
      "post_id": "1213447420692660271",
      "thread_id": "1213447420692660225",
      "status": "approved",
      "source": "duoshuo",
      "author_id": 0,
      "author_key": "0",
      "message": "官方的观点是发的发的所发生的",
      "created_at": "2014-07-09T18:27:53+08:00",
      "likes": 2,
      "reports": 0,
      "privileges": {
        "delete": true,
        "moderate": true
      },
      "type": "",
      "parent_id": 0,
      "root_id": 0,
      "comments": 0,
      "reposts": 0,
      "agent": "Mozilla\/5.0 (Windows NT 6.1; WOW64) AppleWebKit\/537.36 (KHTML, like Gecko) Chrome\/35.0.1916.153 Safari\/537.36",
      "parents": [],
      "author": {
        "name": "我能",
        "avatar_url": null,
        "url": null
      }
    },
  },
  "users": {
    "2120851": {
      "user_id": "2120851",
      "name": "codegeek",
      "url": "http:\/\/weibo.com\/1891991231",
      "avatar_url": "http:\/\/tp4.sinaimg.cn\/1891991231\/50\/5663654316\/1",
      "threads": 0,
      "comments": 38,
      "social_uid": {
        "weibo": "1891991231"
      }
    }
  },
  "response": ["1213447420692660260"],
  "options": {
    "formPosition": "bottom",
    "order": "asc",
    "limit": 1,
    "hot_posts": 3,
    "max_depth": 5,
    "show_context": false,
    "like_thread_enabled": true,
    "parse_html_enabled": false,
    "show_weibo": true,
    "show_qqt": true,
    "show_reposts": true,
    "deny_anonymous": false,
    "auth_in_win": true,
    "require_guest_email": true,
    "require_guest_url": false,
    "use_smilies": true,
    "use_images": false,
    "poweredby_text": "七大洲旅游网正在使用多说",
    "mzadx_id": null,
    "message": "",
    "source": "duoshuo"
  },
  "code": 0
}
```

#### 返回参数
- `code` <Int> 结果码。`0` 为成功, 失败时为错误码。
- `errorMessage` <String> 错误消息。当 `code` 不为 `0` 时，返回错误消息。
- `response` <Object> 多说 API 返回结果中，通常在 `response` 中含有主要返回数据。当 `code` 为 `0`, 当前页的评论的 ID 列表，评论的具体信息可以在 `parentPosts` 当中查找到，若果是回复类型的评论其父级评论也可以在 `parentPosts` 当中查到。
- `thread` <Object> 当前文章的信息
- `hotPosts` <Object> 当前热门的评论
- `cursor` <Object> 评论列表的游标信息
- `parentPosts` <Object> 当前页的评论和其父级评论的完整信息
- `option` <Object> 当前的配置信息
