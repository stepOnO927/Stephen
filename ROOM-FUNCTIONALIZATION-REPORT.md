# 27房间功能化 · 0.13.18-preview

此表由实际房间数据生成。27原ID保持；物理房间等级和专属设施等级独立。主/次入口复用既有控制器，不复制一套温室、医疗或武器系统。

| 房间 | ID | 层 | 主入口 | 次入口 | 主体模型 | 生活/维护观察条目 | 故障链 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 培养舱 | containment | 0 | 观察B-07 (observe) | food / medical / roomMemory | chamber | 13 | fault:doorFault / incident:hatch_spring / incident:fog_patch / incident:tray_edge |
| Jack 的房间 | quarters | 0 | 睡眠 (rest) | journal / inventory / jasmine | cot | 10 | incident:cot_leg / incident:locker_hinge / incident:damp_blanket / incident:ops_bunk_latch |
| 它自己的空间 | living | 0 | 衣物与收藏 (wardrobe) | privacy / bedroom / habits | nest | 10 | incident:privacy_lamp / incident:loose_rug / incident:shelf_reach |
| 医疗室 | medical | 0 | 查看患者 (patients) | pharmacy / recovery / quarantine | bed | 13 | incident:bed_brake / incident:thermometer_case / incident:privacy_screen / incident:ops_thermo_offset |
| 遗传实验室 | genetics | -1 | 突变分析 (mutations) | experiment / serums / plantArchive | scanner | 10 | incident:sample_labels / incident:cooler_door / incident:microscope_lens / incident:ops_exhaust_gasket |
| 工程室 | engineering | -1 | 基地维护 (maintenance) | power / water / roads | toolwall | 29 | fault:airClog / incident:tool_return / incident:plan_revision / incident:bench_ground / incident:ops_heater_guard |
| 厨房 | kitchen | 0 | 准备餐盒 (cook) | food / harvest / pharmacy | stove | 10 | incident:kitchen_seal / incident:kitchen_labels / incident:kitchen_drain / incident:ops_cold_coil |
| 仓库 | storage | 0 | 整理库存 (inventory) | valuables / trade / bedroom | racks | 10 | incident:storage_damp / incident:storage_ledger / incident:storage_crate / incident:ops_load_brace |
| 温室 | greenhouse | -1 | 检查种植槽 (plants) | seeds / ecology / harvest | hydroponics | 22 | incident:bed_leak / incident:seed_envelope / incident:shade_screen / incident:ops_root_mat |
| 工坊 | workshop | -1 | 武器工坊 (weapons) | weapons / parts / roads | weaponbench | 10 | incident:workshop_vice / incident:workshop_sparks / incident:workshop_batch / incident:ops_grinder_flange |
| 观察室 | observation | -1 | 观察公共区域 (cameras) | habits / pets / visitors | monitors | 12 | incident:camera_glare / incident:clock_sync / incident:recorder_cable / incident:ops_camera_blind |
| 档案室 | archive | -1 | 查阅档案 (storyFiles) | medicalArchive / newsArchive / personnel | files | 10 | incident:folder_mould / incident:catalog_gap / incident:reader_fan / incident:ops_ups_cell |
| 供电室 | power | -2 | 供电与分配 (power) | maintenance / powerPolicy / climate | generator | 14 | fault:powerDrop / incident:battery_clip / incident:fuel_strainer / incident:breaker_cover / incident:ops_brush_dust |
| 净水室 | water | -2 | 净水与供水 (water) | waterTest / maintenance / ecology | tank | 24 | fault:waterLeak / incident:test_cup / incident:tank_lid / incident:drain_mesh / incident:ops_gauge_zero |
| 通讯室 | radio | -1 | 收听新闻 (news) | visitors / deliveries / caravans / climate / dailyReport | radios | 10 | incident:aerial_clamp / incident:message_slip / incident:speaker_cone / incident:ops_coax_water |
| 研究大厅 | hall | -1 | 规划研究 (research) | plantArchive / diseaseArchive / mutations | whiteboard | 10 | incident:board_leg / incident:projector_dust / incident:meeting_chairs / incident:ops_floor_cable |
| 封锁下层 | lower | -2 | 调查下层设施 (survey) | restore / materials / leave | barrier | 10 | incident:barrier_lamp / incident:debris_edge / incident:survey_anchor |
| 零号通道 | zero | -3 | 零号资料 (zeroArchive) | continuity / survey / leave | airlock | 10 | incident:airlock_seal / incident:gauge_window / incident:reader_contacts |
| 黑级研究翼 | black | -3 | 权限与指令 (blackOrders) | research / storyFiles / e3 | authority | 10 | incident:terminal_key / incident:seal_box / incident:desk_lamp |
| 维修夹层 | crawl | -2 | 检查维修旁路 (repairBypass) | maintenance / materials / survey | pipes | 10 | incident:pipe_wrap / incident:hatch_pin / incident:chalk_marks / incident:ops_sump_float |
| 旧育成室 | nursery | -2 | 照看获救生物 (pets) | patients / storyFiles / roomMemory | incubators | 10 | incident:incubator_latch / incident:toy_stitch / incident:quiet_vent / incident:ops_heat_patch |
| B 系列库房 | series | -2 | 查看B系列遗物 (seriesRelics) | storyFiles / objects / roomMemory | relicCases | 10 | incident:case_pad / incident:shelf_card / incident:case_lock |
| 停用手术室 | surgery | -2 | 高级照护 (advancedMedical) | recovery / medicalArchive / survey | surgicalTable | 10 | incident:table_pad / incident:lamp_arm / incident:instrument_wrap / incident:ops_hinge_residue |
| 地下三层 | sublevel | -3 | 深层设施调查 (survey) | restore / materials / leave | ventShaft | 10 | incident:vent_damper / incident:cable_guard / incident:survey_tripod |
| 未登记楼梯 | stairs | -3 | 数台阶 (steps) | markSteps / listen / leave | stairs | 10 | incident:tread_strip / incident:handrail_joint / incident:marker_smear / incident:ops_step_edge |
| 黑级动力核 | core | -3 | 查看动力核 (corePower) | coreOverride / maintenance / continuity | reactor | 10 | incident:coolant_joint / incident:shield_bolt / incident:service_probe / incident:ops_bond_strap |
| 无编号房间 | unnumbered | -3 | 查看未登记终端 (unknownTerminal) | objects / dreams / roomMemory | unmarked | 10 | incident:door_label / incident:desk_socket / incident:floor_tile |

## 可验证行为

- 独立楼层图、27种主体几何、灯色与3个陈设标识；程序SVG有分面与渐变，可替换PNG/WebP。环境声为27种很轻的合成声配置，默认静音，切换/关闭会停止旧声源。
- 主次按钮全部在隔离浏览器点击检查；电力、净水、维修旁路与动力核显示独立实时读数。公共监控缺电/摄像机停机时离线；B-07私人摄像头需要同意。
- 已认识且信任足够的人可入住，床位取决于开放的Jack房间等级，上限8。值班、休息、隔离、医疗和旧人物关系使用同一人物ID。
- 温室、医疗、工坊有可逆专精；分区勘查和回收有限，台阶记录保留，动力核旁路实际扣资源/增加基地污染。
- Jasmine记忆盒只显示已经发现的四个原剧情旗标；本轮不创造她的额外故事，不显示Host seeds。

## 内容容量与交付边界

- 27房间均至少10条轻观察和3条独立跨日运营事件，共327条观察、81条跨日事件；另有4条设备故障链。跨日运营事件包含处理、两日复查和逾期损耗，不冒充81篇大型主线剧情。
- 原有旧翼6房仍是独立模块，没有混入27房计数。其复杂连续性长线、所有历史人物家庭/战争/继任任务不在此次已完成范围。
- 本轮是可替换程序美术与合成环境声；不冒充正式手绘背景、角色动画或录制配音。


## 验收边界

- 27原房间ID、主题几何、至少10条轻观察/3条事件保留；当前100个独立可处理事件、200分支与327条观察分别计数。
- 程序SVG与合成环境声仍为可替换呈现；background normal/damaged/upgraded/night数据仍待正式资产，不能称手绘或录音完成。
- 主次入口使用现有温室/医务/工坊控制器；复杂下层剧情、非工作个人习惯、值班早期提醒和其他原规格仍见LAB-REMAINING-BEHAVIOR-AUDIT.md。
- 当前报告只证明表列数据和已有相关测试，不证明全部100运营/40房间条款。