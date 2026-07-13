# テスト（SWE.4 / SWE.6）

A-SPICE の検証プロセスに対応するテスト置き場。

```
04_test/
├── qualification/   # SWE.6 適格性確認テスト（実ブラウザ E2E）
└── unit/            # SWE.4 単体テスト（DOM非依存の純ロジック）
```

## 適格性テスト（例：Playwright + Chromium）

単一ファイルの webapp を実ブラウザで開いて、要求どおり動くか（`QTC-*`）を確認する。
この開発環境では Chromium が `/opt/pw-browsers` にプリインストールされている。

```bash
# 1. playwright-core を用意（初回のみ）
export PLAYWRIGHT_SKIP_BROWSER_DOWNLOAD=1
npm i -D playwright-core

# 2. 実行
node 04_test/qualification/<機能名>.mjs
```

成功したら各 `QTC-*` の結果と Pass 件数を出力し、終了コード 0。
失敗時は終了コード 1（CI で検知できる形にする）。

## 対応表（雛形：機能を追加したら埋める）

| テスト | 検証対象 | 仕様 |
|--------|----------|------|
| （例）`sample.mjs` | （検証する機能） | `02_software/SWE.5-6-integration-qualification-test.md` |

## TODO
- `unit/` に純関数の単体テストを追加（DOM非依存）。
- GitHub Actions で push 時に自動実行（`06_management/SUP.8-9-10-*` 参照）。
