# 権利・利用条件

本パックは、このプロジェクトで作成した自作のNpcPartsDevice1.0.7とCorpseCollector0.3.0を収録します。他作者のMOD、ゲーム本体コード／DLL、デコンパイル資料、抽出画像・モデル・音声、Unity・Spine・BepInEx・HarmonyのDLLは同梱しません。ゲーム名・前提ソフト等の権利は各権利者に帰属します。

ゲームのモデル・アイコン・腹部素材等は、利用者の正規ゲーム内アセットを実行時に参照します。自作の位置補正・部位分類・描画処理は含みますが、抽出ゲーム画像そのものは配布しません。

作者：yukarigohan（NpcPartsDevice v1.0.7）

以下は自作MODに適用する独自の利用条件です。MIT・GPL等のライセンスは適用していません。

- MODの無料利用を許可します。
- 個人利用目的の改造・機能追加を許可します。
- 改造版を改造した本人が使用することを許可します。
- オリジナル版と改造版の無断再配布を禁止します。
- DLL・MOD本体の全部または一部を再配布する場合は、作者yukarigohanの事前許可が必要です。
- 公式配布ページへのリンク共有を許可します。

これらの許諾は自作部分に限ります。ゲーム本体・第三者の素材やコードの権利は各権利者に帰属し、yukarigohanがそれらの権利を所有することを意味しません。

## デバッグ参照情報の例外

配布者の承認により、確定DLLのハッシュを維持するため、DLL内に残るPDB参照のビルド先絶対パスだけを例外として許容しています。これらの参照にはユーザー名を含みません。**PDBファイル本体は同梱しません。** ソース、ログ、セーブ、config、認証情報も同梱しません。

DLLのデバッグ参照を除去するとハッシュが変わるため、このパックではバイナリ編集・再ビルドを行っていません。

---

# Rights and usage terms

This pack contains the project's own NpcPartsDevice1.0.7 and CorpseCollector0.3.0 plugins. It does not bundle third-party mods; game source/binaries or decompiled material; extracted images, models, or audio; or Unity, Spine, BepInEx, or Harmony binaries. Respective owners retain their rights in the game and prerequisites.

Game models, icons, and belly assets are referenced from the user's legitimate game at runtime. Authored placement, region-classification, and rendering code is included; extracted game images themselves are not distributed.

Author: yukarigohan (NpcPartsDevice v1.0.7)

The following custom terms apply to the authored mods. No MIT, GPL, or other standard license is applied.

- Free use of the mods is permitted.
- Modification and feature additions for personal use are permitted.
- The person who makes a modified version may use that version personally.
- Unauthorized redistribution of either original or modified versions is prohibited.
- Redistribution of all or any part of the DLLs or mods requires prior permission from the author, yukarigohan.
- Sharing links to the official distribution page is permitted.

These permissions apply only to the authored portions. Rights in the game and third-party assets or code belong to their respective rights holders; this notice does not claim that yukarigohan owns those rights.

## Debug-reference exception

The distributor explicitly permits only the existing embedded PDB build-path references to remain, preserving the established DLL hashes. Those references do not contain a username. **The actual PDB files are not bundled.** Source files, logs, saves, configurations, and credentials are also excluded.

Removing debug references would change the hashes; no binary editing or rebuilding was performed for this pack.
