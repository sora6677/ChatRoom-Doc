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
Header：
  ManagerId(string)：管理員 (唯一碼)
  ManagerToken(string)：身分驗證令牌
```

```
MetHod：GET
傳入參數：
傳入JSON：
傳入範例：
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
Header：
  ManagerId(string)：管理員 (唯一碼)
  ManagerToken(string)：身分驗證令牌
```

```
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  NewPassword(string)：管理員新密碼
傳入範例：
  data={"NewPassword":"test123"}
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

## GetMasterGroupList - 取大群主列表
```
***僅身分為官方的帳號可呼叫
Header：
  ManagerId(string)：管理員 (唯一碼)
  ManagerToken(string)：身分驗證令牌
```

```
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  GetLimit(int)：要取得筆數 ***最少取10筆
  GetPage(int)：要取得頁數 ***從1開始
傳入範例：
  data={"GetLimit":10,"GetPage":1}
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
  {"status":200,"msg":"成功","data":{"TotalPage":1,"MasterGroupLists":[{"ManagerId":"34444","ManagerAccount":"test_master001","UpperId":10000},{"ManagerId":"39674","ManagerAccount":"test_master002","UpperId":10000}]}}
失敗範例：
  {"status":1001,"msg":"傳入資料異常","data":{}}
```

## CreateMasterGroup - 創建大群主
```
***僅身分為官方的帳號可呼叫
Header：
  ManagerId(string)：管理員 (唯一碼)
  ManagerToken(string)：身分驗證令牌
```

```
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  MasterAccount(string)：大群主帳號
  MasterPassword(string)：大群主密碼
傳入範例：
  data={"MasterAccount":"test_master001","MasterPassword":"test123"}
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
  {"status":1005,"msg":"建立失敗","data":{}}
  {"status":1101,"msg":"帳號重複","data":{}}
```

## GetGroupList - 取群主列表
```
***僅身分為官方的帳號或對應的大群主可呼叫
Header：
  ManagerId(string)：管理員 (唯一碼)
  ManagerToken(string)：身分驗證令牌
```

```
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  MasterGroupId(string)：要查的群主ID ***若身分為群主,傳入自己的 ManagerId
  GetLimit(int)：要取得筆數 ***最少取10筆
  GetPage(int)：要取得頁數 ***從1開始
傳入範例：
  data={"GetLimit":10,"GetPage":1}
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
Header：
  ManagerId(string)：管理員 (唯一碼)
  ManagerToken(string)：身分驗證令牌
```

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
Header：
  ManagerId(string)：管理員 (唯一碼)
  ManagerToken(string)：身分驗證令牌
```

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
Header：
  ManagerId(string)：管理員 (唯一碼)
  ManagerToken(string)：身分驗證令牌
```

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
