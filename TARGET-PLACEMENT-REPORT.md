# TargetPlacementValidator · 0.13.10-preview

本轮对应用户明确要求的独立目标布局校验器。当前项目尚无Happy Club小游戏；本轮不将地图地点、门票、25秒挑战、转盘、农场/遗传/150食谱或全项目滚动审计宣称已完成。

实现文件：`js/happyClub/TargetPlacementValidator.js`，已在`index.source.html`的core之后载入。浏览器使用`Abyss.TargetPlacementValidator`，Node使用`require()`；没有依赖、DOM读取、随机数、货币或存档副作用。

## 统一负责

- 出生点、完整目标边界、边缘留白、UI/前景遮挡、场上最多3目标。
- Common 100%、Uncommon 82%、Rare 65%、Epic 50%、Legendary 38%、Anomalous 26–32%。默认Common为100×100 CSS像素；可通过构造配置调整基础尺寸。Bomb为独立类型，不作为rarity。禁止调用方另传width/height绕过尺寸计算。
- 变形使用0–1之间的线性关键帧，计算整个周期的最大宽高；最小可点尺寸默认8 CSS像素。Common不变形，Bomb仅±5%；其他等级允许有限轮廓缩放。未知旋转/任意函数轨迹拒绝，避免漏算包络。
- 常规gap为`max(80 * min(viewport.width/1280, viewport.height/720), 0.55 * 两者最大宽度)`。Bomb参与任意一对时，额外乘1.2，顺序对称。不是只检查Bomb出生点。
- 静止、连续折线、二阶和三阶Bezier均检查完整轨迹。折线使用每段包络；Bezier经de Casteljau分成16段，每段控制点凸包的矩形包络覆盖该段连续曲线，不是离散采样。每段包含最大变形尺寸，与场地、UI、前景及其他目标整个路径检查。
- 目标之间使用最大矩形外接圆半径和成对gap的保守距离证明。`safeRadius`为自身诊断数据；不同体型/Bomb请始终调用校验器，不能自行相加safeRadius替代成对检查。
- 不通过时返回具体stage/reason，不强塞。`findPlacement`尝试最多32个调用方提供的候选，全部失败返回`DELAY_SPAWN`。
- 运行中`validateAdvance`重新检查保留的整条路径。未来冲突时`PAUSE`并保持当前pose；当前位置已被挡住、越界、非法输入或目标数量异常则`HIDE`。找不到安全位置时宁可少刷。

当前策略保守要求整个活动期主体100%可见，满足规格的80%/75%/70%下限。包络可能拒绝部分实际上安全的曲线；不确定时拒绝，而非穿模。美术对比度、视觉轮廓命中测试、生命周期和生成概率需后续Happy Club控制器负责，不能仅凭矩形证明。

## 接入示例

```js
const placement = new Abyss.TargetPlacementValidator();
const scene = {
  viewport: {x: 0, y: 0, width: 1280, height: 720},
  existingTargets: activeTargets.map(t => t.plan),
  uiBounds: [],
  foregroundBounds: []
};
const candidate = {
  id: 'round-1-target-3', type: 'REWARD', rarity: 'RARE',
  position: {x: 300, y: 300},
  path: {type: 'polyline', points: [{x:300,y:300},{x:500,y:300}]},
  morph: [{at:0,scaleX:1,scaleY:1},{at:1,scaleX:.8,scaleY:1.1}]
};
const result = placement.validate(candidate, scene);
if (result.ok) activeTargets.push({plan: result.plan, progress: 0});
// 否则延迟，或交给findPlacement尝试缩短/改向/静止的候选。

const decision = placement.validateAdvance(target.plan, target.progress, nextProgress, scene);
if (decision.action === 'MOVE') {
  target.progress = nextProgress;
  renderFromPose(decision.pose);
} else if (decision.action === 'PAUSE') {
  renderFromPose(decision.pose); // 不推进运动进度
} else {
  retireTarget(target); // 立即停止输入与绘制
}
```

坐标统一为arena局部CSS像素；UI和树干遮挡也转换到同一坐标系。不得混入canvas DPR像素。渲染器须使用`poseAt`/decision.pose的边界，不能再加未登记位移、缩放或重影溢出；场地/遮挡变化后继续调用`validateAdvance`。已有目标必须是同一实例prepare/validate生成的不可变plan，不能拿伪造bounds或序列化对象冒充。未来保存小游戏时，应保存source再重新构建和验证plan，本轮不修改存档schema。

## 验证

专项测试：6稀有度、异常尺寸边界、非法/稀疏输入、出生/边界/遮挡、路径中间碰撞、完整Bezier包络、变形最大尺寸、普通gap、Bomb双向+20%、Bomb与Legendary/Anomalous、重复ID/数量上限、延迟生成、运行中暂停/隐藏、尺寸变更、不可变plan、旧游戏状态和RNG无变化。

500条确定性随机曲线中229条获准；逐条用201个位置检查边界和距离，作为测试oracle。实际安全证明仍来自连续包络。浏览器和发布验收结果随后记录。

接入兼容：奖励rarity与type接受现有游戏使用的小写ID，内部规范化为大写；不修改原目录ID。构造配置与plan不可变，实例私有WeakMap防止伪造既有目标。

本轮相关回归（6个测试文件）通过：新校验器、房间事件/观察、Claude保护文本、CG10→11/firstWord、存档/武器导入。源码HTTP专项通过，298个CSS/脚本与11CG资源可加载，私有路径仍拒绝。本轮未重跑此前0.13.9的93文件全套，不将旧日志算作新全套结果。实际Chrome1366、768、390宽的几何夹具各183姿态、三个目标、动态暂停/隐藏及无横溢出通过；成品游戏载入模块，状态/RNG不变，无页面错误。夹具不是完整Happy Club。
