# 实验室两份规格全范围验收索引

当前公开入口0.13.201；以下保留原规格与历史批次证据，早期待办/未发布记录应结合文末后续回执判断。未逐项证明的要求仍待验收。

本索引保留原规格范围。未逐条核对的项目标为“待证明”，不能凭现有绿测标为完成。历史实现证据见 LAB-OPERATIONS-REPORT.md / ROOM-FUNCTIONALIZATION-REPORT.md / ROOM-INCIDENTS-REPORT.md。本轮新增行为见 LAB-DUTY-RELIEF-REPORT.md 与 LAB-RADIO-DUTY-REPORT.md。

2026-10-07新增局部证据：js/lab/trade.js + lab-trade.test.cjs/browser.cjs 已接入通讯订货、次日货箱、仓库单次验收、原商队交易收据与日报、旧档空字段兼容。购买和验收严格分开，不将此标为所有访客或全部100运营/40房间项已完成。当前补丁本地，公开部署尚待执行；具体证据和边界见LAB-OPERATIONS-PROGRESS.md最新记录。

访客医生局部证据：medicine.js consultationDoctor已识别实际放行医生；等待/未放行/隔离/留院/严重病况/死亡/封闭医务室不可提供服务。lab-physician-presence.test.cjs与lab-visiting-doctor-browser.cjs证明原会诊真实消费、只影响在场患者、读档和次日离开禁用。医生不自动入住或排班；并不证明全部访客职业服务完成。此补丁本地未发布。

XLIX/L局部验收新增证据：日报当前/今日/次日仪器预报与准确率显示，六种真实推荐来源与优先级、进入相应房间功能的只读按钮。lab-report-planning专项和Chrome六按钮导航/768/390通过，summary无状态/RNG副作用，隐藏weatherPlan不泄露；旧日报无字段兼容。相关6文件/2920运营日/150天气日通过。完整140项审计仍未完，新增代码本地未发布。

下一版I、LII/LIII新增证据（本地未发布）：当天首次真正进入基地主页自动一页晨报，presented按存档/日期保存，已读旧档不重弹、事件/已有界面优先、次日重显；同页汇总真实五类紧急情况，普通资源/磨损不红框。fire为原事故窗口下真实有燃料严重磨损的动力设备故障，可修理和读档。lab-briefing专项及真实主页按钮流程通过；7相关回归/2920运营日通过。完整报告首次进入、年度跨日和多存档行为继续按原140项范围审计，不仅凭该小链将全目标标为完成。

## LAB OPERATIONS · 100项

### I · DAILY LAB REPORT

验收：待逐条证明。

每天第一次进入实验室主界面时：

生成：

DAILY LAB REPORT

不要弹多个窗口。

只显示一页简洁总览。

例：

DAY 143

POWER:
STABLE

WATER:
LOW

AIR:
GOOD

FOOD:
12 DAYS

GREENHOUSE:
3 plants ready
1 plant stressed

INFIRMARY:
B-07 recovering
Pet #2 stable

VISITORS:
CR-17 expected 19:00–21:00

SECURITY:
Bandit pressure HIGH

WEATHER:
Acid rain after 18:00

NEWS:
Glassfield outbreak continues

MAINTENANCE:
Water filter efficiency 63%

NOTE:
Pet #2 destroyed one planter.

### II · 报告分类

验收：本地已证明12分类均存在。operationsUI.report逐项生成BASE/RESOURCES/GREENHOUSE/INFIRMARY/SECURITY/VISITORS/NEWS/WEATHER/MAINTENANCE/B07/PETS/TASKS；lab-briefing-browser实际页面显示12个data-ops-section；此证据只覆盖分类存在，不替代每分类全部深层内容验收。

DAILY REPORT至少包含：

BASE

RESOURCES

GREENHOUSE

INFIRMARY

SECURITY

VISITORS

NEWS

WEATHER

MAINTENANCE

B07

PETS

TASKS

### III · MORNING REPORT

验收：待逐条证明。

每日早晨：

MORNING REPORT

重点：

今天需要注意什么。

例如：

- 今日官方商队
- 天气
- 疫情
- 温室成熟
- 医务室患者
- 资源短缺
- 维修问题
- 土匪风险

### IV · EVENING REPORT

验收：待逐条证明。

晚上：

EVENING REPORT

记录：

- 今天来了谁
- 交易
- 谁受伤
- 谁生病
- 植物成熟
- 维修
- 资源变化
- 新闻变化
- NPC死亡 / 事件

### V · 报告不是强制阅读

验收：待逐条证明。

玩家可以：

READ

SKIP

ARCHIVE

重要警报仍然单独显示。

普通内容不要打断玩家。

### VI · LAB STATUS

验收：待逐条证明。

实验室增加整体状态：

POWER

WATER

AIR QUALITY

TEMPERATURE

STRUCTURAL CONDITION

CLEANLINESS

CONTAMINATION

SECURITY

COMFORT

### VII · POWER

验收：待逐条证明。

电力来源：

GRID REMNANT

GENERATOR

BATTERY

SOLAR

ANOMALOUS SOURCE

影响：

灯

温室

医务室

电脑

安全门

冷藏

### VIII · POWER STABILITY

验收：待逐条证明。

状态：

STABLE

UNSTABLE

LOW

CRITICAL

BLACKOUT

### IX · WATER

验收：待逐条证明。

水系统影响：

饮水

医务室

清洁

温室

厨房

### X · AIR QUALITY

验收：待逐条证明。

空气受：

灰尘

黑霉

污染

孢子

过滤器

影响。

### XI · CLEANLINESS

验收：待逐条证明。

加入轻量：

CLEANLINESS

但不要让玩家每天扫地。

只有长期忽略时才产生后果。

### XII · 清洁度后果

验收：待逐条证明。

低清洁度：

害虫增加

感染风险上升

宠物问题增加

食物污染风险上升

### XIII · 自动清洁

验收：待逐条证明。

升级：

AUTO CLEANING

NPC

宠物行为

可降低维护频率。

### XIV · DUTY ROSTER

验收：待逐条证明。

新增：

DUTY ROSTER

玩家可以安排：

GREENHOUSE DUTY

INFIRMARY DUTY

SECURITY DUTY

MAINTENANCE DUTY

KITCHEN DUTY

CLEANING DUTY

RADIO DUTY

### XV · 谁能值班

验收：待逐条证明。

可能参与：

Jack

B-07

NPC

部分宠物

机器人

### XVI · Jack值班

验收：待逐条证明。

Jack强项：

MAINTENANCE

SECURITY

VEHICLE

弱项：

COOKING

MEDICAL

BOTANY

除非升级技能。

### XVII · B-07值班

验收：待逐条证明。

根据成长阶段和性格：

可帮助：

温室

宠物

门岗观察

简单整理

医疗陪伴

### XVIII · B-07不能当万能助手

验收：待逐条证明。

B-07可能：

忘记

偷懒

做错

拒绝

自己改规则

### XIX · 宠物值班

验收：待逐条证明。

宠物可：

PEST CONTROL

SECURITY ALERT

POLLINATION

COMPANIONSHIP

但不能复杂操作设备。

### XX · 值班疲劳

验收：待逐条证明。

重复让同一角色长期值班：

FATIGUE

STRESS

可能上升。

### XXI · ROUTINE SYSTEM

验收：待逐条证明。

角色会形成长期习惯。

记录：

routineId

subject

action

timePreference

location

frequency

strength

### XXII · Jack习惯

验收：待逐条证明。

例如：

晨间先看新闻

暴雪前检查发电机

睡前锁工具柜

晚上修设备

### XXIII · B-07习惯

验收：待逐条证明。

例如：

晚上去温室

商队来时去门边看

下雨时看玻璃

压力高时睡门边

每天看第一株植物

### XXIV · 宠物习惯

验收：待逐条证明。

例如：

睡医务室门口

偷温室水果

跟着Jack维修

固定睡某个角落

### XXV · ROUTINE MEMORY

验收：待逐条证明。

如果一个行为重复很多次：

形成：

ESTABLISHED ROUTINE

以后角色可能自动执行。

### XXVI · 习惯被打断

验收：待逐条证明。

如果：

停电

生病

NPC死亡

Grey Tide

来访

会打断习惯。

角色可能产生反应。

### XXVII · MAINTENANCE SYSTEM

验收：待逐条证明。

加入基地维护。

设施拥有：

condition

wear

lastMaintenanceDay

priority

### XXVIII · 可维护设备

验收：待逐条证明。

包括：

GENERATOR

WATER FILTER

PUMP

HEATER

COOLING

AIR FILTER

GREENHOUSE LIGHT

HYDROPONICS

INFIRMARY SCANNER

SECURITY CAMERA

DOOR LOCK

RADIO

SERVER

### XXIX · 状态

验收：待逐条证明。

GOOD

WORN

POOR

FAILING

BROKEN

### XXX · 不要每件每天坏

验收：待逐条证明。

故障必须：

慢

有预兆

可预测

### XXXI · 故障预兆

验收：待逐条证明。

例如：

灯闪

水压低

泵变吵

过滤器效率下降

电脑报错

### XXXII · FAILURE CHAINS

验收：待逐条证明。

重要：

故障可以形成连锁。

例如：

水管漏水

↓

墙体潮湿

↓

BLACK MOLD

↓

AIR QUALITY下降

↓

呼吸疾病风险增加

↓

医务室压力上升

↓

Clean Moss需求增加

### XXXIII · 电力连锁

验收：待逐条证明。

发电机效率下降

↓

温室灯不稳定

↓

植物成长慢

↓

食物产量下降

↓

价格 / 库存压力上升

### XXXIV · 门锁故障

验收：0.13.153行为、长期病程及公开三尺寸通过；证据见文末回执。

门锁损坏：

SECURITY下降

但对B-07可能：

Door Anxiety下降或上升

取决于个体。

### XXXV · 维修优先级

验收：待逐条证明。

玩家可设置：

LOW

NORMAL

HIGH

CRITICAL

### XXXVI · 自动维修

验收：待逐条证明。

高级设施：

AUTO MAINTENANCE

只处理：

小问题

严重故障仍需要：

Jack

NPC

零件

### XXXVII · MAINTENANCE MATERIALS

验收：待逐条证明。

需要：

Scrap

Wire

Filter

Seal

Battery

Pipe

Tool Parts

### XXXVIII · RESOURCE FORECAST

验收：待逐条证明。

Daily Report显示：

FOOD:
12 days estimated

WATER:
7 days

FUEL:
4 days

MEDICINE:
LOW

不要只显示绝对数字。

### XXXIX · RESOURCE BURN RATE

验收：待逐条证明。

根据：

人口

宠物

患者

天气

温室

车辆

变化。

### XL · STORAGE

验收：待逐条证明。

基地仓库分：

GENERAL

FOOD

MEDICAL

GREENHOUSE

WEAPONS

VEHICLE PARTS

ANOMALOUS

### XLI · 医疗库存

验收：待逐条证明。

Daily Report显示：

bandage

basic meds

herbal support

quarantine supplies

### XLII · 温室摘要

验收：待逐条证明。

报告：

READY TO HARVEST

DISEASED

LOW WATER

MUTATING

FIRST FRUIT

### XLIII · 医务室摘要

验收：待逐条证明。

显示：

patients

severity

recovery

quarantine

### XLIV · B-07 DAILY STATUS

验收：待逐条证明。

不要直接显示所有隐藏值。

报告只可显示：

OBSERVED:

- ate normally
- slept poorly
- avoided door
- spent time in greenhouse

### XLV · PET DAILY STATUS

验收：待逐条证明。

例如：

Pet #1:
healthy

Pet #2:
stole fruit

Pet #3:
minor injury

### XLVI · SECURITY

验收：待逐条证明。

报告：

visitorRisk

banditPressure

doorStatus

cameraStatus

### XLVII · VISITOR LOG

验收：待逐条证明。

日报整合：

Today:

19:10
CR-17 Official Caravan
TRADED

22:34
Unknown Visitor
DOOR NOT OPENED

### XLVIII · NEWS SUMMARY

验收：待逐条证明。

不要在Daily Report复制整篇新闻。

只显示：

TOP 3 IMPORTANT

点击进入完整NEWS。

### XLIX · WEATHER SUMMARY

验收：待逐条证明。

显示：

CURRENT

TODAY

NEXT 24H

### L · TASK PRIORITY

验收：待逐条证明。

自动生成：

RECOMMENDED TASKS

例如：

1.
Replace water filter

2.
Check B-07 fever

3.
Harvest potatoes

4.
CR-17 arrives tonight

### LI · 只是推荐，不强迫

验收：待逐条证明。

玩家可以完全无视。

### LII · LAB ALERTS

验收：待逐条证明。

紧急事件：

POWER FAILURE

PATIENT CRITICAL

INTRUDER

FIRE

CONTAMINATION LEAK

使用：

CRITICAL ALERT

### LIII · 非紧急别弹红框

验收：待逐条证明。

普通：

成熟植物

商队

低库存

只用小提示。

### LIV · 实验室一天

验收：待逐条证明。

世界时间推进时：

晨报

↓

玩家自由活动

↓

来访

↓

维护

↓

治疗

↓

探索

↓

晚报

### LV · 夜间自动事件

验收：待逐条证明。

睡觉后：

模拟：

植物

患者

维修

宠物

NPC

天气

### LVI · 夜间事件例

验收：待逐条证明。

Pet #2 slept in greenhouse.

B-07 woke at 03:12.

Water pressure dropped.

Official caravan passed.

### LVII · 玩家不在基地

验收：待逐条证明。

实验室仍然运行。

### LVIII · AWAY SIMULATION

验收：待逐条证明。

如果玩家远行：

simulate:

resources

plants

medical

maintenance

visitors

### LIX · 回家报告

验收：待逐条证明。

离开多日：

RETURN REPORT

例如：

AWAY:
6 DAYS

Visitors:
4

Plant harvests:
7

Failures:
1

Patients:
B-07 recovered

### LX · NPC AUTONOMY

验收：待逐条证明。

如果NPC住在实验室：

他们会：

工作

休息

生病

吵架

帮忙

### LXI · SHIFT CONFLICT

验收：待逐条证明。

NPC可能：

不想值夜班

换班

迟到

生病

### LXII · PERSONNEL RELIABILITY

验收：待逐条证明。

NPC拥有：

reliability

skill

fatigue

morale

### LXIII · 不要做HR模拟器

验收：待逐条证明。

只用于事件和效率。

### LXIV · KITCHEN

验收：待逐条证明。

加入厨房摘要：

MEALS AVAILABLE

FRESH FOOD

SPOILAGE RISK

### LXV · 自动饮食

验收：待逐条证明。

居民会吃库存。

偏好影响：

选择

心情

### LXVI · 特殊餐

验收：待逐条证明。

病人：

RECOVERY MEAL

B-07：

favorite food

### LXVII · BASE COMFORT

验收：待逐条证明。

基地：

COMFORT

来源：

heat

furniture

plants

cleanliness

lighting

music

### LXVIII · COMFORT影响

验收：待逐条证明。

影响：

stress recovery

sleep

morale

### LXIX · HOME FEEL

验收：待逐条证明。

隐藏指标：

HOME_STATE

不是数字展示。

阶段：

FACILITY

SHELTER

LIVED-IN

HOME

### LXX · HOME变化

验收：待逐条证明。

通过：

家具

植物

照片

习惯

宠物

NPC

改变。

### LXXI · 实验室事故

验收：100个独立可处理运营事件已本地证明（2026-10-07），200处理分支、100逾期路径、保存/复查/结案及实际Chrome100事件/27房间通过。证据见LAB-100-INCIDENTS-REPORT.md；尚未公开发布，不外推其他条款。

至少加入：

100个Lab Operations事件。

### LXXII · 小故障

验收：待逐条证明。

例：

灯泡坏

水管滴水

门卡

收音机杂音

冰箱故障

### LXXIII · 中故障

验收：待逐条证明。

泵坏

暖气坏

过滤器堵

温室漏水

### LXXIV · 大故障

验收：待逐条证明。

发电机停机

污染泄漏

医疗系统故障

门锁失效

### LXXV · 多阶段事故

验收：待逐条证明。

例如：

FILTER FAILURE

Day 1:
air quality下降

Day 3:
mold

Day 6:
respiratory illness

### LXXVI · 玩家提前维修

验收：待逐条证明。

可避免后果。

### LXXVII · Jack SKILL

验收：待逐条证明。

Jack维修成功：

提升：

MAINTENANCE EXPERIENCE

### LXXVIII · 技能等级

验收：待逐条证明。

MAINTENANCE LEVEL 1–20

影响：

维修时间

材料

故障预测

### LXXIX · B-07学维修

验收：待逐条证明。

高关系 / 高好奇：

B-07可：

递工具

记工具位置

指出声音异常

### LXXX · B-07可能学错

验收：待逐条证明。

比如：

把胶带当万能维修。

### LXXXI · Tool Memory

验收：待逐条证明。

B-07可能记住：

Jack总把10mm扳手放哪。

### LXXXII · 随机生活事件

验收：待逐条证明。

至少100个。

例如：

B-07占Jack椅子

宠物偷工具

NPC偷吃

水杯打翻

### LXXXIII · 非系统性剧情

验收：待逐条证明。

至少30%运营事件：

没有奖励。

只是生活。

### LXXXIV · Maintenance Notes

验收：本地已接入手写维护日志及真实故障回看，专项单元/实际Engine与浏览器/迁移/满容量保存通过，详见LAB-MAINTENANCE-LOG-REPORT.md；本批未发布。

Jack可以写：

MAINTENANCE LOG

例如：

“Pump 3 still sounds wrong.”

### LXXXV · 日志长期回收

验收：本地已接入手写维护日志及真实故障回看，专项单元/实际Engine与浏览器/迁移/满容量保存通过，详见LAB-MAINTENANCE-LOG-REPORT.md；本批未发布。

后来真正坏时：

玩家会发现以前就有预兆。

### LXXXVI · Radio Duty

验收：待逐条证明。

如果有人值：

RADIO DUTY

提高：

news update

visitor warning

### LXXXVII · Security Duty

验收：待逐条证明。

提高：

fake caravan detection

bandit warning

### LXXXVIII · Medical Duty

验收：本地成功值班早期症状观察、90病421宿主组合及真实Engine/browser/存读验证通过，见LAB-DUTY-OBSERVATIONS-REPORT.md；本批未发布。

提高：

early symptom detection

### LXXXIX · Greenhouse Duty

验收：本地实现并专项验证。保留原成功值班健康收益，三类独立病害已接原逐日生态、生长循环；真实成功值班早于普通可见症状，潜伏首日不透露、记录去重、护理逐日恢复、实际按钮/旧档/中英/手机通过。80病例及240活动问题、全157人物/90新闻的五成熟档保存通过。18种植照护链和8全年运营相关回归通过；新增后的完整113命令与公开部署尚待取得，不将此条当整体140项完成。见PLANT-HEALTH-INTEGRATION-PROGRESS.md。

提高：

plant health

early disease detection

### XC · Maintenance Duty

验收：待逐条证明。

降低：

failure risk

### XCI · 值班自动分配

验收：待逐条证明。

玩家可选择：

MANUAL

AUTO

AUTO根据技能安排。

### XCII · AUTO不是完美

验收：待逐条证明。

AI排班可能：

效率高

但不考虑角色偏好。

### XCIII · Role Preference

验收：待逐条证明。

角色可能：

喜欢温室

讨厌夜班

怕医务室

喜欢门岗

### XCIV · 角色冲突

验收：待逐条证明。

排班不合适：

stress

complaints

事件

### XCV · 临时替班

验收：待逐条证明。

生病时：

别人代班。

### XCVI · IMPORTANT MEMORY EVENTS

验收：本地六类真实首次事件、旧标记兼容、长期房间留存与后续回看、亲历知识隔离已有单元及实际浏览器证据，见LAB-OPERATIONAL-MEMORIES-REPORT.md。本次110文件完整回归仍运行，尚未重新发布。

运营系统也能产生记忆：

FIRST BLACKOUT

FIRST MAJOR REPAIR

FIRST PATIENT

FIRST HARVEST

FIRST VISITOR

FIRST WINTER

### XCVII · DAILY REPORT历史

验收：待逐条证明。

保存最近：

30–100天。

### XCVIII · 报告搜索

验收：待逐条证明。

可以按：

visitor

disease

failure

plant

搜索。

### XCIX · WORLD IMPACT

验收：待逐条证明。

基地运营结果影响外界：

医疗援助

粮食

商队

NPC

### C · FINAL PRINCIPLE

验收：待逐条证明。

LAB OPERATIONS不是：

“更多数字。”

它的目标是：

让玩家感觉：

这个地方每天都有人吃饭。

有人生病。

有人浇水。

有人修电。

有人敲门。

有东西会坏。

有植物会长。

宠物会闯祸。

B-07会形成习惯。

Jack会忘记休息。

玩家离开以后：

世界不会停。

玩家回来时：

实验室已经度过了几天自己的生活。

## THE LAB IS A PLACE · 40项

### I · ROOM ACTION BAR

验收：待逐条证明。

每个房间进入后增加：

ROOM ACTION BAR

位置：

房间页面底部或侧栏。

包含：

PRIMARY ACTION
该房间最核心功能

SECONDARY ACTIONS
2–6个辅助功能

ROOM STATUS
房间状态

ROOM MEMORY
房间记忆/事件

DECORATE
装饰

LEAVE
离开

不要让每个房间都出现几十个按钮。

### II · 系统入口原则

验收：待逐条证明。

原本主菜单系统入口：

暂时保留作为快捷入口。

但点击后：

应导航到对应房间，
再打开房间内部系统。

例如：

Main Menu
→ Greenhouse

实际上：

goToRoom("greenhouse")
→ openRoomSystem("plants")

而不是直接打开独立Greenhouse页面。

### III · 旧升级数据不要硬合并

验收：待逐条证明。

目前存在：

home.greenhouse
vs
greenhouse system upgrade

home.medical
vs
infirmary level

不要直接覆盖旧值。

建立：

ROOM SYSTEM ADAPTER

例如：

room.greenhouse.level
显示房间物理状态

greenhouseSystem.level
显示专属系统能力

UI可以组合显示：

ROOM LEVEL 3
BOTANY FACILITY LEVEL 5

后续再设计统一迁移。

本轮优先：
安全兼容旧档。


01 — 培养舱
ID: containment

定位：

B-07最早的空间。

核心功能：

OBSERVE B-07
观察

CHECK LIFE SUPPORT
检查生命维持

FEEDING HATCH
喂食口

GLASS / DOOR CONTROL
玻璃与门

ENVIRONMENT CONTROL
环境调节

MEMORY
查看这里发生过的重要记忆

后期：

培养舱应该逐渐失去“牢房”功能，
转化成：

旧房间
纪念空间
医疗观察间
或者B-07自己选择使用的私人角落。

独特交互：

摸玻璃

检查旧铭牌

看空碟

看旧温度记录

查看指印胶带

开/关内侧释放装置

不得让培养舱后期永远停留在“囚禁界面”。

视觉：

大型玻璃舱
管道
生命维持设备
旧B-07铭牌
冷凝水
早期CG相关物件


02 — Jack 的房间
ID: quarters

定位：

Jack私人空间。

核心功能：

SLEEP

CHANGE CLOTHES

PERSONAL STORAGE

JOURNAL

JASMINE MEMORY BOX

PHOTO ALBUM

PRIVATE OBJECTS

重要：

这是最适合做人设细节的房间。

可出现：

红线

照片

旧工具

衣服

床边药

烟灰缸（若世界设定允许）

扑克牌

旧音乐播放器

专属事件：

Jack失眠

B-07敲门

宠物占床

生病休息

Jasmine回忆

视觉必须与普通living room完全不同。


03 — 它自己的空间
ID: living

定位：

B-07真正私人空间。

核心原则：

这是B-07的房间。

Jack不是默认拥有全部控制权。

功能：

B07 DECORATION

B07 PRIVATE COLLECTION

COMFORT OBJECTS

FAVORITE ITEMS

CLOTHING / ACCESSORIES

OBSERVED HABITS

PRIVACY

SLEEP SPACE

允许B-07自己改变摆放。

高Autonomy时：

某些物品位置由B-07决定。

Jack可能发现：

藏起来的水果

卡牌

石头

NPC礼物

异常小物

植物

这是“Facility → Home”转化的核心房间之一。


04 — 医疗室
ID: medical

直接接入：

INFIRMARY

房内核心入口：

PATIENTS

DIAGNOSIS

TREATMENT

MENTAL STATE

HERBAL LAB

RECOVERY

MEDICAL STORAGE

QUARANTINE

患者真实出现在房间：

Jack

B-07

Pets

NPC

视觉：

病床
扫描设备
医疗柜
植物治疗角
毛毯
监视器

随着等级变化明显升级。

不要再使用桌柜模板。


05 — 遗传实验室
ID: genetics

功能：

MUTATION ANALYSIS

GENOME ARCHIVE

SERUM RESEARCH

PLANT MUTATION

CREATURE TRAITS

B-SERIES SAMPLE ANALYSIS

高级：

Zero sample
Grey Tide biology
Host相关隐藏内容

风险：

实验事故
污染
样本错误
突变

视觉：

样本柜
冷藏设备
显微设备
生物扫描
培养皿


06 — 工程室
ID: engineering

Jack主场。

功能：

BASE MAINTENANCE

POWER ROUTING

WATER SYSTEM

DOOR SYSTEM

VEHICLE MODULE DESIGN

AUTOMATION

CAMERA SYSTEM

LAB OPERATIONS

显示：

当前基地故障地图。

这里可以成为：

Jack Maintenance Skill
核心升级房间。

视觉：

大型工具墙
电线
蓝图
电箱
拆开的设备


07 — 厨房
ID: kitchen

功能：

COOK

PRESERVE FOOD

MAKE RECOVERY MEAL

B07 FAVORITE FOOD

PET FOOD

FOOD STORAGE

TEA / HERBAL DRINK

事件：

做饭失败

B-07偷吃

宠物翻垃圾

NPC一起吃饭

Jasmine记忆

厨房必须成为重要生活场景来源。


08 — 仓库
ID: storage

功能：

GENERAL STORAGE

SORT

VALUABLE STORAGE

TRADE PREP

CONTRABAND

LARGE ITEM STORAGE

INVENTORY MANAGEMENT

展示：

箱子
大型变卖物
家具
旅行装备

特殊：

东西太多后真的视觉变拥挤。

升级：

货架
分类
防盗
环境控制


09 — 温室
ID: greenhouse

直接接入全部：

GREENHOUSE 3.0

PLANTS
SEEDS
ECOLOGY
HYDROPONICS
TREES
HERBS
BREEDING
PROCESSING
AUTOMATION
ARCHIVE

玩家必须能在房间里看到：

实际种植槽
树
植物
水培架
异常隔离箱

视觉根据实际种植内容改变。

温室不再是静态背景。


10 — 工坊
ID: workshop

功能：

WEAPON CRAFTING

WEAPON REPAIR

DISMANTLE

RESONANCE

ARMOR / GEAR

FURNITURE REPAIR

VEHICLE PARTS

CRAFTING

武器实体展示。

工作台上出现：

当前正在升级的武器。

专属：

100武器仓库管理快捷入口。


11 — 观察室
ID: observation

不只是“看培养舱”。

功能：

CAMERAS

B07 BEHAVIOR LOG

PET BEHAVIOR

VISITOR CAMERA

ANOMALY OBSERVATION

WORLD SENSOR

可以切换：

实验室各摄像头

门外

温室

医疗室

禁止变成偷窥B-07的万能监控。

高Autonomy后：

B-07私人空间摄像头可能被关闭。


12 — 档案室
ID: archive

功能：

LORE

PROJECT ABYSS

B-SERIES

ZERO

BLACK CLEARANCE

JASMINE FILE

WORLD HISTORY

NPC RECORDS

MEDICAL ARCHIVE LINK

NEWS ARCHIVE LINK

这里也是故事模式的重要叙事空间。

玩家读/不读资料继续生成flags。


13 — 供电室
ID: power

功能：

POWER NETWORK

GENERATOR

BATTERY

SOLAR

POWER PRIORITY

EMERGENCY POWER

ANOMALOUS POWER

停电时必须真的来这里。

玩家可以决定：

医疗室优先
温室优先
防御优先
生活区优先

资源不足时产生真正选择。

视觉：

大发电机
电池架
断路器
电缆


14 — 净水室
ID: water

功能：

WATER STORAGE

FILTRATION

PUMP

GREENHOUSE SUPPLY

MEDICAL WATER

RAIN COLLECTION

CONTAMINATION TEST

水污染事件从这里处理。

视觉：

储水罐
过滤器
泵
管道
漏水痕迹


15 — 通讯室
ID: radio

直接接入：

WASTELAND NEWS NETWORK

功能：

NEWS

RADIO

CARAVAN TRACKING

WEATHER

DISTRESS SIGNALS

GOVERNMENT CHANNEL

BLACK MARKET FREQUENCY

HAUNTED RADIO

玩家每天听晨报/晚报就在这里。

视觉：

大量旧无线电
墙面地图
信号灯
天线控制
纸条


16 — 研究大厅
ID: hall

定位：

所有研究体系的中央Hub。

功能：

TECH TREE

BOTANY RESEARCH

MEDICAL RESEARCH

ECOLOGY RESEARCH

GENETICS RESEARCH

ENGINEERING RESEARCH

ANOMALY RESEARCH

不要让具体实验在这里完成。

它负责：

规划
分配研究点
查看项目

视觉：

巨大旧研究大厅
中央白板/终端
多部门工作站


17 — 封锁下层
ID: lower

定位：

高风险探索/故事区域。

功能：

EXPLORE LOWER LEVEL

RESTORE POWER

OPEN SEALED ROOMS

RECOVER MATERIAL

ANOMALY CHECK

动态：

逐步解锁实际小区域。

不能只是一个“点击探索”。


18 — 零号通道
ID: zero

功能：

ZERO ARCHIVE

ZERO ACCESS

CONTINUITY SIGNALS

SCAN ANOMALY

LOCKED DOORS

故事后期关键区域。

每次进入可能有：

细微环境变化。

禁止大量重复刷资源。

视觉必须极其独特。


19 — 黑级研究翼
ID: black

功能：

BLACK CLEARANCE ORDERS

GOVERNMENT FILES

RESTRICTED RESEARCH

HIGH-TIER EQUIPMENT

E3 / government-related content

玩家在这里真正看到：

旧权力结构。

可接：

官方终端
过期权限
黑级扫描


20 — 维修夹层
ID: crawl

这间特别适合Jack。

功能：

CRAWLSPACE REPAIR

HIDDEN WIRING

PIPE BYPASS

SECRET ROUTE

SMALL CACHE

ANOMALY ACCESS

这里是：

Jack专属捷径网络。

升级后：

允许更快修不同房间。

也能发现：

墙后空间
旧纸条
藏东西的地方


21 — 旧育成室
ID: nursery

不要和Greenhouse混淆。

这是：

旧实验生命育成室。

功能：

OLD CREATURE RECORDS

PET INCUBATION

EGG / COCOON CARE

RESCUED CREATURE CARE

B-SERIES CHILDHOOD CLUES

可以改造成：

宠物育成区

或者保留部分旧设备。

情绪上应该有：

空床
旧玩具
编号


22 — B 系列库房
ID: series

功能：

B-SERIES RELICS

OLD EQUIPMENT

SPECIMEN OBJECTS

PERSONAL TRACES

RECOVERED ITEMS

例如：

杯子涂鸦
旧食盆
编号牌
排班表

不是普通仓库。

这是B-Series的“遗物室”。


23 — 停用手术室
ID: surgery

功能：

ADVANCED MEDICAL

OLD SURGICAL ARCHIVE

BIOLOGICAL SCAN

SEVERE INJURY TREATMENT

RESTRICTED PROCEDURE RECORDS

重要：

治疗玩法保持抽象。

不加入现实手术细节。

高Medical Level才重新启用。

视觉：

停用灯
老旧手术台
封存设备
灰尘


24 — 地下三层
ID: sublevel

定位：

深层设施探索。

功能：

SUBLEVEL EXPEDITION

RESOURCE RECOVERY

OLD INFRASTRUCTURE

SECRET ROOMS

POWER RESTORATION

这里可以逐步扩大成：

内部2D探索区域。

危险度较高。


25 — 未登记楼梯
ID: stairs

这个房间必须做得怪。

功能：

DESCEND

ASCEND

LISTEN

MARK FLOOR

LEAVE OBJECT

CHECK STEP COUNT

楼层可能：

偶尔和地图不一致。

Continuity seed。

例如：

今天：

34级台阶

之后：

35

不要弹：

ANOMALY!

让玩家自己发现。


26 — 黑级动力核
ID: core

功能：

CORE POWER

BLACK SYSTEMS

EMERGENCY OVERRIDE

HIGH-TIER ENERGY

CONTINUITY INFRASTRUCTURE

风险：

巨大能源
故障
污染

可以为：

Black Clearance设备
高级实验
提供电力。

但使用可能增加：

风险/世界状态变化。

视觉：

与普通Power Room完全不同。

大型核心设施。


27 — 无编号房间
ID: unnumbered

这是最终最自由的一间。

不要一开始告诉玩家用途。

功能根据玩家发现逐渐出现：

OBJECT PLACEMENT

ANOMALOUS STORAGE

UNKNOWN TERMINAL

DREAM EVENT

CONTINUITY EVENT

HOST EVENT

MEMORY ROOM

房间布局可能：

细微变化。

物品可能：

位置错误。

某些存档里功能不同。

必须是：

游戏里最神秘的房间之一。

### IV · 27间房全部增加唯一视觉主题

验收：待逐条证明。

禁止继续：

14间桌柜复制。

每间至少有：

1个大型视觉主体

2–5个独特props

1套主要光线

1个环境声音


例如：

medical:
病床 + 医疗监视器

engineering:
工具墙 + 大电箱

kitchen:
灶台 + 食物架

storage:
高货架 + 箱子

workshop:
武器工作台

archive:
档案架 + 终端

power:
发电机

water:
巨大水罐

radio:
无线电墙

nursery:
旧育成舱

surgery:
手术台

core:
动力核心

stairs:
楼梯本身

### V · 房间状态必须视觉化

验收：待逐条证明。

例如：

DAMAGED：

漏水
火花
破灯

DIRTY：

灰尘
杂物

UPGRADED：

新设备
新家具
灯光变化

ABANDONED：

蜘蛛网
关闭设备

不要只改数字。

### VI · 房间功能快捷键

验收：待逐条证明。

进入房间后：

显示最重要的1–3项。

例如温室：

[PLANTS]
[ECOLOGY]
[HARVEST]

医疗：

[PATIENTS]
[TREAT]
[RECOVERY]

工坊：

[CRAFT]
[WEAPONS]
[DISMANTLE]

然后：

MORE

打开完整子系统。

### VII · 实际房间位置关系

验收：待逐条证明。

建立：

LAB FLOOR MAP

至少按层划分。

例如：

LEVEL 0:
Containment
Quarters
Living
Kitchen
Storage
Medical

LEVEL -1:
Greenhouse
Workshop
Engineering
Power
Water
Radio

LEVEL -2:
Genetics
Observation
Archive
Hall
Crawl
Nursery
Series
Surgery

LEVEL -3:
Lower
Sublevel
Stairs

RESTRICTED:
Zero
Black
Core
Unnumbered

布局可根据当前代码调整，
但必须稳定。

### VIII · 房间之间有移动时间

验收：待逐条证明。

不需要复杂走路模拟。

但房间切换可：

轻微时间推进
过渡
脚步音

不能感觉像27个浏览器Tab。

### IX · 房间角色位置

验收：待逐条证明。

Jack
B-07
pets
NPCs

应存在：

currentRoom

他们真的在某个房间。

### X · FIND CHARACTER

验收：待逐条证明。

玩家可以：

找B-07

系统可能说：

“Greenhouse.”

然后进入温室。

不要瞬移NPC到玩家面前。

### XI · ROOM SCHEDULE

验收：待逐条证明。

习惯系统直接绑定房间。

例如：

08:00
Jack → kitchen

09:00
B-07 → greenhouse

14:00
Jack → engineering

22:00
B-07 → living

### XII · 门口事件

验收：待逐条证明。

Visitor Bay最好挂在：

主入口 / observation / radio

玩家可以：

从Observation看

从Radio对讲

去Visitor Bay开门

### XIII · ROOM MEMORY

验收：待逐条证明。

每个房间记录：

重要事件。

例如：

Medical:
B-07 first illness

Greenhouse:
B-07 first plant

Kitchen:
first failed meal

Containment:
first sight

Room Memory页面可查看。

### XIV · PERSONAL ROOM MEMORY

验收：待逐条证明。

不是任务日志。

只是：

“This happened here.”

### XV · 房间死亡痕迹

验收：待逐条证明。

NPC死亡后：

其常用房间可能留下：

空椅子
工具
杯子
照片

### XVI · 房间损坏

验收：待逐条证明。

基地遭袭：

不是抽象：

HOME DAMAGE -10

而是具体：

Greenhouse glass damaged

Water room pump broken

Kitchen window cracked

### XVII · Repair从房间内完成

验收：待逐条证明。

玩家进入受损房间：

REPAIR

显示：

问题

材料

预计时间

### XVIII · Jack维修动画/表现

验收：待逐条证明。

不需要复杂3D动画。

可以：

角色立绘

小CG

工具声音

进度

### XIX · 房间专属事件池

验收：待逐条证明。

每房至少：

10个轻事件

3个较大事件

27房最低：

270+轻事件

81+大事件潜力

不要求一次全部完成，
但架构必须支持。

### XX · ROOM SPECIALIZATION

验收：待逐条证明。

部分房间升级后允许二选一专精。

例如：

Greenhouse：

FOOD PRODUCTION
或
MEDICAL BOTANY

Medical：

EMERGENCY CARE
或
LONG-TERM RECOVERY

Workshop：

WEAPON
或
GENERAL FABRICATION

### XXI · 不锁死内容

验收：待逐条证明。

专精：

增强某方向

不是永久封死另一方向。

### XXII · 房间氛围声音

验收：待逐条证明。

每房有：

ambientSoundId

例如：

power:
generator hum

water:
pump + dripping

greenhouse:
fans + water

radio:
static

archive:
paper + distant fan

### XXIII · 光照差异

验收：待逐条证明。

containment:
cold cyan

quarters:
warm dim

medical:
cold white

greenhouse:
grow light

engineering:
orange work light

radio:
screen glow

zero:
almost colorless

black:
deep neutral / red status lights

### XXIV · 房间升级必须改变画面

验收：待逐条证明。

Level 1和Level 5：

不能看起来完全相同。

升级可加入：

equipment
lighting
storage
cleanliness
automation

### XXV · 房间装饰限制

验收：待逐条证明。

不同房间允许不同家具。

例如：

Medical：
不能在手术台上放沙发。

Greenhouse：
植物家具优先。

Quarters：
自由度最高。

### XXVI · B-07房间自主装饰

验收：待逐条证明。

Living Room：

部分格子为：

B07_CONTROLLED

玩家不能直接移动，
除非B-07允许。

### XXVII · 房间状态摘要

验收：待逐条证明。

Lab map显示：

medical
PATIENT: 1

greenhouse
HARVEST: 4

power
WARNING

radio
NEW SIGNAL

不要展开完整系统。

### XXVIII · 主菜单瘦身

验收：待逐条证明。

将重复一级入口逐渐缩减。

HOME保留：

紧急提示
快捷方式

但具体功能属于房间。

### XXIX · Quick Access

验收：待逐条证明。

不想每次走房间的玩家：

可使用：

QUICK ACCESS

但UI显示：

GO TO GREENHOUSE

而不是抽象弹菜单。

### XXX · 旧研究翼6房

验收：待逐条证明。

保持：

探索地点。

不要错误加入主实验室27间。

但可以从：

OLD WING MAP

进入。

### XXXI · 旧翼和主实验室区别

验收：待逐条证明。

MAIN LAB：
生活和长期系统

OLD WING：
探索 / 历史 / 风险

### XXXII · 物理布局未来扩展

验收：待逐条证明。

架构必须允许以后：

2D walkable lab

或：

3D lab exploration

现在即使还是UI房间，
也按真实空间关系设计。

### XXXIII · ROOM VISUAL ART

验收：待逐条证明。

未来每间房可以拥有：

roomBackground

roomDamagedBackground

roomUpgradedBackground

roomNightBackground

无需本轮一次生成全部，
但数据字段准备好。

### XXXIV · 重要房间CG

验收：待逐条证明。

可以逐步制作：

Containment

Quarters

Living

Medical

Greenhouse

Workshop

Radio

Zero

Black

Unnumbered

### XXXV · 房间之间共享系统

验收：待逐条证明。

例如：

Medical需要：
Power
Water
Herbs

因此房间系统互相依赖。

### XXXVI · Dependency Example

验收：待逐条证明。

Power broken
↓
Medical scanner unavailable

Water broken
↓
Greenhouse irrigation unavailable

Greenhouse damaged
↓
Herbal medicine shortage

### XXXVII · ROOM EVENT CHAINS

验收：待逐条证明。

事件可跨房间。

例如：

Water Leak
↓
Crawlspace
↓
Mold
↓
Medical respiratory cases

### XXXVIII · ROOM OWNERSHIP FEEL

验收：待逐条证明。

Jack应该逐渐对某些房间有：

“我的工作区”

B-07：

“我的房间”

宠物：

“喜欢的地方”

### XXXIX · LAB MAP UI

验收：待逐条证明。

地图不要只是列表。

使用：

楼层结构图

房间块

状态icon

点击进入。

### XL · FINAL DESIGN PRINCIPLE

验收：待逐条证明。

玩家不应该想：

“我要打开医疗系统。”

应该想：

“我去医疗室看看B-07。”

玩家不应该想：

“打开种植菜单。”

应该想：

“去温室，草莓应该熟了。”

玩家不应该想：

“看新闻菜单。”

应该想：

“去通讯室听早报。”

玩家不应该想：

“修理基地数值。”

应该想：

“净水室那台泵又他妈响了。”

这才是：

LAB IS A PLACE

而不是：

LAB IS A MENU.


## 2026-10-07 · 0.13.15补充实证（不替代140项逐条验收）
访客临床接入：js/lab/visitors.js admitted + js/lab/operations.js npcAtLab，医疗命令/患者列表、Street会面/日程、临床用水/传播、日报与人数一致；新增lab-visitor-care专项和真实浏览器流程通过。访客多日住院、多类型访客与交易交接仍缺实现，故Visitor模块整体仅部分完成。16项相关回归通过及年度/长期病程数据见LAB-VISITORS-REPORT.md。两份规格尚未逐项证明，不据此关闭整体目标。

0.13.16补充：医疗室与入口形成真实留院/跨日照护/资源消耗/复查/出院链；15项相关回归、真实四次Engine rest及移动端按钮验证通过。157位已知NPC患者表完整性已验证；封闭房间无扫描仪增强，心理状态不自动触发传染隔离。对应代码及局限见LAB-VISITORS-REPORT.md。更多访客类别/交易/完整医生来访仍缺，140项整体仍待逐条完成与验收。

## 晚报 / 夜间结果增量证据（2026-10-07，本地）
LIV/LV 部分新增实现：真实夜间告别入口可查看只读晚报；睡眠后记录实际结算结果，历史日报保留睡前最终状态。最近7个时间跨度，不伪造外出逐夜。对话优先避免晨报遮挡。夜间/晨报实际Chrome流程、保存刷新、五成熟槽配额、301源资源通过。详见LAB-OPERATIONS-PROGRESS.md。此证据不表示LIV/LV全部原文需求已完成，不表示所有140项或公网新发布已完成。

## XXV/XXVI 排班习惯局部证据（2026-10-07，本地未发布）
已形成的排班习惯可因外出、缺席、病况、封房、疲劳、断电、改班、未完成中断；原因变更只记一次动作反应，实际成功班次恢复，不补算中断日。供电不足停用电力值班、逃离B07不能工作。7相关文件及实际Chrome保存/断电→恢复流程通过，303源资源通过。具体见LAB-OPERATIONS-PROGRESS.md。非工作习惯/Grey Tide/全部访客互动尚未完整证明，保留原条款待办。

## LXIV / 07厨房 局部证据（2026-10-07，本地）
厨房已有可见只读现成餐食、安全收获与临期/禁用量摘要；恢复菌菇汤实际制作入原inventory，原ration保持默认。lastCookDay解开检查/制作共用锁且旧档保守兼容。5相关文件、真实Chrome制作/读取/英文/平板手机及304源资源通过。居民偏好自动饮食、全部厨房功能、正式美术与生活场景仍待证明，不将本增量作为该条完整完成。

## LXV 居民饮食新增证据（2026-10-07，本地未发布）
每日实际存活/在场居民和留院患者单次消耗原食品/净水成本；可开启安全收获选择，稳定个人类别偏好影响选择与小幅morale，封房/污染/过期门禁、死亡/离开去重、外出基地居民仍消耗。六相关文件与实际Chrome策略→夜间消耗→保存读取→英文本/手机平板通过，305源入口资源通过。特殊患者菜谱/宠物餐等继续保留原范围待办。

## LIV/LV 夜间人物与天气增量实证（2026-10-07，本地）
真实原模拟结算后记录在基地人物健康/活动病例/死亡、central天气与已收到新闻阶段；离岗死亡仍记、异地/潜伏期不提前泄漏，不造时间或新事件。7条汇总、68人/90主题均可保存；实际Chrome手机/平板、中英文、刷新、历史、五满量档及309源码资源通过。完整110回归先通过，新增后的111全套尚待取得。个人睡眠/宠物固定角落/全部非工作习惯未完成，因此这些条款仍是部分完成，不据此关闭全目标。详见LAB-NIGHT-DETAILS-REPORT.md。

## 2026-10-08 XXI–XXVI个人非工作习惯增量（本地）
13具体行为接入实际新闻阅读/房间/原每日结算，形成与中断、物理位置、真实水果消耗、换代与Story隔离专项通过；实际Chrome26175/58956、9相关2130、7存档24380、8年度2920日97473均退出0。52活动位置/180习惯/50宠物等五满容量档经无损keys-v2压缩20写入成功（51523），旧keys-v1/普通记录与可携导出兼容。参见LAB-PERSONAL-ROUTINES-REPORT.md。全部访客/停电对每类私人习惯的影响、特殊厨房和正式美术仍须证明；不将局部验收覆盖整140项。

## 2026-10-08 公网增量证据

LXVI个人习惯、07厨房恢复/宠物送餐与植物病程护理已发布0.13.20-preview；真实公网流程与旧档恢复通过。保鲜继续复用原植物加工，不冒称完整食谱扩展；140项仍按原范围验收。详见release-0.13.20-public-verification.json与TASK-AUDIT.md。


## 0.13.144 · 运营 XVIII：零号自主值班（本地验收通过，待公开）

- 原规格：运营 XVIII 五种行为分别接入自然日结：忘记、休息、做错、拒绝、另选安排。候选空岗须房间可用、有实际需要且无人排班，供电限制仍有效；不修改明日排班。
- 不接班不增加工作疲劳或扣可靠度；拿错工具为实际失败尝试，无工作成果；房间、习惯和完成记录按实际工作，非永久改排班。
- 新增 operations.b07Duty.records，30条上限、每天一条、旧档为空、非法/重复/未来记录过滤。换代清空个人决定，实验室资产保留。双语值班界面展示最近6条；无任务或奖励弹窗。
- 新模块 js/lab/b07Duty.js；接入 operations/operationsState/operationsUI/routineTransitions/legacy 与源码入口。
- 验证：专项自然随机六结果与旧档/缺席/健康/剧情/同日幂等通过；6个运营、学习、医务观察、习惯与真实换代相关文件通过。真实浏览器1366/768六结果可见、zh/en/zh、重新载入及实际休息跨日通过，无页面异常。
- 用户截图的七项狩猎导航另以1366×768、768×1024、390×844、844×390实测：内容真实滚动，导航Y位置误差<0.1px，六个实际切页、末尾按钮命中、无横向溢出通过。
- 尚非全目标完成；运营其余原条款、其余正式美术/人物长剧情及公网AI继续核对。Supabase组织已获选择授权，价格工具不可用，不创建未确认费用项目。


## 0.13.145 · 运营 XVI：Jack弱项技能成长（本地通过，待公开）

- 发现实际厨房/医务/温室工作能力固定42，成功值班不成长。新增 js/lab/jackSkills.js 与 operations.jackSkills；三项独立记录实际成功班次和最后完成日。门槛6/15/30/50/80班，0–5级，每级工作能力+6，从42到72；不把Jack变成专业医生，不改诊断/治疗规则。
- 仅真实日结成功且实际工作者为Jack时增长，使用成长前技能判定当班，失败/外出/隔离/疲劳休班/断电/房间不可用不增长；同日不重复。不为B-07、宠物、替班NPC计入Jack经验。维修与安防原强项、车辆系统不改。
- 旧档默认三项0，不推算/赠送过去经验；非法/未来/小数/越界字段回退；Jack技能随实验室完整换代保留，零号个人学习仍重置。排班界面显示三项等级/能力/实际班次/下一级，双语无奖励弹窗。
- 专项：三项各通过实际日结累积到80班/5级；同种随机种子的训练前后真实成功率改善、失败不记、独立技能、重复日结与旧/坏存档通过。7个运营/学习/医务观察/习惯/换代相关文件通过。
- 真实浏览器1366/768/390：三项均原生选择Jack排班→实际休息日结→跨升级门槛→可见48/100与1/5级→zh/en/zh→刷新保留，通过，无页面异常和横向溢出；手机截图已查看。
- XVI车辆强项及其他运营/房间条款尚需逐项统一核对，本批不声称整节或全部历史目标完成。


## 0.13.147 · 运营 IV 白天变化与无损存储（本地验收通过，待公开）

- 发现夜间差量已有，但同日新闻回应、在场人物健康/死亡变化未进入当日报告。operations.finish仅同日真实前后差量合并到 reports[].changes；NPC保留首次/最新健康、已显现病例数及生命状态，新闻保留首次/最新阶段；已存在的链状态不会被普通播报覆盖。跨夜仍用原nights，无伪造发生时刻。
- 仅观察在实验室/前一状态在场的人物；不复制来源/讣告原文，不揭示潜伏病例，不把健康下降擅自诊断为外伤；旧日报缺少changes时不补发历史。新字段可选，原15项summary及剧情/结局不改。
- 日报/历史晚报双语显示当日已观察变化；60报告与7夜间范围保持，不删除NPC/新闻。保存边界共用已验证数值压缩，完全相同变化组共享存储，读取恢复命名字段。
- 真实压力测试发现五成熟槽超限，继而增加同步无损LZW封套（abyss-local-lzw-v1），旧raw与keys-v1/v2读取保留，导出仍是原明文abyss-backup-v2。字典满重置、25万多样字符、emoji/不成对代理字符/控制字符、非法字母表/引用/重置、备份恢复与原型安全通过。
- 五个真实隔离浏览器成熟槽：50宠物、180习惯、80植物病例、240活动提醒、全部已知NPC/90新闻、每档60个不同日报变化；20次手动/自动保存及备份全部通过，占用3521512字节，端点与数量不裁剪。
- 单元：新同日变化专项及原夜间详情/晚报/报告规划/运营/零号值班/Jack技能、存储编码通过。真实浏览器1366/768/390原生新闻选择、可见健康死亡fixture、双向语言切换、刷新/休息后历史保留通过；原夜间详情及存储导出/导入/旧格式/坏编码备份恢复浏览器通过。最初并行浏览器启动/加载超时后，按终态改为顺序执行，未放宽断言。
- 仅完成本条实际缺口；原140条、全部正式美术与公网AI仍未统一终验，目标保持active。


## 0.13.148 · 同日恢复不抹掉过程（本地通过，待公开）

- 补147明确记录的缺口：reports[].changes.npc[].trace记录真实相邻观察前后健康/显现病例数/生命状态，依发生顺序保存。100→83→100仍显示两段及83–100范围，病例出现/恢复同理；不推断伤害原因，不写虚假时刻，不曝光潜伏病因。
- 每人每天最近32段、累计次数及本功能已记录的健康/病例最小最大值；超过窗口仍保留已观察极值。缺席后的不连续观察各段保留完整前值，不把间隔补成连续事件。原147摘要无trace时保持原样；首次新变化才建trace，过去过程不倒推。
- 新js/lab/dayTrace.js；NightDetails保存边界为每个trace自适应选择完整段、重复段引用或真实连续状态编码。三种表示均可无损还原命名字段；保留原结构/大小安全上限，不通过减人物/新闻/槽位或提高限制让测试通过。
- 专项验证：健康往返/临床出现消退、53次观察保留32条、原低值仍保留、死亡离开排班、无变化不增、旧/非法trace回退和原导出/紧凑存读通过。不同连续段/重复完整段（含缺口）与非法引用专项通过。原同日摘要/夜间详情/晚报/报告规划/编码/真实换代/武器存档7文件回归通过。
- 真实浏览器1366/768/390可见100→83→100受控fixture、原生展开/历史切页、zh/en/zh、刷新及真实休息归档通过，无横向溢出或页面异常。
- 初次满量逐段压力测试触发Local save exceeds structural limits；修复编码后，五个成熟槽保留60天不同的全部161人物/90新闻、每人32段/总33次、50宠物/180习惯/80植物病例/240活动提醒，20次手动/自动及备份成功，占6177826字节，逐段数量/端点均不裁剪。
- 仍不等于原运营IV或140条全部验收；其余历史扩展与公网AI保持欠项。


## 0.13.149 · 运营VII/VIII供电来源与真实备用电量（本地通过，待公开）

- 五类输入原已存在，发现备用电池每七天计时自动+20而无实际储能；新climate.batteryCharge为0–20。实际外部供给>0且总电力≥45时每日最多转存3、总储备等额扣除；低于10时仅释放剩余电量，部分电量不冒充完整保护。没有日期自动补满。原batteryReady旗标保留兼容，不再当能源来源。
- 旧档缺字段且旧电池已准备好→20，旧冷却未结束→0，未装→0；非法字段回退/截断；实际新购买带20初始电量，禁止重复购买。换代保留设备与现有电量，读档不重充。
- 发电量取实际可用油量（最多.35/日）与现有generator.condition；部分油按比例产出，损坏不耗油。残余电网/日照与太阳能家具/异常能源现有产出参数保留。天气停电判定/RNG次序、五档电力状态、低电力医疗优先等原门禁保留。
- js/lab/power.js提供纯当前来源估算与电池转存；Climate.lab调用真实日结。储备设备页五卡片双语/自适应布局，说明是当前估算而非未来预报。查看不扣燃料/不改状态，不暴露隐藏天气计划。
- 专项：五来源、故障/部分燃料、21天断电无免费回充、7步等能转存、部分备用、旧/坏档、实际购买/休息/同日幂等/读档与Story门禁通过。原climate351事件/150种子日、运营/习惯中断/夜报/换代回归通过；换代电量7保留。
- 浏览器1366/768/390原生购买、真实断电释放20→0、重新供电次日充至3、双语和刷新恢复通过；五卡片尺寸/水平边界检查，手机截图查看。强化无重叠检查与最终公开验证随本版发布执行。
- 尚不宣称原VII所有灯/温室/医务/电脑/门/冷藏效应已统一验收；其余历史大目标仍active。


## 0.13.150 · 分区供电真正约束加工与冷藏（本地通过，待公开）

- 核对原VII设备影响：温室增长/灌溉、医务设备加成、监控与房间灯已有powered判断；发现六种植物加工仅检查剩余2–4电力，低于10或优先别区仍能运作；冷藏设备已装即免热天食物储备额外损失，未统一考虑分区断电。
- PlantProcessing.facilityReady/available统一实际命令与按钮门禁：养成、在基地、开放温室、非事件/梦/战斗、温室已获供电、真实原料/污染/保质期、AP及用量；失败无消费，成功保留原六方法/费用/批次性状。提示说明10/25阈值并直达原生供电优先选择。
- 电力10–24新增storage优先（默认medical保留），培养舱持续保留供电。LabPower.refrigerating统一冷藏实际效果与状态显示：设备已装并且storage有电。热天食物储备额外损失与原随机鲜食变质均使用该判断，不把“已安装”当“正在运行”。
- 单元六方法逐一验证断电/别区失败原子性与正确分区成功/精确消耗，离基地/封房/Story/战斗/无AP/污染拒绝；旧默认/新优先读档、低电医疗/冷藏取舍与150组真实热浪日资源/水果变质通过。原150天气日/351事件、种植200种/性状医疗/运营/习惯中断/电池与换代回归通过。
- 浏览器1366/768/390：原生加工页跳转→选择greenhouse→实际保存加工扣1AP/3电力→storage冷藏→加工禁用→中英→刷新保留policy/批次→切medical显示冷藏离线，通过，无溢出/页面异常，手机截图查看。
- 未限制基础人工观察/照护、查阅已有记录/剧情/旧flag，不以全停机冒充设备影响。电脑、安全门、全部27房间与其他历史条款继续逐条核对，整体目标active。

同版核对补充：日报食物/燃料支撑天数也仍按“冰箱已装/发电机已装”计算，现与实际冷藏供电和实际发电燃料共用判断；不让预估继续假设断电冰箱或坏发电机仍在工作。专项验证预估随冷热供电变化、坏机无燃料burn，通过。


## 0.13.151 · 供水回路的真实供电与设备状态（本地通过，待公开）

- 原运营IX/XXVIII净水回路核对：旧回收只检查气候滤芯维护值及水泵磨损，停电/供电别区仍出水，净水滤芯设备故障不影响产出。新增纯LabPower.waterRecovery，实际日结、日报支撑天数、房间读数共用。必须已装滤芯、耗材维护>20、水泵与滤芯设备均在线（状态>=20且供水区有电）；产出保留最高0.45/日，两设备各按condition/80上限1折算。
- 新增water应急供电优先项，10–24可选供水区并保留培养舱，<10停机、>=25全区原规则保留。旧默认medical与五个原值不变，旧存档不赠设备或净水；新值正常保存。自动系统不要求Jack在场，封闭访问不等于关闭电路。
- 雨水+1.4、储水箱+0.15、家具水箱+0.12独立保留；原储备不被清空，饮水/医务/清洁/厨房/人工照护门禁不变。净水室可直接打开供电优先，并双语显示当前真实回收量与规则。
- 专项单元：0/9/10/20/25供电边界、医疗/冷藏/供水取舍、泵与滤芯19/20/40/80/100状态、耗材阈值/设备缺失/未建水房、真实每日水量、雨水与储水箱、离场/封房、纯读取无RNG或状态变化、旧/新policy与日报读数通过。供电/冷藏加工/运营/预估/150天气日351事件/真实换代回归通过。
- 隔离浏览器1366/768/390：净水室原生入口→0.000→供电优先原生选water→0.450→中英→刷新保留→实际一天净水49.95→泵损坏显示0.000通过，无溢出/页面异常，390截图已查看。
- 电脑/安全门、所有27房间与历史扩展统一终验仍欠，不以这一批代表全部完成；整体目标active。未修改受保护台词、route/ending/flags、真实玩家进度或实际密钥。


## 0.13.152 · 研究终端供电与安全设备状态（本地通过，待公开）

- 原VII电脑影响：Research.terminalReady统一实际研究purchase/availability与物品identify；养成须在基地、非战斗且终端有电。档案室已启用时需可进入、server实际在线（状态>=20且档案区供电）；初期未建档案室沿用培养区初始终端，避免新增房间解锁死锁。10–24新增archive应急优先，六个原值/默认medical与>=25全区规则保留。
- 科技网络与物件页显示双语在线/离线，执行研究和鉴定按钮与实际命令一致；失败不扣点/材料/不改变鉴定、异常权限或RNG。已解锁科技、已发现物件、主线记录和剧情推进仍能查看；Story不受养成供电限制。所有42项原科技及前置/材料/互斥/BLACK条件不变。
- 安全门与摄像机日报状态按真实在线性显示OFFLINE；封门SEALED、坏锁FAILING保留，旧日报不回写。自动隔栏/门岗核验协助使用online(lock)与online(camera)，不存在的门锁不再算可用；机械房间出入/主线门钥匙/route/ending/flags不变。原断电摄像机已能取消门岗保护，本批不把该原功能算新增。
- 专项验证七种离线原因原子失败、初期终端/档案终端、10电边界、20状态边界、新旧policy、真实购买科技与黑玻璃鉴定/异常可见性和完整存读、纯读取、Story隔离、门/摄像机实际状态、未建门锁无保护通过。phase3全部20检查、真实门岗日结/袭击与访客核验、运营/日报/供水/加工冷藏回归通过。
- 隔离浏览器1366/768/390：离线研究与鉴定禁用→主线记录仍可读→原生选择archive优先→实际研究vital_scan与鉴定黑玻璃→刷新精确恢复→坏服务器中英状态→断电日报设备离线通过，无溢出/页面异常，390截图查看。
- XXXIV门锁故障对B-07 Door Anxiety个体差异尚需实现/证明；其他全部房间/历史扩展原条款统一终验、正式美术、长剧情、公网AI审批仍欠，整体目标active。


## 0.13.153 · XXXIV门锁故障的个体反应（本地通过，待公开）

- 新增js/lab/doorResponse.js，接入现有医务日结、DiseaseRisks与DiseaseBalance；不新增病种/关系值或改主线flag。仅养成、在基地且存活在场B-07，物理门锁condition<20且已存在才参与。单纯断电不冒充卡锁；Story/离场/已离世/未建锁/condition>=20均无效。
- 胆怯>=60且比独立高>15：UNSETTLED，每日既有medical.stress +0.8；独立>=60且高过胆怯>15、并仍未获自由：RELIEVED，stress -0.8；其余中性。全部0–100有界。已有自由不因锁坏获得重复解放奖励。旧门锁故障链仍真实降低基地security。
- 现有disease_77 Door Anxiety使用既有病程：环境恢复倍率分别0.75/1.2，仅此病此个体。紧张且压力>80才给原随机暴露池加入相关环境资格，仍走原2.5%抽取、宿主/三病例上限、恢复保护；不强制发病、评估或治疗，不瞬间治愈，不改别的心理病/身体健康/创伤记忆。
- 病况反应只在既有医疗每日推进中执行，读档/同日观察不重复。观察写入既有有界患者history与运营notes（首次观察，双语注册），不凭动作自动诊断；同一观察中英文不会重复记。旧档没有新必填字段；后继个体仍用全新B-07患者资料，历史实验室记录保留。
- 医务室现有7个病程状态与4档严重度补中文/英文标签，稳定状态ID不变。原截图中文直接显示IMPROVING/MODERATE已修，新增data-medical-condition用于真实行验证。
- 专项：两种反应/中性、阈值/排除、精确压力、只影响既有门焦虑、纯读取/不改flag与个性、30种子真实医务日结差异、300种子原机制12次发病、两类各20种子的最长300日自然病程均恢复且保留保护期、实际Engine休息/存读/幂等、原故障链security下降通过。临床90种、90×3环境×40种子=10800病程、门岗/运营/真实继任存档回归通过。
- 初版隔离浏览器1366/768/390实际Engine休息两种个体→历史双语→刷新精确保留→原生修锁停止环境效应但不清病况/flag通过。中文状态补丁的最终浏览器验收随本版发布执行。
- 尚非整体目标完成；其余运营/27房间与所有历史扩展原条款仍须统一逐条终验，正式美术/长剧情与真正公网AI审批仍欠。


### 0.13.153 公开验收回执（2026-10-15）

游戏提交fb061f11ae132a64bb166aa0dfe0b484dfbe4ee3；Pages run38829864593 completed/success。公网1366/768/390两种个体真实Engine休息、原锁坏security损失、现有门焦虑病程差异、观察记录双语/中文严重度、刷新精确保留与不重复推进、原生修锁停止环境反应但不清病况与flag，通过，无横向溢出/页面异常。日志verification/lab-door-response-public-153.log。index与五张外置CG逐字节一致，426源码资源200、私密路径404通过。

专项包含30种子日结、300种子原暴露机制12次发病、两类各20种子最长300日均恢复；90疾病三环境四十种子10800病程、临床行为/运营/门岗/实际继任旧新档回归通过。交付../abyss-lab-0.13.153-preview.zip，不含实际密钥、玩家档案或依赖。XXXIV门锁个体反应本批已取得行为与公开证据；其余历史140条/27房间和扩展仍按原始范围逐项终验，不把测试通过当全部完成。正式美术/人物长剧情与真实公网AI审批仍欠，整体目标active。


## 0.13.154 · 深层房间的独立已发现档案（本地通过，待公开）

- 原27房间12/18/19/22/27核对：zeroArchive/seriesRelics/blackOrders/e3/continuity/unknownTerminal原先全部打开同一个旧progress.story列表，没有分区资料和E3真实时间。新增js/lab/roomRecords.js，按七种入口分别投影当前存档真实发现：StoryFiles已read/show/READ标记、已获Expedition documents、实际Narrative.history片段/seen完成记录、已留下continuity.echoes与真实story.revision.e3。
- 档案室storyFiles整合已发现内容；零号通道只零号/来源记录；B系列只B系列/录音/对应文档；黑级只权限指令；E3显示相关伊甸记录与真实执行窗口；连续性与未登记终端分别按自身已发现资料和已留回声展示。不展示未发现标题/未读正文，不从完整scene.lines补写未实际听到的行。旧档若只保留完成标记，显示完成记录而不伪造对白。
- 销毁记录保留处理事实，不恢复正文；排队/active但未记入history的场景不泄漏。Host seed/raw flags不显示；不新增异常解释/机构设定/后果，不重写Claude审定文本或任何保护场景。无任何新存档字段、跨档/Meta读取、剧情flag写入或研究奖励。
- E3仅在已知指令且原计时存在时显示HH:MM:SS，读取原remainingSeconds/status，不启动/加速/推进计时；到期只说明后续待确认，不创作后果。档案室回收实际narrative.firstWord.word/day。原发现场景/调查选择及flag生成仍走原系统，不把查阅冒充首次调查。
- 七入口保留房间可进入门禁与返回房间；已缓存记录不依赖活服务器。卡片独立折叠，语言变化重绘对应分区并保留展开项，窄屏无横向溢出。
- 专项验证空档/七种分类/未发现和部分行防剧透/销毁不可复原/HTML转义/纯读和保护文本哈希/旧完成记录/真实E3状态与孤立未知计时隐藏/实际首词/序列化及跨存档隔离通过。27房间/独立场景与装饰/原房间操作、Claude修订全量、首词CG与回收回归通过。
- 隔离浏览器1366/768/390七个原生房间按钮、真实分类排除、断电已发现内容可读、阅读前后完整Engine状态不变、销毁保护、E3 03:25:45、首词、语言展开项保留、刷新精确恢复通过；390截图查看，427源码资源200/私密路径404通过。
- 仅证明本批分区档案功能；这些房间的所有原条款（实际下层小区域、扫描/隐门等）及其余历史扩展统一终验、正式美术、人物长剧情、公网AI审批仍欠，整体目标active。


### 0.13.154 公开验收回执（2026-10-15）

游戏提交781558592c1a60d64a6e8ee0d1cb79b64d376528；Pages run38831474747 completed/success。公网1366/768/390七个原生房间档案入口分类与排除、断电已发现资料可读、阅读前后Engine全状态一致、销毁记录保护、E3真实03:25:45、实际首词回收、双语展开项保留、刷新精确保留通过，无横向溢出/页面异常。日志verification/lab-room-records-public-154.log。index和五张外置CG逐字节一致，427源码资源200与私密路径404通过。27房间与装饰/访问/观察回归、Claude全文/保护哈希/旧档/倒计时/ACT IX全量与首词CG回归通过。

交付../abyss-lab-0.13.154-preview.zip。仅接回各房间已发现记录，没有改主线调查选择或奖励。下一项已直接核对rooms.js：lower/sublevel/crawl的survey仍只扣1AP并记entry/utility/rear，materials只按未领区域给2废料；尚无局部供电修复/局部门状态/连通分区，不能算原17/20/24探索条款完成。后续须补真正作用，同时保留旧survey/salvaged和所有主线/隐藏房间门禁。其余历史扩展统一终验、正式美术、人物长剧情、真实公网AI审批仍欠，整体目标active。


## 0.13.155 · 下层连通区域、局部线路与检修门（本地通过，待公开）

- 原房间17/20/24核对：lower/sublevel/crawl原3区survey只是各扣1AP和记数组。新增js/lab/facilities.js统一真实命令/按钮/拓扑：入口调查→隔离破损支路→设备区调查→局部线路修复→手动释放检修门→后段调查。调查/隔离/修复/释放各1AP；已调查路线免费移动，实际更新Jack所在房间与本地区域。未按顺序、房间/事件/战斗/离场/Story/无AP或材料不足均原子拒绝。
- 三房保留各自几何路线、名称与配电箱/屏蔽/阀门造型；实际地图按调查、所在区、检修门与主网电力显示。修复消耗2废料+1线缆（lower/sublevel）或1密封件（crawl），只一次，改善本房损坏12；不生成电力。局部照明只在已修复且本区真实有电时亮。
- 新roomSystems.rooms[id].local可选version1/secured/repaired/doorOpen/area，严格按有效调查/安全工序读取；旧survey/salvaged原样保留，不伪造修复或重发废料。旧已调查后段仍可沿已知路线通行。原每区2废料、每房最多6的一次性回收保留。换代保留物理线路/门/回收进度，新个体关系与病况仍独立。
- crawl LV2且线路已修复、后段已调查时，工程/供电/净水的原设备维修每次增加6点基础修复量（仍按原工作倍率与100上限），费用/AP/部件不变；封闭夹层或目标房间、离场则无捷径。未打开其他主线/隐藏房间，未改任何route/ending/故事flag。
- 实际浏览器暴露原UI死路：休息触发日常事件时，原选择被当前功能页隐藏，Navigation.select又因pending拒绝回主页。新增Navigation.revealEvent并在UI.showPending使用，保留导航历史后回主页显示真实事件，不自动选择。新分区页面明确提示并提供处理事件入口。
- 单元：三房完整流程/精确AP与费用、乱序/重复/缺料/各门禁原子失败、有限回收、纯地图/主网灯光、旧路线与坏字段、精确存读、实际泵维修+6通过。27房间/运营/档案/场景/Claude保护文本及真实继任回归通过；继任测试特意放入已修线路/开门与部分已回收状态，完整保留。
- 隔离浏览器1366/768/390共九条完整流程：原生调查隔离修复释放→AP0真实休息→后段/免费移动→3次有限回收→语言→刷新精确恢复，crawl原生泵维修额外6点通过；三个尺寸事件入口可见且真实选项可点击处理，通过，无页面异常/横向溢出，390两种地图截图查看。428源码资源200/私密路径404通过。
- 仍不声称三房全部原规格完成：异常扫描/秘密通路的叙事接入、更深入区域与其他房间/历史扩展统一终验、正式美术、长剧情、公网AI审批仍欠；整体目标active。


### 0.13.155 公开验收回执（2026-10-15）

游戏提交7ae2ae006301e44f86a211040219c6bb85ce9306；Pages run38834854172 completed/success。公网1366/768/390三房共九条完整原生调查/隔离/修复/手动开门→AP0真实休息→后段/免费移动→有限回收→语言→精确读档通过，夹层真实维修+6通过。三个尺寸额外真实事件入口将页面切回home，原生选项可见可点击并成功处理，未清空事件绕过。无页面异常/横向溢出。日志verification/lab-facilities-public-155.log。index与五张外置CG逐字节一致，428源码资源200/私密路径404通过。

专项三房乱序/重复/缺料/门禁原子性、纯地图/真实供电、旧调查与有限领取/坏字段/精确重载/实际维修增量，及27房间/运营/档案/场景/Claude保护与实际继任回归通过；继任用已修线路、已开检修门、后段与部分已领取的真实新字段验证，不只测试空默认。交付../abyss-lab-0.13.155-preview.zip。不含实际密钥、玩家存档、依赖，未调用付费AI。

本批完成局部分区连通与修复/门/维修捷径，不等于17/20/24全部要求。异常扫描/秘密路线的剧情与权限接入、旧育成室等其他房间独立作用、所有历史扩展原条款统一终验、正式美术、人物长剧情、真实公网AI审批仍欠，整体目标active。


## 0.13.162 · 27房间原生入口与跨窗口返回（2026-10-16，本地验收）

对照27房间原规格PART I/II及房间01/02，新增tests/room-entry-browser.cjs，逐房从真实按钮进入主系统/次级入口，再点击返回，使用实际活动窗口而非只检查#modal。27间当前可见入口去重后130项，1366/768/390共390次点击与返回本地通过；JSON逐项记录verification/room-entry-matrix.json，四类页面各三尺寸留图。最初审计误把其他窗口、正常离开与库存不足提示算作无效，已校正活动界面和合理拒绝判定；未将这些误报宣称为游戏漏洞。

实际修复：
- js/lab/roomUI.js：观察室/通讯室来访入口保存来源房间；喂食口用原有具体食物选择，Jack房间睡眠用原有结束今日确认，不再跳到B07互动/夜间交流。成功普通喂食/休息后，在没有事件、对话、发现或强制窗口时返回原房间。
- js/expeditionUI.js、js/road/ui.js：仓库/变卖物和车辆窗口接回来源房间按钮，每次筛选/换页重建后保留。车辆页支持工程室和工坊各自来源。修复旧库存窗口close事件移除新房间nav-docked样式的竞态。
- js/navigation.js、js/lab/roomUI.js：外部导航清除旧来源，跨窗口内部切换保留来源；回房间关闭旧窗口与车辆渲染，不残留遮挡层。js/expansionUI.js移除重复adopt调用。
- 返回前检查真实所在地；不在实验室（包括有效载具行驶中）按钮禁用且控制器拒绝，不瞬移、不改进度。锁定提示不附返回按钮，控制器也不能绕过；剧情模式拒绝养成房间execute与return，不改剧情状态。

新增tests/room-care-browser.cjs三尺寸通过：具体食物真实扣库存/行动点、首次照料奖励发现保留并实际确认、普通喂食返回、仓库筛选和中英切换后回房间、车辆子页返回/合法行驶禁止回房间、来访返回、强制提示不被覆盖、取消睡眠不跨日/确认真实跨日并落盘、切剧情档后房间操作不能推进或改档。无付费AI。测试曾使用不满足旧存档校验的旅行样本被正常迁回基地，已改为真实拥有车辆/有效目的地的drive样本并断言校验后仍在行驶，最终拒绝路径才计入证据。

换装与滚动回归1366×768、768×1024、1024×768、390×844、844×390通过：锁房可换装、模块品牌隐藏/主页恢复、顶栏原地、仓库分别完整显示21/10/10/6/4卡且可滚动。27房间状态/升级隔离、12陈设/5状态、7档案投影及Claude双语保护相关回归通过。435源码资源和私密路径保护通过。版本0.13.162中英日志/菜单/页脚一致，语言包14090。未改存档字段，无数据迁移；原旧档、物品/剧情/flags/route/ending不删除。

验收边界：130入口可用不等于27房间每项专属玩法已实现。培养舱独立生命维持/玻璃门/旧物交互、Jack私人细节、其余原规格未逐条证实项继续列为待验；不能把通用观察文本当作完成。审定梦/Host、深层秘密、全部历史扩展统一终验、正式美术/人物长剧情及真实公网AI审批仍欠。公开结果在后续回执；整体目标未完成。


### 0.13.162 · PART I / II 房间入口逐房证据

以下每行在1366/768/390各实际点击所有列出按钮，并验证当前活动界面与返回。leave预期到培养舱；合理库存不足/未调查提示计为可见响应，不能计为完成其后玩法。测试从隔离房间基线开始，不将其夸大为从世界地图驾车到每间房或完成全流程。动态展开按钮/各专属系统深层功能不在此表的完整性结论内，仍须分别核对原规格。

| 房间ID | 实际入口 | 当前入口结论 | 原规格专属玩法全量结论 |
|---|---|---|---|
| containment | `observe`、`food`、`medical`、`roomMemory` | 三尺寸点击/返回通过 | 仍须按原条款逐项证明 |
| quarters | `rest`、`journal`、`inventory`、`jasmine`、`roomMemory` | 三尺寸点击/返回通过 | 仍须按原条款逐项证明 |
| living | `wardrobe`、`privacy`、`bedroom`、`habits`、`roomMemory` | 三尺寸点击/返回通过 | 仍须按原条款逐项证明 |
| medical | `patients`、`pharmacy`、`recovery`、`quarantine`、`roomMemory` | 三尺寸点击/返回通过 | 仍须按原条款逐项证明 |
| genetics | `mutations`、`experiment`、`serums`、`plantArchive`、`roomMemory` | 三尺寸点击/返回通过 | 仍须按原条款逐项证明 |
| engineering | `maintenance`、`power`、`water`、`roads`、`roomMemory` | 三尺寸点击/返回通过 | 仍须按原条款逐项证明 |
| kitchen | `cook`、`food`、`harvest`、`pharmacy`、`jasmine`、`roomMemory` | 三尺寸点击/返回通过 | 仍须按原条款逐项证明 |
| storage | `inventory`、`valuables`、`trade`、`bedroom`、`roomMemory` | 三尺寸点击/返回通过 | 仍须按原条款逐项证明 |
| greenhouse | `plants`、`seeds`、`ecology`、`harvest`、`roomMemory` | 三尺寸点击/返回通过 | 仍须按原条款逐项证明 |
| workshop | `weapons`、`parts`、`roads`、`roomMemory` | 三尺寸点击/返回通过 | 仍须按原条款逐项证明 |
| observation | `cameras`、`habits`、`pets`、`visitors`、`roomMemory` | 三尺寸点击/返回通过 | 仍须按原条款逐项证明 |
| archive | `storyFiles`、`medicalArchive`、`newsArchive`、`personnel`、`roomMemory` | 三尺寸点击/返回通过 | 仍须按原条款逐项证明 |
| power | `power`、`maintenance`、`powerPolicy`、`climate`、`roomMemory` | 三尺寸点击/返回通过 | 仍须按原条款逐项证明 |
| water | `water`、`waterTest`、`maintenance`、`ecology`、`roomMemory` | 三尺寸点击/返回通过 | 仍须按原条款逐项证明 |
| radio | `news`、`visitors`、`deliveries`、`caravans`、`climate`、`dailyReport`、`roomMemory` | 三尺寸点击/返回通过 | 仍须按原条款逐项证明 |
| hall | `research`、`plantArchive`、`diseaseArchive`、`mutations`、`roomMemory` | 三尺寸点击/返回通过 | 仍须按原条款逐项证明 |
| lower | `survey`、`restore`、`materials`、`leave`、`roomMemory` | 三尺寸点击/返回通过 | 仍须按原条款逐项证明 |
| zero | `zeroArchive`、`continuity`、`survey`、`leave`、`roomMemory` | 三尺寸点击/返回通过 | 仍须按原条款逐项证明 |
| black | `blackOrders`、`research`、`storyFiles`、`e3`、`roomMemory` | 三尺寸点击/返回通过 | 仍须按原条款逐项证明 |
| crawl | `repairBypass`、`maintenance`、`materials`、`survey`、`roomMemory` | 三尺寸点击/返回通过 | 仍须按原条款逐项证明 |
| nursery | `pets`、`patients`、`storyFiles`、`roomMemory` | 三尺寸点击/返回通过 | 仍须按原条款逐项证明 |
| series | `seriesRelics`、`storyFiles`、`objects`、`roomMemory` | 三尺寸点击/返回通过 | 仍须按原条款逐项证明 |
| surgery | `advancedMedical`、`recovery`、`medicalArchive`、`survey`、`roomMemory` | 三尺寸点击/返回通过 | 仍须按原条款逐项证明 |
| sublevel | `survey`、`restore`、`materials`、`leave`、`roomMemory` | 三尺寸点击/返回通过 | 仍须按原条款逐项证明 |
| stairs | `steps`、`markSteps`、`listen`、`leave`、`roomMemory` | 三尺寸点击/返回通过 | 仍须按原条款逐项证明 |
| core | `corePower`、`coreOverride`、`maintenance`、`continuity`、`roomMemory` | 三尺寸点击/返回通过 | 仍须按原条款逐项证明 |
| unnumbered | `unknownTerminal` | 三尺寸点击/返回通过 | 仍须按原条款逐项证明 |


### 0.13.162 公开验收回执（2026-10-16）

提交e6cf9b5d01045d6b597f65d6549f2ac8c4a0f3fe；Pages 38954294538 completed/success。最终公网27房间、每尺寸130个独立入口、1366/768/390共390次原生点击/当前窗口/返回通过，零失败；逐项JSON和27行验收表分别在verification/room-entry-matrix.json及LAB-SPEC-ACCEPTANCE-INDEX.md。普通离开与明确拒绝条件按真实预期校验，未把入口通过当作专属玩法全量完成。

公网实际照料三尺寸通过：食物库存/AP、真实首照料发现保留、普通照料回原房间、库存筛选/语言/跨窗口返回、车辆子页/合法drive状态禁用返房/控制器拒绝且不改档、来访来源、锁定窗口无返房按钮且API不能跳过、睡眠取消/真实跨日落盘、Story存档拒绝养成房间操作且不改故事状态。三尺寸菜单/中英日志一致为0.13.162；index与五张外置CG逐字节一致。四个公网脚本连续执行退出0，verification/*-public-162.log留证。

本地五尺寸换装/仓库/顶栏回归、435源码资源及私密路径、房间/陈设状态/发现档案/Claude保护相关回归通过。英文包14090。提供../abyss-lab-0.13.162-preview.zip，不含真实.env/密钥/玩家进度/依赖，无付费AI。既有存档字段/剧情文本/flags/routes/endings未改。

下一批按原27房间条款补实际专属交互：优先培养舱生命维持、玻璃/门与已发现旧物，不写新剧情、不提前显示隐藏线索；同时继续未全量证明的历史目标。审定梦/Host、深层秘密、全历史统一验收、其余正式美术/人物长剧情与真实公网AI审批仍欠，整体目标保持未完成。


## 0.13.163 · 培养舱实际检查与舱边旧物（2026-10-16，本地验收）

对照27房间原规格01，新增js/lab/chamber.js，主观察入口不再只写通用观察句。面板显示既有Climate室温、Home空气质量、Climate电力/水储备，以及Ops空气过滤器/水泵/走廊门锁的真实状态。过滤器和泵按各自所属工程/供水分区供电；不把培养舱有电误当成它们全有电，不制造氧气传感器或B07体温。B07是否在舱边由原角色实际位置投影，开放后显示旧培养舱，不复制怪物模型。

行为：记录仪器检查每天一次、1AP，保存当时数值/设备状态/通道和驻留快照，旧记录不会随维修变动；保留最近120次。外侧玻璃接触检查每天一次、免费，只记实际动作，不虚构体温、加关系/治疗或改RNG。门锁现场按钮调用原ops:repair，原报价、工具零件、废料、AP、磨损修复与原观察链照常；空气过滤器/水泵按钮实际进入其所属房间，不能遥控修复未进入房间。环境设备接既有气候系统。

旧物：B07旧铭牌、喂食口/空碟、旧搪瓷杯、胶带指印、旧体温记录各有独立图形，后三项仅在当前档原旗标/已完成场景证明后出现，部分播放不提前显示指印。明确记录旧物位置后，只把已知物件元数据存进房间；不授予库存副本、不创建剧情flag。新chamberRecords范围只投影当前档实际听到的原台词和已记firstWord，旧档只有完成记录则保留完成、不补对白。Host flags不标注、不新生成或高亮种子。

存档：roomSystems.rooms.containment.chamber使用可加v1结构：checks/glassDays/objects。旧档缺失默认空；非法日期、重复记录、未知物件过滤；读面板不写状态/全局meta。实际继任测试加入原仪器记录及杯/指印元数据，完整房间资产和旧物仍保留，不给新B07旧身体/关系。未改旧fields/scenes/flags/routes/endings。

本地：lab-chamber单元通过真实读数/读取纯净、精确AP/当时快照、拒绝原子性、跨日保存、旧档迁移、原通道条件、已读单句及首词转义；legacy-lab-carry实际告别/新个体和查读通过。隔离Chrome1366/768/390实际检查、触玻璃、原门锁修复及精确费用、原生移到工程室/返回、通道开放、五旧物记录、仅一条已听对白、中英展开保持、精确刷新/重复禁用通过。每张旧物卡原生滚动/命中检查和真实视口截图通过；曾尝试超长子元素截图产生不正确裁切，已弃用。原room-care三尺寸、27房间/7旧档案及Claude保护相关回归通过。436源码资源200/私密路径保护通过。语言包14121，版本0.13.163日志/菜单/页脚一致。

### 原培养舱条款当前范围
| 原要求 | 此批证据与边界 |
|---|---|
| OBSERVE / CHECK LIFE SUPPORT | 已接实际环境和设备读数、1AP逐日检查；不是完整生理传感器模型 |
| FEEDING HATCH | 0.13.162具体食物/AP库存已实测，本批兼容回归 |
| GLASS / DOOR CONTROL | 触外侧玻璃可记录；通道开放复用原Home.freedom表达/健康门槛，不加AP、不能反锁；未伪造DOOR_INSIDE_RELEASE |
| ENVIRONMENT CONTROL | 接既有环境/设备系统，读数随原系统变化；未新增一套无效滑杆 |
| 旧铭牌/空碟/杯/旧温度/指印 | 已知条件下独立显示、明确记录后随实验室保留；原对白仅实际已读部分 |
| 开/关内侧释放装置 | 完整电气开关仍未实现，不能把原单向开放和只读指示冒充完成 |

公开验收结果见后续回执。其余27房间条款、审定梦/Host、深层秘密、全历史统一终验、其余正式美术/人物长剧情、真实公网AI审批仍欠；整体目标未完成。


### 0.13.163 公开验收回执（2026-10-16）

提交c2130e97fb279c815af0498f355aa5188a462194，Pages 38958868806 completed/success。最终公网1366/768/390三尺寸培养舱真实分区供电读数、1AP检查/免费外侧接触、原门锁修复和准确费用、实际进入检修房间、原有日常通道开放条件、五类已知旧物明确记录、单条实际听过的原对白、语言展开保持和精确刷新全部通过。每个旧物卡片均通过原生滚动/遮挡命中检查，手机主面板与旧物视口已查看。

额外公网原生“准备告别→自由离开→输入新名→迎接新个体→培养舱”通过：chamber仪器/接触/旧物元数据逐字节保留，世界日20不回退、代际2/年龄0/新名独立，旧物仍五件，新个体没有补出旧对白；刷新后仍完全一致。verification/lab-chamber-inheritance-browser-public-163.log退出0，对应截图lab-chamber-inheritance.png。不是仅调用继任函数的表面断言。

原room-care三尺寸公网回归、菜单/日志中英与0.13.163一致、index及五张外置CG字节校验通过，四脚本连续退出0；verification/*-public-163.log留证。单元/实际继任/房间/已发现档案/Claude保护相关回归通过；436源码资源200及私密路径保护通过；英文包14121。此批未重复宣称162的390入口矩阵全量新验，仅对变化入口和相关实际流程作新验证。

完整交付../abyss-lab-0.13.163-preview.zip，包含培养舱代码、新旧档及继任测试、七张场景/旧物/继任截图；不含真实.env、密钥、玩家存档、依赖，无付费AI。旧data/route/ending/flags和审定文本未删除或改写。

内侧释放装置完整开关仍欠，当前只有原有单向通道开放/故障读取；后续继续，不以此批替代完整要求。其余房间、审定梦/Host、深层秘密、历史统一终验、正式美术/长人物剧情、公网AI审批仍未全部完成，整体目标未完成。


## 0.13.164 · 内侧释放装置实际控制（2026-10-16，本地验收）

补原培养舱“开/关内侧释放装置”条款。新增js/lab/insideRelease.js，内侧电动驱动器与独立机械拉柄分离；不是仅切一个UI文字。安装沿用已开放日常通道前提，扣1AP/1电线/1工具零件；开关切换免费。合上玻璃门只是合上未锁门板，不修改home.freedom或任何剧情旗标。SVG门板位置随实际开合改变。

电动释放需开关ON、培养舱真实供电与驱动状态至少20，每次开门扣0.2电力、驱动磨损1；机械/外侧开门无该消耗，断电/关闭回路/驱动故障仍可从内侧手动开门。驱动器检修扣1AP/1电线并修复40，上限100。无待机虚构耗电、无重锁、无关系/健康/剧情加成。

真实移动：放在LabOperations.finish中个人日程确定之后、日报捕获之前，依据原人物实际驻留变化打开门。主动出舱按当前电动/机械路径，返回时外侧开门；医疗隔离转移记作转移操作，不臆称它主动按键。自由离开/它选择离开的真实告别也打开实际门板；自然寿终不虚构离开动作，下一位进入时才外侧开门。消失/升华不新加解释、警示或异常揭示。耗电进入实际日报，单元对照ON/OFF真实Engine跨日验证0.2差值和日报一致。

存档：chamber.release可加v1，installed/enabled/condition/panelClosed/installedDay/nextId/近120条真实操作记录。旧163档缺字段默认未安装；已有DOOR_INSIDE_RELEASE/shared_release则兼容为已安装、安装日期未知0，不重复扣件、不新造剧情flags。切换/维修/开门含真实操作者、当时电力与磨损；数据校验剔除重复/未来/未知记录。读界面不改状态或Meta。继任保留硬件/开关/磨损/原日志，新个体的关系及通道许可仍按原规则独立。

UI：开关/机械/电动/检修独立按钮、状态卡及使用记录；操作和中英切换保留门控与记录展开，不再每按一次都折回目录。按钮受实际库存、AP、供电、磨损和门板位置约束。原培养舱/旧物流程已回归，手机图已检查。

验证：lab-inside-release单元通过安装/维修/开门精确成本、原子拒绝、断电/故障机械释放、禁止反锁、无剧情/RNG改动、旧标识兼容、新旧档保存、真实跨日自主出舱、耗电日报、医疗转移、真实告别/自然寿终/继任。Chrome1366/768/390原生安装→关门→OFF/机械→ON/电动→断电/磨损/维修→中英展开→精确刷新→真实睡眠出舱→独立继任流程通过，含实际自由告别门板已开。原chamber三尺寸、运营13设备/7排班、真实夜报/夜间详情、个人日程、门锁不同反应、实际实验室资产继任及Claude保护相关回归通过。一次浏览器自动审批超时而未启动，重试一次后正常完成，不把超时当测试失败或通过。437源码资源200及私密路径保护通过，英文包14139，0.13.164版本校验通过。

原“开/关内侧释放装置”在此实现电动回路ON/OFF及真实开合/能耗/故障/手动后备；保留原开放条件，不以反锁剥夺已给出的通行。原163记录保留作历史，不再代表此条当前仍欠。完整27房间其余条款、Jack私人空间、审定梦/Host、深层秘密、全部历史统一终验、其余正式美术/人物长剧情与真实公网AI审批仍欠，整体目标未完成。公开结果见后续回执。


## 0.13.165 · 55件异常物件纠错（2026-10-16，本地验收）

按原物件名称/原lore逐项核对55件。确认并纠正9件：死者磁带机不再用裸磁带替代，改有机身/扬声器/双卷带窗/播放控制/提手；熄灭的星依据中文原设定是金属星球，取消五角星；生长的书取消幼苗，补书页/装订根线；饥饿镜取消臆造牙齿，保留镜面/坐姿倒影；食盐心脏为连续心脏体积/主动脉与管口，不再两个分离球体；无影梳妆镜改椭圆镜面/转轴支架/底座；空瓶增加开放瓶口与内壁；无字墓碑改拱顶非完整圆盘；骰子六面分别1/6、2/5、3/4，相对和七，不再同屏出现相对的3与4。

定位时曾误把旧bedroomArt.item当最终渲染器，已核实bedroomDepth覆盖旧函数，当前实际渲染具备XYZ旋转及中心锚点；因此没有按错误判断修改位置/碰撞，也没有迁移用户布局。55件继续使用同一个实体模型用于目录、卧室和无编号房间，不另造错配贴图。库存、ID、尺寸/占地、价值、剧情文本、flags和存档格式均未改变。

验证：55件名称/原设定逐项检查；55个独立模型、220方向几何/真实卧室render引用/有限边界和语义部件检查通过；浏览器55目录/55卧室、32放大旋转视图无裁切/NaN/页面错误，9件纠正对照图已查看（verification/anomalous-corrections-165.png）。原生1366/768/390三尺寸实际卧室已摆物转入、库存转入、双语/保存刷新/取回数量守恒与房间陈设显示通过。实际继任资产无损、Claude场景/保护哈希、版本校验、内侧释放装置、437源码HTTP资源和私密路径保护通过。英文包14142，内联主页44376522字节。

此批是具体错配与几何修复，不声称55件全部达到正式手工美术品质；原55件造型/比例与正式美术仍接受逐件后续审查。0.13.164内侧释放控制此前完成本地验收，尚未单独公开，本次一并进入165公开包。其余历史任务及公网AI审批仍未全部完成，不标记整体目标完成。公开验证回执随后补记。


### 0.13.165 公开验收回执（2026-10-16）

提交9f6d2f6111b5d7522ec1c0655a5815d4f18cf527，Pages38964019745 completed/success。最终公网六个脚本顺序执行退出0：anomalous-art-browser（55目录/55卧室/32放大旋转及9件纠正截图）、lab-unlisted-browser（三尺寸真实摆放物与库存转入/自由取回/数量守恒/中英刷新）、lab-inside-release-browser（三尺寸精确费用/实际门板/断电故障手动/真实跨日及独立告别继任）、lab-chamber-browser（三尺寸实际设备与旧物）、release-log-browser（三尺寸0.13.165中英菜单/日志一致）、public-release-integrity（主页及五CG与安全发布目录逐字节一致）。verification/*-public-165.log留证。九件新截图与55件全图已查看。

前一批164内侧释放装置随165正式上线，包含真实自由告别门板打开及新个体硬件保留；164没有单独发布，不虚构164公开运行号。165的几何修复不改变任何物件ID/尺寸/库存/价格/原lore或布局，旧存档不需迁移。审定剧情/保护文本、继任资产及437源码资源回归通过，无实际玩家进度或密钥读取，无付费AI请求。

交付../abyss-lab-0.13.165-preview.zip，含本批源代码、测试与新旧模型截图、安全公开主页，排除真实.env/密钥/玩家存档/依赖。55件仍是可旋转的代码实体，不能把本次九件纠正宣称为全量正式手绘美术完成；整体历史目标仍未完成。后续继续Jack私人空间、剩余27房间条款、审定梦/Host/深层秘密与全历史统一终验，其余正式美术/人物长剧情、公网AI审批仍有欠项。


## 0.13.166 · Jack私人收纳与相册（2026-10-16，本地验收）

对照27房间原规格02，新增js/lab/privateEffects.js与privateEffectsUI.js。在quarters新增“私人收纳与相册”，保留原睡眠/日记/公共库存/Jasmine入口。实际库存物件可进入私人盒或相册，两处共用24件；取回恢复同一库存数量，整理免费/0AP。非食物按既有loot白名单验证；鲜食/原食物栏及商队水果咖啡巧克力不进入盒中。相册只接实际已拥有的old_photo/p5_photo，不凭空赠照片、不画未知人物或替换正式CG。仅在Jack当前进入quarters、房间可用、无出行/事件/狩猎/梦且养成模式可操作。

新增roomSystems.rooms.quarters.effects可加v1：box/album/memories/transfers。读档缺失默认空，不改原库存/剧情字段。存取数量、共享容量、公共库存上限先校验后变更；过容量的合法旧数据保留供取回，不静默裁掉。交接保留实际日期/物件/数量/位置最近80条。只有一件时不重复展示批量按钮。手机双列小卡、82px容器图标、可折叠说明；最初单列检查只有两张完整卡未达标，已修正并保持至少3张完整卡验收门槛，最终手机图显示四张完整卡。

Jasmine盒只识别当前story.flags已知的KNOT/SINK/PLATE/REMOTE；玩家明确记录后保存片段索引和记录日，随实验室/继任保留。读取不自动写入、不看Meta、不授予故事flag或生成结局。jasmineRecords仅回看当前档实际听过的red_thread/project_mia/daily_remote原行；完成记录缺台词仍不重建，继任不给新个体补旧对白。未修改任何scene、批准原文、route/ending/hidden flag。

本地lab-private-effects单元通过真实数量守恒/24容量/0AP/库存上限/错误动作与数量原子拒绝/房间与模式门槛/已知片段纯读取和明确保存/旧档缺字段/合法超容量不删物/实际Engine自由告别继任与精确重载。Chrome1366/768/390原生房间入口→盒存牌→盒与相册各存一张实际照片→取回→已知回忆记录→中英展开保持→刷新→真实告别/新个体→取回原存物数量通过；每尺寸再实际存六种物件，至少3张完整卡可见，手机截图已查看。原喂食/睡眠/返回三尺寸、版本日志中英三尺寸、实际继任世界资产、Claude保护、培养舱回归通过。439源码资源200及私密路径保护通过，英文包14163，内联主页44392851字节。公开验证随后补记。

### 原02条款当前验收边界
| 条款 | 现状与证据 |
|---|---|
| Sleep | 原结束今日/取消/落盘，room-care三尺寸回归通过 |
| Change clothes | Jack自己的服装仍欠；B07换装不计作Jack换衣 |
| Personal storage | 本批真实私人盒/相册与库存守恒，含新旧档与继任 |
| Journal | 原Jack日记入口保留；本批不改日记文本 |
| Jasmine memory box | 四个已知片段、明确记录后保留，原已听文字只读 |
| Photo album | 实际已拥有的两种照片独立收纳，可取回；不补未知人物图片 |
| Private objects | 实际拥有的牌/播放器/笔纸等可私人收纳，不复制库存 |
| 原列五类专属事件 | 尚不能全算完成；当前quarters事件是cot_leg/locker_hinge/damp_blanket/ops_bunk_latch，不足以证明原失眠/敲门/占床/病休/Jasmine五项 |
| 独特视觉 | 原cot/thread/photo/locker与living不同；本批增加独立盒与相册绘制，不宣称正式房间美术全完 |

继续Jack服装/五类原事件和剩余27房间条款、审定梦/Host/深层秘密、历史统一终验、正式美术/人物长剧情及公网AI审批。整体历史目标仍未完成，不能以本批收纳替代整间房的全部要求。


### 0.13.166 公开验收回执（2026-10-16）

提交c2b6bc8b61cf799ffbc19ae7e159b1d5e1270771；Pages38967602314 completed/success。最终公网lab-private-effects-browser/room-care-browser/release-log-browser/public-release-integrity四脚本顺序完成退出0。1366/768/390每尺寸均原生进入Jack房间、真实库存分别存盒和相册、取回数量、0AP、只记录已知片段、中英展开保持、精确重载、自由告别→输入新名→新个体→仍可取回原物数量通过；每尺寸实际另存六类物件，保持至少三张完整卡同屏，390截图实见四张完整卡。原喂食/睡眠/房间返回、日志中英0.13.166对齐通过；主页及五外置CG与安全发布目录逐字节一致。verification/*-public-166.log留证，private-effects三张尺寸图随包交付。

本地单元与旧档缺字段、原子拒绝、实际继任、已知回忆纯读取及明确记录、Claude保护、原培养舱及439源码资源/私密路径保护通过；英文包14163。提供../abyss-lab-0.13.166-preview.zip，不含真实.env、密钥、玩家进度或依赖，没有付费AI测试。

原02条款的衣服与专属五类事件仍欠；现有四条quarters维修类事件不冒充原五项。全历史目标保持未完成，下一批继续原条款而不以私人盒替代整间房。


## 0.13.167 · Jack自己的换衣（2026-10-16，本地验收）

对照原27房间02的CHANGE CLOTHES，新增js/lab/jackWardrobe.js与jackWardrobeUI.js。quarters提供Jack换衣，与B07的wardrobe入口/装扮实体完全独立。六套基本衣服直接可选，不做房间等级或稀有度额外解锁：旧工作外套、卷袖工作衬衫、检修连体服、防雨工作披衣、保暖厚外套、帆布维修围裙。六个cut分别有外套口袋/卷袖露前臂/连体服腿部结构/披衣轮廓与反光带/长厚外套及绗缝/交叉围裙带，几何去色后仍六种，不是换调色板冒充。

roomSystems.rooms.quarters.wardrobe为可加v1，只存outfit与changedDay。旧档缺字段为work/日期未知0；未知ID回基础衣服，未来或非法日期回0。换衣0AP/0资金，不改变库存、能力、体温、病程、关系或故事flag。需进入Jack房间并满足原实验室/事件门槛；同衣服、未知ID、剧情模式、出行/狩猎/梦或封房均原子拒绝。已选衣服随实验室和真实继任保留，不把B07旧装扮重新穿到新个体上。

实际展示：LabRoomArt依据LabRooms.characters的实际Jack驻留绘制选中衣服，只在Jack真实在场、房间开放且养成模式显示；密闭/失去的房间不画人，避免凭空复制。脚下阴影落到房间地面，左侧前景避开床柜；未登记房间沿用其原画后附加同一已在场人物。人物档案也读取同一选择。帽子和后脑遮住脸，无眼鼻口、无清晰正脸；不改审定CG或剧情演出。代码人物不等同于正式手绘CG完成。

测试：lab-jack-wardrobe单元通过六种去色后不同剪裁、真实房间render、预览纯读取、指令只改衣服元数据、无AP/钱/属性/库存/flag变化、所有拒绝原子性、旧档默认/非法数据、安全存读和实际Engine告别/继任保留。Chrome1366/768/390原生六套依次换上、当前禁用/预览同步、房间里真实冬装、人物档案展示、属性/零号装扮/库存不变、中英切换、按钮命中和SVG边界、精确刷新、原生告别→输入新名→新个体→仍可继续换围裙通过。六套对照图及手机房间图已查看，七张截图随包。原私人盒/相册/回忆索引与三尺寸实际继任、原喂食/睡眠/返回、真实世界资产继任、Claude保护及版本日志回归通过。英文包14169，内联主页44404126字节；公开回执随后补记。

### 原02条款最新范围
- Jack CHANGE CLOTHES现有实际可用的六套基本衣服、保存、继任与房间展示；不是以B07换装充数。
- 原五类事件（失眠/敲门/占床/病休/Jasmine回忆触发）仍不能全算完成；当前四个房间维修事件仍不是它们的替代。本批只审计到Jack病例有实际sleep/health/conditions，宠物实际位置与B07通行/驻留可供后续条件使用，没有为凑事件伪造病情/移动/成熟对白。
- 原睡眠、日记、私人盒、照片相册与已知Jasmine索引保持既有验收边界；27房间其余条款、梦/Host/秘密与历史统一终验、正式美术/长人物剧情仍欠。

### 公开AI外部状态更新
本轮Supabase list_projects返回projects为空；此前不可用的get_cost现在恢复，此前选定组织的project查询返回monthly/amount0。已按工具“先复述费用并确认”的明确要求向用户发出每月0美元创建abyss-lab-ai-access的确认，尚未收到答复；没有调用确认费用或创建项目。组织选择无需重问；等待不影响本地推进。未读取真实.env/密钥或玩家进度，无付费AI请求。整体目标保持未完成。


### 0.13.167 公开验收回执（2026-10-16）

提交c64e442e350fa9bf4e8172d5db2cfd15c768de74；Pages38977756651 completed/success。最终公网lab-jack-wardrobe-browser三尺寸全部通过：六套原生点击、实际房间与人物档案选衣同步、无零号/属性/库存/货币影响、中英、按钮命中/人物边界、精确刷新、原生自由告别/新个体与继续换衣。其后lab-private-effects-browser、room-care-browser、release-log-browser三尺寸及public-release-integrity全部通过，终端退出0；主页与五外置CG与安全公开目录逐字节一致。verification/*-public-167.log留证，七张Jack衣服/房间截图随包。

新增单元同时覆盖27间实际房间render的单个Jack投影、纯读取与当前衣服引用；这是绘制层检查，不冒充27房间全部专属玩法终验。旧档缺字段、原子拒绝、实际世界资产继任、私人盒/相册、Claude保护、441源码资源/私密路径保护、本地原生三尺寸回归通过。英文包14169；内联主页44404126字节，公开主页26824934字节。

#### 加载超时的真实边界
曾分别出现30秒与120秒的page.reload等待DOMContentLoaded超时，进程均已明确失败退出，没有当作通过。相关回归把刷新导航上限与原首次打开的120秒统一，业务/存档断言不变；没有继续无限提高时限。用同一份公开产物本地file读取全三尺寸未复现；直接公网curl返回HTTP200，压缩传输17732426字节、3.216秒；磁盘空闲107.9GB、空闲内存10.07GB。加入可选网络/文档就绪日志后，最终公网私人收纳三尺寸精确刷新均通过：有阶段仍ready=loading而game=true，主文档结束后才DOMContentLoaded。超时根因仍未完全确认；不把统一时限当网页故障修复，首页体积与加载稳定性继续列为性能缺项，后续需量测与减重。相关诊断verification/private-effects-navigation-diagnostic-167.log与private-effects-public-artifact-local-167.log；后者是本地对照，不冒充公网结果。

交付../abyss-lab-0.13.167-preview.zip，排除真实.env/密钥/玩家进度/依赖，没有付费AI测试。原五类Jack房间事件仍欠；冬装物资与季节经济沿用原系统，本批只完成基本外观换衣，不据此宣布冬季生存准备条款已完成。其余房间、梦/Host/秘密/历史统一终验、正式美术/长人物剧情仍需继续。公开AI数据库项目仍为空，0美元/月报价确认待用户答复；未调用创建。整体目标保持未完成。


## 0.13.168 · 玻璃物件修复与剧情加载减重（2026-10-16，本地通过，待公开）

- 本轮用户再次报告55件模型问题。逐项复核实体模型后，修正未落沙漏、反向沙漏、只装旧雨的瓶：玻璃仍为实体壳，但使用透明材质显示沙与雨。未落沙粒留在上半部，反向沙漏保留下部沙堆与上行沙线。无声铃/深井铃补内壁和铃舌。不是再次把旧造型测试当作用户视觉问题已全部解决；未指定的其他不满意造型仍可继续纠正。
- 55件图鉴和房间模型、32放大旋转视图及新增5件玻璃/铃铛截图已实际检查，220旋转边界及真实房间同模型检查通过。实体ID、库存、摆放、碰撞尺寸和存档结构未改。专项物理模型及无编号房间守恒/迁移单元回归通过。
- 同时完成前批已实施的11张CG按需加载：公开首页6,058,792字节，原26,824,934字节，约减77.4%；本地单文件仍内嵌全部原图。11张PNG原像素不变。慢加载保留前图，实际解码显示后解锁，失败工具栏原生重试；旧请求、退出及后台完成不会误解锁或覆盖新图。图库缩略图使用浏览器延迟加载。
- 新加载实际浏览器1366/768/390三尺寸全部11图、延迟、404、原生重试、收藏、快存/读取/刷新/回退、firstWord及养成清图通过；原9组CG旧回归已分组通过。Claude原文/保护场景哈希/选择/72小时计时/旧档测试通过。首次本机HTTP测试被网络沙箱拒绝，获准本机隔离测试后完整重跑成功；没有访问真实浏览器存档。
- 整体历史目标仍未完成；私人五事件、其他房间完整专属玩法及正式美术/长剧情等保持欠项。公网AI数据库尚未创建，费用查询已恢复并返回每月0美元，仍等待工具要求的明确费用确认。无付费AI调用。


### 0.13.168 公开回执（2026-10-16）

运行提交：6bb8f63f89a02ba92277667e0ce6650cb63337ef；Pages 38986524657 completed/success。公网顺序回归 anomalous-art-browser → lab-unlisted-browser → story-cg-loading-browser → release-log-browser → public-release-integrity 整个命令 exit 0。55件图鉴/房间和32放大旋转无裁切/无页面错误；无编号房间三尺寸真实库存/实体转交/双语/刷新/归还全部通过。11张CG三尺寸慢图、全部解码、收藏、快存/读档/回退、firstWord及养成清图通过；三尺寸跳过旧请求与404原生重试通过。中英菜单/日志版本0.13.168一致，零存档变更/横溢出/页面错误。公网index和11PNG均HTTP200，SHA256逐字节与本地安全输出相同。

公开首页解压后6,058,792字节，实际传输2,013,023字节；本次三次浏览器DOMContentLoaded约4.4/7.9/4.7秒，仅为本轮网络测量，不承诺所有设备或网络速度。原11张图片与剧情文本保留。修复截图见verification/anomalous-glass-168.png，加载测量与原图哈希见verification/story-cg-loading-metrics.json、verification/public-release-integrity.json。

这不是全部正式美术通过：本轮明确修复3件玻璃内含物遮挡和2件铃铛缺构造，其余模型的用户视觉反馈仍应继续处理。整个历史目标仍active，五个私人事件等欠项没有冒充完成。


## 0.13.169 · Jack房间五个私人事件（2026-10-16，本地逻辑通过，浏览器验收中）

原规格：27-ROOM FUNCTIONALIZATION，02 quarters，Jack失眠 / B-07敲门 / 宠物占床 / 生病休息 / Jasmine回忆。新增js/lab/quartersLife.js及quartersLifeUI.js，接入房间状态/事务/实际角色位置与图像/界面。不是把原维修事件改名充数，不改Claude剧情或故事日常scene。

- 真实条件：白天或夜间的现有病况/健康不足触发生病休息；夜间睡眠低于35、压力至少65或实际工作疲劳至少80触发失眠。宠物限当前可自由到达、未逃离/未隔离、未独立安置的猫/鼠/犬；B-07须仍在实验室、通道已开放、实际房间可通行、未被工作/日常路线/疾病/灰潮拦住。Jasmine只读取已有四种记忆flag或私人盒内已记索引，原文仅使用当前档实际听过的记录，不重建缺失台词。
- 每日最多触发1个；生病/失眠可次日再次出现，其余各至少间隔4天，以最久未见的合格类型优先，不消耗世界随机数。10个选择保留独处与不处理的选项；收费休息各1AP：生病睡眠+8/压力-3/既有工作疲劳-4，失眠睡眠+6/压力-4/既有工作疲劳-6。不改健康、疾病、照护疗程、物资/货币、剧情flags、Host seeds或结局条件。
- 来访是实际位置，不是只有卡片描述；B-07到房门会调用既有内侧释放观察，电机关闭时实际记录机械开门。谢绝会退回可用房间，不惩罚关系；宠物可留在床角或腾出位置，床上显示原物种造型。访问在跨日/时段变化/失去安全条件时结束，未处理片刻记为过去/中断，无惩罚。
- 私人记录最多60条；旧档缺life字段为空，不连续补播。记录与私人物件随实验室继任保留；旧个体的待处理对话不移给新个体。日期/ID/类型/选择/访客校验，缺失每日守卫由真实历史修复。渲染纯读取，只有事务写状态。
- 修复主页房间图片缓存漏掉实际住户、夜间状态和Jack衣服的问题。房间主体仍使用现有美术；不把该接入算作所有房间正式美术完成。
- 核心五事件及10选择、纯预览/失败原子性/旧档/篡改数据/真实派发存读/继任/真实手动开门专项通过；私人收纳、六种衣服、内侧释放、个人日常、保护剧情/哈希等6文件回归通过。三尺寸原生点击和实际屏幕仍在验收，未经通过不记公开完成。
- 剩余：其余27房间原始条款、人物长剧情、正式美术与历史大扩展统一终验继续欠；AI数据库仍等待明确费用确认，未创建/未调用付费AI。整体目标active。


### 0.13.169 本地最终验收

最终构建首页6,076,546字节；443个源码CSS/JS与11张CG的localhost HTTP检查通过，私密路径返回404，实验室源码浏览器零缺资源/脚本异常。最终五事件专项（全部10选择、真实工作疲劳、角色实际缺席/隔离、封闭返回房间、历史修复守卫、未处理旧个体敲门的真实告别/继任）通过；其余5文件相关单元通过。三宽度1366/768/390最终原生5事件均完成：房间按钮实际进入、真实床上住户、谢绝返回、en/zh、准确AP、不改物资/健康/flags、已知回忆查阅、展开历史、刷新与当天不重复、主页当前衣服刷新，零pageerror/横溢出。旧换衣/私人收纳/房间照料/日志四组各三宽度回归也通过。

本地调试修复了嵌入回忆卡片切换语言的空容器错误，修正测试标题选择器避免把嵌套标题当重复场景。滚动和展开状态保留。此记录证明本地候选已通过；公开回执随后单独记录，不能将它等同于完整历史需求完成。


### 0.13.169 潜伏期边界修复

首次公开候选五事件/照料/日志/资源完整性三尺寸已通过后，额外检查真实HUMAN潜伏病例：原条件会因INCUBATING记录触发生病休息，单元测试已复现失败。现在排除潜伏期与已康复记录；现有实际低健康/公开不适仍可触发，病程与诊断不改。新增每个宽度的原生无提前事件检查，最终公开回执以修复提交为准。

潜伏期修正版本地三尺寸已通过：每个宽度先验证1个真实HUMAN潜伏病例无事件且病程保留，再完成5种事件的原生流程，合计18个场景。隔离场景复用同一个测试槽；五槽上限保持原样。


### 0.13.169 最终公开回执（2026-10-16）

最终运行提交 d6786abbb9d4d5c77777831277ffd0d4d0d493ef；Pages 38990805361 completed/success；网址 https://stepono927.github.io/Stephen/?release=0.13.169-r2 。最终公网 lab-quarters-life-browser → public-release-integrity 整体exit 0：1366/768/390每个宽度1个潜伏期无提前事件案例+5个完整私人事件，合计18场景；主页真实床位/当前雨衣刷新、中英、AP/库存/健康/flags、已知回忆界面、历史、刷新不重演全部通过，零pageerror/横溢出。index及11原PNG逐字节与安全本地输出一致。

初版提交f185e72aa5dcf1f5e7ec680d60b5dce91699e4a9的公网照料/日志各三宽度已通过；随后精确比较确认运行源码只改潜伏期资格这一处条件，其余代码不变，并以新增潜伏病例与原五事件完成上述最终复测。既有换衣/收纳/内侧释放/个人日常/受保护剧情等单元回归和源码HTTP443路径已通过。

原五个私人事件条款现在可标已公开验收。未把它等同于Jack房间全部美术、全部27房间专属玩法或完整历史目标完成。正式美术、全局残留英文（例如HABITAT/ROOM ACTIONS标签）、人物长剧情、其他原始扩展的统一验收及公开AI审批继续按原范围推进；费用确认未收到，未调用付费AI，配音按用户后续安排。


## 0.13.170 · 物品模型纠错与房间汉化（2026-10-18，本地验证，待公开）

再次核对55件既有物品后，修正4件可确认的构造问题：绿瞳银骷髅改为颧骨、鼻腔、开口下颌与16颗银牙；无记录终端增加44键与空格、通风槽和旋钮；第十三只手套改圆掌、五指与空袖口，去掉木块底座；纸窗恢复完整纸面与透光纹理，不再误用蓝玻璃。原55个ID、位置尺寸、库存与保存字段均不改，图鉴/卧室/收存继续使用同一模型。55件几何/220旋转和真实浏览器图鉴与卧室、32放大方向无裁切检查通过；已查看新全图。本批4件具体纠错不等于55件正式美术全量验收。

并完成此前在做的27房间与运营标签局部汉化：新增独立displayLabels显示映射，六个专精保留canonical option value，费用与AP不变；12日报分类、6成色、楼层/等级/房间SVG/地名/日期可切换，历史查询同时匹配中英文地名，切语言保留草稿、筛选与展开记录；玩家维护文字标记data-user-text，保留原文。真实浏览器1366/768/390均完成27房间zh/en/zh、六个真实付费专精与刷新、十二分类/六成色、双语历史筛选、草稿与原文/主页标签且无状态变化、页面错误和溢出。

专项模型、显示、维护日志、商路、房间记录及Claude保护文本测试通过；源码HTTP检查444资源和私密路径拦截通过（默认网络沙箱EACCES后在独立localhost重试通过）。原始大型扩展、剩余正式美术、全游戏漏译与公网AI审批仍未全部验收；本批不读取真实.env/密钥或玩家进度，不调用付费AI。


### 0.13.170 公开验收回执（2026-10-18）

运行提交586f1a8ac4e1959946d3793ab635dbb8822c2c2c，Pages39098732699 completed/success。公网 https://stepono927.github.io/Stephen/?release=0.13.170 顺序执行 anomalous-art-browser → lab-unlisted-browser → lab-display-labels-browser → release-log-browser → public-release-integrity，整个命令exit 0。55件图鉴/房间模型、32放大方向和4件修复截图通过；1366/768/390真实收存/取回/摆放、数量守恒、中英和读档通过；27房间三语言切换、六个实际付费专精/刷新、十二日报、六成色、双语历史搜索及草稿/维护原文保留通过，零pageerror/横向溢出。公网index及11张原CG均HTTP200，SHA256逐字节与安全本地输出一致。此批只修4件明确构造，不把55件几何测试等同55件美术已获用户认可。


## 0.13.171 · 原03私人空间：B-07实际自主摆放（2026-10-18，本地候选）

原条款“允许B-07自己改变摆放；高Autonomy时某些物品位置由B-07决定”此前没有实际布局变化。本批新增js/lab/livingArrangement.js，接入真实日结、房间状态与房内显示。自由通行、本人实际在living、独立性至少60或既有autonomy理念至少6、房间开放且损坏低于60、无离开/隔离/重病/灰潮/待解决事件/梦境/狩猎时，安静跨日可移动一件已摆放的小物；至少间隔4天。不会移动床/椅/屏幕/镜/画/灯、支撑别的物件的家具、未拥有或未摆放的物品。

目标位置通过原Bedroom.validate：原实体UID、数量、旋转与支撑不改；边界、门口、家具碰撞及桌面完整支撑沿用原规则。桌面中心按物品真实旋转底面计算，实际可移动距离最少0.2；地面至少0.5。没有合法位置就没有虚假记录；不耗世界RNG，不创建物品，不扣AP/钱，不增加关系/剧情flags。实际卧室renderer使用修改后的相同XYZ坐标。

新增living.arrangement可选v1字段：最多60条原个体姓名/代数/出生日起点/原新坐标，当前偏好须与真实记录及实际在场物件一致。旧档默认未观察，不补过去动作；同日换代也清除偏好与个人冷却，实体和原个体记录保留。未使用的新字段保持fresh，避免继任资产无故变更。房内双语列表与展开记录保留；不写B-07新对白、不改保护文本。

专项已通过：真实位置/原数量、4天门槛、安全门禁、完全阻塞不伪造、真实桌面支撑、旧/坏存档迁移、独立新代和实际告别继任；原季度私人事件、个人日常、继任资产、显示与Claude保护相关回归通过。源码HTTP445资源与私密路径保护通过。浏览器最终三尺寸流程正在验收，后续以公开回执为准。原03的独立私人收藏、礼物/藏物等其他条款和全部历史目标仍未完整验收。


### 0.13.171 公开验收回执（2026-10-18）

运行提交151948b8e21fce1992d0e6c50358247bb03e0e1a；Pages39099840995 completed/success；网址 https://stepono927.github.io/Stephen/?release=0.13.171 。公网顺序lab-living-arrangement-browser → lab-quarters-life-browser → release-log-browser → public-release-integrity整个命令exit 0。自主摆放三个尺寸均实际点击结束今日，物件从(4,4)移到(1.5,3.5)，UID/拥有数/摆放总数守恒，原碰撞规则通过；实际卧室SVG使用新坐标，双语/展开历史/刷新精确保留。原五类私人事件加潜伏期无提前触发共18场景、中英版本日志与零存档变更/页面错误/横溢出通过。公开index与11原CG均HTTP200且SHA256与安全输出逐字节相同。

新增专项还验证真实桌面支撑移动、完全阻塞无假记录、60条记录上限、同日不同代两条记录均保留、旧/坏存档与实际告别继任，不继承旧偏好但保留实体与历史。已查看手机新增面板截图。此批完成原03的实际自主摆放，不把它等同原03完整私人收藏/所有正式美术/历史原范围全部完成；整体目标继续active。


## 0.13.172 · 原03私人收藏与九类物件模型（2026-10-18，本地通过，待公开）

新增LabLivingCollection及独立UI，living房内提供私人收藏入口。九种已有库存物件：扑克牌、缺角棋盘、骨白骰子、完整音乐播放器、旧漫画、手绘扑克牌、木象棋、骨骰子、石制睡猫。递出一件由在场个体决定是否接受；接受从实际库存扣1进12格架子，拒绝不扣库存，且同日同物不反复催问。不给AP/钱/关系分数，也不修改剧情flags；不是宠物好感兑换。

当前个体的藏品需请求归还；压力/恐惧至少60或怨恨至少45时可不归还，每件每天一问。本人必须实际在自己的空间、自由通行且无隔离/已显现重症；Jack须实际在场，房间开放且损坏低于60，无当前事件/梦/狩猎/外出。旧个体藏品保留原姓名、日期、出生日起点与代数，取回同一物品恢复库存；新个体不继承旧偏好。临床潜伏期不用于提前阻断或泄漏病况。

新增可选living.collection v1：12实体条目、递增ID、自动从原个性/能力选择的手边物、80交接记录。旧档为空，无补发库存或历史；坏档非法/重复ID、未来日期、不支持物件过滤。有效实体不因前一非法重复编号被丢弃。实际告别/继任与存读通过，公共库存/藏品总数守恒。NPC赠礼没有可靠既有交接来源，本批不编造来源，藏水果/植物及礼物仍待接入。

九种模型由collectionArt与ItemModel共用：实体库存和藏架同造型，手绘牌与标准牌、单骰与双骨骰、8×8棋盘与象棋分别表现；播放器有耳机/磁带窗，漫画有分镜，石猫有蜷曲姿态。卡片模型72px高、小圆角网格，不再用统一方箱。代码SVG不是全量正式手绘美术完成。

验证：九种真实交接/拒绝/归还/每日防重复、费用/AP/RNG/flags/stat不变、容量与失败原子性、旧坏档迁移、实际Engine及告别继任通过；自主摆放、私人事件、既有私人收纳、显示、人物/电脑模型与Claude保护回归通过。源码HTTP448资源/私密路径保护通过。1366/768/390浏览器实际递出9件、九模型边界与完整显示、归还/拒绝、双语/展开记录/选项保留、刷新精确保留、无页面错误/横向溢出通过。桌面模型截图已查看。公开回执随后补记，原03与全部历史目标仍未整体完成。


### 0.13.172 公开验收回执（2026-10-18）

运行提交6b0a3f9637ab3ec2cd31c704f90ef0b2241ec790；Pages39101211624 completed/success。公网 https://stepono927.github.io/Stephen/?release=0.13.172 顺序执行 lab-living-collection-browser → lab-living-arrangement-browser → release-log-browser → public-release-integrity 整体exit 0。1366/768/390均原生递出九件（共27次接受）、九模型在边界内、准确归还/拒绝/同日限制/库存与架子数量守恒；AP/钱/RNG/flags/stats不变，中英切换保留选项与展开记录，刷新精确保留。原实际日结自主摆放三尺寸、新版本日志三尺寸通过，零pageerror/横溢出；index和11张原CG均HTTP200且SHA256与安全本地包逐字节相同。桌面与手机藏架截图已查看，手机双列显示。

新增坏档回归确认前一条非法重复ID不能吞掉后一条有效实体。原03的私人收藏基础交接、实际持有与自动手边偏好取得代码和公网证据；不把它冒充NPC赠礼来源、藏水果/活植物等全部原条款完成，也不把程序SVG当作所有正式手绘完成。整体历史目标保持active。


## 0.13.173 · 原03藏果、实际自取与27种生果图示（2026-10-18，本地通过，待公开）

新增js/lab/livingFruit.js：自由通行、实际在自己的空间、健康可行动且自主性足够的当前个体，安静跨日可从可进入的温室收获盘收存一份真实安全生果。支持现有27种FOOD水果，不偷新闻任务批次、加工品、污染>25或已腐坏的食物；优先低价格/较充足原批次，最多三份，至少隔四天；不消耗世界随机数、不生成食物/资金/关系奖励。

每份保留原plantId、收获日、品质、污染、原有botanicalTraits。保质期直接读取原PlantProcessing/PlantBreeding规则（含LONG_STORAGE），不是从藏匿/发现/继任时重新计时。Jack实际在房间才能发现；纯打开面板不透露未看见的藏果，也不代写观察，未观察的隐藏/进食不出现在玩家记录。已发现的当前个体藏果需请求归还，可拒绝且每份每天一问；旧个体食物可取回，保持原年龄。收获库400批次及每批数量上限、同批精确合并沿用；库满或温室封闭时不改食物或消耗请求。坏果可清理为原系统一份堆肥，不可重置日期变回可卖/可喂食的鲜果。

饥饿>=45时可自取当前个体实际安全藏果，每天至多一个藏/吃动作。营养与SWEET/AROMATIC心情收益沿用原生果喂食，额外调用原ClinicalEffects.afterAction；27个适用B07食欲病症逐个与Garden.feed对照等价，不绕过临床食欲修正，不给喂食/对白/剧情flag奖励，不自动治疗。隔离/已显现重症/外出/灰潮/待解事件/梦/狩猎等状态不触发；不借潜伏期提前泄漏病况。

新增可选living.fruit v1，三份实体、60记录、当前代独立冷却/递增ID。旧档为空，不补历史；坏/重复/未来数据过滤。真实告别继任和保存后，原食物及原姓名记录保留，新个体不自动继承食物归属或进食习惯；原私人收藏/自主摆放/主线保护文本不删。

另新增FruitBatchArt：现有27种可食生果分别使用对应的果形、籽、切面、果蒂等程序SVG及腐坏霉斑；收获库和藏处共用，不再用盆栽示意替代水果。西瓜、猕猴桃、石榴等切面、两类葡萄/莓及虚构生果各有对应构造，保持旧ID/价格/数值；加工品及非生果原入口不改。不是全量正式手绘美术验收。

专项：真实批次守恒/原性状和日期、不可远程发现、四天与三份上限/同日幂等、真实自取/坏果堆肥及不可重售、请求拒绝/满库/封闭原子性、全部27可食果覆盖、旧坏档/真实继任/保存通过；原收藏、自主摆放、继任资产、Claude保护相关回归通过。源码HTTP450资源/私密路径保护通过。真实收获库27模型及54新鲜/腐坏渲染边界/双语无状态变更通过，三尺寸实际藏/发现/归还/自取/腐坏/清理/刷新通过；最终公网回执随后记录。私人活植物/异常物归属/真实NPC礼物、其他历史原条款及正式美术仍未整体完成。

### 0.13.174 后补公网回执
最终运行1b60584d3cf72c5a585e65a267be538ef2d44e07，Pages39105512831成功；公网模型55/房间55/32旋转、无编号房间三宽度真实转入取回/读档、三宽度日志及index与11张原CG逐字节一致，顺序链exit 0。此批仍漏了实际目录的外层家具画框；0.13.175补足真实目录验收，不能用174模型总览替代。

### 0.13.175 最终公开验收（2026-10-18）
运行提交2e0dacb088a34afb8b98f9c36fb355a0f926629d；Pages39107282165 completed/success；https://stepono927.github.io/Stephen/?release=0.13.175 。公网顺序anomalous-catalogue-browser → lab-unlisted-browser → release-log-browser → public-release-integrity整个命令exit 0。1366/768/390真实目录四页55件匹配、取景占幅至少77%、中英至少四完整卡片、原文说明及同模型大图、普通家具画框保留、分类/页面不改存档，无裁切/横溢出/pageerror；三尺寸实际转入取回/读档和日志通过；index及11原CG HTTP200且SHA256逐字节与安全输出相同。
旧公开174原生目录明确复现object_radio占幅0.368421失败，非仅新增属性检查。新手机实际截图已查看。55件共用[0.7,0.5]/0.8元数据另存anomalous-scale-audit-175.json为真实欠项，未放大旧档造成碰撞；全部独立造型/物理尺度/正式美术仍需继续。私人活植物、异常物归属、NPC礼物实际来源及其他历史扩展/公开AI依旧按原范围推进，整体目标active。

## 0.13.176 · 整批55件异常陈设尺寸与结构整改（2026-10-18，本地候选）
用户确认指整批55件，按完整运行时目录逐项处理。新增anomalousObjectScale：55个显式ID分别设置占地、高度、包围盒；模型XYZ与碰撞尺寸共用定义，目录独立取景，不依赖稀有度或序号套同形状。全55件新增各自结构件；硬币去底座改薄片，心脏改心尖/心室/主动脉，手套弯指与扁袖口，照片转向侧脸、电话断线、凸透镜、闭眼木偶、打字机空格/色带/滚轴等按既有物件说明核对。不改55个ID、价格、稀有度、物件故事或其他剧情。
Bedroom可选objectScaleVersion=2。旧档先用旧尺寸校验完整布局，再把能合法原地适配的物品迁至新尺寸；贴墙/碰撞项保留objectScaleVersion=1和原位置/UID/库存。重复读取幂等，不删除合法旧布局。已摆物件可用下拉列表选取，显示占地/高度；旧物可预览适配附近0.1网格合法位置，继续沿用门口/边界/碰撞规则。预览不写档，不丢其他未保存编辑；确认后才写入，取消可恢复。满房间失败保持原数据，不消耗AP/钱/RNG，也不移动其他物品。新摆放不能伪造旧尺寸。
专项已证明55组实际XYZ跨度等于定义、55几何形状不靠ID/颜色区分、220旋转、旧墙边床/全部库存/幂等与满房间拒绝、真实继任资产保留。1366/768/390实际旧档原生选择→适配预览→取消→保留另一个未保存移动→确认→微小硬币选择→双语→精确刷新流程通过；新版全量目录和公开终验随后补记。程序实体模型仍不等同全部正式手绘美术/所有历史目标完成。
另更正175审计附件：原文件仅直接加载基础数据而记了30项，漏25地下物件；本批按完整运行时重建55项历史尺寸审计，原175已发布ZIP保持不变，不将少项报告作为55项证明。

### 0.13.176 发布前本地验收
已核对完整55项结构部件清单，每项确有对应实体面，且55组几何签名忽略ID/颜色后仍不同。55件真实XYZ尺寸一致、220旋转、透明内含物/铜银币薄片/心脏心尖/扁袖口等专项通过；330个全55件旧中心四方向/两侧边界迁移案例，以及满房间保留、只调整目标、伪造旧尺寸拒绝、幂等通过。真实继任资产、私人收纳、自主摆放、无编号房间、住户风险/20000抽样、Claude审定文本与保护哈希均有通过证据。本轮未执行完整285+模块全套，不冒充全套通过。
本地顺序anomalous-scale-browser → anomalous-art-browser → anomalous-catalogue-browser → lab-unlisted-browser → release-log-browser整个命令exit 0：1366/768/390旧墙边床、预览不写档、取消、其他未保存移动不丢、确认后实际XYZ渲染、小硬币列表选择、双语/精确刷新；55目录/55共同房间尺度/32放大旋转、实际四页目录165件逐页检查、中英至少四完整卡片、收存取回库存守恒与三尺寸新版本日志均通过，无裁切/pageerror/横溢出。源码HTTP451资源通过，私密路径仍404，未使用真实存档或付费AI。

发布前补充：旧固定0.02碰撞容差会放过新尺寸硬币重叠，现仅对新尺寸异常物按小物占地比例收紧容差，上限仍0.02；旧兼容物件和普通家具规则保持。新增新硬币重叠拒绝、仅边缘相接允许、旧相接布局兼容检查通过。


## 0.13.176 最终公开回执（2026-10-18）

- 范围：整批55件异常陈设；新增独立实体结构、逐件宽深高和实际碰撞尺寸，床/椅子/电脑/硬币不再同尺寸。旧摆放保留UID、位置、所有权和数量；冲突的旧模型先保留旧尺寸，可在卧室建造终端选中后“适配实际尺寸”预览，确认并保存后生效。
- 实证：55件尺寸与XYZ模型一致、220旋转、330旧布局案例、拥挤房间原子拒绝、微小硬币碰撞通过。1366/768/390真实原生浏览器适配预览/取消/保留其他未保存编辑/确认/重载全部通过；AP、货币、RNG和真实库存数量保持正确。
- 公开验证：55图鉴+55房间模型、32放大旋转；三屏中英文图鉴四页、无编号房间存取/继任/重载、更新日志均通过。首次手机网页下载120秒超时，重跑整组三屏后通过；未隐去该网络记录。
- GitHub运行提交：e32811c7b510d3190275eafc727871a7b998dd6e；Pages 39110201211 completed/success。公开index与全部11张CG逐字节SHA256一致；运行index Git blob为92c4c3b21d150ce100f42ff231e83941b01a2059。公开入口：https://stepono927.github.io/Stephen/?release=0.13.176 。
- 安全：仅隔离合成测试存档；没有读取/上传真实.env、密钥、玩家存档或付费AI调用。全部自动检查结果见verification/anomalous-176-results.json；完整仓库测试未在本批全跑，不把相关检查冒充全项目终验。
- 更正：旧175尺寸审计文件只纳入30件基础定义、漏25件地下定义；本批修正为完整55件，并保留更正说明。旧175已交付ZIP未被改写。
- 剩余：历史大型扩展统一验收、其余正式美术、私人植物/异常物品真实所有权与NPC赠物等范围仍在原目标中；本批通过不等于用户已认可全部造型或整体目标完成。


## 0.13.177 · 原03私人异常小物实体归属（2026-10-18，本地候选）

对照27房间原附件03的“异常小物/私人收藏”，新增LabLivingAnomalies。按176实际体积筛选44种现有小物，床/椅/电脑等大件不进入此架；沿用原ID、故事、模型、数值及原获取渠道，不凭空补发或编造NPC赠物。仅可递出陈设库存中未摆放的一份实体；在场个体决定是否接过，收下扣原库存并进入六格私人架，不能同时摆放或进入无编号房间。实体总数统计包含库存、无编号收存及私人架。

归还须当前持有人在场、可以拒绝、每件每天一问。满99件陈设库存时不动实体、不消耗询问；返回只回原库存，不自动摆放。旧个体的姓名/出生日期/代数随原物保留，新代不继承旧归属；取回旧藏物仍需实际进入房间。0AP、0钱、无关系/属性奖励、无世界随机数及剧情flags变化。

新增可选living.anomalies v1，旧档缺字段为空；六件实体、递增ID、60条实际交接记录，非法/重复/未来数据过滤；拒绝记录序号不复用。界面从自己的空间→私人收藏进入；异常区靠前，可折叠、中英切换保留展开与选择，使用现有同一实体模型。

专项44件逐一实际扣除/归还与同模型、已摆副本不能复制、拒绝/每日防重复/满架/满库原子性、旧坏档、实际Engine存读与告别继任通过。原九种收藏、藏果、旧布局、世界继任、无编号收存、Claude保护文本回归通过。源码HTTP452资源及私密路径404通过，API密钥显式为空；完整仓库全套未执行，不以这些专项冒充全部历史终验。三屏最终公开回执随后记录。

剩余保留：私人活植物、真实NPC赠物来源、正式美术、历史大型扩展逐条统一验收及公开AI后端；原目标未完成。


### 0.13.177 最终公开验收（2026-10-18）

运行提交0e6818833847cf00f68d8d941e212a16c9265103；Pages39112192775 completed/success；公开入口 https://stepono927.github.io/Stephen/?release=0.13.177 。公网顺序lab-living-anomalies-browser → lab-living-collection-browser → lab-living-fruit-browser → lab-unlisted-browser → release-log-browser → public-release-integrity整个命令exit 0。1366/768/390六类原生异常小物递出、同模型、摆放副本不可复制、准确归还/拒绝/刷新、中英展开状态与原AP/钱/RNG/flags不变；原九种收藏、实际藏果发现/食用/腐坏堆肥、无编号房间转存/布局/重载及日志全部通过。index和11原CG均HTTP200、SHA256逐字节等于安全本地输出，运行index Git blob e81b27e54a57c881349144dd87bc670ff4139014。手机实际紧凑双列四完整卡片截图已检查。

完整证据verification/living-anomalies-177-results.json含44真实ID/尺寸与源码哈希；本批只完成异常小物真实交接、归属与许可基础。原03的自主挑选/藏物/实际观察发现、私人活植物、真实NPC赠礼来源仍欠；其余历史大型扩展、正式美术与真实公网AI继续按原目标逐条验收，整体目标未完成。没有读取真实玩家存档/.env/密钥，也没有付费AI测试；完整仓库全套未执行，不冒充全部通过。


## 0.13.178 · 原03自主挑选异常小物与实际发现（2026-10-18，本地通过待公开）

在177真实交接与归属基础上接入LabLivingAnomalies.finish：养成模式、安静跨日、自由通行、实际在自己空间、健康>=30、自主性>=60或原autonomy>=6、未显现重症/隔离/灰潮/恐惧过高等条件下，从可以进入且未严重损坏的仓库取一件真实未摆放小物。沿用44个现有小物ID，优先较低稀有度，再按已有好奇/独立倾向选择；不取已经在架上同种物件、不动已摆副本、不生成库存。至少隔四天、每个个体最多自主收存三件，整个架子仍最多六件。0AP/0钱/无属性、关系、flags奖励、不使用世界RNG。

选择记录保留实际source=chosen、当前姓名/出生日期/代数。Jack不在房间则discoveredDay=0，收藏卡片、计数和可见历史不泄漏未观察物；猜ID不能取回。纯渲染/中英文切换不发现或写状态。实际room:enter/inspect或Jack在房内过夜才记录found；UI显示发现日，选择时刻不冒充亲眼见证。归还沿用177的在场许可、每日一次、可拒绝、满库存原子拒绝。

存档仍living.anomalies v1附加字段。177旧手动交接默认source=offered并保持已知可见，不重播、不隐藏原物；新隐藏状态/发现记录精确保存。继任保留旧实物及观察状态、原所有者；新个体重新建立选择间隔，不继承旧习惯。读档由真实选择记录修复缺失冷却。

专项44种逐件实际自主扣库存/同一实体总数、隐藏ID拒绝、远程不可发现、纯渲染、实际进入/重复发现、四天/三件限制、安全门禁、旧附加字段迁移及真实Engine过夜/存读/告别继任通过。初次灰潮测试夹具误设未来预报，已改为当天实际weatherByRegion；当前灰潮抑制案例通过，未以测试假象修改天气逻辑。原177全部44种手动交接、九类普通收藏、藏果、自主摆放、世界资产继任与Claude保护回归通过。源码HTTP452资源/私密路径404通过；完整仓库全套未执行。

本地原生浏览器1366/768/390顺序自主过夜→隐藏读档→远程面板不可见→实际进入→同模型发现→双语保持展开/不写档→拒绝读档→次日归还全部通过；原六类交接三尺寸及当前日志通过，无pageerror/横向溢出。手机实际发现截图已查看。公网回执随后补记。原03私人活植物和真实NPC赠物来源、全部历史大型扩展统一验收/正式美术/真实公网AI仍欠，整体目标未完成。


### 0.13.178 最终公开验收（2026-10-18）

运行提交10b8769db19115b607af247bae6fb581db5b3c9d；Pages39113967698 completed/success；https://stepono927.github.io/Stephen/?release=0.13.178 。公网顺序lab-living-anomaly-choice-browser → lab-living-anomalies-browser → lab-living-fruit-browser → release-log-browser → public-release-integrity整个命令exit 0。1366/768/390实际过夜扣真实陈设库存→隐藏状态精确读档→远程面板不泄漏→真实进入后发现→同模型→双语展开/不写状态→拒绝存读→次日原数量归还通过；原六类手动交接、藏果发现/食用/腐坏堆肥及日志全三尺寸通过。index及11张原CG均HTTP200、SHA256逐字节等于安全本地输出，运行index Git blob f540ee3f25eb0900604aa7c2d0aec55d5bce05b4。

44种自主选择与全部真实数量、同级物品受好奇/独立倾向影响、安全门禁、旧177字段兼容、实际继任已取证。证据verification/living-anomaly-choice-178-results.json包含44项清单、代码哈希与公开校验，三宽度真实发现截图随包。英文目录14288；完整仓库全套未执行，不冒充全部测试通过。无真实玩家存档/.env/密钥读取上传，无付费AI调用。

原03当前专项索引：自主摆放171、九类实际库存收藏172、真实藏果173、异常小物手动交接177与自主收存/实际发现178已有公开证据。私人活植物、真实NPC赠物来源仍待实施；隐私/睡眠空间/房内服装等整间房专属条款仍须逐项统一终验，不能据此宣称整间房或27房间全部完成。全部历史大型扩展、正式美术、真实公网AI等原目标继续保持未完成。


## 0.13.179 · 原03真实私人活植物与照料（2026-10-18，本地通过，待公开）

按27房间原03“私人收藏/植物/观察到的习惯”，新增LabLivingPlants。支持156种现有单槽、非树木、非ANOMALOUS植物，最多三盆；树木/异常植物保持原设施，不凭空赠种子或改原获取路径。手动递出由当前在场个体决定接受；移动原植株对象与UID，携带原遗传五轴/父系/世代/特性/扫描记录（经原校验）、播种日/生理日龄、水分、健康与植物病害。温室原槽位释放，但原种子/收获/钱/AP/剧情flags不会因搬运增减。

GardenState原植株读取提取为readPlants，Garden原单株生长提取为stepPlant，原温室仍调用同一规则。修改前捕获800个真实基线，覆盖200物种×有无遗传×正常/缺水低照/临寿状态；修改后生长、健康、水分、寿命、生态、自动浇水费用与原日志逐字段完全一致。基线记录原源码SHA256 cd792a7366a805e6e6e6c323692c420d0f3af875895fbe0902a263164315e011，可对照178已交付源包；不是把新实现输出当预期。

私人盆栽独立保存原盆土/病害，继续原生理、基因修正、寿命和PlantHealth病害规则；不靠移动清除病害/重置年龄。没有温室水培自动设备/种植专项加成。浇水实际扣0.5净水；已见病斑护理沿用1AP/2净水及三日护理，不即时治愈。合适健康/自由通行/自主性条件下可自己保留一盆（每个个体同时最多一盆自主保留、至少七天间隔）并用真实水照料。新搬来的植物不会同一天被重复生长计算。Jack实际进入/检查才发现；远程面板、计数、记录不提前泄漏，纯渲染不写档。

搬回温室/清理枯株须询问，可拒绝、每盆每天一问；同日拒绝递出不能通过改变恐惧立即催问。满温室/关闭设施/满堆肥桶先原子拒绝，不丢植株或消耗询问机会。归还同一株及原病害，采收/育种/扫描仍由原温室执行；不能用温室按钮远程操作私有植株。枯株可在许可下变成原一份堆肥；已过花期/寿命的盆栽保留枯株，不用读档复活。旧个体植物与归属保留，新代不自动继承归属/照料习惯。

新增可选living.plants v1，缺字段旧档为空且不追播；读档仍用原GardenState/PlantHealth校验，去除非法/重复/跨容器重复UID、保留真实植株所有权，抬高greenhouse.nextId避免后来播种撞ID。源码HTTP453资源、私密路径404通过；156物种往返、谱系/年龄/水/病害精确保留，三盆/温室/堆肥容量、许可、实际干/湿盆过夜对照用水差0.5且世界RNG相同、隐藏发现/旧坏档/实际继任通过。200种原温室、植物病害/寿命/状态模型/污染、认证种子/实际G1→G2→G3分析、原异常物/藏果/世界继任和Claude保护回归均通过。完整仓库全套未执行，不冒充全量。

本地1366/768/390原生UI两条流程通过：原株/病害搬入→精确护理/浇水→温室不能遥控→双语/不改状态→拒绝读档→次日原株归还；真实过夜自主留下→远程不可见→实际进入发现→同模型与精确存读。手机截图已检查；空温室不渲染空白选择框/无效递出按钮，最终复测/公网回执随后补记。复用原PlantArt生长/健康模型，不把程序图标视为全部正式美术完成。NPC赠物真实来源、房内实景陈设/隐私/睡眠/服装等原03整体验收、其余历史大型扩展/正式美术和真实公网AI仍欠，整体目标保持未完成。


### 0.13.179 最终公开验收（2026-10-18）

运行提交e63a1e835f1c2aa75283f093e5a6f58225b448ed；Pages39116138019 completed/success；https://stepono927.github.io/Stephen/?release=0.13.179 。公网顺序lab-living-plants-browser → lab-living-anomaly-choice-browser → lab-living-fruit-browser → release-log-browser → public-release-integrity整个命令exit 0。1366/768/390实际原株及病害搬入、原UID/谱系/日期/状态保存、护理1AP/2水与浇水0.5水、温室不可遥控私人株、双语/纯渲染、拒绝读档/次日原株归还；实际过夜自主保留→远程不可见→实际进入后发现→原模型/精确存读全部通过。原异常小物与藏果三尺寸及日志通过；index与11张原CG HTTP200且SHA256逐字节匹配安全本地输出，运行index Git blob b1ba5aa954ca6cbe62e059c3e69c6ee8126d5132。

最终手机界面已检查：空温室不显示空白下拉或无效按钮；已知盆栽也只在Jack实际在场时显示当前水分/健康，远程不提供实时状态，未知植株不提前泄漏。单元已验证156种往返、800个修改前原温室基线（全200种）、真实干湿盆过夜用水差0.5且RNG相同、遗传/生命周期/病害/容量/旧UID迁移/实际继任；原污染/认证种子/G1至G3品系分析及Claude保护回归有通过证据。证据verification/living-plants-179-results.json含156项清单、源码/基线哈希与公网收据，六张三宽度护理/发现截图随包。完整仓库全套未执行，不冒充全套通过。

原03私人活植物的真实搬运、照料与观察发现本批取得公开证据。NPC赠物实际来源仍欠：已查Street.gift是玩家送出旧物，Social.help发资金而无实体工具，这两者不能倒填成NPC给零号的赠礼；后续须核对其他路径并建立真实交接。房内实景摆设/隐私/睡眠/服装等整房间原条款、历史扩展统一终验、其余正式美术和真实公网AI继续按原目标推进。没有读取上传真实玩家存档/.env/密钥，无付费AI测试，整体目标未完成。


## 0.13.180 · 原03八位NPC真实纪念物来源（2026-10-18，本地通过待公开）

新增NPCKeepsakes：Lenny/Mara/Finch/June/Reeve/Milo/Oona/Ben八位既有人物，各有一件明确的私人纪念物、独立中英赠物台词与物件故事，使用八种对应既有实体模型。来源是新增有限NPC私人物件，未交出为1，实际接收后为0，终身/继任/刷新不补回；不是玩家库存赠出再复制，也不从旧Street.gift或Social.help标记倒填收到过的礼物。每次必须当前原NPC仍活着且未被接替、熟悉Jack（3次接触/35信任）、当前时段当面交谈，零号自由通行、实际同行、身体允许且在场。聚落按原实际抵达流程；实验室住户须NPC/Jack/B07确在同一房间。

由当前个体决定接不接。拒绝不耗NPC物件，当天不再催问；接收原子写入赠送者ID/实际姓名、接收日、原接收个体姓名/出生日期/代数和KEPT位置。不增加AP、资金、属性或NPC信任、不耗世界RNG。只新增八份私人纪念物，不声称所有NPC支线/自主社交均已完成，也不把信任值本身冒充交接凭据。

物件为可识别的私人纪念物，不折现、不混入普通库存；可在实际自己的空间询问移入BOXED旧物盒，可拒绝且每天一问。旧礼物/来源随实验室保留，原赠送关系不改；新个体可自愿接过旧物，另记holder姓名/出生日期/代数，原donor/recipient/day保持。不给继任者自动补领同一NPC礼物。带入旧盒是实体位置变化，不是销毁/出售。

新的living.gifts v1可选，旧档缺字段为空，不编造过去；重复/非法/未来/错误物品的收据过滤，有效条目不被前一非法重复吞掉。保存来源时保留历史赠送者姓名，不依赖当前NPC显示名覆盖；死亡和接替不删已收到的实体。NPC记忆始终保存本批新增中文原文，运行时注册并打包对应英文，中文/英文接收后都可正确双向切换和读档，不把英文界面下收到的台词永久写成英文。

单元八位全部实际接收/有限总数/来源与模型/不推断旧flags、拒绝/错误地点/死亡/接替/隔离/封闭通行/重复原子拒绝，实验室三方同房间与异房间拒绝，实际Engine/存读/告别继任及新持有人自愿接过通过。普通私人收藏、156盆栽、异常小物、120NPC/900旧语境、世界资产继任和Claude保护回归通过。源码HTTP454资源/私密路径404通过，测试API显式为空。完整仓库全套未执行，不冒充全量通过。

本地1366/768/390八位原生人物页递出、16次中英切换/规范记忆、8份精确来源与存读、纪念盒/归还手边/拒绝三尺寸通过；原盆栽与日志三屏回归通过。手机卡片缩短、完整来源/故事展开查看，最终截图及公网回执随后补记。其余房间实景、隐私/睡眠/服装及独立社交的完整原条款、所有历史大型扩展统一终验、正式美术与真实公网AI仍欠，整体目标未完成。


### 0.13.180 最终公开验收（2026-10-18）

运行提交71e5881c83e4468db52f99f6a51d4c1f8ecacb0a；Pages39118137921 completed/success；https://stepono927.github.io/Stephen/?release=0.13.180 。8位NPC原生赠物在1366/768/390全部通过，有限来源、原接收者/新持有人、拒绝/读档和中英记忆均有证据。原1000条人物日常翻译/每屏60次实际交谈与原私人盆栽三尺寸回归通过。日志三尺寸与index+11原CG逐字节校验通过。整批55异常物几何/220旋转、物理尺寸/330旧布局迁移、公开四页55件图鉴在电脑/平板/手机再次通过；没有把模型唯一性等同于全部正式美术审定。

证据verification/npc-keepsakes-180-results.json与三屏截图随源包；当前公开index Git blob256158d272f59065c0ae26648608092e338bdd55。完整仓库全套未执行。房间实景/隐私/睡眠/服装和独立社交的完整原条款、历史扩展统一终验、其余正式美术和真实公网AI仍欠；整体目标保持active。本批八条赠物不是所有NPC支线完成。未读取或上传真实玩家存档、.env或密钥，无付费AI测试。


## 0.13.181 · 原03私人房间的摄像头许可（本地候选，2026-10-18）

核对发现旧privacy命令只切换永久布尔值，Jack无需在场，且旧开启状态会跨日保存；观察室直接依赖该位。新增LabLivingPrivacy与可选living.privacy v1：实际Jack与零号同房间、自由通行、身体允许且设备可用时当面询问。沿用原语言/怨恨/信任/独立性条件，并考虑已知恐惧和压力；它可拒绝。每个个体每天一问，拒绝不增关系分、不耗AP/资金/库存/世界RNG。

许可保存当天、出生日期与代数，关闭后同日不再重问；换日、换代、收回自由通行、严重病况/隔离、离开或不再愿意时撤回。原private布尔兼容同步，但单独旧false不再视为永久同意；旧档缺模块默认摄像头关闭，不改其他物件/剧情/flags。观察室按有效许可显示或遮蔽住户，不能靠篡改旧private位绕过。许可和拒绝不传给新个体。

新增隐私面板，实际按钮询问/关闭，纯渲染/切换中英不写档。单元覆盖当面、设备、身体、封闭、故事/事件、原子拒绝、当日限制、过夜、旧坏档和实际Engine存读/告别继任。原27房间、运营、习惯/房间事件、Jack私人事件、真实世界资产继任、原私人盆栽/NPC赠物与Claude保护回归通过。三屏最终浏览器、公开与资源收据随后补记，完整仓库全套未运行。

本批仅修真实摄像头隐私授权，未把它等同于整间私人空间/睡眠/服装/实景/独立社交的所有原条款；这些及历史大型扩展统一终验、其余正式美术与真正公网AI继续保留。配音由用户后续提供，目标未完成。


### 0.13.181 最终公开验收（2026-10-18）

运行提交9e65f36e35f8c8325bcc9c692a669e3b097942e9，Pages39120271781 completed/success。公开 https://stepono927.github.io/Stephen/?release=0.13.181 的顺序浏览器命令最终exit 0：私人摄像头原生当面许可→双语纯面板→读档→观察室可见→关闭后遮蔽、拒绝保存/当日不重问、原生休息过夜收回许可，1366/768/390全部通过；八位NPC原赠物来源/模型/记忆/交接/拒绝/继任持有人原流程三屏回归通过，日志三屏通过。index及11张原CG逐字节校验通过，运行index Git blob3c04cd6b0aa4282a3c2684c0e64111d3d49ebb34。

455个源码资源/11CG/私密路径404通过，测试服务器显式空API Key且不加载.env。单元实际Engine读档、隔夜及告别/新个体测试通过；旧private=false不作同意，许可按出生日期/代数/当天有效，收回自由通行和不再愿意即时关闭。另13个房间、运营、实际收藏/盆栽、摆放、习惯/事件、世界资产继任和Claude保护相关单元文件通过；完整仓库全套未运行。verification/living-privacy-181-results.json含源码哈希、实际公网收据，三屏截图随源包。

本批仅修摄像头的真实隐私许可与观察室接入；不把它冒充整间房睡眠/实景/服装/独立社交或全部隐私场景。所有历史扩展原要求、其余正式美术和真实公网AI继续欠，配音由用户后续提供，目标保持active。没有读取上传真实玩家存档/.env/密钥，也未调用付费AI。


## 0.13.182 · 原03真实床铺过夜与睡眠（2026-10-18，本地候选）

原私人房间有静态窝垫与家具布局，但原rest只推进全局日期，未保存实际用了哪张床，也不使用医务sleep值。新增LabLivingSleep与可选living.sleep v1：真实过夜前零号实际在living、自由通行、身体允许、房间开放才接入，不搬走其他房间/值班/隔离中的个体。14种实际已摆放床铺均可用，只拥有未摆放的床不算；没有床仍有原窝垫。保留实际UID/item、个体姓名/出生日期/代数、当夜和实际恢复量；连续使用可保留该个体偏好，家具本身与库存数量不变。

安静/低恐惧压力、未饥饿、房间未明显受损、原operations.comfort达到条件时，原医务sleep每夜最多+2（床）/+1（窝垫），100上限，实际日结一次；不增加健康/关系/AP/资金/世界RNG，不清除疾病/计划/护理记录。病况与其他医务逻辑仍按原Infirmary.observe执行。零健康、严重病况、隔离或不在房间不获得此恢复。浮点增量收据归限到2，避免2.000000000000007导致读档误删合法记录。

Jack未实际进房前，新记录不进入面板/历史/房间图像；进入后保存discoveredDay，纯渲染与双语切换不发现、不写档。记录最多60晚，旧档为空不倒填；原个体痕迹随实验室保留，新个体不继承sleep/床铺偏好。实际床收回后仍保留历史来源，但图像不继续展示已收走的床。房间床图使用相同BedroomArt.model及真实UID，不重画已批准CG，不冒称正式手绘美术。

单元14床/窝垫/所有权/条件/身体/封闭/错误地点/当夜去重/容量上限/原医务计划及隐蔽病况/旧坏档/真实Engine原过夜对照、存读/告别继任通过。90真实疾病各30晚2700次医务兼容检查，逐次证明只改有上限sleep、不额外改病程/计划/历史/信任/压力/健康/世界RNG，合法宿主和存读均通过。这是兼容验证，不冒充完整逐病长期平衡验收。原10个房间/摆放/隐私/个人习惯/私人事件/90临床/疾病/继任/Claude保护相关文件通过；最终三屏与公开回执随后补记，完整仓库全套未执行。

整间房实景、服装、独立社交和其余原条款，以及全部历史大型扩展统一终验、正式美术、真实公网AI仍继续，配音由用户后续提供，整体目标未完成。


### 0.13.182 最终公开验收（2026-10-18）

运行提交8e3a3620726572cbdf915b210ecb4e23fbd4bb7d，Pages39122253377 completed/success，公开 https://stepono927.github.io/Stephen/?release=0.13.182 。顺序浏览器命令最终exit 0：真实床/窝垫过夜与医务sleep恢复、远程不可见、原生实际进房发现、对应真实床UID/模型且只有一份可见、双语纯面板/展开历史保留、精确读档和床收回后的历史来源，1366/768/390全部通过；原私人摄像头许可/拒绝/关闭/存读/隔夜与日志三屏回归通过。index与11原CG逐字节匹配，运行index Git blob a5f051b2c99a171ca70912217708f918e0c3173b。

源码HTTP456资源、11CG与私密路径404通过，测试服务器显式空API Key且不加载.env。14真实床种/实体、窝垫、所有权/位置/身体/损坏/当夜幂等/65夜保留60/旧坏档、真实Engine原过夜对照/读档/告别继任通过。90真实疾病×30医务夜=2700兼容检查通过，逐次保持病程/诊断/疗程/历史/信任/压力/健康/随机数不被睡眠模块改动，只允许有上限sleep变化；不是完整逐病长期平衡终验。原10个房间/摆设/隐私/习惯/私人事件/临床/疾病/继任/Claude保护单元文件通过；完整仓库全套未运行。

verification/living-sleep-182-results.json包含源码哈希与公网收据，六张三宽度房内模型/面板截图随源包。房间图复用实际BedroomArt床模型，不冒称新建14份正式美术；通用bedroom:layout仍是玩家统一布局提交，其与私人摆设完整许可的边界尚需整体验收，本批不把睡眠接入当作Jack已无所有控制权。整间房实景/服装/独立社交及全部历史大型扩展统一终验、其余正式美术和真实公网AI继续欠，配音由用户后续提供，目标保持active。未读取上传真实存档/.env/密钥，无付费AI测试。


## 0.13.183 · 快乐俱乐部满库陈设奖品无损交接（2026-10-18，本地通过待公开）

从最终规格74节与实际发奖/存档链核对，发现Wheels.grant将陈设owned增加到最高100000，而Bedroom.read每种仅保留99；超过99的原奖品会在重载丢失。新增HappyClubFurnishings：新奖品先进入实际99库存，满库原ID/原件数进入prizes暂存，不代换成钱或材料、不改奖池/概率。旧档仍明确保存的owned>99且在旧生产上限100000内的数量，精确保留为legacy暂存；只从原始库存迁移，不从历史开奖/旧文字猜补，不给已无数量证据的损失造出物品。归一化后反复读档不重复增加。

实验室物资仓库和俱乐部奖品窗口可免费领取有空间的部分，每次最多100件；同种99上限不改，满库继续保留。原子检查地点/事件/挑战/容量，暂存上限时Token、资金、RNG和保底保持。真实无编号房间储存物件减少原库存后，可再领一件，原收存实体不复制或丢失；继任按实验室资产保留prizes/legacy。界面有独立双语来源，复用对应实体模型，小型可滚动列表；领取只刷新暂存区，保留仓库筛选及展开状态。

310个可入池陈设全部满99发放/保留/读取通过；所有已知陈设原始超额精确迁移、旧无俱乐部字段、无真实超额不猜补、非法值、部分/100件批次、地点/事件/容量原子失败、实际Engine保存、真正无编号房间转存再领取/真实继任通过。原9000次抽取、六池与全部保护排除、史诗第六抽保底、Draw All、5100局内检查点、490帧实际购车驾驶入场、门票/日限、6场景、完整奖品类别、18统计、11成就、NPC/新闻/周活动、世界继任及Claude保护相关11文件回归通过。

本地1366/768/390原生Common家具/Rare异常物满99中奖→跳过动画→刷新保留→双语暂存→真实移入无编号房间→实验室仓库部分领取/筛选保留→精确读档全部通过，只有一个可见暂存面板。源码HTTP457资源、11CG/私密路径404通过；测试服务器显式空API Key且不加载.env。完整仓库全套未运行，公开回执随后补记。

新增HAPPY-CLUB-SPEC-ACCEPTANCE.md，74节原条款逐节完整保留并校验，指向实际源码/测试；已有专项不等于统一终验，各节仍按全条款待验。其余历史模块范围、正式美术、私人空间完整控制许可等原要求与真实公网AI保留，配音由用户后续提供，整体目标active。


### 0.13.183 最终公开验收（2026-10-18）

运行提交9ee3af11bc72908b3755b778324e66ac9f7d305f，Pages39123602545 completed/success，公开 https://stepono927.github.io/Stephen/?release=0.13.183 。顺序浏览器命令最终exit 0：Common家具/Rare异常物满99原生中奖→跳过演出→原物暂存/精确读档→双语窗口→真实移入无编号房间腾出一份→实验室物资仓库部分领取→筛选/展开保留和再读档，1366/768/390全部通过，无货币/AP/RNG/Token或开奖序号额外改变，只有一份可见暂存区。原生靶场两击/结算/刷新恢复/8000-12000-18000票价/每日三轮及日志三屏全部通过。index、完整74节索引与11原CG逐字节匹配，运行index Git blob4ca2a94838ff1f9abaa3b6e36bb7fe87208f231e。

310种可入池陈设全部满库保留/读取、所有已知陈设真实旧超额迁移、没有数量不从中奖历史猜补、部分/100件/旧坏档/容量与地点原子性、真实无编号房间转存与真实继任通过。原17个相关单元文件（俱乐部存档/9000抽奖/驾车/场景/类别/统计/成就/NPC新闻，加6种奖品适配和世界继任/Claude保护）全部通过；5100局内存读检查点和490帧实际购车驾驶入场保留证据。源码HTTP457资源、11CG/私密路径404通过，测试显式空API Key且不加载.env。完整仓库全套未运行。

证据verification/club-furnishings-183-results.json含源码哈希、公网收据与完整原规格保留校验，六张三宽度俱乐部/仓库截图随源包。新增HAPPY-CLUB-SPEC-ACCEPTANCE.md完整保留74节所有原文、逐节源码/测试入口，各节仍待统一全条款验收，不能用本批存档修复宣称整个俱乐部完成。其他历史模块、正式美术、私人空间完整许可及真实公网AI等原范围继续保留，配音由用户后续提供，整体目标active。没有读取上传真实玩家存档/.env/密钥，无付费AI测试。


## 0.13.184 · 快乐俱乐部终局漏记、重复恢复与重开边界（2026-10-18，本地候选）

复现旧Round.advance在elapsed>=25000时先end清掉在场靶，真实种子1788458060/22.3秒/一次避让+在场第二Bomb直接跳25秒，旧结果只记1。新TIME在清场前计入当前仍在场且未误击的Bomb；自然已到期的Bomb已移出，不重复。LEFT、BOMB或场外RECOVERED不把未完成的在场Bomb冒充避开。先前Token不变，终局/重复end/恢复保持幂等。

新增还原校验：序号至少覆盖已生成数量，在场Bomb+避让+误击不超过已生成Bomb，在场奖励靶+已击破数不超过已生成奖励靶，命中数覆盖在场半命中。有效version1存档不改字段、不改剧情/route/ending/flags；不猜补旧已结算但缺少在场记录的成就。另复现历史已结算round又残留active时11 Token会重复成22；新Core.read忽略已留存结算ID的重复active，保留原收益与历史，不重复支付。

浏览器查到旧modal close事件晚到会取消新面板RAF和ResizeObserver、误结束新round，造成数据已结算但画面停旧统计；HappyClubUI/WheelUI在新俱乐部表面已打开时忽略旧关闭事件，真正X关闭仍按LEFT结算。补中英文明确本轮结束/Bomb反馈，存档原因ID不改。

真实种子单元覆盖TIME/LEFT/BOMB/RECOVERED、SELF CONTROL及WRONG ONE真实Engine解锁、两种重复历史/active恢复、Token保留、坏的在场统计、重复保存和8个粗细时钟比较；原300种子91075姿态/2988击破/153个Bomb保留例/平均13.5933目标、5100局内检查点、成就/统计/310陈设/继任/Claude保护通过。六级9000抽、辅助动态、独立TargetPlacementValidator及运行期边界/曲线路径/Bomb距离回归通过。最终三屏与真实驾驶/25秒时钟、公网回执随后补记，完整仓库全套未运行。

保留全部74节原文的HAPPY-CLUB-SPEC-ACCEPTANCE.md补本批对应条款；其余74节统一验收、其他历史扩展、正式美术和真实公网AI继续欠，配音由用户后续提供，整体目标active。


## 0.13.184 · 俱乐部终局与快速重开（已公开验证）

- 实际修复：自然计时结束时，最后仍存在的黑靶未计入避开数；仅TIME计入尚未命中的黑靶，LEFT/BOMB/RECOVERED不补算。真实种子1788458060由1修正为2，SELF CONTROL读取实际结算。
- 已知历史ID仍保留时，重复活动轮次不再重复结算。复现过11 Token错误变22，本次仍为11；原奖励、历史、统计保持。此保护针对保留的历史ID，不宣称无限期防重放。恢复时检查真实存活靶与累计命中/生成数的一致性。
- 修复同一弹窗快速关闭再打开后，旧close事件停止新一轮/新奖品展示的问题；真实关闭仍正常退出结算。中英终局反馈显示实际原因，不改存储枚举。
- 本地：终局单测、300种子91075姿态与2988清靶、9000轮盘抽取及相关存档/成就/统计/家具/运动/摆放/继任/剧情回归通过；源入口457资源通过。未运行整库全套测试，不将局部通过等同全部规格完成。
- 公开：1366/768/390三尺寸分别通过终局、真实两击、奖品满99保留/部分领回、菜单更新日志；罕见状态使用真实确定性种子和受控时钟，按钮关闭及黑靶点击原生操作。驾车流程为原生购车/出发/停车/入场，实际加速物理帧500/490/500；桌面另有自然25秒到时结算。三档门票8000/12000/18000、读档和每日3次限制通过。
- 发布：runtime commit `fdcd1548b7e9a6e5ad8b7a5de0cd4fee49f53405`；index blob `851daa9e681498d32d2703ae89f8bfec3f84ed9d`；Pages run `39125907282` success。公开index、完整74节原规格索引、11张原CG共13文件逐字节一致。
- 证据：verification/club-terminal-184-results.json、6张终局截图、3张到场截图与verification/public-release-integrity.json。隔离测试存档；未读取上传真实玩家存档/.env/密钥，未调用付费AI。
- 仍欠：Happy Club全部74节统一终验、中文Token银行/模式枚举漏译核对、正式美术与全部历史大扩展逐项验收、公开AI审批后台。整体目标保持active；保护剧情/route/ending/flags及11张原CG保留。


## 0.13.185 · 俱乐部双语显示与兑换连续性（本地已验收，待公开）

六级Token银行/按钮/中奖等级类别与天数、四种挑战名称、奖励靶aria-label、五名原NPC名字/原对白/画像说明和节日新闻标题补齐本地语言。稳定DOM value、Token/模式ID、旧存档/概率/奖池/保底保持；开奖中切换语言不取消动画，已揭晓的物品名称随语言改变，不重新发奖。修复新日志记录缺必需pending字段后，原生菜单/日志入口三屏复测通过。源码入口顶部版本由旧0.13.95同步到0.13.185；自包含与公开包仍使用同一构建版本。

1366/768/390浏览器实测：COMMON原生兑换→动画中双语切换→跳过→DRAW ALL共12个真实Token→每件名称核对→刷新，全部游戏字段一致（仅排除正常savedAt）；HARD原生购票/实际生成靶→动态语言切换→结束；四选项value不变，静电夜首票10000/困难8000；第77天节日与静电夜两类新闻、五个人像说明通过。纯切换语言时游戏状态/RNG完全不变，无溢出/pageerror。另有终局/正常两击/满库陈设三屏回归与22个相关单元文件通过，源码HTTP457资源通过；完整仓库全套未运行。六张本批截图和verification/club-locale-185-results.json随源码包交付。

HAPPY-CLUB-SPEC-ACCEPTANCE.md仍保留74节全部原始正文，追加局部证据，不缩小目标。完整74节统一终验、正式美术/历史大扩展和公开AI审批后台仍欠；配音由用户后续提供。未读取上传真实存档/.env/密钥，无付费AI测试，保护剧情/route/ending/flags和11原CG保留，整体目标active。


### 0.13.185 最终公开验收（2026-10-18）

运行提交`a3df3c4a1eab883b34118ad8d629042b226416ce`，index blob `df306a33c7aab320ceb837cb210f6147a170dc54`，Pages `39127284079` completed/success，公开 https://stepono927.github.io/Stephen/?release=0.13.185 。线上顺序浏览器最终exit0：双语实际兑换/跳过/DRAW ALL十二件/刷新原结果、四挑战选项与费用/在场真实靶、五个人像/既有名字与对白映射/两种活动新闻；原生两击/门票/每日限制、罕见种子受控时钟终局/防重复/关闭、满库99陈设暂存/真实无编号转存/实验室部分领取、原生菜单/日志。1366/768/390全部通过，无pageerror或横向溢出。

index、完整74节索引与11张原始CG共13文件线上逐字节匹配。完整74节正文仍全部存在；追加的只是本批局部证据，未以显示修复宣称整个俱乐部或历史目标完成。源码HTTP457资源、22个相关单元文件通过，完整仓库全套未运行。隔离测试档，未读取上传真实存档/.env/密钥，无付费AI测试。六张本批截图及verification/club-locale-185-results.json含源码哈希与公开收据随源码包。

仍须完成：74节统一全条款/最终观感、其余历史大扩展/正式美术与公开AI审批后台；私人房间布局控制权边界继续按原规格核对。配音由用户后续提供，保护剧情/route/ending/flags与11CG保留，整体目标active。


## 0.13.186 · 私人房间布局许可与自主位置（本地已验收，待公开）

对应27房间原稿03“这是B-07的房间；Jack不是默认拥有全部控制权”：自由生活的当前住户拥有布局决定权。家具编辑为独立预览，实际保存必须有当天、当前生命、同一实际基线和同一完整预览的当面许可；保存后用完。健康/实际共同在场/自由通行/有效房间与既有意愿条件检查，不按关系点收费或奖励。拒绝当天不再问。无改动不重复写收据。

高Autonomy使用原LabLivingArrangement真实记录和favorite UID保护它自主决定的位置，不能通过删除、换UID/物品或移走对应支撑覆盖；其他家具仍能请求。当前自主物件定义均为floor，支撑关联分支采用明确标注的前向兼容合成支撑夹具验证，未冒充现有surface物件实测。实际尺寸适配预览仍本地；直接fitScale提交也走同一许可，原55模型迁移/原地适配与库存保持。

摄像头与布局许可独立；未实际进入房间时终端不展示私人物理布局，原生进入后才能预览。新字段roomSystems.rooms.living.layout为加法迁移，旧档没有许可，旧家具/收藏不重置。日期/主人/实际房间变化或意愿撤回使旧许可失效；真实Engine休息/继任后旧许可不传递，过去的短收据保留，旧对象/route/ending/flags和保护剧情不改。

本地1366/768/390：原生进入、坐标预览/请求/确认、双语保留未保存预览、同日许可刷新恢复、改方案失效/保存消耗、取消不改实物、拒绝刷新仍保留、自主真实小物覆盖阻断及高自主仍同意其他家具全部通过。原摄像头三屏、满99家具奖励/真实无编号转存/实验室部分领取三屏、更新日志三屏通过；17个相关单元文件、源码HTTP458资源通过。完整仓库全套未运行，不据此宣布全部27房间完成。六张截图与verification/living-layout-186-results.json随源包。

仍欠所有历史原范围统一终验、其余27房间/生产遗传/世界社会/正式美术与公开AI后台等。配音由用户后续提供。隔离测试档，未读取上传真实玩家存档/.env/密钥，无付费AI，整体目标active。


0.13.186 追加路径核对：无编号房间直接从卧室移入、异常生活事件的封存选项，原来都会直接删掉已摆放位置；现于任何库存/AP/住户副作用前检查同一份完整布局许可。空闲库存副本照常转入；私人房间可先原生获准收回再实际交接。事件未获准时仍可选择原“保持距离”分支完成，无死锁。实际三屏侧栏进入→双份物件→一份空闲库存转入→另一份当面请求/确认收回→再转入，最终两份在库、AP只消耗原定2点，未复制或丢物。私人空间归属在本生命曾自由生活后保留，重新锁门不恢复默认控制；既有自主摆放/睡眠记录也证明原归属，下一个个体不继承旧许可。当前17文件单元及路径测试覆盖实际Engine存读。


### 0.13.186 最终公开验收（2026-10-18）

最终运行提交`35c47e39f454cf8ba2d924aa38dd05eec49e328d`，index blob `c2c47de4a831e57ba2959feca40c7fa45b07ab60`，Pages `39129466428` completed/success。公开 https://stepono927.github.io/Stephen/?release=0.13.186 。线上顺序浏览器最终exit0：1366/768/390原生房间进入/预览/当面请求/精确保存/同日许可刷新/许可用完/取消/拒绝/真实自主物件保护、语言切换不改未保存预览或游戏状态；无编号房间与事件封存旁路也由实际原生路径验证，两份实体最终交接、原AP2点且不重复。未获准时原保持距离选项能结束事件。

同三屏原摄像头独立许可/关闭/监控/过夜过期、满99陈设奖品保留/无编号真实转存/实验室部分领取、原生菜单/日志通过。index、完整74节俱乐部原规格索引与11张原CG共13公开文件逐字节一致。17个相关单元文件通过，新增源码后HTTP458资源通过；完整仓库全套未运行。支撑面保护目前为前向兼容合成夹具验证，未冒充当前floor-only自主物件的surface实测。

证据verification/living-layout-186-results.json（含最终源码哈希与公开收据）、六张三屏许可/保护截图、相关永久单测和原生浏览器脚本随源码包。未读取上传真实玩家存档/.env/密钥，无付费AI调用；家具/收藏和旧记录保留，保护剧情/route/ending/flags及11CG未改。此批是房间03控制权子项完成，不是全部27房间、全部74俱乐部节或全部历史扩展完成；其余原范围/正式美术/真实公网AI后台继续，配音由用户后续提供，整体目标active。


## 0.13.187 · 三种血统特征真实遗传与旧待产保护（本地已验收，待公开）

对应GENETICS EXPANSION原稿VIII/IX/XIV/XVII：STABLE_LINE、GENETIC_MEMORY、DOMINANT_TRAIT此前仅正常记录/继承，未发挥各自特效。本批在原五轴、族谱、种畜、G3命名/称号与出生分析中补接：稳定血系缩小正常方差，遗传记忆提高携带者已有特征的传递率，显性标记提高其中一个实际已有特征并在四项上限下优先保留；没有统一抬高五轴均值、物种稀有度或取消近亲/突变/缺陷。

新配种保存inheritanceVersion:2到既有待产快照，新出生沿用format version1并带该规则字段。旧待产缺字段按原规则1/原种子/原亲本/原设施和原traitPool处理，旧出生分析缺字段不添1而保持原fingerprint；旧动物不补发性状、不改基因。新出生的原有小概率新增性状池接入稳定/显性；平均遗传率≥85且农场设施≥5可进入GENETIC_MEMORY候选池，仍须实际出生随机选中，非直接赠送。植物既有算法不切换。

1056组更新前算法输出与预测精确一致（内含264植物控制）；12288组配对种子比较，稳定产出轴偏差平方总量104553→61598，均值不抬高；同一4096种子记忆特征RICH_MILK传递2601→3414，显性目标LONG_LIVED传递2591→3418而未标记RICH_MILK仍2601；各组突变122和原缺陷61/62/63不变。这是受控样本，不是所有动物统一概率。新增13440组规则2矩阵覆盖六设施/极端与非对称五轴/健康0–100/近亲0–1及四性状上限，均在预测与原历史核验界内。

三种新增特征均从真正Core成功配种→真实birth流程获得并保存，保持Common山羊稀有度。浏览器1366/768/390原生配种扣原100资金/1AP、同存旧/新待产→刷新→7次真实过夜→旧规则与新规则各自精确出生→幼畜/全农场再读，通过。预测/语言切换不改状态/RNG；LV4不显示稀有特效名，LV5显性提示不泄露需LV6的异常目标。原出生变异分析、植物种植/分析/交叉/命名/栽培与日志三屏回归通过。23个相关单元文件、源码HTTP458资源通过，完整仓库全套未运行。

证据：verification/genetic-inheritance-187-legacy-baseline.json、verification/genetic-inheritance-187-results.json、六张三屏预测/幼畜截图和永久回归脚本随源包。后续还需完整原始动物/植物/全部性状/世界异常/生产经济与历史扩展统一终验，不把三特征修复称为全遗传系统完成。原保护剧情/route/ending/flags及11CG保持；未读取上传.env/密钥/真实玩家档，无付费AI，配音后续由用户提供，整体目标active。


### 0.13.187 最终公开验收（2026-10-18）

运行提交`a30ffd4d75be82a7d59873f8c818777ba967cf5c`，index blob `85a4a229ec6ba7a34ee1dd861d34185325e7bd2c`，Pages `39131432491` completed/success，公开 https://stepono927.github.io/Stephen/?release=0.13.187 。线上顺序测试最终exit0：1366/768/390每宽原生预测/配种/原100资金与1AP/同存旧新待产→刷新→7次原生过夜→各自原规则和新规则真实出生→幼畜与全农场再读，DNA/特征/亲本/突变缺陷/版本精确；纯预测与语言切换不改状态/RNG。LV4稀有效果仍不点名，LV5显性提示不泄露LV6异常目标。三宽旧出生变异分析与防重复收费、植物种植/四级分析/实际杂交/命名/栽培品系/读档、原生菜单日志回归通过。

公开index、完整74节俱乐部原稿索引和11原CG共13文件逐字节一致。1056组更新前遗传输出与预测完全相同，264植物控制是其中子集；新规则12288配对比较与13440矩阵通过，三种遗传特征均可真实出生获得；原240000历史核验包络回归等23个相关单元文件通过，源码HTTP458资源通过。完整仓库全套未运行。没有把三特征补齐说成整个动物/植物遗传及其余历史规格全完成。

文件verification/genetic-inheritance-187-results.json包含源码哈希、受控分布数值和公开收据；更新前基线、六张三屏预测/新生图、永久单测/浏览器与原测试加强均随源码包。未读传真实玩家档/.env/密钥，无付费AI，旧动物与待产不补发/重抽，旧出生分析fingerprint保持；保护剧情/route/ending/flags与11CG保留。其余动物/植物全部性状/异常/经济、历史扩展、正式美术、27房间/俱乐部统一终验与真实公网AI继续；配音由用户后续提供，整体目标active。


## 0.13.188 · 55件异常陈设复核与市场预览修复（2026-10-18，本地通过，待公开）

用户明确指整批55件。本批复查现有55独立XYZ模型与220旋转、实际尺度/旧布局迁移及真实库存守恒，均通过；未把已有0.13.176整改冒充本次重做。新发现地下市场25件异常陈设仍复用旧家具viewBox，造成相同模型显示明显缩小；现直接复用AnomalousObjectArt.icon，模型、标签、自适应框与卧室目录/详情相同，普通家具保留原相机。未增加商品、改库存/费用/获取概率或真实玩家存档。

本地3相关模型/尺度/无编号测试文件及地下经济回归通过；新增永久市场归一断言25件。隔离浏览器1366/768/390：原生地下市场/库存/纪念页导航，加单独审查页实际25个市场渲染器的身份/无裁切/标签/至少77%框覆盖；全部55件原生卧室目录四页、双语、紧凑可见卡片、浏览不改状态也通过。25件审查页不是25件原生市场实际获取演示。完整仓库全套未运行。仍需继续逐项正式美术/全部历史扩展验收；本批不宣称全部模型美术或整体目标完成。


### 0.13.188 最终公开验收

运行提交6d7607eaa4cc39b9a7d050b69c6b6a8b734c2b30，index blob eaa9ef84984a4682be3ca295de2fadabedfcd9da，Pages39132600949 completed/success。https://stepono927.github.io/Stephen/?release=0.13.188 公网1366/768/390的55件原生目录/25件实际市场渲染器审查与原生市场标签导航通过，所有浏览器脚本最终exit0。公开index、完整74节规格索引和11原CG共13文件逐字节一致。相关模型/尺度/无编号/地下经济/保护剧情共5单元文件通过，源码HTTP458资源通过，完整仓库全套未运行。修复限于25件市场预览框，55件原独立模型复核；不是本轮新作55件正式美术。无真实档/密钥上传，库存和旧摆放保留。证据verification/anomalous-market-188-results.json及三屏图；其余历史任务仍active。


## 0.13.189 · 食欲不佳/耐寄生虫作用与实际获取（2026-10-18，本地已验收，待公开）

对应原GENETICS EXPANSION XV/XVI。POOR_APPETITE此前只有名称/负面计分，现每日真正供食后降低12饥饿（普通18），原饲料与水消耗不减，LOW_FEED独立；缺料仍增加12饥饿，不发放小餐或补偿，原饥饿<60生产门槛继续。PARASITE_RESISTANT此前误作用于所有疾病，现按原DiseaseData.category===PARASITIC限定暴露、同栏接触、恶化风险；不能免疫，普通耐病/韧性/易病/基因/预防/恢复算法与界限保留。暴露采用原gate随机值与原候选抽取，不额外消耗全局RNG；不具此性状时原路径不变。

仅未来普通供应点Core buy在真实既有动物seed上派生一次独立性状抽取，前10%抗寄生/后10%食欲差，四性状已满则不追加；不改原五轴、性别、性情、价/AP或全局RNG。其他来源、Model.individual原始算法、原14项birthPool及已冻结version2 inheritancePool不变；已有库存/动物/黑车声明/认证运输/旧待产不补发/重抽。两性状由现有父母继承路径传入真实幼畜，不向旧出生池补项。UI实际作用沿用LV3可见门槛，LV2不泄露，中文英文纯切换不改变状态。

新增永久tests/homestead-appetite-parasites.test.cjs与三屏-browser。84真实PET疾病病程/168受控单病暴露池/24同栏接触，非寄生疾病对照一致；有性状仍会染病。真实每日同75饥饿供食：普通57可生产，食欲差63沿原门槛停产，饲料水照常扣除；LOW_FEED、缺料、0/100边界、4项上限/其他来源/旧档不补发均通过。普通购买世界种子33→animalSeed8397891为食欲差，40→10814826为抗寄生；各经真实Core配种→待产→出生→Engine/Save，出生种子540738/270369，基因/traits/原version2完全一致，未手填性状。单位出生测试性别与配对条件受控，不宣称自然世界分布。

18个相关单元文件通过（包含原1056遗传基线/13440规则2矩阵、原出生变异/认证/黑车/生产/成长/安全/植物与保护剧情、源码HTTP458资源），完整仓库全套未运行。1366/768/390隔离浏览器原生两次购买/原费用AP、LV2隐藏LV3说明、中英文纯切换、两次原付费扫描/刷新、真实过夜63vs57/饲料和基因精确再读通过。遗传旧新待产与7日真实过夜回归、原生更新日志见最终收据。未读传真实存档/.env/密钥、无付费AI。此为两个原始性状子项补齐，不代表整个畜牧/植物/食堂/世界社会/27房间/俱乐部/历史美术/公网AI全部完成；整体目标active。


### 0.13.189 最终公开验收（2026-10-18）

运行提交f1140bf89de58b87cfcbbf5fcb3cd35499c55a3a，index blob c01a7c599fa33641b0cec87f18f220d844adae7f，Pages39133480321 completed/success。公开https://stepono927.github.io/Stephen/?release=0.13.189 。公网1366/768/390原生普通供应购买真实两性状/原钱AP/扫描LV2隐藏与LV3说明/中英文纯切换/两次付费扫描/刷新/原生过夜供食饥饿63vs57和原饲料/基因/再读均通过。旧/规则2待产冻结、每宽7次真实过夜分别出生/幼畜保存及原生更新日志均最终exit0。公开index、完整74节规格索引与11张CG共13文件逐字节一致。

18个相关单元文件通过，含84真实PET病程、168受控单病暴露池、24同栏接触、两实际普通购买→配种→待产→出生保存、原1056旧基线/13440新规则矩阵等；源码HTTP458资源通过，完整仓库全套未运行。新效果不改旧动物、五轴、既有待产种子/亲本/遗传池/旧出生分析；无真实档/.env/密钥上传及付费AI。三屏截图和源码哈希见verification/homestead-appetite-189-results.json随源包。并非90疾病全长期平衡或全部遗传/畜牧/食堂/历史需求终验；原完整目标保持active，真实公网AI后台尚未部署，配音由用户后续提供。


## 0.13.190 · 人物餐食生活循环与独立进食（2026-10-18，本地通过，待公开）

对应原CANTEEN EXPANSION I/II/VI/X/XVIII/XXI：现有目录实际为160（原150+俱乐部10）和30速食，10开局食谱保留。此前人物饱腹/水分只增不减，低饱腹不影响休息；现以原FoodEffects游戏时钟结算Jack和实际在实验室驻留/入院的存活人物，每小时饱腹-.5/水分-.25，低于20的实际时段每12小时疲劳+1、每24小时士气-1；当时低饱腹的运营休息疲劳恢复由10变7.5。没有添加Sanity、致死饥饿或改疾病治疗。

每人保存nutritionHour，重复区间不结算；旧缺字段从读档已有时钟开始，无过去欠账；离开的NPC不追算，死者不结算，更替身份重新建立独立记录。菜单、纯语言切换、读档不推进时间、不吃掉食品。Jack出门不使家中NPC停表；居民原有LabMeals实际已扣的.3食品/1安全收获和.35水，现补12饱腹/6水分，短缺按实际比例补充，不另扣资源，不动B07餐盒。原居民行记录和一次/日防重仍是结算依据，读档不重放。

新增口粮包所选人物饮水：现有实际净水1份/恢复至多25水分，无AP/RNG/B07状态变化，满水、死亡、远处NPC/非实验室水源、战斗/驾车/事件/剧情模式均拒绝。拆开原ReadyFood全局B07存活/逃离限制与具体B07进食资格，人物及兼容宠物不因B07不在而被封禁；B07自己缺席/健康0/已离世不能喝水、吃速食、餐盒或实验料理，Jack能量胶也检查Jack存活。UI区分B07与所选人物，低饱腹提示及当前人物营养不会显示前任记录。

新增永久canteen-nutrition单元/浏览器。28相关单元文件通过，包含160实际制作→存活Jack食用、28兼容人类速食与全部30速食原回归、基础10/书籍120/教学20/收获10与俱乐部来源回归、限时效果/偏好/居民口粮/运营/继任/畜牧原遗传及保护剧情；完整仓库全套未运行。160制作对象测试使用合成解锁和精确真实食材，未冒称自然一局全收集；原各来源的独立测试另列。源码HTTP458资源通过。

本地1366/768/390：原生仓库口粮包→人物低饱腹提示/语言纯切换→饮水实际1份→购买罐头→所选人物吃→读档→原生休息24游戏小时，Jack饱腹-12水-6、居民原付费供餐净抵消→再读；合成B07离世档其按钮禁用，Jack仍原生买/吃/保存且B07健康保持0。另顺序回归旧人物口粮/普通购买/居民实际安全收获/厨房书籍制作/更新日志。两组三屏截图见verification/canteen-{nutrition,recipient}-190-宽度.png。

尚不能称整个食堂完成：原稿XVII的B07学习简单料理/盐糖、偷吃、随意加料未接入（现有Jack厨房实验不等于它学习）；完整原需求/配音后续/其余历史扩展/真实公网AI仍保留，整体目标active。不改保护剧情/route/ending/flags或11原CG，不读传真实档/.env/密钥，无付费AI。


### 0.13.190 最终公开验收（2026-10-18）

运行提交b31d4e3f36b5f7a37f2e59ae2adf40bf99e4be5e，index blob729a08536415c7579c9009ea8bee2db1a1762ddf，Pages39135004490 completed/success。https://stepono927.github.io/Stephen/?release=0.13.190 公网顺序六浏览器脚本均终态exit0：1366/768/390人物营养/低饱腹提示/纯语言切换/1净水饮水/实际买吃罐头/读档/原生24h过夜及驻留NPC原付费口粮抵消/B07离世后Jack进食与B07禁用，旧人物口粮/普通口粮购买/厨房书籍制作/原生更新日志；居民自动安全温室收获供餐也经原生过夜/保存/中英/三屏验证。公开index、完整74节规格索引和11原CG共13文件逐字节一致。

28相关单元文件通过（确切路径及源码哈希在verification/canteen-nutrition-190-results.json），源码HTTP458资源通过，完整仓库全套未运行。160配方制作对象测试合成解锁、真实食材/AP/水，另有原基础/书籍/教学/收获/俱乐部来源测试，不冒称一局自然全收集；30速食原回归保留，其中28适用人类。旧营养从已有游戏时钟迁移，不追扣历史；身份/死者/非现场独立，旧居民实际供餐不重复扣粮，不吃B07餐盒；保护剧情/route/ending/flags和11CG保持。无真实档/.env/密钥上传及付费AI。六张营养/对象三屏图随包。B07学习简单料理仍待实施，不能用Jack实验替代；其余完整食堂及历史/正式美术/真实公网AI待办保留，整体目标active，配音由用户后续提供。


## 0.13.191 · B-07学习基础料理（2026-10-18，本地通过，待公开）

原CANTEEN EXPANSION XVII此前确实未接入，Jack实验不能替代。本批新增独立B07Cooking模块：只在养成模式、日常通道已开放、基础语言≥1、Jack实际在安全厨房、双方存活且无外出/事件/检疫等阻碍时邀请；值班/私人作息不被强行覆盖。愿意才从实际位置走到厨房，不愿意留在原处，无食材/AP/RNG/关系罚分；同日不反复请求，已有拒绝也不能靠临时搬到厨房绕过。菜单不替它移动。

原生厨房新折叠面板，十份开局基础料理每天实际练习一次。原配方、净水和1AP由原Canteen cook事务结算；盐糖弄错品质-18，随意多加料品质-12并实际额外消耗1份本配方食材，偷吃也消耗1份真实余料并降低自身饥饿4。只从安全、未封存/过期/污染的实际余料中选择，没有余料时不会凭空偷吃/加料。保留正常制作结果，菜单和读档不重抽。单次原事务克隆后完整提交，失败不扣AP/食材也不推进RNG；本体普通Jack制作不改变随机路径。

独立个人practice按实际完成次数累计，每次熟练+5、上限100；两次同菜记住步骤，错做也能学习。概率从45%降到最低10%，不保证完美。256对相同世界种子、真实烹饪事务的受控新手/熟练者比较，错误114/34；这不是整个自然世界分布。20个实际游戏日期的Core事务及真实Engine 1AP/4h、十份基础料理、四结果实际食材/品质/一餐一用都已测。普通共同练习不要求开启AI，不新增战斗/关系数值。

新profile保存当前generation/birthDay、练习计数/日期、邀请结果和最多20条实际餐盒结果，严格读取来源、日期、质量与余料；新增十个已有Memory允许表条目，学会步骤按原记忆系统保存与告别归档，沿用现有通用记忆容量，没有改64条上限。旧缺字段默认为未学，不从Jack熟练度或旧餐盒倒推；旧餐盒/食谱/货币/路线不改。实际Engine告别→新个体明确清空个人料理学习，Jack知识、食材与已做餐盒保留，旧个体的步骤记忆留在原生命归档。

25个相关单元文件通过（保护剧情/原食堂/人类营养/个人物品/布局/摄像头/作息/继任/安全原料），源码HTTP459资源通过，完整仓库全套未运行。本地1366/768/390原生侧栏进入厨房→邀请→偷吃真实余料→存读→原生过夜→第二次练习/步骤记忆→再读、同日次数、拒绝不惩罚/不强移/存读、中英文纯显示、无溢出和页面异常通过；1366额外原生盐糖及随意加料四结果验证。初次浏览器选择器撞到楼层图同名快捷入口，已收窄到实际侧栏，完整三屏重跑通过，未把初次失败称为通过。

练习/邀请成功后保持面板展开，普通厨房操作保留。另顺序回归三屏原营养循环/人物饮水/死者隔离、厨房书籍制作和更新日志。六张learned/refused截图与verification/b07-cooking-191-results.json随源包。此为XVII子项完成，不是全食堂所有来源/稀有度/社交效果与全部历史扩展完成；正式美术、原世界/房间/俱乐部等统一验收及真实公网AI仍按原完整目标推进，整体active。保护剧情/route/ending/flags及11原CG保持，无真实档/.env/密钥读取上传，无付费AI测试，配音由用户后续提供。

0.13.191证据口径补充：20次Core练习使用合成的逐日日期与补充库存，不冒称20次自然过夜；真实浏览器另走原生过夜与第二次练习。

0.13.191追加语言验收：新增十种步骤记忆使用统一原文保存并注册精确英文映射；真实浏览器在英文下完成第二课，再切中文与刷新，记忆内容不被翻译改写，显示随语言正确切换。发现此项后修复并重新验收，最终运行回执见下。

0.13.191兼容补充：读取层只对这十个新增料理记忆ID、且精确匹配既定英文措辞时规范化原文；日期、次数和练习记录不变，其他受保护/自定义记忆不改。最终修正后25个相关文件与三屏完整学习流程重新通过。


### 0.13.191 最终公开验收（2026-10-18）

运行提交7c8e962c1a349fa54227532d95f10e791e62ac41，index blob a9f4d6a23648bc8b8b0f7413c00c4ca6b09e8435，Pages 39137551687 completed/success。公开地址 https://stepono927.github.io/Stephen/?release=0.13.191&build=2 。最终语言兼容修正后25个相关单元文件通过；公网四个顺序浏览器脚本全部终态exit0，1366/768/390原生邀请/实际料理/食材与品质/原生过夜第二课/英文创建步骤记忆→中文→刷新、拒绝不强移不罚分、人物营养/饮水/居民付费供餐/死者隔离、书籍制作与更新日志通过。公开index、完整74节索引和11原CG共13文件逐字节一致，保护剧情及原存档结构保留。前一候选6570bee已被记忆语言修正替代，不能作为本批最终运行回执。

用户所指整批55件异常物品追加实测：4个相关单元通过；本地与公网三屏原生目录4页/55件、25件地下市场实际渲染器和原生入口通过，模型身份/可见画框/无裁切、中英筛选与存档无变化。市场修正使用同一标准模型和归一画框，不冒称本批重做55份新美术，造型质量仍可继续针对实际反馈调整。证据并入verification/b07-cooking-191-results.json。

本批完成料理学习子项和已知模型预览修复，未称完整历史目标完成；完整食堂来源/稀有度/社交、正式美术、原世界/房间/俱乐部全条款及真实公网AI仍待继续，目标active。无真实档/.env/密钥读取上传及付费AI测试。


## 0.13.192 · 好奇动物的真实日常互动（2026-10-18，本地验证，待公开）

对照GENETICS EXPANSION PART XII发现CURIOUS此前只有围栏离开风险，没有更容易互动的正向作用。本批修复实际HomesteadEvents每日观察：原18%分支、原候选顺序/随机抽取和无好奇时RNG逐项保持；原抽签位于18%至24%时，仅从八个已有命名/新来/饱食/家谱日常互动中挑选符合条件的CURIOUS个体。临床、故障、离栏、过期产物等不进入额外池，不凭空制造状态、疾病、产物或奖励。健康至少60、饥饿/压力低于65、非检疫、无活动疾病、非离栏/运输、Jack存活且无狩猎/旅程/梦/事件才能得到额外机会。

沿用真实原事件的名字/来源/语言阶段/父母记录条件、28日冷却、每日一次、3日保留与原选择/资源/AP/存档单次结算。好奇读specialTraits，即使temperament不同仍生效；不补发旧性状，不重抽基因/待产种子/亲本/旧事件，原围栏风险保持不改。遗传实验室三级后在原性状面板解释实际作用，中英同步。

19个相关单元文件通过，包含原100事件/200结果的真实Engine分支、生产/成长/繁育/疾病/旧档/继任与Claude保护文本；源码HTTP459资源通过，完整仓库全套未运行。4096对相同控制种子的真实观察：普通750，好奇1002，额外252；所有原18%分支结果及RNG完全一致，不冒称自然世界长期分布。普通真实farm:buy世界seed2可获得CURIOUS；真实Engine rest种子774553834产生farm_case_named_calm并存读一致。八种日常的来源/阶段/名称/家谱条件均逐一检查。

本地三屏1366/768/390原生休息过夜→真实好奇观察→双语纯显示→刷新→原生选择扣原成本→消失/再次刷新保持单次，已通过。首次测试因夹具包装丢失options、以及误关闭语言切换已保留的details读取空文本而失败，均修正测试后完整重跑；没有放松状态/文字/存读断言。截图verification/homestead-curiosity-192-宽度.png、精确源码哈希和测试范围在verification/homestead-curiosity-192-results.json。

本批为CURIOUS条款真实实施，不将它替代整套动物/植物遗传链、其余历史世界/房间/俱乐部/食堂/正式美术及真实公网AI的未完成范围；整体目标active。未读传真实存档/.env/密钥，无付费AI，保护剧情/route/ending/flags和11原CG保持。

0.13.192回归补充：旧homestead-traits-browser曾在未达三级时断言性状可见，并遗漏0.13.189已存在的新购特征。修正隔离夹具为三级、预期使用现行真实marketTraits后，原生购买/照料/存读完整断言保留；没有降低实际游戏查看门槛。

0.13.192后续核对入口：原GENETICS EXPANSION PART XVIII的五个动物异常性状，当前homestead代码引用集中在model/traits/UI；故事revision/player中的同名Host线索属于另一系统，不能作为动物行为完成证据。下一批需核对真实获取、观察触发和保留旧候选/运输/怀孕种子的接入方案，现未标为完成。


### 0.13.192 最终公开验收（2026-10-18）

运行提交2bb0d72c749848f8c47c9269da21e51937f04968，index blob b94e25a0f61ee7d60f7f57e46092da4561b1dd8f，Pages 39138961500 completed/success。https://stepono927.github.io/Stephen/?release=0.13.192 公网顺序四个浏览器脚本终态exit0，1366/768/390：原生休息→真实好奇观察、相同个体/原选项、双语纯显示、刷新、原生成本结算、清单消失/再次刷新单次；原故障观察/原生购买优质乳性状/照料/存读与原生更新日志通过。公开index、74节规格索引和11原CG共13文件逐字节一致。

19相关单元文件通过（包括原100养殖事件/200结果），源码HTTP459通过；新增八种日常条件逐一覆盖，4096配对观察普通750/好奇1002、额外252，原18%选择/RNG完全一致。真实购买与真实Engine过夜可达，不将受控种子样本称为自然世界长期分布。完整仓库全套未运行，原始全部历史目标仍active，动物异常表现等后续缺项未删。验证与精确源码哈希见verification/homestead-curiosity-192-results.json；三屏截图随包。旧档无新必填字段，原事件、动物基因/待产种子/亲本保留；不读传真实存档/.env/密钥，不调用付费AI。


## 0.13.193 · 动物世界表现与照料随记（2026-10-18，本地已测，待公开）

对照GENETICS EXPANSION PART XVIII，五种动物异常性状此前仅字段/标签。本批HomesteadAnomalies接入实际farm:care陪伴：出生登记日期/季节不一致、听诊移开后迟到波形、避开金属水槽倒影、毛尖静电吸纸屑、年龄登记相差一天。只生成普通照料随记，不弹异常告警、不新增任务/疾病/战斗/产出数值，也不修改真实年龄/成长/寿命/基因。沿用原陪伴1AP、经验/压力/亲近变化；额外随记不多收费、不用RNG。需实际栏舍，一天最多新增一条，最多16条、显示最近4条；重复陪伴仍按原规则花费，但不重抽随记。

新野外ANIMAL候选显式保存anomalyVersion1；只有新候选中的异常苍白牛从五项固定一项，新俱乐部静电兔在中奖生成时固定STATIC_FUR。不是在查看、领取或读取时重抽；真实捕获、预留运输、返场和检疫/归属限制沿用，所有权未确认不能交易。旧无标记的v1-v4候选/运输、旧个体与已生成奖励不补发性状、不删换原特征；已保存基因/健康/亲本/待产种子不改。新增可选careObservations严格读取日期/当前性状和真实年龄差；不合格记录忽略，旧缺字段不创建。五种动物表现与同名故事Host seed分属各自系统，不修改保护剧情。

28个确实存在的相关单元文件通过：五项实际候选→exp:choose捕获→运输存读→真实exp:advance返场→安置→farm:care，五个可达种子分别31390/55010/79023/140258/646529；原11项野外场景回归、俱乐部真实异常奖、遗传旧结果/100养殖事件200结果/生产/安全/继任/Claude保护文本均保留。源码HTTP460资源通过，完整仓库全套未运行。25个受控日期的原care记录函数验证16条上限，未冒称25次自然过夜。首次单元载荷误写对象，已按现有远征字符串协议修正测试并完整重跑。

本地1366/768/390逐一原生操作全部五项：捕获→运输刷新→返回→栏舍安置→陪伴→照料随记→纯中英切换→刷新→再次陪伴，同日只一条且实际基因/年龄不变，无页面异常/横溢出。verification/homestead-anomalies-193-宽度.png与精确源码哈希/证据JSON随包。不把受控五次场景当自然长局触发概率验收；完整原始大目标仍active，其他遗传链/世界/房间/俱乐部/食堂/正式美术/真实公网AI未删改。无真实档/.env/密钥读取上传，无付费AI。

0.13.193后续已定位：原GENETICS EXPANSION PART XII写明HARDY提高环境耐受；当前traits.resistance有该性状的疾病风险作用，但traits.environment的冷热/污染损耗尚未读取HARDY。下一批需补真实环境效果、保留DISEASE_RESISTANT旧别名的既有疾病含义，并验证旧动物/实际日结，而不能把临床抗性当作环境耐受完成证据。


### 0.13.193 最终公开验收（2026-10-18）

运行提交8040ecf07d779866a7b87fe09ec0088e2a69c498，index blob eb31bf3c9893336ffd6062e5e8b5e0c497f67572，Pages 39140163231 completed/success。https://stepono927.github.io/Stephen/?release=0.13.193 公网顺序五浏览器脚本全部终态exit0：1366/768/390各自完整执行五种实际捕获→运输刷新→真实返场→安置→陪伴→随记→中英切换→刷新→重复照料不重抽；原野外运输、真实俱乐部异常轮盘/跳过/固定中奖个体/待领取/实验室单次交接、好奇真实过夜及原生更新日志均通过。公开index、完整74节规格索引及11原CG共13文件逐字节一致。

28相关单元文件全部通过，精确清单和源码哈希在verification/homestead-anomalies-193-results.json；源码HTTP460资源通过。没有改原基因/真实年龄/成长寿命/生产或原照料消耗，旧候选/运输/已生成奖励不补发或重抽，新增可选随记不影响旧字段。25个受控照料日期用于验证16条上限，不冒称25次自然过夜。完整仓库全套未运行，所有历史大目标仍active；五种动物表现不等于同名故事Host系统的变更。三屏截图随包，无真实档/.env/密钥读取上传或付费AI。


## 0.13.194 · HARDY环境耐受（2026-10-18，本地通过，待公开）

原GENETICS EXPANSION PART XII明确HARDY提高环境耐受，先前仅临床resistance生效。本批canonical HARDY实际减少15%的冷热/牧场污染健康损耗和冷热压力增加，幼畜低温损耗同样减轻。减损在原环境健康损耗2点封顶之后进行，极端组合仍能生效且不免疫；原COLD_HARDY/HEAT_HARDY/POLLUTION_TOLERANT/FRAGILE/ROBUST/ELITE_RESILIENCE与体质换算继续按原机制组合。正常环境0损耗不会变成回血，老年损耗不变。

不复用has别名给旧DISEASE_RESISTANT加新环境收益；旧别名仍保持原15%疾病风险减免，canonical HARDY也保留原疾病作用。原基因/获取概率/出生池/孕期种子/亲本快照均不变，旧损伤读取不会被自动恢复。UI将canonical HARDY中文纠正为“环境耐受”，旧耐病别名仍叫耐病；遗传实验室三级后说明实际15%作用，中英同步。没有新增存档字段或更改旧性状ID。

23个确实存在的相关单元文件通过，源码HTTP460资源通过。2304个体质/温度/污染/栏舍/其他性状组合，幼畜安全保温/无免疫/原封顶后减损及全部原临床风险/别名/无基因变化验证。冷热污染各12次共36次真实HomesteadDaily日结使用受控高随机值隔离感染，不冒称自然世界长期平衡；另三种天气通过未替换随机的真实Engine rest，健康普通/HARDY/旧别名分别69.75/69.9/69.75、69.75/69.9/69.75、70/70.1125/70，真实气温-14/43和牧场污染90。

真实普通购买世界种子37(母)/51(公)获得HARDY；实际配种种子1、保存的遗传种子270369、逐日日结出生farm_3，真实父母编号和后代减损/存读通过，没有用手工塞入性状代替来源验证。原遗传1056旧结果/孕期快照、幼畜/成长/生产/医疗/气候/继任及Claude保护文本回归通过。完整仓库全套未运行。首次单元夹具保护期1000超出既有day+30限制，修为合法day+20，未弱化读取规则。

本地1366/768/390九次原生暴雪/热浪/污染牧场休息，实际饲料3份、健康和冷热压力差值、旧别名不加环境收益、完整英文说明无汉字残留、菜单/语言纯显示与刷新保存均通过；原生优质乳购买/照料/存读、幼畜真实休息消耗奶料与成熟离开育幼页、更新日志顺序回归通过。verification/homestead-hardy-194-宽度.png与精确源码哈希及测试清单随包。没有改保护剧情/route/ending/flags或11原CG，无真实档/.env/密钥读取上传，无付费AI。

本批只完成HARDY环境条款，完整动物/植物遗传链、其余历史世界/房间/俱乐部/食堂/正式美术/真实公网AI仍在原目标中，active，不以本批通过替代全部验收。

0.13.194后续来源审计：原规格FINE_WOOL、LONG_LIVED、SHORT_LIVED已有产出/寿命作用和允许字段，但当前founder、固定birthPool、marketTraits及其他已检查生成入口尚未提供这些性状的自然获得链；默认继承只保留亲本已有特征，不能把允许表或手工夹具当可获得。后续需补自然来源、真实继代与旧待产/运输/已生成奖励不重抽的证明，原条款仍未标完成。

0.13.194说明文字收尾：本批玩家更新日志改用“环境耐受”和旧版“耐病”等中文名称，不展示内部字段名/亲本快照/随机种子；开发验收记录仍保留技术证据。性状运行源码与已通过23单元的版本一致，重新构建后对最终公开包验证。

0.13.194后续寿命一致性核对：HomesteadModel.stage仍以物种原始lifespan的75%标记OLD；实际死亡、oldAgeLoss与繁育年龄窗口已经按LONG_LIVED/SHORT_LIVED调整寿命。自然来源补齐时还须统一阶段显示与真实衰老窗口，保留原日龄/健康与旧存档，不把有标签但阶段不一致算作完整寿命特征。


### 0.13.194 最终公开验收（2026-10-18）

最终运行提交2d90bc8dd8b2687f3e3d86d03327e565489a96ff，index blob bd7aa96936d825e773adb5bfd2e984832154a1fd，Pages 39141700176 completed/success。https://stepono927.github.io/Stephen/?release=0.13.194&build=2 公网顺序四浏览器脚本全部终态exit0，1366/768/390原生暴雪/热浪/污染牧场过夜、精确原饲料消耗、健康/冷热压力减损、旧耐病别名保持临床含义、完整中英说明/纯显示/刷新、旧性状实际购买/照料、幼畜真实休息奶料与成熟离页、原生日志均通过。公开index、完整74节索引与11原CG共13文件逐字节一致。

23个相关单元文件通过；2304个环境组合和36次受控日结、另未替换随机的真实Engine天气过夜、真实购买HARDY父母→保存孕期→逐日出生→后代作用/保存，证据范围按上文与verification/homestead-hardy-194-results.json精确区分。源码HTTP460资源通过，完整仓库全套未运行。最终仅收尾本批面向玩家的中文说明，环境运行源码与23单元通过时一致；首轮候选81cdc2已被说明收尾版替代。三屏截图随包，旧档不自动回血，不改基因/原种子/保护剧情/route/ending/flags，11原CG保持，无真实档/.env/密钥读取上传或付费AI。

这是HARDY环境条款完成，未称完整历史目标完成；三种自然性状来源及寿命阶段一致性等已记录具体后续缺口，原始全部范围仍active。


## 0.13.195 · 三种自然性状来源与真实寿命一致性（2026-10-18，本地通过，待公开）

对照原GENETICS EXPANSION，本批补齐FINE_WOOL、LONG_LIVED、SHORT_LIVED的实际普通供应点新购来源，非手工夹具授予。沿用原派生获取随机值，不额外推进世界RNG；原前10%寄生抗性/后10%食欲不佳区间保持，之后5%长寿、5%短寿、仅产羊毛物种的10%优质羊毛候选；四性状满时不再增加，不给已有相反寿命性状的新个体硬塞另一个。新生成的普通供应动物才调用此函数，旧个体、读取、已生成商队/拍卖/俱乐部/运输记录不补发或重抽，原M.individual、出生池、旧孕期种子及亲本快照不改。自然后代可以按原遗传规则保留亲本已有性状。

新增共享lifespan计算，保留既有长寿×1.15、短寿×0.8与同时存在时相乘的含义，统一Model.stage、实际oldAgeLoss、繁育年龄窗口、日结死亡（含离栏个体）。过去阶段以物种原寿命75%标OLD，导致长寿过早老年/短寿阶段太晚；现在与实际寿命75%一致。日龄、基因和已存健康不改，不复活旧亡者/不延后已经记录的离开。不是只改标签：真实日结同龄普通/长寿/短寿的恢复与衰退结果59.756875/60.75/59.41796875。

优质羊毛沿用真实羊毛品质+10、产量不变和品质100上限；现在其来源真正可达。遗传室三级后以“优质羊毛/长寿/短寿”中文说明实际效果，并显示个体自然寿命与老年起始日龄，不新增杂乱面板。玩家更新说明无内部种子/字段用语，开发证据保留具体数据。

36个确实存在的相关单元文件通过，包含已生成商队/拍卖/官方G3与G4/档案挤出家谱、原收益评价/血统命名/付费核查、旧遗传1056样本、孕期、植物遗传对照、生产/医疗/继任/Claude保护文本；源码HTTP460资源通过，完整仓库全套未运行。实际购买世界种子：优质羊毛母58/公57，长寿母34/公32，短寿母61/公63；三类实际配种seed1→保存遗传seed270369→逐日出生farm_3、父母编号/原料成本/后代作用/存读通过，不以允许表代替来源。

10000羊样本+10000山羊对照为覆盖32位的受控派生种子，羊长寿511/短寿474/优质羊毛991、山羊不出现优质羊毛；并非20000次自然玩家交易，不冒称全世界长期平衡。168个物种/寿命性状边界、亡者和送出个体的日龄冻结、真实到寿死亡归档且不自动给肉；六次受控真实日结比较同一已购羊的FINE_WOOL有无，品质恰+10、产量/日期/来源保持。初次采样连续小种子偏差及健康50不足生产门槛导致测试失败，改用覆盖序列与合法健康70/卫生70夹具，未改概率或削弱原生产门槛。

本地1366/768/390原生完成三种购买/纯双语说明/刷新，优质羊毛真实休息（按实际游戏照料和事件处理）→生产→出售→刷新；保留真实购买个体身份/基因，用合成年龄边界验证长寿PRIME/短寿OLD，再走原生休息与保存，不冒称自然活过完整寿命。原优质乳实际购买/照料、幼畜奶料与成熟离页、更新日志顺序回归终态通过。截图verification/homestead-lifespan-195-宽度.png和精确哈希/测试清单随包。

完整原始动物/植物遗传、世界/房间/俱乐部/食堂/正式美术/真实公网AI及其他历史目标仍active；本批不是全部完成。无真实档/.env/密钥读取上传，无付费AI；保护剧情/route/ending/flags和11原CG保留。

0.13.195后续性状审计入口：ARCHIVE_LINE、PERFECT_TEMPERAMENT、AGGRESSIVE目前在已检查的畜牧代码中主要是允许表、显示、价值/压力作用或继承保留；普通创始性格仍只有四类，现有新购/出生新增池没有这三项的起始来源。下一批核对真实来源与档案血统证据、极优性格的行为效果和好斗性格的实际互动，不能把已有字段或stress数值当成所有原始性格要求完成。原范围保留。


### 0.13.195 最终公开验收（2026-10-18）

运行提交5d8d1b3c79047a91a557c4cc455a4e86353f8cc8，index blob 4652bcc2a2365c7af56483e61d2c363caa1f4994，Pages 39143324723 completed/success。https://stepono927.github.io/Stephen/?release=0.13.195 公网顺序四浏览器脚本终态exit0：1366/768/390真实购买三种性状、完整中英作用说明/纯显示/刷新、优质羊毛原生休息/实际产物/真实出售价格与扣数量/刷新，已购个体身份基因保留的合成年龄边界+原生休息验证长寿/短寿阶段；旧优质乳购买/照料、幼畜实际奶料与成熟离页、原生更新日志通过。公开index、74节完整索引与11原CG共13文件逐字节一致。

36相关单元文件通过，精确清单、源码哈希、实际父母来源与孕期/出生证据在verification/homestead-lifespan-195-results.json；源码HTTP460资源通过，完整仓库全套未运行。10000羊+10000山羊为受控来源样本，168物种/性状阶段边界及实际日结/归档不等于自然长局平衡；三类真实购买父母→保存孕期→逐日出生→后代作用/存读已各自证明。原基因算法/出生池/已保存亲本与种子保留，旧个体/已生成运输和奖品不补发或重抽；寿命改动不改实际日龄和已存健康。三屏截图与代码随包，无真实档/.env/密钥读取上传、无付费AI。

本批完成三项自然来源与寿命阶段一致性，不冒称完整历史目标完成；稀有血统/性格来源及其实际行为等后续缺项仍按原始范围继续，整体active。保护剧情/route/ending/flags和11原CG保持。


### 0.13.196 · 整批55件异常小物复查（2026-10-18）

用户确认问题指整批55件。本批没有把55个唯一ID当作55件造型合格：新增每件明确实体部件核对表，逐件比较图鉴与25件地下商店的实际模型；已有55件实物网格保留，本批实际改造1件空瓶的材质/瓶颈。空瓶改为透明玻璃瓶身、中空瓶颈，保留实体瓶口和单独瓶塞，不借用雨瓶液体。房间碰撞尺寸、旧摆放、四向旋转、库存和剧情不改。

9个相关单元文件终态通过，含55身份部件、220旋转、旧尺寸迁移、异常收存/选择、地下交易、保护剧情与源码HTTP460资源。新测试初次因VM跨realm数组原型比较失败，改为宿主Array.from后通过，未放宽身份覆盖。完整仓库全套未运行。

本地四浏览器脚本顺序通过：55件图鉴四页及25件商店预览在1366/768/390宽度核对名称/网格/完整取景/中英切换/不改隔离测试档；另55件图鉴/房间全景、32放大旋转截图与更新日志通过。全55截图已人工检查，不代表所有正式美术已达最终审美要求。没有读取真实玩家档/.env/密钥，没有付费AI。

公网发布验证通过，见下方本批最终回执。其余大型扩展与正式美术仍按原目标继续，不报告整体完成。


### 0.13.196 最终公开验收

运行提交3a924bd918c7ee7860a491aa04e98fd4f6ea42b5，index blob c50622be60876b476ac975788415050224ce6ce3，Pages 39144378943 completed/success。公网顺序四浏览器脚本终态exit0；1366/768/390图鉴55件四页、商店25件真实预览、名称/模型对应、中英切换、菜单更新日志和隔离档不变通过。55模型房间/图鉴及32放大旋转也通过。公开index、完整74节索引和11原始CG共13文件逐字节一致。

本批实际修改空瓶透明材质和中空瓶颈，55件身份逐项复查；不冒称55件都重新设计或正式美术全部完成。详见verification/anomalous-identities-196-results.json和55件截图，9单元文件通过，完整仓库全套未运行。原始历史目标仍active。


### 0.13.197 · 稀有血系与性格真实来源（2026-10-18，本地验收）

对照原GENETICS EXPANSION的AGGRESSIVE/ARCHIVE_LINE/PERFECT_TEMPERAMENT：补齐正常获取来源，非只添标签。新普通供应点在原派生随机流0.4–0.405区间、原沉稳且无紧张/好斗时可有极优性格；0.405–0.445区间、原非沉稳且无沉稳/极优时可有好斗。并非所有动物无条件0.5%/4%；四性状满额不再加，原0–0.4五类来源及全局RNG抽数保留。20000受控山羊样本实际极优16、好斗580，不当作自然长局掉率实证。原工厂/出生池不变，旧动物/运输/奖励不补发。

新日落商队认证来源v2，在六份真实祖代链的创始记录有空位时加入档案血系，再由原遗传算法实际传到G2/G3。付款凭证v2保存现有动物和六祖代；旧凭证v1继续按原数据读取，默认specimen仍v1，新offers才用v2。128组对0.13.196源码模块的每字段旧生成/读取对比一致；256组新来源/凭证可读，四性状上限及祖代验证保留。档案标签不等于已核验、优秀基因或更高物种稀有度。

极优压力每天额外−2，好斗同栏额外+2的原实际日结保留并双语说明；孤立/饥饿/疾病/环境仍生效。普通性状三级、隐藏性状五级显示限制不变。测试实际购入雌雄父母→真实配种→保存孕期→逐日出生→保存后代，三类均成功；档案系额外经真实商队交接、兽医评估/解除隔离、购买普通雄兔，诞生G4且实际家谱一致。

30相关单元文件终态exit0，名单与源码哈希见verification/homestead-rare-197-results.json；源码HTTP460资源、100农场事件/200选择、原遗传1056基线/植物对照、保护剧情通过。完整仓库全套未运行。初次新测试仅因隔离测试资金300000不足真实报价337355，已设为1000000，原价格/门禁不改。

本地三屏新浏览器脚本已完成真实极优/好斗购买、原生休息/刷新、中英文说明，以及认证商队付款→保存队列→原生返回→原生休息→唯一动物交接，六份祖代/原基因保留；原羊毛寿命/更新日志两脚本也已三屏终态exit0。手机截图已查看。好斗实际攻击互动仍未实现，不将当前压力效果冒称完整攻击行为；全遗传链、植物/食堂/俱乐部全条款及其余历史目标仍active。无真实玩家档/.env/密钥读取上传、无付费AI。


### 0.13.197 最终公开验收（2026-10-18）

运行提交dac378941fe1c4e192ad74be8f01a32765f9c4be，index blob 27accb79e5b0b807a3a29bd899a980403732c6ab，Pages 39145668252 completed/success。公网顺序三浏览器脚本exit0：1366/768/390真实极优/好斗购买、中英文作用、原生休息/刷新；认证血统付款→保存运输→原生免费返回实验室→原生休息过夜→唯一交接，档案性状、原基因及六祖代保留；旧优质羊毛实际休息/产物/出售、长短寿合成年龄边界及原生更新日志均通过。公开index、完整74节验收索引和11原CG共13文件逐字节一致。

30个相关单元文件终态通过、七份最终源码/测试/原版fixture哈希与详细边界在verification/homestead-rare-197-results.json。128组旧模块逐字段生成/读取、256新凭证、20000受控来源样本不冒称自然长局平衡。三类真实来源→父母或商队祖代→玩家出生后代/存读均验证，档案系G4家谱一致。完整仓库全套未运行；好斗攻击互动和全部原始历史目标仍active，不报告整体完成。无真实档/.env/密钥/付费AI访问。


### 0.13.198 · 好斗动物真实同栏冲突（2026-10-18，本地验收）

继0.13.197正常来源/遗传之后，补原AGGRESSIVE“易攻击”的实际行为。新增独立HomesteadConflicts，不挤掉原100养殖事件/200结果。仅实际同栏、非运输/离栏/检疫/离世、非群落、成年且健康至少50、无活动疾病或怀孕的双方可进入候选；好斗方压力≥40、饥饿>60或同栏空间>85%才有机会。每日全场只选一对并做一次机会判定，最高20%；实际造成同伴2点身体伤害（按体质生命储备换算健康百分比）、同伴压力+4、发起方+2。原临床伤情/基因不被替换。

每个游戏日最多一次，同一发起方7日、同栏3日冷却。真实喂食挡板花4木材/1AP并持久减半该栏机会；1AP把原个体移入足够容量的现有空栏；1AP安抚严格走原care的−12压力/+5经验/+5熟悉，不另发奖励或恢复同伴健康。三日内限一次处理，缺资源/无空栏/条件变化/重复指令原子拒绝。已受伤低于50仍允许保护处理，不能把新的伤情变成按钮死锁。

可选conflicts字段只在有实际机会或记录时创建，最多30条历史和20个栏舍挡板；读档不重放伤害/扣费/移动，坏记录局部丢弃、原动物保留。历史缺失日程补算不生成新事故，仅新推进的当前日有机会；无合格动物不增加RNG抽取或旧字段。归档/死亡后保留历史而不重生动物。

26个实际存在的相关单元文件终态通过，原100事件200选择、临床/护卫/运输/继任、原遗传与稀有来源、保护剧情及源码HTTP461资源通过，完整仓库全套未运行。4096配对机会对照原423/挡板210（非自然长局平衡）；实际日结无强制随机种子2027808452、完整Engine原生休息种子3668339987均触发真实伤情。

本地浏览器最终三屏（1366/768/390）实际原生休息→冲突→分别点击挡板/分栏/安抚→实际资源/原伤/基因身份/一次结算/刷新通过；原稀有来源和更新日志脚本也已顺序三屏终态exit0。手机截图已查看，按钮未互相覆盖。早期英文新句被模板拆成中英混排，已改为独立完整短句节点并明确登记三种处理结果；处理前后均测纯英文。初次伤情测试未标已结算日导致正常日结恢复，修正隔离夹具时戳，生产恢复规则未改；首轮测试清单发现错文件名预检即停，改为实际homestead-raids后26文件才算通过。

本批补好斗实际冲突与处理，不代表完整动物/植物遗传、俱乐部74条、食堂/27房间、世界社会梦连续性、正式美术或公开AI均已完成；全目标仍active。无真实玩家档/.env/密钥读取上传，无付费AI。


### 0.13.198 最终公开验收（2026-10-18）

运行提交98df4a73ab4e4ef9cc42502e9efcebd122bb7bfa，index blob 27c145b2b3ec6c160e6d7d1e0a5da5f8c0de85eb，Pages 39147142669 completed/success。公网三脚本顺序终态exit0：1366/768/390原生休息触发实际购入好斗动物的冲突，分别点击挡板/空栏分开/按原规则照料，真实扣费、原伤不自动恢复、基因身份保持、一次处理、结果存读和处理前后纯英文通过。旧稀有性格购买/商队六祖代付款→原生返回→原生休息交接，以及原生更新日志三屏通过。公开index、完整74节索引和11原CG共13文件逐字节一致。

最终26单元文件通过，源码HTTP461资源；11份最终源码/夹具/测试哈希、4096对照机会423/210、两个未强制随机的完整日结/原生休息种子和边界在verification/homestead-conflicts-198-results.json。旧档无记录不补发伤害，历史补算只在新推进当前日评估；受伤低于候选阈值仍可保护处理。三屏截图随包。完整仓库全套及自然长期平衡未运行，不把局部结果夸大为全部历史目标完成；整体active。无真实档/.env/密钥或付费AI访问。


### 0.13.199 · 留种再杂交来源断链修复（2026-10-18，本地验收）

对照原GENETICS EXPANSION的植物杂交/品系parentLines与留种继承：实际缺陷是breed只取a.cultivar||a.plantId，漏掉a.seedLot，导致G2留种植株再杂交把来源写回基础物种。本批仅新杂交改为seedLot→cultivar→普通种源优先，旧parents/parentLines不改写。新有完整五轴的杂交加入可选crossRecordVersion:1及两株crossParents，记录实际uid、来源、代数、当日健康/基因/性状/扫描资料与捕获日；取的是原扣3健康后的实际育种输入，不额外抽随机数或消耗资源。

新快照严格核对两株不同个体、来源/亲本ID、出生代数、日期、基础物种与原兼容组；历史族群杂交读取不因当前研究等级降低而丢失。损坏快照局部丢弃但保留版本标记/种子/基因，报告INCOMPLETE/旧报告stale；不补造原记录。新快照纳入来源指纹，后续实际亲本恢复不改写冻结数据，也不会让旧报告误过期。旧无标记记录及旧来源报告指纹保持原义；普通种源不被冒充外部认证。

种子库增加默认折叠的育种时亲本快照，保留遗传实验室显示等级；两条实际留种批次归档后仍可追踪。22相关单元文件终态通过（精确名单/源码哈希见verification/plant-cross-199-results.json），包含64组原0.13.198源码模块的基因/性状/RNG/AP/研究点/亲本健康对照、真实G1日结→G2留种种植/日结→G3杂交→归档→杂交种植/日结收获→G4登记五记录遍历、坏快照不毁档/报告过期、原5000历史容量、200物种800生理基线/遗传效果、成就新闻、保护剧情与源码HTTP461资源。完整仓库全套未运行。

新浏览器已首次三屏通过原生种植/浇水/休息（成熟度未直接改写）、杂交实际1AP/15研究点、两来源归档、双语快照与刷新、G3种植/休息/收获→G4登记五记录追踪；最终兼容性校验版四浏览器脚本也已三屏顺序终态exit0。G1来源夹具由真实Garden日结/收获生成，非完整世界长期自然局，不把这条链当作所有200植物和全部遗传条款已完成。手机截图已查看，面板默认折叠，未遮挡控件。首次浏览器测试修正为只点外层summary（另两项是嵌套基因标题）；长流程使用基础口粮照料而非尚未开放的凝胶，未放宽科技门槛。

全原始历史目标仍active，其他植物条款/俱乐部74条/食堂/27房间/社会梦连续性/正式美术及公开AI仍逐项验收；不报告整体完成。无真实玩家档/.env/密钥读取上传、无付费AI。


### 0.13.199 最终公开验收（2026-10-18）

运行提交a042651a2e959fcac926218e62d115f22bf19c9c，index blob c831f7bb9266e6213319ef76dd3b4f3398511ab1，Pages 39148749314 completed/success。公网四浏览器脚本顺序终态exit0：1366/768/390真实留种G2植入→原生浇水/休息生长→实际杂交1AP/15研究点→两源批次归档/亲本快照中英/刷新→杂交种植/原生生长/收获→G4登记五记录追踪；未直接改写成熟度。旧留种普通收获/G3登记/5000历史容量、旧品系分析原生1AP/重复拒绝/祖代变更过期、更新日志三屏通过。公开index、完整74节索引和11原CG共13文件逐字节一致。

最终22相关单元文件终态通过，源码HTTP461资源；8份最终源码/夹具/测试哈希、64组0.13.198原模块对照、坏快照不删种子基因/报告过期和旧无快照记录保留，在verification/plant-cross-199-results.json。G1来源为受控真实Garden日结/收获夹具，G2之后为真实浏览器原生操作；不冒称完整自然世界长期局或全部200植物全条款验收。手机截图随包。全仓库全套未运行；原完整历史目标仍active，无真实档/.env/密钥/付费AI访问。


## 0.13.200 · 55件异常物品复查与3件结构纠错（已公开验证）

用户明确指整批55件。逐件身份映射/四向几何与实际仓库核对；此次集中修正观察者相机（对焦环、光圈、透明前镜）、永亮电筒（凹面反光杯、独立灯珠、透明镜片）、食盐心脏（弯曲中空主动脉和分支）。真实近景检查另发现反光杯/光圈面朝向错误，已修正并增加实际相机可见检查。未修改道具ID、故事、数量、价格、稀有度、获取概率、碰撞尺寸或存档字段；不声称55件正式美术全部完成。

本地6个测试文件及最终公网三屏仓库检查均通过，发布与资源一致性已验证。其余历史大型扩展与整体验收仍欠。


### 0.13.200 公网回执（2026-10-18）

- 运行代码：`2c3aadc187bc4eb788db943ef605cc086d0c424c`；公开 index blob：`390ea19e62a85cc97a8838beed8a88e64d8be7a3`。
- GitHub Pages：39150664666，completed / success。
- 最终本地6个单元文件通过（模型4项、保护剧情、461个源码资源）；公网1366/768/390三屏四页55件仓库、中英过滤与测试档不变通过；55模型/32放大旋转检查通过。
- 公开index、完整74节Happy Club规格索引及11张CG共13文件与安全发布目录字节一致。
- 3件结构修正，不是55件新建模或全套正式美术完成。其余历史工作与公网AI仍按原清单继续。


## 0.13.201 · 普通轮盘奖品满库存保留（已公开验证）

确认原代码在资金10000000、材料1000000、每种种子100000、每种药剂1000000、每种变卖物10000000上限时截掉奖励或存读截断。新增可选wheels.pendingStock v1按真实奖品ID保留溢出数量，总暂存上限1000000000；没有溢出/旧档缺字段时不生成，不从历史中奖记录倒推补偿。原容量不变。

五种普通奖品及重复装扮/壁纸/满仓车辆备用件转换的材料共用此保留机制；不是替换已有武器实体副本、动物、速食、用品、壁纸收藏写入和陈设暂存。抽奖前保守预留每次250单位最大可能空间，暂存不足时不扣Token、不推进RNG/序号/保底。

在俱乐部或实验室物资仓库按空位部分领取，每次最多10000单位；无额外费用/抽取/RNG/AP，不会被同次自动观察再次领取。普通返回实验室后的有效操作可自动转入空位。非养成/外出/进行中的挑战或事件不领取。原生浏览器发现靶场动画每帧重建新暂存DOM，已以状态键缓存修复。

新增测试实际抽到五种满仓奖品；覆盖全部普通奖品ID、重复补偿、旧档默认缺省、部分/10000上限、上下文/容量原子拒绝、真实Engine存读与256组原代码结果/RNG/保底比较。完整74节终验和其他历史欠项仍未完成。最终公网回执另记。


### 0.13.201 本地最终验证

27个实际测试文件全部通过：23个俱乐部测试加2个靶子安全、保护剧情与462资源HTTP。专项覆盖200种种子、75种药剂、150种变卖物全部425种普通奖品ID的真实暂存/存读；256组旧代码奖品/RNG/保底/数量一致；9000次原奖池抽取。四个浏览器脚本按顺序运行，均在1366/768/390通过：五类满仓实际抽取258单位保留、原陈设领取、原生全部兑换/跳过、菜单/更新日志。真实购票结束后领取250资金；实验室其余四类空位由隔离测试准备，再原生点击部分领取，不冒称实际消耗全部满仓物品的游戏流程。未使用真实玩家存档或付费AI。


### 0.13.201 公网回执（2026-10-18）

运行提交`2040638140fb03c2c17f529fa2620dbe4e1a23d5`；index blob `e9f5b37e1a5faf916ef8d25767d8d4d8c7c412d8`。GitHub Pages 39152215780：completed / success。公网四个浏览器脚本在1366/768/390全部通过（普通满仓奖品、原陈设领取、原生全部兑换、版本日志）；公开index/74节完整索引/11张CG共13文件逐字节一致。

实际继任、跨自动存档隔离、删除该档后奖励不残留的追加专项通过；测试使用原有合法长度名字与明确自动存档入口，不修改手动/自动存档语义。新暂存字段缺省不造奖励，原保护剧情与存档边界保留。完整俱乐部74节、55件最终美术和其他历史欠项仍继续；不将专项通过当整体完成。文件：verification/happy-club-stock-201-results.json。


## 0.13.202 · Jack独自烹饪实际失误与熟练（本地候选）

原食堂XVI/XLI要求初期可能做坏、厨艺/同菜Mastery降低失败率；此前普通cook仅用品质公式且完全不耗随机数，只有厨房实验和B07学习可能失败，不能代替Jack独自制作。本批新JackCooking用于以后普通cook：原派生厨艺0–100、同菜原Mastery0–5，失误率max(2%,22%-厨艺×0.12%-Mastery×1.6%)；每次成功开始的独立制作只消耗一次世界随机数，六种结果为顺利/烧焦/太咸/太苦/干硬/奇怪口感。

失误仍按原配方扣真实食材、净水和1AP、产生可食用餐盒且累计原熟练次数，品质取max(0,min(35,原品质-25))；成功沿用原品质公式。收益/售价/不满足60不获高级Buff均走原效果系统，不新增疾病/永久加成。新餐盒可选cooking v1保存结果与当时厨艺/Mastery/原品质；旧餐盒无字段时不添加，坏可选记录不删除/重判餐盒。继任保留Jack知识和原实体餐盒。

B07原四种练习继续走原基础装盒，不叠加Jack新失误；256组原0.13.201源码的实际练习结果/RNG/食材/餐盒/记忆严格一致。制作预检失败不消耗RNG或原料；食谱显示当前概率，Jack厨艺面板在实际操作后保持展开。

新增CANTEEN-SPEC-ACCEPTANCE.md保留47节原始规格与SHA256，未缩减全目标。32相关单元已通过，最终三屏与公网回执待完成后记入。整食堂所有来源/正式美术/其余历史目标并未完成。


0.13.202手机餐盒补充：实际截图发现旧内联餐盒说明与给B07/所选人物/出售/清理按钮拥挤，现分为语义article元数据段与可换行操作区；测试用实际DOM边界检查说明与按钮/select及控件之间不重叠，不改送餐对象和原费用。


### 0.13.202 本地最终验证

32个相关单元文件通过；最后手机卡片布局调整后另重跑Jack专项、核心料理、出售、筛选四文件通过。463个源码资源/私密路径保护通过，原保护剧情通过。2048组受控同种子新手/熟练比较失误455/44，六结果覆盖；160配方用精确真实原料/AP/水制作和一次食用、256组旧B07练习源码结果/RNG/用料/记忆完全一致，旧餐盒不补字段，坏可选记录只丢记录不丢餐盒；实际Engine保存及继任保留。未运行完整仓库全套。

最终五个顺序浏览器脚本在1366/768/390全部终态通过：Jack原生厨房→第5次练习熟练1→烧焦品质35→刷新→实际品质食用→顺利制作/品质售价→再读，B07原邀请/四结果/过夜学习/拒绝、原书架购买学习和制作、原出售、双语版本日志。新Jack浏览器初始熟练4次/食材和固定种子由隔离fixture准备，不冒称自然从零完整养成或世界长期分布；实际第5次由按钮制作。新增餐盒DOM文字/按钮/select及控件之间无重叠，最终手机截图已人工检查。
