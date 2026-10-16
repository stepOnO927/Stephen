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

验收：0.13.153本地行为与长期病程通过；公开终验见文末回执。

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
