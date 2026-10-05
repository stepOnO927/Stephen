## 0.11.0-preview — 2026-10-05 武器2.0与叙事分层

- 补齐69把武器体系与27把高级武器专属R1–R6；独立副本、重复获取选择、通用核、同伴、多目标、延迟队列、展示和指标。
- 新增30段生活场景、6段Jasmine日常回忆、7个Host伏笔和8个连续性伏笔；原有20章/结局保留。
- 新增六阶段语言、情绪节奏、延迟选择回响、稳定文本ID与人物声音卡；四个重复结尾分别重写。
- 新增PREEMPTIVE SILENCE及对应隐藏成就。修复独自调查通用台词重复、死亡后角色发言、章节标识缺失、剧情界面窄列、章节时间被覆盖。
- 本地与公开版继续分离；公开版只含静态游戏，不上传密钥和玩家存档。
- 程序SVG仍为占位资源，历史大规模扩展待办见TASK-STATUS.md。

## 2026-10-05 霜线与昨日：专属共鸣、战斗走位
- 霜线狙击枪加入远距强化、准备暴击、瞄准提速、可见霜线标记、标记穿甲与极远距离精准重击。
- 昨天记录独立原始命中；加入暴击记录、有限复制与一次性状态残影，不再叠加原来的两套重复攻击规则。
- 战斗加入接近/拉开距离按钮，移动耗时且允许敌人行动；原来无法主动使用的远距离机制现在可进入。
- 新触发、标记和上一击记录随存档保留，兼容旧战斗存档。剩余高级共鸣仍在开发。

## 2026-10-05 守桥人的枪：弹匣与条件共鸣
- 新增每场战斗12发弹匣、24发有限备用弹药、后坐累积和换弹控制；换弹耗时1.6秒，敌人仍可行动。
- 接入R1后坐减轻、R2首次实际交战稳定性、R3连续命中最多五层、R4低弹匣暴击、R5战斗实验体低生命短暂攻击、R6一次受重创后有限坚守。
- 空弹匣禁用射击；弹药、后坐、触发次数随存档保留，旧战斗存档兼容。坚守不回血、不免死。
- 该模块当前用于荒野狩猎；独立宠物协同及公路战斗弹药尚未扩展。武器2.0整体仍在开发。

## 2026-10-05 武器副本全流程修复
- 锻造同名副本不覆盖原件，升级和修理同步实例。
- 道路换装可选择具体副本；存档刷新保持正确装备及共鸣。
- 商队换物按具体副本估价与消耗，保护锁定/已装备武器。
- 跨代装备迁移保留多副本、暂存、升级、共鸣、耐久和永久命名方向。
- 武器2.0仍是开发版，剩余高级专属机制继续开发。

## 2026-10-05 重复武器与满仓选择
- 修复镜面飞盘R6未识别实际狙击敌人的远程回击。
- 重复获取显示保留、指定共鸣目标和确认分解；选择刷新后仍保留。
- 满仓武器安全暂存，可作为共鸣材料，也可替换未锁定、未装备的旧副本。
- 仓库手动共鸣允许选择材料；修复损坏存档实例ID碰撞与暂存ID序列。
- 武器2.0其余高级机制仍在开发，此次不宣称整体完成。

## 2026-10-05 武器2.0共鸣开发版
- 修复慢武器敌方行动时间积累与重载截断；69把武器的下一回合重载对照一致。
- 独立副本、100格仓库及满仓暂存，锁定与装备副本受到保护；共鸣真实消耗一把同名副本。
- 修复地下武器身份模块加载顺序；接入16件稀有条件共鸣和10件史诗独立机制。
- 无名工具R6命名与四种永久方向；仓库显示逐级说明、条件数值和动作时间。
- 导入保留模式并写入新槽，导出包含全局收藏，聊天按存档槽隔离。
- 此为开发版：同伴协同、电弧多目标、其余高级武器共鸣与重复掉落选择界面仍在开发，武器2.0尚未全部完成。

## 2026-10-05 武器显示修复
- 修复 AK47 缺少绘制函数，以及地下武器的剑、匕首、手枪、步枪、霰弹枪模型名称未绑定的问题。
- 发布本地69件武器；升级界面显示持有废料、材料与升级后的攻击加成，分别提示升级失败原因。
- 69件武器模型在浏览器有非零可见轮廓；实际点击升级、69件0至5级升级、存档重载及战斗测试通过。
- 附件武器2.0（独立副本、100格、R1至R6和专属机制）尚未完成，不计入本次修复发布。

## 0.10.0-preview — 2026-10-05

- 四季、30/36/45日季节长度、九区域温度与12类天气、五种预报设备。
- 持久路况、气候寻路、出发风险简报、天气耗油/损耗、慢速资源与聚落经济。
- 20件天气装扮、5处限定地点、3件异常物、4件实际需摆放的功能家具、10项成就。
- 350条情境变体记录和1个聚落两难委托，首冬记忆；不宣称350段独立长篇。
- 顶层存档仍4，climate子版本1；旧档稳定储备与7日保护，剧情模式不强制生存玩法。
- 详细边界与测试见TASK-STATUS.md；有名NPC跨聚落迁居、完整难民剧情和独立广播仍待深化。

## 0.9.2-preview — 2026-10-05

- 修复顶部研究资金与抽奖废料币混淆：可明确选择支付货币。研究资金80/800，废料币8/80。
- 收藏 → 回收抽奖：独立回收舱、扫描、余额、保底、结果卡与明确限制原因。
- 先保存结果再播放动画；共享原有概率与保底，无行动点消耗，存档schema保持4。
- 验证扣款、余额不足、模式限制、刷新、英文及桌面/手机布局。

## 0.9.1-preview — 2026-10-05

- 九种体型轮廓裁剪与独立眼睛眨眼、镜片适配；保留旧存档结构。
- 当前十个分类各增加六件，共60件独立 SVG 模型，含独立中英文背景说明。
- 商店、探索、照护里程碑、兑换码继续使用原有逻辑。
- 程序图形可独立替换；不宣称实现布料物理。历史待办状态保留。

## 0.9.0-preview — 2026-10-05

- 八个主分区、52个二级入口；导航配置与组件独立模块化。
- 首页精简、详情折叠；完整系统使用主内容区，短操作保留弹窗。
- 面包屑、返回、Ctrl+K搜索、最近使用、实验体与住户情境操作。
- 桌面侧栏 / 手机抽屉；界面偏好独立持久化。
- 保留原有玩法、存档与剧情模式限制。完整玩法测试、52入口及驾驶浏览器检查通过。

## 0.8.3-preview — 2026-10-04

- Replaced the shared short scenery loop with stable distance-indexed landmarks, varied by route. Visual-only interpolation smooths 100ms simulation updates.
- Stop painting and pause animations in the obscured laboratory while Roads are open; restore on close. Cache WebGL environment/cabin meshes and adapt internal resolution on slow frames.
- New saves own no vehicle. Acquire the sedan for 120 credits (including 20 L of fuel) or another eligible vehicle; driving and cabin commands require actual ownership. Road save version 3 retains existing owned vehicles and explicitly labels old starter gifts.
- Direct Get Out / Enter Location controls work after arrival in all 39 locations, including friendly settlements. Safe rooms have no guards, locked doors or repeatable loot chests.
- Pixel room fixtures follow 12 purposes, with distinct clinic, ward, theatre, morgue, control and cooling layouts. Fixed viewport clipping and doubled HUD.
- Verified acquisition / departure / arrival / entry / exit / reload; old saves, friendly and hostile interiors, keyboard/touch controls and mobile. Full original regression suite passed. In the same software-rendering test, average frame time fell from roughly 100ms to 18ms after obscured background painting was disabled; this is a test result, not a universal FPS guarantee.
- Remaining scope: route-based driving; complete indoor settlement commerce and NPC routines are not included.

## 0.8.2-preview — 2026-10-04

- Cockpit now has explicit destination selection / Start Trip controls, rather than opening an inert parked driving view.
- Restore canvas focus after navigation, departure and selector changes so WASD reaches the controls. Failure messages refresh immediately.
- Add Sit in Driver Seat; roadside seating preserves the target and distance, and supports Resume Trip. Explain compact vehicles' lack of standing aisles.
- Park and Stand Up for walkable vehicles; cabin walking also accepts arrow keys.
- Move minimap to the upper right on desktop and mobile.
- Verified keyboard and on-screen throttle, focus, seat/resume, truck walking and HUD placement at 1366×768, 1920×1080 and 390px; zero page errors.

## 0.8.1-preview — 2026-10-04

- 67 connected road segments link all 39 destinations, with shortest accessible routes and active-route highlights.
- Live cockpit minimap: moving vehicle arrow, heading, route and bounded world perimeter.
- Hard shoulder limits with speed reduction; rendered road moves laterally when steering. Platform ceiling blocks movement.
- Prevent roadside destination changes from teleporting to the origin. Arrival persists immediately and mileage cannot overshoot.
- Existing route saves reconstruct geometry without resetting distance, fuel, money or inventory. Detours preserve cursor position.
- Driving remains route based: free off-road movement and manual junction selection are not included.

# v0.8.0-preview — 2026-10-04

加入真正3D后舱、公路地图和横版回收、18车型定义、运输尺寸、64探索装扮、35遗物独立背景、30主要人物个人短事件。修复动力、救援、陈列、门锁、读档与金额上限等问题。仍为开发预览：赛车和秘密车辆完整剧情、正式模型及部分历史需求未完成，详见 ROAD-PROGRESS.md。

# 0.7.1 — 2026-10-04

完成：人物差异化 SVG、真实扑克牌、六类立体电脑及卧室电脑结构、剧情指定高潮抖屏与暗色冲击。无存档格式改动。商队、人物会面、重载、移动端、减少动态与浏览器错误检查通过。

# v0.7.0 · 2026-10-04

新增商队交易、成色、护送与持久人物系统。详细计数、组合方式、测试和限制见 RELEASE-0.7.0.md。

# v0.6.0 · 2026-10-04

卧室共享 XYZ 投影、21 主题壁纸配色、纯叙事 Story 模式、隐藏关系/调查/延迟回应、资格结局与八个叙事成就。完整验证和限制见 RELEASE-0.6.0.md。

# v0.5.0 — Containment Life · 2026-10-04

- 高阶壁纸动态化；新增异常壁纸「邪恶实验室」。培养舱、怪物大小与距离可调整，统一地面锚点。
- 武器 48 件：每件独立来源故事；新增弓、长剑、匕首和三种枪；6 类攻击特效，霰弹散射与银轨光束分别绘制。
- 新增 100 件变卖物（20 类轮廓 × 5 个结构变体），按稀有度抽取，探索有效返回后回收；新增 30 个成就。
- 第二住户 12 种；最多 3 位活动，保存个体种子、需求、记忆和关系。提供领养、组装与探索救援。捕食冲突有多次预警、分隔和极低概率致命结果。
- 卧室 150 件模块化家具（25 类 × 6 种结构）；30 件异常陈设。自由拖动、坐标微调、旋转、仓储、持有复制、桌面支撑、墙界、碰撞、门口净空、预览与取消。
- 500 个情境/反应组合，200 个生活事件变体（156 物种/情境、14 家具、30 异常陈设），不是 200 条独立长篇支线。
- step114514 永久兑换资格与每档一次性发放分离；迁移旧兑换历史，新内容补发，不重填使用过的物资。
- 修复壁纸总数写死、武器数值循环、旧模型重复花器、家具中空区域难点击；空指针武器替换鼠标箭头轮廓。
- 多色实验室 Logo 与版本号。制作组 St3phEn。

# ABYSS LAB 更新日志

制作组：**St3phEn**。最新内容列在最上方；回顾不虚构历史发布日期。未完成内容不记作已交付。

## 2026-10-04 · 合身装扮、日末活动与历史内容补齐

- 装扮跟随 8 种变异体型调整，面饰/尾饰按眼睛和尾尖定位；修复衣柜裁剪。新增 20 件独立装扮，总数 170。
- 剧情模式叙事期间拦截普通行动；日末收尾后开放活动窗口，主线选择免费。
- 居所场景共 80 条；实验体可以表达住处、灯光和温度偏好；重损房间可永久封存，记忆保留。
- 区域旅行接入现有 65 个探索事件，支持途中选择、回收、读档和免费返程；营地场景 20 条、基础食物 15 种。
- 20 个 NPC 加入 100 条独立关系回应；修复重复点击刷次数、关系旗标丢失和部分英文观点残留中文。
- 梦境共 75 条，五个主要梦各三段短序列；增加 20 条跨代观察、15 条遗物场景、10 条回声观察。
- 公开网站建立在 GitHub Pages；静态公开版使用备用对白，本机保留安全的 AI 后端。
- 新/旧存档和完整规则回归通过；浏览器验证两种桌面尺寸、移动宽度、英文、file://，无脚本错误。
- 长篇阵营/区域剧情、战争/家庭发展、完整梦境关卡和云端 AI 部署仍未完成。详见 TASK-STATUS.md。

## 2026-10-04 · 荒野狩猎与神秘药剂

- 养成模式加入可选狩猎循环：14 区域、24 普通敌人、10 精英、8 首领、34 招式。
- 加入 55 瓶药剂（50 普通神秘药剂 + 5 赌剂），每瓶独立伪 3D 模型规格和单独背景故事，支持档案、未知剪影、使用确认、发现揭示与配方复现。
- 加入 40 武器、蓝图锻造、升级修理与 6 异常武器，包括战斗内 404 弹窗。
- 加入 100 个新外观、3 新穿戴槽、8 训练、6 食谱、6 可协商悬赏与 12 成就。
- 废料抽取仅用游戏内所得，十连少见以上、20 抽稀有、60 抽史诗保底，含软保底与重复补偿。
- 败退损失未带回物资、损坏武器并留下临时虚弱和恐惧；普通失败不删除实验体，免费撤退保留当前战利品。
- 主存档版本保持 4，新增 hunt v1。旧存档、原功能与服务器端 API 配置保留。
- 修复原房间成就提前解锁，以及新系统读档缓存、突变 ID、重复缩放、剪影样式和英语战斗日志问题。
- 已验证规则与浏览器流程；敌人/武器专属插画、复杂攻击动画、进一步长期平衡仍待扩展。详见 HUNT-REPORT.md。

## 2026-10-03 · 制作组署名与更新日志

- 游戏制作组统一署名为 St3phEn。
- 终端菜单新增「更新日志」，支持中文和英文。
- 开始维护本文件，记录完成内容、修复及未完成事项。

## 2026-10-03 · MEGA 扩展可玩核心版

- 实验室：27 个房间定义，升级、修理、装饰、房间记忆和自主移动的画面变化。
- 旅行：17 个区域、10 个地标、7 类天气、路线取舍及免费返程。
- 人物：20 位人物，Jack 与实验体的独立关系、援助及托付资料风险。
- 多代养成：生命档案、遗物及同一实验室的下一代，重新建立个体关系。
- 梦与连续性：15 个梦、世界线回声、连续性结论，12 个新成就和 6 张新背景。
- 修复：新个体继承旧身体创伤、NPC 网络重置、姓名静默重置、房间记忆英文不完整。

未完成：附件要求的大批场景、完整战争和长篇连续性碰撞剧情仍待扩展；网站发布被环境审批阻止，尚未上线。详细数量和测试见 MEGA-PROGRESS.md。

## 既有版本回顾（未推定发布日期）

- Jasmine 改名及旧存档兼容。
- Jack 的 20 章剧情、日记、粗口强度和扩展结局；主线不扣 AP。
- 六聚落、人物记忆、传闻、长期后果和最初 20 张伪 3D 壁纸。
- 饰品换装、100 种全身颜色、中英文切换与服务器端 AI 对话。

后续更新应同时维护本文件和游戏内 js/data/updateLog.js；只有实现并验证的内容列入完成项。

## 2026-10-04 · 兑换码与独立删档
- 增加当前存档兑换码入口与全物品外观补给。
- 兑换壁纸、颜色与皮肤仅绑定本档，不进入跨档收藏。
- 支持删除当前档，清除手动/自动/备份，重置实时状态，防止自动保存复活。

## 2026-10-04 · 收藏美术整改 / St3phEn
- 50 件探索物品完整专属图形覆盖，撤下三种通用盒子/瓶子/卡片模板。
- 废土服饰的身体、背部、项链、尾部、脸部、武器和特效轮廓重绘，全部100件采用新材质流程。
- 13 件原有高级服饰独立重绘；15 瓶高级和赌剂的特殊收容外壳。
- 40 件战斗武器新增对应物品图，替代纯文字展示。

## 2026-10-04 · 潮汐拾遗与夜班档案 / St3phEn
- 新增20件独立造型装扮，总数170件，覆盖10个部位。
- 加入两组隐藏套装共鸣，整合探索掉落与废料抽取；两件普通生活纪念自动解锁。
- 已兑换全收藏的旧档自动补齐新装扮，已有装备、预设和关系保留。
- 准备GitHub Pages发布包，服务器密钥不进入公开包。

## Weapon 2.0 — Dawn / Null Pointer (2026-10-05)
- Dawn: first successful strike, next-encounter victory bonus, temporary defense and dedicated light effect.
- Null Pointer: six exclusive resonance ranks, capped positive streak, once-per-fight defense dereference and probabilistic incoming damage nullification.
- Persisted combat state and bilingual resonance descriptions.
- Verified 10 new mechanism checks and isolated browser combat/reload at 1366 and 1920 widths. Weapon 2.0 remains in progress.

## Weapon 2.0 — Authority and Clearance (2026-10-05)
- Council blade: six distinct ranks, opening ceremony, timed block, next-hit retaliation, capped stability recovery and explicit faction benefits.
- Black Clearance rifle: elite and Abyss targeting, first shield breach, elite victory carry and saved three-way enemy intel scan.
- Both pass isolated 1366/1920 browser combat and reload checks; previous 69-weapon R6 replay remains passing. Remaining advanced weapons, companions and multiple targets are still in progress.

## Weapon 2.0 — 404 POP-UP (2026-10-05)
- Six distinct resonance ranks: trigger probability, second window, critical/speed, shield-clear interruption, damage redirection and two distinct first-trigger effects.
- Saved one-use state, bounded secondary damage, actual shield/repair suppression and in-game-only error windows.
- Fixed anomalous resonance attack-time modifiers being ignored.
- Six mechanism checks, 69-weapon R6 replay and isolated 1366/1920 browser combat/reload checks pass. Other remaining Weapon 2.0 work is still in progress.

## Weapon 2.0 — remaining resonance and encounter systems (2026-10-05)
- Add all six ranks for Second Hand, Empty Chamber, Red Thread, Companion Fang, Chain Arc, Silver Rail, Dismantling Hook and Drone Relay.
- Saved delayed-damage combat clock, real independent second target and continuation, Jack/pet party HP and selectable existing pet companions.
- Finish six-rank coverage for all 13 Epic, 8 Legendary and 6 Anomalous weapons; reset Rare consecutive-hit windows on misses.
- Add weapon-only DPS estimates, saved independent weapon display, physical carried-weapon cargo volume/weight, rare universal cores and max-resonance duplicate guidance.
- Added timed, team and final audit tests. Full regression baseline and current affected-system tests passed; browser checks cover 8 remaining advanced weapons, real second-target damage, party/timer/reload and display/companion controls. Art remains replaceable procedural SVG.
