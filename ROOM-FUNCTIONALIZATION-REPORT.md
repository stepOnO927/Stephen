# 27房间功能化 · 0.13.7-preview

此表由实际房间数据生成。27原ID保持；物理房间等级和专属设施等级独立。主/次入口复用既有控制器，不复制一套温室、医疗或武器系统。

| 房间 | ID | 层 | 主入口 | 次入口 | 主体模型 | 生活/维护观察条目 | 故障链 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 培养舱 | containment | 0 | 观察B-07 (observe) | food / medical / roomMemory | chamber | 13 | fault:doorFault |
| Jack 的房间 | quarters | 0 | 睡眠 (rest) | journal / inventory / jasmine | cot | 5 | — |
| 它自己的空间 | living | 0 | 衣物与收藏 (wardrobe) | privacy / bedroom / habits | nest | 5 | — |
| 医疗室 | medical | 0 | 查看患者 (patients) | pharmacy / recovery / quarantine | bed | 13 | — |
| 遗传实验室 | genetics | -1 | 突变分析 (mutations) | experiment / serums / plantArchive | scanner | 4 | — |
| 工程室 | engineering | -1 | 基地维护 (maintenance) | power / water / roads | toolwall | 29 | fault:airClog |
| 厨房 | kitchen | 0 | 准备恢复餐 (cook) | food / harvest / pharmacy | stove | 6 | — |
| 仓库 | storage | 0 | 整理库存 (inventory) | valuables / trade / bedroom | racks | 5 | — |
| 温室 | greenhouse | -1 | 检查种植槽 (plants) | seeds / ecology / harvest | hydroponics | 22 | — |
| 工坊 | workshop | -1 | 武器工坊 (weapons) | weapons / parts / roads | weaponbench | 4 | — |
| 观察室 | observation | -1 | 观察公共区域 (cameras) | habits / pets / visitors | monitors | 12 | — |
| 档案室 | archive | -1 | 查阅档案 (storyFiles) | medicalArchive / newsArchive / personnel | files | 8 | — |
| 供电室 | power | -2 | 供电与分配 (power) | maintenance / powerPolicy / climate | generator | 14 | fault:powerDrop |
| 净水室 | water | -2 | 净水与供水 (water) | waterTest / maintenance / ecology | tank | 24 | fault:waterLeak |
| 通讯室 | radio | -1 | 收听新闻 (news) | caravans / climate / dailyReport | radios | 10 | — |
| 研究大厅 | hall | -1 | 规划研究 (research) | plantArchive / diseaseArchive / mutations | whiteboard | 4 | — |
| 封锁下层 | lower | -2 | 调查下层设施 (survey) | restore / materials / leave | barrier | 3 | — |
| 零号通道 | zero | -3 | 零号资料 (zeroArchive) | continuity / survey / leave | airlock | 2 | — |
| 黑级研究翼 | black | -3 | 权限与指令 (blackOrders) | research / storyFiles / e3 | authority | 2 | — |
| 维修夹层 | crawl | -2 | 检查维修旁路 (repairBypass) | maintenance / materials / survey | pipes | 3 | — |
| 旧育成室 | nursery | -2 | 照看获救生物 (pets) | patients / storyFiles / roomMemory | incubators | 3 | — |
| B 系列库房 | series | -2 | 查看B系列遗物 (seriesRelics) | storyFiles / objects / roomMemory | relicCases | 3 | — |
| 停用手术室 | surgery | -2 | 高级照护 (advancedMedical) | recovery / medicalArchive / survey | surgicalTable | 3 | — |
| 地下三层 | sublevel | -3 | 深层设施调查 (survey) | restore / materials / leave | ventShaft | 2 | — |
| 未登记楼梯 | stairs | -3 | 数台阶 (steps) | markSteps / listen / leave | stairs | 2 | — |
| 黑级动力核 | core | -3 | 查看动力核 (corePower) | coreOverride / maintenance / continuity | reactor | 2 | — |
| 无编号房间 | unnumbered | -3 | 查看未登记终端 (unknownTerminal) | objects / dreams / roomMemory | unmarked | 1 | — |

## 可验证行为

- 独立楼层图、27种主体几何、灯色与3个陈设标识；程序SVG有分面与渐变，可替换PNG/WebP。环境声为27种很轻的合成声配置，默认静音，切换/关闭会停止旧声源。
- 主次按钮全部在隔离浏览器点击检查；电力、净水、维修旁路与动力核显示独立实时读数。公共监控缺电/摄像机停机时离线；B-07私人摄像头需要同意。
- 已认识且信任足够的人可入住，床位取决于开放的Jack房间等级，上限8。值班、休息、隔离、医疗和旧人物关系使用同一人物ID。
- 温室、医疗、工坊有可逆专精；分区勘查和回收有限，台阶记录保留，动力核旁路实际扣资源/增加基地污染。
- Jasmine记忆盒只显示已经发现的四个原剧情旗标；本轮不创造她的额外故事，不显示Host seeds。

## 仍不能说已完成

- 尚未达到每个房间10条轻事件+3条重大事件的最终内容容量；现有池的准确数目见表。4条真实连续故障链集中于相关设备房，不是81条独立大型事故剧情。
- 原有旧翼6房仍是独立模块，没有混入27房计数。其复杂连续性长线、所有历史人物家庭/战争/继任任务不在此次已完成范围。
- 本轮是可替换程序美术与合成环境声；不冒充正式手绘背景、角色动画或录制配音。
