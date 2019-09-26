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
* 每一資料夾都拆為四個子資料，分別為`js`、`json`、`wxml`、`wxss`四種檔案類型， 其中json與wxss依情況可以省略。
### 技術架構
小程序的運行環境分成`渲染層`和`邏輯層`。  
其中Wxml與Wxss工作在渲染層，Js腳本在邏輯層。
以下簡易做解釋   

index.wxml
```
<view>{{ msg }}</view>
```
index.js
```
Page({
  onLoad: function () {
    this.setData({ msg: 'Hello World' })
  }
})
```
* 以這個範例來說，可以看到三點：  
    * `渲染層`(WXML、WXSS文件)與數據相關。(`Show Dat`)  
    * `邏輯層`(js文件)產生、外處數據。(`What Data`)  
    * `邏輯層`(js文件)通過Page實例的setData方法傳遞數據到渲染層。(`Send Data`)  

### 邏輯層  
小程序由範例可知，邏輯層是由JavaScript編寫。  
邏輯層將數據進行外處後發給視圖層，同時接受視圖層的反饋。  
在JavaScript基礎上，發現以下幾點。  
* 以`App`與`Page`的方法，進行小程序的開發。  
* 在開發程序中，有大量不同的Api可提供調用方法其中都屬於內建Api，在現有唯信架構中提供。  
* 而在每個頁面中，都視可以獨立操作的。  
* 而在測試中發現，在為框架中因為不屬於在瀏覽器的閱讀，所以JavaScript中web的能力皆無法使用。如:`document`、`window`等等  

### 渲染層/視圖層
主框架是由WXML與WXSS編寫，由組件來進行展示。由邏輯層的數據反映成視圖，同時將試圖層所發生的事件反饋诶邏輯層。  
WXML(WeiXin Markup language) 用於描述頁面的結構體。   
* 具備數據綁定、列表選染、條件渲染、模板、引用、事件   

WXS(WeiXin Script) 小程序屬腳本語言，结合 WXML，可以構出頁面結構。   
* 頁面渲染、數據處理   

WXSS(WeiXin Style Sheet) 用於描述頁面樣式。   
* 以英文直翻，為一套樣式語言，負責描述WXML的組件樣式   

而組件(Component)是視圖最基本的元件。    

### 通信模型
小程序主要分為`渲染層`與`邏輯層`兩種線程來做管理。  
* 渲染層使用`WebView`進行。   
* 邏輯層使用`JsCore`運行JS腳本。    
<img src="https://github.com/sheng19960125/WeChat-Mini-Program/blob/master/model.png" width="750px" alt="模型" />
Native指唯信客戶端，網路請求等也經由Native轉發。如上圖所示。    
WXML先轉為JS在回到原本的樣式，過程如下。

```
<view>{{ msg }}</view> 
    
{ msg:"Hello World" }  
    
{ name:"view",
  children:[
    {text:"Holle World"}
  ]
}
    
view -> "Hello World"
```


