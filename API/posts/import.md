### GET `/posts/import.json` 同步评论接口
  - `short_name`* <String> 站点注册的多说二级域名
  - `secret`* <String> 站点密钥
  - `posts`* <Map/Array> 评论列表
    - `post_key`* 这条评论在当前站点的 ID
    - `thread_key`* 这条评论所对应文章在当前站点的 ID
    - `message`* 评论内容
    - `post_id` 对于从多说导出的数据，再次导入多说，会根据此 ID 进行匹配，自动忽略 `post_key` 参数
    - `parent_key` 父级评论在当前站点的 ID
    - `author_key` 评论者在当前站点的 ID
    - `author_name` 评论者的用户名
    - `author_email` 评论者的邮箱，如果没有设置头像会根据这个信息从 `gravatar` 获取头像
    - `author_url` 评论者的 URL，评论者头像或者名字会跳转到改 URL
    - `ip` 评论者的 IP
    - `agent` 评论者 `User Agent` 信息，通常包括浏览器版本、引擎、设备等信息
    - `likes` 这条评论被「赞」的次数
    - `reports` 这条评论被「举报」的次数
    - `created_at` 评论发表时间。请注意时间的格式为 `yyyy-mm-dd hh:MM:ss`。如 `2012/12/12 12:12:12` 和 `2012-1-12 12:12:12` 的格式，都不会被成功识别，第二个时间是因为月份应为 `01`
    - `status` 评论状态。支持：`approved`：已通过，`pending`：待审核，`deleted`：已删除。不建议将已删除数据导入多说，会在到期30天之后自动从数据库中清除。

#### 请求范例
暂无

#### 返回数据参数
- `code` <Int> 结果码。`0` 为成功, 失败时为错误码。
- `errorMessage` <String> 错误消息。当 `code` 不为 `0` 时，返回错误消息。
- `response` <Object> 多说 API 返回结果中，通常在 `response` 中含有主要返回数据。当 `code` 为 `0` 时返回。`response` 是以 `post_key` 为主键，`post_id` 为值的数组
  - `post_id` <Int64> 评论在多说的对应 ID

#### 返回数据范例
```js
{
  "code":0,
  "response": {
    "1001":"1152985276292923001",
    "1002":"1152985276292923002",
    "1003":"1152985276292923003",
    "aboutme":"1152985276292923004"
    }
  }
}
```
