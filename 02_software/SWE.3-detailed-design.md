# SWE.3 詳細設計・実装

各コンポーネント（SWA）の中身を、関数レベル（SWD）で設計する。
実装は `03_implementation/index.html`。コミットには対応する SWR / SWD / CR番号を書く。

## 主要関数（SWD）

| SWD | 関数 | 入力 → 出力 | 対応SWR |
|-----|------|-------------|---------|
| SWD-persist | `persist()` | 状態 → localStorage 書込 | SWR-DATA-01 |
| SWD-load | `load()` | localStorage → 状態復元 | SWR-DATA-01 |
| SWD-xxx | （例）`addItem(x)` | 入力 → items 追加・再描画 | SWR-XXX-01 |

## 擬似コード（必要な関数のみ）

```
addItem(x):
  1. 入力を検証
  2. db.items.push({...})
  3. persist()
  4. render()
```

## 実装メモ
- 純ロジック（計算・整形）は DOM から分離し、`04_test/unit/` で単体テストしやすくする。
