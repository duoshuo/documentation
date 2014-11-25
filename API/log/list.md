### GET `/log/list.json` 同步评论到本地的通知接口
  - `short_name`* <String> 站点注册的多说二级域名
  - `secret`* <String> 站点密钥
  - `since_id` <int64> `0` 同步开始的记录 ID
  - `limit` <int> `50` 最大条数，1 ~ 200
  - `order` <String> `desc|asc`

#### 请求范例
```bash
$ curl -X GET \
  http://api.duoshuo.com/log/list.json? \
  short_name = apitest& \
  secret     = xxxxxxxx
```

#### 返回数据参数
- `code` <Int> 结果码 `0` 为成功，失败时为错误码。
- `errorMessage` <String> 错误消息。当 `code` 不为 `0` 时，返回错误消息。
- `response` <Object> 多说 API 返回结果中，通常在 `response` 中含有主要返回数据。当 `code` 为 `0` 时返回。
  - `log_id` <Int64> 记录 ID, 按时间顺序递增
  - `user_id` <Int> 对评论执行该操作的用户 ID
  - `action` <String> `create|approve|spam|delete|delete-forever` 操作类型，以此为：创建评论、通过评论、标记垃圾评论、删除评论、彻底删除评论
  - `meta` <Object|Array> 根据操作类型不同，`meta` 的类型会有变化。当 `action` 为 `approve, spam, delete, delete-forever` 之一时，`meta` 为 `array`。数组每一个项为一条评论的 ID。当 `action` 为 `create` 时，`meta` 为 `object`, 为新创建的评论信息。
    - `post_id` <Int64> 评论 ID。请注意，`post_id` 为 64 位二进制整数，MySQL 数据类型建议定义为 `bigInt`。
    - `thread_id` <Int64> 文章在多说的 ID。请注意，`thread_id` 为 64 位二进制整数，MySQL 数据类型建议定义为 `bigInt`。
    - `thread_key` <String> 文章在原站点的文章标识。无记录时，为 `NULL`
    - `author_id` <Int> 作者在多说的 ID, `0` 表示匿名用户
    - `author_name` <String> 作者显示名。有可能为空字符串。
    - `author_email` <String> 作者邮箱。有可能为空字符串。
    - `author_url` <String> 作者网址。有可能为空字符串。
    - `author_key` <String> 作者在网站中对应的 ID。有可能为 `0`
    - `ip` <String> 作者 IP 地址。格式为 `*.*.*.*`
    - `created_at` <String> 评论创建日期，格式示例：`2012-07-13T21:58:13+08:00`
    - `message` <String> 评论内容
    - `status` <String> 评论状态。创建评论时，可能的状态：`approved` 已经通过；`pending` 待审核；`spam` 垃圾评论。
    - `parent_id` <Int64> 父评论 ID。请注意，`thread_id` 为 64 位二进制整数，MySQL数据类型建议定义为 `bigInt`
    - `type` <String> 类型。现在均为空
    - `date` <Int> 执行该操作的时间戳

#### 返回数据范例

```js
{
  "code":0,
  "response":
  [{
    "log_id":"777888",
    "user_id":"378928",
    "action":"create",
    "meta": {
      "post_id":"7511238",
      "thread_id":"3118382",
      "author_id":"378928",
      "author_name":"多说小武",
      "author_email":"xiaowu@duoshuo.com",
      "author_url":"http://weibo.com/u/2472294147",
      "author_key":"12",
      "ip":"222.130.10.10",
      "created_at":"2012-07-13T21:58:13+08:00",
      "message":"联句每言松竹意，停杯多说古今人。",
      "status":"approved",
      "type":"",
      "parent_id":"0",
      "thread_key":"108"
    },
    "date":1342187893
  },
  {
    "log_id":"888999",
    "user_id":"378928",
    "action":"delete",
    "meta":["6142557","7511532","8511993","9621469"],
    "date":1342378758
  }]
}
```
