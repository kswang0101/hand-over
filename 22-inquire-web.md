## InQuire Web

### Web Application and Web API
* Projects
  - [InQuire_WL / inquire-subscription](http://inquire.insyde.com:3000/InQuire_WL/inquire-subscription)
  - [InQuire_WL / inquire-server](http://inquire.insyde.com:3000/InQuire_WL/inquire-server)
  - [InQuire_WL / inquire-api](http://inquire.insyde.com:3000/InQuire_WL/inquire-api)
* To-do
  - [ ] `InQuire_WL / inquire-subscription` 可以列出當前使用者所有可見的 Publications 列表，無需切換 Channel 

InQuire 所提供的服務絕大部分都與 Web 相關，當應用需求不是那麼適合使用 wxWidgets 來呈現的情況下，使用傳統的 Web Site 或 [Single-page Application](https://medium.com/@hulitw/introduction-mvc-spa-and-ssr-545c941669e9) 在開發及維護上是比較方便的

這三個 Project 皆使用 [Node.js](https://nodejs.org/en/) 開發，在 Live-update Server 上使用 [nvm-windows](https://github.com/coreybutler/nvm-windows) 來管理 Node.js 版本，使用 [PM2](https://github.com/Unitech/pm2) 來管理各個 Process。這些 Service 在 Live-update Server 上使用的 Port 請參考 Live-update Server 的 `C:\README.md`，啓動腳本請參考 `C:\startuo.ps1`

`InQuire_WL / inquire-subscription` 爲 Single-page Application，使用 [React Starter Kit](https://github.com/kriasoft/react-starter-kit) 作爲 Boilerplate，其目的是將 [原本於 e-Insyde 的 Publication](https://sys.insyde.com/Publication/PubList.asp) 加上 Group 與 Category 屬性

`InQuire_WL / inquire-server` 使用 [Express' application generator](https://github.com/expressjs/generator)，使用 [Pug (Jade)](https://github.com/pugjs/pug) 作爲 Template Engine，主要提供 `File Center` 與 `Training`(Youtube) 的頁面

`InQuire_WL / inquire-api` 使用與 `InQUire_WL / inquir-server` 同樣的 Web Framework，主要提供 `Email Verification` 與 `Skype for Bisiness` 的 Web API


### Web API
* Projects
  - [InQuire_WL / auto-test-cache](http://inquire.insyde.com:3000/InQuire_WL/auto-test-cache)
  - [InQuire_WL / auto-test-grpc](http://inquire.insyde.com:3000/InQuire_WL/auto-test-grpc)
  - [InQuire_WL / subscription-grpc](http://inquire.insyde.com:3000/InQuire_WL/subscription-grpc)
* To-do
  - [ ] 使用 `InQuire_WL / auto-test-grpc` 取代 `InQuire_WL / auto-test-cache`

這三個服務皆使用 Golang 撰寫，其目的在於 Serivce Owner 爲提供 Web API 而是提供 Database 權限直接讀取，而頻繁讀取可能造成 Database 效能低落，因此自行建造具 Cache 機制的 Web API Service 來避免 Client 直接讀取 Database

Dependencies 透過 [govendor](https://github.com/kardianos/govendor) 來進行管理，目錄架構參考了 [Standard Go Project Layout](https://github.com/golang-standards/project-layout)。其中 `InQuire_WL / auto-test-cache` 是較早期的應急 Project，用於改善執行 MySQL Query 需要數十秒的問題，而之後的新 Project `InQuire_WL / auto-test-grpc` 其目的是希望 Client 不要直接讀取 Database，而是全部透過 Web API 來進行 `Auto-test` 的相關操作，但目前尚未完工

`InQuire_WL / subscription-grpc` 是針對 Notification 的資料 Cache，Subscription Message 以及 User 對應的 Channel 資料皆是存放於公司的 ERP Database，但因效能不佳問題，需在本地備份避免頻繁存取


### User Guide 
* Projects
  - [InQuire_WL / inquire-user-guide](http://inquire.insyde.com:3000/InQuire_WL/inquire-user-guide)
  - [InQuire_WL / inquire-gitbook-theme](http://inquire.insyde.com:3000/InQuire_WL)

InQuire 的 User Guide 使用 Gitbook 撰寫，詳細文檔請參考 [GitBook Toolchain Documentation](https://toolchain.gitbook.com/)，爲了處理 URI 路徑問題因此對 Default Theme 做了一些修改
