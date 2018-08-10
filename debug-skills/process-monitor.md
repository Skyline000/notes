# Process Monitor

Download link: [https://docs.microsoft.com/en-us/sysinternals/downloads/procmon](https://docs.microsoft.com/en-us/sysinternals/downloads/procmon)

{% file src="../.gitbook/assets/processmonitor.zip" caption="Process Monitor v3.50" %}

![](../.gitbook/assets/image%20%284%29.png)

 ProcMon把RegMon與FileMon的監控放在一起

 ProcMon免安裝，只解EXE檔出來放在桌面就可以開始

1. 開啟/停止記錄事件: 打X時表示現在停止捕捉事件
2. 自動下捲: 由於監聽過程中，清單會不斷增長，你可以選擇ProcMon永遠顯示清單最下方的最新記錄。不過清單通常長得很快，會捲到你眼花。
3. 清除目前清單中的記錄
4. 設定Filter: 超重要! ProcMon是廢鐵或是寶劍全看你會不會設Filter，後面再做詳細介紹
5. 指定桌面程式: 這個小瞄準器在SPY++裡很有名。如果你今天想要觀察某個桌面程式讀了哪些Registry、寫了哪幾個File，將小瞄準器拖拉到那個程式的UI上，ProcMon就會在Filter中加入限定該程式的條件\(指定Process ID\)
6. 搜尋: 在現有的記錄中找尋特定文字
7. 跳至Registry/File: 粉方便的功能! 在記錄中會看到某些Registry或File的名稱，點選那一列記錄後按下去，若是Registry記錄就會開Registry Editor停在該Registry Key上，若是File就會開啟FileMonitor停在該檔案的所在目錄上。在記錄上按右鍵也有個Jump To，效果相同。
8. 9,10 用來指定你要監聽的範圍，分別是Registry、File及Process活動，如果你只關心File存取，就只開啟File，真正的線索才不會被埋藏在一大堆沒用的Registry記錄中。





Reference: [http://blog.darkthread.net/blogs/darkthreadtw/archive/2007/08/18/977.aspx](http://blog.darkthread.net/blogs/darkthreadtw/archive/2007/08/18/977.aspx)

