# TCP client + display PGM picture tool
>主要可以透過TCP與server連線，並呼叫server傳送pgm圖，並且能直接在tool上顯示出PGM

## 一、提供的功能
- 支援TCP/IP連線
- 傳送PGM格式檔案
- 能讀取PGM圖並顯示

## 二、環境
使用VS 2017 C#專案來開啟

## 三、介面
### (1) TCP

[![](https://github.com/mxgijojo230/for-test-github/blob/master/pgm_tool/1.png?raw=true)](https://github.com/mxgijojo230/for-test-github/blob/master/pgm_tool/1.png?raw=true)

- 輸入TCP server IP 與 port進行連線
- 連線成功後執行能執行Receive Data來取得PGM圖
- 勾選continue在執行則會不中斷的取得資料
- 勾選Display則會將每筆接收到的PGM圖顯示在視窗上
- 執行save則會儲存當下的PGM圖到目錄中



### (2) PGM Display
[![](https://github.com/mxgijojo230/for-test-github/blob/master/pgm_tool/2.png?raw=true)](https://github.com/mxgijojo230/for-test-github/blob/master/pgm_tool/2.png?raw=true)

- 點選Browse選擇PGM檔所在的資料夾
- 在File name輸入圖檔名稱
- 選擇Show可以將圖檔顯示到視窗上

後續可以透過opencv color bar轉換成顏色的深度圖方便辨識

[![](https://github.com/mxgijojo230/for-test-github/blob/master/pgm_tool/3.jpg?raw=true)](https://github.com/mxgijojo230/for-test-github/blob/master/pgm_tool/3.jpg?raw=true)

## 四、TCP指令

TCP傳輸的流程如下，在接收server指令的部分是透過BackgroundWorker進行偵測，避免指令缺失

 * 在執行connet後，client會與server建立socket
 * 按下Receive Data 會先傳送指令給server要求接收的檔案
 
 ```
 TCP_CMD=1
 ```
 
 * 2.如果有檔案server將會回檔案大小，若無server則回傳0
 * 3.接著再傳送指令給server表示能傳送data
 
 ```
 TCP_CMD=2
 ```
 
 * 4.接收來自server的data並更據前面收到的檔案大小確認資料完整性
 * 5.若要結束連線，按下disconnect則server會關閉該socket
  
 ```
 TCP_CMD=0
 ```


   [dill]: <https://github.com/joemccann/dillinger>
   [git-repo-url]: <https://github.com/joemccann/dillinger.git>
   [john gruber]: <http://daringfireball.net>
   [df1]: <http://daringfireball.net/projects/markdown/>
   [markdown-it]: <https://github.com/markdown-it/markdown-it>
   [Ace Editor]: <http://ace.ajax.org>
   [node.js]: <http://nodejs.org>
   [Twitter Bootstrap]: <http://twitter.github.com/bootstrap/>
   [jQuery]: <http://jquery.com>
   [@tjholowaychuk]: <http://twitter.com/tjholowaychuk>
   [express]: <http://expressjs.com>
   [AngularJS]: <http://angularjs.org>
   [Gulp]: <http://gulpjs.com>

   [PlDb]: <https://github.com/joemccann/dillinger/tree/master/plugins/dropbox/README.md>
   [PlGh]: <https://github.com/joemccann/dillinger/tree/master/plugins/github/README.md>
   [PlGd]: <https://github.com/joemccann/dillinger/tree/master/plugins/googledrive/README.md>
   [PlOd]: <https://github.com/joemccann/dillinger/tree/master/plugins/onedrive/README.md>
   [PlMe]: <https://github.com/joemccann/dillinger/tree/master/plugins/medium/README.md>
   [PlGa]: <https://github.com/RahulHP/dillinger/blob/master/plugins/googleanalytics/README.md>
