# template-aspice-webapp

**A-SPICE（Automotive SPICE）の V字モデル**に沿って開発するアプリの雛形。
`template-vanilla-webapp`（単一ファイルの最小スターター）に、要求〜テストを追跡する
**プロセスの骨格**を被せたもの。GitHub の Template repository に指定して複製して使う。

- 実装本体：`03_implementation/index.html`（単一ファイル・サーバ不要・ログイン不要）
- リポジトリ直下の `index.html` は本体への転送ページ
- 公開URL（複製後）：`https://hosoyama0909.github.io/<リポジトリ名>/`

> なぜこの雛形か：`app-familybook` で回している A-SPICE テーラリング運用を、
> 中身を抜いて再利用可能にしたもの。新アプリでも最初から「要求→設計→実装→検証→トレース」を
> たどれる状態で始められる。

## リポジトリ構成（V字の流れ順に採番）

```
.
├── 00_process/          # プロセス定義・テーラリング・用語
├── 01_system/           # SYS.1 要求 → SYS.2 分析 → SYS.3 アーキ
├── 02_software/         # SWE.1 要求 → .2 アーキ → .3 詳細設計 → .4/.5/.6 検証仕様
├── 03_implementation/   # index.html（実装＝配信対象）
├── 04_test/             # SWE.6 適格性テスト / SWE.4 単体
├── 05_traceability/     # トレーサビリティ・マトリクス（中核）
├── 06_management/       # MAN.3/5, SUP.8/9/10
├── .github/             # Issue/PR テンプレ（SUP.9/10）
├── README.md / CHANGELOG.md
```

番号は **V字モデルの読み順**（要求→設計→実装→検証→トレース→管理）に対応。

### V字モデルと成果物の対応

```
 要求・設計（左）                              検証（右）
 01 SYS.1 ステークホルダ要求 ───────────▶ （運用確認）
   01 SYS.2 システム要求 ─────────────▶ 04 SWE.6 適格性テスト
     01 SYS.3 システムアーキ ─────────▶ 04 SWE.5 結合テスト
       02 SWE.1 SW要求 ───────────────▶ 04 SWE.6 適格性テスト
         02 SWE.2 SWアーキ ───────────▶ 04 SWE.5 結合テスト
           02/03 SWE.3 詳細設計・実装 ─▶ 04 SWE.4 単体検証
```

左右は `05_traceability/traceability-matrix.md` で相互リンクする。

## この雛形から新アプリを作る手順

1. GitHub でこのリポジトリの **「Use this template」** から新リポジトリを作成
   （名前は小文字ケバブケース＋プレフィックス。例：`app-baseball`）。
2. `03_implementation/index.html` の中身を書き換えてアプリを作る。
   `localStorage` のキー（`template-aspice-webapp:*`）をアプリ名に合わせて一意にする。
3. `README.md` / `CLAUDE.md` のアプリ名・公開URLを新アプリのものに直す。
4. `main` に push → GitHub Pages（**Deploy from a branch / root**）で公開。
5. ハブ（`hosoyama0909.github.io`）の `index.html` にカードを1枚足してリンク。

## 新機能を追加する手順（1機能＝ミニV字）

1. Issue で変更依頼（CR）を起票（`.github` テンプレ）
2. `01_system` / `02_software` の要求に ID を採番して追記
3. アーキ・詳細設計に反映（SWE.2 / SWE.3）
4. `03_implementation/index.html` を実装（コミットに要求ID / CR番号）
5. `04_test/` で検証
6. トレーサビリティ・マトリクスを更新 → レビュー → merge → タグ

完了条件は `06_management/MAN.3-project-management.md` の Definition of Done を参照。

## 配信（GitHub Pages）

**ブランチ配信（Deploy from a branch / root）** を使う。リポジトリ全体をパスで配信するので、
プロセス文書を同じリポジトリに置いたまま、ルートの転送ページからアプリを開ける。
