# 实验室两份规格全范围验收索引

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

验收：待逐条证明。

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

验收：待逐条证明。

Jack可以写：

MAINTENANCE LOG

例如：

“Pump 3 still sounds wrong.”

### LXXXV · 日志长期回收

验收：待逐条证明。

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

验收：待逐条证明。

提高：

early symptom detection

### LXXXIX · Greenhouse Duty

验收：待逐条证明。

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

验收：待逐条证明。

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
