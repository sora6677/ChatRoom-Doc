# ChatRoom_backend-Doc 聊天室後台

## ManagerLogin - 管理員登入
```
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  UserAccount(string)：玩家帳號
  UserNick(string)：玩家暱稱
  UserPassword(string)：玩家密碼
傳入範例：
  data={"PlayerAccount":"abc","PlayerNick":"ts99","PlayerPassword":"test"}
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{}}
失敗範例：
  {"status":1001,"msg":"傳入資料異常","data":{}}
```

## ManagerLogout - 管理員登出
```
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  UserId(int)：玩家ID (唯一碼)
  AuthToken(string)：身分驗證令牌
傳入範例：
  data={"UserId":"abc","AuthToken":"test"}
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{}}
失敗範例：
  {"status":1001,"msg":"傳入資料異常","data":{}}
```

## ManagerModifyPassword - 管理員修改登入密碼
```
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  UserId(int)：玩家ID (唯一碼)
  AuthToken(string)：身分驗證令牌
傳入範例：
  data={"UserId":"abc","AuthToken":"test"}
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{}}
失敗範例：
  {"status":1001,"msg":"傳入資料異常","data":{}}
```

## ManagerProduceGroupToken - 管理員產生群主加入令牌
```
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  UserId(int)：玩家ID (唯一碼)
  AuthToken(string)：身分驗證令牌
傳入範例：
  data={"UserId":"abc","AuthToken":"test"}
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{}}
失敗範例：
  {"status":1001,"msg":"傳入資料異常","data":{}}
```

## ManagerKickMember - 管理員踢除會員
```
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  UserId(int)：玩家ID (唯一碼)
  AuthToken(string)：身分驗證令牌
傳入範例：
  data={"UserId":"abc","AuthToken":"test"}
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{}}
失敗範例：
  {"status":1001,"msg":"傳入資料異常","data":{}}
```

## ManagerKickMember - 管理員禁言|解禁言會員
```
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  UserId(int)：玩家ID (唯一碼)
  AuthToken(string)：身分驗證令牌
傳入範例：
  data={"UserId":"abc","AuthToken":"test"}
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{}}
失敗範例：
  {"status":1001,"msg":"傳入資料異常","data":{}}
```

## ManagerLowList - 管理員下層會員列表
```
***依照管理員身分顯示下層會員列表
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  UserId(int)：玩家ID (唯一碼)
  AuthToken(string)：身分驗證令牌
傳入範例：
  data={"UserId":"abc","AuthToken":"test"}
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{}}
失敗範例：
  {"status":1001,"msg":"傳入資料異常","data":{}}
```
