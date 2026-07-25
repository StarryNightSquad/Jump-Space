# Jump Space Mod 集合

Jump Space (Keepsake Games) 的 MelonLoader mod 集合，基于 IL2CPP 反编译分析开发。

## 部署

将 `Mods/` 目录下带版本号的 DLL 复制到游戏安装目录的 `Mods/` 文件夹。

## Mod 列表与版本历史

---

### JumpSpace More Players — 多人联机突破

当前版本: **v1.5.1** | DLL: `JumpSpaceMorePlayers_v1.5.1.dll`

突破4人联机限制，允许5-16人同时游戏。v1.5.0起支持1-8P独立战利品倍率配置。

| 版本 | 日期 | 变动 |
|------|------|------|
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

当前版本: **v1.4.0** | DLL: `JumpSpaceCrisisDumper_v1.4.0.dll`

导出CrisisHandlerSheet中1P-4P各人数配置的DamageControllerData全部字段(27个)。v1.4.0起输出Markdown格式(`危机数据.md`)。快捷键: F7 手动重新导出

| 版本 | 日期 | 变动 |
|------|------|------|
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

当前版本: **v1.5.0** | DLL: `JumpSpaceDamageConstReader_v1.5.0.dll`

读取CalculateServerDamage中的IL2CPP运行时初始化常量值。v1.5.0修复Harmony Prefix参数签名(ref→in)导致的CoreCLR崩溃。快捷键: F11 实时日志开关

| 版本 | 日期 | 变动 |
|------|------|------|
| v1.5.0 | 2026-07-25 | **崩溃修复**: ①CalculateServerDamage Prefix参数签名`ref DamageInfo`→`in DamageInfo`，匹配IL2CPP原始签名，避免struct引用字段GC不安全复制导致CoreCLR Access Violation(0xc0000005) ②移除m_Ship_StateBlackboardData引用字段访问(BlackboardAuto属性GC不安全) ③DamageInfo字段访问加try-catch保护 |
| v1.4.0 | 2026-07-24 | **ISIL→RVA映射偏移修正+伤害逻辑纠正+术语更新**: RVA=ISIL_Address-ImageBase+0x22A0，PE验证5常量全部匹配。纠正伤害逻辑：应急保护窗口内90%减伤(非100%穿透)，窗口外低血量50%减伤急救，正常血量全额伤害。术语：爆发保护→应急保护，血细胞→核心生命单位 |
| v1.3.0 | 2026-07-24 | **RVA映射修正+语义纠正**: ①移除错误的+0x12B0偏移，改用RVA=ISIL_Address-ImageBase(0x180000000)，修复运行时常量读取返回垃圾值 ②语义标签纠正：0.1f=爆发保护倍率(非"正常倍率")，5.0f=爆发窗口时长(非"时间窗口") ③CalculateServerDamage逻辑描述纠正：爆发窗口内100%穿透，窗口外才应用0.1f/0.5f倍率 ④Harmony日志标签同步修正 |
| v1.2.0 | 2026-07-23 | **Markdown格式输出**: 输出文件改为`伤害常量.md`，表格/标题/列表markdown语法 |
| v1.1.0 | 2026-07-21 | 移除F10冗余快捷键(已有自动导出)；保留F11实时日志开关 |
| v1.0.0 | 2026-07-16 | 初始版本：读取伤害计算常量 |

---

### Jump Space Enemy Health Exporter — 敌人血量导出

当前版本: **v3.1.0** | DLL: `JumpSpaceEnemyHealthExporter_v3.1.0.dll`

导出所有AI_TuningFile的血量/护盾数据，含激活检定(✅当前生效/❌门槽未知)。v3.1.0起输出Markdown格式(`敌人血量.md`)。快捷键: F8 手动重新导出

| 版本 | 日期 | 变动 |
|------|------|------|
| v3.1.0 | 2026-07-23 | **Markdown格式输出**: 输出文件改为`敌人血量.md`，表格/标题/列表markdown语法，激活标记保留 |
| v3.0.0 | 2026-07-22 | **激活检定**: 步战敌人扫描OnFoot_SquadData.m_MinRequiredPlayerCount，飞船扫描AIShipSheet.m_MinPlayerCount(含偏移x58回退)，模糊名称匹配关联AI_TuningFile，输出✅/❌/❓标记；新增ExportSpawnConfiguration生成配置参考表 |
| v2.3.0 | 2026-07-21 | 恢复F8手动重新导出(空战载具需场景中有敌方飞船才能捕获) |
| v2.2.0 | 2026-07-21 | 移除F8冗余快捷键(已有自动导出，场景加载时自动执行) |
| v2.1.0 | 2026-07-19 | 增强导出功能 |
| v1.0.0 | 2026-07-17 | 初始版本：导出敌人血量数据 |

---

### Jump Space Item Editor — 物品编辑器

当前版本: **v3.8.0** | DLL: `JumpSpaceItemEditor_v3.8.0.dll`

控制台交互式修改武器品质/词条/瞄具，模块池可编辑配置文件。四大分类浏览：武器/组件/神器/消费品。神器/消费品支持GUID白名单配置文件。火箭弹纳入消费品"特种"子分类。快捷键: F5 快速加载手持武器

| 版本 | 日期 | 变动 |
|------|------|------|
| v3.8.0 | 2026-07-26 | **模块过滤优化+废案滤除+流派限制标注**: ①恢复AllowedItems白名单/ForbiddenItems黑名单过滤——步战武器用TemplateGuid匹配，飞船组件用ComponentDataGuid匹配 ②废案检测——不在任何流派(School)、不在任何池配置、非基础模块(m_IsBasicModule=false)的模块从编辑器中滤除(23个确认废弃) ③流派限制标注——飞船组件中不可自然生成的模块在名字后追加"（不可自然生成）" ④步战武器过滤链: 池过滤→飞船排除→废案→AllowedItems→ForbiddenItems→自然生成标注 ⑤飞船组件过滤链: ItemType→废案→AllowedItems→ForbiddenItems→自然生成标注 |
| v3.7.0 | 2026-07-25 | **原生生成+日志系统+删除瞄具覆盖**: ①SpawnItem/SpawnComponent改用ItemGenerator.Generate()原生生成(自动流派选择+Allowed/Forbidden过滤+模块权重)，手动Build回退，Dev_ItemEquipper最简回退 ②新增ItemEditorLogger双通道日志(MelonLogger控制台+Mods/ItemEditor_Logs/日期滚动文件，7天自动清理，Exception自动记录完整堆栈) ③删除SpawnItemWithScopeOverride——原生生成已自动选择符合稀有度的瞄具，生成与编辑独立 |
| v3.6.1 | 2026-07-25 | **默认配置文件嵌入**: 新增DefaultConfigEmbed类，将所有配置文件内容嵌入mod，首次运行自动生成UserData/ItemEditor/目录下的9个配置文件(firearm/melee/artifact/consumable/engine/shield/generator/materia/ship_weapon)，新用户无需手动创建 |
| v3.6.0 | 2026-07-25 | **步战武器模块池拆分为枪械+近战**: ①InfantryWeaponPool拆分为FirearmPool(64个)+MeleePool(64个)，通用模块54个两边都显示 ②枪械专属30个(BackloadedBoost/BasicRounds/ExtendedMagazine等)，近战专属10个(AcidRiposte/BreachRiposte/ParryLunge等) ③IsModuleCompatibleWithWeapon新增isMeleeWeapon参数，根据武器类型选择对应池 ④创建firearm_pool.txt和melee_pool.txt配置文件 ⑤WeaponCatalogEntry新增IsMelee属性 |
| v3.5.0 | 2026-07-24 | **火箭弹纳入消费品+物品池配置文件写入**: ①rpg从InfantryWeaponCarryTypes移至ConsumableCarryTypes——火箭弹纳入消费品"特种"子分类(与磁轨炮并列) ②创建artifact_pool.txt(23个神器GUID)和consumable_pool.txt(21个消费品内部名)白名单配置文件 ③消费品GUID使用内部名格式(Pickupable_XXX)，神器GUID使用32位hex格式 |
| v3.4.0 | 2026-07-24 | **神器/消费品配置文件系统**: ①新增ItemPoolConfig——神器/消费品GUID白名单配置文件(UserData/ItemEditor/artifact_pool.txt+consumable_pool.txt) ②白名单模式(文件存在时仅加载列出的物品)vs全量模式(文件不存在时加载全部) ③新增ie reload_pools/ie item_pools命令——热重载和查看物品池状态 ④目录加载后自动过滤神器/消费品 |
| v3.2.1 | 2026-07-24 | **IL2CPP互操作修复**: ①genItem!=null改为(object)genItem!=null——IL2CPP中GeneratedItem从struct变为class，op_Inequality对null右操作数调用Il2CppObjectBaseToPtrNotNull抛nullRef ②m_Modules/m_Cosmetics使用Il2CppReferenceArray<T>构造函数转换 ③m_BaseValueRolls使用Il2CppStructArray<float>构造函数转换 |
| v3.2.0 | 2026-07-24 | **消费品/特殊武器生成**: ①扩展CarryType映射——新增ShieldGenerator/grenade/melee/hullRepairTool等消费品与特殊武器 ②DevEquipper始终作为补充数据源(不再仅作fallback) ③GUID去重避免重复加载 |
| v3.1.0 | 2026-07-24 | **白板修复**: 移除IsBuilderReady/BuilderHasWeaponTemplate错误检查——DevBuildItemAsync通过Addressables异步加载，不查m_WeaponTemplates |
| v3.0.0 | 2026-07-23 | **重大更新**: ①模块池配置文件系统——9个可编辑txt文件替代硬编码过滤，支持热重载(ie reload_modules/ie module_pools) ②瞄具编辑——ie scope命令查看/替换瞄具，仅显示当前稀有度兼容瞄具防止重载丢失 ③ie load直接显示详细信息(跳过ie info) ④ie info显示外观附件(✅标记解雇) ⑤修复生成物品白板bug——m_FoundInChallengeRating从0改为按品质自动设置(Common=1/Rare=3/Epic=5/Legendary=8) |
| v2.0.0 | 2026-07-17 | 重构为控制台交互式编辑器 |
| v1.0.0 | — | 初始版本 |

---

### Jump Space Loot Multiplier Dumper — 战利品乘数导出

当前版本: **v2.1.0** | DLL: `JumpSpaceLootMultiplierDumper_v2.1.0.dll`

导出GlobalLootDataRule乘数表+LootManagerData基础数量表。v2.1.0起输出Markdown格式(`战利品倍率.md`)。快捷键: F9 手动重新导出

| 版本 | 日期 | 变动 |
|------|------|------|
| v2.1.0 | 2026-07-23 | **Markdown格式输出**: 输出文件改为`战利品倍率.md`，表格/标题/列表markdown语法 |
| v2.0.0 | 2026-07-22 | **可读性重构**: 按活动类型分类(Finale/Major/Minor/Safe等)，概览摘要表，◆固定/◇随机标记，权重概率估算(CR1≈0% CR5≈0%)，展开LootBundleContainer内容 |
| v1.0.0 | 2026-07-22 | 初始版本：导出GlobalLootDataRule乘数+LootManagerData基础数量 |

---

### Jump Space Consumable Exporter — 消费品数据导出

当前版本: **v1.3.0** | DLL: `JumpSpaceConsumableExporter_v1.3.0.dll`

导出消费品/部署物数据到Markdown文件。v1.3.0起部署物场景数据支持跨导出调用缓存。v1.2.0起输出中文Markdown格式(`消费品数据.md`)。快捷键: F4 手动重新导出

| 版本 | 日期 | 变动 |
|------|------|------|
| v1.3.0 | 2026-07-24 | **部署物场景数据缓存+名称修正**: ①部署物消耗后仍保留场景数据(实例级Dictionary按名称索引，新数据优先+缓存回退)，标注[缓存数据]来源 ②中文名称修正——医疗针剂→医疗兴奋剂、医疗伙伴→医疗 EM-8、增援部署物→伤害放大器 ③弹匣持持续时间改为"直到充能用完"(无部署动画) |
| v1.2.0 | 2026-07-23 | **Markdown格式输出**: 输出文件改为`消费品数据.md`，表格/标题/列表markdown语法 |
| v1.1.0 | 2026-07-21 | 移除F4冗余快捷键(已有自动导出) |
| v1.0.0 | — | 初始版本 |

---

### Jump Space Module Classifier — 模块近战/枪械分类器

当前版本: **v3.0.0** | DLL: `JumpSpaceModuleClassifier_v3.0.0.dll`

方案A分类器：通过分析步战模块的AllowedItems/ForbiddenItems，将74个步战模块分类为近战专属(MeleeOnly)/枪械专属(RangedOnly)/通用(Universal)。v3.0.0修复近战武器反推机制和分类逻辑。输出`模块分类结果.md`供ModuleExporter读取。快捷键: F8 手动重新扫描

| 版本 | 日期 | 变动 |
|------|------|------|
| v3.0.0 | 2026-07-25 | **分类阈值修正+武器名输出**: ①分类阈值从100%改为>50%(forbidMostMelee=ForbiddenMeleeCount*2>totalMelee)，Breakthrough等禁止4/5近战的模块正确分类为RangedOnly ②ModuleResult新增AllowedMeleeNames/ForbiddenMeleeNames等 ③ExportResults新增详细武器兼容性章节 |
| v2.0.0 | 2026-07-25 | **方案A完善版**: ①近战武器发现——m_WeaponEntriesByGuid只含枪械，从AllowedItems收集非枪械GUID反推近战武器(5个) ②ForbiddenItems含非武器物品(35个GUID仅在Forbidden中出现，是消耗品/Cosmetic等，不影响分类) ③分类逻辑——AllowedItems白名单驱动+ForbiddenItems从forbidAll判专属(None) ④交叉验证通过——MeleeOnly 10/RangedOnly 10/Universal 54/None 0 ⑤输出枪械分组(基础4+附加60)+近战分组(基础4+附加60) |
| v1.0.0 | 2026-07-25 | 初始版本：方案A兼容性矩阵分类 |

**分类逻辑说明**:
- **AllowedItems(白名单)**: 含近战GUID=兼容近战，含枪械GUID=兼容枪械，两者都有=Universal
- **ForbiddenItems(黑名单)**: 仅当禁止全部枪械(forbidMostRanged)→近战专属，仅当禁止全部近战(forbidMostMelee)→枪械专属，同时禁止全部→None
- **两者皆空** = Universal
- 非武器禁止项(消耗品/Cosmetic等GUID)不影响分类

---

### Jump Space Module Exporter — 模块数据导出

当前版本: **v1.18.0** | DLL: `JumpSpaceModuleExporter_v1.18.0.dll`

导出所有模块/武器/组件数据到Markdown文件。v1.15.0起基础模块按武器类型分别收集(枪械基础模块不再出现在近战分组)。v1.14.0起基础模块判定使用BaseModuleSet.m_Modules显式列表。快捷键: F1 飞船导出, F2 特殊武器重新导出

| 版本 | 日期 | 变动 |
|------|------|------|
| v1.18.0 | 2026-07-25 | **近战基础模块过滤修正**: isRangedOnlyBase = rangedBase && !meleeBase，BasicDamage同时存在于rangedBase和meleeBase中→保留在近战分组 |
| v1.17.0 | 2026-07-25 | **基础模块按武器类型分离**: CollectBaseModuleNames改为CollectBaseModuleNamesByType，按PickupableItem_Data_GenericWeapon区分为枪械/近战武器，分别收集基础模块名集合。枪械专属基础模块(BasicMag/BasicReload/BasicTrigger等)不再出现在近战分组 |
| v1.14.0 | 2026-07-25 | **基础模块判定修正**: ①从PickupableItem_Data.m_BaseModuleSet.m_Modules显式列表收集基础模块名集合，替代m_IsBasicModule字段(该字段仅用于UI显示，不影响物品生成逻辑) ②EmpToCorrosion_Ship标注为废案(未被任何模块池引用，已被EmpToDisruption替代) |
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

当前版本: **v3.9.0** | DLL: `JumpSpaceRarityMod_v3.9.0.dll`

修改物品稀有度/品质。v3.9.0起默认权重导出为Markdown格式(`默认权重.md`)。

| 版本 | 日期 | 变动 |
|------|------|------|
| v3.9.0 | 2026-07-23 | **Markdown格式输出**: 默认权重导出改为`默认权重.md`，表格/标题markdown语法 |
| v3.7.0 | 2026-07-12 | 增强稀有度修改功能 |
| v1.0.0 | — | 初始版本 |

---

### Jump Space Status Effect Exporter — 状态效果导出

当前版本: **v1.2.0** | DLL: `JumpSpaceStatusEffectExporter_v1.2.0.dll`

导出所有状态效果的描述与数值到Markdown文件。v1.2.0起输出Markdown格式(`状态效果数据.md`)。

| 版本 | 日期 | 变动 |
|------|------|------|
| v1.2.0 | 2026-07-23 | **Markdown格式输出**: 输出文件改为`状态效果数据.md`，表格/标题/列表markdown语法 |
| v1.1.0 | 2026-07-21 | 移除F9冗余快捷键(已有自动导出) |
| v1.0.0 | 2026-07-15 | 初始版本：状态效果数据导出 |

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
| [`状态效果数据.md`](状态效果数据.md) | Status Effect Exporter | 所有状态效果描述与数值 | — 状态效果计算器

当前版本: **v1.5.0** | DLL: `JumpSpaceStatusEffectCalc_v1.5.0.dll`

导出9个状态效果的TweakableValues并计算实际伤害，含模块覆盖影响章节。v1.5.0起综合ModuleExporter数据，按稀有度输出模块对状态效果参数的覆盖与满级值。v1.4.0起输出Markdown格式(`状态效果算法.md`)。

| 版本 | 日期 | 变动 |
|------|------|------|
| v1.5.0 | 2026-07-23 | **模块覆盖影响**: 综合ModuleExporter数据，新增"模块覆盖影响"章节——12个模块显式(Virus×4/Corrosion×4/Sear×8/Rupture×3/EMP×5)，按效果分组，按稀有度(Common/Uncommon/Rare/Epic)输出覆盖参数+满级值计算(baseValue + perUpgrade × maxLevel) |
| v1.4.0 | 2026-07-23 | **Markdown格式输出**: 输出文件改为`状态效果算法.md`，表格/标题/列表markdown语法 |
| v1.3.0 | 2026-07-21 | 移除F9冗余快捷键(已有自动导出) |
| v1.2.0 | 2026-07-15 | 增强计算功能 |
| v1.0.0 | — | 初始版本 |
