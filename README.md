# 飲み物自動販売機（ブラウザ版 / PWA）

このフォルダをそのまま **GitHub Pages / Netlify / Vercel / Cloudflare Pages** にアップすると、
自動販売機アプリをブラウザで動かせます。オフラインでも動作（PWA）し、キオスク端末向けの設定も入れています。

## 使い方（ローカル）
1. このZIPを解凍
2. フォルダを開き、`index.html` をブラウザで開く（Chrome 推奨）
3. オフライン対応するには一度オンラインで開いてキャッシュさせてください（Service Worker 登録）

## デプロイ方法
### GitHub Pages
1. GitHubで新規リポジトリを作成
2. このフォルダの中身をコミット＆プッシュ
3. リポジトリの Settings → Pages → Source を `main` / `/ (root)` に設定
4. 数十秒後に公開URLが発行されます

### Netlify
1. Netlifyにログイン → "Add new site" → "Deploy manually"
2. このフォルダをドラッグ＆ドロップ（ビルド不要）

### Vercel
1. New Project → "Import" → このフォルダを選択
2. フレームワークは "Other"（ビルド不要）

### Cloudflare Pages
1. "Create a project" → "Upload assets"
2. このフォルダをアップロード（ビルド不要）

## キオスク（自動販売機のブラウザ）でのポイント
- 端末のブラウザを **全画面表示** に設定（Chrome: `F11` / Android: Kioskモードアプリなど）
- 画面のスリープを無効化（OS設定）
- ネット不安定でも使えるよう、PWAキャッシュ済みにしておく
- 価格や商品は `index.html` の `products` 定数を書き換え

## QR決済連携のヒント
- 現在は「支払い完了（デモ）」ボタンです。実運用では各キャッシュレス事業者の **静的QR**（店頭に貼る）と組み合わせて運用するのが簡単です。
- もしリンク払い（URLスキーム）を使う場合は、事業者仕様に合わせて `simulatePayment()` 内で外部URLを開くように変更してください。

## ファイル一覧
- `index.html` … アプリ本体（あなたのHTMLをベースにPWA対応・ローカル保存などを追加）
- `manifest.webmanifest` … PWA設定
- `service-worker.js` … オフラインキャッシュ
- `icons/` … PWAアイコン（差し替え可）
