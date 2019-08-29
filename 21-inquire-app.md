## InQuire App

### Desktop Application
* Projects
  - [InQuire_WL / InQuire_WL](http://inquire.insyde.com:3000/InQuire_WL/InQuire_WL)
* To-do
  - [ ] [升級 CEFPython 到 v66.0，感謝 Lampix 願意資助](https://github.com/cztomczak/cefpython#funding-for-v660-release)
  - [ ] Linux 版本安裝腳本 (for Live-update)
  - [ ] 使用 Python3 與 wxPython4.0 重構

InQurie 是使用了 Python2 寫成的 Desktop Application，其目的是在不改變公司現有系統的前提下，整合所有服務成爲唯一入口。大部分的 Dependencies 已經透過 [Pipenv](https://docs.pipenv.org/) 管理，需要手動安裝的部分請參考 README.md

構成 InQuire 主體有三大 Framework：[wxPython Classic](https://wxpython.org/news/wxpython-3.0.2.0-release/index.html)、[CEF Python](https://github.com/cztomczak/cefpython) 以及 [Twisted](https://twistedmatrix.com/trac/)，分別負責 GUI、WebView 以及 Event Loop

本應用使用 [PyInstaller](http://www.pyinstaller.org/) 編譯，在 Windows 下使用 [InnoSetup](http://www.jrsoftware.org/isinfo.php) 打包爲 Installer。目前 Linux 版本僅於 [Ubuntu 16.04 LTS](http://releases.ubuntu.com/16.04/) 與 [Ubuntu 14.04 LTS](http://releases.ubuntu.com/14.04/) 測試。目前尚未撰寫安裝用的 Bash Script，不過在 Ubuntu 上其實也可以使用 Python Script 來處理


### System Tray
* Projects
  - [kevin.chen / InQuireTrayTest](http://inquire.insyde.com:3000/kevin.chen/InQuireTrayTest)
  - [kevin.chen / LiveUpdateTray](http://inquire.insyde.com:3000/kevin.chen/LiveUpdateTray)

開發語言爲 Kotlin 與 Java，目前公司最多人使用的 Linux Desktop 環境是 Ubuntu Desktop，Ubuntu 在 18.04 之前的 LTE 版本使用的是 Unity，而 Unity 的 System Tray 與 Windows 相比少了部分功能，而高層希望在 Linux 的行爲要與在 Windows 一樣，因此改使用 [AWT](https://www.wikiwand.com/en/Abstract_Window_Toolkit) 來畫出 System Tray。

編譯流程使用 [Gradle](https://gradle.org/) 管理，目錄架構就是一般標準的 Java 目錄架構。要注意的是 Ubuntu 14.04 LTS (Trusty Tahr) 的 `default-jdk` 是 Java 7，因此不能直接使用 Lambda


### Start Menu
* Projects
  - [InQuire_WL / inquire-react-start-menu](http://inquire.insyde.com:3000/InQuire_WL/inquire-react-start-menu)

使用 [Create React App](https://github.com/facebook/create-react-app) 創建的 Web App，會透過 InQuire 的 Twisted Web Server 得到當前使用者可使用的 Service 列表並渲染在網頁上