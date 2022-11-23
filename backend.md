# ChatRoom_backend-Doc 聊天室後台

## 共用錯誤代碼
|回傳碼|說明|
|---|---|
|200|成功|
|1000|異常錯誤|
|1001|傳入資料異常|
|1002|資料庫異常|
|1003|登入令牌驗證失效|
|1004|無此權限|
|1005|建立失敗|

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

## GetManagerInfo - 取得管理員個人資訊
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
    ManagerAccount(string)：管理員帳號
    ManagerType(int)：管理員類型 0:官方 1:大群主 2:群主 3:玩家
    UpperId(string)：管理員上層ID
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"ManagerAccount":"chat_user","ManagerType":0,"UpperId":0}}
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
    TotalPage(int)：總頁數
    MasterGroupLists(object array)：大群主列表
      MasterId(string)：大群主ID
      MasterAccount(string)：大群主帳號
      MasterType(int)：身分類型,0:官方 1:大群主 2:群主 3:會員
      UpperId(string)：大群主上層ID,官方ID
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"TotalPage":1,"MasterGroupLists":[{"MasterId":"34444","MasterAccount":"test_master001","MasterType":1,"UpperId":10000},{"MasterId":"39674","MasterAccount":"test_master002","MasterType":1,"UpperId":10000}]}}
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
  MasterGroupId(string)：要查的大群主ID ***若身分為大群主,傳入自己的 ManagerId
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
    TotalPage(int)：總頁數
    GroupsList(object array)：群主列表
      GroupId(string)：群主ID
      GroupAccount(string)：群主帳號
      GroupNick(string)：群主暱稱
      GroupType(int)：身分類型,0:官方 1:大群主 2:群主 3:會員
      ChatId(string)：聊天室ID
      UpperId(string)：群主上層ID,所屬的大群主ID
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"TotalPage":1,"GroupsList":[{"GroupId":"61663","GroupAccount":"test_group01","GroupNick":"group01","GroupType":2,"ChatId":"k3nhs6fovavh8hu9vheqgueu0m","UpperId":"39674"},{"GroupId":"79833","GroupAccount":"test_group02","GroupNick":"group02","GroupType":2,"ChatId":"rcuhlhqltkan27s19g2uc4e0mk","UpperId":"39674"}]}}
失敗範例：
  {"status":1001,"msg":"傳入資料異常","data":{}}
```

## CreateMasterGroup - 創建群主
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
  MasterId(string)：大群主ID
  GroupAccount(string)：群主帳號
  GroupNick(string)：群主暱稱
  GroupPassword(string)：群主密碼
  ChatName(string)：聊天室名稱
傳入範例：
  data={"MasterId":"39674","GroupAccount":"test_group01","GroupNick":"group01","GroupPassword":"test123","ChatName":"測試群01"}
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

## GetUsersList - 取玩家列表
```
***除官方帳號外,僅同群的上層皆可呼叫
Header：
  ManagerId(string)：管理員 (唯一碼)
  ManagerToken(string)：身分驗證令牌
```

```
MetHod：POST
傳入參數：
  data：JSON
傳入JSON：
  GroupId(string)：要查的群主ID ***若身分為群主,傳入自己的 ManagerId
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
    TotalPage(int)：總頁數
    UsersList(object array)：玩家列表
      UserId(string)：玩家ID
      UserAccount(string)：玩家帳號
      UserNick(string)：玩家暱稱
      UserType(string)：身分類型,0:官方 1:大群主 2:群主 3:會員
      ChatId(string)：聊天室ID
      UpperId(string)：玩家上層ID,所屬的群主ID
回傳方式：JSON
```

```
成功範例：
  {"status":200,"msg":"成功","data":{"TotalPage":1,"UsersList":[{"UserId":"47988","UserAccount":"testUser02","UserNick":"userNick02","UserType":3,"ChatId":"rcuhlhqltkan27s19g2uc4e0mk","UpperId":"79833"},{"UserId":"69307","UserAccount":"testUser01","UserNick":"userNick01","UserType":3,"ChatId":"rcuhlhqltkan27s19g2uc4e0mk","UpperId":"79833"}]}}
失敗範例：
  {"status":1001,"msg":"傳入資料異常","data":{}}
```
