# DeviceOn/BI Release Note
## DeviceOn/BI v-1.03.006 (2022-03-03)
### [Fix] ###
- [#28106][Datasource] Multi-language dropdown issue
- [#28120][#28122][Archiver] Bad MIN / MAX value of cumulative parameter (TimeInterval = recording rate)
- [#28109][Evaluator] Calculation parameter's calculation result failed.
- [#28121][Archiver] Missing Day/Month/Year data of discrete parameter
- [#28123][Datasource] While no HIS data of Constant / Text parameter within query time range, panel will get a null data.
- [#28125][Archiver] Bad Hour data (AVG) of Current parameter.
### [Update] ###
- [Panel][ene-report-panel] Support reportMerged function of datasource.
-   
## DeviceOn/BI v-1.03.005 (2022-02-22)
### [Fix] ###
- [#27888][Portal] Cannot display alarm group after create it.
- [#27921][Portal] Translation error
- [#27936][Evaluator] Calculation parameter's calculation result failed.
- [#27949][DashboardWizard] Some panels from template cannot display value properly
## DeviceOn/BI v-1.03.003 (2022-01-15)
### [Fix] ###
- [#27675][Worker] Cannot display RT data of constant parameter
- [#27676][Portal] UI Typo error
- [#27677][Evaluator] Calculation parameter no data
- [#27678][Portal] [Menu] malfunction of Marquee and Alarm setting 
- [#27716][datasource] YoYTrend function failed while cross day inquiry
- [#27723][datasource] Trending data with "Mark Alarm" function will display failed on group bar chart.
- [#27733][Portal] Notification page forever loading 
## DeviceOn/BI v-1.03.002 (2021-12-28)
### [Fix] ###
#### DataWorker ####
- [#27600] Wrong tag count of devices
- [#27601] No historical data while recording rate had been set

## DeviceOn/BI v-1.03.001 (2021-12-22)
### [New Feature] ###
#### Portal UI ####
* [Login] New login page with tabs to login to Dashboard or DeviceOn/BI Portal
* [UI] New header UI / New Quick start description(Settings -> Help -> Quick Start)
* [User Management] Support startup dashboard page setting ("User Management" -> Edit -> "Set startup dashboard page")
* [Menu] Support Marquee and Alarm setting.

#### My Devices (Device Management) ####
* [Repository] Allow user to use their own APP Repository for Application OTA (Need to purchase your own IoTSuite-AppHub first in Advantech WISE-MarketPlace)
  1. Add a Repo. in "Repository" tab.
  2. While using Application OTA function (in Applications tab -> Actions -> click "Application"), switch to Repository tab, change "Source" dropdown options to your newly created Repository.

### [Update] ###
#### Portal UI ####
* [Update][Menu Dialog][Select dashboard URL dialog] UI adjustment
* [Update] Highlignt item of device list / forwarding page 

#### Alarm Service ####
* [Update] New /alarm/rt/num API for RT alarm count
* [Update] New /alarm/rt/desclist API for Dashboard marquee
#### Datasource Backend ####
* [Update] YoYTrend function supports "Hour" (compare with same hour yesterday)
* [Update] new return fields of Alarmlog_record function 
  * almoccurrence: Alarm Occurrence Of This Month
  * almvalue: Current Value
  * equipparam: Parameter Name
#### Dashboard Plugin / Panels ####
* [Update][datasource plugin] New mark alarm functionality which can show alarm info on Trend chart (Need to use Group Bar chart panel to show it)

### [Fix] ###
#### Portal UI ####
* [#27490] Last Query Time / Last Successful Time will change while refresh page
* [#27553][Wizard][World Map][fix] Missing targets while New from existing
* [#27379][MyDevices] Wrong UI display
* [Org Setting] After disable Inspection, cannot enable it again.
* [Archiving] Fail to get Objects' icon
#### DBMaster ####
* [Fix] Wrong cacheUnit that will cause data always not cached in.
* [Fix] Always get blob data even if it still in DB
#### Archiver ####
* [Fix] Wrong init analog data
#### DataWorker ####
* [#26263] Didn't mark offline quality while the Device offline
#### Dashboard Plugin / Panels ####
* [Fix][EnE WorldMap] Kept Card Info in Panel json which will cause slow load speed


## DeviceOn/BI v-1.02.005 (2021-11-30)
### [Portal] ###
* [#27292] add object from device error
### [DataArchiver] ###
* [Fix] Wrong Min data calculation for discrete parameter

### [Datasource backend] ###
* [Update] groupStatusOccurrenceTable，groupStatusDurationTable，groupStatusAlarmOccurrence function
* [Update] display name support multiple variable (@tagname / @desc / @unit) combination. Ex. "@tagname (@unit)"
* [Update] ringratio function support new table / timeserie format

### [DBMaster] ###
* [Fix] Calculation function return null value while source data has bad quality.

## DeviceOn/BI v-1.02.004 (2021-11-26)
### [Portal] ###
Bug Fix:
* [MyDevice] Loading does not hide when there is no devices.
* [MyDevice] 修复tagList中status类型点value没有显示online/offline的问题
* [Object] parameter删除框英文单词不截断
Update:
* [Menu] User who have root-org. admin/Engieer permission can create/update/delete Menu in sub-orgs.
### [DataWorker] ###
* [Fix] Wrong JSON format ('infinity' value) for Archiver
* [Fix] Didn't release Redis CachedMap may cause data lost.
### [DataEvaluator] ###
* [Fix] Produce 'infinity' value without single quote in JSON Format
### [DataArchiver] ###
* [Fix] Some parameters have min data only, not have hour data.
### [Job Executor] ###
* [Inspection] 新增組織時, 沒有預設將Org owner加入inspection帳號權限

## DeviceOn/BI v-1.02.003 (2021-11-15)
### [Portal] ###
Bug Fix:
* [#26742] [Dashboard] Sync with Dashboard問題
* [#26838] 前端問題造成巡檢功能無法登入
* [#27008] [DM] 新增WISE/ADAM設備，卻沒顯示mqtt broker /port資料
* [#27020] [Profile] 新增profile，然後save，畫面會一值在loading
* [#27079] [Dashboard Wizard] 編輯2.1 Object Monitoring內的panel，在Alarm Status/Object status內沒顯示圖片
* [System Setting] 修复alarm category和alarm level删除时无法点击删除和取消按钮的bug
* [UI] 修正systemSetting和object的dialog样式并去除外层滚动条
* [Wizard][fix] 不支援的Panel只修改該panel的title & description, 其他json不動
* 
Update:
* [change] change the default number of page list to 50
### [api-portal] ###
* [#27103] codesys設備，上傳的tag有重覆，導致DM無法操作
* [Fix] device datavalue 转换为number的精度丢失问题
* [Fix] fix invite user 漏加inspection权限
### [dbmaster] ###
* [Fix] 如果value出現infinity字樣(不合法的json)會造成處理資料失敗
* [Update] enhance performance to get large number of devinfo

### [DataPacker] ###
[Fix] rename blob folder path (之前全部使用TagName, 造成Min以上資料讀取不到, Min以上需使用Parameter Name)

### [DataWorker] ###
[Fix] 设备上传 data 消息，以及设备上线/离线时，没有更新内存中 TagInfo 的 quality.
[Fix] 如果设备上线后这个点没有再传数据, 则不给补数据

### [Datasource Backend] ###
[Update] his data 取消上下线补null，改为按datasource plugin配置是否标记异常而多返回异常信息

## DeviceOn/BI v-1.02.002 (2021-10-26)
### [Portal] ###
Bug Fix: 
* [#26838] 巡檢功能無法登入
* [#26833] [Forwarding]新增MQTT+SSL ，但在rule使用這個auth，按test，卻fail
* [#26832] [User] Expired Date of a user in an organization異常
* [#26830] [Org] 手動新增Org, 但巡檢功能卻是啟用
* [#26749] [User Auth] 新增v1角色，只有Viewer權限，卻可以新增dashboard
* [#26742] [ErrorMsg] Sync with Dashboard 後無法正常編輯Dashboard
* [Forwarding] 新增Object or parameter後, 回Forwarding頁面無法看到新增的項目
* [Dashboard Wizard] graph panel編輯display name後按save, 出去後再edit一次, display name仍是舊的
* [Dashboard Wizard] Panel若綁定Parameter後, 這個Parameter被刪除了, 再次編輯此Panel時會無法選擇Parameter  
Update:
* [Dashboard Wizard] 支援配置EnE World Map card panel的Marker Type/Map Type屬性
* [Menu] Root Org的Dashboard分頁增加Menu子分頁配置此組織的SRPFrame
* [Menu] 增加theme配置
* [Device List] 優化調整 device list, 並調整為異步加載
* [Profile/Object/Archive] Remove the recording rate options which less than 1 min

### [DataSource Backend] ### 
Bug Fix:
* [#26735] Panel歷史資料顯示異常 (未按照TimeInterval回傳)

Update:
* Object List會顯示當前組織+子組織下的Object, Object以 "OrgName/ObjectName"顯示
* Function "report" renamed to "reportAnalogBasic"
* Add "reportMerged" function
  
### [DBMaster] ###
Bug Fix:
* [#26719] 透過dbmaster api去Get history calculated data，precise用month / year會出現error
* [Fix] Blob http client沒有正確init造成拿blob資料失敗
  
### [DataPacker] ###
Bug Fix:
* [#26714] 資料庫沒有配置資料, 回傳Error給前端, 造成Save Org失敗

## DeviceOn/BI v-1.02.001 (2021-09-29)
### [New Feature] ###
#### Device Management - Application management #### 
  * Support remote install/update/uninstall applications in UNO/TPC devices.
  * Co-work with WISE-PaaS/APPHub services.
  * Support Linux APP(Deb / Zip / tar.gz) & Docker APP (Docker Compose).
  
#### Inspection - Job Management (Previously named Issue Management) ####
  * Arrange your job and corresponding tasks in Patrol Inspection Portal.
  * Assign all the tasks at once after you finished the job arraangement.
  * Support Planning Job duplication.
  * Support PDF attachment type.

#### Dashboard Datasource ####
  * Add "Report" Function to return parameter's Max/Min/Avg/Last in Table format.  
### [Update] ###
#### [Portal] ####
  * [System] Adjustment of error Message notification UI.
  * [System] Add "Sync with Dashboard" dialog to handle the missing dashboard folder.
  * [Organization] Display create time and creator of the organization.
  * [Organization][Inspection Setting] QRCode of inspection URL
  * [Organization][Inspection Setting] QRCode of inspection APP download link
  * [Dashboard Wizard] Support General Dashboard creation (Edit/Create dashbord -> Basic Information -> Visibility).
  * [Dashboard Wizard] Add "Object Monitor (Reset)" Panel template.
  * [Dashboard Wizard] Add "URL" Setting in EnE Worldmap Card
  * [Forwarding] Support MQTT+SSL
  * [User] Expired Date of a user in an organization. (Default value = "No Limit")
  * [User] Mark of Organization Creator and let creator cannot be deleted.
  * [Object] New formula description UI in Calculation Parameter setting.

#### [Portal Backend] ####
  * [Fix] device configuration update may cause corresponding object's alarm disappear.
#### [api-hub] ####
  * [SSO] Get OrgList by SSO user's privilidge
  * [API] Change input parameter of (POST /dbmaster/data/RawData/query)
  * [API] Add fixed interval data API (GET /dbmaster/data/fixedScale)
  * [API] Add get interval list API (GET /dbmaster/interval/list)

#### [Archiver] ####
  * [Update] Cache the intermidiate data in local memory to improve performance
  * [Fix] Faild to process new "discrete" parameter

#### [DataPacker] ####
  * [Refactor] Increase the number of gorutine to handle RAW data


## DeviceOn/BI v-1.01.007 (2021-09-10)
#### [Portal] ####
Bug Fix:
* [#26387] 在org內新增用戶，按取消，卻不能關閉
* [#26359] New From Template產生的Dashboard，沒有依設定"僅顯示組織層次結構"

#### [DataWorker] ####
Update:
* 只有recording rate > 0 才保存RAWData

Bug Fix:
* Redis connection overflow

#### [DBMaster] ####
Update:
* Increase gorutine to 100 to handle scale data
Bug Fix:
* Faild to scale data of constant parameter
* Get RAWData delete time by object ID (Cannot by device ID in 1.01 version)

#### [Notification] ####
Bug Fix:
* Cannot display preview message with "Others" if it has space in "Others" string

#### [Archiver] ####
Update:
* Revert version to 1.00.011

## DeviceOn/BI v-1.01.006 (2021-08-26)
#### [Portal] ####
Bug Fix:
* [#26223][Blob] 設定Azure blob後，按save後，沒有lock住畫面，就可操作其他功能
* [#26215][Object] copy to my org生成的object，parameter內的最大變化率 / 分鐘 是10000
* [#26206][DM] 上傳adam後，點列表會顯示異常
* [#26195][Dashboard Wizard]新增空白dashboard, save後, 就一直loading
* [#25618][Forwarding]處理Request Body格式有誤
* [Forwarding]當authentication List是空的, 從Forwarding List切過去再切回來, Row Per Page選單會變成1

Update:
* [Object][User] object list,user list头像懒加载
* [Parameter] 累算点最大变化量默认值改为999999999 
 
#### [DataWorker] ####
Bug Fix:
* [#25546]ADAM/WISE設備斷線後，燈號還是綠燈

#### [datapacker] ####
Update:
* 加大設定Azure blob的Timeout

#### [Archiver] ####
Bug Fix:
* 存数据时没有根据 equipid 计算出 hashcode 导致当 equipid >= 128 时数组异常

Updated:
* 使用內存處理min/hour表
* 去掉 ene_data_d_min 数据表
* 2倍recording rate以前的tmpdata從內存中移除, 避免memory leak

#### [api-org] ####
Updated:
* datasource datatype拿掉ACCUM

#### [api-subscribe] ####
Updated:
* 新增支援訂閱advanced subscribe(5000 parameters)模式

## DeviceOn/BI v-1.01.005 (2021-08-17)
#### [Portal] ####
Bug Fix:
* [#26137][DM] 上傳Adam6051後，無法設定configuration
* [#25933][Plugin/forwarding] 在繁中語系，刪除auth，出現的提示訊息卻是簡中
* [#25922][Dashboard Wizard]建立2.1 Object Monitoring dashboard，部分panel無資料
* [#25835][Object]Device copy to my org後生成的Object, 編輯該Object會無法SAVE
* [#25619][Forwarding] 使用patch方法無法測試成功並SAVE
* [#25618][Forwarding] 使用put方法無法測試成功並SAVE
* [Forwarding] 若Auth有被Forwarding Rule使用, 應該要阻擋刪除該Auth
* [Org Setting] 修复save org后blob信息没有更新，影响days to object data设定的bug
* [Dashboard Wizard] 修正用戶從Dashboard修改dashboard後, JSON結構改變(多了i18n多語言), 而Wizard後續無法修改的問題
* [Plugin] 修复删除authentication，页面loading卡住bug
  
Update:
* [Subscribe] 增加advance subscribe的序號支援
* [Dashboard Wizard] Switch Panel修改可獨立開關object/parameter/timeinterval的設定介面
* [Inspection] 巡檢在disable狀態, 分頁顯示Service disabled訊息

#### [Portal-backend] ####
Update:
* Subscribe增加advance subscribe的序號支援

#### [Archiver] ####
Bug Fix:
* 取消使用tmpdataAvg/tmpdatasum/tmpdatadiscrete中間表, 解決數據量大時, mongodb存取緩慢的問題

#### [dbmaster] ####
Bug Fix:
* Cumulative Parameter的AVG(差值)計算方式有誤
* Scale api回傳值的timestamp會飄移
* 日資料以上, 沒有回傳Parameter所在時區的00:00:00
* 如果帳號有大寫字母, 會找不到組織的Auth資訊  
Update:
* 新增TopViewableOrgs給api-org使用, 可顯示用戶權限能看到的根節點列表
* 當Panel顯示點數上限足夠時, 不主動scale, 而是直接返回資料庫的數據

#### [datapacker] ####
Update:
* 若備份失敗會寄通知email到組織的creator
* 接收notify/cfgchange mqtt消息, 取得刪除組織的通知, 並刪除相關Blob資料

#### [api-org] ####
Bug Fix:
* ringratio的同天/同小時, 改取用資料庫中的AVG數據來計算

Update:
* 取消同週期上下線時, 會畫一條下引線的行為, 改為和下線相同(顯示null)

## DeviceOn/BI v-1.01.004 (2021-07-14)
#### Knowing Issues ####
* [Forwarding] 若Auth有被Forwarding Rule使用, 應該要阻擋刪除該Auth
* [Portal] Device copy to my org後生成的Object, 編輯該Object會無法SAVE

#### [Portal] ####
Update:
* [Org Setting] External Blob Setting in Root Org Settings
* [Inspection Setting] 若Inspection Disable, 優化畫面顯示為Service Disabled
  
Bug Fix:
* [#25743][Device] SA空間，新增WISE/ADAM，port無法切換
* [#25810][SRPDashboard] 用New From Template建立dashboard，preview無法看到資料
* [#25809][SRPDashboard] 用New From Template建立1.1 Organization Overview Water，无法选择组织。
* [#25807][Plugin] 新增Plugin，SAVE後，再新增Plugin會有殘留資料
* [#25776][Plugin/Forwarding]檢查json format功能，只輸入數字，檢查卻是正確
* [#25745][Plugin/forwarding] auth已經被使用，再去刪除，出現的提示訊息異常
* [#25619][Forwarding] 使用patch方法無法測試成功並SAVE
* [#25618][Forwarding] 使用put方法無法測試成功並SAVE
* [#25607][Plugin] 按refresh按鈕，顯示成功，但狀態還是fail
* [#25593][Plugin] 設定plugin時，在配置output有相同的部分，會導致計算公式轉換錯誤

#### [dashboard-API] ####
Bug Fix:
* 只存在子組織的Admin/Engineer/Operator不能寫值, 會出現Error提示

#### [api-plugin] ####
Update:
* 刪除Org時, api-plugin訂閱消息, 並刪除該org相對應的plugin資源

## DeviceOn/BI v-1.01.003 (2021-07-05)
#### [Portal] ####
Bug Fix:
* [#25542][Device Group] 編輯group內的Description，SAVE後，卻還是空的
* [#25543][Device Group] 紅色框內的按鈕名稱，切換語系後，也都是英文
* [#25545][Device Group] backup權限不能把另一個backup user刪除
* [#25547][Device Group] 在設備上面，點選"從組織中刪除"，出現的提示框訊息有問題
* [#25550][Device Group] 用manager去把另一個backup user改成viewer，卻不行
* [#25553][Device Group] Device Name太長，會超出框外
* [#25562][Device Group] 註冊新帳號，再從存在的group加入新帳號，但新帳號內的group卻還是空的
* [#25576][Plugin] 新增bearer Auth，save後，再去編輯，api body 會變成之前殘留的資料, token密鑰也消失
* [#25577][Plugin] 新增Plugin，SAVE後，卻出現error
* [#25579][Plugin] 新增Bearer頁面 提示不正确
* [#25584][Plugin] 新增Plugin，SAVE後，再去編輯，出現異常
* [#25589][Plugin] 在org內新增parameter後，plugin功能會被disable
* [#25604][Plugin] preview result是fail，但message卻是顯示success
* [#25605][Forwarding] 新增Basic/MQTT Auth，save異常
* [#25611][Forwarding] 增加MQTT forwarding，topic用二個變量，按測試卻不是送到對應的topic
* [#25613][Forwarding] 在Payload參數增加時間，參數時間是指定常數量parameter，按測試卻沒回應
* [#25616][Forwarding] 查詢狀態為200，但卻是X(fail)

#### [api-plugin] ####
Bug Fix:
* [#25541][Plugin] 當plugin引用的计算点是每秒運算一次，會導致内存寫滿，plugin無法運作 (加上ARC演算法)

#### [Datasource API] ####
Bug Fix:
* [#25591][Datasource]在Grafana增加singlestat panel，卻沒顯示資料
* [#25541]用New From Template建立2.1 Object Monitoring和4.1 Alarm Report，preivew卻沒有資料 

#### [DBCreator] #### 
Update:
* 改變讀取dashboardTemplate / panelTemplate方式為從json檔讀入

## DeviceOn/BI v-1.01.002 (2021-06-11)
#### [DBCreator] #### 
Bug Fix:
[#25489] Cannot add/delete Org or Object (caused by missing DB fields)

#### [Portal] ####
Update:
* [Profile] Profile card highlight
* [Menu Management] Menu Management highlight


## DeviceOn/BI v-1.01.001 (2021-06-07)
[New Feature]
* Plugin Service 
  * Allow user to integrate 3rd party API data into DeviceOn/BI
  * A plugin function defines one API call
    * Support OAuth2 / Basic Authentication / Bearer / User defined string method of Authentication
    * Can define input source from BI Parameter or fix string
    * Can define one to many output from JSON format of API response body
  * A plugin function can only be defined in Root Org.
  * Plugin functions of a root org can be shared within this root org and it descendant orgs.  
* Forwarding Service
  * Allow user to forward BI data onto 3rd party API / MQTT position
  * A forwarding rule defines one rule to forward data onto an api or a MQTT topic
    * Can define request body JSON format
    * Can define variable of JSON data and bind the variable with BI parameter
  * A forwarding rule can be defind in any level of org.
* Device Group in Device Management
  * Allow user to organize their devices by group
  * A group can be shared to other users.
  * User can view group as chart or list.
* External API Interface - api-hub-deviceon-bi
  * Integrate DBMaster API with sso token validation

[Update]
* [Portal] Calculation Parameter UI update
  * Integrate Plugin function list
* [Portal] Create Profile from device
  * New UI flow to create a profile from device
* [Dashboard Panel] Panel & display update
  * EnE Dashboard switch panel
  * EnE alarm panel
  * Datatable with monitor function 
  * Hide Org / Object id (#xxx) in dropdown list of data source
* [DBMaster] Support set parameter value
  
---
## DeviceOn/BI v-1.00.011 (2021-05-21)

### [Portal] ###

Bug Fix：

* [Parameter] 修复计算点公式中参数关联param name有冒号时显示和保存不完整的bug
* [User] 修復Org->User tab的loading樣式不起作用
* [Subscribe] trial/subscribe頁面, create org添加校验特殊字符与org校验保持一致
* [System Setting] role setting中, Value / Alarm設定列消失
* [System Setting] License Setting設定trial org的expired date失敗 

---
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


