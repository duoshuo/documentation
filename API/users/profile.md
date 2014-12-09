## 获得用户数据

### GET `/users/profile.json`
  - `user_id`* <String> 用户ID

#### 请求范例
```bash
$ curl -X GET \
  http://api.duoshuo.com/users/profile.json? \
  user_id=378333
```

#### 返回范例
```js
{
  "response": {
    "user_id": "378333",
    "name": "欢喜佛祖",
    "url": "http:\/\/t.qq.com\/hsu5199",
    "avatar_url": "http:\/\/app.qlogo.cn\/mbloghead\/d4aab6bf54582d4f7a18\/50",
    "threads": 0,
    "comments": 0,
    "social_uid": {
      "qq": "83B14496C07AFD09ABA30EE8BA7A284C"
    },
    "post_votes": "0",
    "connected_services": {
      "qqt": {
        "name": "欢喜佛祖",
        "email": "602532062@qq.com",
        "avatar_url": "http:\/\/app.qlogo.cn\/mbloghead\/d4aab6bf54582d4f7a18\/50",
        "url": "http:\/\/t.qq.com\/hsu5199",
        "description": "我是台湾台北人現定居大連，所有了解我認識我的朋友們都叫我(佛祖)，所以您叫我(佛祖)这名稱就好，我个人處世之道嗎！就是：人與人相處之道,誠信相交,以誠相待,信義為本.....",
        "service_name": "qqt"
      },
      "qzone": {
        "name": "欢喜佛祖",
        "avatar_url": null,
        "service_name": "qzone"
      }
    }
  },
  "code": 0
}
```

#### 返回参数

- `code` `<Int>` 结果码。`0` 为成功。失败时为错误码。
- `errorMessage` `<String>` 错误消息。当 `code` 不为 `0` 时，返回错误消息。
- `response` `<Object>` 当 `code` 为 `0` 时，返回请求到的 `JSON` 对象。
