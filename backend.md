# ChatRoom_backend-Doc 聊天室後台

## 共用錯誤代碼
|回傳碼|說明|
|---|---|
|200|成功|
|1000|異常錯誤|
|1001|傳入資料異常|
|1002|資料庫異常|

## ManagerLogin - 管理員登入
```
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  ManagerAccount(string)：管理員帳號
  ManagerPassword(string)：管理員密碼
傳入範例：
  data={"ManagerAccount":"chat_user","ManagerPassword":"123456"}
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
    ManagerId(string)：管理員ID
    AuthToken(string)：管理員令牌
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"ManagerId":"10000","AuthToken":"1bab341c06ca0d432e3d37adc892a4a1","ManagerType":0}}
失敗範例：
  {"status":1102,"msg":"無此帳號","data":{}}
  {"status":1103,"msg":"密碼錯誤","data":{}}
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
