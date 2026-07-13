# A-SPICE 適用方針とテーラリング

このリポジトリは、webアプリ開発を **Automotive SPICE（A-SPICE）** のプロセス参照モデルに
沿って進めるための雛形です。学習を目的としているため、本来は自動車の安全系ソフト向けである
A-SPICE を、個人開発の webapp に合わせて **テーラリング（適合）** しています。

複製したら、この文書の「テーラリング」節を新アプリの前提（規模・目的・体制）に合わせて見直してください。

## A-SPICE とは（超要約）

- **プロセス参照モデル（PRM）＋アセスメントモデル（PAM）**。VDA（ドイツ自動車工業会）が
  評価対象を絞った "VDA scope" を定義している。
- 中心は **V字モデル**：左側で「要求→アーキ→設計」と分解し、右側で「単体→結合→適格性」と
  検証していく。左右の各段が対になっている。
- 評価軸は **能力レベル 0〜5**。学習段階では **レベル1（実施している）→ レベル2（管理している）** を目標にする。

### 主要プロセス（VDA scope, v3.1 準拠）と、このリポジトリでの成果物

| ID | プロセス | 成果物 |
|----|----------|--------|
| SYS.1 | 要求抽出 | `01_system/SYS.1-stakeholder-requirements.md` |
| SYS.2 | システム要求分析 | `01_system/SYS.2-system-requirements.md` |
| SYS.3 | システムアーキ設計 | `01_system/SYS.3-system-architecture.md` |
| SWE.1 | ソフトウェア要求分析 | `02_software/SWE.1-software-requirements.md` |
| SWE.2 | ソフトウェアアーキ設計 | `02_software/SWE.2-software-architecture.md` |
| SWE.3 | 詳細設計・実装 | `02_software/SWE.3-detailed-design.md` ＋ `03_implementation/index.html` |
| SWE.4 | ソフトウェア単体検証 | `02_software/SWE.4-unit-verification.md` ＋ `04_test/unit/` |
| SWE.5 | 結合・結合テスト | `02_software/SWE.5-6-integration-qualification-test.md` |
| SWE.6 | ソフトウェア適格性確認テスト | 同上 ＋ `04_test/qualification/` |
| SUP.8 | 構成管理 | `06_management/SUP.8-9-10-supporting-processes.md`（＝Git運用） |
| SUP.9 | 問題解決管理 | 同上（＝Issue/バグ管理） |
| SUP.10 | 変更依頼管理 | 同上（＝Change Request/PR） |
| MAN.3 | プロジェクト管理 | `06_management/MAN.3-project-management.md` |
| MAN.5 | リスク管理 | `06_management/MAN.5-risk-management.md` |

## テーラリング（何を残し、何を省くか）

学習目的・個人開発・非安全という前提で、以下のように適合する。

### 残す（骨格）
- **双方向トレーサビリティ**：STK → SYR → SWR → SWA → SWD → 実装 → テスト を
  ID で相互リンク（`05_traceability/traceability-matrix.md`）。A-SPICE の肝。
- **V字の各段の成果物**：要求・アーキ・設計・検証を文書化。
- **構成管理（SUP.8）**：Git のブランチ運用・タグ・コミット規約で代替。
- **問題管理・変更管理（SUP.9/10）**：GitHub Issue / PR で運用。

### 省く・簡略化する（正式にテーラリングとして記録）
| プロセス | 判断 | 理由 |
|----------|------|------|
| ACQ.* / SPL.* | 除外 | 発注者・供給者関係が無い（一人開発） |
| SYS.4 システム統合 | SW結合に統合 | 単一実行体（HW/複数ECU無し） |
| SUP.1 品質保証（独立監査） | セルフレビューで代替 | 独立したQA組織が無い |
| 能力レベル判定 | 概念のみ | 学習段階。まずはPA1.1達成を目指す |

> テーラリングは「手を抜く」ことではなく、**なぜ省くかを根拠付きで記録する** ことが A-SPICE 的に重要。

## 開発サイクル（このリポジトリでの回し方）

1機能を1イテレーションとし、その中で「要求→アーキ→設計→実装→検証→トレース更新」の
**ミニV字**を回す。詳しくは `README.md`「新機能を追加する手順」と
`06_management/MAN.3-project-management.md` を参照。
