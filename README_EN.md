# Mad Island — NPC Parts Device Complete Pack v1.0.7

[日本語マニュアル](README.md) | [Changelog](CHANGELOG.md) | [Rights and usage terms](RIGHTS.md)

This pack adds cultivation capsules that display and duplicate NPC parts or corpses, and can create living NPC copies from eligible corpses. It contains two plugins: **NpcPartsDevice 1.0.7**, which integrates the device features, and **CorpseCollector 0.3.0**, which adds corpse collection for selected NPCs.

**The user has verified insertion, duplication, revival, and save restoration for a normally recruited, deceased NPC ID17 in v1.0.3. This does not certify every NPC, special state, or save slot.** The author is yukarigohan. See the terms below and RIGHTS.md for use, modification, and redistribution.

v1.0.7 fixes revival rejection caused by deceased companions' AI types, aligns ordinary ID9 display scale with the source NPC, and fixes its whole-display X offset at the user-confirmed -0.100. The temporary F10 tuning UI has been removed. Belly XY offsets, Daruma display, Y/Z depth, costs, and save formats are unchanged. The user has confirmed v1.0.7 in game.

## Download

Download the distribution ZIP from [GitHub Releases](https://github.com/yukarigohan000/MadIsland-NpcPartsDevice/releases/latest).

## Author and usage terms

Author: yukarigohan (NpcPartsDevice v1.0.7)

The following custom terms apply to the authored mods. No MIT, GPL, or other standard license is applied.

- Free use of the mods is permitted.
- Modification and feature additions for personal use are permitted.
- The person who makes a modified version may use that version personally.
- Unauthorized redistribution of either original or modified versions is prohibited.
- Redistribution of all or any part of the DLLs or mods requires prior permission from the author, yukarigohan.
- Sharing links to the official distribution page is permitted.

These permissions apply only to the authored portions. Rights in the game and third-party assets or code belong to their respective rights holders; this notice does not claim that yukarigohan owns those rights.

## 1. Requirements and files

- Windows Mad Island, Unity Mono. Reference environment: Steam build **25095856**, Unity **2021.3.45f2**, **BepInEx 5.4.23.5**.
- A legitimate game installation and compatible BepInEx 5 / Harmony environment are required separately. This is not a BepInEx 6 or IL2CPP build.
- The plugins validate game/dependency compatibility and may stop after a game update or when an incompatible DLL is present.
- No game, Unity, Spine, BepInEx, or Harmony binaries are bundled. No extracted game images, saves, or configuration files are included. CheatMenu is not required.

```text
README.md
README_EN.md
CHANGELOG.md
RIGHTS.md
BepInEx/
  plugins/
    NpcPartsDevice/NpcPartsDevice.dll
    CorpseCollector/CorpseCollector.dll
```

| Plugin | Version | Plugin GUID |
|---|---|---|
| NpcPartsDevice | 1.0.7 | `local.madisland.npcpartsdevice` |
| CorpseCollector | 0.3.0 | `local.madisland.corpsecollector` |

SHA256:

```text
NpcPartsDevice.dll
afc36edd7eaa6d00cc2429eac0da51b11eb7e679ee9a1e492b25697940a020e6

CorpseCollector.dll
f742231867eec39aa7a6fe0cac8af41a21a18544fb2b6902b3fcc5219a667e9b
```

NpcPartsDevice requires the included CorpseCollector even if you do not use its extra corpse types. Internal log messages may retain legacy module names or versions; they do not require separate legacy DLLs.

## 2. Installation and updates

1. Exit the game.
2. Back up all saves, configuration files, and the current related plugins. See the backup instructions below.
3. With BepInEx 5.4.23.5 already installed, extract the archive's `BepInEx` folder into the game folder containing `Mad Island.exe`. Avoid creating an extra nested `plugins` directory.
4. When updating an integrated installation, keep the old main DLL outside `plugins`, then replace it. If CorpseCollector already matches the hash above, it does not need replacing. Do not reset existing configuration files unnecessarily.
5. Start the game manually. Check `BepInEx/LogOutput.log` for `[NpcPartsDevice Integrated] ready 1.0.7` and CorpseCollector loading.
6. First check opening a device, inserting a source, and withdrawing it on a backed-up save. If you see `inactive`, dependency errors, or a save refusal, exit without continuing to overwrite saves.

### Migrating from separate plugins

Move the following old DLLs **outside the entire plugins directory** before installing this pack. Moving them to another subdirectory inside `plugins` does not disable them.

- The old NpcPartsDevice main DLL
- NpcPartsDeviceBridge, ModItemJapanese, NpcPartsDeviceUi
- NpcPartsDeviceSkin, NpcPartsDeviceIcons, NpcPartsDeviceAnimation
- NpcPartsDeviceNineSlots, NpcPartsDeviceCosts, NpcPartsDeviceRevive

Do not run BellyTuner alongside the integrated version; the final offsets are built in. Development/diagnostic plugins and third-party mods that depend on the old plugin GUIDs may also be incompatible. Duplicate legacy modules cause the integrated version to stop.

Existing item keys, the native 33-slot XML format, and legacy configuration filenames are retained. Keep the complete old DLL set and matching saves/configuration for rollback. Do not mix the integrated and separate plugin sets.

## 3. Crafting and placing devices

Four cultivation capsule recipes are added using Cassie's crafting category that contains the standard artificial-human capsule, `capsule_01`. They reuse its material definitions. The source recipe and its normal progression requirements must be available.

| Size | Item key | Icon label |
|---|---|---|
| Small | `parts_duplicator_small_01` | 小 |
| Normal | `parts_duplicator_01` | 普 |
| Large | `parts_duplicator_large_01` | 大 |
| Extra large | `parts_duplicator_xlarge_01` | 超 |

Craft, place, and open the device through normal equipment interaction. Start outdoors with adequate free space. Multiple devices keep separate contents and displays. Large subjects may extend outside the small capsule.

## 4. Nine visible slots

The upper row is **source → flesh → milk → life orb**, left to right. The lower row contains five output slots.

| Purpose | Internal saved slot | Accepted item |
|---|---:|---|
| Source | 0 | One eligible corpse or NPC part |
| Flesh | 1 | `food_flesh_01` |
| Milk | 7 | `food_milk_01` |
| Life orb | 8 | `orb_life_01` |
| Five outputs | 2–6 | Results of ordinary duplication |

Use the native inventory click/drag controls. Some bulk-transfer and scrolling operations are restricted while this device UI is open. The milk and orb slots reject other items.

Nine visible slots still use the **native 33-slot XML storage format**. Do not use internal slots 9–32 as additional free storage. Unexpected legacy contents trigger a withdrawal-only view: recover all displayed contents before continuing. The mod does not silently delete leftovers or repair every historical save generation.

## 5. Duplication, revival, and costs

| Operation, per item/NPC | Flesh | Milk | Life orb | Result |
|---|---:|---:|---:|---|
| NPC part duplication | 50 | 10 | 0 | Device output slot |
| Corpse duplication | 100 | 50 | 0 | Device output slot |
| Revival duplication | 300 | 100 | 10 | Living NPC near the device |

Choose **1–5** copies. Costs scale with the selected quantity: five revivals require 1500 flesh, 500 milk, and 50 orbs. Each dedicated material slot must hold the full required amount; native stack limits still apply. Ordinary duplication never consumes orbs. **The source corpse or part is retained.**

### Steps

1. Insert one eligible source. Revival requires a corpse; a body part alone is not enough.
2. Add materials and empty all five output slots. Revival also requires empty outputs as a safety condition, although living NPCs are not put into those slots.
3. Select quantity 1–5. Use `複製` for ordinary duplication or `蘇生複製` for revival. The UI displays material requirements/shortages. Many added controls remain Japanese; this English manual does not translate the UI.
4. The native joining effect, FX84 and sound143, runs once regardless of quantity. Publication occurs after the native approximately 4.4-second routine. Exact visual-effect completion timing is not guaranteed.
5. Collect ordinary copies from the device; revived NPCs appear nearby.

Materials and results are not published during the effect. Closing the UI, switching devices, starting a save, changing scenes, or invalidating the request cancels without consumption. Repeated clicks are guarded, and conditions are checked again before commit. Batches use all-success/all-cancel behavior. Concurrent effects on multiple devices are not supported.

Some legacy item descriptions still mention 50 flesh. The table above and current operation UI describe the integrated costs.

## 6. Eligible sources and admission limits

Parts are checked against native part/species/corpse definitions. A key beginning with `parts_` is not sufficient by itself. Ordinary corpse duplication and revival have different supported ranges.

Humanoid corpse insertion checks death, item mapping, and data required for native saving. Independent corpse data does not need an original world actor or a matching friend-list entry. Ordinary belongings and relationship records can remain on the original. Admission does not guarantee that the additional duplication/revival conditions will pass.

**Important native-save exception:** corpses with `friendID >= 10` are restored as references to registered NPCs. If that registration is missing or conflicting, native loading can clear the corpse slot or resolve the wrong actor. This mod refuses storage/restoration in that case. It does not rewrite the original ID or invent a missing original NPC.

Living NPCs, malformed required data, unsupported body/save structures, nested NPC/part belongings, and unsupported external apparel/dialogue data are rejected. Other existing corpse types retain their legacy compatibility limits.

## 7. Humanoid revival list

The implementation lists **39 NPC IDs** below. Names are the Japanese reference names; game language and individual names may differ. **Inclusion is not certification of every individual or special state.**

| ID | NPC name (Japanese reference) |
|---:|---|
| 5 | レイカ |
| 6 | ナミ |
| 9 | 乙女 |
| 10 | 原住民 |
| 11 | 大柄原住民 |
| 12 | 小柄原住民 |
| 14 | 男の子原住民 |
| 15 | 女原住民 |
| 16 | 女の子原住民 |
| 17 | 女大柄原住民 |
| 18 | 原住民老爺 |
| 19 | 原住民老婆 |
| 42 | マミー |
| 43 | ダディー |
| 44 | 地底の女 |
| 72 | 太った青年 |
| 73 | 華奢な乙女 |
| 85 | 試作タイプA |
| 86 | 試作タイプB |
| 87 | 試作タイプC |
| 89 | 青年 |
| 90 | 姉御原住民 |
| 91 | 兄御原住民 |
| 110 | ジャイアント |
| 113 | キャシー |
| 114 | シノ |
| 115 | サリー |
| 116 | メリー |
| 118 | ミラ |
| 140 | 大柄女の子原住民 |
| 141 | 大柄男の子原住民 |
| 142 | 地底の女の子 |
| 143 | 地底の男の子 |
| 144 | 娘 |
| 145 | 息子 |
| 162 | カナ |
| 163 | ルル |
| 180 | 大柄青年 |
| 181 | 地底青年 |

Animals, plants, and mermaids are not revival targets. Being collectable through CorpseCollector does not imply revival support.

### Originals and new NPCs

- The original corpse, belongings, equipment, relationships, and original friend registration remain intact.
- Copies are independent. Reviving a registered deceased friend uses the native friend-management path and assigns a different new friendID to each copy.
- Unregistered NPCs retain the supported original faction/AI path; they are not all forcibly made companions. Unverifiable affiliation is rejected.
- New living NPCs start at maximum HP, initially idle, with empty inventory and equipment. Social relationships are initialized separately for the new individual. Pregnancy/father data is handled independently and is not cleared by this policy.
- All 1–5 NPCs and nonoverlapping safe locations are prepared before commit. Search expands when needed; no suitable space means cancellation without material consumption.
- A failed batch cancels its new NPCs/registrations/material changes. If cancellation itself reports an error, do not keep clicking or overwriting saves; use the matching backup.

## 8. Pregnancy, missing limbs, and Daruma displays

Supported pregnancy data includes the father reference/species code and progress value, copied independently. The mod does not reset progress or invent fetal data. Supported left/right arm and leg loss, multiple missing limbs, and corresponding visuals are carried over. Combined pregnancy and missing-limb states are implemented. Fatal neck/torso loss, unresolved father data, and unrestorable body visuals cannot be revived.

Daruma is identified using the native state data, not inferred merely from four missing limbs. Dedicated-model candidates are **9, 14, 15, 16, 17, 44, 90, 140, 142, 143, 144, 145**. Native Daruma-machine models and appearance data are reused. The special display pose applies only inside the capsule; revived NPCs keep missing limbs but use normal AI/movement rather than being fixed to a chair.

The current pregnancy-belly selection uses existing pregnancy data: father information present and progress value0. If a dedicated belly is absent, a compatible milking-machine belly is independently reproduced for the exhibit. IDs9/17/44/140 use that donor path, 142/144 use an independent native belly, and ID15 uses its existing native belly. Face, hair, skin, and body appearance are intended to be retained; not every candidate appearance is certified.

Internal overlap is **breasts → belly → legs**, front to back. ID9's known Mosaic part is removed under limited conditions. ID44 has special-appearance support. IDs44/144 reuse the existing native Head-plane depth alignment to keep the exhibit behind the capsule glass.

Built-in belly offsets, in the established bone-length/scale ratio units:

| ID | X | Y |
|---:|---:|---:|
| 9 | -0.11 | 0.6938 |
| 17 | 0 | 0.5006 |
| 44 | -0.1 | 0.4375 |
| 140 | 0.02 | 0.2628 |
| 142 | 0 | 0 |
| 144 | 0 | 0 |

BellyTuner and its JSON are not required. Only the belly is adjusted, and reinserting a corpse does not accumulate offsets.

## 9. Other integrated features

- **Exterior tint:** all four sizes and multiple instances use top `#17091F`, base `#222A36`, and upper/lower lamps `#7DFF2A`. Tint multiplication does not guarantee exact screen colors. Native glass RGB/alpha and lamp flashing remain unchanged.
- **Icons:** native game sprites are read at runtime, recolored by part, and labeled with the four size characters. Shared source sprites/textures are not overwritten; extracted game images are not distributed.
- **Compatibility helpers:** cover selected extra corpses, ID44's class1 appearance, and clone inventory initialization. ID71 has existing display-depth alignment; normal-size IDs5/71/118 have existing placement corrections.
- **Japanese text:** adds device/extra-corpse names/descriptions in Japanese mode and corrects device-as-body-part labeling. Individual names and item keys are retained. No full English UI translation is added.
- **Special exhibits:** ID110 has an available hair-display selection in supported conditions. It does not change the original/output and is not saved across scenes.
- **Development give button:** disabled by default, unnecessary for normal play, and still restricted to Save01.

## 10. Using CorpseCollector 0.3.0

Additional collection targets are **5 Reika, 6 Nami, 71 Mermaid, 113 Cassie, 116 Merry, 118 Mira/Death girl, and 121 Ent queen**. Item keys are `npc_corpsecollector_<ID>`, one body per slot.

1. Interact normally with the deceased target.
2. Use the native carry action in its corpse interaction panel. Ensure sufficient carrying capacity and inventory space.
3. Use normal NPC-item placement controls to place the collected corpse again. Ordinary belongings, equipment, and individual data follow the native save path.

Living/fainted targets, insufficient capacity, and unsafe nested contents are refused. Dead IDs118/121 have attack/associated processing stopped before collection. The plugin does not kill living NPCs or add collection for every NPC type.

**Mermaid food conversion** is a separate action on the land corpse panel, labeled `食材化`. Empty the corpse's belongings/equipment and reserve space for four fish-meat items. Conversion consumes the corpse and yields four `fish_meat_02`. It is not a T-key action on the inventory item. Collecting plant/mermaid corpses does not add them to the revival list. All seven targets and every food-conversion condition have not been certified in this release's runtime confirmation.

## 11. Saving and backups

Regular slots **1–19** use the game's native slot table; loading native backup slot0 is also implemented. This is not a claim that every slot was tested. Direct external-directory/Workshop loading is unsupported and blocks saving/duplication.

Device contents belong to each world's native Build/Chest data; no new custom save file is introduced. A new game does not inherit the previous loaded slot number. The normal save UI selects the destination. Loading, returning to title, and changing worlds clear pending work and temporary displays. Unknown destinations, failed loads, or failed cleanup block saving.

**With the game closed, copy these together outside the game folder:**

- The entire `Mad Island_Data/StreamingAssets/XML/` directory: keep all slot XML, images, and related files from the same point in time.
- `BepInEx/config/` and the current related DLL set.
- If you use another installation or synchronization setup, confirm the actual active save location. Avoid synchronization overwriting a restored backup.

Registered revived companions use native friend saving. Persistence of unregistered revived NPCs across save/load remains unguaranteed. There is no custom store that recreates deceased/deleted actors automatically. Reviving again from the retained corpse is a new operation with a new material cost.

## 12. Known limits and troubleshooting

- A listed NPC may still fail state, Prefab, pregnancy/limb, or external-reference checks. Revival inside houses has restrictions; use an outdoor location first.
- Missing positive-ID registrations, unsupported nested inventory, and external save extensions are not forcibly repaired. Do not manually rewrite IDs to bypass a refusal.
- Game updates, all third-party mod combinations, and every slot/state combination are not guaranteed. Mods that search for separate legacy plugin GUIDs may be incompatible.
- For loading failures, check duplicate DLLs, BepInEx version, the included CorpseCollector version, and old `General/Enabled=false` settings. Back up configuration before editing it and restart afterward.
- If saving is refused or rollback/display errors persist, stop overwriting saves and restore matching backups. Review personal information and file paths before sharing logs.

This packaging task did not modify code, rebuild plugins, or rerun functionality tests. It checks the established DLL metadata/hashes and archive contents. The v1.0.7 runtime-confirmed case is the ID17 case stated at the top; no additional runtime certification is implied.

## 13. Uninstalling and rolling back

Withdraw device contents first. Do not overwrite a save containing mod-specific devices or corpse keys while the required plugins are absent. Keep a pre-installation save available.

With the game closed, move both DLLs outside `plugins`. Removing DLLs does not automatically remove custom items or spawned NPCs. For rollback, restore the matching old DLLs, configuration, and save set together. If returning to the old separate plugins, do not mix them with the integrated main DLL.

Configuration files may be retained in backup. This pack does not automatically delete old saves or settings.
