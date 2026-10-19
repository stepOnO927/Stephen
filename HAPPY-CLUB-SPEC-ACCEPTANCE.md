# 快乐俱乐部最终规格 · 74节完整验收索引

来源：用户最终规格“MEGA LOCATION — HAPPY CLUB FINAL SPEC”，后发覆盖旧规则。原文SHA256：bdf7db89c00cbd7ec3aaf565aff08f4e097058a1e1682d2ec1f4ee625e60dd65。

此页完整保留74节原始条款，不把既有单元绿测当作统一终验。每节下列源码/测试是核对入口，不表示全节已达成。0.13.183–185补齐了陈设满库保留、终局结算边界和双语显示；不是宣布整个俱乐部完成。其余历史模块仍在TASK-AUDIT.md与BATCHED-UPDATES.md中，未删范围。

统一终验须覆盖：新档实际无车→购车/地图路线→实际驾驶停车下车→25秒原生点击→费用/次数/两击/Bomb/公平性→存读/结算→六级奖池与原实体入库/容量→保底/排除/批量/跳过→统计/成就/NPC/新闻，并核对下面每一条。视觉与最终玩法感仍需实际观感证据。

0.13.214补充连续证据：三屏原生无车购车→实际加速驾驶→停车进入→真实25秒鼠标两击→当轮Token兑换→刷新→三轮8000/12000/18000与日封顶；另修复每帧奖品节点重建和重复RAF。见HAPPY-CLUB-STABLE-214-REPORT.md。本批不覆盖全部74节，原始条款完整保留。

## PART I — 地点

原稿行 10–42。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/location.js; js/road/core.js。测试入口（tests/下）：happy-club-arrival; happy-club-venue。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

新增地点：

HAPPY CLUB
快乐俱乐部

REGION:
BLACK FOREST / 深林

必须：

- 永久标记在世界地图
- 可驾车前往
- 不随机消失
- 属于安全娱乐地点
- 有停车场
- 售票窗口
- 靶场
- 奖品区
- 休息区
- 宠物等待区

地图位置建议：

BLACK FOREST
├─ Abandoned Mansion
├─ Hunter Camp
├─ Deep Research Well
└─ HAPPY CLUB

==================================================
</details>

## PART II — 门票

原稿行 43–73。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/core.js; js/happyClub/round.js。测试入口（tests/下）：happy-club-save; happy-club-game-browser。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

基础门票：

8,000 Credits / ROUND

每张票：

只允许一次25秒挑战。

同一天重复游玩：

第1次：
8,000

第2次：
12,000

第3次：
18,000

建议每天最多3次。

之后：

CLOSED FOR TODAY

避免无限刷。

==================================================
</details>

## PART III — 货币规则

原稿行 74–93。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/core.js; js/happyClub/round.js。测试入口（tests/下）：happy-club-save; happy-club-game-browser。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

仅允许游戏内：

CREDITS

禁止：

真钱

付费抽奖币

付费Spin

现金提现

现实货币购买次数

==================================================
</details>

## PART IV — 挑战基本结构

原稿行 94–114。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/core.js; js/happyClub/round.js。测试入口（tests/下）：happy-club-save; happy-club-game-browser。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

流程：

进入Happy Club
→ 支付门票
→ 第一人称靶场
→ 25秒计时
→ 靶子间歇出现
→ 每个普通奖励靶需要2次点击命中
→ 成功击破获得对应等级Wheel Token
→ 25秒结束
→ 批量进入奖励转盘
→ 获得奖励

如果误点Bomb：

当前ROUND立即结束。

==================================================
</details>

## PART V — 第一人称表现

原稿行 115–146。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

使用：

FIRST PERSON VIEW

前方：

像素树林

树干

灌木

旧围栏

石头

倒木

靶场机械结构

背景允许：

2D pixel forest

前景：

第一人称准星 / 鼠标点击

==================================================
</details>

## PART VI — 目标必须保证可见

原稿行 147–178。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

任何奖励靶生成时：

必须保证玩家一定能看到。

普通奖励靶：

至少80%主体可见。

Legendary：

至少75%。

Anomalous：

至少70%。

禁止：

完全藏树后

完全藏灌木后

颜色完全融进背景

出现在UI按钮背后

出现在画面裁切边缘导致无法点

==================================================
</details>

## PART VII — 靶子不会永久存在

原稿行 179–208。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

所有目标：

都有 visibleDuration。

时间结束：

目标自动：

下沉

滑回树后

跑走

缩回

翻倒

或异常消失

如果玩家没有在消失前完成所需命中：

MISS

不奖励Token。

==================================================
</details>

## PART VIII — 靶子稀有度

原稿行 209–232。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

奖励靶：

COMMON

UNCOMMON

RARE

EPIC

LEGENDARY

ANOMALOUS

另有：

BOMB

Bomb不是稀有度。

==================================================
</details>

## PART IX — 稀有度与大小

原稿行 233–280。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

COMMON

size:
100%

--------------------------------------------------

UNCOMMON

size:
82%

--------------------------------------------------

RARE

size:
65%

--------------------------------------------------

EPIC

size:
50%

--------------------------------------------------

LEGENDARY

size:
38%

--------------------------------------------------

ANOMALOUS

size:
26–32%

越稀有：

整体越小。

==================================================
</details>

## PART X — 稀有度越高，消失越快

原稿行 281–321。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

这是核心规则。

COMMON

visibleDuration:
2.5–3.2s

--------------------------------------------------

UNCOMMON

2.0–2.6s

--------------------------------------------------

RARE

1.5–2.0s

--------------------------------------------------

EPIC

1.05–1.45s

--------------------------------------------------

LEGENDARY

0.70–1.05s

--------------------------------------------------

ANOMALOUS

0.45–0.75s

==================================================
</details>

## PART XI — 稀有目标生成后留空窗

原稿行 322–346。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

如果出现：

EPIC
LEGENDARY
ANOMALOUS

下一次spawn略微延迟。

Epic:
+0.25s

Legendary:
+0.40s

Anomalous:
+0.60s

目的：

让玩家能注意到它。

==================================================
</details>

## PART XII — 刷新频率

原稿行 347–370。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

刷新率不能太高。

正常spawn interval：

1.0–2.1秒

动态调整。

如果：

场上已有2个靶

则延迟下一次生成。

如果：

场上为空

可以稍微加快。

==================================================
</details>

## PART XIII — 同时存在数量

原稿行 371–390。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

正常：

1个

偶尔：

2个

极少：

3个

禁止：

长时间出现4个及以上。

==================================================
</details>

## PART XIV — 25秒靶子总量

原稿行 391–404。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

平均：

9–14个

特殊快速局：

最多16个

禁止把25秒做成疯狂点击风暴。

==================================================
</details>

## PART XV — 靶子可以移动

原稿行 405–432。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

普通奖励靶允许：

移动。

movementType包括：

STATIC

SLOW_SLIDE

FAST_SLIDE

VERTICAL_RISE

SIDE_PEEK

SWING

RUN_ACROSS

CURVE_MOVE

STOP_AND_GO

==================================================
</details>

## PART XVI — 稀有度与移动

原稿行 433–470。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

COMMON：

大多数静止
或极慢移动

UNCOMMON：

慢速移动

RARE：

明显移动

EPIC：

移动速度更高
可能改变方向一次

LEGENDARY：

快速
不规则移动
短暂停顿

ANOMALOUS：

位置轻微错位
重影
突然短距离位移

但：

不能真正瞬移到玩家无法反应的位置。

==================================================
</details>

## PART XVII — 靶子可以变形

原稿行 471–496。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

允许：

MORPH TARGET

变形只作用于：

视觉轮廓
大小
宽高比
姿态

例如：

圆靶
→ 细长靶

动物轮廓
→ 压低身体

金属牌
→ 折叠

==================================================
</details>

## PART XVIII — 稀有度与变形

原稿行 497–520。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

COMMON：
基本不变形

UNCOMMON：
偶尔轻微缩放

RARE：
可能改变一次形状

EPIC：
可以持续轻微变形

LEGENDARY：
明显变形 + 移动

ANOMALOUS：
不规则轮廓变化
错误重影
比例短暂异常

==================================================
</details>

## PART XIX — 变形不能坑人

原稿行 521–540。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

即使变形：

可点击面积必须：

和视觉主体一致。

禁止：

视觉大
实际hitbox小

或：

视觉小
hitbox乱跑。

==================================================
</details>

## PART XX — 目标碰撞布局系统

原稿行 541–554。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

非常重要：

所有靶子之间：

禁止互相覆盖。

禁止贴得太近。

禁止移动到另一个靶子的空间。

==================================================
</details>

## PART XXI — Target Safe Zone

原稿行 555–576。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

每个靶子拥有：

targetBounds

safeRadius

movementPathBounds

生成前：

先检测目标区域。

只有满足：

noOverlap = true

才允许spawn。

==================================================
</details>

## PART XXII — 最小靶子间距

原稿行 577–594。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

推荐：

两个普通目标之间：

至少保留：

目标最大宽度的 0.4–0.7 倍

或固定屏幕距离：

约60–100px

根据分辨率动态缩放。

==================================================
</details>

## PART XXIII — 不允许生成重叠

原稿行 595–618。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

生成目标前：

必须检测：

existingTargetBounds[]

如果候选spawn point：

与任意现有目标重叠

或距离小于：

MIN_TARGET_GAP

则：

拒绝该点位

重新寻找位置。

==================================================
</details>

## PART XXIV — 移动路径也必须检测

原稿行 619–636。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

不能只检测出生点。

移动靶生成时：

整个 movementPath

必须提前检查：

是否会经过其他目标的：

safeRadius

movementPathBounds

==================================================
</details>

## PART XXV — 移动不能撞靶

原稿行 637–658。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

如果运行期间两个移动路径可能产生冲突：

优先：

1. 修改后生成靶子的路径
2. 降低移动距离
3. 改变方向
4. 暂停该目标移动
5. 延迟spawn

禁止：

两个靶子直接穿过去

禁止：

移动靶叠在另一个靶子上。

==================================================
</details>

## PART XXVI — 动态避让

原稿行 659–680。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

如果特殊情况下路径发生意外冲突：

使用：

TARGET AVOIDANCE

移动目标：

提前减速

暂停

反向

或提前消失

而不是穿过另一个靶子。

==================================================
</details>

## PART XXVII — Bomb也遵守间距规则

原稿行 681–704。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

Bomb Target：

同样不能：

盖住奖励靶

贴着奖励靶

移动到奖励靶上。

尤其：

Bomb + Legendary

同时出现时：

必须明显分离。

玩家不能因为目标重叠而误点Bomb。

==================================================
</details>

## PART XXVIII — Bomb Target

原稿行 705–726。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

新增：

BOMB TARGET

视觉：

SOLID BLACK

纯黑色主体。

形状可：

黑圆靶

黑动物轮廓

黑金属牌

==================================================
</details>

## PART XXIX — Bomb视觉识别

原稿行 727–748。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

Bomb必须：

明显区别普通目标。

虽然纯黑，

但在深色森林背景中必须可识别。

允许：

极细深灰外轮廓

轻微边缘光

禁止：

完全融进黑背景。

==================================================
</details>

## PART XXX — Bomb需要几次命中

原稿行 749–766。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

Bomb：

1次点击即触发。

与奖励靶不同。

奖励靶：

2 hits。

Bomb：

1 hit = ROUND ENDED。

==================================================
</details>

## PART XXXI — 点击Bomb的后果

原稿行 767–796。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

立即：

stop timer

stop target spawning

disable target input

结束当前25秒Happy Club round。

注意：

只是结束本轮小游戏。

不是：

ABYSS LAB Game Over

不是：

Jack死亡

不是：

删档

==================================================
</details>

## PART XXXII — Bomb不会清空之前奖励

原稿行 797–810。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

误点Bomb之前已经获得：

Wheel Tokens

全部保留。

只是：

剩余时间作废。

==================================================
</details>

## PART XXXIII — Bomb反馈

原稿行 811–830。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

可以：

画面轻微变暗

短错误音

工作人员吹哨

显示：

ROUND ENDED

BOMB HIT

不要做真实爆炸。

==================================================
</details>

## PART XXXIV — Bomb出现概率

原稿行 831–850。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

NORMAL：

5%

HARD：

7%

STATIC NIGHT：

9%

绝对上限：

12%

==================================================
</details>

## PART XXXV — Bomb保护

原稿行 851–870。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

开局前3秒：

不能生成Bomb。

两个Bomb之间：

至少间隔4秒。

每局最多：

2个Bomb。

大多数局：

0–1个。

==================================================
</details>

## PART XXXVI — Bomb显示时间

原稿行 871–886。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

1.1–1.8s

不要太短。

Bomb考验：

识别

克制

而不是反应速度。

==================================================
</details>

## PART XXXVII — Bomb可以移动

原稿行 887–908。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

允许Bomb：

轻微移动

例如：

SLOW_SLIDE

SWING

PEEK

但：

移动速度不得达到Legendary级。

Bomb不能通过疯狂运动诱导误触。

==================================================
</details>

## PART XXXVIII — Bomb可以变形

原稿行 909–924。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

最多：

轻微形变。

禁止：

Bomb变成和Legendary/Anomalous几乎一样。

必须始终保持：

纯黑视觉身份。

==================================================
</details>

## PART XXXIX — 奖励靶命中

原稿行 925–944。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

普通奖励目标：

需要2次有效点击。

第一次：

HIT 1

第二次：

TARGET CLEARED

然后：

获得1个对应等级Wheel Token。

==================================================
</details>

## PART XL — 连击

原稿行 945–964。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

连续清除目标：

combo+

可用于：

score

排行

成就

但：

不要让combo直接改变奖励稀有度太多。

==================================================
</details>

## PART XLI — 推荐靶子概率

原稿行 965–988。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

在非Bomb的奖励目标roll中：

COMMON:
42%

UNCOMMON:
27%

RARE:
17%

EPIC:
9%

LEGENDARY:
4%

ANOMALOUS:
1%

==================================================
</details>

## PART XLII — 稀有度动态修正

原稿行 989–1005。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

特殊事件：

TARGET FESTIVAL：

Rare+提升

STATIC NIGHT：

Anomalous：
1% → 3%

但门票提高。

==================================================
</details>

## PART XLIII — 目标种类

原稿行 1006–1029。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

普通圆牌

动物轮廓牌

金属目标

木制目标

机械升降靶

摇摆靶

跑动靶

折叠靶

异常错误靶

Bomb靶

==================================================
</details>

## PART XLIV — Reward Token

原稿行 1030–1047。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/wheels.js; js/happyClub/wheelUI.js; js/happyClub/furnishings.js; other prize adapters。测试入口（tests/下）：happy-club-wheels; happy-club-pool-coverage; happy-club-furnishings。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

每击破一个奖励靶：

Common Wheel Token

Uncommon Wheel Token

Rare Wheel Token

Epic Wheel Token

Legendary Wheel Token

Anomalous Wheel Token

==================================================
</details>

## PART XLV — Common Wheel

原稿行 1048–1069。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/wheels.js; js/happyClub/wheelUI.js; js/happyClub/furnishings.js; other prize adapters。测试入口（tests/下）：happy-club-wheels; happy-club-pool-coverage; happy-club-furnishings。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

包含：

基础材料

普通植物

普通种子

普通速食

普通家具

普通武器

普通装扮

Credits

==================================================
</details>

## PART XLVI — Uncommon Wheel

原稿行 1070–1087。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/wheels.js; js/happyClub/wheelUI.js; js/happyClub/furnishings.js; other prize adapters。测试入口（tests/下）：happy-club-wheels; happy-club-pool-coverage; happy-club-furnishings。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

包含：

Uncommon武器

Uncommon食谱

优质种子

动物用品

Uncommon家具

医疗用品

==================================================
</details>

## PART XLVII — Rare Wheel

原稿行 1088–1111。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/wheels.js; js/happyClub/wheelUI.js; js/happyClub/furnishings.js; other prize adapters。测试入口（tests/下）：happy-club-wheels; happy-club-pool-coverage; happy-club-furnishings。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

包含：

Rare武器

Rare食谱

Rare植物

Rare动物

Rare家具

Rare装扮

Rare变卖物

车辆零件

高品质种畜

==================================================
</details>

## PART XLVIII — Epic Wheel

原稿行 1112–1133。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/wheels.js; js/happyClub/wheelUI.js; js/happyClub/furnishings.js; other prize adapters。测试入口（tests/下）：happy-club-wheels; happy-club-pool-coverage; happy-club-furnishings。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

包含：

Epic武器

Epic植物

Epic食谱

Epic动物

Epic家具

Epic装扮

高阶Serum

高基因动物

==================================================
</details>

## PART XLIX — Legendary Wheel

原稿行 1134–1157。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/wheels.js; js/happyClub/wheelUI.js; js/happyClub/furnishings.js; other prize adapters。测试入口（tests/下）：happy-club-wheels; happy-club-pool-coverage; happy-club-furnishings。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

包含：

Legendary武器

Legendary动物

Legendary植物

Legendary食谱

Legendary家具

Legendary装扮

Legendary变卖物

壁纸

高级种畜

==================================================
</details>

## PART L — Anomalous Wheel

原稿行 1158–1189。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/wheels.js; js/happyClub/wheelUI.js; js/happyClub/furnishings.js; other prize adapters。测试入口（tests/下）：happy-club-wheels; happy-club-pool-coverage; happy-club-furnishings。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

Anomalous靶成功击破：

获得：

ANOMALOUS WHEEL TOKEN

池：

Anomalous Weapon

Anomalous Plant

Anomalous Furniture

Anomalous Object

Anomalous Cosmetic

Anomalous Wallpaper

Anomalous Valuable

Anomalous Serum

少量：

Anomalous Animal

==================================================
</details>

## PART LI — 特殊获得物禁止进池

原稿行 1190–1217。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/wheels.js; js/happyClub/wheelUI.js; js/happyClub/furnishings.js; other prize adapters。测试入口（tests/下）：happy-club-wheels; happy-club-pool-coverage; happy-club-furnishings。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

所有物品增加：

wheelEligible

以下必须：

false

Story-exclusive

Ending-exclusive

Host-exclusive

Continuity-exclusive

Redemption-code exclusive

Unique World Relic

One-time Memorial

Unique Quest Reward

==================================================
</details>

## PART LII — 高级Wheel不能跨到异常

原稿行 1218–1229。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/wheels.js; js/happyClub/wheelUI.js; js/happyClub/furnishings.js; other prize adapters。测试入口（tests/下）：happy-club-wheels; happy-club-pool-coverage; happy-club-furnishings。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

Legendary Wheel：

不能抽Anomalous。

Anomalous只能：

Anomalous Wheel。

==================================================
</details>

## PART LIII — Draw All

原稿行 1230–1247。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/wheels.js; js/happyClub/wheelUI.js; js/happyClub/furnishings.js; other prize adapters。测试入口（tests/下）：happy-club-wheels; happy-club-pool-coverage; happy-club-furnishings。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

挑战结束后：

支持：

DRAW ALL

例如：

Common ×4
Rare ×2
Epic ×1

可以一次结算。

==================================================
</details>

## PART LIV — Skip Wheel Animation

原稿行 1248–1259。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/wheels.js; js/happyClub/wheelUI.js; js/happyClub/furnishings.js; other prize adapters。测试入口（tests/下）：happy-club-wheels; happy-club-pool-coverage; happy-club-furnishings。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

转盘动画：

1.5–3秒。

支持：

SKIP ANIMATION。

==================================================
</details>

## PART LV — Bad Luck Protection

原稿行 1260–1271。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/wheels.js; js/happyClub/wheelUI.js; js/happyClub/furnishings.js; other prize adapters。测试入口（tests/下）：happy-club-wheels; happy-club-pool-coverage; happy-club-furnishings。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

可做轻度保护：

连续5次Epic Wheel未出Epic：

下一次至少Epic。

不要做复杂付费式pity系统。

==================================================
</details>

## PART LVI — First Visit

原稿行 1272–1289。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/people.js; js/happyClub/reactions.js; js/happyClub/ui.js。测试入口（tests/下）：happy-club-reactions; happy-club-venue。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

首次到访：

小剧情。

Manager：

“Two hits.”

“Twenty-five seconds.”

“Black targets end the round.”

“Keep what you earn.”

==================================================
</details>

## PART LVII — B-07剧情

原稿行 1290–1327。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/people.js; js/happyClub/reactions.js; js/happyClub/ui.js。测试入口（tests/下）：happy-club-reactions; happy-club-venue。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

第一次：

B-07：
“八千？”

Jack：
“嗯。”

B-07：
“打木板？”

Jack：
“……嗯。”

--------------------------------------------------

看到Bomb：

B-07：
“黑的不能打？”

Jack：
“对。”

--------------------------------------------------

Jack误点：

B-07：
“你刚才说不能打。”

Jack：
“我知道。”

==================================================
</details>

## PART LVIII — B-07不能参与点击

原稿行 1328–1341。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/people.js; js/happyClub/reactions.js; js/happyClub/ui.js。测试入口（tests/下）：happy-club-reactions; happy-club-venue。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

B-07只：

观察

评论

反应。

不要让AI代玩家点击。

==================================================
</details>

## PART LIX — 宠物

原稿行 1342–1351。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/people.js; js/happyClub/reactions.js; js/happyClub/ui.js。测试入口（tests/下）：happy-club-reactions; happy-club-venue。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

宠物留在：

REST AREA

不能进入靶场。

==================================================
</details>

## PART LX — Club NPC

原稿行 1352–1367。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/people.js; js/happyClub/reactions.js; js/happyClub/ui.js。测试入口（tests/下）：happy-club-reactions; happy-club-venue。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

加入：

Club Manager

Range Attendant

Prize Clerk

Rich Collector

Suspicious Regular

==================================================
</details>

## PART LXI — 环境美术

原稿行 1368–1393。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/environment.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-environment; happy-club-art。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

Happy Club：

旧霓虹牌

森林停车场

售票口

旧木结构

靶场

奖品区

名字虽然叫：

HAPPY CLUB

但氛围可以有：

废土式黑色幽默。

==================================================
</details>

## PART LXII — 新闻联动

原稿行 1394–1405。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/events.js。测试入口（tests/下）：happy-club-events。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

WASTELAND NEWS可播：

“HAPPY CLUB today reports increased Rare Target activity.”

“STATIC NIGHT tonight.”

“Happy Club temporarily closed after bandit activity.”

==================================================
</details>

## PART LXIII — Weekly Event

原稿行 1406–1417。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/events.js。测试入口（tests/下）：happy-club-events。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

每周：

TARGET FESTIVAL

提高：

Rare / Epic概率。

==================================================
</details>

## PART LXIV — Accessibility

原稿行 1418–1430。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/core.js; js/happyClub/ui.js; js/happyClub/round.js。测试入口（tests/下）：happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

提供：

Target Contrast
NORMAL / HIGH

Cursor Size

Reduced Motion

==================================================
</details>

## PART LXV — 运动辅助

原稿行 1431–1446。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/core.js; js/happyClub/ui.js; js/happyClub/round.js。测试入口（tests/下）：happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

Reduced Motion开启：

靶子仍可移动，

但：

速度降低

变形幅度降低

不会改变奖励概率。

==================================================
</details>

## PART LXVI — 统计

原稿行 1447–1482。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/core.js; js/happyClub/achievements.js。测试入口（tests/下）：happy-club-statistics; happy-club-achievements。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

记录：

happyClubVisits

targetsSpawned

targetsCleared

commonCleared

uncommonCleared

rareCleared

epicCleared

legendaryCleared

anomalousCleared

bombsSpawned

bombsAvoided

bombsHit

accuracy

bestCombo

bestRun

==================================================
</details>

## PART LXVII — 成就

原稿行 1483–1519。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/core.js; js/happyClub/achievements.js。测试入口（tests/下）：happy-club-statistics; happy-club-achievements。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

HAPPY?
第一次进入。

TWO HITS
第一次击破奖励靶。

SHARP EYES
击破Rare。

BIG GAME
击破Epic。

NO WAY
击破Legendary。

WHAT WAS THAT?
击破Anomalous。

BLACK TARGET
误点Bomb。

SELF CONTROL
一局避开2个Bomb。

WRONG ONE
Legendary和Bomb同时出现时误点Bomb。

TWENTY-FIVE SECONDS
单局击破10个以上目标。

EXPENSIVE HOBBY
累计消费100,000 Credits。

==================================================
</details>

## PART LXVIII — 生成算法硬规则

原稿行 1520–1554。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

每次目标spawn必须：

1.
生成candidate position

2.
生成candidate bounds

3.
生成完整movement path

4.
检查：

屏幕边界

可见性

其他靶子bounds

其他靶子safeRadius

其他靶子movementPathBounds

5.
只有全部合法才spawn

否则：

重新roll位置/路径。

==================================================
</details>

## PART LXIX — 靶子空间优先级

原稿行 1555–1572。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

如果找不到安全位置：

不要硬塞。

选择：

延迟spawn。

因此：

宁可少刷一个，

也不能重叠。

==================================================
</details>

## PART LXX — 运动过程持续检测

原稿行 1573–1596。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

移动过程中：

实时或分段检测：

futurePosition

如果即将进入另一个target safe zone：

该目标：

减速

暂停

反向

或提前退出

禁止穿模 / 重叠。

==================================================
</details>

## PART LXXI — Bomb误触公平性

原稿行 1597–1612。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

Bomb周围的：

MIN_TARGET_GAP

可以比普通靶：

再增加20%。

尤其避免：

奖励靶紧贴炸弹导致误点。

==================================================
</details>

## PART LXXII — 最高稀有靶公平性

原稿行 1613–1644。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

Legendary / Anomalous出现时：

不得被：

Bomb

普通靶

UI

树干前景

严重遮挡。

难点应该来自：

小

快

移动

变形

而不是：

看不见或被挡住。

==================================================
</details>

## PART LXXIII — 最终推荐25秒节奏

原稿行 1645–1679。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

平均每局：

9–14个target spawn。

一般：

Common:
3–5

Uncommon:
2–4

Rare:
1–3

Epic:
0–2

Legendary:
0–1

Anomalous:
通常0

Bomb:
0–2

这只是期望分布。

不要每局强制凑齐。

==================================================
</details>

## PART LXXIV — 最终玩法感

原稿行 1680–1782。状态：尚待全节统一验收；已有实现/专项证据需按最新版本复核。

源码入口：js/happyClub/round.js; js/happyClub/TargetPlacementValidator.js; js/happyClub/targetArt.js。测试入口（tests/下）：happy-club-round; target-placement; target-placement-runtime; happy-club-motion。

<details><summary>原始验收条款（未缩减）</summary>

==================================================

玩家看到：

一个目标出现。

可能：

大、慢、Common。

也可能：

一个很小的Legendary从树后快速滑过。

也可能：

Anomalous短暂变形重影。

也可能：

纯黑Bomb突然探头。

目标会：

移动

变形

消失。

但是永远：

能看见

能点到

不会互相覆盖

不会互相贴太近

不会移动到彼此身上。

玩家的难度来自：

识别

反应

准度

克制

而不是：

UI混乱。

==================================================
FINAL REPORT
==================================================

完成后报告：

1. Happy Club世界地图位置
2. 门票与每日次数
3. 25秒挑战
4. First Person mode
5. Target spawning
6. Target disappearance
7. Spawn interval
8. Target rarity
9. Rarity size scaling
10. Rarity duration scaling
11. Moving targets
12. Morphing targets
13. Movement path generation
14. Non-overlap spawning
15. Minimum target gap
16. Path collision prevention
17. Dynamic target avoidance
18. Bomb Target
19. Bomb probability
20. Bomb hit round ending
21. Bomb reward retention
22. Bomb safe gap
23. Two-hit reward targets
24. Target visibility guarantee
25. Wheel Tokens
26. Common Wheel
27. Uncommon Wheel
28. Rare Wheel
29. Epic Wheel
30. Legendary Wheel
31. Anomalous Wheel
32. wheelEligible exclusions
33. Draw All
34. Accessibility
35. News integration
36. B-07 dialogues
37. Achievements
38. Save schema
39. Tests
40. Modified files
</details>

## 0.13.183 本批附加存档缺口

已确认旧转盘将同种陈设发到99以上，Bedroom.read仅保留99。新发奖用实际99库存+按ID保留原物的prizes暂存；旧档原owned超过99的真实数量进入legacy暂存，未从中奖文字倒推。实验室物资仓库和俱乐部奖品区可部分领取、每次100，不收费/重抽，不改原奖池/Token/保底。具体运行、测试、线上结果见verification/club-furnishings-183-results.json及TASK-STATUS.md最新回执。完整74节终验尚未完成。


## 0.13.184 · 终局统计与结算边界新增证据

对应PART XXXI–XXXIII、LXVI、LXVII的局部实证：真实种子1788458060在22.3秒已有一次Bomb避让、另一Bomb仍在场；旧版直接跳至25秒会漏记，现TIME结束前处理在场未误击Bomb。LEFT、BOMB和场外RECOVERED不额外赠送这种避让；先前获得的各级Token保留。实际SELF CONTROL/WRONG ONE通过原成就系统解锁，结算/刷新只计一次。进行中靶的数量/半命中/序号与统计核对，已留存结算历史中的同round ID不会再支付。

另修复快速重开俱乐部时排队的旧close事件误结束新局/取消新演出；真正点关闭仍正常LEFT结算。结算提示提供中英文并保留原TIME/BOMB/LEFT/RECOVERED存档ID。测试采用真实随机生成的罕见局面，浏览器边界测试明确使用受控时钟；普通购车/驾驶/25秒自然超时另行原生验证。完整74节全条款与最终观感仍未统一通过，不能从这些局部结果推定全模块完成。


## 0.13.185 · 双语呈现与真实兑换新增证据

对应IV、XLIV–LIV、LX、LXII–LXIV、LXVI的显示/操作局部验证：六级银行、兑换按钮、中奖Token/稀有度/类别、四种挑战下拉选项和奖励靶可访问名称使用本地语言。DOM value与存档仍为原NORMAL/HARD/TARGET_FESTIVAL/STATIC_NIGHT和六级Token ID，未改概率/奖池/保底/费用。五个原NPC名字/对白和画像说明注册既有中英映射；节日/静电夜新闻标题同步。没有重写原对白。

三屏实际原生COMMON兑换、跳过、DRAW ALL共12个Token，切换两种语言时逐字段检查整个游戏状态/RNG未变；刷新后所有游戏字段一致（只排除正常存盘时间戳），奖品不重抽。进行中真实生成靶仍保留HARD，动态语言切换不中断揭晓。日77同时验证两类活动，静电夜首票10000、普通困难首票8000，存储值不替换成中文。具体本地/线上收据见verification/club-locale-185-results.json与TASK-STATUS.md。74节原始条款全部保留；全条款统一终验、正式观感和其他历史模块仍待完成。


## 0.13.201 · 普通轮盘奖品满库存保留（本地候选）

确认原代码在资金10000000、材料1000000、每种种子100000、每种药剂1000000、每种变卖物10000000上限时截掉奖励或存读截断。新增可选wheels.pendingStock v1按真实奖品ID保留溢出数量，总暂存上限1000000000；没有溢出/旧档缺字段时不生成，不从历史中奖记录倒推补偿。原容量不变。

五种普通奖品及重复装扮/壁纸/满仓车辆备用件转换的材料共用此保留机制；不是替换已有武器实体副本、动物、速食、用品、壁纸收藏写入和陈设暂存。抽奖前保守预留每次250单位最大可能空间，暂存不足时不扣Token、不推进RNG/序号/保底。

在俱乐部或实验室物资仓库按空位部分领取，每次最多10000单位；无额外费用/抽取/RNG/AP，不会被同次自动观察再次领取。普通返回实验室后的有效操作可自动转入空位。非养成/外出/进行中的挑战或事件不领取。原生浏览器发现靶场动画每帧重建新暂存DOM，已以状态键缓存修复。

新增测试实际抽到五种满仓奖品；覆盖全部普通奖品ID、重复补偿、旧档默认缺省、部分/10000上限、上下文/容量原子拒绝、真实Engine存读与256组原代码结果/RNG/保底比较。完整74节终验和其他历史欠项仍未完成。最终公网回执另记。


### 0.13.201 本地最终验证

27个实际测试文件全部通过：23个俱乐部测试加2个靶子安全、保护剧情与462资源HTTP。专项覆盖200种种子、75种药剂、150种变卖物全部425种普通奖品ID的真实暂存/存读；256组旧代码奖品/RNG/保底/数量一致；9000次原奖池抽取。四个浏览器脚本按顺序运行，均在1366/768/390通过：五类满仓实际抽取258单位保留、原陈设领取、原生全部兑换/跳过、菜单/更新日志。真实购票结束后领取250资金；实验室其余四类空位由隔离测试准备，再原生点击部分领取，不冒称实际消耗全部满仓物品的游戏流程。未使用真实玩家存档或付费AI。
