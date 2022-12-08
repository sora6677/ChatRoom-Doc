# ChatRoom_frontend-Doc 聊天室前台

## 錯誤代碼
|回傳碼|說明|
|---|---|
|200|成功|
|1000|異常錯誤|
|1001|傳入資料異常|
|1002|資料庫異常|
|1003|登入令牌驗證失效|
|1004|無此權限|
|1005|建立失敗|
|1101|帳號重複|
|1102|無此帳號|
|1103|密碼錯誤|
|1104|查無此ID|
|1105|查無指定聊天室|
|1106|聊天室人數已滿|

## UserRegister - 註冊
```
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  UserAccount(string)：玩家帳號 **限制 12 碼
  UserNick(string)：玩家暱稱 **限制 12 碼
  UserPassword(string)：玩家密碼 **限制 12 碼
傳入範例：
  data={"UserAccount":"testUser02","UserNick":"userNick02","UserPassword":"test123"}
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
    AuthToken(string)：登入驗證令牌
    UserId(int)：玩家ID
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"AuthToken":"552bffdb5c5ea4045d88e71c7b8f2b1d","UserId":47988}}
失敗範例：
  {"status":1005,"msg":"建立失敗","data":{}}
  {"status":1101,"msg":"帳號重複","data":{}}
  {"status":1105,"msg":"查無指定聊天室","data":{}}
  {"status":1106,"msg":"聊天室人數已滿","data":{}}
```

## UserLogin - 登入
```
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  UserAccount(string)：玩家帳號
  UserPassword(string)：玩家密碼
傳入範例：
  data={"UserAccount":"testUser02","UserPassword":"test123"}
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
    AuthToken(string)：登入驗證令牌
    UserId(int)：玩家ID
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"AuthToken":"79df2a0420d9add88bf3401360104682","UserId":47988}}
失敗範例：
  {"status":1102,"msg":"無此帳號","data":{}}
  {"status":1103,"msg":"密碼錯誤","data":{}}
```

## UserLogout - 登出
```
Header：
  UserId(int)：玩家ID (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
MetHod：GET
傳入參數：
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

## UserGetInfo - 取得玩家資訊
```
Header：
  UserId(int)：玩家ID (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  SearchId(int)：要查詢的玩家ID
傳入範例：
  data={"SearchId":69307}
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
    UserAccount(string)：玩家帳號
    UserNick(string)：玩家暱稱
    UserType(int)：身分類型 0:官方 1:大群主 2:群主 3:玩家
    ChatId(string)：聊天室ID
    UpperId(int)：上層ID = 上層的 UserId
    UpperNick(string)：上層ID暱稱
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"UserAccount":"testUser01","UserNick":"userNick01","UserType":3,"ChatId":"rcuhlhqltkan27s19g2uc4e0mk","UpperId":79833,"UpperNick":"group01"}}
失敗範例：
  {"status":1001,"msg":"傳入資料異常","data":{}}
```

## UserModifyNick - 修改暱稱

```
Header：
  UserId(int)：玩家ID (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  NewNickName(string)：新暱稱
傳入範例：
  data={"NewNickName":"defts"}
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

## UserModifyPassword - 修改密碼

```
Header：
  UserId(int)：玩家ID (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  NewPassword(string)：新密碼
傳入範例：
  data={"NewPassword":"123456"}
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

## UpFile - 上傳檔案

```
URL： 依聊天室回傳的上傳網址
Header：
  UserId(int)：玩家ID (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
MetHod：POST
Content-Type：multipart/form-data
檔案上傳 key： UpFile
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
    FileUrl(string)：檔案網址
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"FileUrl":"http://xxx"}}
失敗範例：
  {"status":1001,"msg":"傳入資料異常","data":{}}
```

## GroupProduceToken - 群主產生加入令牌

```
***產生之後每次取都會是同一個令牌，此令牌不會失效
Header：
  UserId(int)：玩家ID (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
MetHod：GET
傳入參數：
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
    GroupAddUrl(string)：指定群組加入網址
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"GroupAddUrl":"http:\/\/127.0.0.1:8070\/frontend\/UserRegister.php?token=33060558081c80a2133385f26412d790"}}
失敗範例：
  {"status":1001,"msg":"傳入資料異常","data":{}}
```

## GroupLowList - 群主下層會員列表

```
Header：
  UserId(int)：玩家ID (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
MetHod：GET
傳入參數：
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
    UserId(string)：玩家ID
    UserAccount(string)：玩家帳號
    UserNickName(string)：玩家暱稱
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":[{"UserId":"47988","UserAccount":"testUser02","UserNickName":"userNick02"},{"UserId":"69307","UserAccount":"testUser01","UserNickName":"defts"}]}
失敗範例：
  {"status":1001,"msg":"傳入資料異常","data":{}}
```

## GroupMuteList - 群主禁言列表
```
Header：
  UserId(int)：玩家ID (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
MetHod：GET
傳入參數：
```

```
回傳參數：
  status(int)：代碼
  msg(string)：訊息
  data(object)：
    UserId：玩家ID (唯一碼)
    UserAccount：玩家帳號
    UserNickName：玩家暱稱
    MuteInvalid：禁言失效時間
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":[{"UserId":"69307","UserAccount":"testUser01","UserNickName":"defts","MuteInvalid":"2022-11-24 10:47:46"}]}
失敗範例：
  {"status":1001,"msg":"傳入資料異常","data":{}}
```

## GroupSetMuteUser - 群主禁言|解禁言玩家

```
Header：
  UserId(int)：玩家ID (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  MuteId(int)：要禁言玩家
  MuteTime(int)：要禁言時間 0:解禁 >0:禁言幾分鐘
傳入範例：
  data={"MuteId":69307,"MuteTime":10}
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
  {"status":1104,"msg":"查無此ID","data":{}}
```
