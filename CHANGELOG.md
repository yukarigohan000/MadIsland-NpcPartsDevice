# 更新履歴 / Changelog

## v1.0.11

### 日本語

- 起動時に特定DLLのSHA256完全一致を要求する過剰な制限を撤廃。
- `Assembly.Location` が空の場合に、依存ファイルを取得できず初期化が停止する問題に対応。
- ゲーム本体の登録・保存・復元に必要なAPIの互換性を確認する方式へ変更。
- セーブ保護、複製トランザクション、ロールバックなどの必要な保護は維持。
- BepInEx 5.4.21.0を基準に再ビルドし、5.4.23.5とのAPI互換性も静的検証。
- BepInEx 5.4.23.5の開発用ゲームで実機確認済み。5.4.21.0は静的API互換性確認のみで実機未確認。その他の5.4.xは動作未確認。
- CorpseCollector v0.3.0は変更なし。5.4.21.0ではバージョン警告が残る可能性あり。

### English

- Removed the overly strict startup requirement for specific DLLs to match exact SHA256 hashes.
- Addressed initialization stopping when `Assembly.Location` is empty and the dependency file cannot be accessed.
- Replaced file-hash checks with compatibility checks for the game APIs needed for registration, saving, and restoration.
- Retained save protection, duplication transactions, rollback, and other necessary safeguards.
- Rebuilt against BepInEx 5.4.21.0 and statically checked API compatibility with 5.4.23.5.
- Tested in the development game with BepInEx 5.4.23.5. For 5.4.21.0, only static API compatibility has been checked; it has not been tested in game. Other 5.4.x versions have not been tested.
- CorpseCollector v0.3.0 is unchanged and may still produce a version warning on 5.4.21.0.

## v1.0.10

- ID110・114の部位パーツで、複製アニメーション終了後に完成品が生成されない問題を修正。
- ゲーム標準のデータ復元による人格情報の変更で、複製検証が失敗するケースに対応。
- Fixed body-part duplication for IDs 110 and 114 producing no finished item after the animation.
- Preserved saved personality information when native data restoration would otherwise change it and fail clone validation.

## v1.0.9

- 通常・大型・超大型培養槽の部位パーツ表示を修正。
- 元の部位パーツのサイズ・形状を保持する処理を改善。
- ガラスとの描画前後関係を改善。
- 小型で使用していた正常な補正処理を、対応する部位パーツ展示に共通適用。
- Fixed body-part display in normal, large, and extra-large capsules.
- Improved preservation of the source part's size and shape.
- Improved the depth relationship with capsule glass.
- Reused the working small-capsule corrections for supported body-part displays.

ID16・17の部位展示とID110・114の部位複製はユーザー実機確認済みです。従来の21 ID／12 ID一覧の全機能を再検証したものではありません。CorpseCollector v0.3.0は変更していません。

The user confirmed the part-display fixes for IDs 16/17 and part-duplication fixes for IDs 110/114 in game. This does not revalidate every feature across the previous 21-ID/12-ID lists. CorpseCollector v0.3.0 is unchanged.

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
- Candidate support for registered deceased companions' ordinary belongings/relationships; its strict current-registration requirement was revised in 1.0.3.

## NpcPartsDevice 1.0.1

- NineSlots・Costs・ReviveのSave01限定を、標準スロットと世界の状態を使う共通判定へ変更。標準33枠XMLと既存機能は維持。
- Replace the Save01-only feature gate with native slot/world-session validation, retaining the native 33-slot XML and established features.
- 新規ゲーム・ロード・タイトル復帰の一時状態を管理し、保存先不明・失敗したロード等では停止。
- Manage temporary state across new games, loads, and title transitions; stop on unknown destinations or failed loads.

## NpcPartsDevice 1.0.0

- 本体、Bridge、日本語表示、UI、Skin、Icons、Animation、NineSlots、Costs、Reviveを1DLLへ統合。CorpseCollector0.3.0は独立維持。
- Integrate the core, Bridge, Japanese text, UI, Skin, Icons, Animation, NineSlots, Costs, and Revive into one DLL while keeping CorpseCollector0.3.0 separate.
- 本体GUID・アイテムキー・保存形式を維持。旧個別DLLとの重複読込みを拒否。アイコンは利用者のゲーム内Spriteを実行時参照する方式へ変更。
- Retain the main GUID, item keys, and save format; reject legacy-module duplicates and obtain icon pixels from the user's game at runtime.

## 統合前からの主な機能 / Earlier integrated features

- 人型39 IDの1〜5体蘇生、登録済み死亡仲間の新規ID、妊娠・欠損、ダルマ展示、6種類の固定腹部XY、ID44/144の既存深度補正。
- Revival for 39 humanoid IDs in batches of 1–5, new IDs for revived registered companions, pregnancy/missing limbs, Daruma exhibits, six fixed belly offsets, and existing ID44/144 depth correction.
- 9枠UI、素材コスト、標準結合演出、4サイズ外装・アイコン・サイズ表示。
- Nine-slot UI, material costs, native joining effects, and four-size exterior/icon/size-label support.

## CorpseCollector 0.3.0（本パックで変更なし / unchanged）

- ID5・6・71・113・116・118・121の追加死体回収・再配置と標準保存。人魚死体パネルの食材化で魚肉4個を得る操作。
- Collection/placement/native saving for corpse IDs 5/6/71/113/116/118/121 and the mermaid corpse-panel action yielding four fish-meat items.

過去の履歴は確認できた主要項目の要約です。各機能の現在の制限と確認範囲はREADMEを参照してください。

Historical entries summarize confirmed major changes. See the manuals for current limits and runtime-confirmation scope.
