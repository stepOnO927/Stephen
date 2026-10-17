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
