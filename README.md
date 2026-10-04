# CAHE — Course Architecture & Higher Education Tool

シラバス設計支援ツール / Syllabus Design Support Tool

> 改訂版ブルーム・タキソノミーと Fink の Significant Learning タキソノミーに基づいた、
> 大学教員のためのインタラクティブなシラバス作成支援ツール

## Live Demo

🔗 **https://kimikazu.github.io/cahe/**

## Features / 機能

| 機能 | Feature | 説明 |
|------|---------|------|
| 学習目標ジェネレーター | Learning Objectives Generator | Bloom's × Fink's の組み合わせで目標文を自動生成 |
| シラバス構成ビルダー | Syllabus Structure Builder | 8〜16回の授業計画を一覧で構成 |
| 評価・ルーブリック生成 | Assessment & Rubric Generator | 評価方法に応じた4段階ルーブリックを自動生成 |
| 整合性マトリクス | Alignment Matrix | 目標×活動×評価の Constructive Alignment を可視化 |

## Theoretical Foundation / 理論的基盤

- **Revised Bloom's Taxonomy** (Anderson & Krathwohl, 2001) — 6段階の認知プロセス次元
- **Fink's Significant Learning Taxonomy** (Fink, 2003) — 6カテゴリの有意味学習
- **Constructive Alignment** (Biggs, 2003) — 学習目標・教授活動・評価方法の整合性

## Usage / 使い方

### GitHub Pages で直接利用
上記の Live Demo リンクからブラウザで利用できます。

### Google Sites に埋め込み
1. Google Sites で「埋め込み」→「URL を指定」を選択
2. `https://kimikazu.github.io/cahe/` を入力
3. サイズを調整して配置

### ローカルで利用
```bash
git clone https://github.com/kimikazu/cahe.git
open cahe/index.html
```

## Bilingual / 多言語対応

日本語・英語のリアルタイム切替に対応しています。ヘッダーの言語ボタンで切り替えられます。

## Tech Stack

- **Vanilla HTML/CSS/JS** — フレームワーク不要、単一ファイル
- 外部依存なし — オフラインでも動作
- レスポンシブデザイン対応

## License

MIT
