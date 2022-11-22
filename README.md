# ChatRoom_backend-Doc 聊天室後台

## UserRegister - 註冊
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

## UserLogin - 登入
```
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  UserAccount(string)：玩家帳號
  UserPassword(string)：玩家密碼
傳入範例：
  data={"PlayerAccount":"abc","PlayerPassword":"test"}
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

## UserLogout - 登出
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
  data={"NewNickName":"efg"}
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
  data={"NewPassword":"efg"}
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

## GroupProduceToken - 群主產生加入令牌

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

## GroupKickMember - 群主踢除(刪除)會員

```
Header：
  UserId(int)：玩家ID (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
MetHod：POST
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

## GroupMuteMember - 群主禁言|解禁言會員

```
Header：
  UserId(int)：玩家ID (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
MetHod：POST
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

## GroupLowList - 群主下層會員列表

```
***如果身分是大群主，呼叫此API，回傳的資料是下層的所有群主
Header：
  UserId(int)：玩家ID (唯一碼)
  AuthToken(string)：身分驗證令牌
```

```
MetHod：POST
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
