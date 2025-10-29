10/9 LOT ID:WE3325A07002 AGV無法自動搬運入庫

查詢MCS發現,AGV不搬運,不搬運的原因為: PortASRS3FDC04,PORT TYPE NEED RESERVE
![[../attachments/Pasted image 20251009144013.png]]

去查ASRS裡的MQ上下傳狀態
發現現存物料檔案不存在

![[../attachments/Pasted image 20251017092110.png]]


接下來在ASRS建立新物料資料,且只能使用ASRS旁的電腦,無法使用個人電腦新增,因為沒有連結到手臂資料庫
(新物料資料會由押出新材料時提前提供,按照裡面提供的資料去新增)
例:![[../attachments/搖盤線捲資料_含料號_V16.xlsx]]
excel檔內需新增的料號,通常只有紅圈處須新增
![[../attachments/Pasted image 20251023085358.png]]

接下來到ASRS裡


![[../attachments/Pasted image 20251022153959.png]]

1.選擇維護作業
2.物料資料維護
3.輸入完該物件所需基本資料
4.按下新增即可
須注意ASRS輸入時重量單位為克(g),內外徑為毫米(mm),高度為公分(cm)

接下來去重打報文
[EZoMQ 登入頁面](https://ymmq.walsin.com/ezomq/login)
帳號:YM3A
密碼:1qaz2wsx


1.在EzoMQ頁面下
2.左側欄位選擇YM(MES正式機)
3.上方選擇發行端 
(因為要先找MES有無發報文給WES)
4.Ctrl+F 搜尋列輸入 download
5.下方找到 ASRS_MESTRANSDOWNLOADREQ_PUB
6.找到最右邊底圖為綠色方塊的白色眼睛,點擊眼睛

![[Pasted image 20251028102007.png]]

7.先移動至畫面最下方,將每頁顯示改為100,可以擴大搜尋範圍
(每頁顯示改為100後,可以再切換至下一頁再搜尋)
![[Pasted image 20251028101412.png]]


8.將lot id將lot id WE3325A07002貼上搜尋列後會出現搜尋結果 
結果顯示10/8 3:31,並點擊紅框處藍字的超連結
![[Pasted image 20251028104625.png]]

9.點擊上圖紅框藍字後會出現以下畫面
![[Pasted image 20251029093925.png]]

10.因為我們要讓MES重發報文到WES端,故選擇發送端拋送(紅框處),並選擇重拋即可
![[Pasted image 20251029094611.png]]

11.接著再到WES裡確認,剛才重新發送result為ok
![[Pasted image 20251029095442.png]]

12.到WES裡的命令資料查詢確定是否產生該筆ID的入庫命令
13.可以手動開堆高機入庫or AGV 全自動入庫



