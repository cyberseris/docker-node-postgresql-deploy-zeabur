## 啟動方式

1. 安裝相依套件

```
npm ci
```

2. 設定環境變數

使用 Docker 開發：
範例
```
POSTGRES_USER=
POSTGRES_PASSWORD=
POSTGRES_DB=
DB_HOST=postgres
DB_PORT=5432
DB_USERNAME=
DB_PASSWORD=
DB_DATABASE=
DB_SYNCHRONIZE=true
DB_ENABLE_SSL=false
PORT=8080
LOG_LEVEL=debug
JWT_EXPIRES_DAY=30d
JWT_SECRET=
GOOGLE_CLIENT_ID=
GOOGLE_CLIENT_SECRET=
SESSION_SECRET=
```

使用 localhost 開發伺服器（資料庫仍使用 Docker）：

```
POSTGRES_USER=
POSTGRES_PASSWORD=
POSTGRES_DB=
DB_HOST=localhost
DB_PORT=5432
DB_USERNAME=
DB_PASSWORD=
DB_DATABASE=test
DB_SYNCHRONIZE=true
DB_ENABLE_SSL=false
PORT=8080
LOG_LEVEL=debug
JWT_EXPIRES_DAY=30d
JWT_SECRET=
GOOGLE_CLIENT_ID=
GOOGLE_CLIENT_SECRET=
SESSION_SECRET=
```

## 開發指令

- `npm run dev` - 啟動開發伺服器
- `npm run start` - 啟動伺服器與資料庫
- `npm run restart` - 重新啟動伺服器與資料庫
- `npm run stop` - 關閉啟動伺服器與資料庫
- `npm run clean` - 關閉伺服器與資料庫並清除所有資料

## 實際開發
## 前端 Open with Live Server, index.html  
```
<a href='http://localhost:8080/api/v1/users/auth/google'>Login with Google</a>
```
## 後端
- 開啟 docker desktop
- Dockerfile - 修改成 node 環境版本 node:20-alpine3.19
- .env 使用 localhost 開發伺服器, DB_HOST=localhost, 使用雲端主機，DB_HOST=postgres
- `npm run start` - 啟動伺服器與資料庫
- `npm run dev` - 啟動開發伺服器
- 本機運行程式碼， google auth 已授權的重新導向 URI: http://localhost:8080/api/v1/users/auth/google/callback
- 雲端主機 docker 部署， google auth 已授權的重新導向 URI: http://domain:8080/api/v1/users/auth/google/callback ，不能設定 IP 網址(http://IP:8080/api/v1/users/auth/google/callback)

## 雲端部署


## 除錯指令參考
```
docker container prune -f
docker system prune -f
docker image rmi seriskey/butter-sugar
docker volume ls
docker volume rm root_pgData
net stop winnat
net start winnat
docker pull seriskey/butter-sugar
docker compose --env-file .env up -d
docker compose --env-file .env down
```
