### POST `/posts/create.json` 发表评论接口
  - `short_name`* <String> 站点注册的多说二级域名
  - `secret`* <String> 站点密钥
  - `message`* <String> 评论内容
  - `thread_key` <String> 被评论文章在原站点的文章标识，如果有 `thread_id` ，此参数是可选参数，否则是必选参数。
  - `thread_id` <String> 被评论文章的多说文章ID，如果有 `thread_key`，此参数是可选参数，否则是必选参数。
  - `parent_id` <String> 父评论（被回复的评论）的 ID
  - `author_name` <String> 作者名字。如果已登陆多说，此参数是可选参数，否则是必选参数。
  - `author_email` <String> 作者邮箱。如果已登陆多说，此参数是可选参数，否则是必选参数。
  - `author_url` <String> 作者网址
  - `remote_auth` <String> `remote_auth` 串是判断用户是否登录的依据。
  - `jwt` <String> 用户身份信息
  - `access_token` <String> SSO 登录获取的 `access_token`

#### 请求范例

匿名发表新评论:
```bash
$ curl -X POST \
  http://duoshuo.com/api/posts/create.json? \
  short_name = official& \
  author_email = jp.chenyang%40gmail.com& \
  author_name = Perchouli& \
  thread_id = 1152923703638301959& \
  author_url = http%3A%2F%2Fduoshuo.com& \
  message = 匿名发表新评论
```

登陆后发表评论:
```bash
$ curl -X POST \
  http://duoshuo.com/api/posts/create.json? \
  short_name = official& \
  remote_auth = remote_auth%3AW10%3D+f6b2d4ddd2c960d9a4fa41cefee55bdb1876bea8+1354681746& \
  thread_id = 1152923703638301959& \
  message = 登陆多说发表评论
```

#### 返回数据参数
- `code` <Int> 结果码。`0` 为成功, 失败时为错误码。
- `errorMessage` <String> 错误消息。当 `code` 不为 `0` 时，返回错误消息。
- `response` <Object> 多说 API 返回结果中，通常在 `response` 中含有主要返回数据。当 `code` 为 `0` 时返回。
  - `post_id` <Int64> 评论 ID。请注意，`post_id` 为 64 位二进制整数，MySQL 数据类型建议定义为 `bigInt`。
  - `parent_id` <Int64> 父评论 ID。请注意，`thread_id` 为 64 位二进制整数，MySQL数据类型建议定义为 `bigInt`
  - `thread_id` <Int64> 文章在多说的 ID。请注意，`thread_id` 为 64 位二进制整数，MySQL 数据类型建议定义为 `bigInt`。
  - `status` <String> 评论状态。创建评论时，可能的状态：`approved` 已经通过；`pending` 待审核；`spam` 垃圾评论。
  - `source` <String> 评论来源
  - `author_key` <String> 作者邮箱。有可能为空字符串。
  - `author_name` <String> 作者显示名。有可能为空。
  - `author_url` <String> 作者网址。有可能为空字符串。
  - `message` <String> 评论的内容
  - `created_at` <String> 评论创建日期，格式示例：`2012-07-13T21:58:13+08:00`
  - `likes` <Int> 评论被点「赞」的次数
  - `reports` <Int> 评论被「举报」的次数
  - `type` <String> 类型。现在均为空

#### 返回数据范例
```js
{
  "code":0,
  "response":
    {
    "post_id": "1152985276292923003",
    "parent_id":  "1152985276292923000",
    "thread_id": "1152923703638301959",
    "status": "approved",
    "source": "duoshuo",
    "author_key": "1",
    "author_name": "Perchouli",
    "author_url": "http://weibo.com/perchouli",
    "message": "登陆多说发表评论",
    "created_at": "2012-11-01T11:36:38+08:00",
    "likes": 0,
    "reports": 0,
    "comments": 0,
    "reposts": 0,
    "type": "",
    "privileges": {
      "delete": true,
      "update": true,
      "moderate": true
    },
    "author":{
      "user_id": "2288",
      "name": "Perchouli",
      "url": "http://weibo.com/perchouli",
      "avatar_url": "http://tp3.sinaimg.cn/1893629610/50/1292295250/1",
      "domain": "",
      "connected_services": {
        "weibo": "1893629610",
        "douban": "3382783",
        "baidu": "839143886"
      }
    }
  }
}
```
