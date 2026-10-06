# Architecture · unified schema v3

The game uses classic scripts and one `window.Abyss` namespace so the portable `index.html` works offline. `index.source.html` is the editable entry; `tools/build-local.cjs` embeds the stylesheet and scripts into the portable entry.

## State and flow

`Engine` owns one validated state object and commits commands transactionally. Successful commands are saved through the existing `abyss-lab-save-v1` key and then rendered. `State.validate` is the migration boundary for schema versions 1, 2, 3, and 4. It keeps the base creature simulation, accessories, personality, memories, exploration metadata, active expedition, history, flags, documents, and settings in one save.

`s.inventory` is the only quantity map. It stores laboratory food and exploration loot counts under stable item IDs. `s.exploration.items` stores expedition item metadata such as source, date, and identification; it has no second quantity field. `ExpeditionState.validate` migrates the old `exploration.items[id].quantity` values into `s.inventory`. Both content sets resolve their rarity IDs through `Abyss.Rarity`, which provides the shared six-tier catalog and maps expedition drop/recovery weights.

Accessory records and equipment live in `s.collection`; lore documents, world flags, hidden rooms, fatigue, active progress, and expedition history live in `s.exploration`. The two archive screens retain their distinct record types.

## Modules

- `core.js`, `state.js`, `save.js`, `engine.js`: shared utilities, canonical state, migration, persistence, and command transactions.
- `actions.js`, `events.js`, `mutations.js`, `exploration.js`: existing laboratory rules and legacy one-step exploration compatibility.
- `accessories.js`, `personality.js`, `memory.js`, `wardrobe.js`, `accessoryArt.js`: accessory collection, equipment, reactions, personality, memory, and wardrobe UI.
- `data/explorationData.js`, `rarity.js`, `expeditionState.js`, `inventory.js`, `expedition.js`, `expeditionUI.js`: exploration content, shared rarity catalog, item quantity operations, expedition state, rules, and terminal UI.
- `renderer.js`, `ui.js`: creature rendering and laboratory UI.

Scripts load from data to schema and rules, then engine and UI. Keep `index.source.html` script order intact when adding modules.

## Compatibility

Version 1 saves migrate legacy exploration quantities and initialize accessory/personality defaults. Version 2 saves migrate accessory state and initialize exploration fields. Version 3 stores the combined schema. The save key and backup behavior stay compatible with both supplied builds.

An active expedition blocks laboratory actions while allowing expedition commands, settings, and ending acknowledgement. Event choices and expedition choices remain separate because they have different lifecycles and state effects.

## Costume design and creature identity (2026-10-02)

- `js/data/accessoryStyles.js`: independent palette families; rarity does not dictate an item's material colors.
- `js/accessoryModels.js`: replaceable 2D SVG geometry, seams, enamel, transparent lenses, fabric folds and metal trim.
- `js/accessoryArt.js`: assembles geometry/materials and attaches items to existing slots; unique gradient IDs preserve independent UI/preview SVGs.
- `js/identity.js`: Unicode name normalization, validation, legacy default and transactional rename behavior. `rename` costs no AP and may run during an expedition.
- `s.name`: optional additive field in schema 3. Missing/invalid legacy names become 零号 without changing other save fields. No save-key change.
- The monitor name control and terminal menu open the naming form. New-game confirmation opens it automatically; retaining the default is allowed.
- Run `node tests/identity.test.cjs` for naming compatibility, atomic invalid inputs, persistence and model coverage.


## Phase 3 modules and transaction order

- data/phase3Data.js: 42 technology records, six branches, eight families, 28 final forms, four curated hybrids, six story chapters, research items, food and experiment extensions.
- data/visualComponents.js: 88 replaceable component records, compatibility metadata and 88 added mutation candidates.
- data/progressionExpeditions.js: research-gated locations, ability-gated exploration choices, key discoveries and the hidden Zero room.
- data/itemModelData.js: individual pseudo-3D object meshes as front/top/side SVG faces.
- progressState.js: schema 4 defaults and strict migration/sanitization; quantities remain exclusively in s.inventory.
- research.js: XP/level thresholds, one-time discovery ledger, point costs, prerequisites, exclusivity, identification and BLACK authorization.
- evolution.js: hidden scoring, gradual stages, conflicts, contextual abilities, final/hybrid selection and biological history.
- story.js: chapter eligibility, persistent decisions, delayed context and story history.
- progression.js: small coordinator of command results, diet tracking, unlocked protocols and inter-system gates.
- progressionUI.js: research network with SVG connections, scroll/zoom/filter controls, detail pane, records and non-alert choice overlays.
- visualEvolution.js: eight body paths plus modular variant drawing and costume-preserving shared rig transformations.
- itemModel.js: mesh/material assembly and silhouettes for research/loot cards.

Engine dispatch validates gates and runs a command on a clone, applies existing achievements/accessory hooks, calls Progression.observe to reconcile discoveries and progression, then atomically commits, saves and renders. A failed command never replaces the state. UI keeps no canonical progress state.

Schema 4 adds s.progress (research, evolution, story, diet, protocols). Existing names, collection, personality, memories, inventory and active expeditions are retained. Available tech is derived from data and state rather than serialized. Hidden evolution scores are stored internally and never rendered as percentages.

Build with node tools/build-local.cjs. Classic script order is declared in index.source.html; generated index.html has no runtime resource dependency and works alone over file://.

事件扩展：js/data/eventExpansion.js 管理情境文案与隐藏遭遇；js/eventRules.js 共用进化条件和多物资奖励。保留原事件 ID / 选项 ID 以及 v4 存档结构。

怪物对话：server.js 与 server/dialogue.cjs 仅处理文字。js/chatContext.js 构造只读状态白名单，js/creatureChat.js 显示独立弹窗。Key 仅服务器环境变量；聊天历史用 sessionStorage，与 localStorage 游戏存档解耦。角色追加设定放 server/creature-lore.txt。

## Phase 5
- narrativeState.js：子存档 version 1 的默认值/白名单迁移。顶层保持 v4 与原存档键。
- dialogueRules.js：统一声明式条件，无 UI 依赖。
- language.js：词义、教词、六档语言与首词。
- narrative.js：事务内节点选择、照料桥接、队列、记忆、章节、延迟后果和 NG+。
- narrativeUI.js：中央 VN 展示、打字机、选择、档案、交互菜单；不调用外部模型。
- data/narrative*.js / projectAbyss.js / abyssRooms.js：内容与系统分开，新增内容主要添加节点、条件与效果。
- STORY_BIBLE.md：仅开发内部；静态服务器白名单不提供该文件。
- 既有六篇观察记录与新调查主线并存，保留旧字段的奖励和权限依赖。

## Phase 6 boundaries

Runtime remains classic scripts / no game engine. `phase6Data` is content-only; `campaignBeats` extends the node graph after Campaign configures the expanded chapter order. `Campaign` owns timeline-specific route tendencies, consequences and death states. `Meta` owns account discoveries only, stored separately from all creatures. `Save` owns the slot catalog, selected session, manual snapshots, autosave and backups; `Engine` remains the mutation/notification boundary. `ModeUI` owns custom dialogs, `SkinArt` owns replaceable cosmetic SVG patterns.

Top-level saves remain v4 for existing validation; optional campaign schema is v1, slot catalog v1 and meta v1. Raising mode filters campaign nodes at both enqueue and dispatch, and suppresses legacy Story.sync. Story actions are free only inside campaign choices; normal Actions costs remain unchanged. Campaign choices with a gameplay action temporarily provide action capacity, then restore original AP; validation and resource charging still use the original action module.

Shared rewards are read-only keys/skins. Never copy a living creature from one mode to another implicitly. An explicit import replaces the current record after confirmation and keeps that slot's mode. Engine.replace enforces that mode; a Raising record cannot resolve a campaign ending. Meta rewards never alter stats or relationship memory.

## 全身改色与本地化
Colors 对生物图层统一应用染色场，描边使用独立阴影渐变，设备和服饰不参与染色。I18n 属于呈现层：英文目录只映射显示文字，不改动数据 ID、Canonical 中文记忆、属性或游戏随机数。DOM 原文通过 WeakMap 保留，动态模板先匹配再代入值，怪物名字与玩家输入受到保护。界面语言在独立 localStorage 键 abyss-lab-language-v1 保存，与实验体存档隔离。浏览器不会调用翻译服务。英文目录由 build-language 合成，人工修订覆盖缓存译文，再由 build-local 内嵌进可移植入口。

## Phase 8: Jack 与剧情呈现

- `jackState.js`：十项隐藏倾向、已阅读拍点、重要日记、Mia 线索、待完成结局的存档验证。
- `storyPresentation.js`：独立语言强度偏好 `abyss-lab-text-intensity-v1`，不修改实验体属性、随机种子、分支或行动点。历史对白使用相同的措辞映射。
- `data/jackData.js`：中英文一起编写的 20 章主体、人物说话身份、内容辅助函数。
- `data/jackDoorScenes.js`：THE LOCK、开门、门槛与第一段走廊。
- `data/jackPersonalScenes.js`：日记、四次梦、普通谈话、学习粗口和 Mia 条件线索。
- `data/jackEndingScenes.js`：六条较长的结局场景；WE 的五种回答均进入实际离开流程。
- `data/jackActExtensions.js`：各章特有的日常细节和较长对话。
- `data/jackDataFinalize.js`：人物档案、隐藏条件、回调变体、旧奖励索引、内容注册；不调用外部翻译。
- `jackStory.js`：状态决定的语气、门槛反应、章节迁移、日记和结局延迟完成。
- `jackUI.js`：档案／日记界面和设置选项，沿用现有弹窗与排版。

Narrative 的 `nextNode` 可以由单个 choice 覆盖。主线仍不消耗 AP；日常养成调用原 Actions。对白区使用 narration / thought / dialogue 三种呈现，记录保持相同的 voice 字段。

顶层存档仍为 v4，narrative 升为 v2，jack 子结构为 v1。旧 9／14 章存档按已完成章节 ID 映射，而非直接使用索引；irregularity 对应 jack_name、continuity 对应 between。旧字段、原始存储键、备份、收藏和关系均保留。新增章没有旧奖励索引，避免提前发放机密文件。

扩展结局先保存 pendingEnding，阅读完成后才更新死亡状态、结束标记和 Meta 奖励；读到一半可以刷新继续。结局期间阻止新的养成操作与跳过，设置和档案仍能使用。实验体已离世时主要调查场景使用独白版本，不恢复身体。

## Phase 9：聚落与背景收藏

WastelandData / WastelandScenes 保存聚落、人物、双语场景与成就；WastelandState 负责初始化和迁移。Wasteland 只通过 Engine 命令修改本轮聚落状态、人物记忆、传闻和延期项目；WastelandUI 读取快照并展示，行动费用来自 Wasteland.price，避免显示与扣费不一致。主线 AP 规则不变，聚落外出与行动各使用 1 AP，返回免费。

WallpaperData 提供条件和元数据，WallpaperArt 独立生成分层 SVG，Wallpapers 处理 Meta 收藏、培养室／菜单应用及性能偏好，WallpaperUI 管理筛选和预览。20 个场景没有永久合并到生物图层；后续可单独替换背景素材。画廊缩略图静态，最高三档选中场景可动，低性能／减少动态模式关闭动画。

顶层 v4 存档新增 wasteland v1。缺少该字段的旧档自动补齐。Meta 保留原键与版本，仅补 wallpapers、wallpaperLab、wallpaperMenu；聚落关系不跨角色共享，背景收藏跨模式共享。人物内部 mia 标识继续兼容，显示名统一为 Jasmine。

## MEGA 核心版

Home / Journey / Legacy / Dreams / Social / Continuity 各自负责自己的子结构与规则，通过 Engine 的命令边界提交，失败不改当前状态。ExpansionUI 负责六个界面及主画面的房间位置展示。HomeData / JourneyData / DreamData / PeopleExpansion 保存人工双语内容；ExpansionRewards 接入原有成就、结局和背景收藏。

六个新子结构都是 v1，顶层仍为 v4；缺失字段自动补齐。多代保存世界 day，个体 age 使用 day - legacy.birthDay，不继承具体性格、忠诚、怨恨、身体创伤或确切记忆。Social 的 NPC 网络保留，仅实验体对人的关系归零。主线个体不能被替换。

Continuity 的跨周目记录在独立 meta 键，单个角色只保存自己的回声与决定。旧 Meta 结局可迁为已知记录，不推算缺失的重复通关次数。结束循环后不恢复旧关系，也不删原有收藏。Dreams 的象征物和正常库存分开。

语言构建器额外收集源码中人工提供的 t(中文,英文) 字符串对，因此保存过的房间记忆在重新启动后也能完整翻译。构建过程不调用翻译服务。独立公开发布目录只复制单页游戏；静态发布标志仅选择备用对白，不涉及本机密钥。

## 荒野狩猎扩展 · 2026-10-04

`HuntState` 是可选 v1 子存档与白名单迁移；`Combat` 是无 DOM 的回合规则、战斗派生属性、状态效果与自主行动；`Hunt` 管远征分歧、悬赏、撤退、恢复与成就；`HuntRewards` 管药剂、抽取、保底、蓝图、锻造与装备。所有操作走 Engine 副本事务，狩猎活动中阻止其他消费行动，免费返程始终可用。

`SerumData / HuntData / WeaponData / HuntCosmetics` 分别提供 55 瓶药剂、区域/敌人/招式、40 武器、100 外观。`SerumArt` 管独立伪 3D 容器；`HuntArt` 管附件锚点与占位模型；`HuntUI` 管七个终端页面，`hunt.css` 单独保存新样式。现有 Renderer 只增加可选附件分支及三个槽，不重写主场景。新增 `visual.asset` 可以替换图片而不更改战斗规则。

顶层存档仍 v4。药剂数量、已发现、已消费与赌剂结果分开；随机序列沿用持久化 PRNG。狩猎活动、战斗状态、体力、护盾、保底和战利品随存档保存。五套预设自动补齐工具/特效/武器外观槽。多代新个体不继承旧人的战斗创伤。

自包含构建器现在内联所有本地 CSS 链接，保持 `index.html` 直接打开可运行。新规则测试：`tests/hunt.test.cjs`；浏览器流程：`tests/hunt-browser.cjs`。细节、计数和剩余美术工作见 `HUNT-REPORT.md`。

## Redeem codes (2026-10-04)
`js/redeem.js` owns optional version-1 save entitlements, grants and terminal. State v4 migration defaults old saves to no entitlement. Meta reads overlay the active save; redeemed collections never write shared meta. Save deletion removes manual/auto and both backups, clears active session and resets live state. Independently copied saves remain independent.

## Collection art atelier
`artMaterials.js` supplies isolated SVG material IDs. `coutureModels.js` owns slot-local theme silhouettes and 13 individual premium overrides. `objectSculptures.js` provides authored loot silhouettes alongside the ten existing item meshes. `weaponArt.js` owns all 40 weapon illustrations. `serumSculptures.js` provides 15 bespoke outer housings. No game-state, IDs, rewards or save fields changed.

## Fit, evening story gate and authored observations (2026-10-04)

AttachmentRig fits slot-local art to mutated body profiles, eyes and tail tips. Renderer retains existing global growth scaling. StoryDay owns the optional narrative dayWindow, synchronizes after transactions and restores legacy pending activities. Engine enforces its action gate, UI only presents the resulting state.

HomeScenesExpansion, DreamExpansion, CampExpansion and KitchenFoods extend existing catalogs. RelationshipDialogue supplies 100 bilingual responses selected from individual relationships and harm history. LegacyScenes supplies 45 observations with optional Legacy.seen and typed keepsakes; personal memories remain independent across generations. JourneyEncounters adapts the existing Expedition resolver and inventory grants without duplicating event rules. Each new field defaults on older saves; the top-level schema remains v4.

Public distribution uses tools/build-github.cjs and an explicit five-file allowlist. See TASK-STATUS.md for verified scope and remaining requirements.

## Containment Life · v0.5.0

SceneComposition stores chamber/specimen/depth values independently of Renderer growth. SceneCompositionUI moves the vessel, platform, shadow and creature through a common ground transform; creature scale is a separate ground-anchored transform. WallpaperArt generates perspective geometry; high tiers add theme-specific SVG effects honoring low quality, reduced motion and visibility.

WeaponExpansion adds data and balances rarity bands without replacing Combat. WeaponArt constructs individual geometry; WeaponEffects is a presentation-only SVG adapter. Combat owns all outcomes.

SalvageData registers 100 objects into the existing ExpeditionData inventory catalog. Salvage rolls a six-tier distribution first, then a contextual item; observes completed field returns and records actual discoveries/sales. CollectionAchievements adds 30 measurable rules. SalvageArt uses 20 constructed families with 5 structural variants.

ContainmentData owns furniture, anomalous objects and pet species. Bedroom validates item counts, finite placement, footprint, collision, doorway reservation and full surface support before committing. Removing a supporting table in the editor also stores dependent objects. BedroomArt projects an eight-unit room; ContainmentUI edits an isolated draft and dispatches only on confirmation. Inventory art is paginated to 18 visible cards.

Pets owns individual petSeed, survival needs, tendencies, relationships, warnings, escape and memories; B-07 remains independent. PetBehavior contains reusable context/response combinations, scalable beyond 500 by adding fragments. ContainmentEvents provides data-driven life encounters. Life event choices are free and resolve once. Predation requires species size/diet, severe stress/hunger and repeated warnings; separation prevents it. Normal disagreements do not automatically kill.

Entitlements stores permanent browser-local eligibility in abyss-lab-entitlements-v1. Redeem v2 records claimedRewards in each save. Legacy v1 code history migrates without replenishing old consumables; new item IDs are fulfilled once. Each new save receives its own package once; deleting a save does not remove permanent eligibility. No server or API key is involved. Top-level save version remains 4; each new optional field validates and defaults independently.

## v0.6.0 Story separation and XYZ presentation

StoryMode owns optional version-1 hidden story state, legacy migration, allowed-command policy, chapter clock, choice effects, investigations and delayed callbacks. StoryRoutes owns ordered ending gates within the player's chosen decision. StoryFiles is the optional record catalog; StoryUI presents it without exposing hidden numbers. Raising observers remain guarded in Engine; Story only runs narrative/continuity observers. Top-level save version stays 4.

BedroomDepth overrides BedroomArt through the same public contract. Furniture uses local XYZ primitives rotated in the room plane then projected by the editor's shared camera. Physical support height and sort order agree with Bedroom's placement validation. Irregular legacy decorations retain a projected plinth fallback. WallpaperArt picks wall/floor materials by theme.

## v0.7.0 Trade and street systems

CaravanData registers goods in the authoritative inventory catalog and computer furnishings in ContainmentData; StreetData provides named/minor identity and modular portrait catalogs. StreetAmbient separates authored occupational bases from explicit context combinations.

Caravans owns its RNG, saved visits/stocks/conditions/prices/relations/wanted status and escort contracts. Commands run inside Engine's transaction clone. Existing combat resolves escorts; observed wins bank once, retreat clears contracts. Offers use authoritative inventory, equipment, serum and placement counts. Street owns identity seeds, routines, independent memories/relationships and dialogue actions. StoryMode delegates only narrative person actions; sandbox economy commands stay blocked.

EconomyUI renders paginated views and dispatches commands. EconomyArt supplies replaceable SVG goods and layered portraits. Legacy preserves world commerce and Jack relationships, resetting the new creature's social bond. Optional schema-1 fields are sanitized without changing the top-level v4 key.


## 0.7.1 presentation modules
- `npcModels.js`: role-specific silhouette/face/clothing SVG; `visualRole` supports artist-authored overrides.
- `goodsModels.js`: replaceable card and computer illustrations. `economyArt.js` remains the facade.
- `bedroomDepth.js`: computers use the furniture rotated XYZ camera.
- `storyEffects.js`: explicit node/line cues, deduplication and motion preferences; no game-state mutations or random calls.

## v0.8.0-preview 公路模块

RoadData/VehicleData/RoadLayouts/RoadRewards/RoadEvents 仅描述内容。RoadState负责嵌套存档迁移和校验；Road负责事务命令和互斥；Vehicles负责工程条件/车库记录；RoadCargo负责体积/尺寸；RoadMap负责平台物理；RoadCombat负责即时战斗；RoadLoot负责收集与估价。RoadUI只派发命令并处理输入；Road3D为独立WebGL网格渲染，RoadPixel为独立2D画布。渲染不会修改状态或取核心随机数。

旧伪3D cabin.js保留在开发目录作为参考，不再用于后舱界面。source入口经build-local打包为可独立打开的index.html。公路仅在养成模式开放；严格剧情模式保持原隔离。

## Road navigation (0.8.1-preview)

`js/road/network.js` owns the connected graph, tier-aware shortest paths, validated saved routes, bounded interpolated world pose and heading. Core commands own collisions and travel transactions; RoadUI draws both world map and cockpit minimap from the same geometry. The WebGL environment shifts by the vehicle's bounded lane offset without moving cabin art. RoadState restores route IDs or reconstructs legacy route geometry while preserving saved distance and route length. Route-based driving is not free-roaming world physics.

## Travel presentation and ownership (0.8.3-preview)

- `js/road/scenery.js`: deterministic, route-specific world-distance landmark descriptors; never consumes gameplay RNG.
- `js/road/motion.js`: interpolates render snapshots only; simulation, history and saves continue to use actual state.
- `js/road/siteArt.js`: modular pixel room painters selected by room purpose and biome, reusable outside this renderer.
- WebGL caches static world/cabin buffers and translates the world in a shader. Occluded lab animations/painting pause while the road shell is open and resume on close.
- Road save schema v3 permits `vehicle:null` / no owned vehicles, stores acquisition origin, validates selected ownership and preserves old starter gifts with an explicit legacy origin.
- All arrivals expose entry. Friendly sites have no enemies or repeatable loot containers; hostile side-scrolling combat is retained.


## UI shell (0.9.0)

- `js/navigationData.js`: eight sections and declarative routes to existing controllers; new features must have an owning section.
- `js/uiComponents.js`: reusable sidebar, section header, tab bar, item grid, empty state, alert and context menu.
- `js/navigation.js`: presentation routing, breadcrumb/back, search, urgent summary and layout memory. No copies of game state. Reads Engine snapshots; commands remain in existing controllers.
- `navigation.css`: shell, nonmodal system workspace, responsive sidebar/drawer. Existing detail, meter, confirmation and artwork components remain in their own modules.
- `Abyss.UI.modal` retains confirmations/rewards as modal dialogs. Full-system dialogs are mounted with `dialog.show()` in `#section-surface`; their existing delegated events and controller rendering continue to work. Expedition and chat have matching presentation hooks; Road retains its renderer in the same main workspace footprint.
- `abyss-ui-layout-v1` stores section, per-section tab, sidebar state, disclosures and recent routes independently of gameplay saves. Invalid top sections fall back to Home. Exported game saves and API context contain no navigation state.
- Story-only restrictions are preserved; Raising-only tools show a mode explanation rather than exposing sandbox commands.
- UI route tests: `tests/navigation-browser.cjs`, `tests/navigation-full-browser.cjs`. The latter opens all 52 routes, verifies no currency/AP changes, context, language, persistence, responsive layout and mode isolation.

## 0.9.1 rendering modules

`eyeArt.js` owns shared eye geometry and individual blink origins; `attachmentRig.js` aligns garment and lens anchors. `renderer.js` clips torso clothing to the expressed body path before applying local tailoring, with unique per-preview clip IDs. `data/atelierAccessories.js` adds 60 data-driven collectibles; `tailoredModels.js` owns their independent SVG silhouettes and materials remain in AccessoryStyle. Existing save schema is unchanged; generic collection reconciliation and redemption include new IDs.

### 回收抽奖（0.9.2）
`js/drawUI.js`只负责画面、支付选项与结果展示；`js/huntRewards.js`统一报价与原子扣款，默认兼容旧废料币调用。Engine保留模式守卫。结果与RNG先保存再播放动画；两种货币共享奖池及保底，不变更schema。样式独立于`draw.css`。


## Climate module (0.10.0-preview)

`js/climate/` separates data, validated state, deterministic daily rules, event records, collectible acquisition/art, UI and optional audio. `Climate.tick(before,next)` runs only when Raising advances a game day. Story exposes a read-only terminal. World simulation uses nine regions rather than individual scenery points. RoadNetwork reads persisted road conditions for routing; Road controls pass a read-only preparation brief and invoke bounded vehicle wear. Caravans, Street, Actions and combat read shared climate factors without owning weather simulation.

The top-level schema remains 4 and `climate.version` is 1. A separate saved RNG precomputes the actual three-day weather plan; forecasts are imperfect observations of that plan. Opening UI or reloading cannot reroll the weather. Old saves initialize from their current day, stable reserves and a seven-day grace period. Legacy carries world climate but resets the new creature’s weather memories/preferences. File-local classic scripts preserve the self-contained build and existing local save behavior.

New `climate.css` targets only the weather workspace/cinematic. Weather accessory art stays in replaceable SVG layers and uses AttachmentRig for body fit. Four furniture objects have independent depth geometry and only grant effects when placed. The event catalog explicitly contains contextual variants; see CLIMATE-REPORT.md for remaining narrative and audio limitations.

## 武器2.0实体与获取决策
- `js/weapons2.js`：实体持有权、唯一ID、锁定保护、共鸣消耗、满仓暂存、替换和分解；`hunt.weapons`仅是选中实例的兼容视图。
- `js/huntState.js`：实例/暂存/待处理决策的存档白名单迁移；损坏ID重建并保留副本。
- `js/weaponAcquisitionUI.js`：重复获取与满仓选择、指定共鸣目标/材料、确认分解；只通过Engine命令改变状态。
- `js/weaponStorageUI.js`：筛选、排序、同名折叠及逐副本控制。暂存物可以单独打开管理界面。
- `js/weaponRare.js`、`js/weaponEpic.js`、`js/weaponNamed.js`：条件共鸣和战斗局部状态；UI不参与伤害计算。
获取时新实体先入仓或暂存，待处理决策仅记录其ID。关闭弹窗或刷新不会删除实体；保留仅确认决策，分解/共鸣/替换必须通过受保护的明确命令。满仓暂存不计入100格实体仓库，可直接作为材料；不得自动吞掉重复副本。

武器全流程：锻造使用Weapons2.grant创建副本；狩猎/道路换装共用Weapons2.equip，兼容缓存先写回再切换实际实例。商队offer绑定weapon-instance:UID，来源记录weaponInstanceId与实例一起保存。跨代用Weapons2.carry保留全部合规副本与暂存，永久权益覆盖全库存；不通过重建每种武器一把来迁移。

武器战斗扩展职责：
- js/weaponFirearm.js：当前狩猎AK弹匣、有限备用弹药、后坐与换弹；不会改动货币或库存。
- js/weaponLegendary.js：各传说武器独立触发与临时记录。目前霜线和昨天已接入，其他传说仍待实现。复制记录只存原始单次命中，不存复制或连击总伤害。
- combat.js：结算走位、耗时、敌方行动和带护盾的伤害；走位不会消耗日常AP，但不是免费战斗动作。
- huntState.js：白名单恢复标记、复制记录、一次触发状态；weaponEffects.js只绘制残影与精确射击效果，不结算伤害。

WeaponAnomalous owns stateful anomalous resonance hooks (prepare/stats/hit/incoming); WeaponLegendary owns legendary hooks including encounter start and victory. Combat invokes hooks; HuntState validates their saved fields. No UI or network dependency.

WeaponPopup handles 404 resonance with saved random decisions, bounded secondary strikes, shield/status effects and temporary suppression of shield/repair buffs. Combat supplies actual hit resolution; the UI renders one or two in-game error windows. Anomalous attack-time modifiers use the same combat clock as all other rarities.

WeaponTimed owns a saved combat-seconds queue; echoes never recurse. WeaponRed owns counter opportunities and bounded relationship/memory reliability. CombatGroup owns one independent flanking enemy (HP/shield/status/position), including real arc/rail hits and continuation after primary defeat. CombatParty owns encounter HP for Jack and an opt-in existing pet, guard redirection and Pack triggers; ordinary creature HP remains the main fight subject. WeaponMetrics calculates clearly labeled weapon-only sustained DPS and physical carried-weapon volume. Independent displayed-instance UID is saved and removed safely when its instance disappears.

## 叙事模块（0.11.0-preview）
- js/story/lifeScenes.js：30段双语生活数据与按章一次安排。
- js/story/foreshadowing.js、js/lore/jasmine.js：条件伏笔/分级连续性及兄妹回忆。
- js/dialogue/voices.js：独立六阶段声音规则；npcCards.js为既有NPC声音卡及死亡/继任回应。
- js/story/chapters.js：20章目标与关系元数据；使用独立chapterMetadata供选择后果使用，避免提前推进章节。
- js/story/cadence.js：情绪缓冲、首次自称、存档白名单及延迟后果，不负责显示。
- js/story/endings.js、host.js：固定结尾数据与隐藏分支，保留旧ID。
- js/story/textRegistry.js：稳定文本ID，主线/世界/角色分层，变体与选项可单独维护。
- narrativeState/storyMode/narrative/jackStory接入以上规则；NarrativeUI只呈现既定文本。ChatContext/server/dialogue只提供可选自由对话，不写游戏状态。
- navigation.css的剧情专用规则最后覆盖通用导航列，避免隐藏侧栏仍占空间。

## 审定整合与独立剧情播放器（0.12.0-preview）
- data/storyRevisionScenes、Daily、Patches仅持有审定双语数据、行级操作、机构常量；story/revision负责游标/旧flags兼容、一次daily、ACT IX自动分流、按游戏日的E-3计时。
- story/presentation定义CG元数据、按timeline的已读本、10手动/quick/auto记录；global Meta的storyCG为增量字段。Save导入/导出携带已读本，删timeline清理本地手动与备用，不清全局收藏。
- story/player+story-player.css是独立全屏显示层；narrativeUI在Story不重复渲染。打字完成才记已读；AUTO/Skip遇选择停；回看保存完整状态快照而非反向加减flags。
- Narrative负责状态命令与选择，Player不结算养成数值。Engine只在剧情检查点保存，避免每字每行写盘；手动保存精确当前位置。
- story/textRegistry稳定ID保持保护场景原ID，新审批正文REV1前缀；daily表现阶段覆盖仅显示声音，不降低持久语言阶段。
- build-local将唯一CG嵌入portable HTML，editable source使用独立PNG；server静态白名单单独列入CSS和CG，绝不开放服务器文件目录。
- 最新实际验收与未完成需求以NARRATIVE-INTEGRATION-REPORT、TASK-AUDIT为准；旧逐日记录不代表当前实现缺失。

## 双CG与视口（0.12.1-preview）
- StoryCG只声明帧、正式资源与运动参数；StoryCGLayer拥有当前/旧图双层和转场，仅显示，不改剧情。
- StoryViewport负责标准/webkit全屏、HTML目标、安全视口尺寸和失败降级；Player保持触屏/键盘/保存交互职责。
- build-local以正式CG路径内嵌PNG，不依赖临时图片。server只开放明确新增资源。

0.12.2：StoryCG.cues按scene和line声明三图顺序；StoryCG.artDirection与STORY-CG-ART-DIRECTION定义Jack长期角度/帽子规范，不改NarrativeData保护文本。

0.12.3：story-player.css明确CG父层0、对白3、顶部工具4、选择5，避免图片的子z-index跨层遮挡UI；圆润玻璃与系统字体只影响呈现，保留文字/存档逻辑。
## 0.13.1：植物加工、医疗与新闻

- greenhouse/processing.js：数据化加工方式、资源消耗、保质期与价值；breeding.js：品系、亲本、代数与遗传；art.js：独立SVG/未来图片渲染入口。
- diseases.js：疾病内容；riskRules.js：暴露条件；illness.js：潜伏、病程、恢复观察与接触；medicine.js：患者、照护、隔离、资源及旧档读取。
- outbreaks.js：世界疫情、路线、检疫站、当地价格；newsData.js：90个主题目录；news.js：读取世界状态并记录事实变化，不靠打开页面随机造新闻。
- 医疗与温室数据保存在各自状态分支，沿用兼容读取；UI只发送命令。临床记录不修改剧情记忆、Host或Continuity旗标。

## 0.13.2：临床行为与医疗运输

- clinicalEffects.js：按疾病分类/独立覆盖数据计算症状，改变现有进食、训练和疲劳字段，不创造未参与玩法的假属性。
- exposure.js：只接收已成功提交的行为及前后状态，构建环境/食物/事件上下文；lastExposureDay防止同日反复刷新风险。
- clinicalEnglish.js：90条症状/照护英文，与原始疾病编号一一对应，只注册显示文本，不迁移原始剧情/存档字符串。
- relief.js：有上限的医疗运输状态、实际道路搜索、来源地预留物资、延期/改道与一次性交付；保存在infirmary.relief，新闻仅阅读这些记录。


新闻独立链：newsChainsData.js定义15条内容/选项/成本/等待天数；newsChains.js处理确认来源、跨日状态、事务成本和存档校验；news.js只展示与发命令。污染批次使用newsChainId稳定绑定，避免列表下标变化误销毁。

## 独立新闻扩展（0.13.5）

newsChainsData / Batch2 / Batch3Data只持有中英文场景、等待日和显式成本。newsChains为公共阶段、存读档和事务状态机；Batch3拥有新来源判定与维护效果，发现钩子由成功游戏事务调用，页面读取不制造事件。news.js只呈现与派发。数量来自数据长度，目前40/90。房间操作仍由home.js校验，UI同步禁用不可用进入和修理，审计见ROOM-USAGE-AUDIT.md。

`newsChainsBatch4Data.js`承载剩余50条中英文剧情；`newsWorld.js`维护持久区域事件/接收/交接与宵禁。`GardenEquipmentArt`在art.js中独立提供产品、设备、床位SVG接口。Road.atLab统一实验室地理判定。


## 0.13.7：实验室运营与逐病平衡

- greenhouse/diseaseBalance.js：90个明确参数与环境修正；illness/medicine继续负责病程与实际照护，不改剧情旗标。
- lab/operationsData.js与operationsState.js：设备/岗位/零件/故障数据，追加保存与严格有界读取；operations.js：游戏日协调、真实资源、排班、维护、返回报告；operationsUI.js仅展示与派发。
- lab/lifeEventsData.js与maintenanceEventsData.js：双语独立观察条目；events.js使用单独随机数和每日/一次性保护。
- lab/roomData.js：27原ID的楼层、入口、专精、声景/未来背景引用；rooms.js：权限、有限动作、人物位置和隐私；roomUI.js复用已有玩法并保持返回上下文；roomDiagnostics.js只读取同一设备状态。
- roomArt.js/roomDecorArt.js独立SVG层，可替换正式图片；roomAudio.js管理用户开启后的合成环境声与切换清理。没有新增大型引擎或付费生成调用。
- 顶层状态version仍为4；operations与roomSystems各自version 1。旧档缺分支时按当前日初始化，保留原有医疗、人物、物品、剧情与设施升级。没有将物理房间等级硬映射为医疗/温室等级。

### 房间事件（0.13.8）
roomIncidentData.js定义双语题目、选择、成本、后续与逾期；roomIncidents.js处理有界存档、按日触发及原库存结算。operations.incidents兼容旧档，UI通过ops:incident命令调用，剧情模式不参与。
