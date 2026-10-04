# CAHE — シラバス設計支援ツール

## プロジェクト概要
改訂版ブルーム・タキソノミーとFinkのSignificant Learningタキソノミーに基づいた、大学教員向けのインタラクティブなシラバス作成支援ツール。Google Sites iframe埋め込みを想定した単一HTMLファイル。

## アーキテクチャ
- **単一ファイル構成**: `index.html` にHTML/CSS/JSをすべてインライン
- **外部依存なし**: CDN・フレームワーク不使用、オフライン動作可能
- **多言語**: `i18n` オブジェクトで日本語/英語を管理、`setLang()` でリアルタイム切替

## 理論的基盤
- **Revised Bloom's Taxonomy** (Anderson & Krathwohl, 2001): 6段階の認知プロセス次元（記憶→理解→応用→分析→評価→創造）
- **Fink's Significant Learning Taxonomy** (Fink, 2003): 基礎的知識、応用、統合、人間の次元、関心、学び方の学習
- **Constructive Alignment** (Biggs, 2003): 学習目標・教授活動・評価方法の三者整合性

## 4つの機能タブ

### 1. 学習目標ジェネレーター (`panel-objectives`)
- Bloomの6段階をクリックで複数選択 → `selectedBlooms[]`
- Finkの6カテゴリを任意選択 → `selectedFinks[]`
- 科目名・トピックを入力し、適切な動詞を使った目標文を自動生成
- 生成結果は `generatedObjectives[]` に保持、整合性マトリクスへ直接追加可能

### 2. シラバス構成ビルダー (`panel-syllabus`)
- 8/10/15/16回の授業計画を一覧で構成
- 各週にトピック（テキスト入力）、教授活動（select）、評価方法（select）を設定
- テキスト形式でエクスポート（クリップボードコピー）

### 3. 評価・ルーブリック生成 (`panel-assessment`)
- 評価方法（レポート/プレゼン/プロジェクト等）×ブルームレベルを選択
- `rubricTemplates` オブジェクトから4段階ルーブリックを自動生成
- レポート・プレゼンテーション・プロジェクトに固有テンプレートあり、他は汎用

### 4. 整合性マトリクス (`panel-alignment`)
- 学習目標を行、Bloom/Fink/教授活動/評価方法を列としたマトリクス
- `alignmentRows[]` で状態管理
- 整合性チェック: 活動・評価が未設定の目標を検出して警告

## 主要なデータ構造
```javascript
bloomLevels[lang]     // 各レベルの id, name, desc, verbs[]
finkCategories[lang]  // 各カテゴリの id, name, desc
rubricTemplates[lang] // 評価方法別の criteria[], levels{4,3,2,1}
alignmentRows[]       // {objective, bloom, fink, activity, assessment}
i18n[lang]            // 全UIテキストの翻訳キー
```

## 今後の拡張候補
- [ ] Bloomの知識次元（事実的/概念的/手続き的/メタ認知的）の追加（現在は認知プロセス次元のみ）
- [ ] 動詞データベースの拡充（各レベル20語以上）
- [ ] CSV/PDFエクスポート機能
- [ ] ルーブリックテンプレートの追加（ディスカッション、ポートフォリオ、ピア評価等に固有テンプレート）
- [ ] 学習目標のABCD形式対応（Audience, Behavior, Condition, Degree）
- [ ] ローカルストレージによるデータ永続化
- [ ] DP（ディプロマ・ポリシー）との対応マッピング機能

## 配布
- GitHub Pages: `https://kimikazu.github.io/cahe/`
- Google Sites 埋め込み: iframe で上記URLを指定
