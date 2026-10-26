# 8c-legal

8consulting のアプリの公開文書（プライバシーポリシーなど）を GitHub Pages で配信する。公開先：`https://legal.8consulting.co.jp/<app>/<lang>/`。

- 正本は 8c-shared `templates/legal/`（共通の雛形と、アプリごとの差し込み値）。このリポジトリには**描画した結果だけ**を置く。文面を変えるときは 8c-shared の雛形を変え、ここは作り直す
- 根拠：8c-shared `docs/decisions/2026-10-26-owner-decisions-afternoon.md` 決定 1〜3
- 連絡先・施行日（＝ストア提出日）は、描画のときに `--set` で入れる（8c-shared には置かない）

## 作り方
```sh
python3 <8c-shared>/templates/legal/render.py \
  <8c-shared>/templates/legal/privacy-policy.ja.html \
  <8c-shared>/templates/legal/apps/<app>.ja.json \
  --set contact_email=… --set effective_date=YYYY-MM-DD --set revised_date=YYYY-MM-DD --set version_history=… \
  > <app>/ja/index.html
```
公開したら `index.html` の一覧に 1 行足す。変更は PR で、独立レビューの「マージ可」の後にマージ（8c-shared `docs/decisions/2026-10-26-merge-delegation.md`）。ストアに URL を登録する操作は本人。

## 公開前の確認
8c-shared `templates/legal/README.md` の「公開前の確認」（国外移転の照合、UMP の「プライバシー設定」の入口、GA4 の保存期間、改定のお知らせの場所）。
