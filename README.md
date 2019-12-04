# WISE.M+ Release Note
---
## **0.81.001 (2019-12-3)**
> **[Bug Fix]**
> *  **Proxy**
>       - [Proxy]   
>           1. [Update] use api-profile-proxy  URL instead of apm URL
> *  **Dataworker**
>       - [Enhance]
>           1. [Fix] bugfix: 一个 device 出现异常数据后被设置 ErrCode, 异常消除后 ErrCode 未清除。
>           2. [Update] 增加设置 10 秒的 MongoDB serverSelectionTimeout 时间，
>           3. [Update] 增加设置 10 秒的 MongoDB socketTimeout 时间，
>           4. [Update] 加载 device 资料时，略过 edgeid 为空的 device。
>           5. [Update] 加载 device 资料时, 若 edgeid 两端有空格, 则先修剪空格。
>           6. [Update] 删除 device 时，devicertdata 可能删除失败, 所以再以 edgeid 为条件删除一次。
>           7. [Update] TotalObjects() 函数参数定义更新: 若 objectType 传负值, 则认为任何 objectType 都符合查询条件。
> *  **Menu Management**
>       - [CSS Bug]
>           1. [Fix] bugfix: 修正新增拖拉&收合功能後產生的menu tree css bug。
> *  **Profile**
>       - [Parameter UI]
>           1. [Fix] bugfix: 在Parameter List中的Formula cell增加ellipsis(...) 讓超出長度的文字以...表示。
>           2. [Fix] bugfix: 修正category 輸入框顯示高度太窄問題。
>           3. [Fix] 修正hover category tag時，Delete button出現圓圈並超出外框
>           4. [Note] APP_ENV : development 的時候指向cn 其他值指向.com
>       - [Excel]
>           1. 新增Excel欄位Validation, 並顯示每個錯誤的Cell欄位 :
>           2. Information分頁
>              a) profileName 未填or只填空格
>              b) mode 未填or只填空格
>           3. Parameter分頁, 必填欄位未填or只填空格
>              a) 不分類型的必填欄位包含
>                    parameterName / paramType / dataType / value / 
>                    groupRec / recRate / dataKeptDays
>              b) Number類型額外必填欄位包含
>                    spanHi / spanLo / decimalPrecision / recType
>                    maxChangeRatePerMin
>              c) 計算點額外必填欄位包含
>                    calcRate / formula
>           4. 其他分頁的parameterName未填or只填空格 
>           5. spanHi < spanLo
>           6. span Hi, spanLo, decimalPrecision不是number
>           7. 錯誤的 paramType and dataType
>           8. parameterName重複或含有特殊字元(目前特殊字元只允許-_)
>           9. Alarm Code Excel新增ja欄位
> *  **Portal**
>       - [Object UI]
>           1. [Fix] bugfix: 修正Defect #18553 新建object from profile會拿到非預期的圖片。
>       - [new feature]
>           + group/organization 
>           + 修改建组织的操作流程：建组织第一步先选模板(可不选)
>           + 新建组织时创建默认物件，与组织同名。更新组织时同步更新默认Object 
>           + 修改语言切换bar位置
>           + 添加头部引导条
>           + 经纬度改为必填，如果可以获取到来自Google提供的api 的经纬度，用获取的经纬度，拿不到研昆山研华经纬度当默认值
>           + worldmap template 添加清空按钮，可不填
>           + 编辑模式下隐藏引导条
>           + object 
>           + select parameter
>           + 界面新增 block type
>           + 默认展示的参数个数从10改到30
>           + parameter type 列添加筛选功能
>           + 选择模板添加清空按钮，可不选
>           + profile list 添加过滤，值显示public 或者当前用户自己建的profile
>           + select tag
>           + 修改操作按钮的图标
>           + setup object
>           + 编辑参数时，param name和rule name 不可修改, 修改param删除时候的确认提示 、 rule name 删除时候添加确认步骤
>           + from device 创建 object 时，来自区块的点保存为模板时参数名去掉区块的名字
>           +  新增object 时候将当前Object 的id 从'>           +1'改为 '@equipId'
>           + 计算公式里所有自定义函数存给后台时添加两个参数：当前的 orgid、objectid。用 @orgId 表示正在创建的group id,@equipId 表示正在创建的Object id
>           + 添加 calcFormulaDisplay 字段
>           + 修改 stateTxt 默认字段为'[[0,0],[1,1]]'
>           + 添加自定义函数的跳转页面
>           + 修改从profile 建object 时绑定设备时的取值逻辑：设备点config优先，如果设备config 参数值为空或者没有配置则取来自    profile 的值。
>           + save as profile 的 owner 统一转换为全小写
>           + 编辑模式下隐藏引导条
>           + home 新增 Home page 
>           + header 新增item：'home' 用于回到 home 页面
>           + organizationManagement 
>           + 锚点跳转时候展开相应的列表
>           + object list
>           + 新增 org./group 列
>           + 列出有权限的所有object(上一版本只展示当前组织的object)
>           + 显示默认object(包括子节点的默认object)
>           + 添加 view button(子组织的默认object父节点只有view 的权限)
>           + common
>           + 处理文字溢出
>           + 如果有多层弹框, cancel 按钮需要确认表示结束进程，点击确定将关闭底层所有弹框。
>        - [fix]
>           + group/organization 
>           + 英文語言編輯organization視窗上的標題文字為Edit Group
>           + object 
>           + select parameter
>           + 默认选中的模板和参数不对应
>           + setup object
>           + 从模板读取记录类型没有读取，保存为模板时记录类型没有保存
>           + deadBand delayTime、restoreDelayTime、deadBandType 字段无法存储(alarm 组件JSON 有更新)
>           + header 
>           + help里面的quick start 文字溢出
> *  **API Portal**
>       - [new feature]
>           1. edge add errcode
>           2. edge blocktypename 不区分大小写
>           3. org Admin可以添加new user
>           4. 添加非space manager不能删除root org的限制
>           5. 添加root org的admin可以看到所有子组织不管是否有权限；并且可以把自己加入没有权限的组织中
>           6. alarm tag group支持报警区间多选
>           7. M+ Admin对应Dashboard org Admin M+其余角色对应viewer
>       - [fix]
>           1. fix alarm notification messageccontain '' ""创建notification group会失败的问题
>           2. 如果org下面已经创建alarmusergroup删除org会失败的问题
>           3. fix 当notification权限scope已存在时报错的问题
> *  **Notification Group**
>       - [UI]
>           1. [Fix] bugfix: fix submit get error when description is empty and the first time create notification group-dev,fix submit get error when description is empty and the first time create notification group.
>           2. [Fix] 修正Create Notification Group時，若不輸入description, Submit時會出現error
> *  **Data source**
>       - [Raw Data]
>           1. [Update] 分钟历史数据，查询范围起始补前一笔数据，2.新增rawdata，limit为900。
>       - [New Features]
>           1. datasource新增displayname dropdown
>           2. 新增历史数据Minute,Day,Week,Month,Year支持补数据
>           3. 新增rawdata原始数据，返回结果上限900
>           4. datasource新增cumulate datatype
>           5. 提升hisdata，rawdata查询速度
>       - [fixbug]
>           1. 修复rtdata返回结果在graph panel中不显示问题
>           2. 修复digital点历史值查询不到问题
>           3. 修复graph legend与时间轴不对应问题
>           4. 修复部分查询不能返回target问题
>       - [function type]
>           1. objectmonitor返回结果新增column
>           2. 新增object/groupStatusDuration/Occurrence，object/groupAvail计算digital点状态发生时数，启动次数及时间稼动率
>           3. objectmonitor，alarmlog_rt，alarmlog_his，worldmap使用M+ object设置的【Additional Message URL】作为额外信息链接
>           4. worldmap支持cumulate数据
>           5. alarmlog_rt新增parameter作为返回数据的column

## **0.80.008 (2019-11-11)**
> **[Bug Fix]**
> *  **Portal**
>       - [Object]   
>           1. [Fix] Fix bug Defect #18458 建立object將左側DataSource移至右側時會選不到測點
>           2. [Fix] Fix bug Defect #18457 建立object時，點擊所新增設備測點名稱DataSource欄位為空白
>       - [Alarm]
>           1. alarm group的 alarm rules的多选框默认选择一项，清空后取消勾选，发生修改时user management，space manager被邀请的用户不允许修改信息，list 的按钮显示为view图标，创建space manager时对非当前用户创建的子用户添加邀请机制
## **0.80.007 (2019-11-01)**
> **[Bug Fix]**
> *  **Portal**
>       - [Object]   
>           1. [Fix] Click ‘>’ when no device information is requested, and the device information will be requested automatically until the data comes back, and then the data will be moved from left to right;
>           2. [Fix] Add description for 0,1 change stateTxt from ‘’ to ‘[[0,0],[1,1]’
>           3. [Fix] Fix constant point data type error when coming from profile change 31/32/33 to 11,12,13;
>           4. [Fix] Fix the bug that parameter DOM does not update sometimes after paramtype changes;
>           5. [Fix] Fix bug defect #18307:alarm 在object裡的參數設定警報時，range類型的H警報無法由>=改為>;
>           6. [Fix] Fix bug: “==” was mistaked to “/ b ==”
>       - [Device]
>           1. [Fix][device 时间戳] edit 时间戳可以修改 Edit device timestamp to be modifiable;
>           2. [Fix][tagInfo]  列表 unit 重复 tagInfo list unit field displays Unit
>           3. [Fix][iSensing] iSensing生成按钮disabled, User clicks "Generate" button get username and password. "Generate" button could not be clicked before the data came back. After the data was responsed successfully, it became clickable;
>       - [Profile]
>           1. [Fix] 如果Excel中，Complex Alarm只設定一個Range上傳會失敗;
>           2. [Fix] 檢查完整份Excel後顯示完整錯誤 目前支援檢查：
>               - parmeterName : Empty / include special symbol / duplicate /  only contain space
>               - paramType : Empty
>               - value : Empty
>               - dataType : Empty
>           3. [Fix] Decimal Places / Calculating Rate / Days to keep data / Max change rate若設為0沒辦法正確Save;
>           4. [Fix] Excel 內的 decimalPrecision, dataKeptDays, maxChangeRatePerMin, recRate, calcRate 若設為0，生成Profile沒有正確填0而是填預設值;
>       - [upload / delete dialog multi-lang] - 上傳 / 刪除的dialog多語言
>           - 打開 profile，上傳 alarm code excel 同時 check 語言是否與 tab 相同，上傳成功後刪除 alarm code excel ，並檢查刪除時的語言是否有跟隨 tab，切換至下一個 tab 重複動作
>           - 上傳 alarm code excel，切換至不同語言的 tab 做刪除的動作，check 刪除的語言是否有跟隨 tab
>           - 故意傳不接受的類型或過大的檔案檢查文件上傳錯誤的訊息語言是否有跟隨 tab 更換
>           - 圖片的部分與上述 alarm code excel 的測試手法相同
>           - profileManagement 或 menuManagement 刪除 card -> 跳出 delete dialog -> 取消或確認 -> 切換系統語言反覆測試
>           - 開啟有 parameter 的 profile 點選刪除 parameter -> check 語言跟隨 tab -> 取消或確認 -> 切換 tab 反覆測試
>           - 開啟有 image upload 的 dashboard 或 profile -> 確認上傳語言-> 確認 message 語言 -> 確認刪除語言

> *  **dataworker**
>       - [Connection] 
>           1. [Fix] 当数据的时间戳毫秒部分是 ‘0’ 或 ’00’ 时, DataThread 会陷入死循环导致无法处理数据且占CPU 100%;
>           2. [enhance] 增加探测线程是否被阻塞或当掉, 如果发生, 则记录线程栈状态并重启线程
> *  **Notification**
>       - [Alarm Priority]
>           1. [Fix] 修改 almtrigger 中 Priority 由 int 改为 string 的遗留问题，之前未修改全。

## **0.80.006 (2019-10-12)**
> **[Bug Fix]**
> *  **Portal**
>       - [Object]   
>           1. [Fix] 常数点更新初始值栏位在 profile 里隐藏。Object 模式下，当新建 常数点的时候隐藏。
>           2. [Fix] 修补当页面数据量大切换org 时， 编辑上一个org 的 object 会将 object 存到当前Org 下的bug。解决办法：编辑时不更新orgId，object 加载完毕再结束loading。
>           3. [Fix] 修补当处于object 编辑页面时，token 失效后重新登录，继续编辑后点保存，此时Org id 被重置， 会保存到最新被选中的org 下的问题。解决办法：如果是新增，取用户点新增按钮时候的id,如果是编辑，不会更新orgid;
>           4. [Fix] DataType of Deadband(float), Alarm Delay(positive integer), Alarm Restore Delay(positive integer)
> *  **dataworker**
>       - [Connection] 
>           1. [Fix] Fixed the bug of iSensing and NB-IoT device cannot upload data;
> *  **Alarm Service**
>       - [Message Queue]
>           1. [Fix] 把RabbitMQ Queue的AutoDelete改成false, 避免失去連線後queue被自動刪除
>           2. [Fix] 加上log, 如果某一個message處理太久會寫下log   
> *  **Panel**
>       - [controller-switch]
>           1. [Fix] Cannot setvalue bug @ first button
>           2. [Fix] Cannot change button color properly while set same tag @ both side of button

> **[Add]**
> *  **dataworker**
>       - [DataProcess] 
>           1. [Add] Change tag value时，如果新的value是一个字符串形式的数值, 则自动转成数值, 且isNum设为true。 Amqp consumer 保存为 MainClass 的静态对象, 以测试是否能解决broker重启后无法重新绑定到channel的问题。 timer thread 也保存为 MainClass 的静态对象, 测试是否是非静态对象导致 timer thread 停掉。 logDebugMsg 接口从 TimerThread class 中转移到 _Util class 中。 增加内置数学函数 pow 的支持;

## **0.80.005 (2019-09-27)**
> **[New Features]**
> *  **Portal**
>       - [UI]   
>           1. [Fix] New UI bug fixed;
>           2. [Update] Support object/dev/org/group name auto filter front/end space and  case insensitive;
> *  **dbcreator**
>       - [Role and User] 
>           1. [Fix] Fix the bugs of the user role as space manager;

## **0.80.004 (2019-09-23)**
> **[New Features]**
> *  **Portal**
>       - [UI]   
>           1. [Fix] New UI bug fixed
>           2. [Update] Update SSO and UI css
> *  **dbcreator**
>       - [Resource]   
>           1. [Update] Add new message string and tips

## **0.80.003 (2019-09-20)**
> **[New Features]**
> *  **Portal**
>       - [UI]   
>           1. [Fix] New UI bug fixed
> *  **dbcreator**
>       - [Space manager]   
>           1. [Fix] insert the default, which id=0 account as space manager

## **0.80.002 (2019-09-19)**
> **[New Features]**
> *  **Portal**
>       - [UI]   
>           1. [Fix] New UI bug fixed
> *  **Dataworker**
>       - [Calc Tag]   
>           1. [Fix] by Timer/by Event bug, if Calculation frequency=0 second, will by Event

## **0.80.001 (2019-09-18)**
> **[New Features]**
> *  **Portal**
>       - [Organization]   
>   
>       - [Profile Management]   
>           1. [Update] New UI/UX for Object Profile
>           2. [Update] Change Alarm Code List file from .csv to .xlsx (Excel Format)
>           3. [Add] Search Profile by Category filter
>           4. [Add] Search Profile by Name (fuzzy search)
>           5. [Add] Profile Privacy (Only can see Public Profiles and login user's Private Profile)
>           6. [Add] Calculation Parameter support formula check and auto generate code
>           7. [Add] Profile Preview from Profile Management Page
>       - [Menu Management]   
>           1. [Add] Support Multiple SRP in one organization
>           2. [Update] Select Dashboard Dialog can list all dashboards of this org in WISE-PaaS Dashboard
>           3. [Add] Drag & Drop configuration for menu tree
>       - [Alarm & Notification]
>           1. [Fix][Notification Group] Cannot change Alarm Group / User Group in Edit Mode
>           2. [Fix][Notification Group] Alarm Group / User Group with placeholder and light color
>           3. [Add][Notification Group] Can add Group/Object/Parameter path text in message by "Select Variable Dialog"
>
        
## **0.62.005 Build001 (2019-8-16)**
> **[New Features]**
> *  **Portal**
>     1. Update UI/UX to 0.52 version;
>     2. Support iSensing Device;
>     3. Fixed some bugs;
> * **Portal Service** 
>     1. As portal;
> * **Worker** 
>     1. 增加支持毫秒数不为 3 位数的 timestamp 格式. 完成功能: 自定义函数记录到PostgreSQL中. 取消输出log: Send message to iot-hub, topic=xxx, message=xxx 消息, 以减少log。 增加功能: 如果没有配置 tag.datatype，则自动把数值类型点的 datatype 设为1，非数值的设为3. 支持外挂计算函数每个函数有独立的 serviceurl。
>     2. Fixed some bugs;
> * **Archiver** 
>     1. Change to data access by object
> * **Notification&Alarm** 
>     1. Fixed some bugs;
> * **DBCreator** 
>     1. Change the build package to Gradle Mode

## **0.62.004 Build001 (2019-8-8)**
> **[New Features]**
> *  **Portal**
>     1. Update UI/UX to 0.52 version;
>     2. Support iSensing Device;
>     3. Fixed some bugs;
> * **Portal Service** 
>     1. As portal;
> * **Worker** 
>     1. Support iSensing Device;
>     2. Fixed some bugs;
> * **Archiver** 
>     1. Change to data access by object
> * **Notification&Alarm** 
>     1. Fixed some bugs;
> * **DBCreator** 
>     1. Change the build package to Gradle Mode

## **0.62.003 Build001 (2019-7-23)**
> **[New Features]**
> *  **Portal**
>     1. Update UI/UX to 0.52 version;
>     2. Show Creator of Device in Device List;
>     3. Fixed some bugs;
> * **Portal Service** 
>     1. As portal;
> * **Worker** 
>     1. Seperate database creator to dbcreator;
>     2. Fixed some bugs;
> * **Archiver** 
>     1. No changes
> * **Notification&Alarm** 
>     1. Support Line
> * **DBCreator** 
>     1. Seperated from the worker;
>     2. Will change this APP to cf Task next version;

## **0.62.002 Build001 (2019-7-9)**
> **[New Features]**
> *  **Portal**
>     1. Support online taginfo;
>     2. Menu management support multi-language;
>     3. Fixed some bugs;
> * **Portal Service** 
>     1. As portal;
> * **Worker** 
>     1. Support NB-IoT;
>     2. Fixed some bugs;
> * **Archiver** 
>     1. No changes
> * **Notification&Alarm** 
>     1. No Changes

## **0.61.001 Build001 (2019-6-11)**
> **[New Features]**
> *  **Portal**
>     1. Support calculation tag;
>     2. Support Alarm;
>     3. More dashboard template;
> * **Portal Service** 
>     1. As portal;
> * **Worker** 
>     1. Support new version WebAccess;
>     2. Support MQTT Action=4
>     3. Support calculation tag;
> * **Archiver** 
>     1. No changes
> * **Notification&Alarm** 
>     1. New Apps

## **0.50.004 Build003 (2019-5-5)**
> **[New Features]**
> *  **Portal**
>     1. Add auto refresh device status function;
>     2. Dashboard support multi-language;
>     3. Change [Add Device] dialogue Layout;
>     4. Add SSO Cookie to support Grafana Login;
>     5. Add debug logs on system setting/others;
>     6. Add saveFreq,paramShortName,statetTxt field；   
> * **Portal Service** 
>     1. Machine API add saveFreq, paramShortName, stateTxt(state0-state7) property
>     2. Get Version API

## **0.50.004 Build001 (2019-4-28)**
> **[New Features]**
> 1. First Version Control

> **[Fixes]**
> 1. Support the device status manual refresh

## **0.50.002 Build001 (2019-4-xx)**
> **[Space List]**

> | Server   |org     |   space|    Description |
> |--------  |--------|--------|----------------|
> |HK        |AdvIIoT-EnE |DeviceMPlus |For RD Develop|
> |HK        |AdvIIoT-EnE |EnergyPlus |For Dalian JiuPeng Develop|
> |HK        |AdvIIoT-EnE |SRPDemo |For PM/PSM Demo|
> |HK        |AdvIIoT-EnE |ZhiPin |For Fuzhou ZhiPin test WISE.M+|
> |PeKing    |AdvIIoT-EnE |WISEMPlus |For RD Develop/Test/Demo in ACN|
> |HK    |AdvIIoT-SAE |TrainingMplus |For FAE/AE Demo/Training|
