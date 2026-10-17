# CLAUDE.md（www_redirect — 旧住所 www.tas9.net の転送と見張り）

名刺ページは 2026-10-17 に `www.tas9.net` から **`takahashi.tas9.net`**（`web\tas9_net`）へ移した。
このリポジトリは、空いた `www.tas9.net` を GitHub Pages につないでおくための小さな転送ページ（公開リポ `tas9-labo/www_redirect`）。

## 役割は2つ

1. **転送**：古い www のリンクから来た人を、同じパスのまま `https://takahashi.tas9.net/` へ送る（`index.html`・`404.html` は同じ中身）。
   www の証明書は 2026-12-13 で切れる。それ以降は証明書が出ない限り、www を開くと警告が出る（転送はおまけ・本人了承済み）。
2. **見張り**：www の証明書の申請が直ったかを確かめる窓口。申請の状態はこのリポジトリの
   `gh api repos/tas9-labo/www_redirect/pages` の `https_certificate` で見る。
   毎週の点検（`docs\整合性チェック.ps1` の [3.9]）が自動で見て、`approved` で `domains` が `["www.tas9.net"]` だけになったら知らせる。

## なぜ住所を変えたか（経緯の要点）

apex（www 無しの tas9.net）を GitHub に向けた実験（2026-09）の名残で、www の証明書の更新申請が「www＋apex の2つ組」のまま止まり、
付け直し・サイト作り直し・サポート依頼（無料プランは受け付けず）でも消せなかった。有料プランや新しいサービスは使わない（本人判断）。
詳細は `web\tas9_net\CLAUDE.md`「公開の足回り」。

## www に戻す時（見張りが知らせたら・本人が決める）

1. このリポジトリの Pages のカスタムドメインを外す（`gh api -X PUT repos/tas9-labo/www_redirect/pages` に `{"cname": null}`）
2. `web\tas9_net` の `CNAME`・index.html・tas9.vcf・`print/` の住所を www に戻して作り直し、push
3. 戻すかどうか・takahashi を残すかは本人が決める。戻さないなら見張りだけ続ける
