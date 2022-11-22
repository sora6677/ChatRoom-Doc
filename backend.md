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
