# 第11张首词CG接入报告

CG_ACT3_FIRST_WORD → assets/story/cg/act3_first_word.png，使用用户原图，不修改图片，不生成插画。

实际剧情ID为project_first_word（章节别名first_word）。第2行B-07的{firstWord}出现时切换，第0–1行不提前展示。原受保护文本完整保留。550ms交叉淡化、8秒1→1.025推镜、水平漂移1px，人物不变形；没有闪白/震屏/粒子/爆点。

第10张CG_ACT3_BEFORE_THE_FIRST_WORD在当前项目缺少正式源图，仅预留元数据与第0行插入位置，不显示缩略图、不用其他图替代。源图补齐后才能验收10→11实际两图交叉淡化；现有两层播放器支持该过渡。

首词沿用narrative.firstWord对象（word/day/context），已有旧档读取兼容；不新增第二套随机首词。剧情同步仅在值缺失时填充，后续{firstWord}及共同记忆读取该字段。

专项自动测试通过：原图字节一致、节点时机、收藏锁定、非默认首词持久化/回调、快存/读档/导入。原Claude剧情保护哈希及独立剧情存档测试通过。

真实Chrome浏览器1366×768与768×1024通过：Space首词/CG、图片解码、首见解锁、快存/读档/刷新、回看及养成模式隔离，0页面错误、无页面横溢出。并非物理iPad Safari测试。

修改：js/story/presentation.js、tools/build-github.cjs、index.html；新增资源与tests/first-word-cg*.cjs。
