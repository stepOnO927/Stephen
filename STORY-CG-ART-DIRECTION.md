# Story CG永久美术规范 — Jack

来源：用户于2026-10-05提供的生命维持维修CG及明确美术要求。适用于后续所有Story CG，除非用户明确修改。

- Jack通常从背面、3/4背面、侧面、低头或脸部部分被遮挡的角度呈现。
- 避免清晰的正面露脸。若后续必须正面呈现，必须戴磨旧的深色帽子，帽檐遮住大部分脸。
- 维修场景以手、扳手、管道连接和B-07隔玻璃观察为重点；不把维修画成双方已经建立亲密互动。
- 小动态只移动整个画面：轻微等比缩放和少量平移；不单独扭曲或动画化Jack/B-07身体。
- 图像作为独立可替换资产；未实际观看不显示图库缩略图。

代码对应：js/story/presentation.js的StoryCG.artDirection。未来制作/接入CG时须按此检查角度、帽檐、角色阶段和构图。

## 当前序章正式顺序

1. CG_PROLOGUE_B07_FIRST_SIGHT：第4句，真正首次发现舱内生命。
2. CG_PROLOGUE_GLASS_TEMPERATURE：第6句，上前检查玻璃温度。
3. CG_PROLOGUE_LIFE_SUPPORT_REPAIR：第13句，“他用一片垫圈补住管道。”开始实际维修。

第三张使用用户提供的原PNG，路径assets/story/cg/prologue_life_support_repair.png，SHA256 d690e0eaad825e273ca8571f55f41dc087f27b8860030f0de21922703e9ffec7。700ms交叠淡化，9秒1→1.035推镜，水平-2px、垂直0，画面变换中心60%/63%靠向双手和管道；无额外粒子或人物变形。
