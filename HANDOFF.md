# セッション引き継ぎ（2026-07-19 更新）

新セッションはこのファイルを読めば状況を把握できる。次の一言でOK: 「`~/Projects/kishufarm/HANDOFF.md`を読んで続きを進めて」

## このセッションでやったこと（すべてコミット済み、pushは全リポ保留中）

1. **farm-app外部公開への方針転換を記録**: `~/Projects/farm-app/docs/adr-001-multitenancy-and-ai.md`（外部公開前提）と`strategy/03-agritech.md`（旧「90日間は外部提供しない」）の矛盾を解消。理由は「農家からのニーズが分かり、ビジネス化する必要があると判断したため」。decision-log.md・03-agritech.md・90day-action-plan.mdを更新（kishufarm: `3b17556`）
2. **GO条件の具体化**: ADR-001にコード調査ベースの改修箇所一覧を追記（farm-app: `a8f68c7`）。知人農家向けヒアリング設計を新規作成（kishufarm: `86d66bb`、`research/agritech-hearing-script.md`）
3. **farmappsummary.md（ユーザー提供の事業戦略サマリー）を反映**:
   - ポジショニング確定：個人農家向け「記録・AI診断アプリ」で競合と正面勝負しない。ターゲットは**従業員のいる農業法人（全国3.3万社）**。差別化軸はガントチャート・チケット管理・@メンションなどのチーム機能
   - 料金プラン確定：Free ¥0 / Pro ¥980/月 / Team ¥2,980/月/組織（10人まで、超過+¥400/人）。収益目標 月20〜30万円（有料組織90〜130社）
   - 実装順序の原則：マルチテナント化＋Stripe連携が未着手のため、機能は先にFree相当で全部作る。アクセス判定は`src/ui/aiFeatures.ts`の`canUseAiFeature()`に集約し、後で課金判定に差し替える
   - AI機能ロードマップ（詳細は`~/Projects/farm-app/docs/roadmap.md`の「事業戦略サマリー」節）: ①音声メモ構造化（実装済み、下記） ②農薬帳票CSV/PDF出力（**実装済み**、`e0e8a17`。farmappsummary.mdは「未着手」表記だが実態とズレているので注意） ③記録検索チャット（未着手） ④天気×防除助言（未着手） ⑤病害虫画像診断（未着手、競合アグリハブが先行）
4. **音声メモ→AI構造化機能をmainに統合**: 別ブランチ`claude/app-chatgpt-api-integration-pq1rgo`（旧mainから分岐、コミット`53a81ff`）を、最新main起点の新ブランチ`claude/voice-memo-ai-onto-main`（コミット`77c7ac7`）にcherry-pick。App.tsxのimportコンフリクトを解消し`npm run build`成功を確認。**まだpush・main統合はしていない**
5. **GO条件①②を実ヒアリング待ちにしない方針に変更**: ユーザー判断により、過去の市場調査（競合比較・法人市場規模）で十分としてAI機能実装を先に進めることに決定。decision-log.mdとADR-001に記録済み

## プロジェクト別の現状と残課題

### farm-app（`~/Projects/farm-app/`）— 実装フェーズ
- **直近のブロッカー**: `OPENAI_API_KEY`がVercel未登録（`vercel env ls`で確認済み）。**Claudeには入力させず、ユーザー自身が`vercel env add OPENAI_API_KEY`かVercelダッシュボードで登録すること**（カード登録必須・無料トライアルなし、使用上限額の設定推奨）
- ブランチ`claude/voice-memo-ai-onto-main`（commit `77c7ac7`）: 音声メモ→AI構造化機能。ビルド確認済み・未push。APIキー登録後にmainへマージしてデプロイ
- 次のAI機能実装候補（`docs/roadmap.md`のロードマップ順）: ③記録検索チャット → ④天気×防除助言 → ⑤病害虫画像診断（コスト最大・競合対抗の目玉）
- マルチテナント化・RLS修正はADR-001に改修箇所（App.tsx 9箇所＋API2本）とログイン設計課題（`login_id`のorg横断ユニーク性未決）を記録済み。着手タイミングは会員権・Web/AEO事業との兼ね合いで判断

### kishufarm-site（`~/Projects/kishufarm-site/`）— 本番反映済み
- 残タスクは`TODO.md`参照。ユーザー作業待ち（Resend APIキー、GA4測定ID、Search Console登録、写真撮影、価格確定）が中心

### kishufarm（`~/Projects/kishufarm/`）— 戦略リポジトリ
- 90日プランPhase1（7/18〜7/31）は先行案内LP・見積りテンプレ・見込み客リスト10件などが未着手のまま

## 次セッションの着手候補

- **farm-app**: OPENAI_API_KEYが登録済みなら、`claude/voice-memo-ai-onto-main`をmainにマージ・デプロイ確認 → 次のAI機能（③記録検索チャット）着手
- kishufarm 90日プランPhase1の実行タスク着手（ドラフト作成が中心、価格確定等ユーザー確認が要るものは除く）
- anuhair案件（`~/Projects/anuhair/`）: 未コミット整理＋オーナーへのリマインド文面用意（Googleアカウント確認・デザイン受領のブロッカー解消）。持ち越し中

## 主要参照ファイル
- `~/Projects/farm-app/docs/adr-001-multitenancy-and-ai.md` — farm-app設計・GO条件・改修箇所
- `~/Projects/farm-app/docs/roadmap.md` — 機能一覧・AI機能ロードマップ・事業戦略サマリー
- `~/Projects/kishufarm/research/agritech-hearing-script.md` — 知人農家ヒアリング設計（実施は任意化）
- `~/Projects/kishufarm/decision-log.md` — 意思決定の記録
- `~/Projects/kishufarm-site/TODO.md` — サイトの残タスク
