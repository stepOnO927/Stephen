# 审定剧情整合报告 · 0.12.0-preview

2026-10-05，St3phEn。以用户提供的Claude C-1至C-9双语原文为准；没有为过渡新增哲学总结。范围是本轮整合与演出，不是完成所有历史扩展。

## 1. 文件

新增：js/data/storyRevisionScenes.js、storyRevisionDaily.js、storyRevisionPatches.js；js/story/revision.js、presentation.js、player.js；story-player.css；assets/story/cg/prologue_b07_first_sight.png；tests/story-revision.test.cjs、story-presentation-save.test.cjs、story-player-browser.cjs；本报告和TASK-AUDIT.md。

接入修改：index.source.html、game.js、navigation.css；js/state.js、save.js、meta.js、engine.js、storyMode.js、narrative.js、jackStory.js、narrativeUI.js、storyEffects.js、navigation.js、navigationData.js、ui.js、dialogue/voices.js、story/textRegistry.js、data/updateLog.js；server.js静态白名单；构建脚本、phase8测试夹具、ARCHITECTURE.md、CHANGELOG.md、TASK-STATUS.md。index.html及英文语言包为生成文件。

## 2. 替换场景

p8_lock_after、project_mia、project_zero、project_incident、project_black、project_open_door。原sceneId保留；六场CN/EN逐行与审定数据匹配。project_open_door拆为原intro、四个接续子节点和原response，不改变批准的正文顺序。

行级补丁15场：jack_name、bseries、eden、chamber、between、last_door、final、p8_threshold、p8_first_steps、p8_sea_admission、p8_stay_threshold、p8_ask_inside、p6_ending_we、p8_we_leave、p6_ending_sea。原系统前七项使用project_前缀，保留现有ID并映射别名。42条删/替换操作全部匹配到目标；未以整场重写代替行级精简。

## 3. 新增场景

daily_cup、daily_nickname、daily_blackout、daily_cooking、daily_fever、daily_remote。分别15、19、26、29、29、25个beat；独立可维护数据，无奖励任务标题，无Boss或新增玩法。四个Q1回复子节点为project_open_door_q1_world/hurt/leave/silence，仅承载批准的接续和共同正文。

## 4. 新flags

42个默认false，完整列表由js/story/revision.js统一声明：

JASMINE_MEMORY_KNOT、JASMINE_MEMORY_SINK、JASMINE_MEMORY_PLATE、JASMINE_MEMORY_REMOTE、RADIO_GIRL_NOT_HEARD_SINCE、B07_NOT_JASMINE_ACKNOWLEDGED、ZERO_FILE_CONTRADICTORY、ZERO_FILE_MODIFIED_AFTER_POWER、ZERO_REDACTED_LINK_B、B07_DEFERRED_ZERO_FILE、B07_KNOWS_SWITCH、CI0012_DUPLICATE_ENTRY、CI0012_FUTURE_DATE、DOOR_OPENED_UNEXPLAINED、BLACK_ORDER_17C_KNOWN、HALE_CONTACT、CRA_GUARDIAN_OFFER_MADE、EDEN_E3_COUNTDOWN_72H、DOOR_INSIDE_RELEASE、KEY_SHARED、ACCESS_RULES_SHARED、JACK_FEAR_ADMITTED、MUG_IN_CHAMBER、JACK_WARNING_CHIP_VALID、NAME_TAPE_FINGERPRINT、B07_REJECTED_NICKNAMES、B07_ACCUSED_JACK_BLACKOUT、B07_MIRROR_AVERSION_SEED、JACK_LEFT_DURING_BLACKOUT、B07_WRONG_SALT_SUGAR、B07_HONESTY_PERMISSION_USED、TEMP_LOG_STARTED、B07_TRACKS_JACK_TEMP、B07_HAND_TURN_SEED、OLD_GEL_CALLBACK、NO_SIGNAL_MONITOR、ACT_IX_DONE、OPEN_DOOR_Q1_world、OPEN_DOOR_Q1_hurt、OPEN_DOOR_Q1_leave、OPEN_DOOR_Q1_silence、TODO_NARRATIVE_RESOLUTION。

事实在对应beat到达时记录；不会开场全授予，也不将Host标成玩家任务。

## 5. ACT IX

Q1有效ID只有world/hurt/leave/silence。批准接续后到p8_lock_after，Q2只有open/keep。unlock并入open；not_ready/not_me/honest/unknown及第二个silence不再提供。open同时接内侧释放、共享钥匙和规则，并写旧系统兼容flag。Q1非silence写JACK_FEAR_ADMITTED。

门后不弹“最后在哪里”选择：fear≥25、trust<0或resentment≥35→stay；autonomy≥12且trust<12→walk_alone；Jack控制高于诚实5或旧lock_retained→ask_inside；否则first_steps。分流由隐藏值决定，保护节点中的旧选择数据不删除，运行时自动执行合适接续。

## 6. ID问题

没有重复scene ID。全表扫描另发现两项旧choice问题并修复：rare_clock完全相同的第二个silence去重；project_final_response原两个creature对应不同决策，将autonomy决策的raw ID改为autonomy，保留实际结局逻辑。共同门后正文使用稳定共享文本ID供已读跳过，不是重复scene/choice。

## 7–8. 兼容与旧存档

保留所有旧flags。shared_release→DOOR_INSIDE_RELEASE、shared_rules→ACCESS_RULES_SHARED、fear_leave_admitted→JACK_FEAR_ADMITTED；新open反写旧shared_release/shared_rules/door_unlocked。顶层schema仍4，新增story.revision.version=1。旧active游标映射到对应/最近新行并限界，原route/ending判定保留。

旧档没有新flag时false；旧章越过daily时放optionalDaily供菜单记忆回放，不连播补课。旧档没有执行新BLACK场景不自动造倒计时。旧门后进行中的档识别phase和路径继续，ACT X等待门后段完成。手动记录按timeline独立，损坏主记录可读备用；CG及已读内容导出/导入，删档清除该timeline的手动/备用/已读，保留既有全局收藏语义。

## 9. 日常安排

| 场景 | 进入章节 | 语言表现 |
|---|---|---|
| daily_cup | ACT II，I结束后 | 无B-07对白 |
| daily_nickname | ACT III，II结束后 | 无B-07对白 |
| daily_blackout | ACT IV，III结束后 | Stage0–1 |
| daily_cooking | ACT V，IV结束后 | Stage1–2原文 |
| daily_fever | ACT VII，VI结束后 | Stage2原文 |
| daily_remote | ACT X之前、IX分流完成后 | Stage3–4 |

按章节一次性入队，低情绪强度，早期语言使用场景表现阶段，不降低角色持久成长阶段；没有成熟化润色。

## 10. incident

左开关、重复CI-0012及同一错字、未来一天/空确认人、门自己打开、门挡另一侧均按审定正文正常显示。仅隐藏flag记录前四项；没有ANOMALY DETECTED弹窗、红字解说或时间异常结论。

## 11. BLACK倒计时

读到结尾启动e3={startedDay,startedChapter,remainingSeconds:259181,status:'running'}，对应批准的71:59:41。按照游戏日变化扣86400秒/日，章节和存档保存；不是挂机消耗现实72小时。ACT XV原有时间推进会使其到期。到期置expired和TODO_NARRATIVE_RESOLUTION且幂等，不添加后果、伤害、新结局或自行写回收文本。

## 12–13. Host与Jasmine

Host seeds只存隐藏flags，与镜面回避/翻手背/桃子习惯原文结合；不亮标、不加正常日志、不作为任务。?debug=1开发面板才可查。

Jasmine KNOT/SINK/PLATE/REMOTE按实际beat记录；jasmineCount提供0–4计数给后续检测，不自动产生结局。机构、Hale人物卡集中在storyRevisionScenes的数据常量中。Jasmine不是被替代的恋爱/宠物好感关系。

## 14. 体温回收

daily_fever写TEMP_LOG_STARTED和B07_TRACKS_JACK_TEMP；p6_ending_we既有互记体温beat必须两者都true才显示。旧档未经历前置时过滤该句，避免结局凭空回忆；不重写结局其余功能。

## 15–16. 完整性和保护

扫描全表nextNode与choice引用有效，所有补丁找到原目标，全20章路径无undefined。12个受保护节点的完整JSON SHA256与修改前基线一致：project_b07、survival、wasteland、second_abyss、first_word、sky、red_thread、abandoned、p8_tool、p8_alarm、p8_walk_alone、p8_infinity。

“你的手。”“我开过——没开过另一扇门。”“先到这边来。”“包括不？”均保留。原始scene数据保护与运行时自动分流兼容；未删原结局/hidden flag。

## 17. 仍需主编剧确认

- REQUIRES_NARRATIVE_APPROVAL：工资句、三个极弱Host seeds、机构/Hale命名。
- TODO_NARRATIVE_RESOLUTION：E-3到期后具体剧情。
- 源稿内部矛盾：daily_cooking“你说过我可以说实话。”含第一人称，与源稿自检“Stage1–2没有我”不一致；逐字保留，未擅改。
- wasteland两条受保护内心句保留。既有首次自称场景不删除。没有新增未经审定的过渡对白。

## 18. 测试与演出

- 54模块回归中前53完成；最后聊天测试的本机连接被沙箱EACCES阻止。对最后模块使用允许本机连接的环境复测，5/5通过。不是把基础设施失败忽略成通过。
- story-revision：文本逐字中英、12保护哈希、42补丁、引用/去重、六daily、ACT IX、20章、计时存档/到期、旧档可选场景、体温前置通过。
- story-presentation-save：十个独立位置+quick/auto、备用恢复、导出全局CG/已读、Iron限制、timeline删档通过。
- 实际Chrome：1920×1080、1366×768、390×844首见CG、Space/打字、Save/Load/刷新、回看选择flag恢复、日志/画廊、AUTO/SKIP、无横向溢出、养成喂食与顶部固定、无pageerror通过。截图verification/vn-first-sight-*.png。
- 源码HTTP入口与portable file://入口：所有脚本/CSS/CG资源、英文正文和菜单、按住Ctrl快进、全屏进入/退出均通过，零脚本/缺失资源错误。新增存档测试独立复测通过并纳入今后的全套脚本。

全屏播放器独立CSS/DOM，养成逻辑保留。提供的PNG仅在project_b07真正首次看到舱内生物时展示，前四beat黑底。其他场景没有资源时黑底，不冒充全部CG已制作。音量有接入设置，正式BGM/配音尚未提供；公开静态版不会调用私人AI密钥。
