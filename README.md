# DeviceOn/BI v-1.00.005 (2021-1-8)

[Portal]

Fixed all test bugs;
* [#23549] 畫面出現WISE.M+	
* [#23562] 父層和子層org，在顯示dashboard list有異常	
* [#23563] Dashboard New From Existing沒有顯示dashboard	
* [#23564] 編輯已存在的dashboard後，下次點選new from Existing就會爆掉	
* [#23565] 新增object from device，我選擇scada上傳的所有tag，有501個，但卻只有500個	
* [#23566] 新增object from device，我選擇adam上傳的所有tag，有16個，卻只有看到12個	
* [#23571] 在grafana增加資料夾和dashboard，但從new from existing，沒看到新增的資料夾	
* [#23575] Monitor選擇Analog Input分頁，AI的部分應該置頂	
* [#23576] WISE device有12個tag，但tag list的分頁總數卻只有1	
* [#23577] 新增一個空的org，然後在底下增加一個空的child org，但看到child org的parameter count是8
* [#23618] Adam 6000沒有支援Firmware OTA和Configuration OTA，但卻可以使用	
* [#23619] WISE 4012E內的Configuration設定，可以設定Enable Burnout Fcn和Burnout Scale Mode
* [#23620] My Devices 勾選device數量異常	
* [#23622] 從My Devices，使用copy to my org，但在object內看到Recording Rate是1秒	
* [#23643] 使用copy to my org，在object內看到Recording Rate是1秒，到dashboard查看歷史資料，卻是空的	
* [#23644] 刪除設備的提示訊息內 有錯字	
* [#23646] 刪除設備點參數的提示訊息內，有部分變成簡體	
* [#23671] 上傳UNO，點選monitor，在總覽分頁會一直出現error	
* [#23697] Adam 6060內的Configuration設定，當DO channel設定成不同mode，在切換channel後，會要求設定資料，無法save或dispatch
* [#23732] WISE 4012E內的Configuration設定Analog Input/Common Settings，有二個異常
* [#23733] WISE 4012E內的Configuration設定Analog Input/Common Settings，修改Average Channel Setting設定，卻save fail
* [#23734] WISE 4012E內的Configuration設定Analog Input/Channel Settings，總覽沒有資料
* [#23735] WISE 4012E內的Configuration設定Digital Output，切換channel後，會要求設定Low/High to High Delay Time，導致無法save

[MyDevices]

1. MyDevice relatived micro-service update to version 1.00.005

---

# DeviceOn/BI v-1.00.003 (2020-12-17)

[API-Portal]

Fixed all test bugs;

[Portal]

1. Support 3 scenarios: device management , trail, subscriptionmode;

[MyDevices]

1. MyDevice relatived micro-service update to version 1.00.003

---

# DeviceOn/BI v-1.00.002 (2020-12-07)

#### [Dashboard Plugin]

Fixed:

* [#23026] 使用template建立1.1 Organization Overview Water dashboard，然後觸發alarm，但dashboard卻沒顯示alarm;
* [#23046] 使用template建立dashboard，有使用到Grouped Bar Chart Panel顯示異常
* [#23050] 在3.1 Inflow pumping station，切換object，Water Flow In-Out Panel都顯示N/A
#### [Portal-WISE-MPlus]

Fixed:

* [#23047] 使用profile(AutoTest_Profile)建立object後，object內沒有設定alarm， 但topic(valchg)卻收到資料;

---


# DeviceOn/BI v-1.00.001 (2020-12-07)

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
### 

### DeviceOn/BI v-1.00.00*

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

4. [Change] Org.’s functional items from waterfall to tabs
5. [Add] Inspection
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
6. [Change] Move “Alarm Group” function into “Event” tab
7. [Change] Move “User Group” / “Notification Group” functions into “Notification” tab

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

3. [Add] Support packing MongoDB data into Azure blob
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
4. [Add] Data Packer micro-service
    * trigger “DELETE mongoDB data” message to Data Cleaner
        * With blob address configuration

Rawdata: delete data before 5 days ago

Min data: delete data before 7 days ago

Hour / Day : delete data before 45 days ago

        * Without blob address configuration (standard version)

Use Object setting (days to keep Min / Other data) & parameter setting (days to keep RAW data)

    * Clear Blob by user’s setting
        * Use Object setting (days to keep Min / Other data) & parameter setting (days to keep RAW data)
    * Get Data APIs (internal use)
    * Update data APIs for data resuming (internal use)
5. [Add] Data Cleaner micro-service
    * [Add] Delete RAWData by drop collection
    * [Add] Delete RAWData by parameter
    * [Add] Delete data (deviceInfo / rtdata / rawdata) by Device
    * [Add] Delete data (tagInfo / rtdata / rawdata) by tag
    * [Add] Delete Historical data (min/hour/day/week/month/year) by object
    * [Add] Delete Historical data (min/hour/day/week/month/year) by parameter
6. [Add] MyDevice relatived micro-service
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


