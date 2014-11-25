### POST `/sites/join.json` SSO 单点登录接口
  - `short_name`* <String> 站点注册的多说二级域名
  - `secret`* <String> 站点密钥
  - `access_token`* <String> SSO 完成时从多说获得的用户 `token`
  - `user`* <Map/Array> 站点创建的用户信息
    - `user_key`* <String> 这个用户在用户站点中的 ID（**注意：**此ID不是用户在多说的ID）
    - `name`* <String> 用户的显示名
    - `role` <String> 用户在原站点中的身份。支持参数值：`administrator`:管理员, `editor`:编辑, `author`:作者, `user`:用户。管理员将具有多说站点管理后台的所有控制权限，编辑将具有一定评论管理和数据查看权限。
    - `avatar_url` <String> 用户在站点中设定的头像地址
    - `url` <String> 用户设定的网址
    - `email` <String> 邮箱地址。用于被回复时的邮件提醒功能，以及评论管理时的显示等场合。
    - `created_at` <String> 用户创建时间。请注意时间的格式为 `yyyy-mm-dd hh:MM:ss`。如 `2012/12/12 12:12:12` 和 `2012-1-12 12:12:12` 的格式，都不会被成功识别，第二个时间是因为月份应为 `01`


#### 请求范例
暂无

#### 返回数据参数
- `code` <Int> 结果码。`0` 为成功, 失败时为错误码。
- `errorMessage` <String> 错误消息。当 `code` 不为 `0` 时，返回错误消息。
- `response` <Object> 多说 API 返回结果中，通常在 `response` 中含有主要返回数据。当 `code` 为 `0` 时返回。`response` 是多说用户信息,当用户填写了 `email` 地址时，也将包含 `email` 地址信息
  - `user_id` <Int32> 用户在多说的对应 ID，正常返回后，表明站点所传递的在站点中 ID 为 `user_key` 的用户，已经和多说 ID 为 `user_id` 的用户建立了关联。

#### 返回数据范例
```js
{
  "code":0,
  "response": {
      "user_id": 9999999,
      "name":"用户名",
      "url":"http://duoshuo.com",
      "avatar_url":"http://tp4.sinaimg.cn/2472294147/50/5620116219/1",
      "threads":100,
      "comments":3000
    }
  }
}
```
