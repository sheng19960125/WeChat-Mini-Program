## WeChat-Mini-Program
### Init WeChat-Mini-Program (安裝唯信小程序 流程介紹)
* 首先搜尋網址 https://developers.weixin.qq.com/miniprogram/dev/devtools/download.html
* 依照個人喜好選擇想要下載的開發模板 通常下載穩定版Stable Build (1.02.1907300) 版號會依照更新而變
* 下載後直接安裝，選擇路徑等基本設定後，即可安裝完成，並啟動唯信小程序
### 開發者工具介紹
* 創建小程序(項目->新建項目 如下圖所示)   
<img src="https://github.com/sheng19960125/WeChat-Mini-Program/blob/master/step1.PNG" width="750px" alt="新增" />  

* 主頁面   
<img src="https://github.com/sheng19960125/WeChat-Mini-Program/blob/master/main.PNG" width="750px" alt="主頁" />
  
* 畫面的上部紫色框內的部分為工具欄、藍色框內的部分為模擬器、黃色框內的部分為編輯器、宗色框內的部分為調試器。  
* 官方提供`wcc`與`wcsc`兩種編譯工具，`wcc`編譯器可以將`wxml`文件編譯成`js`文件，`wcsc`編譯器可以將`wxss`文件編譯成`js`文件。
* 在調適方面可見功能已經相當強大，模塊：Console、Sources、Network、Storage、Appdata、Wxml、Sensor、Trace。  
Console：程序錯誤信息，開發者可在此輸入調適code。   
Sources：設置斷點，確認變量內容，修改等。  
Network：Request與Socket請求情況。  
Storage：進行wx.setStorage 或者wx.setStorageSync 存儲數據時，可進行基本新增移除修改等功能。  
Appdata：及時數據顯示，可在此編輯數據，並會及時反饋。  
Wxml：類似於Html前台，可直接修改Wxml數據並匯集時反饋，但部會保存於code中。  
Sensor：模擬地理位子，設備表現重力感測等。  
Trace：連接的設備上取得調試信息並進行顯示。  
* 每一資料夾都拆為四個子資料，分別為`js`、`json`、`wxml`、`wxss`四種檔案類型。  
如果以CodeIgniter架構來說  
`js`相對於`controller`  

