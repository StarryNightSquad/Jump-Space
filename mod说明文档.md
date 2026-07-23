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
| v1.5.0 | 2026-07-22 | **1-8P独立战利品倍率**: 每种LootType×5-8P共24个独立配置项(Consumables/Weapons/HeavyWeapons/Materia/Generic)，5-8P Prefix完全接管使用配置总倍率，8P+使用8P值，1-4P原版逻辑不拦截 |
| v1.4.0 | 2026-07-22 | **5P+战利品倍率系统**: 重构AdjustLootTypeAmountsBasedOnGlobalRules为Prefix完全接管(非clamp)，每种LootType一个5P倍率配置，5P+时先算4P基础乘数再叠加配置倍率 |
| v1.3.0 | 2026-07-21 | **战利品缩放修复**: 新增 `LootDataSheet.AdjustLootTypeAmountsBasedOnGlobalRules` Prefix补丁，>4人时payerCount clamp到4，使用4人乘数配置。ISIL验证原方法用payerCount-1索引m_DataMultipliers数组，>4人越界保护跳过乘法导致战利品不缩放 |
| v1.2.1 | 2026-07-21 | **SetEnabledBasedOnPlayerCount关键修复**: m_MaxValue扩展目标从FALLBACK_PLAYER_COUNT(4)改为MaxPlayers.Value(如8)。v1.2.0缺陷：>4人时playerCount>4仍导致SetActiveNetworked(false)禁用任务对象 |
| v1.2.0 | 2026-07-20 | **任务目标修复**: 新增3个补丁——SetEnabledBasedOnPlayerCount.Evaluate() Prefix扩展m_MaxValue；PlayerCountCondition.Evaluate() Prefix改为>=比较；MateriagunInteractionController Postfix日志 |
| v1.1.0 | 2026-07-19 | **>4人数值回退策略**: ISIL验证发现三种>4人行为——struct字段查表(安全)、List索引查表(回退[0])、switch无default(零修饰符)。新增12个playerCount clamp Prefix补丁(10 WaveSpawner + ChallengeRating + ModifierSystem) |
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
| Consumables (消耗品) | 1.25 | 1.50 | 1.75 | 2.00 |
| Weapons (武器) | 1.0 | 1.0 | 1.0 | 1.0 |
| HeavyWeapons (重型武器) | 1.0 | 1.0 | 1.0 | 1.0 |
| Materia (大/小/云材料) | 1.0 | 1.0 | 1.0 | 1.0 |
| Generic (其他) | 1.0 | 1.0 | 1.0 | 1.0 |

- 1-4P: 原版逻辑不拦截
- 5-8P: Prefix接管，使用用户配置的总倍率(非叠加)
- 8P+: 使用8P配置值
- LargeMateria/SmallMateria/MateriaClouds共用Materia组

---

### Jump Space Crisis Dumper — 危机系统数据导出

当前版本: **v1.3.0** | DLL: `JumpSpaceCrisisDumper_v1.3.0.dll`

导出CrisisHandlerSheet中1P-4P各人数配置的DamageControllerData全部字段(27个)。v1.3.0起增加CR级别激活检定(★当前CR激活/✗未激活)。快捷键: F7 手动重新导出

| 版本 | 日期 | 变动 |
|------|------|------|
| v1.3.0 | 2026-07-22 | **CR激活检定**: CR区间列表标记当前GetData激活段(★)，详细数据区每个DCD标记★当前CR激活/✗CR未激活/✗人数未激活，非激活人数组整体标记[✗未激活人数] |
| v1.2.0 | 2026-07-22 | 新增当前玩家数激活检定：GetData返回当前CR区间配置，激活人数列标★，>4P提示使用4P配置 |
| v1.1.0 | 2026-07-22 | 重构输出格式：增加跨人数对比摘要表(低CR/高CR)，详细数据改为分组紧凑布局 |
| v1.0.0 | 2026-07-22 | 初始版本：导出飞船危机系统1-4P配置数据 |

---

### Jump Space ChemicalPayload Fix — 化学弹头修复

当前版本: **v1.0.0** | DLL: `JumpSpaceChemicalPayloadFix_v1.0.0.dll`

修复ValuePerUpgrade符号反了导致升级后触发门槛升高、腐蚀伤害降低的bug。

| 版本 | 日期 | 变动 |
|------|------|------|
| v1.0.0 | 2026-07-09 | 初始版本：修复化学弹头ValuePerUpgrade符号错误 |

---

### Jump Space Damage Constant Reader — 伤害常量读取

当前版本: **v1.1.0** | DLL: `JumpSpaceDamageConstReader_v1.1.0.dll`

读取CalculateServerDamage中的IL2CPP运行时初始化常量值。快捷键: F11 实时日志开关

| 版本 | 日期 | 变动 |
|------|------|------|
| v1.1.0 | 2026-07-21 | 移除F10冗余快捷键(已有自动导出)；保留F11实时日志开关 |
| v1.0.0 | 2026-07-16 | 初始版本：读取伤害计算常量 |

---

### Jump Space Enemy Health Exporter — 敌人血量导出

当前版本: **v3.0.0** | DLL: `JumpSpaceEnemyHealthExporter_v3.0.0.dll`

导出所有AI_TuningFile的血量/护盾数据，含激活检定(★当前生效/✗不生效/⚠门槛未知)。快捷键: F8 手动重新导出

| 版本 | 日期 | 变动 |
|------|------|------|
| v3.0.0 | 2026-07-22 | **激活检定**: 步战敌人扫描OnFoot_SquadData.m_MinRequiredPlayerCount，空战飞船扫描AIShipSheet.m_MinPlayerCount(含偏移0x58回退)，模糊名称匹配关联AI_TuningFile，输出★/✗/⚠标记；新增ExportSpawnConfiguration生成配置参考表 |
| v2.3.0 | 2026-07-21 | 恢复F8手动重新导出(空战载具需场景中有敌方飞船才能捕获) |
| v2.2.0 | 2026-07-21 | 移除F8冗余快捷键(已有自动导出，场景加载时自动执行) |
| v2.1.0 | 2026-07-19 | 增强导出功能 |
| v1.0.0 | 2026-07-17 | 初始版本：导出敌人血量数据 |

---

### Jump Space Item Editor — 物品编辑器

当前版本: **v2.0.0** | DLL: `JumpSpaceItemEditor_v2.0.0.dll`

控制台交互式修改武器品质/词条。快捷键: F5 快速加载手持武器

| 版本 | 日期 | 变动 |
|------|------|------|
| v2.0.0 | 2026-07-17 | 重构为控制台交互式编辑器 |
| v1.0.0 | — | 初始版本 |

---

### Jump Space Loot Multiplier Dumper — 战利品乘数导出

当前版本: **v2.0.0** | DLL: `JumpSpaceLootMultiplierDumper_v2.0.0.dll`

导出GlobalLootDataRule乘数表+LootManagerData基础数量表。v2.0.0起按活动类型分类，含概览摘要+固定/随机标记+概率估算。快捷键: F9 手动重新导出

| 版本 | 日期 | 变动 |
|------|------|------|
| v2.0.0 | 2026-07-22 | **可读性重构**: 按活动类型分类(Finale/Major/Minor/Safe等)，概览摘要表，◆固定/◇随机标记，权重概率估算(CR1≈X% CR5≈X%)，展开LootBundleContainer内容 |
| v1.0.0 | 2026-07-22 | 初始版本：导出GlobalLootDataRule乘数+LootManagerData基础数量 |

---

### Jump Space Module Exporter — 模块数据导出

当前版本: **v1.8.1** | DLL: `JumpSpaceModuleExporter_v1.8.1.dll`

导出所有模块/武器/组件数据到文本文件。快捷键: F1 飞船导出, F2 特殊武器重新导出

| 版本 | 日期 | 变动 |
|------|------|------|
| v1.8.1 | 2026-07-21 | F5→F1/F6→F2(避免与ItemEditor F5冲突) |
| v1.8.0 | 2026-07-21 | F12→F5(避免Steam截图冲突)；恢复F6手动重新导出特殊武器(装备后数据才可用) |
| v1.7.0 | 2026-07-21 | 移除F5冗余快捷键；F6→F12 |
| v1.6.0 | 2026-07-13 | 增强导出功能 |
| v1.0.0 | — | 初始版本 |

---

### Jump Space Rarity Mod — 稀有度修改

当前版本: **v3.7.0** | DLL: `JumpSpaceRarityMod_v3.7.0.dll`

修改物品稀有度/品质。

| 版本 | 日期 | 变动 |
|------|------|------|
| v3.7.0 | 2026-07-12 | 增强稀有度修改功能 |
| v1.0.0 | — | 初始版本 |

---

### Jump Space Status Effect Calculator — 状态效果计算器

当前版本: **v1.3.0** | DLL: `JumpSpaceStatusEffectCalc_v1.3.0.dll`

导出9个状态效果的TweakableValues并计算实际伤害。

| 版本 | 日期 | 变动 |
|------|------|------|
| v1.3.0 | 2026-07-21 | 移除F9冗余快捷键(已有自动导出) |
| v1.2.0 | 2026-07-15 | 增强计算功能 |
| v1.0.0 | — | 初始版本 |

---

### Jump Space Status Effect Exporter — 状态效果导出

当前版本: **v1.1.0** | DLL: `JumpSpaceStatusEffectExporter_v1.1.0.dll`

导出所有状态效果的描述与数值到文本文件。

| 版本 | 日期 | 变动 |
|------|------|------|
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

| 文档 | 说明 |
|------|------|
| [`战利品分配规则.md`](战利品分配规则.md) | 战利品权重系统(CR插值)、概率计算、最大余额法分配算法、数据结构层级 |
| [`组件故障机制参考.md`](组件故障机制参考.md) | 飞船组件故障机制 |
| [`危机系统深度分析.md`](危机系统深度分析.md) | Broken/Critical差异、节流危机算法、伤害点子系统 |
| [`JumpSpace_人数缩放机制分析.md`](JumpSpace_人数缩放机制分析.md) | >4人数值缩放机制分析 |
