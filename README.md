# Jump Space Mod 闆嗗悎

Jump Space (Keepsake Games) 鐨?MelonLoader mod 闆嗗悎锛屽熀浜?IL2CPP 鍙嶇紪璇戝垎鏋愬紑鍙戙€?

## 閮ㄧ讲

灏?`Mods/` 鐩綍涓嬪甫鐗堟湰鍙风殑 DLL 澶嶅埗鍒版父鎴忓畨瑁呯洰褰曠殑 `Mods/` 鏂囦欢澶广€?

## Mod 鍒楄〃涓庣増鏈巻鍙?

---

### JumpSpace More Players 鈥?澶氫汉鑱旀満绐佺牬

褰撳墠鐗堟湰: **v1.5.1** | DLL: `JumpSpaceMorePlayers_v1.5.1.dll`

绐佺牬4浜鸿仈鏈洪檺鍒讹紝鍏佽5-16浜哄悓鏃舵父鎴忋€倂1.5.0璧锋敮鎸?-8P鐙珛鎴樺埄鍝佸€嶇巼閰嶇疆銆?

| 鐗堟湰 | 鏃ユ湡 | 鍙樺姩 |
|------|------|------|
| v1.5.1 | 2026-07-23 | **Harmony琛ヤ竵淇**: `Patch_SetEnabledBasedOnPlayerCount_Evaluate` 鐨?`out int __origMaxVal` / `int __origMinVal` 鍙傛暟浠__`鍓嶇紑琚獺armony瑙嗕负鐗规畩鍙傛暟浣嗘壘涓嶅埌鍖归厤瀵艰嚧IL缂栬瘧閿欒锛屾敼涓洪潤鎬佸瓧娈?`_origMaxVal` / `_origMinVal` 浼犻€掔姸鎬侊紝淇娓告垙瀵瑰眬鍗℃ |
| v1.5.0 | 2026-07-22 | **1-8P鐙珛鎴樺埄鍝佸€嶇巼**: 姣忕LootType脳5-8P鍏?4涓嫭绔嬮厤缃」(Consumables/Weapons/HeavyWeapons/Materia/Generic)锛?-8P Prefix瀹屽叏鎺ョ浣跨敤閰嶇疆鎬诲€嶇巼锛?P+浣跨敤8P鍊硷紝1-4P鍘熺増閫昏緫涓嶆嫤鎴?|
| v1.4.0 | 2026-07-22 | **5P+鎴樺埄鍝佸€嶇巼绯荤粺**: 閲嶆瀯AdjustLootTypeAmountsBasedOnGlobalRules涓篜refix瀹屽叏鎺ョ(闈瀋lamp)锛屾瘡绉峀ootType涓€涓?P鍊嶇巼閰嶇疆锛?P+鏃跺厛绠?P鍩虹涔樻暟鍐嶅彔鍔犻厤缃€嶇巼 |
| v1.3.0 | 2026-07-21 | **鎴樺埄鍝佺缉鏀句慨澶?*: 鏂板 `LootDataSheet.AdjustLootTypeAmountsBasedOnGlobalRules` Prefix琛ヤ竵锛?4浜烘椂payerCount clamp鍒?锛屼娇鐢?浜轰箻鏁伴厤缃€侷SIL楠岃瘉鍘熸柟娉曠敤payerCount-1绱㈠紩m_DataMultipliers鏁扮粍锛?4浜鸿秺鐣屼繚鎶よ烦杩囦箻娉曞鑷存垬鍒╁搧涓嶇缉鏀?|
| v1.2.1 | 2026-07-21 | **SetEnabledBasedOnPlayerCount鍏抽敭淇**: m_MaxValue鎵╁睍鐩爣浠嶧ALLBACK_PLAYER_COUNT(4)鏀逛负MaxPlayers.Value(濡?)銆倂1.2.0缂洪櫡锛?4浜烘椂playerCount>4浠嶅鑷碨etActiveNetworked(false)绂佺敤浠诲姟瀵硅薄 |
| v1.2.0 | 2026-07-20 | **浠诲姟鐩爣淇**: 鏂板3涓ˉ涓佲€斺€擲etEnabledBasedOnPlayerCount.Evaluate() Prefix鎵╁睍m_MaxValue锛汸layerCountCondition.Evaluate() Prefix鏀逛负>=姣旇緝锛汳ateriagunInteractionController Postfix鏃ュ織 |
| v1.1.0 | 2026-07-19 | **>4浜烘暟鍊煎洖閫€绛栫暐**: ISIL楠岃瘉鍙戠幇涓夌>4浜鸿涓衡€斺€攕truct瀛楁鏌ヨ〃(瀹夊叏)銆丩ist绱㈠紩鏌ヨ〃(鍥為€€[0])銆乻witch鏃燿efault(闆朵慨楗扮)銆傛柊澧?2涓猵layerCount clamp Prefix琛ヤ竵(10 WaveSpawner + ChallengeRating + ModifierSystem) |
| v1.0.0 | 2026-07-18 | **鍒濆鐗堟湰**: NetworkManager.Init Postfix淇敼m_MaxPlayers绐佺牬缃戠粶灞?浜轰笂闄?|

**琛ヤ竵娓呭崟 (17涓?**:
- NetworkManager.Init Postfix (缃戠粶灞傜獊鐮?
- 10脳 WaveSpawner Prefix (娉㈡缂╂斁clamp)
- ChallengeRatingBudgetRow Prefix (鎸戞垬璇勭骇棰勭畻clamp)
- PlayerCountModifierComponent Prefix (淇グ绗lamp)
- SetEnabledBasedOnPlayerCount Prefix (浠诲姟鐩爣婵€娲?
- PlayerCountCondition Prefix (浠诲姟鏉′欢鍖归厤)
- MateriagunInteractionController Postfix (鏃ュ織)
- LootDataSheet Prefix (鎴樺埄鍝?-8P鐙珛鍊嶇巼)

**v1.5.0 鎴樺埄鍝佸€嶇巼閰嶇疆 (LootScaling鍒嗙被)**:

| LootType鍒嗙被 | 5P | 6P | 7P | 8P |
|---|---|---|---|---|
| Consumables (娑堣€楀搧) | 1.25 | 1.50 | 1.75 | 2.00 |
| Weapons (姝﹀櫒) | 1.0 | 1.0 | 1.0 | 1.0 |
| HeavyWeapons (閲嶅瀷姝﹀櫒) | 1.0 | 1.0 | 1.0 | 1.0 |
| Materia (澶?灏?浜戞潗鏂? | 1.0 | 1.0 | 1.0 | 1.0 |
| Generic (鍏朵粬) | 1.0 | 1.0 | 1.0 | 1.0 |

- 1-4P: 鍘熺増閫昏緫涓嶆嫤鎴?
- 5-8P: Prefix鎺ョ锛屼娇鐢ㄧ敤鎴烽厤缃殑鎬诲€嶇巼(闈炲彔鍔?
- 8P+: 浣跨敤8P閰嶇疆鍊?
- LargeMateria/SmallMateria/MateriaClouds鍏辩敤Materia缁?

---

### Jump Space Crisis Dumper 鈥?鍗辨満绯荤粺鏁版嵁瀵煎嚭

褰撳墠鐗堟湰: **v1.4.0** | DLL: `JumpSpaceCrisisDumper_v1.4.0.dll`

瀵煎嚭CrisisHandlerSheet涓?P-4P鍚勪汉鏁伴厤缃殑DamageControllerData鍏ㄩ儴瀛楁(27涓?銆倂1.4.0璧疯緭鍑篗arkdown鏍煎紡(`鍗辨満鏁版嵁.md`)銆傚揩鎹烽敭: F7 鎵嬪姩閲嶆柊瀵煎嚭

| 鐗堟湰 | 鏃ユ湡 | 鍙樺姩 |
|------|------|------|
| v1.4.0 | 2026-07-23 | **Markdown鏍煎紡杈撳嚭**: 杈撳嚭鏂囦欢鏀逛负`鍗辨満鏁版嵁.md`锛岃〃鏍?鏍囬/鍒楄〃markdown璇硶锛孋R婵€娲绘爣璁扳槄/鉁椾繚鐣?|
| v1.3.0 | 2026-07-22 | **CR婵€娲绘瀹?*: CR鍖洪棿鍒楄〃鏍囪褰撳墠GetData婵€娲绘(鈽?锛岃缁嗘暟鎹尯姣忎釜DCD鏍囪鈽呭綋鍓岰R婵€娲?鉁桟R鏈縺娲?鉁椾汉鏁版湭婵€娲伙紝闈炴縺娲讳汉鏁扮粍鏁翠綋鏍囪[鉁楁湭婵€娲讳汉鏁癩 |
| v1.2.0 | 2026-07-22 | 鏂板褰撳墠鐜╁鏁版縺娲绘瀹氾細GetData杩斿洖褰撳墠CR鍖洪棿閰嶇疆锛屾縺娲讳汉鏁板垪鏍団槄锛?4P鎻愮ず浣跨敤4P閰嶇疆 |
| v1.1.0 | 2026-07-22 | 閲嶆瀯杈撳嚭鏍煎紡锛氬鍔犺法浜烘暟瀵规瘮鎽樿琛?浣嶤R/楂楥R)锛岃缁嗘暟鎹敼涓哄垎缁勭揣鍑戝竷灞€ |
| v1.0.0 | 2026-07-22 | 鍒濆鐗堟湰锛氬鍑洪鑸瑰嵄鏈虹郴缁?-4P閰嶇疆鏁版嵁 |

---

### Jump Space ChemicalPayload Fix 鈥?鍖栧寮瑰ご淇

褰撳墠鐗堟湰: **v1.1.0** | DLL: `JumpSpaceChemicalPayloadFix_v1.1.0.dll`

淇鍖栧寮瑰ご鎻忚堪涓璂amage Cap涓嶥amage鏄剧ず浣嶇疆棰犲€掔殑闂銆?

**鍘熺増bug**: 鎻忚堪妯℃澘 "閫犳垚 {1} 鐐逛激瀹冲悗...閫犳垚 {0} 鐐逛激瀹? 涓紝`{0}` 鏄犲皠 Damage Cap (ValueIndex=0)锛宍{1}` 鏄犲皠 Damage (ValueIndex=1)锛屽鑷磋涔夐鍊掆€斺€旇厫铓€浼ゅ鏄剧ず鍦ㄨЕ鍙戦槇鍊间綅缃紝瑙﹀彂闃堝€兼樉绀哄湪鑵愯殌浼ゅ浣嶇疆銆?

**淇鏂规**: 浜ゆ崲 `m_ValueIndex` (0鈫?)锛屼娇 `{0}` 鏄犲皠 Damage銆乣{1}` 鏄犲皠 Damage Cap锛屾弿杩拌涔夋纭細"閫犳垚[瑙﹀彂闃堝€糫鐐逛激瀹冲悗...閫犳垚[鑵愯殌浼ゅ]鐐逛激瀹?銆?

| 鐗堟湰 | 鏃ユ湡 | 鍙樺姩 |
|------|------|------|
| v1.1.0 | 2026-07-25 | **淇鎻忚堪椤哄簭**: 浜ゆ崲m_ValueIndex(0鈫?)浣挎弿杩板崰浣嶇鏄犲皠姝ｇ‘锛涚Щ闄1.0.0閿欒缈昏浆ValuePerUpgrade姝ｈ礋鍙风殑閫昏緫 |
| v1.0.0 | 2026-07-09 | 鍒濆鐗堟湰(宸插簾寮?锛氶敊璇炕杞琕aluePerUpgrade姝ｈ礋鍙凤紝鏈В鍐虫弿杩伴『搴忛棶棰?|

---

### Jump Space Damage Constant Reader 鈥?浼ゅ甯搁噺璇诲彇

褰撳墠鐗堟湰: **v1.5.0** | DLL: `JumpSpaceDamageConstReader_v1.5.0.dll`

璇诲彇CalculateServerDamage涓殑IL2CPP杩愯鏃跺垵濮嬪寲甯搁噺鍊笺€倂1.5.0淇Harmony Prefix鍙傛暟绛惧悕(ref鈫抜n)瀵艰嚧鐨凜oreCLR宕╂簝銆傚揩鎹烽敭: F11 瀹炴椂鏃ュ織寮€鍏?

| 鐗堟湰 | 鏃ユ湡 | 鍙樺姩 |
|------|------|------|
| v1.5.0 | 2026-07-25 | **宕╂簝淇**: 鈶燙alculateServerDamage Prefix鍙傛暟绛惧悕`ref DamageInfo`鈫抈in DamageInfo`锛屽尮閰岻L2CPP鍘熷绛惧悕锛岄伩鍏峴truct寮曠敤瀛楁GC涓嶅畨鍏ㄥ鍒跺鑷碈oreCLR Access Violation(0xc0000005) 鈶＄Щ闄_Ship_StateBlackboardData寮曠敤瀛楁璁块棶(BlackboardAuto灞炴€C涓嶅畨鍏? 鈶amageInfo瀛楁璁块棶鍔爐ry-catch淇濇姢 |
| v1.4.0 | 2026-07-24 | **ISIL鈫扲VA鏄犲皠鍋忕Щ淇+浼ゅ閫昏緫绾犳+鏈鏇存柊**: RVA=ISIL_Address-ImageBase+0x22A0锛孭E楠岃瘉5甯搁噺鍏ㄩ儴鍖归厤銆傜籂姝ｄ激瀹抽€昏緫锛氬簲鎬ヤ繚鎶ょ獥鍙ｅ唴90%鍑忎激(闈?00%绌块€?锛岀獥鍙ｅ浣庤閲?0%鍑忎激鎬ユ晳锛屾甯歌閲忓叏棰濅激瀹炽€傛湳璇細鐖嗗彂淇濇姢鈫掑簲鎬ヤ繚鎶わ紝琛€缁嗚優鈫掓牳蹇冪敓鍛藉崟浣?|
| v1.3.0 | 2026-07-24 | **RVA鏄犲皠淇+璇箟绾犳**: 鈶犵Щ闄ら敊璇殑+0x12B0鍋忕Щ锛屾敼鐢≧VA=ISIL_Address-ImageBase(0x180000000)锛屼慨澶嶈繍琛屾椂甯搁噺璇诲彇杩斿洖鍨冨溇鍊?鈶¤涔夋爣绛剧籂姝ｏ細0.1f=鐖嗗彂淇濇姢鍊嶇巼(闈?姝ｅ父鍊嶇巼")锛?.0f=鐖嗗彂绐楀彛鏃堕暱(闈?鏃堕棿绐楀彛") 鈶alculateServerDamage閫昏緫鎻忚堪绾犳锛氱垎鍙戠獥鍙ｅ唴100%绌块€忥紝绐楀彛澶栨墠搴旂敤0.1f/0.5f鍊嶇巼 鈶armony鏃ュ織鏍囩鍚屾淇 |
| v1.2.0 | 2026-07-23 | **Markdown鏍煎紡杈撳嚭**: 杈撳嚭鏂囦欢鏀逛负`浼ゅ甯搁噺.md`锛岃〃鏍?鏍囬/鍒楄〃markdown璇硶 |
| v1.1.0 | 2026-07-21 | 绉婚櫎F10鍐椾綑蹇嵎閿?宸叉湁鑷姩瀵煎嚭)锛涗繚鐣橣11瀹炴椂鏃ュ織寮€鍏?|
| v1.0.0 | 2026-07-16 | 鍒濆鐗堟湰锛氳鍙栦激瀹宠绠楀父閲?|

---

### Jump Space Enemy Health Exporter 鈥?鏁屼汉琛€閲忓鍑?

褰撳墠鐗堟湰: **v3.1.0** | DLL: `JumpSpaceEnemyHealthExporter_v3.1.0.dll`

瀵煎嚭鎵€鏈堿I_TuningFile鐨勮閲?鎶ょ浘鏁版嵁锛屽惈婵€娲绘瀹?鈽呭綋鍓嶇敓鏁?鉁椾笉鐢熸晥/鈿犻棬妲涙湭鐭?銆倂3.1.0璧疯緭鍑篗arkdown鏍煎紡(`鏁屼汉琛€閲?md`)銆傚揩鎹烽敭: F8 鎵嬪姩閲嶆柊瀵煎嚭

| 鐗堟湰 | 鏃ユ湡 | 鍙樺姩 |
|------|------|------|
| v3.1.0 | 2026-07-23 | **Markdown鏍煎紡杈撳嚭**: 杈撳嚭鏂囦欢鏀逛负`鏁屼汉琛€閲?md`锛岃〃鏍?鏍囬/鍒楄〃markdown璇硶锛屾縺娲绘爣璁颁繚鐣?|
| v3.0.0 | 2026-07-22 | **婵€娲绘瀹?*: 姝ユ垬鏁屼汉鎵弿OnFoot_SquadData.m_MinRequiredPlayerCount锛岀┖鎴橀鑸规壂鎻廇IShipSheet.m_MinPlayerCount(鍚亸绉?x58鍥為€€)锛屾ā绯婂悕绉板尮閰嶅叧鑱擜I_TuningFile锛岃緭鍑衡槄/鉁?鈿犳爣璁帮紱鏂板ExportSpawnConfiguration鐢熸垚閰嶇疆鍙傝€冭〃 |
| v2.3.0 | 2026-07-21 | 鎭㈠F8鎵嬪姩閲嶆柊瀵煎嚭(绌烘垬杞藉叿闇€鍦烘櫙涓湁鏁屾柟椋炶埞鎵嶈兘鎹曡幏) |
| v2.2.0 | 2026-07-21 | 绉婚櫎F8鍐椾綑蹇嵎閿?宸叉湁鑷姩瀵煎嚭锛屽満鏅姞杞芥椂鑷姩鎵ц) |
| v2.1.0 | 2026-07-19 | 澧炲己瀵煎嚭鍔熻兘 |
| v1.0.0 | 2026-07-17 | 鍒濆鐗堟湰锛氬鍑烘晫浜鸿閲忔暟鎹?|

---

### Jump Space Item Editor 鈥?鐗╁搧缂栬緫鍣?

褰撳墠鐗堟湰: **v3.8.0** | DLL: `JumpSpaceItemEditor_v3.8.0.dll`

鎺у埗鍙颁氦浜掑紡淇敼姝﹀櫒鍝佽川/璇嶆潯/鐬勫叿锛屾ā鍧楁睜鍙紪杈戦厤缃枃浠躲€傚洓澶у垎绫绘祻瑙堬細姝﹀櫒/缁勪欢/绁炲櫒/娑堣€楀搧銆傜鍣?娑堣€楀搧鏀寔GUID鐧藉悕鍗曢厤缃枃浠躲€傜伀绠瓛褰掑叆娑堣€楀搧"鐗圭"瀛愬垎绫汇€傚揩鎹烽敭: F5 蹇€熷姞杞芥墜鎸佹鍣?

| 鐗堟湰 | 鏃ユ湡 | 鍙樺姩 |
|------|------|------|
| v3.8.0 | 2026-07-26 | **模块过滤优化+废案滤除+流派限制标注**: ①恢复AllowedItems白名单/ForbiddenItems黑名单过滤——步战武器用TemplateGuid匹配，飞船组件用ComponentDataGuid匹配 ②废案检测——不在任何流派(School)、不在任何池配置、非基础模块(m_IsBasicModule=false)的模块从编辑器中滤除(23个确认废弃) ③流派限制标注——飞船组件中不可自然生成的模块在名字后追加"（不可自然生成）" ④步战武器过滤链: 池过滤→飞船排除→废案→AllowedItems→ForbiddenItems→自然生成标注 ⑤飞船组件过滤链: ItemType→废案→AllowedItems→ForbiddenItems→自然生成标注 |
| v3.7.0 | 2026-07-25 | **原生生成+日志系统+删除瞄具覆盖**: ①SpawnItem/SpawnComponent改用ItemGenerator.Generate()原生生成(自动流派选择+Allowed/Forbidden过滤+模块权重)，手动Build回退，Dev_ItemEquipper最简回退 ②新增ItemEditorLogger双通道日志(MelonLogger控制台+Mods/ItemEditor_Logs/日期滚动文件，7天自动清理，Exception自动记录完整堆栈) ③删除SpawnItemWithScopeOverride——原生生成已自动选择符合稀有度的瞄具，生成与编辑独立 |
| v3.6.1 | 2026-07-25 | **默认配置文件嵌入**: 新增DefaultConfigEmbed类，将所有配置文件内容嵌入mod，首次运行自动生成UserData/ItemEditor/目录下的9个配置文件(firearm/melee/artifact/consumable/engine/shield/generator/materia/ship_weapon)，新用户无需手动创建 |
| v3.6.0 | 2026-07-25 | **姝ユ垬姝﹀櫒妯″潡姹犳媶鍒嗕负鏋+杩戞垬**: 鈶營nfantryWeaponPool鎷嗗垎涓篎irearmPool(64涓?+MeleePool(64涓?锛岄€氱敤妯″潡54涓袱杈归兘鏄剧ず 鈶℃灙姊颁笓灞?0涓?BackloadedBoost/BasicRounds/ExtendedMagazine绛?锛岃繎鎴樹笓灞?0涓?AcidRiposte/BreachRiposte/ParryLunge绛? 鈶sModuleCompatibleWithWeapon鏂板isMeleeWeapon鍙傛暟锛屾牴鎹鍣ㄧ被鍨嬮€夋嫨瀵瑰簲姹?鈶ｅ垱寤篺irearm_pool.txt鍜宮elee_pool.txt閰嶇疆鏂囦欢 鈶eaponCatalogEntry鏂板IsMelee灞炴€?|
| v3.5.0 | 2026-07-24 | **鐏绛掑綊鍏ユ秷鑰楀搧+鐗╁搧姹犻厤缃枃浠跺啓鍏?*: 鈶爎pg浠嶪nfantryWeaponCarryTypes绉昏嚦ConsumableCarryTypes鈥斺€旂伀绠瓛褰掑叆娑堣€楀搧"鐗圭"瀛愬垎绫?涓庣杞ㄧ偖骞跺垪) 鈶″垱寤篴rtifact_pool.txt(23涓鍣℅UID)鍜宑onsumable_pool.txt(21涓秷鑰楀搧鍐呴儴鍚?鐧藉悕鍗曢厤缃枃浠?鈶㈡秷鑰楀搧GUID浣跨敤鍐呴儴鍚嶆牸寮?Pickupable_XXX)锛岀鍣℅UID浣跨敤32浣峢ex鏍煎紡 |
| v3.4.0 | 2026-07-24 | **绁炲櫒/娑堣€楀搧閰嶇疆鏂囦欢绯荤粺**: 鈶犳柊澧濱temPoolConfig鈥斺€旂鍣?娑堣€楀搧GUID鐧藉悕鍗曢厤缃枃浠?UserData/ItemEditor/artifact_pool.txt+consumable_pool.txt) 鈶＄櫧鍚嶅崟妯″紡(鏂囦欢瀛樺湪鏃朵粎鍔犺浇鍒楀嚭鐨勭墿鍝?vs鍏ㄩ噺妯″紡(鏂囦欢涓嶅瓨鍦ㄦ椂鍔犺浇鍏ㄩ儴) 鈶㈡柊澧瀒e reload_pools/ie item_pools鍛戒护鈥斺€旂儹閲嶈浇鍜屾煡鐪嬬墿鍝佹睜鐘舵€?鈶ｇ洰褰曞姞杞藉悗鑷姩杩囨护绁炲櫒/娑堣€楀搧 |
| v3.2.1 | 2026-07-24 | **IL2CPP浜掓搷浣滀慨澶?*: 鈶爂enItem!=null鏀逛负(object)genItem!=null鈥斺€擨L2CPP涓璆eneratedItem浠巗truct鍙樹负class锛宱p_Inequality瀵筺ull鍙虫搷浣滄暟璋冪敤Il2CppObjectBaseToPtrNotNull鎶汵ullRef 鈶_Modules/m_Cosmetics浣跨敤Il2CppReferenceArray<T>鏋勯€犲嚱鏁拌浆鎹?鈶_BaseValueRolls浣跨敤Il2CppStructArray<float>鏋勯€犲嚱鏁拌浆鎹?|
| v3.2.0 | 2026-07-24 | **娑堣€楀搧/鐗规畩姝﹀櫒鐢熸垚**: 鈶犳墿灞旵arryType鏄犲皠鈥斺€旀柊澧瀞hieldGenerator/grenade/melee/hullRepairTool绛夋秷鑰楀搧涓庣壒娈婃鍣?鈶evEquipper濮嬬粓浣滀负琛ュ厖鏁版嵁婧?涓嶅啀浠呬綔fallback) 鈶UID鍘婚噸閬垮厤閲嶅鍔犺浇 |
| v3.1.0 | 2026-07-24 | **鐧芥澘淇**: 绉婚櫎IsBuilderReady/BuilderHasWeaponTemplate閿欒妫€鏌モ€斺€擠evBuildItemAsync閫氳繃Addressables寮傛鍔犺浇锛屼笉鏌_WeaponTemplates |
| v3.0.0 | 2026-07-23 | **閲嶅ぇ鏇存柊**: 鈶犳ā鍧楁睜閰嶇疆鏂囦欢绯荤粺鈥斺€?涓彲缂栬緫txt鏂囦欢鏇夸唬纭紪鐮佽繃婊わ紝鏀寔鐑噸杞?ie reload_modules/ie module_pools) 鈶＄瀯鍏风紪杈戔€斺€攊e scope鍛戒护鏌ョ湅/鏇挎崲鐬勫叿锛屼粎鏄剧ず褰撳墠绋€鏈夊害鍏煎鐬勫叿闃叉閲嶈浇涓㈠け 鈶e load鐩存帴鏄剧ず璇︾粏淇℃伅(璺宠繃ie info) 鈶e info鏄剧ず澶栬闄勪欢(鈽呮爣璁扮瀯鍏? 鈶や慨澶嶇敓鎴愮墿鍝佺櫧鏉縝ug鈥斺€攎_FoundInChallengeRating浠?鏀逛负鎸夊搧璐ㄨ嚜鍔ㄨ缃?Common=1/Rare=3/Epic=5/Legendary=8) |
| v2.0.0 | 2026-07-17 | 閲嶆瀯涓烘帶鍒跺彴浜や簰寮忕紪杈戝櫒 |
| v1.0.0 | 鈥?| 鍒濆鐗堟湰 |

---

### Jump Space Loot Multiplier Dumper 鈥?鎴樺埄鍝佷箻鏁板鍑?

褰撳墠鐗堟湰: **v2.1.0** | DLL: `JumpSpaceLootMultiplierDumper_v2.1.0.dll`

瀵煎嚭GlobalLootDataRule涔樻暟琛?LootManagerData鍩虹鏁伴噺琛ㄣ€倂2.1.0璧疯緭鍑篗arkdown鏍煎紡(`鎴樺埄鍝佸€嶇巼.md`)銆傚揩鎹烽敭: F9 鎵嬪姩閲嶆柊瀵煎嚭

| 鐗堟湰 | 鏃ユ湡 | 鍙樺姩 |
|------|------|------|
| v2.1.0 | 2026-07-23 | **Markdown鏍煎紡杈撳嚭**: 杈撳嚭鏂囦欢鏀逛负`鎴樺埄鍝佸€嶇巼.md`锛岃〃鏍?鏍囬/鍒楄〃markdown璇硶 |
| v2.0.0 | 2026-07-22 | **鍙鎬ч噸鏋?*: 鎸夋椿鍔ㄧ被鍨嬪垎绫?Finale/Major/Minor/Safe绛?锛屾瑙堟憳瑕佽〃锛屸梿鍥哄畾/鈼囬殢鏈烘爣璁帮紝鏉冮噸姒傜巼浼扮畻(CR1鈮圶% CR5鈮圶%)锛屽睍寮€LootBundleContainer鍐呭 |
| v1.0.0 | 2026-07-22 | 鍒濆鐗堟湰锛氬鍑篏lobalLootDataRule涔樻暟+LootManagerData鍩虹鏁伴噺 |

---

### Jump Space Consumable Exporter 鈥?娑堣€楀搧鏁版嵁瀵煎嚭

褰撳墠鐗堟湰: **v1.3.0** | DLL: `JumpSpaceConsumableExporter_v1.3.0.dll`

瀵煎嚭娑堣€楀搧/閮ㄧ讲鐗╂暟鎹埌Markdown鏂囦欢銆倂1.3.0璧烽儴缃茬墿鍦烘櫙鏁版嵁鏀寔璺ㄥ鍑鸿皟鐢ㄧ紦瀛樸€倂1.2.0璧疯緭鍑轰腑鏂嘙arkdown鏍煎紡(`娑堣€楀搧鏁版嵁.md`)銆傚揩鎹烽敭: F4 鎵嬪姩閲嶆柊瀵煎嚭

| 鐗堟湰 | 鏃ユ湡 | 鍙樺姩 |
|------|------|------|
| v1.3.0 | 2026-07-24 | **閮ㄧ讲鐗╁満鏅暟鎹紦瀛?鍚嶇О淇**: 鈶犻儴缃茬墿娑堝け鍚庝粛淇濈暀鍦烘櫙鏁版嵁(瀹炰緥绾ictionary鎸夊悕绉扮储寮曪紝鏂伴矞鏁版嵁浼樺厛+缂撳瓨鍥為€€)锛屾爣娉╗缂撳瓨鏁版嵁]鏉ユ簮 鈶′腑鏂囨樉绀哄悕淇鈥斺€斿尰鐤楅拡鍓傗啋鍖荤枟鍏村鍓傘€佸尰鐤椾紮浼粹啋鍖荤枟 EM-8銆佸鐩婇儴缃茬墿鈫掍激瀹虫斁澶у櫒 鈶㈠脊鑽鎸佺画鏃堕棿鏀逛负"鐩村埌鍏呰兘鐢ㄥ畬"(鏃犻儴缃插姩鐢? |
| v1.2.0 | 2026-07-23 | **Markdown鏍煎紡杈撳嚭**: 杈撳嚭鏂囦欢鏀逛负`娑堣€楀搧鏁版嵁.md`锛岃〃鏍?鏍囬/鍒楄〃markdown璇硶 |
| v1.1.0 | 2026-07-21 | 绉婚櫎F4鍐椾綑蹇嵎閿?宸叉湁鑷姩瀵煎嚭) |
| v1.0.0 | 鈥?| 鍒濆鐗堟湰 |

---

### Jump Space Module Classifier 鈥?妯″潡杩戞垬/鏋鍒嗙被鍣?

褰撳墠鐗堟湰: **v3.0.0** | DLL: `JumpSpaceModuleClassifier_v3.0.0.dll`

鏂规A鍒嗙被鍣細閫氳繃鍒嗘瀽姝ユ垬妯″潡鐨凙llowedItems/ForbiddenItems锛屽皢74涓鎴樻ā鍧楀垎绫讳负杩戞垬涓撳睘(MeleeOnly)/鏋涓撳睘(RangedOnly)/閫氱敤(Universal)銆倂3.0.0淇杩戞垬姝﹀櫒鍙嶆帹鏈哄埗鍜屽垎绫婚€昏緫銆傝緭鍑篳妯″潡鍒嗙被缁撴灉.md`渚汳oduleExporter璇诲彇銆傚揩鎹烽敭: F8 鎵嬪姩閲嶆柊鎵弿

| 鐗堟湰 | 鏃ユ湡 | 鍙樺姩 |
|------|------|------|
| v3.0.0 | 2026-07-25 | **分类阈值修正+武器名输出**: ①分类阈值从100%改为>50%(forbidMostMelee=ForbiddenMeleeCount*2>totalMelee)，Breakthrough等禁止4/5近战的模块正确分类为RangedOnly ②ModuleResult新增AllowedMeleeNames/ForbiddenMeleeNames等 ③ExportResults新增详细武器兼容性章节
| v2.0.0 | 2026-07-25 | **鏂规A瀹屽杽鐗?*: 鈶犺繎鎴樻鍣ㄥ彂鐜扳€斺€攎_WeaponEntriesByGuid鍙惈鏋锛屼粠AllowedItems鏀堕泦闈炴灙姊癎UID鍙嶆帹杩戞垬姝﹀櫒(5涓? 鈶orbiddenItems鍚潪姝﹀櫒鐗╁搧(35涓狦UID浠呭湪Forbidden涓嚭鐜帮紝鏄秷鑰楀搧/Cosmetic绛?涓嶅奖鍝嶅垎绫?鈶㈠垎绫婚€昏緫鈥斺€擜llowedItems鐧藉悕鍗曢┍鍔?ForbiddenItems浠協orbidAll鍒や笓灞?None 鈶ｄ氦鍙夐獙璇侀€氳繃鈥斺€擬eleeOnly 10/RangedOnly 10/Universal 54/None 0 鈶よ緭鍑烘灙姊板垎缁?鍩虹4+闄勫姞60)+杩戞垬鍒嗙粍(鍩虹4+闄勫姞60) |
| v1.0.0 | 2026-07-25 | 鍒濆鐗堟湰锛氭柟妗圔鍏煎鎬х煩闃靛垎绫?|

**鍒嗙被閫昏緫璇存槑**:
- **AllowedItems(鐧藉悕鍗?**: 鍚繎鎴楪UID=鍏煎杩戞垬锛屽惈鏋GUID=鍏煎鏋锛屼袱鑰呴兘鏈?Universal
- **ForbiddenItems(榛戝悕鍗?**: 浠呭綋绂佹鍏ㄩ儴鏋(forbidMostRanged)鈫掕繎鎴樹笓灞烇紝浠呭綋绂佹鍏ㄩ儴杩戞垬(forbidMostMelee)鈫掓灙姊颁笓灞烇紝鍚屾椂绂佹鍏ㄩ儴鈫扤one
- **涓よ€呴兘绌?* = Universal
- 闈炴鍣ㄧ姝㈤」(娑堣€楀搧/Cosmetic绛塆UID)涓嶅奖鍝嶅垎绫?

---

### Jump Space Module Exporter 鈥?妯″潡鏁版嵁瀵煎嚭

褰撳墠鐗堟湰: **v1.18.0** | DLL: `JumpSpaceModuleExporter_v1.18.0.dll`

瀵煎嚭鎵€鏈夋ā鍧?姝﹀櫒/缁勪欢鏁版嵁鍒癕arkdown鏂囦欢銆倂1.15.0璧峰熀纭€妯″潡鎸夋鍣ㄧ被鍨嬪垎鍒敹闆嗭紙鏋鍩虹妯″潡涓嶅啀鍑虹幇鍦ㄨ繎鎴樺垎缁勶級銆倂1.14.0璧峰熀纭€妯″潡鍒ゅ畾浣跨敤BaseModuleSet.m_Modules鏄惧紡鍒楄〃銆傚揩鎹烽敭: F1 椋炶埞瀵煎嚭, F2 鐗规畩姝﹀櫒閲嶆柊瀵煎嚭

| 鐗堟湰 | 鏃ユ湡 | 鍙樺姩 |
|------|------|------|
| v1.18.0 | 2026-07-25 | **近战基础模块过滤修正**: isRangedOnlyBase = rangedBase && !meleeBase，BasicDamage同时存在于rangedBase和meleeBase中→保留在近战分组
| v1.17.0 | 2026-07-25 | **鍩虹妯″潡鎸夋鍣ㄧ被鍨嬪垎绂?*: CollectBaseModuleNames鏀逛负CollectBaseModuleNamesByType锛屾寜PickupableItem_Data_GenericWeapon鍖哄垎鏋/杩戞垬姝﹀櫒锛屽垎鍒敹闆嗗熀纭€妯″潡鍚嶉泦鍚堛€傛灙姊颁笓灞炲熀纭€妯″潡(BasicMag/BasicReload/BasicTrigger绛?涓嶅啀鍑虹幇鍦ㄨ繎鎴樺垎缁?|
| v1.14.0 | 2026-07-25 | **鍩虹妯″潡鍒ゅ畾淇**: 鈶犱粠PickupableItem_Data.m_BaseModuleSet.m_Modules鏄惧紡鍒楄〃鏀堕泦鍩虹妯″潡鍚嶉泦鍚堬紝鏇夸唬m_IsBasicModule瀛楁锛堣瀛楁浠呯敤浜嶶I鏄剧ず锛屼笉褰卞搷鐗╁搧鐢熸垚閫昏緫锛夆憽EmpToCorrosion_Ship鏍囨敞涓哄簾妗堬紙鏈浠讳綍妯″潡姹犲紩鐢紝宸茶EmpToDisruption鏇夸唬锛?|
| v1.13.0 | 2026-07-25 | **椋炶埞鍏ㄩ噺瀵煎嚭**: 绛栫暐D3 FindObjectsOfTypeAll濮嬬粓杩愯锛岄亶鍘嗘墍鏈塖hipMoveSettings_Playership璧勪骇+鍚嶇О鍖归厤锛屼竴娆″鍑哄叏閮ㄩ鑸圭Щ鍔ㄥ弬鏁?|
| v1.12.0 | 2026-07-25 | **椋炶埞鏁版嵁缂撳瓨+閲嶅杈撳嚭淇**: 鈶犻鑸圭Щ鍔ㄥ弬鏁拌法瀵煎嚭璋冪敤缂撳瓨绱Н(瀹炰緥绾ictionary鎸塻hipType绱㈠紩锛屾柊椴滄暟鎹紭鍏?缂撳瓨鍥為€€)锛屽垏鎹㈤鑸瑰悗鎸塅1瀵煎嚭鍙疮绉?鑹橀鑸规暟鎹紝缂撳瓨鏁版嵁鏍囨敞"锛堢紦瀛樻暟鎹級" 鈶′慨澶岮ppendMoveSettings 5涓钀藉悇杈撳嚭涓ゆ鐨勯噸澶峛ug 鈶㈡湭鍏宠仈椋炶埞绫诲瀷(-1)浠呭綋缂撳瓨鏃犲凡鍏宠仈绫诲瀷鏃惰緭鍑?|
| v1.11.0 | 2026-07-25 | **鍒嗙被鍒嗙粍瀵煎嚭**: 姝ユ垬姝﹀櫒妯″潡姹犺鍙朇lassifier鍒嗙被缁撴灉(`妯″潡鍒嗙被缁撴灉.md`)锛屾寜鏋鍒嗙粍(鍩虹+闄勫姞)鍜岃繎鎴樺垎缁?鍩虹+闄勫姞)杈撳嚭锛岄€氱敤妯″潡涓よ竟閮芥樉绀猴紝姣忎釜妯″潡鏍囨敞鍒嗙被鏍囩(杩戞垬涓撳睘/鏋涓撳睘/閫氱敤)銆傚垎绫绘枃浠朵笉瀛樺湪鏃跺洖閫€鍘熸牸寮?|
| v1.10.0 | 2026-07-24 | **杩愯鏃舵暟鎹紦瀛?鎵嬫Υ寮圭被鍨嬪尯鍒?*: 鈶犳墜姒村脊/鐏绛掕繍琛屾椂鏁版嵁璺ㄥ鍑鸿皟鐢ㄧ紦瀛樼疮绉?瀹炰緥绾ictionary鎸夊悕绉扮储寮曪紝鏂伴矞鏁版嵁浼樺厛+缂撳瓨鍥為€€) 鈶℃墜姒村脊瀛愮被鍨嬪尯鍒嗏€斺€擯ickupable_TimedGrenade_Data鏄剧ず"鐮寸墖鎵嬫Υ寮?锛孭ickupable_StickyGrenade_Data鏄剧ず"绮樻€ф墜姒村脊" 鈶㈡墜姒村脊鍚堣琛屾樉绀?(鐮寸墖+绮樻€?" |
| v1.9.0 | 2026-07-23 | **Markdown鏍煎紡杈撳嚭**: 6涓緭鍑烘枃浠舵敼涓轰腑鏂噈d锛歚妯″潡鏁版嵁.md`/`缁勪欢鏁版嵁.md`/`姝﹀櫒鏁版嵁.md`/`绁炲櫒鏁版嵁.md`/`鐗规畩姝﹀櫒鏁版嵁.md`/`椋炶埞鏁版嵁.md`锛岃〃鏍?鏍囬/鍒楄〃markdown璇硶 |
| v1.8.1 | 2026-07-21 | F5鈫扚1/F6鈫扚2(閬垮厤涓嶪temEditor F5鍐茬獊) |
| v1.8.0 | 2026-07-21 | F12鈫扚5(閬垮厤Steam鎴浘鍐茬獊)锛涙仮澶岶6鎵嬪姩閲嶆柊瀵煎嚭鐗规畩姝﹀櫒(瑁呭鍚庢暟鎹墠鍙敤) |
| v1.7.0 | 2026-07-21 | 绉婚櫎F5鍐椾綑蹇嵎閿紱F6鈫扚12 |
| v1.6.0 | 2026-07-13 | 澧炲己瀵煎嚭鍔熻兘 |
| v1.0.0 | 鈥?| 鍒濆鐗堟湰 |

---

### Jump Space Rarity Mod 鈥?绋€鏈夊害淇敼

褰撳墠鐗堟湰: **v3.9.0** | DLL: `JumpSpaceRarityMod_v3.9.0.dll`

淇敼鐗╁搧绋€鏈夊害/鍝佽川銆倂3.9.0璧烽粯璁ゆ潈閲嶅鍑轰负Markdown鏍煎紡(`榛樿鏉冮噸.md`)銆?

| 鐗堟湰 | 鏃ユ湡 | 鍙樺姩 |
|------|------|------|
| v3.9.0 | 2026-07-23 | **Markdown鏍煎紡杈撳嚭**: 榛樿鏉冮噸瀵煎嚭鏀逛负`榛樿鏉冮噸.md`锛岃〃鏍?鏍囬markdown璇硶 |
| v3.7.0 | 2026-07-12 | 澧炲己绋€鏈夊害淇敼鍔熻兘 |
| v1.0.0 | 鈥?| 鍒濆鐗堟湰 |

---

### Jump Space Status Effect Calculator 鈥?鐘舵€佹晥鏋滆绠楀櫒

褰撳墠鐗堟湰: **v1.5.0** | DLL: `JumpSpaceStatusEffectCalc_v1.5.0.dll`

瀵煎嚭9涓姸鎬佹晥鏋滅殑TweakableValues骞惰绠楀疄闄呬激瀹筹紝鍚ā鍧楄鐩栧奖鍝嶇珷鑺傘€倂1.5.0璧风患鍚圡oduleExporter鏁版嵁锛屾寜绋€鏈夊害杈撳嚭妯″潡瀵圭姸鎬佹晥鏋滃弬鏁扮殑瑕嗙洊涓庢弧绾у€笺€倂1.4.0璧疯緭鍑篗arkdown鏍煎紡(`鐘舵€佹晥鏋滅畻娉?md`)銆?

| 鐗堟湰 | 鏃ユ湡 | 鍙樺姩 |
|------|------|------|
| v1.5.0 | 2026-07-23 | **妯″潡瑕嗙洊褰卞搷**: 缁煎悎ModuleExporter鏁版嵁锛屾柊澧?妯″潡瑕嗙洊褰卞搷"绔犺妭鈥斺€?2涓ā鍧楁槧灏?Virus脳4/Corrosion脳4/Sear脳8/Rupture脳3/EMP脳5)锛屾寜鏁堟灉鍒嗙粍锛屾寜绋€鏈夊害(Common/Uncommon/Rare/Epic)杈撳嚭瑕嗙洊鍙傛暟+婊＄骇鍊艰绠?baseValue + perUpgrade 脳 maxLevel) |
| v1.4.0 | 2026-07-23 | **Markdown鏍煎紡杈撳嚭**: 杈撳嚭鏂囦欢鏀逛负`鐘舵€佹晥鏋滅畻娉?md`锛岃〃鏍?鏍囬/鍒楄〃markdown璇硶 |
| v1.3.0 | 2026-07-21 | 绉婚櫎F9鍐椾綑蹇嵎閿?宸叉湁鑷姩瀵煎嚭) |
| v1.2.0 | 2026-07-15 | 澧炲己璁＄畻鍔熻兘 |
| v1.0.0 | 鈥?| 鍒濆鐗堟湰 |

---

### Jump Space Status Effect Exporter 鈥?鐘舵€佹晥鏋滃鍑?

褰撳墠鐗堟湰: **v1.2.0** | DLL: `JumpSpaceStatusEffectExporter_v1.2.0.dll`

瀵煎嚭鎵€鏈夌姸鎬佹晥鏋滅殑鎻忚堪涓庢暟鍊煎埌Markdown鏂囦欢銆倂1.2.0璧疯緭鍑篗arkdown鏍煎紡(`鐘舵€佹晥鏋滄暟鎹?md`)銆?

| 鐗堟湰 | 鏃ユ湡 | 鍙樺姩 |
|------|------|------|
| v1.2.0 | 2026-07-23 | **Markdown鏍煎紡杈撳嚭**: 杈撳嚭鏂囦欢鏀逛负`鐘舵€佹晥鏋滄暟鎹?md`锛岃〃鏍?鏍囬/鍒楄〃markdown璇硶 |
| v1.1.0 | 2026-07-21 | 绉婚櫎F9鍐椾綑蹇嵎閿?宸叉湁鑷姩瀵煎嚭) |
| v1.0.0 | 2026-07-15 | 鍒濆鐗堟湰锛氱姸鎬佹晥鏋滄暟鎹鍑?|

---

## 鎶€鏈爤

- **妗嗘灦**: MelonLoader + Il2CppInterop + HarmonyX
- **娓告垙寮曟搸**: Unity IL2CPP (Netcode for GameObjects)
- **鍙嶇紪璇戝伐鍏烽摼**: Cpp2IL 鈫?ISIL/DiffableCs
- **鐩爣杩愯鏃?*: .NET 6.0

---

## 鍙傝€冩枃妗?

### 鍒嗘瀽鏂囨。

| 鏂囨。 | 璇存槑 |
|------|------|
| [`鎴樺埄鍝佸垎閰嶈鍒?md`](鎴樺埄鍝佸垎閰嶈鍒?md) | 鎴樺埄鍝佹潈閲嶇郴缁?CR鎻掑€?銆佹鐜囪绠椼€佹渶澶т綑棰濇硶鍒嗛厤绠楁硶銆佹暟鎹粨鏋勫眰绾?|
| [`缁勪欢鏁呴殰鏈哄埗鍙傝€?md`](缁勪欢鏁呴殰鏈哄埗鍙傝€?md) | 椋炶埞缁勪欢鏁呴殰鏈哄埗 |
| [`鍗辨満绯荤粺娣卞害鍒嗘瀽.md`](鍗辨満绯荤粺娣卞害鍒嗘瀽.md) | Broken/Critical宸紓銆佽妭娴佸嵄鏈虹畻娉曘€佷激瀹崇偣瀛愮郴缁?|
| [`浜烘暟缂╂斁鏈哄埗鍒嗘瀽.md`](浜烘暟缂╂斁鏈哄埗鍒嗘瀽.md) | >4浜烘暟鍊肩缉鏀炬満鍒跺垎鏋?|

### Mod杩愯鏃跺鍑?(Markdown)

| 鏂囨。 | 鏉ユ簮Mod | 璇存槑 |
|------|---------|------|
| [`榛樿鏉冮噸.md`](榛樿鏉冮噸.md) | Rarity Mod | 鐗╁搧绋€鏈夊害CR鏉冮噸琛?|
| [`鎴樺埄鍝佸€嶇巼.md`](鎴樺埄鍝佸€嶇巼.md) | Loot Multiplier Dumper | 鎴樺埄鍝佷箻鏁颁笌鍩虹鏁伴噺 |
| [`鍗辨満鏁版嵁.md`](鍗辨満鏁版嵁.md) | Crisis Dumper | 椋炶埞鍗辨満绯荤粺1-4P閰嶇疆 |
| [`浼ゅ甯搁噺.md`](浼ゅ甯搁噺.md) | Damage Constant Reader | IL2CPP杩愯鏃朵激瀹冲父閲?|
| [`鏁屼汉琛€閲?md`](鏁屼汉琛€閲?md) | Enemy Health Exporter | 鏁屼汉琛€閲?鎶ょ浘/婵€娲绘瀹?|
| [`妯″潡鏁版嵁.md`](妯″潡鏁版嵁.md) | Module Exporter | 妯″潡鎸夋睜鍒嗙粍鏁版嵁(姝ユ垬姝﹀櫒姹犲惈鏋/杩戞垬鍒嗙粍) |
| [`妯″潡鍒嗙被缁撴灉.md`](妯″潡鍒嗙被缁撴灉.md) | Module Classifier | 姝ユ垬妯″潡杩戞垬/鏋鍒嗙被缁撴灉 |
| [`缁勪欢鏁版嵁.md`](缁勪欢鏁版嵁.md) | Module Exporter | 缁勪欢鎸夌被鍨嬪垎绫绘暟鎹?|
| [`姝﹀櫒鏁版嵁.md`](姝﹀櫒鏁版嵁.md) | Module Exporter | 姝ユ垬姝﹀櫒瀹屾暣灞炴€?|
| [`绁炲櫒鏁版嵁.md`](绁炲櫒鏁版嵁.md) | Module Exporter | 绁炲櫒鎸夌█鏈夊害鏁堟灉鍙傛暟 |
| [`娑堣€楀搧鏁版嵁.md`](娑堣€楀搧鏁版嵁.md) | Consumable Exporter | 娑堣€楀搧/閮ㄧ讲鐗╂暟鎹?|
| [`鐗规畩姝﹀櫒鏁版嵁.md`](鐗规畩姝﹀櫒鏁版嵁.md) | Module Exporter | 纾佽建鐐?鐏绛?鎵嬫Υ寮?杩戞垬/Materia鏋?|
| [`椋炶埞鏁版嵁.md`](椋炶埞鏁版嵁.md) | Module Exporter | 椋炶埞钃濆浘灞炴€?绉诲姩鍙傛暟 |
| [`鐘舵€佹晥鏋滅畻娉?md`](鐘舵€佹晥鏋滅畻娉?md) | Status Effect Calc | 9涓姸鎬佹晥鏋淭weakableValues涓庝激瀹宠绠?|
| [`鐘舵€佹晥鏋滄暟鎹?md`](鐘舵€佹晥鏋滄暟鎹?md) | Status Effect Exporter | 鎵€鏈夌姸鎬佹晥鏋滄弿杩颁笌鏁板€?|


