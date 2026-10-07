# 实验室未完成行为核对 · 2026-10-07

本文件仅记录已直接检查源码的差距，不用测试数量替代规格逐条验收。所有原100运营+40房间条款仍保留在LAB-SPEC-ACCEPTANCE-INDEX.md。

| 条款 | 直接检查的现状 | 尚需实现/证明 |
| --- | --- | --- |
| LXXXVIII Medical Duty | operations.js dutyDay 的 infirmary 成功班次仅给在场患者 medicalTrust +0.3 | 根据真实病例和当前症状做早期发现；不能给远处患者、无症状者或隐蔽病因编造诊断；结果保存和一次性反馈 |
| LXXXIX Greenhouse Duty | greenhouse 成功班次给植物 health +0.8 | 根据真实缺水、健康、害虫和污染做早期问题发现；非随机假警报；不覆盖植物原疾病/生态值 |
| XCVI Important Memory Events | finish 存 firsts.harvest/patient/blackout；通讯首次值班已存 | FIRST MAJOR REPAIR、FIRST VISITOR、FIRST WINTER 的条件、保存和自然回收应逐项核对；firsts.patient 目前按 medical:treat记录，不直接等于首次发现患者 |
| IV Evening Report | 当前晚报保留睡前最终状态、夜间结果和运营notes，交易收据已接入 | 专门核对NPC死亡/受伤和当天新闻变化是否逐项形成差量，不能仅凭最终病例快照宣称完整当天变化记录 |
| XXII–XXIV Personal Routines | 已形成的工作排班习惯及中断/恢复有真实记录 | 所列非工作习惯（看第一株植物、睡门边、宠物偷水果/跟维修等）仍需要独立位置/条件/行为与验证，不能用排班频率代替全部个人习惯 |
| 07 Kitchen | 真实库存摘要、原口粮/恢复汤、居民可开启安全收获偏好选择已实现 | 宠物餐、茶饮、完整配方收藏、厨房特殊生活回调仍需各自对应原要求；primary主按钮文字目前仍叫恢复餐但默认cook保留ration，应统一入口含义 |
| LXXXIV Maintenance Log | 有程序生成的有界notes/history | “Jack可以写”若要求玩家编辑维护记录，现界面没有对应输入/保存操作；需按原规格补可写日志，而非仅系统日志 |
| 正式房间美术与声音 | roomData.background normal/damaged/upgraded/night仍为null，渲染由程序SVG负责，ambientSoundId为合成声路由 | 不能称正式手绘图/录音完成；27房间真实主题几何已有，可替换资产架构与主题差异需保留 |

本次核对时完整回归会话42914仍在运行。当前已验证输出不等于最终退出0，最终结果由verification/lab-latest-full-regression.log和该会话终态决定。回归期间未改动正在被测的运行源码，避免结果混用不同代码版本。

## LXXXVIII/LXXXIX 下步实现的数据依据

直接读取illness.js确认INCUBATING状态和d.incubation门禁；疾病临床英文已有ClinicalEnglish.records[diseaseId].symptoms，不需重新翻译或编造诊断。医务提醒应只来自真实成功值班、存活在场患者及已出现症状的条件；不自动设assessed、不提前暴露潜伏期、不对远处NPC产生本地提醒、不改病程/属性。疾病病况在原Infirmary.observe中推进，因此提醒应在本日观察完成后读取，不能用尚未推进的beginDay病况作为当天最终结果。

温室原Garden.observe会实际推进水分、健康、害虫、污染。提醒应读取该轮真实结果与现有植物uid，绑定成功值班和开放/供电条件；不加入伪造疾病、不提前提示未成熟收获、不重复增加健康。健康改善原+0.8保留，其与问题发现不是同一效果。

此段是源码核对后的实现边界，不是功能已接入声明；当前正式代码仍只含既有信任/健康值班效果。最新完整回归42914正在100种子×35日（每日至多4个动作）的完整Engine循环，当前CPU已确认增长到509.48秒，保持同一进程。完成后再实施上述行为，避免在运行中的全套测试混用代码。
