# Jump Space Mod 集合

Jump Space (Keepsake Games) 的 MelonLoader mod 集合，基于 IL2CPP 反编译分析开发。

## 部署

将 `Mods/` 目录下带版本号的 DLL 复制到游戏安装目录的 `Mods/` 文件夹。

## Mod 列表与版本历史

---

### JumpSpace More Players — 多人联机突破

当前版本: **v1.7.0** | DLL: `JumpSpaceMorePlayers_v1.7.0.dll`

突破4人联机限制，允许5-16人同时游戏。v1.7.0修复SimpleSpawner/RandomSpawning多人问题。v1.5.0起支持1-8P独立战利品倍率配置。

| 版本 | 日期 | 变动 |
|------|------|------|
| v1.7.0 | 2026-07-28 | **SimpleSpawner/RandomSpawning修复**: SimpleSpawner Prefix扩展m_MaxCount/m_MinCount，RandomSpawning Prefix修复>4人时生成逻辑 |
| v1.6.0 | 2026-07-27 | **LootScaling配置修复**: 修复5-8P配置项在MelonPreferences.cfg中不显示的问题 |
| v1.5.1 | 2026-07-23 | **Harmony补丁修复**: `Patch_SetEnabledBasedOnPlayerCount_Evaluate` 的 `out int __origMaxVal` / `int __origMinVal` 参数以`__`前缀被Harmony视为特殊参数但找不到匹配导致IL编译错误，改为静态字段 `_origMaxVal` / `_origMinVal` 传递状态，修复游戏对局卡死 |
| v1.5.0 | 2026-07-22 | **1-8P独立战利品倍率**: 每种LootType×5-8P共4个独立配置项(Consumables/Weapons/HeavyWeapons/Materia/Generic)，5-8P Prefix完全接管使用配置总倍率，4P+使用8P值，1-4P原版逻辑不拦截 |
| v1.4.0 | 2026-07-22 | **5P+战利品倍率系统**: 重构AdjustLootTypeAmountsBasedOnGlobalRules为Prefix完全接管(非clamp)，每种LootType一个5P倍率配置，5P+时先算4P基础乘数再叠乘配置倍率 |
| v1.3.0 | 2026-07-21 | **战利品缩放修复**: 新增 `LootDataSheet.AdjustLootTypeAmountsBasedOnGlobalRules` Prefix补丁，4人时playerCount clamp到4，使用4人乘数配置；ISIL验证原方法用playerCount-1索引m_DataMultipliers数组，4人越界保护跳过乘法导致战利品不缩放 |
| v1.2.1 | 2026-07-21 | **SetEnabledBasedOnPlayerCount关键修复**: m_MaxValue扩展目标从FALLBACK_PLAYER_COUNT(4)改为MaxPlayers.Value(如8)。v1.2.0缺陷：4人时playerCount>4仍导致SetActiveNetworked(false)禁用任务对象 |
| v1.2.0 | 2026-07-20 | **任务目标修复**: 新增3个补丁——SetEnabledBasedOnPlayerCount.Evaluate() Prefix扩展m_MaxValue；PlayerCountCondition.Evaluate() Prefix改为>=比较；MateriagunInteractionController Postfix日志 |
| v1.1.0 | 2026-07-19 | **>4人数值回退策略**: ISIL验证发现三种>4人行为——struct字段查询(安全)、List索引查询(回退[0])、switch无default(零修补符)。新增12个playerCount clamp Prefix补丁(10 WaveSpawner + ChallengeRating + ModifierSystem) |
| v1.0.0 | 2026-07-18 | **初始版本**: NetworkManager.Init Postfix修改m_MaxPlayers突破网络层4人上限 |

**补丁清单 (17个)**:
- NetworkManager.Init Postfix (网络层突破)
- 10× WaveSpawner Prefix (波次缩放clamp)
- ChallengeRatingBudgetRow Prefix (挑战评级预算clamp)
- PlayerCountModifierComponent Prefix (修饰符clamp)
- SetEnabledBasedOnPlayerCount Prefix (任务目标激活)
- PlayerCountCondition Prefix (任务条件匹配)
- MateriagunInteractionController Postfix (日志)
- LootDataSheet Prefix (战利品1-8P独立倍率)

**v1.5.0 战利品倍率配置 (LootScaling分类)**:

| LootType分类 | 5P | 6P | 7P | 8P |
|---|---|---|---|---|
| Consumables (消费品) | 1.25 | 1.50 | 1.75 | 2.00 |
| Weapons (武器) | 1.0 | 1.0 | 1.0 | 1.0 |
| HeavyWeapons (重型武器) | 1.0 | 1.0 | 1.0 | 1.0 |
| Materia (大/小/云材料) | 1.0 | 1.0 | 1.0 | 1.0 |
| Generic (其他) | 1.0 | 1.0 | 1.0 | 1.0 |

- 1-4P: 原版逻辑不拦截
- 5-8P: Prefix接管，使用用户配置的总倍率(非叠乘)
- 8P+: 使用8P配置值
- LargeMateria/SmallMateria/MateriaClouds共用Materia组

---

### Jump Space Crisis Dumper — 危机系统数据导出

当前版本: **v1.5.0** | DLL: `JumpSpaceCrisisDumper_v1.5.0.dll`

导出CrisisHandlerSheet中1P-4P各人数配置的DamageControllerData全部字段(27个)。v1.5.0起改为手动导出模式(F7)并添加Enabled配置开关。输出Markdown格式(`危机数据.md`)。

| 版本 | 日期 | 变动 |
|------|------|------|
| v1.5.0 | 2026-07-28 | **手动导出模式+Enabled配置**: 移除自动导出(切换地图重复导出)，仅F7手动触发；添加MelonPreferences `[CrisisDumper]` Enabled配置开关 |
| v1.4.0 | 2026-07-23 | **Markdown格式输出**: 输出文件改为`危机数据.md`，表格/标题/列表markdown语法，CR激活标记✅/❌保留 |
| v1.3.0 | 2026-07-22 | **CR激活检定**: CR区间列表标记当前GetData激活段(✅)，详细数据区每个DCD标记✅当前CR激活/❌CR未激活/人数未激活，非激活人数组整体标记[❌未激活人数] |
| v1.2.0 | 2026-07-22 | 新增当前玩家数激活检定：GetData返回当前CR区间配置，激活人数列标✅，4P提示使用4P配置 |
| v1.1.0 | 2026-07-22 | 重构输出格式：增加跨人数对比摘要行(低CR/高CR)，详细数据改为分组紧凑布局 |
| v1.0.0 | 2026-07-22 | 初始版本：导出飞船危机系统1-4P配置数据 |

---

### Jump Space ChemicalPayload Fix — 化学弹头修复

当前版本: **v1.1.0** | DLL: `JumpSpaceChemicalPayloadFix_v1.1.0.dll`

修复化学弹头描述中Damage Cap与Damage显示位置颠倒的问题。

**原版bug**: 描述模板 "造成 {1} 点伤害后...造成 {0} 点伤害" 中，`{0}` 映射 Damage Cap (ValueIndex=0)，`{1}` 映射 Damage (ValueIndex=1)，导致语义颠倒——腐蚀伤害显示在触发阈值位置，触发阈值显示在腐蚀伤害位置。

**修复方案**: 交换 `m_ValueIndex` (0↔1)，使 `{0}` 映射 Damage，`{1}` 映射 Damage Cap，描述语义正确："造成[触发阈值]点伤害后...造成[腐蚀伤害]点伤害"。

| 版本 | 日期 | 变动 |
|------|------|------|
| v1.1.0 | 2026-07-25 | **修复描述顺序**: 交换m_ValueIndex(0↔1)使描述占位符映射正确；移除v1.0.0错误翻转ValuePerUpgrade正负号的逻辑 |
| v1.0.0 | 2026-07-09 | 初始版本(已废弃)：错误翻转ValuePerUpgrade正负号，未解决描述顺序问题 |

---

### Jump Space Damage Constant Reader — 伤害常量读取

当前版本: **v1.7.0** | DLL: `JumpSpaceDamageConstReader_v1.7.0.dll`

读取CalculateServerDamage中的IL2CPP运行时初始化常量值。v1.7.0添加Enabled配置开关。v1.7.0已移除Harmony补丁(仅读取常量)。

| 版本 | 日期 | 变动 |
|------|------|------|
| v1.7.0 | 2026-07-28 | **Enabled配置**: 添加MelonPreferences `[DamageConstReader]` Enabled配置开关 |
| v1.7.0 | 2026-07-26 | **崩溃修复**: 完全移除CalculateServerDamage Harmony补丁 |
| v1.4.0 | 2026-07-24 | **ISIL→RVA映射偏移修正+伤害逻辑纠正+术语更新**: RVA=ISIL_Address-ImageBase+0x22A0，PE验证5常量全部匹配。纠正伤害逻辑：应急保护窗口内90%减伤(非100%穿透)，窗口外低血量50%减伤急救，正常血量全额伤害。术语：爆发保护→应急保护，血细胞→核心生命单位 |
| v1.3.0 | 2026-07-24 | **RVA映射修正+语义纠正**: ①移除错误的+0x12B0偏移，改用RVA=ISIL_Address-ImageBase(0x180000000)，修复运行时常量读取返回垃圾值 ②语义标签纠正：0.1f=爆发保护倍率(非"正常倍率")，5.0f=爆发窗口时长(非"时间窗口") ③CalculateServerDamage逻辑描述纠正：爆发窗口内100%穿透，窗口外才应用0.1f/0.5f倍率 ④Harmony日志标签同步修正 |
| v1.2.0 | 2026-07-23 | **Markdown格式输出**: 输出文件改为`伤害常量.md`，表格/标题/列表markdown语法 |
| v1.1.0 | 2026-07-21 | 移除F10冗余快捷键(已有自动导出)；保留F11实时日志开关 |
| v1.0.0 | 2026-07-16 | 初始版本：读取伤害计算常量 |

---

### Jump Space Enemy Health Exporter — 敌人血量导出

当前版本: **v3.2.0** | DLL: `JumpSpaceEnemyHealthExporter_v3.2.0.dll`

导出所有AI_TuningFile的血量/护盾数据，含激活检定(✅当前生效/❌门槽未知)。v3.2.0起改为手动导出模式(F8)并添加Enabled配置开关。输出Markdown格式(`敌人血量.md`)。

| 版本 | 日期 | 变动 |
|------|------|------|
| v3.2.0 | 2026-07-28 | **手动导出模式+Enabled配置**: 移除自动导出(切换地图重复导出)，仅F8手动触发；添加MelonPreferences `[EnemyHealthExporter]` Enabled配置开关 |
| v3.1.0 | 2026-07-23 | **Markdown格式输出**: 输出文件改为`敌人血量.md`，表格/标题/列表markdown语法，激活标记保留 |
| v3.0.0 | 2026-07-22 | **激活检定**: 步战敌人扫描OnFoot_SquadData.m_MinRequiredPlayerCount，飞船扫描AIShipSheet.m_MinPlayerCount(含偏移x58回退)，模糊名称匹配关联AI_TuningFile，输出✅/❌/❓标记；新增ExportSpawnConfiguration生成配置参考表 |
| v2.3.0 | 2026-07-21 | 恢复F8手动重新导出(空战载具需场景中有敌方飞船才能捕获) |
| v2.2.0 | 2026-07-21 | 移除F8冗余快捷键(已有自动导出，场景加载时自动执行) |
| v2.1.0 | 2026-07-19 | 增强导出功能 |
| v1.0.0 | 2026-07-17 | 初始版本：导出敌人血量数据 |

---

---

### Jump Space Loot Multiplier Dumper — 战利品乘数导出

当前版本: **v2.2.0** | DLL: `JumpSpaceLootMultiplierDumper_v2.2.0.dll`

导出GlobalLootDataRule乘数表+LootManagerData基础数量表。v2.2.0起改为手动导出模式(F9)并添加Enabled配置开关。输出Markdown格式(`战利品倍率.md`)。

| 版本 | 日期 | 变动 |
|------|------|------|
| v2.2.0 | 2026-07-28 | **手动导出模式+Enabled配置**: 移除自动导出(切换地图重复导出)，仅F9手动触发；添加MelonPreferences `[LootMultiplierDumper]` Enabled配置开关 |
| v2.1.0 | 2026-07-23 | **Markdown格式输出**: 输出文件改为`战利品倍率.md`，表格/标题/列表markdown语法 |
| v2.0.0 | 2026-07-22 | **可读性重构**: 按活动类型分类(Finale/Major/Minor/Safe等)，概览摘要表，◆固定/◇随机标记，权重概率估算(CR1≈0% CR5≈0%)，展开LootBundleContainer内容 |
| v1.0.0 | 2026-07-22 | 初始版本：导出GlobalLootDataRule乘数+LootManagerData基础数量 |

---

### Jump Space Consumable Exporter — 消费品数据导出

当前版本: **v1.4.0** | DLL: `JumpSpaceConsumableExporter_v1.4.0.dll`

导出消费品/部署物数据到Markdown文件。v1.4.0起改为手动导出模式(F6)并添加Enabled配置开关。输出中文Markdown格式(`消费品数据.md`)。

| 版本 | 日期 | 变动 |
|------|------|------|
| v1.4.0 | 2026-07-28 | **手动导出模式+Enabled配置**: 移除自动导出(切换地图重复导出)，仅F6手动触发；添加MelonPreferences `[ConsumableExporter]` Enabled配置开关；快捷键从F4改为F6 |
| v1.3.0 | 2026-07-24 | **部署物场景数据缓存+名称修正**: ①部署物消耗后仍保留场景数据(实例级Dictionary按名称索引，新数据优先+缓存回退)，标注[缓存数据]来源 ②中文名称修正——医疗针剂→医疗兴奋剂、医疗伙伴→医疗 EM-8、增援部署物→伤害放大器 ③弹匣持持续时间改为"直到充能用完"(无部署动画) |
| v1.2.0 | 2026-07-23 | **Markdown格式输出**: 输出文件改为`消费品数据.md`，表格/标题/列表markdown语法 |
| v1.1.0 | 2026-07-21 | 移除F4冗余快捷键(已有自动导出) |
| v1.0.0 | — | 初始版本 |

---

### Jump Space Module Classifier — 模块近战/枪械分类器

当前版本: **v3.2.0** | DLL: `JumpSpaceModuleClassifier_v3.2.0.dll`

方案A分类器：通过分析步战模块的白名单/黑名单（m_AllowedItems/m_ForbiddenItems），将74个步战模块分类为近战专属(MeleeOnly)/枪械专属(RangedOnly)/通用(Universal)。v3.2.0起改为手动导出模式(F8)并添加Enabled配置开关。输出`模块分类结果.md`供ModuleExporter读取。

| 版本 | 日期 | 变动 |
|------|------|------|
| v3.2.0 | 2026-07-28 | **手动导出模式+Enabled配置**: 移除自动导出(切换地图重复导出)，仅F8手动触发；添加MelonPreferences `[ModuleClassifier]` Enabled配置开关 |
| v3.1.0 | 2026-07-26 | **术语规范化**: 表格列标题Allowed/Forbidden→白名单/黑名单，说明文字AllowedItems/ForbiddenItems→白名单/黑名单（m_AllowedItems/m_ForbiddenItems） |
| v3.0.0 | 2026-07-25 | **分类阈值修正+武器名输出**: ①分类阈值从100%改为>50%(forbidMostMelee=ForbiddenMeleeCount*2>totalMelee)，Breakthrough等禁止4/5近战的模块正确分类为RangedOnly ②ModuleResult新增AllowedMeleeNames/ForbiddenMeleeNames等 ③ExportResults新增详细武器兼容性章节 |
| v2.0.0 | 2026-07-25 | **方案A完善版**: ①近战武器发现——m_WeaponEntriesByGuid只含枪械，从白名单列表收集非枪械GUID反推近战武器(5个) ②黑名单列表含非武器物品(35个GUID仅在黑名单中出现，是消耗品/Cosmetic等，不影响分类) ③分类逻辑——白名单驱动+黑名单从forbidAll判专属(None) ④交叉验证通过——MeleeOnly 10/RangedOnly 10/Universal 54/None 0 ⑤输出枪械分组(基础4+附加60)+近战分组(基础4+附加60) |
| v1.0.0 | 2026-07-25 | 初始版本：方案A兼容性矩阵分类 |

**分类逻辑说明**:
- **白名单(m_AllowedItems)**: 含近战GUID=兼容近战，含枪械GUID=兼容枪械，两者都有=Universal
- **黑名单(m_ForbiddenItems)**: 仅当禁止全部枪械(forbidMostRanged)→近战专属，仅当禁止全部近战(forbidMostMelee)→枪械专属，同时禁止全部→None
- **两者皆空** = Universal
- 非武器禁止项(消耗品/Cosmetic等GUID)不影响分类

---

### Jump Space Module Exporter — 模块数据导出

当前版本: **v1.21.0** | DLL: `JumpSpaceModuleExporter_v1.21.0.dll`

导出所有模块/武器/组件数据到Markdown文件。v1.21.0添加Enabled配置开关+仅导出一次(切换地图不重复)。v1.15.0起基础模块按武器类型分别收集(枪械基础模块不再出现在近战分组)。v1.14.0起基础模块判定使用BaseModuleSet.m_Modules显式列表。快捷键: F1 飞船导出, F2 特殊武器重新导出

**配置**: MelonPreferences `[ModuleExporter]` — Enabled (默认true, 设为false禁用导出)

| 版本 | 日期 | 变动 |
|------|------|------|
| v1.21.0 | 2026-07-28 | **Enabled配置+单次导出**: 添加MelonPreferences Enabled配置开关；改为仅导出一次(切换地图不重置_autoExported) |
| v1.21.0 | 2026-07-26 | **术语规范化**: Allowed/Forbidden→白名单/黑名单，AllowedItems/ForbiddenItems→白名单列表/黑名单列表（m_AllowedItems/m_ForbiddenItems字段名不变） |
| v1.20.0 | 2026-07-25 | **模块分配过滤机制导出**: 白名单/黑名单武器名解析，限定武器显示为"白名单=X个, 黑名单=Y个" |
| v1.19.0 | 2026-07-25 | **废案检测修复**: 新增m_IsBasicModule标志检测，废案判定条件改为!isInSchool && !isBaseModule && !isBasicModuleFlag，Allowed/Forbidden诊断输出 |
| v1.17.0 | 2026-07-25 | **基础模块按武器类型分离**: CollectBaseModuleNames改为CollectBaseModuleNamesByType，按PickupableItem_Data_GenericWeapon区分为枪械/近战武器，分别收集基础模块名集合。枪械专属基础模块(BasicMag/BasicReload/BasicTrigger等)不再出现在近战分组 |
| v1.14.0 | 2026-07-25 | **基础模块判定修正**: ①从PickupableItem_Data.m_BaseModuleSet.m_Modules显式列表收集基础模块名集合，替代m_IsBasicModule字段(该字段**影响生成逻辑**——GetRelevantModules()中m_IsBasicModule=true的模块被排除出随机池，仅能通过BaseModuleSet显式放置) ②EmpToCorrosion_Ship标注为废案(未被任何模块池引用，已被EmpToDisruption替代) |
| v1.13.0 | 2026-07-25 | **飞船全量导出**: 策略D3 FindObjectsOfTypeAll始终运行，遍历所有ShipMoveSettings_Playership资产+名称匹配，一次导出全部飞船移动参数 |
| v1.12.0 | 2026-07-25 | **飞船数据缓存+重复输出修复**: ①飞船移动参数跨导出调用缓存累积(实例级Dictionary按shipType索引，新数据优先+缓存回退)，切换飞船后按F1导出可累积多艘飞船数据，缓存数据标注"（缓存数据）" ②修复AppendMoveSettings 5个段落各输出两次的重复bug ③未关联飞船类型(-1)仅当缓存无已关联类型时输出 |
| v1.11.0 | 2026-07-25 | **分类分组导出**: 步战武器模块池读取Classifier分类结果(`模块分类结果.md`)，按枪械分组(基础+附加)和近战分组(基础+附加)输出，通用模块两边都显示，每个模块标注分类标签(近战专属/枪械专属/通用)。分类文件不存在时回退原格式 |
| v1.10.0 | 2026-07-24 | **运行时数据缓存+手榴弹类型区分**: ①手榴弹/火箭弹运行时数据跨导出调用缓存累积(实例级Dictionary按名称索引，新数据优先+缓存回退) ②手榴弹子类型区分——Pickupable_TimedGrenade_Data显示"破片手榴弹"，Pickupable_StickyGrenade_Data显示"粘性手榴弹" ③手榴弹合计行显示(破片+粘性) |
| v1.9.0 | 2026-07-23 | **Markdown格式输出**: 6个输出文件改为中文md：`模块数据.md`/`组件数据.md`/`武器数据.md`/`神器数据.md`/`特殊武器数据.md`/`飞船数据.md`，表格/标题/列表markdown语法 |
| v1.8.1 | 2026-07-21 | F5→F1/F6→F2(避免与ItemEditor F5冲突) |
| v1.8.0 | 2026-07-21 | F12→F5(避免Steam截图冲突)；恢复F6手动重新导出特殊武器(装备后数据才可用) |
| v1.7.0 | 2026-07-21 | 移除F5冗余快捷键；F6→F12 |
| v1.6.0 | 2026-07-13 | 增强导出功能 |
| v1.0.0 | — | 初始版本 |

---

### Jump Space Rarity Mod — 稀有度修改

当前版本: **v4.0.0** | DLL: `JumpSpaceRarityMod_v4.0.0.dll`

修改物品稀有度/品质。v4.0.0新增CR资源倍率功能（按威胁等级缩放资源产出量，兼容MorePlayers）。

| 版本 | 日期 | 变动 |
|------|------|------|
| v4.0.0 | 2026-07-30 | **CR资源倍率**: 新增Resource配置分类(EnableCRResourceScaling + CR1-5独立倍率)；CRResourceScalingPatch Postfix补丁；兼容MorePlayers(CR倍率叠加在人数倍率之上) |
| v3.9.0 | 2026-07-23 | **Markdown格式输出**: 默认权重导出改为`默认权重.md`，表格/标题markdown语法 |
| v3.7.0 | 2026-07-12 | 增强稀有度修改功能 |
| v1.0.0 | — | 初始版本 |

---

### Jump Space Status Effect Exporter — 状态效果导出

当前版本: **v1.3.0** | DLL: `JumpSpaceStatusEffectExporter_v1.3.0.dll`

导出所有状态效果的描述与数值到Markdown文件。v1.3.0添加Enabled配置开关(默认true)。输出Markdown格式(`状态效果数据.md`)。

| 版本 | 日期 | 变动 |
|------|------|------|
| v1.3.0 | 2026-07-28 | **Enabled配置**: 添加MelonPreferences `[StatusEffectExporter]` Enabled配置开关(默认true，设为false禁用) |
| v1.2.0 | 2026-07-23 | **Markdown格式输出**: 输出文件改为`状态效果数据.md`，表格/标题/列表markdown语法 |
| v1.1.0 | 2026-07-21 | 移除F9冗余快捷键(已有自动导出) |
| v1.0.0 | 2026-07-15 | 初始版本：状态效果数据导出 |

---

---

### Jump Space Gen Capture — 物品生成流程抓取器

当前版本: **v1.8.0** | DLL: `JumpSpaceGenCapture_v1.8.0.dll`

运行时Hook ItemGenerator.Generate，捕获武器/组件生成过程和BaseModuleSet数据。v1.8.0合并F7-F10为单一F7全量导出+模块级Allowed/Forbidden GUID。快捷键: F7 全量导出, F11 场景物品溯源

**配置**: MelonPreferences `[GenCapture]` — Enabled (默认true, 设为false禁用Hook和dump)

| 版本 | 日期 | 变动 |
|------|------|------|
| v1.8.0 | 2026-07-31 | **全量导出合并+模块黑白名单**: 合并F7-F10为单一F7全量导出；新增模块级AllowedItems/ForbiddenItems GUID导出；输出合并为GenCapture_FullDump.log；Section 2新增BaseModuleSet.m_ExcludedRarities导出 |
| v1.7.0 | 2026-07-30 | **ExcludedRarities导出**: Section 2新增BaseModuleSet.m_ExcludedRarities导出（ItemRarityFlags位标志，标识模板排除的品质） |
| v1.6.0 | 2026-07-29 | **F7全量导出合并**: 合并F7-F10为单一F7全量导出；新增模块级AllowedItems/ForbiddenItems GUID导出 |
| v1.5.0 | 2026-07-29 | **F11修复**: 恢复使用Resources.FindObjectsOfTypeAll修复场景扫描 |
| v1.4.0 | 2026-07-28 | **F11修复**: 改用Harmony补丁追踪OnPostSetupItemData事件 |
| v1.3.0 | 2026-07-28 | **F11修复**: 改用FindObjectsOfTypeAll+TryCast |
| v1.2.0 | 2026-07-28 | **F11增强溯源**: 模块GUID→名称解析、MaxRarity截断检测 |
| v1.1.0 | 2026-07-28 | **F7 dump**: ItemGenerationConfig + CosmeticData导出 |
| v1.0.0 | 2026-07-28 | 初始版本：Hook Generate + BaseModuleSet/Weight dump + Enabled配置 |

**输出文件**:
- `Mods/GenCapture_FullDump.log` — F7触发（全量数据）
- `Mods/GenCapture_Trace.log` — F11触发（场景物品溯源）

---

### Jump Space Item Spawner — 物品生成器

当前版本: **v1.28.0** | DLL: `JumpSpaceItemSpawner_v1.28.0.dll`

GUI菜单按分类生成物品到玩家手中。支持三级菜单展开选择个体物品。v1.28.0算法逆向文档一致性修复：ExcludedRarities品质上限+加权随机+模块品质Roll+流派显示。

**配置**: MelonPreferences `[ItemSpawner]` — Enabled (默认true, 设为false则不显示GUI、不响应命令)

| 版本 | 日期 | 变动 |
|------|------|------|
| v1.28.0 | 2026-07-31 | **算法逆向文档一致性修复+灰色名字**: ①ExcludedRarities品质上限检查(传感器/瞄准→只能Common，护盾发生器→最高Epic) ②BaseModuleSet选模块从均匀随机改为m_Weight加权随机 ③School选择从合并所有School改为m_SelectionWeight加权随机选一个 ④TryAddModuleWithRarityFallback先Roll模块品质再降级重试 ⑤Item Editor显示流派名称+替换模块只显示当前流派模块 ⑥ForceNoQuality物品m_TemplateGuid=""使IsGenerated=false→灰色名字 |
| v1.27.0 | 2026-07-31 | **分类修正**: ①CompCatMap {11}从"特殊武器"改为"护盾发生器"(护盾再生器归入护盾发生器) ②爆发护盾名称覆盖归入"特殊武器" ③电池从"补给品"改为"任务物品" ④辅助电源(消耗品)归入"其它/未知" ⑤放射性棒ForceNoQuality ⑥物质容器废案检测不再要求"重型"标签 |
| v1.26.0 | 2026-07-31 | **分类修正+ForceNoQuality**: ①护盾发生器+瞄准模块归入"特殊武器"组件组 ②"强力炮塔"改名"特殊武器" ③特殊武器/补给品/收集品/任务物品/废案物品→ForceNoQuality ④消耗品下新增"废案物品"子分类 |
| v1.25.0 | 2026-07-30 | **BuildModules重写**: 按ISIL逆向确认的两条规则重写——(1)基础模块品质直接绑定物品品质不做Clamp (2)附加模块TryAddModuleWithRarityFallback降级重试(Legendary→Epic→Rare→Common)，按m_MinRarity/m_MaxRarity内联过滤候选模块。移除不存在的ClampModuleRarity方法。ItemEditor替换模块品质改为直接使用物品品质 |
| v1.24.0 | 2026-07-29 | **消耗品生成修复**: 消耗品(IsConsumable=true)不再走RollItemRarity+BuildGeneratedItem流程，改为创建Common品质、0模块、0外观的简单GeneratedItem |
| v1.23.0 | 2026-07-29 | **移除神器功能**: 删除神器GUI按钮和所有神器代码，保留ArtifactEntry类和_allArtifacts字段供参考 |
| v1.22.0 | 2026-07-29 | **Item Editor功能**: 独立GUI窗口编辑手持物品的模块和瞄具。GUI重构为双顶层按钮，Editor功能：获取手持物品信息→显示模块/外观列表→替换模块(品质自动提升至min(m_MaxRarity,物品品质)，去重)→替换瞄具(兼容标签+品质范围过滤)→确认重建 |
| v1.21.1 | 2026-07-29 | **采矿激光枪分类修复**: CarryType映射到"近战"后增加名称覆盖检查，采矿激光/mininglaser改分到"未完成武器" |
| v1.21.0 | 2026-07-29 | **采矿激光枪移至"未完成武器"**: 新增"移除手中物品"按钮(DestroyHeldItem直接销毁) |
| v1.20.0 | 2026-07-29 | **模拟生成+瞄具分配+分类重构+品质权重**: ①注释ItemGenerator.Generate调用，改用BuildGeneratedItem模拟生成 ②RollItemRarity从ItemGenerationConfig读取CR权重 ③RollArtifactRarity调用GameplayModifierManager.GetRarity() ④GenerateCosmeticsForWeapon瞄具分配 ⑤分类重构5大类+子类 ⑥神器品质按自然生成权重分配(60/30/10) |
| v1.19.0 | 2026-07-29 | **神器品质随机生成**: 按自然生成权重(Common=60%, Rare=30%, Legendary=10%)分配品质；AddArtifact后通过unsafe修改m_Rarity(offset 0x1B8) |
| v1.18.0 | 2026-07-28 | **修正GetModuleCount**: ISIL反汇编确认返回School附加模块数(Common=0,Rare=1,Epic=2,Legendary=3)，非总模块数；BuildModules中targetCount改为BaseModuleSet已选数+School附加数 |
| v1.17.0 | 2026-07-28 | **GenerationConfig可用性检查+Enabled配置**: Generate前检查ItemGenerator.GenerationConfig是否为null；添加MelonPreferences Enabled配置开关 |
| v1.16.0 | 2026-07-28 | **模块生成修复**: ItemGenerator.Generate失败时手动构建模块(BaseModuleSet+AllItemModules)；添加GenerationConfig/AllItemModules诊断日志；默认Rarity改为Rare(2模块)；ClampModuleRarity/RollBaseValues/GetModuleCount完整实现 |
| v1.15.0 | 2026-07-27 | **特殊武器移至消耗品**: IsConsumable()优先于WeaponCatMap；CarryType 12/13/26/27从WeaponCatMap移除；名称兜底增强 |
| v1.14.0 | 2026-07-27 | **分类重构**: 近战合并为单一分类；左轮→手枪、PDW→冲锋枪、半自动步枪→步枪；磁轨炮/火箭筒/手雷移至特殊武器；WeaponCatMap优先于IsConsumable；包含m_ShouldGenerate=false物品；名称兜底分类；尝试ItemGenerator.Generate获取模块 |
| v1.13.0 | 2026-07-26 | **三级菜单实现**: 修复GUI.BeginScrollView崩溃；神器列表展开；SpawnSpecificArtifact |
| v1.12.0 | 2026-07-26 | **神器数据源**: AllArtifactScriptables(23个)；AddArtifact()生成 |
| v1.10.0 | 2026-07-25 | **分类功能正常**: 13武器/31组件/1神器/17消耗品 |
| v1.3.0 | 2026-07-24 | **GUI子分类面板修复** |

---

### Jump Space Player Count Tracker — 人数追踪器

当前版本: **v1.3.0** | DLL: `JumpSpacePlayerCountTracker_v1.3.0.dll`

诊断mod，追踪所有playerCount相关方法的调用和返回值，用于定位5P+环境下"禁用干扰器"任务中Power Conduit不出现的根因。32个追踪补丁覆盖干扰器建筑架构全链路。

**配置**: MelonPreferences `[PlayerCountTracker]` — EnableTracking (默认true), MinPlayerCount (默认0)

| 版本 | 日期 | 变动 |
|------|------|------|
| v1.3.0 | 2026-07-31 | 修复补丁15 AmbiguousMatchException；新增12个干扰器建筑补丁(22-32)：JamController.OnActiveChanged、BreakpointInteractManager、MultiInteractBreakpoint、MultiInteractToggler、Destructible.SafeStart、SetEnabledBasedOnPlayerCount.SafeStart；补丁数21→32 |
| v1.2.0 | 2026-07-31 | 新增8个补丁(14-21)：AI_Ship_SquadHandler、OnFoot_WaveSpawner、JumpDriveJamController |
| v1.1.0 | 2026-07-30 | **修复**: 移除GameObjectSpawner.Spawn()补丁(HarmonyException)，补丁数14→13 |
| v1.0.0 | 2026-07-30 | 初始版本：14个追踪补丁 |

---

### Jump Space Config Guide — 配置说明生成器

当前版本: **v1.0.1** | DLL: `JumpSpace_ConfigGuide_v1.0.1.dll`

自动检测已加载的Jump Space mod，生成统一的中文配置说明文件(`UserData/MelonPreferences_配置说明.cfg`)。每次游戏启动自动刷新。

| 版本 | 日期 | 变动 |
|------|------|------|
| v1.0.1 | 2026-07-28 | 初始版本：自动检测已加载mod + 读取MelonPreferences.cfg section + 残留section检测 |

---

## 技术栈

- **框架**: MelonLoader + Il2CppInterop + HarmonyX
- **游戏引擎**: Unity IL2CPP (Netcode for GameObjects)
- **反编译工具链**: Cpp2IL → ISIL/DiffableCs
- **目标运行时**: .NET 6.0

---

## 参考文档

### 分析文档

| 文档 | 说明 |
|------|------|
| [`战利品分配规则.md`](战利品分配规则.md) | 战利品权重系统、CR插值、概率计算、最大余额法分配算法、数据结构层级 |
| [`组件故障机制参考.md`](组件故障机制参考.md) | 飞船组件故障机制 |
| [`危机系统深度分析.md`](危机系统深度分析.md) | Broken/Critical差异、节流危机算法、伤害点子系统 |
| [`人数缩放机制分析.md`](人数缩放机制分析.md) | >4人数值缩放机制分析 |
| [`模块分配过滤机制.md`](模块分配过滤机制.md) | 模块池/白名单/黑名单/流派/废案过滤机制 |
| [`模块分类结果.md`](模块分类结果.md) | 步战模块近战/枪械分类结果(74模块) |

### Mod运行时导出(Markdown)

| 文档 | 来源Mod | 说明 |
|------|---------|------|
| [`默认权重.md`](默认权重.md) | Rarity Mod | 物品稀有度CR权重表 |
| [`战利品倍率.md`](战利品倍率.md) | Loot Multiplier Dumper | 战利品乘数与基础数量 |
| [`危机数据.md`](危机数据.md) | Crisis Dumper | 飞船危机系统1-4P配置 |
| [`伤害常量.md`](伤害常量.md) | Damage Constant Reader | IL2CPP运行时伤害常量 |
| [`敌人血量.md`](敌人血量.md) | Enemy Health Exporter | 敌人血量/护盾/激活检定 |
| [`模块数据.md`](模块数据.md) | Module Exporter | 模块按池分组数据(步战武器池含枪械/近战分组) |
| [`模块分类结果.md`](模块分类结果.md) | Module Classifier | 步战模块近战/枪械分类结果 |
| [`组件数据.md`](组件数据.md) | Module Exporter | 组件按类型分类数据 |
| [`武器数据.md`](武器数据.md) | Module Exporter | 步战武器完整属性 |
| [`神器数据.md`](神器数据.md) | Module Exporter | 神器按稀有度效果参数 |
| [`消费品数据.md`](消费品数据.md) | Consumable Exporter | 消费品/部署物数据 |
| [`特殊武器数据.md`](特殊武器数据.md) | Module Exporter | 磁轨炮/火箭弹/手榴弹/近战/Materia枪 |
| [`飞船数据.md`](飞船数据.md) | Module Exporter | 飞船蓝图属性/移动参数 |
| [`状态效果算法.md`](状态效果算法.md) | Status Effect Calc | 9个状态效果TweakableValues与伤害计算 |
| [`状态效果数据.md`](状态效果数据.md) | Status Effect Exporter | 所有状态效果描述与数值 |
| [`GenCapture_Generation.log`](GenCapture_Generation.log) | Gen Capture | 物品生成事件日志 |
| [`GenCapture_BaseModuleSet.log`](GenCapture_BaseModuleSet.log) | Gen Capture | BaseModuleSet数据(F8触发) |
| [`GenCapture_ModuleWeights.log`](GenCapture_ModuleWeights.log) | Gen Capture | 模块权重数据(F9触发) |

---

### Jump Space Status Effect Calc — 状态效果计算器

当前版本: **v1.6.0** | DLL: `JumpSpaceStatusEffectCalc_v1.6.0.dll`

导出9个状态效果的TweakableValues并计算实际伤害，含模块覆盖影响章节。v1.6.0添加Enabled配置开关(默认true)。输出Markdown格式(`状态效果算法.md`)。

| 版本 | 日期 | 变动 |
|------|------|------|
| v1.6.0 | 2026-07-28 | **Enabled配置**: 添加MelonPreferences `[StatusEffectCalc]` Enabled配置开关(默认true，设为false禁用) |
| v1.5.0 | 2026-07-23 | **模块覆盖影响**: 综合ModuleExporter数据，新增"模块覆盖影响"章节——12个模块显式(Virus×4/Corrosion×4/Sear×8/Rupture×3/EMP×5)，按效果分组，按稀有度(Common/Uncommon/Rare/Epic)输出覆盖参数+满级值计算(baseValue + perUpgrade × maxLevel) |
| v1.4.0 | 2026-07-23 | **Markdown格式输出**: 输出文件改为`状态效果算法.md`，表格/标题/列表markdown语法 |
| v1.3.0 | 2026-07-21 | 移除F9冗余快捷键(已有自动导出) |
| v1.2.0 | 2026-07-15 | 增强计算功能 |
| v1.0.0 | — | 初始版本 |
