# Jump Space Mod 集合

Jump Space (Keepsake Games) 的 MelonLoader mod 集合，基于 IL2CPP 反编译分析开发。

## 部署

将 `Mods/` 目录下带版本号的 DLL 复制到游戏安装目录的 `Mods/` 文件夹。

## Mod 列表与版本历史

---

### JumpSpace More Players — 多人联机突破

当前版本: **v1.3.0** | DLL: `JumpSpaceMorePlayers_v1.3.0.dll`

突破4人联机限制，允许5-16人同时游戏。>4人时所有原版4人上限设计一律回退到4人强度。

| 版本 | 日期 | 变动 |
|------|------|------|
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
- LootDataSheet Prefix (战利品缩放clamp)

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

当前版本: **v2.3.0** | DLL: `JumpSpaceEnemyHealthExporter_v2.3.0.dll`

导出所有AI_TuningFile的血量/护盾数据。快捷键: F8 手动重新导出

| 版本 | 日期 | 变动 |
|------|------|------|
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
