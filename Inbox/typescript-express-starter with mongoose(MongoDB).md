---
title : typescript-express-starter with mongoose(MongoDB)
date : 2024-12-12_週四 13:42
aliases : [express, mongodb, typescript]
---
Note Type :: 📝<br>
Topics :: [[]]<br>
Parent Link :: [[]]<br>

---
# typescript-express-starter with mongoose(MongoDB)

## file structure


```
📦 project_root
└── 📂 src
    ├── 📂 config
    ├── 📂 controllers
    │   └──  xxx.controller.ts
    ├── 📂 database
    ├── 📂 dtos
    │   └──  xxx.dtos.ts
    ├── 📂 exceptions
    ├── 📂 http
    │   └── 📄 xxx.http
    ├── 📂 interfaces
    │   ├──  routes.interface.ts
    │   └──  xxx.interface.ts
    ├── 📂 middlewares
    │   ├──  error.middleware.ts
    │   └──  validation.middleware.ts
    ├── 📂 models
    │   └──  xxx.model.ts
    ├── 📂 routes
    │   └──  xxx.route.ts
    ├── 📂 services
    │   └──  xxx.service.ts
    ├── 📂 test
    │   ├──  index.test.ts
    │   └──  xxx.test.ts
    ├── 📂 utils
    ├──  app.ts
    └──  server.ts
```


+ config
	+ 讀取.env的設定
+ controllers
	+ 接收request資料，並傳至對應的services中
		+ 如：CRUD
+ database
	+ 連接上mongdb
+ dtos
	+ ㄇㄧㄠ
+ exceptions
+ http
+ interfaces
	+ 資料庫table的schema (只有欄位與型別)
+ middlewares
+ models
	+ 資料庫table的schema
+ routes
	+ HTTP Request的routes
		+ 如：CRUD
+ services
	+ 實際運算邏輯的地方
		+ 如：CRUD
+ test

### 新增table流程 (table name: `xxx`)
1. 新增`interfaces/xxx.interface.ts`，並寫入schema
	+ 只有欄位與型別
2. 新增`models/xxx.model.ts`，並寫入schema
	+ 根據`interface`訂好的欄位，加入需要的validator
3. 新增`services/xxx.service.ts`，並寫入table的service
	+ 主要應該是CRUD
4. 新增`controllers/xxx.controller.ts`，並寫入table的controller
	+ 主要應該是CRUD
5. 新增`routes/xxx.route.ts`，並寫入需要的route
	+ 主要應該是CRUD