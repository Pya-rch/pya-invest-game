# INV-GAME-001｜デプロイ検証ゲート

## 目的
GitHubのコード更新を「公開完了」と誤認しない。Renderで実際に最新版がLIVEになり、利用者が開くページが最新版であることを確認する。

## 必須チェック（毎回の公開時）
1. GitHubの対象リポジトリ、ブランチ、commit SHAを記録する。
2. Renderの対象サービスとデプロイ一覧を取得する。自動デプロイ設定が有効でも、実際に新しいデプロイが生成されたか確認する。
3. デプロイが作成されていなければ原因を記録し、権限・設定・Webhookなどを調査する。必要な場合のみ明示的に手動デプロイする。
4. Renderのデプロイが `live` になったことを確認する。`build_in_progress` はDONEではない。
5. LIVEのデプロイcommit SHAが、公開対象のGitHub SHAと一致することを照合する。
6. 公開URLのページ内容（バージョン表記、章数・問題数等）を検証する。キャッシュの影響も区別する。
7. iPhone Safari固有の操作確認は実機Evidenceがない限り「未検証」と記録する。
8. Evidenceとして対象SHA、Render deploy ID、状態、URL、確認時刻、実機確認結果を残す。

## DONE条件
対象commitのRender LIVE確認 + 公開ページの最新版表示確認。利用者への「公開完了」報告はDONE後のみ。

## 既知の事象
2026-11-11: 第2部Prototype 03をGitHubへpushしたが、Renderのデプロイ一覧には初版のLIVEのみ。利用者から「さっきと同じ」と報告。手動デプロイを開始したが、開始時点では `build_in_progress`。自動デプロイ不発の根本原因は未確定。

## 範囲
本ファイルは `pya-invest-game` リポジトリ内の運用チェックリスト。PYĀ Harness全体の00 MASTERやControl Towerへの正式反映は別途必要。
