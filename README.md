# Samoy Codex Pet

Samoyは、Codex Desktopで使えるサモエド風のカスタムペットです。

iPhoneのSafariやホーム画面Webアプリで表示するための簡易ページも同梱しています。

詳しい使い方は [USAGE.md](./USAGE.md) を見てください。

## 内容

- `pet.json`: Codex Desktop用ペット定義
- `spritesheet.webp`: Samoyのアニメーションスプライト
- `index.html`: タップ操作とドラッグ移動ができる通常表示ページ
- `pip.html`: iPhoneの標準動画プレイヤー経由でPiP表示を試すためのページ
- `samoy-*.mp4`: PiP向けの短いループ動画
- `manifest.json`: ホーム画面追加用の設定

## スプライト仕様

Samoyのスプライトは、Codexカスタムペット向けの以下の形式です。

- 画像サイズ: `1536 x 1872`
- グリッド: `8列 x 9行`
- 1セル: `192 x 208`
- 背景: 透明
- 形式: WebP

各行は `idle`、`running-right`、`running-left`、`waving`、`jumping`、`failed`、`waiting`、`running`、`review` の状態に対応しています。

## ダウンロード

Gitを使える場合:

```bash
git clone https://github.com/mitsuhitokawada/samoy-codex-pet.git
cd samoy-codex-pet
```

Gitを使わない場合:

1. GitHubページ右上の `Code` を押します。
2. `Download ZIP` を押します。
3. ZIPを展開します。

## Codex Desktopに入れる

```bash
mkdir -p ~/.codex/pets/samoy
cp pet.json spritesheet.webp ~/.codex/pets/samoy/
```

その後、Codex Desktopを再起動し、`Settings > Appearance > Pets` または `設定 > 外観 > ペット` からSamoyを選んでください。詳しい手順は [USAGE.md](./USAGE.md) にあります。

## iPhoneで見る

このディレクトリでHTTPサーバーを起動します。

```bash
python3 -m http.server 8000 --bind 0.0.0.0
```

iPhoneから、MacのLAN IPアドレスを使って開きます。

```text
http://<MacのLAN IP>:8000/
```

PiP表示を試す場合:

```text
http://<MacのLAN IP>:8000/pip.html
```

## ライセンス

MIT Licenseです。個人利用、改変、再配布を自由に行えます。

## 参考

- [Codexの「ペット」の作り方](https://zenn.dev/galirage/articles/codex-custom-pets)
- [Codexでペットを設定＆作成する方法専用スキルを使って、オリジナルのペットも作ってみた](https://note.com/mbbs/n/n18bcbef03bcb)
