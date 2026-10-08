# 云端迁移交接

当前项目包含完整可编辑源码，不应仅从公开单文件游戏继续开发。

当前版本 0.13.29。总目标仍未完成。先阅读 GOAL-ACCEPTANCE.md、TASK-AUDIT.md、TASK-STATUS.md、BATCHED-UPDATES.md；各模块验收文件记录真实完成范围。养殖独立事件目前60/100，剩40。历史大型扩展、正式美术及公开AI部署仍有未验收项，不得直接宣称完成。

用户要求：保存已有全部玩法、存档、route、ending、隐藏flags和受保护的Claude文本；完成汉化、按钮遮挡修复及独立物品造型；完成历史欠项分批发布。禁止读取或上传实际.env、API Key、玩家存档；不得调用付费API进行测试。公共AI须Stephen114514申请后经主机批准，支持封禁和预算控制，现有静态站不等于已部署后端。

Node >=20。安装 package.json 的依赖后执行 npm run build、npm test。浏览器用隔离新context，不能操作玩家真实进度。CG从公开站恢复，见 tools/restore-cloud-cg.cjs。源代码包不包含任何密钥或玩家存档。

Codex Cloud是云端环境，不是独立安装软件。需在Codex的“Work in → Cloud”建立环境，选Stephen仓库，上传/解压代码包后发布环境；未看到云端环境发布成功和实际测试前，不得标记迁移完成。
