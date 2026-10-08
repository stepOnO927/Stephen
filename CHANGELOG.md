## 0.13.26-preview · 出生、实验体与栏舍事件（本地候选）

养殖独立事件累计40/100，新增20情境、40选择结果；真实出生/父母/双胞胎/性状与平均基因条件，Stage2实验体给未命名山羊起名，在场宠物惊吓和同栏两份病况。保留既有玩家名字、疾病与基因；隔离布尔读档，修复根茎饲料分支漏扣费用。首批事件与旧存档继续。仍欠60养殖事件及完整历史扩展，当前专项通过，浏览器/回归终态及公开部署稍后记录。

## 0.13.25-preview · 血统、真实商队运输、种畜拍卖与野外救援（已公开，Pages #77）

新增整血统命名、种畜评估和死亡家谱；真实灰线/落日商队固定动物报价、预留空间、次日实验室交接；每七日一期、四类NPC竞价的种畜拍卖、资金托管与满钱包返款保留；三个专属远征救援事件、运输读档、原始伤情和基因、返航后隔离与唯一领取。首批20个独立养殖观察（40情境选择）接入真实动物/栏舍条件、行动资源、冷却和跨日保存；100事件尚欠80。未解锁旧档不补发，不影响保护剧情。三宽度实际UI通过；完整回归与公开部署结果见后续记录。历史100动物事件、繁育中心、完整植物品系/食堂/正式美术/公开AI等仍欠。

## 0.13.21-preview · 顶栏固定与滚动入口审计

修复大标题/时间原sticky受父容器滚动限制及地下340m/第07隔离区未固定的问题；两排改为viewport fixed，ResizeObserver测量真实高度并为正文留出空间，语言切换和侧栏宽度保持适配。终端侧栏层级180高于HUD120，Story继续隐藏普通HUD。没有存档结构或属性变更。

实际Chrome：1366/1024/768/390，中英切换、滚动前后顶栏坐标完全相等、菜单覆盖顺序和正文空间通过；61导航入口在1366/390共122次检查，底部启用按钮可命中、无横溢出/页面错误。另有原生图鉴分类、固定标题与返回流程通过。原旧夹具将突变导航直接当图鉴，现房间路由会先进入遗传室，已适配内部入口，未改游戏路由去迁就旧测试。

这是现有导航入口层的审计，不等于所有二级页面、所有按钮业务或新历史扩展都完成。尚未发布的本地修复，发布结果随后记录。

## 0.13.20-preview · 植物病程、个人习惯与厨房送餐（本地已验证，公网待发布）

正式接入三类逐日植物病害与早期值班发现/真实护理；13类非工作习惯、实际房间位置、形成/中断/恢复、换代隔离；厨房喜好餐/宠物备餐/在场患者恢复汤、原库存与每日限制、保鲜入口及已发现Jasmine记忆。修复个人活动误标值班、水生宠物走到维修台、第五满容量档手动保存失败；keys-v2无损压缩兼容keys-v1/普通JSON，导出仍含原全局收藏。

完整115文件回归12933终态退出0（含100种子35日养成、300种子探险和最后模拟接口），在厨房合入前完成。厨房9相关/8年度2920日、原生按钮/刷新/英文768/390与64送餐记录五成熟档验证通过；合入主目录后主专项与Chrome58465终态退出0，20写入全成功10,175,792 UTF16字节，313源码资源检查通过。当前配置116文件，不把115回归冒充116完整命令。

全140项验收、部分生活交互、正式美术与历史大型扩展仍未完成；公网AI未部署。此前0.13.19预览ZIP是历史快照。

## 0.13.19-preview · 值班观察、维护日志与长期运营记忆（历史本地进度）

医务与温室的成功值班记录真实症状或种植风险，同一持续问题去重，复发重新记录。新增可手写、关联设备的维护日志，真实故障可回看先前记录。停电、大修、照护、收获、来访、冬季六类首次事件保留在房间记忆中，近期日志裁剪后仍可查看；实验体只接收自己亲历的记录。

三项实际浏览器专项、旧档迁移、移动界面和五档满容量储存验证通过，完整110文件回归退出0。其后补入夜间NPC健康/死亡、实验室天气与新闻阶段摘要，并修复满量摘要导致的保存配额问题；全部68人/90主题记录与五档容量保留，实际浏览器、相关存读回归及309资源检查通过。新增后的配置为111文件，其完整回归尚待取得，不混用先前110结果。0.13.19尚未发布。独立TargetPlacementValidator已在0.13.18公网验证出生、稀有度尺寸、安全间隔、完整连续路径、Bomb额外20%距离和原子批量生成；完整快乐俱乐部玩法仍未完成。

独立植物疾病、部分非工作习惯、特殊厨房功能、正式美术、历史扩展与原140项逐条验收仍未完整完成；公网AI未部署。

## 0.13.18-preview · 晨晚报告、100个运营事件与厨房生活

补齐首日主页晨报、真实日终晚报与最近7条夜间结果；新增19个独立运营问题至100事件/200分支。习惯保存中断与恢复，断电暂停用电岗位、逃离B07不工作。厨房新增恢复汤、库存/临期摘要与可开启的居民安全收获偏好饮食；修复检查挡住做饭、日报presented默认字段存读差异、英文混排。

验收采用分段：完整107文件入口首轮在expedition存读断言失败，已修复；35文件相关/剩余尾段退出0，所有107配置项均取得通过证据。100种子35日引擎、27000患者日、2920运营日及实际浏览器流程通过；不伪称首轮完整命令退出0。0.13.18已提交ca82b95，GitHub Pages71部署成功；公网六流程会话77969最终退出0，全部通过。公开仓库文件为提交时快照，最终回执记录在本地进度文件。

医务/温室早期提醒、部分非工作习惯、特殊厨房功能、正式美术与原140项验收仍未完整完成；公网AI未部署。

## 0.13.17-preview · 通讯订货、访客会诊与日报建议

通讯订货→隔日货箱→仓库验收使用原商队库存和物品实体，防止重复领取；真实购买/易物/出售接入收据与日报。放行医生访客可现场会诊，离开/隔离/留院/严重病况/封闭医务室不可服务。日报补仪器次日预报、六来源推荐与只读导航，旧档可选字段兼容。独立目标校验器新增原子批量出生。

完整140项验收、更多职业服务、正式美术和部分历史扩展仍未完成，公网AI未部署。完整102文件回归退出码0，公网0.13.17已部署并通过五条隔离浏览器流程。Pages70成功；完整140项验收及历史扩展仍未完成。

## 0.13.16-preview · 留院与出院

新增有限床位、跨日留院照护和食水消耗、复查/出院、当前留院记录保留、旧档默认普通访客；心理状态不自动隔离，封闭医疗室无扫描仪加成。更多访客类别、交易交接和完整140项验收仍未完成。实证见LAB-VISITORS-REPORT.md。

## 0.13.15-preview · 访客临床与在场一致性

已放行访客接入评估/照护/隔离、人物会面、实际用水和日报；不自动入住/排班，不在原聚落重复出现。新增专项与实际界面验证；更多访客类别、留院多日、交易交接、正式美术及两份规格未验收项仍待完成。

## 0.13.14-preview · 入口等候与核验

门口记录与商路独立；已认识NPC按持久日期来访，新闻43的登记冒牌者可由核验发现，放行会造成真实损失。记录、日报、房间位置及离开期间模拟接入。隔离等候不等于完整医疗或入住，更多访客类别/交易交接仍待完成。见LAB-VISITORS-REPORT.md。

## 0.13.13-preview · 门岗值班与袭击减损

实际成功安防班+在线摄像机+可用门锁+开放观察室可提前记录入口警报，并将原基地袭击房间损坏30降为15、安防损失20降为10。其他危机不受加成。旧档新增日期默认0，不追算旧班。完整门口身份核验仍待完成。详见LAB-SECURITY-DUTY-REPORT.md。

## 0.13.12-preview · 通讯值班实际联动

成功值班、设备在线及房间可用时开启隔日之外的新闻接收；每日至多一次，未结上限仍3。日报/新闻的商路确认与袭击记录提示来自实际车队状态，不代表已经抵达实验室门口。封闭、停电、停机和无当日值班不会生效。详见LAB-RADIO-DUTY-REPORT.md。完整目标仍在推进。

## 0.13.11-preview · 修复

新增休班临时替岗，保留原排班，已排班人员不跨岗顶替、隔离和疲劳过高人员不接班；医务值班不再给远方患者加照护信任。专项与长期回归见 LAB-DUTY-RELIEF-REPORT.md。继续保留全范围目标，不将本次修复视作所有运营规格已完成。

# 0.13.10-preview · 2026-10-07

- 新增独立TargetPlacementValidator，统一出生位置、尺寸、变形最大包络、safe gap、连续路径及Bomb额外20%间距。
- 非安全候选延迟生成，动态变更时暂停/隐藏；不改变存档schema或玩法货币。
- 这是基础组件，Happy Club完整小游戏及新养殖/食堂/遗传与滚动审计仍未实施。

# 0.13.9-preview · 2026-10-07

- 剩余24房补72跨日事件、108轻观察；27房达10/3容量。
- 162选择、两日复查、81逾期后果，有限物资成本与一次结算。
- 实验体事件增加在场校验，旧档见闻容量扩至327。
- 不改主线或解锁深层权限；仍保留正式美术与长线扩展待办。

## 0.13.7-preview — 实验室运营、27房间与90病长期平衡（2026-10-06）

90个独立病程参数；全宿主照护、150天接触与复发、真实种植制药闭环及365天记录压力测试。实验室加入12板块日报/60日归档、7岗位排班、13设备/7类维修件、4真实故障链、返回报告和居民入住。

27原房间ID保留，主次入口调用既有玩法；楼层图、专精、独立程序模型、12种摆件、供电/夜间状态与默认静音的轻合成环境声。100生活观察+104维护观察按游戏日触发，不直接发放奖励。旧存档追加字段，不追扣过去的运营日。

修复新旧维修同步、远方会诊、远方患者借用基地扫描器加成、停电监控和医疗按钮提示。未修改审定剧情、Host隐藏规则或既有结局。本轮并非所有历史扩展全部完成；正式插画、录音、每房最终重大故事容量和公网AI部署仍有缺口，见LAB-OPERATIONS-REPORT.md和ROOM-FUNCTIONALIZATION-REPORT.md。

## 0.13.6-preview — 90条新闻、实验室返回与设备模型

完成剩余50条独立中英文多阶段新闻，累计90/90；新增区域报告登记、有限领取/付费交接、夜间宵禁交易校验及真实储备/道路/市场效果。区域登记人物与既有NPC分离，不能算全部历史世界模拟完成。

修复实验室进入车厢后抽奖误锁：位置与表现模式分开，共用Road.atLab判断。修复白线高于车厢地板导致穿车；外部路面下降并保留深度遮挡。补齐10种不同制剂、患者床位、生态与收获卡片模型。具体范围与验证见NEWS-CHAINS-BATCH4-REPORT.md。
## 0.13.5-preview — 一次新增20条独立新闻与房间检查（2026-10-06）

新增20条：走失、避难登记、聚落损失、黑市车队改道、灰潮到来/减弱、酸雨、雷暴、沙尘、暴雪封路、高温、洪水、温室污染/粮食短缺/丰收、食品降价/药剂涨价、车辆求援、车队延误/提前。累计40/90。天气、道路、市场报价、真实库存、车队日程和住户记录作为来源；无车不出现求援，主动放归不报走失，暴雪须同时有同区域真实积雪封路。

15组相关回归通过，新增80种选择组合；存档容量40条，旧新闻保留。修复封闭房间仍能停留、无关事故导致完好房间可扣费修理。27间实验室房间逐个测试通过通用操作，但房间页尚无专属玩法操作入口，不能算全部完整利用；详见ROOM-USAGE-AUDIT.md。

## 0.13.4-preview — 独立新闻第二批（2026-10-06）

新增5条：16地铁入口重新开放、19通行证登记、22商队领队离世、24官员接替、28净水泵悬赏。绑定真实维修、登记、纪念册/继任及悬赏接受记录；伤病、离队或临时接班不误报死亡。20条独立新闻已交付，剩余70条未完成。

每条有两阶段回应、跨日跟进和中英文；纪念调用原系统并防止重复奖励，新官员信任独立增长，已处理悬赏不能继续扣勘查材料。存档容量由内容数量决定，原15条保存不丢失。17/18/20/21/23/25/26/27/29/30尚需底层世界状态，未用虚构公告冒充完成。


## 0.13.3-preview — 第一批独立新闻（2026-10-06）

15/90主题已接入独立多阶段流程：饮水风险与恢复、药柜短缺、医疗队交接、检疫站、发热登记、动物病例、植物病害、种子召回、污染批次、燃料、电网、道路塌陷、维修与隧道入口封锁。初报→选择→1–3游戏日跟进→再次选择→下一日结案；超期无人援助会记录，并按主题减少2储备或增加压力。每主题每档只完成一次，避免刷奖励。

60组合、旧档、重复、资源不足、真实状态及读档验证通过；浏览器实际点击、跨日跟进、英文和1366/768/390宽度通过。剩余75主题仍未交付，下一批处理16–30。未加入配音或收费API调用。

## 2026-10-06 — 温室 / 医务室基础闭环（预览）

- 新增200条植物名录、基础种植收获和跨日医疗照护。完整MEGA扩展尚未完成。
- 修复分类导航滚动、返回空页及旧导航遮挡。
- 公网AI仍未启用。

## 2026-10-06 — 顶部等级横向显示修复

研究等级与时间在同一横向基线显示；日期和行动点不再自动断行。窄屏顶部栏使用独立布局行，内容区自动按实际栏高避让。中英文及1920、1366、1024、768、390宽度已检查。公开游戏仍使用本地备用对白，云端AI尚未开放。

## 0.13.0-preview · 2026-10-06 · 本机验证版（未发布公网AI）

- 新增服务器端AI权限审批，兑换后待审批、主机SSE通知、批准/暂停/封禁，每人20次/日、全局100次/日。
- 未批准/已封禁/超额在OpenAI之前拦截，失败仍有本地对白，权限与玩家存档分离。
- 主机后台仅本机可访问；不是公网管理员认证。Vercel/Supabase连接和生产持久化仍待完成。

## 0.12.9-preview · 2026-10-06

- 第09张CG_ACT2_BLANK_TAPE_FINGERPRINT正式接入，使用用户提供第一版，daily_nickname第15行从08交叠切换。
- 700ms交叠、9秒1.00→1.03微推，观看解锁；不是正式命名，不改台词或命名状态。
- 保留07→08→09顺序及旧存档格式，验证回看、存读档和图库。

## 0.12.8-preview · 2026-10-06

- 接入第08张CG_ACT2_BAD_NICKNAMES，daily_nickname第8行转身时从07交叠切换。
- 700ms交叠、9秒1.00→1.03微推；观看解锁。
- 第09张仅预留CG_ACT2_BLANK_TAPE_FINGERPRINT与第15行指印节点，到这里回到黑底，不使用其他CG替代。
- 保留07原图、审定台词、章节触发与旧存档。

## 0.12.7-preview · 2026-10-06

- 第07张CG_ACT2_B07_NAMEPLATE在daily_nickname第0行铭牌文字出现。没有制作第08张。
- 800ms淡入、9秒1.00→1.03微推，聚焦铭牌与空白胶带，观看解锁。
- 原台词、章节推进、存档格式保持不变。桌面与触屏浏览器测试通过。

## 0.12.6-preview · 2026-10-06

- 修复点击BACK后焦点仍在按钮、Space误触再次回看的问题。
- 新增CG_ACT1_BLACKOUT_BACK_TO_BACK，在daily_blackout第19行Jack坐下时800ms淡入。
- 11秒1.00→1.025微推、2px横向漂移；不提亮、不动画角色，观看解锁图库。
- 保留既有日常场景触发顺序与全部审定台词，显示标题为指定ACT I。
- 桌面与触屏尺寸验证新CG、存读档、回看、图库；无控制台错误。

## 0.12.5-preview · 2026-10-06

- daily_cup第6行递出搪瓷杯时显示CG_ACT1_CHIPPED_MUG。此前使用空碟CG建立连续日常视觉。
- 700ms交叠，9秒1.00→1.035微推、-2px横向漂移；首次观看解锁。
- 仅调整daily_cup的ACT I显示标题，不改变章节推进、台词或存档格式。

## 0.12.4-preview · 2026-10-05

- ACT I新增CG_ACT1_EMPTY_DISH，在project_survival第6行食盆到位时淡入。原文不变。
- 800ms淡入，9秒1.00→1.03推镜，2px竖向漂移。观看解锁，图库隐藏未看缩略图。
- 桌面1366×768与触屏768×1024验证存读档、刷新、回看、图库，无控制台错误。

## 0.12.3-preview — 2026-10-05 圆润玻璃对白框

- 底部改为浮动圆角卡片、透明渐变、磨砂与柔和玻璃反光。
- 优化系统阅读字体、明亮字色、字重/行距；独立角色标签与圆形推进控件。
- 修复CG在16:9遮住对白和工具栏的旧图层问题。
- 中英文、大字号、低透明度、桌面/iPad/手机布局验收；不改剧情或存档。
- 详情见DIALOGUE-GLASS-REPORT.md。

## 0.12.2-preview — 2026-10-05 生命维持维修CG

- 序章第13句接入用户提供的维修原图，顺序为发现→检查→维修；原台词与旧存档保留。
- 700ms交叠、9秒1→1.035微幅推镜，仅水平2px移动；无人物变形。
- 第三张CG首次观看解锁，保存/读档/回看恢复正确画面。
- Jack长期美术规范写入代码数据与STORY-CG-ART-DIRECTION：避正面露脸，必要正面戴磨旧深色帽子遮脸。

## 0.12.1-preview — 2026-10-05 序章双CG / iPad全屏

- 保留首见图，第6句接入指定的第二张玻璃温度图；两张分别按实际观看解锁。
- 800ms淡入、650ms真实交叠与7–8秒微幅推镜；减少动态设置保持静止。
- 兼容Safari前缀全屏与对应退出，菜单留在全屏内；visualViewport、安全边距和横竖屏适配。
- 修复触屏关闭菜单后的焦点；保存/读取/回看和养成模式保留。
- 实体iPad尚未验收；不支持原生全屏时提供铺满可用视口和说明。详见PROLOGUE-CG-REPORT。

## 0.12.0-preview — 2026-10-05 审定剧情整合与全屏演出

- 原ID逐字接入六个审定中英场景、六段日常和42条行级操作；12个保护场景哈希不变。
- ACT IX仅4+2选择，门后自动分流；旧flags/存档与路线保留，BLACK计时按游戏日推进。
- 独立全屏剧情播放器、首见CG、AUTO/已读跳过/日志/回看、10手动+quick+auto、CG画廊。
- 顶部实验室/货币栏固定，剧情手动记录支持备用恢复。
- 未完成历史需求见TASK-AUDIT；E-3后果待审定，其余CG和正式音频尚未提供。

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


## 0.13.1-preview · 2026-10-06 — 地区疫情、医疗新闻与温室加工

- 加入90种疾病风险分类、症状与宿主筛选；宠物、其他怪兽和已接触NPC的医疗记录、隔离及入所观察。
- 地区疫情沿聚落道路传播，检疫站影响控制；当地医疗/食品价格及高风险道路成本读取实际疫情状态。
- 新闻读取实际天气、商队、物资、疫情和死亡记录；90个新闻主题已建档，但并非90条完整独立事件链。
- 温室加入六种加工、保存期限/出售价值、多代品系与三种遗传特征、品系改名；200种植物使用可替换程序SVG。
- 修复新救援宠物在存读档时补建医疗记录导致的状态不一致，补齐加工和品系改名操作入口。
- 配音由用户后续提供；公网AI仍未开放，正式美术及历史大型扩展仍有剩余。

## 0.13.2-preview · 2026-10-06 — 症状行为与医疗运输

- 疾病现在影响进食效果、训练收益、睡眠、补水、污染压力和探索疲劳；潜伏期无提前惩罚，恢复观察影响减弱。
- 成功实验/喂食/出行及停电、隔离等实际行为检查风险，每位患者同日只进行一次有条件的行为风险判定；无效命令和菜单不能刷新概率。
- 区分照护方向，普通身体照护不再对污染病统一算有效，心理恢复不清除剧情记忆和隐藏旗标。
- 医疗补给队使用实际道路、预留来源地药品和燃料，封路等待或改道，到达只交付一次；存档与新闻记录完整保留。
- 修复道路目的地不能操作当地医疗的问题，禁止在外地遥控实验室患者治疗。
- 90种疾病的症状和照护说明补齐本地英文，修复医疗页标签语言残留。
- 此版本仍为预览，完整90类新闻事件链、全部专属病因、正式美术和公网AI仍有剩余。


### 0.13.7剧情CG补丁
接入用户提供的第11张CG，在首词对白出现时展示；第10张源图待提供，仅预留，不替代。原剧情和首词存档兼容保留。

### 0.13.7剧情CG补丁：第10张
补齐首词前维修镜头，10→首词→11固定顺序及550ms双图交叉淡化。累计11张正式CG，首词与存档格式保持不变。

## 0.13.8-preview · 2026-10-07
厨房、仓库、工坊各补齐10轻观察/3跨日事件；新增18处理分支、复查/逾期/有限物资成本与兼容存档。其余24房事件池继续待补齐。


## 0.13.22-preview — navigation rails
- 左侧导航外框固定于视口，菜单列表独立滚动，搜索与折叠入口留在原地。
- 补齐温室、医务室、新闻、日常运行、天气、地下经济、远征物品分类栏固定规则；保留衣橱部位菜单。
- 修复远征独立终端缺少正文滚动容器、矮屏正文空间过小。新闻卡片的行动按钮不作为固定导航。
- 隔离测试存档验证5种尺寸×9模块，不触碰玩家进度。

## 0.13.23-preview — Happy Club playable local candidate

- 永久地图/道路/停车入场、每天8000/12000/18000最多三轮、25秒挑战、六稀有度和九种移动；黑靶结束本轮且保留已赚Token。
- 六级Token真实兑换、全部兑换、跳过动画、最近100条记录、史诗第六次保底、专属/唯一物品排除，武器经原独立副本/待领取路径获得。
- 11项靶场成就、真实命中率、RECOVERED结算统计修复、五位人物程序外观和交谈；高对比和24/32/48px光标按存档保存。
- 专项与三宽度浏览器验证已通过。120文件按前118文件及末两文件修复复验完成；原全套运行曾失败，不记为一次性通过。公开发布待验收。
- 活动/新闻、动物料理等新奖池和正式美术仍欠项；畜牧40物种、个体与遗传核心已开始但未接入正式游戏，不称畜牧已完成。

## 0.13.24-preview — Homestead first playable batch + club schedules

- Laboratory → Homestead: exact unlock resources; ordinary farm supply; pens, names, feed/water, production batches, growth, saved breeding/lineages, veterinary care and independent death records. Eight farm unit/integration suites plus three viewport native UI tests.
- Real greenhouse harvest-to-feed/timber and manure-to-compost; invalid/repeated actions remain atomic. Missing old-save farms stay locked without retroactive RNG or production.
- Forty replaceable procedural animal illustrations; final painted art, rare acquisition paths, 100 farm events, plant cultivar expansion and canteen remain pending.
- Happy Club festival, static night, actual adjacent-road bandit closure/news, language-stage reactions and nine target designs.
- Existing 100-seed long runs, greenhouse, disease catalog, full merge flow and 20 story chapters passed targeted regression; 334 source resources HTTP pass. This is a tested partial expansion, not completion of every historical request.
