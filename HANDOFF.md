# セッション引き継ぎ（2026-07-19）

3連休（7/18〜7/20）でkishufarm関連の停滞プロジェクトを前進させたセッションの引き継ぎ。新セッションはまずこのファイルを読めば状況を把握できる。

## このセッションでやったこと（すべてコミット済み）

1. **kishufarm 事業整理**: 90日プラン・4事業の役割整理は既に完成済みと確認。投資家レビュー（`strategy/05-investor-review.md`）とサイトKPI定義（`strategy/06-site-kpi.md`）を追加
2. **kishufarm-site 品質最大化＋本番デプロイ済み**（トップA案採用）: フォーム実接続・会員権ページ改善・AEO深堀り・画像自前化・UX改善
3. **farm-app**: GAP監査変更のコミット＋ブランチ整理、AI日報生成PoC実装、マルチテナント化の設計ADR作成（**未デプロイ**）

## プロジェクト別の現状と残課題

### kishufarm-site（`~/Projects/kishufarm-site/`）— 本番反映済み
- 詳細な残タスクは **`TODO.md`** に集約。要点:
  - **ユーザー作業待ち**: Resend APIキー登録（`vercel env add RESEND_API_KEY` と `CONTACT_TO`）、GA4測定ID共有、Search Console登録
  - 中川さんに写真撮影依頼（現状ストック写真＋イニシャルのプレースホルダー）
  - 会員権の価格・収穫量目安の確定（membership.htmlの「内容調整中」表記解消）
  - 正式住所・電話・営業時間が確定したらLocalBusiness JSON-LDに追加

### farm-app（`~/Projects/farm-app/`）— 未デプロイ
- **`docs/adr-001-multitenancy-and-ai.md`** に設計と採算試算を集約。要点:
  - AI日報PoC実装済み。動かすには `OPENAI_API_KEY` をVercel環境変数に設定が必要
  - **外部公開の絶対条件**: RLSの穴（`users`/`comments`が他org分まで全件取得できる）を塞ぐ工事が必須。これ抜きで2組織目を乗せると他社データ露出事故
  - AI APIコストは月数円/組織でボトルネックにならない。GO条件は「有料で何組織取れるか」等（ADR第3章）

### kishufarm（`~/Projects/kishufarm/`）— 戦略リポジトリ
- 90日プランPhase1（7/18〜7/31）は実行フェーズが本番。先行案内LP・見積りテンプレ・見込み客リスト10件などが未着手

## 未解決の判断事項（新セッションで確認すべき）

1. **farm-app外部公開の方針転換の記録**: ユーザーは「farm-appを公開する」と判断したが、`strategy/03-agritech.md`は「農業アプリは長期・種まきのみ／90日間は外部提供に着手しない」としており矛盾する。**なぜ今公開に踏み切るのかの理由**を確認し、03-agritechの更新とdecision-logへの記録を行う（このセッションでは理由未確認のため保留した）

## 次セッションの着手候補

- farm-app方針転換の理由記録＋戦略更新（上記1）
- **anuhair案件**（`~/Projects/anuhair/`）: 未コミット整理＋オーナーへのリマインド文面用意（Googleアカウント確認・デザイン受領のブロッカー解消）。今回の3連休プランでDay3想定タスクとして残っている
- kishufarm 90日プランPhase1の実行タスク着手

## 主要参照ファイル
- `~/.claude/plans/3-inherited-glacier.md` — 3連休の全体プラン
- `~/Projects/kishufarm-site/TODO.md` — サイトの残タスク
- `~/Projects/kishufarm/strategy/06-site-kpi.md` — サイトのKPI・計測運用
- `~/Projects/farm-app/docs/adr-001-multitenancy-and-ai.md` — farm-app設計・採算
- `~/Projects/kishufarm/decision-log.md` — 意思決定の記録
