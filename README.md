# DeviceOn/BI Release Note
## DeviceOn/BI v-1.00.010 (2021-05-14)

### [Portal] ###

Bug Fix：

* [#24990] [DM] Tag Type顯示錯誤
* [#24960] DM功能內的configure異常
* [#24958] 在object分頁，繁中語系翻譯錯誤
* [#24951] 在dashboard分頁，新增樣板儀表板，sava後，點預覽儀表板，在回來BI，點新增空白儀表板，會出現空白畫面
* [#24950] 新增wise device，輸入mac，11-11-11-11-11-11-11，save後，在去edit，連線類型卻變成IMEI code
* [#24949] [Menu Management] filter功能異常
* [#24945] 新增警報群組，不用設定名稱，也可以save
* [Org Setting] 修正root org的inspection的dccsUrl的设置 (之前為固定字串)
* 
 
Update Lists：

* [Org Setting] Enable / Disable Inspection設定
* [Home] 開啟Archiving Icon

### [Datasource API] ###
* [Fix] duration/occurrence number recording rate 和 time interval 冲突, 造成多補數據

## DeviceOn/BI v-1.00.009 (2021-04-20)

### [Portal] ###

Bug Fix：

* [#24648] 在DM功能的Devices翻頁，查詢tag #MSYS_EdgeStatus，#符號搜尋不起作用
* [#24571] Advanced Setting - Role功能可以設定Device Configuration權限，但目前所有人都可以新增Device
* [#24569] User Management - filter功能異常
* [#24548] 註冊新帳號，繁中語系的按鈕翻譯錯誤
* [#24541] Profile Mangement新增profile，上傳alarm code xls，按save後會出現error
* [#24540] 從既有儀表板新增dashboard，然後刪除dashboard後，再新增，會導致畫面異常
* [#24539] 新增空白儀表板，加入圖表6個panel，但Water Achieving Rate panel會顯示NA
* [#24536] 上傳WISE 4051的Configuration設定COM，在Slave Response Timeout和Delay Between Polls顯示error提示異常
* [#24520] 上傳WISE 4051的Configuration設定COM，在Stop Bit顯示異常
* [#24484] Notification Message 訊息內容部分有錯(文字點)
* [#24483] Dashboard Panel : Avg.Availability / Running time of whole plant 兩個值顯示異常
* [#24446] 新增LoRa設備，再刪除，就無法再增加原本設備
* [#24407] 設定parameter的最大變化率 / 分鐘為100，然後SAVE AS PROFILE，但在profile看到的最大變化率 / 分鐘卻是1
* [#24402] 連切換通知和事件，有時會沒顯示通知的資料
* [Fix] 解决从home点击object dashboard，界面loading不停止bug
* [Fix] 修正修改优化代码用户对组织没有权限/组织过期tabList启用和禁用功能导致的bug(org畫面loading不停止)
* [Fix] Org List權限顯示修正
  * 用户对于没有权限的org解开权限，tabList要打开disabled。
  * subscribe org过期，重启成功打开disabled。 
  * 跳转到过期的subscribe org，要disabled tabList。
  * 删除org要看用户有没有权限判断展开还是禁用tabList。
 
Update Lists：

* [Update] Archiving畫面優化
  * 支援批次調整recording rate
* [Update] Object畫面優化
  * 支援從Object List內的Organization名稱連結，快速跳轉到該組織
* [Update] DM 調整 Downlink Command History 的 table 不使用樹狀結構顯示多筆 payload 資料，僅顯示總和資訊

   
### [Worker] ###
Bug Fix:
* [Fix] isensing 设备发送 cfg 数据后会先删除所有已有的 tag，然后再一个一个加回来。
* [Fix] 修正了设备发生 UeD 离线后 Redis 中 quality 不更新问题。
* [Fix] Mongodb.deviceInfo.active 的值经常发生错误的问题。改为将 active 和 activetime 一起更新。
  
### [Data Archiver] ###

Bug Fix:

* [Fix] 状态点min数据统计，若原始資料只有一筆，沒有每個recording rate算一筆數據進去資料庫，造成無數據

### [Datasource API] ###

Update list:

* [Update] 更新 get duration/occurrentnumber history data 的 dbmaster api
* [Update] 修改 duration his data 补数据时，按 parameter recording rate为 interval

### [DBMaster] ###

Bug Fix:

* [Fix] DBMaster補的數據也被加入了cache造成Dashboard顯示異常
* [Fix] Digital資料秒數加總，沒有考慮狀態，造成每個狀態算出來的值都相同

 ## DeviceOn/BI v-1.00.008 (2021-03-16)

[Portal]

Fixed all test bugs：

* [#24223] 語系改成繁中，alarm group內的參數設定，卻是空的
* [#24230] 刪除報警用戶群組，再新增，會殘留舊資料
* [#24281] parameter的報警功能無法關閉
* [#24283] org內的Notification，使用測試email，會出現error
* [#24293] 新增org，有出現error，parameter en cannot be null or undefined

Update Lists：

* [Fix] Parameter description輸入單引號會無法儲存
* [Fix] Menu Management create/delete srpframe 時帳號認證失敗
* [Fix] ADAM-6060 configuration issue
* [Fix] Group bar chart - 當laft/right Y軸第一個Parameter的data type不是digital時, 隱藏decimals tooltip
* [Fix] 開通帳號激活码添加校验，A-Z 0-9 16位
* [Fix] 刪除device時, 殘留Model type在filter中
* 
New features:

* [New] Enable create TPC Device
* [New] SRDDashboard新增Graph類型
* [New] LoRa device downlink feature
* [New] Archiving功能 - 快速設定Object / parameter資料保留策略與時間


[Portal Backend]

Update list：

* [Fix] 修改 notification url 为 service格式
  

[Data Archiver]

Update list;

* [Fix] 修改 scheduler 中任务调度部分，解决 task 一直占着 timer 的问题

[Datasource API]

Update list:

* [Fix] 修復Dashboard寫值異常問題

[DBMaster]

Update list:

* [Fix] 因帳號大小寫問題導致無法拿到authstring, 改為全面使用lowercase

New features:

* [New] add graphql mutation to set parameter RT data
---
## DeviceOn/BI v-1.00.007 (2021-3-3)

[Portal]

Fixed all test bugs：

* [#24114] 在edgelink的device，用copy to my org，但object裡面只有1個parameter，修改为edgelink/webaccess scada 不支持copy to my org，需要到组织里用自行创建，会弹出如下消息：“Copy to My Organization does not support SCADA or EdgeLink. Please use Add New Object function in target organization.”
* [#24115] 修正新增profile，加入一個parameter，但recording rate預設是1分鐘
* [#24125] 修正從My Devices，使用copy to my org，當Parameter Quota超過，出現的error異常
* [#24126] 在Home page的左上角汉堡包按鈕，但點下去也沒反應

Update Lists：

* 设备上线状态点 EdgeStatus状态修正
* system setting样式修正，license显示creator栏位，去掉超出total quota的校验，修正错误信息覆盖右侧表格的问题，改为表头显示；
* 修正create object from device，tag的分页number设置与 get all重复导致页面渲染失败的bug；

[ Portal Backend]

Update list：

* 使用http-proxy-middleware 中间件, 支持Http和Https访问;
* {post} /update/parameter/all/deviceobject 新增 hbt 字段，用于worker 动作 portal 更新 device heartbeattime。worker 调用时拿不到token，先改为直接跳过，使用 query.from  = ’worker‘，校验访问源；

[ Data Worker]

Update list：

* 新增功能：设备 Config 信息发生变化时给 Portal-API 发送通知；
* 新增功能：设备网络掉线事件（UeD）延迟处理以避免误报；

[ Data Archiver]

Update list;

* 调整删除ene_tmpdata*_dailybak数据的时间，由固定凌晨3点改为每6小时删除一次，每次保留最近24小时的数据，目的为避开测试空间自动部署的时间；

---

## DeviceOn/BI v-1.00.006 (2021-1-26)

[Portal]

Fixed all test bugs;

* [#23792] 在子層(11)可以看到3個dashboard，再去點org path的父層(00)，但dashboar資料沒有更新
* [#23813] 4012E_157_0112這個設備是連線中，但卻左邊圖像卻是紅燈
* [#23814] 語系設定出現空白
* [#23818] WISE 4012E內的I/O Channel，parameter name的前面有6
* [#23820] 新增org出現error，也沒有出現同名的object
* [#23827] 新增uno設備，輸入mac，按生成，再去按test connection，卻出現error
* [#23828] 新增TPC設備，但沒有地方可以設定型號，mac也不能輸入
* [#23839] 上傳adam 6060，ch1是counter mode，Min Low/High Signal Width和adam utility顯示不一致
* [#23841] 從device建立object，但scada設備可以上傳的tad只剩1個
* [#23852] 從My Devices，使用copy to my org，沒有判斷Parameter Quota
* [#23853] 設定Notification Message格式跑掉
* [#23854] 在System Settings > Advanced Setting > System Notification > Wechat，設定完後，按save，畫面一直停在loading
* [#23855] enable/disable Notification Groups狀態，彈出的通知內容空格很大

[MyDevices]

1. MyDevice relatived micro-service update to version 1.00.006

[ Data Worker]

Update list：

* 新增功能: auto fill tmpdata every 5 minutes for that not changed for long time tags.

---

## DeviceOn/BI v-1.00.003 (2020-12-17)

[API-Portal]

Fixed all test bugs;

[Portal]

1. Support 3 scenarios: device management , trail, subscriptionmode;

[MyDevices]

1. MyDevice relatived micro-service update to version 1.00.003

---

## DeviceOn/BI v-1.00.002 (2020-12-07)

#### [Dashboard Plugin]

Fixed:

* [#23026] 使用template建立1.1 Organization Overview Water dashboard，然後觸發alarm，但dashboard卻沒顯示alarm;
* [#23046] 使用template建立dashboard，有使用到Grouped Bar Chart Panel顯示異常
* [#23050] 在3.1 Inflow pumping station，切換object，Water Flow In-Out Panel都顯示N/A
#### [Portal-WISE-MPlus]

Fixed:

* [#23047] 使用profile(AutoTest_Profile)建立object後，object內沒有設定alarm， 但topic(valchg)卻收到資料;

---

## DeviceOn/BI v-1.00.001 (2020-12-07)

#### [ALL]

Update:

* 支持Device Management
* 支持Trial/Subscription
* 支持巡检派工
* New UI
#### [Portal-WISE-MPlus]

Fixed:

* [#23047] 使用profile(AutoTest_Profile)建立object後，object內沒有設定alarm， 但topic(valchg)卻收到資料;

---

## DeviceOn/BI v-1.00.00*

[Summary]

Three kinds of user scenarios in iiot-operated Edition

1. Device Management
    * Sign up for free
    * Can use device management functionality only
2. Trial
    * One month trial program with 1 trial organization & inspection
    * 1 WISE Point / 150 parameters
    * Org. valid in 30 days and will be auto deleted after 30+30 days.
3. Subscription
    * Subscription program with 1 subscribed organization & inspection
    * 15 WISE Points per month / 2000 parameters
    * Can redeem extra parameter through Market Place

[UI Update]

**Organization**

1. [Change] Org.’s functional items from waterfall to tabs
2. [Add] Inspection
    * Each root org have one inspection site.
    * While trial/subscription Org. created, DeviceOn/BI creates a K8S namespace for installing Inspection pod.
        * Namespace naming rule : inspection<orgId>
        * Example: inspection34
    * After installation, each inspection have an unique website:
        * URL naming rule:[https://inspectionapp-](https://inspectionapp-)<namespace>-<cluster>.<datacenter>.<domainUrl>
        * Example:[https://inspectionapp-inspection16-eks013.hz.wise-paas.com.cn](https://inspectionapp-inspection16-eks013.hz.wise-paas.com.cn)/
    * BI Portal embed inspection portal by iframe.
    * While add / modify / unbind Org.’s users, BI will also add/modify/disable the corresponding inspection users.
    * Delete inspection pod & namespace while this org is being deleted.
3. [Change] Move “Alarm Group” function into “Event” tab
4. [Change] Move “User Group” / “Notification Group” functions into “Notification” tab

**Objects**

1. [Add] “BI data lifecycle” setting in each object.
    * Days to keep Minute data
        * Default : 7 days, Min value: 7 days, Max value: 731 days
    * Days to keep Other data
        * Default : 60 days, Min value: 60 days, Max value : 731 days
2. [Modify] Parameter – Recording Setting
    * Recording Rate:
        * Default = Do not record
        * Revert the dropdown list item : “Do not record” -> 60 min -> …. -> 1 sec
    * Hide “Group Recording”
    * “Days To Keep Data” -> “Days To Keep RAW Data”
        * Default: 3 days, Min value = 0 days, Max value : 30 days

[New micro service]

1. [Add] Data Packer micro-service
  * Support packing MongoDB data into Azure blob
    * rawdata
        * Pack to /datapacker/Rawdata/(objId%10)/(objId)-(parameterName)/timestamp.csv
        * Timestamp = 00:00:00 UTC of each day
        * 1 file per day per parameter
    * d_min
        * Pack to /datapacker/D_Minute/(objId%10)/(objId)-(parameterName)/timestamp.csv
        * Timestamp = 00:00:00 UTC of each day
        * 1 file per day per parameter
    * discreterecording_min & a_min
        * Pack to /datapacker/Minute/(objId%10)/(objId)-(parameterName)/timestamp.csv
        * Timestamp = 00:00:00 UTC of each day
        * 1 file per day per parameter
    * hour
        * Pack to /datapacker/Hour/(objId%10)/(objId)-(parameterName)/timestamp.csv
        * Timestamp = 01/01 00:00:00 UTC of each year
        * 1 file per year per parameter
    * Day
        * Pack to /datapacker/Day/(objId%10)/(objId)-(parameterName)/timestamp.csv
        * Timestamp = 01/01 00:00:00 UTC of each year
        * 1 file per year per parameter
  * trigger “DELETE mongoDB data” message to Data Cleaner
      * With blob address configuration
          - Rawdata: delete data before 5 days ago
          - Min data: delete data before 7 days ago
          - Hour / Day : delete data before 45 days ago

      * Without blob address configuration (standard version)
          - Use Object setting (days to keep Min / Other data) & parameter setting (days to keep RAW data)
  * Clear Blob by user’s setting
      * Use Object setting (days to keep Min / Other data) & parameter setting (days to keep RAW data)
  * Get Data APIs (internal use)
  * Update data APIs for data resuming (internal use)
2. [Add] Data Cleaner micro-service
    * [Add] Delete RAWData by drop collection
    * [Add] Delete RAWData by parameter
    * [Add] Delete data (deviceInfo / rtdata / rawdata) by Device
    * [Add] Delete data (tagInfo / rtdata / rawdata) by tag
    * [Add] Delete Historical data (min/hour/day/week/month/year) by object
    * [Add] Delete Historical data (min/hour/day/week/month/year) by parameter
3. [Add] MyDevice relatived micro-service
    * [Add] api-dm
      API Support for DeviceON/BI Device Configuration, FOTA, COTA
    * [Add] portal-manage
      Management Portal for Define Device Model Profile
    * [Add] api-manage
      API Support for Management Portal
    * [Add] mqtt-proxy
      MQTT+SSL Proxy for DeviceON/BI Portal to Monitor Real Time Data
    * [Add] device-config
      Handle Device Configuration, FOTA, COTA Command by MQTT


