# SUP.8 構成管理 / SUP.9 問題解決管理 / SUP.10 変更依頼管理

支援プロセスを、GitHub の機能で運用する。

## SUP.8 構成管理（Git）
- **ブランチ**：`main`（公開）＋ 機能ごとの作業ブランチ。
- **コミットメッセージ**：日本語。対応する要求ID / CR番号を含める（例：`feat: 記録追加 (SWR-XXX-01 / CR #3)`）。
- **タグ**：リリース時に `v0.1.0` のように付け、CHANGELOG と対応させる。
- 生成物（`node_modules` 等）は `.gitignore` で除外。

## SUP.9 問題解決管理（Issue / Bug）
- バグは Issue（`bug_report` テンプレ）で起票し、重大度（S1〜S3）を付ける。
- 影響する要求ID を書き、修正 PR で閉じる。再発防止のテスト（QTC/UTC）を足す。

## SUP.10 変更依頼管理（Change Request / PR）
- 新機能・仕様変更は Issue（`change_request` テンプレ）で CR を起票。
- 影響分析（波及する成果物）を埋めてから着手。PR の Definition of Done で完了確認。

## CI（任意・推奨）
- push 時に適格性テストを自動実行する GitHub Actions を追加すると、回帰を早期に検知できる。
  （`.github/workflows/` に追加。Chromium は環境変数でパス指定）。
