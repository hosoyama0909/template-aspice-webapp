# SWE.2 ソフトウェアアーキテクチャ

`index.html` 内部を論理コンポーネント（SWA）に分け、各 SWR をどのコンポーネントが担うか示す。
単一ファイルでも「関数群のまとまり」を疑似コンポーネントとして扱う。

## コンポーネント一覧

| SWA | 責務 | 担当するSWR |
|-----|------|-------------|
| SWA-UI | 画面描画・入力受付 | SWR-XXX-01, ... |
| SWA-STORE | localStorage 読み書き（`persist()`/`load()`） | SWR-DATA-01 |
| SWA-XXX | （機能ごとのロジック） | SWR-XXX-* |

## データモデル（localStorage）

```js
// キーは「アプリ名:項目」で一意化（衝突防止）
// 例: template-aspice-webapp:db
{
  // items: [...], settings: {...}
}
```

## 設計判断
- （例）状態は単一オブジェクトに集約し `persist()` 一本で保存 → 保存漏れを防ぐため。
