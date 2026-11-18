# NpcPartsDevice v1.0.12

## v1.0.12 更新内容

- Mad Island v0.6.0.4 beta / Steam Build 26719145に対応。削除された `GetBloodSlots()` の呼び出し2箇所を `GetLayeredSlots("blood")` に変更しました。
- 開発用ゲームの診断r2で、ユーザーがNPC素体の展示・通常複製・蘇生複製の正常動作を確認しました。NPC ID、サイズ、数量、保存ロードの全組合せを再検証したものではありません。
- 生命のオーブ投入の疑いは数量の問題でした（上限999に対し1000個を投入）。不具合としての変更はありません。
- 限定診断を維持します。数値NPC ID、装置、処理結果、状態・素材数量、ロード済みMODのGUID/版、関連Harmonyパッチ所有者をローカルログに記録します。重複・回数を制限し、NPC名・セーブ内容・所持品一覧は出力しません。例外理由を含むため、ログを共有するときは内容を確認してください。ログは配布しません。
- 配布DLLは診断r2と全メソッドIL・契約を照合した再ビルドです。個人のビルド先パスを除くためハッシュは実機確認版と異なります。機能変更はなく、配布DLL自体の実機再試験は未実施です。起動ログの `diagnostics-r2` / `validation pending` は識別用の既存文言です。
- CorpseCollector v0.3.0は同じDLLを同梱します。両DLLのゲームAPI参照は解決済み。Defeat H Plus・Multiple Birthとの併用は未確認です。旧ゲーム版への後方互換性は保証しません。
- ビルドは0警告・0エラー。API・取引取消等84件＋由来確認3件、展示16件を静的/軽量テストで確認。実Unity上の全NPC・全サイズ・全特殊状態の保証ではありません。

## Changes in v1.0.12

- Updated for Mad Island v0.6.0.4 beta / Steam Build 26719145: replaced two calls to removed `GetBloodSlots()` with `GetLayeredSlots("blood")`.
- The user confirmed NPC corpse display, normal duplication, and revival duplication in the development game using diagnostics-r2. This does not revalidate every NPC ID, size, quantity, or save/load combination.
- The life-orb concern was a quantity issue (1000 versus the stack limit of 999); no orb behavior was changed.
- Retains bounded, deduplicated local diagnostics: numeric NPC IDs, devices, outcomes, state/material counts, loaded mod GUIDs/versions and related Harmony patch owners. NPC names, save contents and inventory lists are not logged. Exception reasons may appear; review logs before sharing. Logs are not bundled.
- The distributed DLL is rebuilt and checked against diagnostics-r2 for identical method IL and contracts. Its hash differs to remove personal build paths. Behavior is unchanged; this exact rebuilt binary has not been retested in game. Existing `diagnostics-r2` / `validation pending` startup wording remains for identification.
- Includes unchanged CorpseCollector v0.3.0. All consumed game API references resolve in both DLLs. Coexistence with Defeat H Plus / Multiple Birth is unverified. Backward compatibility with older game builds is not guaranteed.
- Build: zero warnings/errors; 84 API/transaction checks plus 3 provenance checks and 16 lightweight display checks passed. These are not exhaustive Unity runtime tests.

