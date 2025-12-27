# 📊 Portfolio X-Ray

**XIRR（内部収益率）と資産配分を可視化する高度な投資分析ダッシュボード**

楽天証券のCSVファイルを読み込むだけで、プロフェッショナルな投資分析レポートを自動生成するシングルページアプリケーション（SPA）です。

![Portfolio X-Ray](https://img.shields.io/badge/version-1.0.0-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![JavaScript](https://img.shields.io/badge/JavaScript-Vanilla-yellow.svg)

---

## ✨ 主な機能

### 📈 高度な財務分析
- **XIRR計算**: Newton-Raphson法による正確な内部収益率の算出
- **リアルタイムシミュレーション**: 現在価格を編集してXIRRを即座に再計算
- **資産クラス分析**: 株式・債券・REIT・コモディティの自動分類
- **戦略分析**: Core（長期）とSatellite（短期）の投資スタイル判定

### 📊 9種類の可視化チャート
1. **Portfolio XIRR Gauge** - 半円ゲージでポートフォリオ全体のIRRを表示
2. **資産クラス別構成比** - ドーナツチャート
3. **Core vs Satellite比率** - 80:20ルールの確認
4. **資産クラス別XIRR** - 横棒グラフ
5. **月次投資額推移** - 積み上げ棒グラフ
6. **資産クラス別確定損益** - 棒グラフ
7. **XIRR上位5銘柄** - 横棒グラフ
8. **投資スタイル累積構成比推移** - 積み上げエリアチャート
9. **保有期間 vs リターン** - 散布図

### 🤖 AI分析レポート
- Google Gemini 2.5 Flash統合
- ポートフォリオの健全性診断
- パフォーマンス評価
- リバランス提案

### 📥 データインポート
- **楽天証券CSV対応**:
  - 米国株取引履歴
  - 日本株取引履歴
  - 投資信託取引履歴
  - 資産残高ファイル
- **複数ファイル同時読み込み**
- **自動価格更新**: 残高ファイルから現在価格を自動取得

### 📤 エクスポート機能
- **PDF出力**: html2canvas + jsPDFによるレポート生成
- **JSON出力**: データのバックアップ・共有用（※実装予定）

---

## 🚀 クイックスタート

### 必要なもの
- モダンなWebブラウザ（Chrome、Firefox、Safari、Edge）
- 楽天証券からダウンロードしたCSVファイル

### 使い方

1. **ファイルをダウンロード**
   ```bash
   git clone https://github.com/yourusername/Rakuten-trade-portfolio-X-ray-SPA.git
   cd Rakuten-trade-portfolio-X-ray-SPA
   ```

2. **index.htmlをブラウザで開く**
   ```bash
   # macOS
   open index.html
   
   # Windows
   start index.html
   
   # Linux
   xdg-open index.html
   ```

3. **CSVファイルをアップロード**
   - スプラッシュ画面で「ファイルを選択」ボタンをクリック
   - 楽天証券からダウンロードしたCSVファイルを選択（複数可）
   - 自動的に解析が開始されます

4. **レポートを確認**
   - ダッシュボードが表示されます
   - 各種チャートとKPIを確認
   - AI分析レポートを読む
   - 必要に応じてPDFエクスポート

---

## 📁 プロジェクト構成

```
Rakuten-trade-portfolio-X-ray-SPA/
├── index.html          # メインアプリケーション（全機能を含む単一ファイル）
└── README.md           # このファイル
```

**シングルファイルアーキテクチャ**: 
すべてのHTML、CSS、JavaScriptが1つのファイルに統合されており、デプロイが簡単です。

---

## 🔧 技術スタック

### フロントエンド
- **Vanilla JavaScript** - フレームワークなしの純粋なJS
- **Tailwind CSS** - ユーティリティファーストCSSフレームワーク
- **Chart.js** - データ可視化ライブラリ
- **PapaParse** - CSV解析エンジン

### PDF生成
- **jsPDF** - PDFドキュメント生成
- **html2canvas** - HTML→Canvas変換

### UI/UX
- **Lucide Icons** - モダンなアイコンセット
- **Inter & Noto Sans JP** - 日英対応フォント

### AI
- **Google Gemini 2.5 Flash** - AI分析エンジン

---

## 📖 使用例

### 楽天証券CSVファイルの準備

#### 1. 取引履歴のダウンロード
楽天証券にログイン → 各種履歴 → 取引履歴 → CSVダウンロード

**対応ファイル形式**:
- 米国株取引履歴（ティッカー、数量［株］、受渡金額［円］を含む）
- 日本株取引履歴（銘柄コード、数量［株］、受渡金額［円］を含む）
- 投資信託取引履歴（ファンド名、数量［口］、受渡金額［円］を含む）

#### 2. 資産残高のダウンロード
楽天証券にログイン → 保有商品一覧 → CSVダウンロード

**重要**: 資産残高ファイルを含めることで、現在価格が自動更新されます！

### データの読み込み
- 複数のCSVファイルを一度に選択可能
- 取引履歴と資産残高を同時にアップロードすると自動でマージされます
- ファイル形式は自動判別されます

---

## ⚙️ 設定とカスタマイズ

### API キーの設定（AI機能を使う場合）

AI分析機能を有効にするには、Google Gemini APIキーが必要です。

1. [Google AI Studio](https://makersuite.google.com/app/apikey)でAPIキーを取得
2. `index.html`の398行目を編集:
   ```javascript
   const apiKey = "YOUR_API_KEY_HERE";
   ```

⚠️ **セキュリティ注意**: 本番環境では環境変数やバックエンドプロキシを使用してください。

### 銘柄名マッピングのカスタマイズ

投資信託の名称を統一するには、`NAME_MAPPINGS`を編集します（401-404行目）:

```javascript
const NAME_MAPPINGS = {
    "元の名前": "統一後の名前",
    "eMAXIS Slim 全世界株式(オール・カントリー)": "eMAXIS Slim 全世界株式(オール・カントリー)(オルカン)"
};
```

### 資産クラスの分類ルール

`classifyAsset`関数（478-483行目）で分類ロジックをカスタマイズできます:

```javascript
const classifyAsset = (name, ticker) => {
    const n = (name || '').toUpperCase();
    if (n.match(/GOLD|GLD|IAU|SLV|金|プラチナ|コモディティ/)) return 'Commodity';
    if (n.match(/REIT|リート|不動産/)) return 'REIT';
    if (n.match(/BOND|債券|AGG|BND|TLT/)) return 'Bond';
    return 'Equity';
};
```

---

## 📊 KPI指標の説明

### Portfolio XIRR（内部収益率）
- 全投資の年率リターンを示す指標
- 時間加重されているため、投資タイミングの影響を考慮
- 計算式: Newton-Raphson法による数値解析

### 現在の資産評価額
- 保有資産の現在価値合計
- 資産残高ファイルの価格 × 保有数量

### 含み損益（評価益）
- 未実現損益 = 現在の資産評価額 - 累計投資額
- リターン率 = 含み損益 / 累計投資額 × 100

### 確定利益（実現損益）
- 売却済み資産の確定損益
- 配当・分配金は推定値（取引履歴に含まれる場合のみ）

---

## 🎨 UIコンポーネント

### カラースキーム
```javascript
Equity (株式):     #3b82f6 (Blue)
Bond (債券):       #10b981 (Emerald)
REIT:             #f59e0b (Amber)
Commodity:        #eab308 (Yellow)
Core (長期):      #6366f1 (Indigo)
Satellite (短期): #f43f5e (Rose)
```

### レスポンシブデザイン
- デスクトップ: 3列グリッド（1400px max-width）
- タブレット: 2列グリッド（1024px以下）
- モバイル: 1列グリッド（640px以下）

---

## 🧮 XIRR計算の仕組み

### Newton-Raphson法の実装

```
XIRR = r (収益率) を求める
Σ CF_i / (1 + r)^t_i = 0 を満たす r を探す

where:
  CF_i = i番目のキャッシュフロー（買い: 負、売り/現在価値: 正）
  t_i  = 初回投資からの経過年数
```

**特徴**:
- 収束判定: 誤差 < 1e-6
- 最大反復: 100回
- 下限制約: r > -1（-100%以下にならない）

---

## 🐛 トラブルシューティング

### ファイルが読み込めない
- **原因**: CSVファイルのエンコーディングがShift_JISでない
- **解決策**: 楽天証券から直接ダウンロードしたファイルを使用してください

### 価格が自動更新されない
- **原因**: 資産残高ファイルが含まれていない
- **解決策**: 保有商品一覧のCSVを追加でアップロードしてください

### XIRRが0%になる
- **原因**: 
  - 取引が1件のみ
  - 計算が収束しない（極端なリターン）
- **解決策**: ログを確認して取引データが正しく読み込まれているか確認

### AI分析が表示されない
- **原因**: APIキーが設定されていない
- **解決策**: Google Gemini APIキーを設定してください

### PDF出力が途中で切れる
- **現在の制限**: 高さ1200pxまでキャプチャ
- **対応予定**: マルチページPDF生成機能を追加予定

---

## 🔒 セキュリティとプライバシー

### データの取り扱い
✅ **すべての処理はブラウザ内で完結**
- サーバーへのデータ送信なし（AI分析を除く）
- CSVデータはメモリ上でのみ処理
- ページをリロードするとデータは消去されます

⚠️ **AI分析時の注意**
- ポートフォリオサマリーのみをGoogle Gemini APIに送信
- 個別銘柄名や詳細金額は送信されません
- APIキーはクライアント側に保存されるため、公開環境では使用しないでください

### 推奨セキュリティ対策
1. ローカル環境での使用
2. API キーの環境変数化
3. 機密情報を含むPDFの管理に注意

---

## 🚧 既知の問題と制限事項

### 現在の制限
1. **PDF出力**: 1ページ目のみ（高さ1200px制限）
2. **為替レート**: USD/JPYのみ対応
3. **JSON Export**: ボタンはあるが未実装
4. **データ永続化**: LocalStorage未対応

### 互換性
- ✅ Chrome 90+
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Edge 90+

---

## 🛣️ ロードマップ

### v1.1（予定）
- [ ] JSON Export機能の実装
- [ ] LocalStorageによるデータ永続化
- [ ] マルチページPDF生成
- [ ] ダークモード対応

### v1.2（予定）
- [ ] ベンチマーク比較機能（TOPIX、S&P500など）
- [ ] Sharpe Ratio、Max Drawdown計算
- [ ] モンテカルロシミュレーション
- [ ] 相関マトリックス

### v2.0（構想）
- [ ] モジュール分割（ES6 Modules）
- [ ] TypeScript化
- [ ] バックエンドAPI（オプション）
- [ ] マルチユーザー対応

---

## 🤝 コントリビューション

バグ報告、機能提案、プルリクエストを歓迎します！

1. このリポジトリをフォーク
2. フィーチャーブランチを作成 (`git checkout -b feature/AmazingFeature`)
3. 変更をコミット (`git commit -m 'Add some AmazingFeature'`)
4. ブランチにプッシュ (`git push origin feature/AmazingFeature`)
5. プルリクエストを作成

---

## 📝 ライセンス

このプロジェクトはMITライセンスの下で公開されています。

---

## 👨‍💻 開発者

**Kento Saito**

---

## 🙏 謝辞

このプロジェクトは以下のオープンソースライブラリを使用しています:

- [Chart.js](https://www.chartjs.org/) - データ可視化
- [PapaParse](https://www.papaparse.com/) - CSV解析
- [jsPDF](https://github.com/parallax/jsPDF) - PDF生成
- [html2canvas](https://html2canvas.hertzen.com/) - HTML→Canvas変換
- [Tailwind CSS](https://tailwindcss.com/) - CSSフレームワーク
- [Lucide Icons](https://lucide.dev/) - アイコンセット
- [Marked](https://marked.js.org/) - Markdownパーサー

---

## 📞 サポート

質問やサポートが必要な場合:
- [Issue を作成](https://github.com/yourusername/Rakuten-trade-portfolio-X-ray-SPA/issues)
- メール: your.email@example.com

---

## ⚖️ 免責事項

このツールは教育目的および個人利用を目的としています。投資判断は自己責任で行ってください。開発者は本ツールの使用によって生じたいかなる損失についても責任を負いません。

---

**Made with ❤️ for Japanese investors**
