## 同步文章到多说接口

### POST `/threads/import.json`
  - `short_name`* `<String>` 站点注册的多说二级域名
  - `secret`* `<String>` 站点密钥
  - `threads`* `<Map/Array>` 文章列表
    - `thread_key`* `<String>` 文章在原站点中的 ID
    - `title`* `<String>` 文章标题
    - `url`* `<String>` 文章 URL
    - `content` `<String>` 文章内容
    - `author_key` `<String>` 文章作者在原站点中的用户 ID
    - `excerpt` `<String>` 文章摘要
    - `comment_status` `<Bool>` `open|close` 文章是否开启评论
    - `likes` `<Int>` 文章被「喜欢」的次数，该属性导入意义不大，会在被喜欢之后重新统计
    - `views` `<Int>` 文章被查看的次数

#### 请求范例
暂无

#### 返回范例
```js
{
  "code": 0,
  "response": {
    "1001": "1152985276292923001",
    "1002": "1152985276292923002",
    "1003": "1152985276292923003",
    "aboutme": "1152985276292923004"
  }
}
```

#### 返回参数
- `code` `<Int>` 结果码。`0` 为成功, 失败时为错误码。
- `errorMessage` `<String>` 错误消息。当 `code` 不为 `0` 时，返回错误消息。
- `response` `<Object>` 多说 API 返回结果中，通常在 `response` 中含有主要返回数据。当 `code` 为 `0` 时返回。`response` 是以 `thread_key` 为主键，`thread_id` 为值的数组
- `thread_id` `<Int64>`
