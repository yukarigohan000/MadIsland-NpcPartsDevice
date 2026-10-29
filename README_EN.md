# Mad Island — NpcPartsDevice

**A mod that adds a "Body Cultivation Capsule" for displaying, duplicating, and reviving NPC corpses and body parts.**

[日本語](README.md) | [Download](https://github.com/yukarigohan000/MadIsland-NpcPartsDevice/releases/latest) | [Changelog](CHANGELOG.md) | [Terms of Use](RIGHTS.md)

**Version:** v1.0.7  
**Author:** yukarigohan

NpcPartsDevice adds a new placeable device, the **Body Cultivation Capsule**, to Mad Island. You can display NPC corpses or body parts inside it and duplicate them using materials. It also offers **Revival Duplication**, which creates a living NPC from an eligible dead NPC.

The included **CorpseCollector** plugin lets you pick up and carry certain NPC corpses that normally cannot be collected as inventory items.

## Features

- **NPC display:** Show corpses and body parts inside a capsule
- **Normal duplication:** Create copies of corpses or body parts using materials
- **Revival duplication:** Generate living NPCs from eligible dead NPCs
- **Corpse collection:** Pick up the corpses of certain NPCs as items
- **Special appearances:** Display supported pregnancy, missing-limb, and limb-removal (“daruma”) states
- **Batch duplication:** Produce 1–5 items or NPCs at a time
- **Four capsule sizes:** Small, normal, large, and extra-large

## 1. Installation

### Requirements

- Windows version of Mad Island
- **BepInEx 5.4.23.5 (BepInEx 5 series)**
- [This mod's release ZIP](https://github.com/yukarigohan000/MadIsland-NpcPartsDevice/releases/latest)

The reference game version is Steam build **25095856**. Compatibility with other game versions, including later game updates, is not guaranteed. This mod is not for BepInEx 6 or IL2CPP.

### Steps

1. Close the game and back up your save data as a precaution.
2. Download the ZIP from [Releases](https://github.com/yukarigohan000/MadIsland-NpcPartsDevice/releases/latest) and extract it.
3. Copy the ZIP's `BepInEx` folder into your game directory, alongside `Mad Island.exe`.
4. Start the game.

Your folders should look like this:

```text
Mad Island/
├─ Mad Island.exe
└─ BepInEx/
   └─ plugins/
      ├─ NpcPartsDevice/
      │  └─ NpcPartsDevice.dll
      └─ CorpseCollector/
         └─ CorpseCollector.dll
```

**Both DLLs are required.** Do not remove `CorpseCollector.dll`, even if you do not plan to use corpse collection. Other mods such as CheatMenu are not required.

**Upgrading from older separate plugins:** Move the old, pre-integration NpcPartsDevice-related DLLs out of the `plugins` directory before installing this package. This includes the old NpcPartsDevice core, Bridge, Ui, Skin, Icons, Animation, NineSlots, Costs, Revive, and ModItemJapanese plugins. Do not load the old plugins together with the integrated version.

## 2. Crafting and placing the capsule

The Body Cultivation Capsule is added to **Cassie's crafting category**. It uses the same crafting category and material recipe as the original **Artificial Human Manufacturing Capsule**. Depending on game progress, the recipe may not yet be available.

| Size | Suggested use |
|---|---|
| Small | Smaller NPCs and body parts |
| Normal | Average-sized NPCs |
| Large | Larger NPCs |
| Extra-large | Very large NPCs |

Craft and place a capsule, then interact with it as you would with other equipment. You can place multiple capsules. A large NPC's model may extend outside a small capsule.

## 3. Using the capsule

Each capsule has **nine visible slots**: one source slot, three material slots, and five output slots.

| Slot | What goes here |
|---|---|
| Source | One eligible NPC corpse or body part |
| Flesh | Flesh used for duplication |
| Milk | Milk used for duplication |
| Life Orb | Orbs required for revival duplication |
| Output ×5 | Items produced through normal duplication |

### Displaying a corpse or body part

1. Open the capsule.
2. Put an eligible corpse or body part in the **Source** slot.
3. The model is displayed inside the capsule.

**Displaying something does not consume duplication materials.**

### Normal duplication

1. Place a corpse or body part in the Source slot.
2. Put the required Flesh and Milk into the material slots.
3. Empty all five output slots.
4. Choose a quantity from **1 to 5**, then press **Duplicate** (「複製」).
5. After the animation finishes, collect the resulting items from the output slots.

The original corpse or body part is not consumed.

### Revival duplication

1. Place an **eligible dead NPC's corpse** in the Source slot. A body part alone cannot be revived.
2. Add Flesh, Milk, and Life Orbs, then empty all five output slots.
3. Select **1 to 5** NPCs and press **Revival Duplication** (「蘇生複製」).
4. After the animation, living NPCs appear near the capsule.

Revived NPCs are separate individuals from the originals. If the original was a deceased companion with a valid registration, the new NPC is registered as a new companion. **NPCs that were not companions do not automatically become companions.** Newly generated NPCs have empty inventories and no equipment.

**Note:** Revival may be refused if the NPC's state, companion registration, or saved data does not meet the requirements. Try using the device outdoors or in another spacious location.

### Required materials

| Action (per item or NPC) | Flesh | Milk | Life Orbs |
|---|---:|---:|---:|
| NPC body-part duplication | 50 | 10 | Not required |
| NPC corpse duplication | 100 | 50 | Not required |
| Revival duplication | 300 | 100 | 10 |

Material costs scale with the quantity selected. For example, duplicating three corpses requires 300 Flesh and 150 Milk. You can also check the required amounts in the in-game interface.

## 4. NPCs confirmed in-game

This table includes **only NPC IDs for which the author has reported successful in-game tests**.

**✅ = Confirmed in-game / — = Not tested (does not necessarily mean unsupported)**

| NPC ID | NPC name | Display | Normal duplication | Revival duplication | Corpse collection |
|---:|---|:---:|:---:|:---:|:---:|
| 5 | Reika (レイカ) | ✅ | ✅ | ✅ | ✅ |
| 6 | Nami (ナミ) | ✅ | ✅ | ✅ | ✅ |
| 9 | Maiden (乙女) | ✅ | ✅ | ✅ | — |
| 10 | Native (原住民) | ✅ | ✅ | ✅ | — |
| 15 | Female Native (女原住民) | ✅ | ✅ | ✅ | — |
| 16 | Native Girl (女の子原住民) | ✅ | ✅ | ✅ | — |
| 17 | Large Female Native (女大柄原住民) | ✅ | ✅ | ✅ | — |
| 44 | Underground Woman (地底の女) | ✅ | ✅ | ✅ | — |
| 71 | Mermaid (人魚) | ✅ | ✅ | ✅ | ✅ |
| 90 | Native Big Sister (姉御原住民) | ✅ | ✅ | ✅ | — |
| 110 | Giant (ジャイアント) | ✅ | ✅ | ✅ | ✅ |
| 113 | Cassie (キャシー) | ✅ | ✅ | ✅ | ✅ |
| 114 | Shino (シノ) | ✅ | ✅ | ✅ | ✅ |
| 115 | Sally (サリー) | ✅ | ✅ | ✅ | ✅ |
| 116 | Mary (メリー) | ✅ | ✅ | ✅ | ✅ |
| 118 | Mira (ミラ) | ✅ | ✅ | ✅ | ✅ |
| 121 | Ent Queen (エントクイーン) | — | — | — | ✅ |
| 140 | Large Native Girl (大柄女の子原住民) | ✅ | ✅ | ✅ | — |
| 142 | Underground Girl (地底の女の子) | ✅ | ✅ | ✅ | — |
| 144 | Daughter (娘) | ✅ | ✅ | ✅ | — |
| 162 | Kana (カナ) | ✅ | ✅ | ✅ | ✅ |
| 163 | Lulu (ルル) | ✅ | ✅ | ✅ | ✅ |

**In-game confirmed: 21 NPC IDs for each of display, normal duplication, and revival duplication; 12 NPC IDs for corpse collection.**

These results confirm that the listed features succeeded for the listed NPC IDs in specific tests. They **do not guarantee every special state**, such as pregnancy or missing limbs, or compatibility after a game update.

NPC names are descriptive translations of the Japanese names and may differ from the official English localization.

## 5. Corpse collection (CorpseCollector)

This plugin allows you to carry certain corpses that normally cannot be picked up as corpse items. See the table above for NPC IDs confirmed in-game.

1. Interact with the dead body of an eligible NPC.
2. Use the carry/collect option in the corpse interaction panel.
3. Keep the collected corpse in your inventory and use it for display or duplication in a compatible capsule.

You need sufficient inventory space. Living or unconscious NPCs cannot be collected as corpses.

### Processing a mermaid corpse into food

Interact with a mermaid corpse lying on the ground and choose the separate **Process into Food** (「食材化」) action to consume the corpse and receive **four pieces of fish meat**. Make room in your inventory first. This is separate from corpse collection.

## 6. Special appearances

For some supported NPCs, the mod can display and duplicate certain pregnancy, missing-limb, or limb-removal (“daruma”) states. Some NPC/state combinations cannot be reproduced or revived.

## 7. Saves and precautions

The capsule uses the game's standard save format. It is designed to handle normal save slots **1–19**, but this does not mean that every slot has been tested in-game.

Before installing, updating, or removing the mod, close the game and **back up your save data and configuration files**. Be especially careful if a capsule contains corpses or materials, or if you have revived NPCs in your save.

If you encounter repeated save/load errors or unusual capsule behavior, avoid repeatedly overwriting the save. Consider restoring a backup instead.

## 8. Frequently asked questions

**Q. Why can't I find the capsule in the crafting menu?**  
Check Cassie's crafting category and whether you meet the requirements for the original Artificial Human Manufacturing Capsule.

**Q. Why can't I put this NPC in the capsule?**  
Check whether the NPC is supported and whether the corpse or body part contains the necessary character data. Even a tested NPC ID may fail in certain special states.

**Q. Why are Duplicate or Revival Duplication unavailable?**  
Check the source item, required materials, all five empty output slots, selected quantity, and—when reviving—the NPC's death state and companion registration.

**Q. Why does a duplicated or revived NPC have no items?**  
This is intentional. Newly generated NPCs do not inherit the original's inventory or equipment.

**Q. Why doesn't the mod load?**  
Check that BepInEx 5 is installed, both DLLs are in the correct folders, and no older separate plugins are loaded alongside the integrated version. A game update may also cause incompatibility.

## 9. Uninstallation

1. Close the game.
2. If possible, remove all corpses, materials, and finished items from your capsules, then back up your save.
3. Move `BepInEx/plugins/NpcPartsDevice` and `BepInEx/plugins/CorpseCollector` out of the `plugins` directory.

Saves containing mod-specific items or generated NPCs may no longer work correctly after removing the mod. Restore a save from before installation if necessary.

## 10. Terms of use

**Author: yukarigohan**

- Free use: **Permitted**
- Modifications and feature additions for personal use: **Permitted**
- Private use of your modified copy: **Permitted**
- Unauthorized redistribution of the original or modified mod: **Prohibited**
- Redistribution requires prior permission from the author
- Sharing links to the official release page: **Permitted**

See [RIGHTS.md](RIGHTS.md) for the full terms. This is an unofficial Mad Island mod. Rights to the game itself and third-party assets or code remain with their respective owners.

---

[Download](https://github.com/yukarigohan000/MadIsland-NpcPartsDevice/releases) | [Changelog](CHANGELOG.md)
