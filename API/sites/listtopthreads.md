### GET `/sites/listTopThreads.json` 获取站点中每日/每周/每月/总评论数最多的文章
  - `short_name`* <String> 站点注册的多说二级域名
  - `range` <String> `daily|weekly|monthly|all` 获取的范围
  - `num_items` <int> `5` 获取的条数
  - `channel_key` <int> 文章所属的频道

#### 请求范例
```bash
$ curl -X GET \
  http://api.duoshuo.com/sites/listTopThreads.json? \
  short_name = apitest
```

#### 返回数据参数
- `code` <Int> 结果码。`0` 为成功, 失败时为错误码。
- `errorMessage` <String> 错误消息。当 `code` 不为 `0` 时，返回错误消息。
- `response` <Object> 多说 API 返回结果中，通常在 `response` 中含有主要返回数据。当 `code` 为 `0` 时返回。
  - `thread_id` <String> 文章在多说数据库中的 ID
  - `created_at` <String> 文章创建时间
  - `title` <String> 文章标题
  - `url` <String> 文章链接
  - `likes` <Int> 这篇文章被点击「喜欢」的次数
  - `comments` <Int> 文章评论数
  - `reports` <Int> 这篇文章相关微博数

#### 返回数据范例
```js
{
  "code":0,
  "response":
  [{
    thread_id: "1",
    title: "多说是什么？",
    created_at: "2011-11-24T16:10:56+08:00",
    url: "http://blog.duoshuo.com/2011/11/what-is-duoshuo/",
    likes: 20,
    comments: 1384,
    reposts: 0
  },{
    thread_id: "2",
    title: "安装了多说的网站举例",
    created_at: "2011-12-02T12:57:14+08:00",
    url: "http://blog.duoshuo.com/all-installed/",
    likes: 26,
    comments: 640,
    reposts: 3
  }]
}
```
