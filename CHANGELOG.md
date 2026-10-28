# 更新履歴 / Changelog

## v1.0.7 Public release documentation

- 作者名yukarigohanと独自利用条件を確定・反映。DLLと機能は変更していません。
- Confirmed author credit (yukarigohan) and custom usage terms. No DLL or functionality changes.

## v1.0.7

- v1.0.7の修正：登録済み死亡仲間のAI種別による蘇生拒否を修正。ID9通常展示の倍率を元NPC基準へ整合し、展示全体のX補正をユーザー確定値−0.100に固定しました。F10開発用調整UIは削除済みです。腹部XY・ダルマ展示・Y/Z深度・素材・保存形式は変更していません。v1.0.7はユーザー実機確認済みです。
- v1.0.7 fixes revival rejection caused by deceased companions' AI types, aligns ordinary ID9 display scale with the source NPC, and fixes its whole-display X offset at the user-confirmed -0.100. The temporary F10 tuning UI has been removed. Belly XY offsets, Daruma display, Y/Z depth, costs, and save formats are unchanged. The user has confirmed v1.0.7 in game.
- NpcPartsDevice 1.0.7 / CorpseCollector 0.3.0.

## 配布パック v1.0.3 / Distribution pack v1.0.3

- 確定済みNpcPartsDevice1.0.3とCorpseCollector0.3.0を2本構成で収録。日本語・英語READMEと権利説明を追加。今回の配布準備でDLLの変更・再ビルドはしていません。
- Packages the established NpcPartsDevice1.0.3 and CorpseCollector0.3.0 binaries, Japanese/English manuals, and rights notes. No binary changes or rebuilds were made for packaging.
- ユーザー実機確認：正規加入したID17の死亡仲間の投入・複製・蘇生・保存復元。全種類・全状態・全セーブ番号の保証はしません。
- User runtime confirmation: insertion, duplication, revival, and save restoration of a normally recruited deceased ID17 companion. Other combinations are not universally certified.

## NpcPartsDevice 1.0.3

- 死体投入・保存の判定を、複製・NPC登録の判定から分離。独立死体データと人間関係の値に不要な元NPC検索を要求しない方式へ変更。
- Separate corpse admission/persistence from clone/registration eligibility; independent corpse data and opaque relationship values no longer require an original-actor lookup.
- 原本のID・荷物・社会関係・妊娠欠損を維持。複製先の社会関係だけを初期化し、独立ID・空荷物の従来方針を維持。
- Retain original identity, belongings, relationships, pregnancy, and limb data; initialize social relationships on independent copies while retaining established ID/empty-inventory behavior.
- 正IDの欠落・競合参照は、標準ロードでのスロット消失・別個体操作を防ぐため拒否。自動的な元NPC補完・再登録は追加しない。
- Refuse missing/conflicting positive-ID native references to prevent slot loss or wrong-actor resolution; no automatic original-NPC repair/re-registration.
- 既存の限定28項目とビルド合格記録を保持。配布作業では再実行していません。
- Existing 28-check/build results are retained; they were not rerun for packaging.

## NpcPartsDevice 1.0.2（未導入候補 / undeployed candidate）

- 登録済み死亡仲間の通常荷物と関係情報に関する互換処理を試作。現在の登録との厳密な照合を要求する設計は1.0.3で見直し。
- Candidate support for registered deceased companions' ordinary belongings/relationships; its strict current-registration requirement was revised in1.0.3.

## NpcPartsDevice 1.0.1

- NineSlots・Costs・ReviveのSave01限定を、標準スロットと世界の状態を使う共通判定へ変更。標準33枠XMLと既存機能は維持。
- Replace the Save01-only feature gate with native slot/world-session validation, retaining the native33-slot XML and established features.
- 新規ゲーム・ロード・タイトル復帰の一時状態を管理し、保存先不明・失敗したロード等では停止。
- Manage temporary state across new games, loads, and title transitions; stop on unknown destinations or failed loads.

## NpcPartsDevice 1.0.0

- 本体、Bridge、日本語表示、UI、Skin、Icons、Animation、NineSlots、Costs、Reviveを1DLLへ統合。CorpseCollector0.3.0は独立維持。
- Integrate the core, Bridge, Japanese text, UI, Skin, Icons, Animation, NineSlots, Costs, and Revive into one DLL while keeping CorpseCollector0.3.0 separate.
- 本体GUID・アイテムキー・保存形式を維持。旧個別DLLとの重複読込みを拒否。アイコンは利用者のゲーム内Spriteを実行時参照する方式へ変更。
- Retain the main GUID, item keys, and save format; reject legacy-module duplicates and obtain icon pixels from the user's game at runtime.

## 統合前からの主な機能 / Earlier integrated features

- 人型39 IDの1〜5体蘇生、登録済み死亡仲間の新規ID、妊娠・欠損、ダルマ展示、6種類の固定腹部XY、ID44/144の既存深度補正。
- Revival for39 humanoid IDs in batches of1–5, new IDs for revived registered companions, pregnancy/missing limbs, Daruma exhibits, six fixed belly offsets, and existing ID44/144 depth correction.
- 9枠UI、素材コスト、標準結合演出、4サイズ外装・アイコン・サイズ表示。
- Nine-slot UI, material costs, native joining effects, and four-size exterior/icon/size-label support.

## CorpseCollector 0.3.0（本パックで変更なし / unchanged）

- ID5・6・71・113・116・118・121の追加死体回収・再配置と標準保存。人魚死体パネルの食材化で魚肉4個を得る操作。
- Collection/placement/native saving for corpse IDs5/6/71/113/116/118/121 and the mermaid corpse-panel action yielding four fish-meat items.

過去の履歴は確認できた主要項目の要約です。各機能の現在の制限と確認範囲はREADMEを参照してください。

Historical entries summarize confirmed major changes. See the manuals for current limits and runtime-confirmation scope.
