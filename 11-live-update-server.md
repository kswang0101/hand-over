## Live-update Server
Live-update 各個 Service 所使用的 Port 整理在 `C:\README.md`，目前有註冊啓動時會執行的 Script `C:\startup.ps1`，其內容是使用 [PM2](https://github.com/Unitech/pm2) 去啓動管理各個 Service

![pm2-ls](resources\pm2-ls.png)

### Directory Structure

各個 Service 的 Binary 並不是放在 `C:\Program Files` 之下，而是 `C:\01.web_service` 目錄

* Service Binary
    - [Apache HTTP Server](https://httpd.apache.org/)
        + __Path__: `C:\01.web_service\Apache2.2`
        + __Target__: 原本使用 `80` Port 的 Web Server，目前棄用
    - [Gitea](https://gitea.io/)
        + __Path__: `C:\01.web_service\gitea`
        + __Target__: 方便部署用的 Git Server
    - [MariaDB](https://mariadb.org/)
        + __Path__: `C:\01.web_service\MariaDB 10.1`
        + __Target__: 與 `MySQL` 相容，目前未使用
    - [Nginx](http://nginx.org/)
        + __Path__: `C:\01.web_service\nginx-1.11.9`
        + __Target__: Web Server 兼 Reverse Proxy Server，使用 `80` 與 `8080` Port
    - [PostgreSQL](https://www.postgresql.org/)
        + __Path__: `C:\01.web_service\PostgreSQL9.6`
        + __Target__: 功能比較強大的 RDBMS，目前 `Subscription` 會拿來存儲已讀記錄與我的最愛
    - [RabbitMQ](https://www.rabbitmq.com/)
        + __Path__: `C:\01.web_service\RabbitMQ Server`
        + __Target__: Message Queue Server，原本是要給 InQuire 的 Notification Web API 使用的

我已經寫了一些基本的 Batch Script 已方便重啓 Service，亦放在 `C:\01.web_service` 下

* Nginx Restart Steps
    1. `C:\01.web_service\taskkill_nginx.bat` 
    2. `C:\01.web_service\stop_nginx.bat` 
    3. `C:\01.web_service\start_nginx.bat` 


* Directory Tree
```md
C:\
+---01.web_service
|   +---Apache2.2
|   +---gitea
|   +---MariaDB 10.1
|   +---nginx-1.11.9
|   +---PostgreSQL9.6
|   +---RabbitMQ Server
|   \---_projects
|       +---api.inquire
|       +---auto-test-cache
|       +---doc.inquire
|       |   +---cust
|       |   \---empl
|       +---message.inquire
|       +---server.inquire
|       \---subscription-grpc
+---_file_storage
|   +---FileCenter
|   +---gitea-repositories
|   +---LiveUpdate
|   \---_reverse
\---_sql_data
    +---LiveUpdate
    \---_reverse
```