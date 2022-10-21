> 快速實現對應業務

### 實現授權`code`的獲取和自動更新

1.使用`docker-compose`部署,該方式可以自動實現數據緩存到 redis,自動啟動代理服務器等功能.
**具體`compose`方式部署,請參照:**
https://github.com/yuanzhibang-tool/docker/tree/main/oapp-code-docker-compose

> 該`compose`實現了代理,redis 存儲以及定時更新`access_token`和`ticket`的工作,並會定時清理日誌,保持日誌不會佔用過多空間

_注意:請配置好您這邊需要的開放平台應用信息以及在開放平台該應用下添加 ip 白名單,否則會返回錯誤,已掛載日誌到`logs`目錄下,如有問題請查看目錄,開發者如果需要自己組合業務請參考該`compose`文件自己調整._

---

### 支持的 docker 鏡像,請參照

https://hub.docker.com/u/yuanzhibang

---

Docker 鏡像構建以及 `code` 更新任務為開源項目,請參照:

https://github.com/yuanzhibang-tool/docker.git

https://github.com/yuanzhibang-tool/oapp-token-cron-task.git

!>請注意閱讀項目以及目錄下的 README.md 以更快實現功能開發

---

### 業務接口的快速開發

**node 接口開發**
我們對接口的調用進行了封裝,`node`開發我們封裝了`node`的`npm`庫

https://www.npmjs.com/package/@yuanzhibang/oauth-server

具體使用說明,請參照開源項目,和代碼備註.

https://github.com/yuanzhibang-tool/oauth-server.git

---

**java,php,python 接口開發**
我們提供了 demo,對接口進行了一定的封裝,請參考使用.

https://github.com/yuanzhibang-tool/demo

---

**_demo 或者 npm 包已完成的工作:_**

1.`js` 簽名生成

2.所有接口的封裝調用

3.接口調用支持設置代理,具體使用請參照 單元測試代碼

4.支持從 redis 獲取`server_access_token`或者`js_ticket`

!>歡迎猿猿們提供其他語言的 demo 代碼,請按照其他語言的封裝進行封裝,並提供單元測試.提供的代碼將遵循 MIT 協議.
