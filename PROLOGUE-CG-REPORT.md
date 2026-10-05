# 0.12.2追加：生命维持维修CG

第三张正式ID CG_PROLOGUE_LIFE_SUPPORT_REPAIR。正式资源assets/story/cg/prologue_life_support_repair.png原样复制用户新图，SHA256 d690e0eaad825e273ca8571f55f41dc087f27b8860030f0de21922703e9ffec7。

project_b07第13句“他用一片垫圈补住管道。”切入，前两张仍第4/6句；没有改动任何场景正文/选择。700ms两层交叠，9秒1→1.035，水平-2px、垂直0，变换中心60%/63%靠向双手和管道。人物未单独变形，无额外overlay。

Jack永久美术规范见STORY-CG-ART-DIRECTION.md及StoryCG.artDirection：背面、3/4背面、侧面、低头、部分遮脸优先；正面必须戴磨旧的深色帽子，帽檐遮大部分脸。

图库按实际观看解锁，未看前无缩略图。沿用增量Meta/StoryBook，不追补授予；Save/Load/Rollback从scene+line恢复第三图。触屏浏览器检查1366×768、1024×768、768×1024的真实切换、运动、quick/读取/刷新/回看/日志/图库；单元测试核对三图触发与原图哈希，保护场景/20章仍通过。实体iPad限制仍见下方0.12.1记录。

修改presentation.js、cgLayer.js、server.js白名单、版本/日志/构建allowlist；新增正式PNG、美术规范、repair-browser测试；重生成portable HTML与英文包。下方为0.12.1双CG验收历史记录。

# 序章双CG与iPad全屏 · 0.12.1-preview

2026-10-05，St3phEn。

## 资源与位置

- CG_PROLOGUE_B07_FIRST_SIGHT：保留已有首次发现CG，正式路径 assets/story/cg/prologue_b07_first_sight.png；project_b07第4句“下面有电。培养舱内……”才显示。第0–3句黑底，章节标识先出现。
- CG_PROLOGUE_GLASS_TEMPERATURE：复制用户第二附件codex-clipboard-bdf27447-fe0e-46a1-a789-24e979c21afb.png到assets/story/cg/prologue_glass_temperature.png；第6句“先检查空气管和排水口，再用手背试玻璃的温度”切入。SHA256为258f3aa5d19681d74c4248e4b9fdc462f5ef8507836c4dd9ee6b6678c5450a91，与来源完全相同。没有选用第一附件的握拳候选图。
- 两张都属于PROLOGUE / project_b07 / Something Alive，未改动受保护场景原始文本、台词ID或flag。

## 动态

首见图800ms淡入、8秒1→1.03缩放，位移4px/2px；温度图650ms真实两层crossfade、7秒1→1.04，位移-3px/2px。旧图在新图下淡出，避免切图时黑闪。动画只在CG改变时开始，不随每句对白重新开始。慢镜在最大位置停住，不循环抖动。两张都用contain保持构图，画面层铺满，底部半透明框独立覆盖，没添加粒子/夸张光效。

关闭游戏动态、系统减少动态偏好时静止。Save/Load/Rollback根据现有scene和line恢复CG；不恢复毫秒级动画位置。图片独立、可替换，portable HTML构建内嵌两张PNG，源码版使用正式路径。

## iPad修复

原按钮只调用root.requestFullscreen，缺少方法时静默无效；全屏目标root也不包含同级dialog。新viewport模块兼容标准与webkit前缀方法及对应退出/事件；document.documentElement包含剧情和原生菜单。请求失败或不支持时有明确提示，并铺满visualViewport，而不是无反应。viewport resize/scroll/旋转会同步可视宽高/偏移，viewport-fit=cover和safe-area留边保护控件；触控按钮至少44px。

Safari地址栏由浏览器控制；备用铺满不是“成功隐藏地址栏”。已加入主屏幕独立启动相关meta，备用提示说明从Safari添加到主屏幕的使用方式。没有要求关闭浏览器安全设置或打开实验性开关。

## 收藏与存档

每张只在各自出现时解锁。未观看温度图前图库仅???，不泄露缩略图。Meta与StoryBook沿用增量字段，旧档不丢首张解锁；到第6句时自然获得第二张。手动/quick/auto的cg字段和文本位置会按当前帧记录，读档恢复；回看不删除已经实际看过的全局收藏。普通HUD在Story隐藏，Raising不改数值。

## 实测

- 1024×768、768×1024、1180×820、820×1180和1920×1080隔离Chrome触屏：首次触发、第二张切换、真实两层淡化、缓慢transform、保存/读取/刷新、回看、HTML原生全屏内保存菜单、Safari前缀模拟、不支持API的备用模式、旋转后尺寸、无横向溢出、Raising喂食、零pageerror通过。
- 1920/1366/390原剧情播放器回归：打字/Space、选择不自动选、10位置+quick/auto、log/gallery、Auto/Skip、固定HUD、零错误通过。
- 源码HTTP和file://入口：英文菜单/正文、CG、Ctrl快进、全屏、零缺失资源通过。
- prologue-cg、story-revision、story-presentation-save通过：指定候选原图哈希、精确CG触发、元数据/图库/导出、保护节点哈希、20章/旧档兼容及独立保存保持。

这些是触屏/接口模拟，不是实体iPad Safari测试；尚未在用户设备上直接验收。失败分支有降级，不能宣称所有iPadOS版本都支持原生全屏。其余历史任务状态仍见TASK-AUDIT.md。

## 文件

新增js/story/cgLayer.js、viewport.js、第二CG、tests/prologue-cg.test.cjs、prologue-ipad-browser.cjs及本报告。修改presentation.js、player.js、story-player.css、index.source.html、server.js白名单、tools/build-local.cjs/build-github.cjs/test.cjs、版本与更新日志；重生成index.html和英文语言包。
