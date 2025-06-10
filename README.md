# 美容クリニック顧客分析システム

## 概要
美容クリニックに来店する顧客の継続率とアップセル率向上のための顧客分析システムです。
数秘術、占星術、四柱推命、動物占い、姓名判断、音霊占いを組み合わせたAI分析により、
顧客の性格特性と購買傾向を分析し、最適な接客戦略を提案します。

## 主要機能

### 🔮 5つの核心ビジネス指標
1. **継続志向度** - ルーティン型 vs 変化型
2. **新規刺激欲求** - トレンド型 vs 定番型
3. **価格・価値観感度** - コスパ型 vs 品質重視型
4. **決断スピード** - 即決型 vs 熟考型
5. **コミュニケーションスタイル** - 感情型 vs 論理型

### ⚡ 10秒タブレット分析
- 氏名・生年月日・性別の入力から即座に分析
- スタッフ向け接客スクリプト自動生成
- リアルタイム顧客対応支援

### 📊 管理機能
- 会社別データ管理（12桁ID）
- 分析結果の蓄積・集計
- 効果測定ダッシュボード

## 技術スタック

- **フロントエンド**: HTML, CSS (TailwindCSS), JavaScript
- **バックエンド**: Cloudflare Workers, Hono
- **AI**: OpenAI GPT-4o-mini
- **データベース**: Cloudflare KV
- **デプロイ**: GitHub Actions + Cloudflare Workers

## ビジネス目標

- **継続率**: +10% 向上
- **アップセル率**: +15% 向上
- **次回予約確定率**: +10-15ポイント向上
- **スタッフトレーニング時間**: 短縮

## ディレクトリ構造

```
beauty-clinic-customer-analysis/
├── .cursor/                    # Cursor AI設定・ルール
├── src/                        # バックエンドソースコード
├── public/                     # フロントエンドファイル
├── package.json               # 依存関係管理
├── wrangler.jsonc             # Cloudflare Workers設定
└── README.md                  # このファイル
```

## セットアップ

1. リポジトリのクローン
2. 依存関係のインストール: `npm install`
3. 環境変数の設定: `.env`ファイル作成
4. 開発サーバー起動: `npm run dev`

## デプロイURL
- **本番環境**: https://cloudflare-workers-customer-assessment.ten-ai.workers.dev
- **管理画面**: https://cloudflare-workers-customer-assessment.ten-ai.workers.dev/admin
  - ユーザー名: `admin`
  - パスワード: `0000`

## 主要機能
1. **顧客情報入力** (`/form.html`) - 姓名、生年月日、性別の入力
2. **AI顧客分析** (`/api/results`) - 5つの核心ビジネス指標による分析
3. **結果表示** (`/result-tabs.html`) - タブ形式での詳細分析結果
4. **管理機能** (`/admin`) - 会社登録・管理
5. **会社専用ページ** (`/c/{会社ID}`) - 各クリニック向けカスタムページ

## 5つの核心ビジネス指標
1. **継続志向度（ルーティン型）** - 来店周期・次回予約戦略
2. **新規刺激欲求（トレンド型）** - 季節限定・新商品受容性
3. **価格・価値観感度（コスパ型）** - 割引効果・セット販売適性
4. **決断スピード** - クロージングタイミング・フォロー戦略
5. **コミュニケーションスタイル** - 感情型 vs 論理型アプローチ

## 自動デプロイ設定

### GitHub Secrets の設定
GitHub リポジトリの Settings > Secrets and variables > Actions で以下を設定：

1. **CLOUDFLARE_API_TOKEN**
   - Cloudflare Dashboard > My Profile > API Tokens
   - "Create Token" > "Custom token"
   - Permissions:
     - Account: Cloudflare Workers:Edit
     - Zone: Zone:Read
     - Account: Account:Read
   - Account Resources: Include - ＆Co.GROUP (AI)

2. **CLOUDFLARE_ACCOUNT_ID**
   ```
   f936ae74ccb3e57720edbdd06d1f0f13
   ```

3. **OPENAI_API_KEY**
   - OpenAI APIキーを設定

### 自動デプロイの動作
- `main` ブランチへのpushで自動デプロイ実行
- Pull Request作成時にもデプロイテスト実行
- GitHub Actionsで`wrangler deploy`を自動実行

## ローカル開発

### 環境変数設定
`.dev.vars` ファイルを作成：
```
OPENAI_API_KEY=your_openai_api_key_here
ADMIN_PASSWORD=0000
```

### 開発サーバー起動
```bash
# 依存関係インストール
npm install

# ローカル開発サーバー起動
npm run dev
# または
wrangler dev
```

### デプロイ
```bash
# 手動デプロイ
npm run deploy
# または
wrangler deploy
```

## プロジェクト構造
```
src/
├── index.js                 # メインエントリーポイント
├── middleware/
│   └── auth.js              # Basic認証ミドルウェア
└── routes/
    ├── admin.route.js       # 管理画面ルート
    ├── client.route.js      # 会社専用ページルート
    ├── results.route.js     # 顧客分析APIルート
    └── compatibility.route.js # 相性診断APIルート

public/
├── form.html               # 顧客情報入力フォーム
├── result.html             # 基本結果表示
├── result-tabs.html        # タブ形式結果表示
├── css/                    # スタイルシート
└── js/                     # JavaScript

.github/workflows/
└── deploy.yml              # GitHub Actions CI/CD
```

## ライセンス
このプロジェクトは私的利用のため作成されています。

---

**開発者**: otaotakahiro
**作成日**: 2024年6月10日
**自動デプロイ**: ✅ GitHub ⟷ Cloudflare Workers 連携完了
