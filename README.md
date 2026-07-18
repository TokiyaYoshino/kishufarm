# kishufarm — 霧珠ファーム 経営戦略リポジトリ

霧珠ファーム（京都・亀岡）の全体戦略・市場調査・行動プランを管理するリポジトリ。

## 構成

```
research/        市場調査（施策の根拠となる数字・事例）
strategy/        戦略ドキュメント
  00-overview.md         全体戦略（4事業の役割・相乗効果・優先順位）
  01-vineyard.md         ぶどう・ワイン・会員権の施策
  02-vegetables.md       野菜生産・卸の施策
  03-agritech.md         農業管理アプリ kishu-farm の施策
  04-web-aeo.md          Web制作×AEO事業の施策
  90day-action-plan.md   直近90日の週次行動プラン
decision-log.md  意思決定の記録（いつ・何を・なぜ）
```

## 読み方

1. まず `strategy/00-overview.md` で全体方針を掴む
2. `strategy/90day-action-plan.md` で「今週やること」を確認する
3. 施策の根拠を確認したいときは `research/` を参照する

## 運用ルール

- 大きな意思決定をしたら `decision-log.md` に1行追記する
- 施策の追加・変更は該当する `strategy/0X-*.md` を更新し、90日プランに反映する
- 売上等の生数字は公開リポジトリに載せない（レンジ表記に留める）
