# 圆润玻璃对白框 · 0.12.3-preview

范围仅剧情呈现和版本记录，没有改动剧情、路线、flags、存档结构或养成规则。

## 视觉

- 底部由直角全宽切面改为带屏幕留边的悬浮卡片；桌面32px、平板28px、手机26px圆角。
- 分层透明渐变、22px磨砂模糊、轻微饱和度调整、暗化背景、顶部柔和反光、细边与内外阴影。是Liquid Glass风格的CSS呈现，没有宣称使用Apple原生材质或光学折射引擎。
- 文字独立保持明亮，不对整个面板使用opacity；最低背景遮光和背景亮度控制保护浅色CG中的阅读对比度。原不透明度设置保留，低值设可读性下限。
- 阅读字体优先Apple系统SF/PingFang，Windows Segoe UI Variable/Segoe UI与Microsoft YaHei UI；字号/字重/行距/字间距重新调整，均为系统字体，无外部字体网络依赖。
- 角色名为圆润小标签，推进为圆形按钮；平板触控区域44px。选择区域上移避免和底部卡片重叠，大段对白可在阅读区域滚动。
- Safari使用-webkit-backdrop-filter；不支持模糊时提供更实的渐变底色。高对比度/减少透明偏好使用实色背景。

## 同时修复的旧问题

CG图片的正z-index曾越过没有独立层级的UI：在16:9图像覆盖全屏时，可遮住对白、角色名和工具栏；4:3留黑边时仅黑边内露出部分UI，因此此前DOM可见与点击测试没有发现真实绘制遮挡。

现在明确分层：CG父层0、对白3、顶部标识/工具栏4、选择5。截图已确认文字和玻璃卡片真实显示，不仅检查DOM存在。

## 检查

- 1920×1080、1366×768、1024×768、768×1024、390×844实际浏览器截图。
- 中英文、特大字号、低不透明度下的长对白边界、阅读区、选择间距和横向溢出检查通过。
- 维修CG、quick/load/reload/rollback/gallery/log，以及原播放器Space/Auto/Skip/选择不自动选和养成模式回归通过。
- 使用隔离测试存档。实体iPad未直接验收；平板测试为触屏浏览器尺寸模拟。

## 文件

story-player.css、js/data/updateLog.js、index.source.html、package.json、CHANGELOG.md、TASK-STATUS.md；生成英文包和portable index.html。verification/dialogue-glass-*.png与dialogue-glass-check.cjs记录实际视觉检查。
