# 使い方

このドキュメントでは、SamoyをダウンロードしてCodex DesktopやiPhoneで使う方法を説明します。

## 1. ダウンロードする

### Gitを使う場合

ターミナルで以下を実行します。

```bash
git clone https://github.com/mitsuhitokawada/samoy-codex-pet.git
cd samoy-codex-pet
```

### ZIPでダウンロードする場合

1. GitHubのリポジトリページを開きます。
2. 緑色の `Code` ボタンを押します。
3. `Download ZIP` を押します。
4. ダウンロードしたZIPファイルを展開します。
5. 展開したフォルダを開きます。

## 2. Codex Desktopのペットとして使う

リポジトリ内の `pet.json` と `spritesheet.webp` を、Codexのペットフォルダに配置します。

macOSの場合:

```bash
mkdir -p ~/.codex/pets/samoy
cp pet.json spritesheet.webp ~/.codex/pets/samoy/
```

配置後、Codex Desktopを再起動してください。ペット選択画面にSamoyが表示される場合は、Samoyを選択します。

ペット選択は、通常 `Settings > Appearance > Pets` または `設定 > 外観 > ペット` から開けます。

うまく表示されない場合は、以下を確認してください。

- `~/.codex/pets/samoy/pet.json` が存在すること
- `~/.codex/pets/samoy/spritesheet.webp` が存在すること
- Codex Desktopを再起動していること
- ペット一覧の下側にあるカスタムペット欄までスクロールしていること

## 3. スプライト仕様

Samoyは以下の形式で作っています。

- 画像サイズ: `1536 x 1872`
- グリッド: `8列 x 9行`
- 1セル: `192 x 208`
- 背景: 透明
- 未使用セル: 透明
- 形式: WebP

行ごとの状態は以下です。

| 行 | state | フレーム数 | 役割 |
| --- | --- | --- | --- |
| 0 | `idle` | 6 | 通常時 |
| 1 | `running-right` | 8 | 右方向への移動 |
| 2 | `running-left` | 8 | 左方向への移動 |
| 3 | `waving` | 4 | あいさつ |
| 4 | `jumping` | 5 | 跳ねる反応 |
| 5 | `failed` | 8 | 失敗時の反応 |
| 6 | `waiting` | 6 | 待機中 |
| 7 | `running` | 6 | 作業中 |
| 8 | `review` | 6 | レビュー中 |

## 4. iPhoneでSamoyを表示する

iPhoneで表示する場合は、Mac上でこのフォルダをHTTP配信します。

```bash
python3 -m http.server 8000 --bind 0.0.0.0
```

Mac上で確認する場合:

```text
http://127.0.0.1:8000/
```

iPhoneから見る場合は、MacとiPhoneを同じWi-Fiに接続し、MacのLAN IPアドレスを使います。

```text
http://<MacのLAN IP>:8000/
```

例:

```text
http://192.168.x.x:8000/
```

## 5. iPhoneのホーム画面に追加する

SafariでSamoyページを開いたあと、共有ボタンから `ホーム画面に追加` を選ぶと、アプリのように起動できます。

## 6. PiP表示を試す

PiP表示用ページをSafariで開きます。

```text
http://<MacのLAN IP>:8000/pip.html
```

PiPはiOS側の制限があるため、ページ内ボタンだけで必ず小窓化できるとは限りません。Safariで動画を再生し、iPhone標準プレイヤーのPiPボタンを押すか、`設定 > 一般 > ピクチャインピクチャ > 自動的に開始` をONにしたうえで再生中にホーム画面へ戻してください。

## 7. よくある問題

### iPhoneからページが開けない

以下を確認してください。

- MacとiPhoneが同じWi-Fiに接続されていること
- URLが `http://` で始まっていること
- MacのHTTPサーバーが起動したままになっていること
- macOSのファイアウォールやWi-Fiルーターの端末間通信制限が邪魔していないこと

### PiPにならない

iOSやSafariの仕様により、Webページから必ずPiPへ移行できるとは限りません。まず動画を再生し、標準プレイヤーのPiPボタンを使ってください。

## 8. 安全性について

このリポジトリに含まれる主な実行コードは、静的なHTML、CSS、JavaScriptです。インストール時に必要なのは `pet.json` と `spritesheet.webp` のコピーだけです。

外部のペット生成スキルや別リポジトリを使う場合は、実行前に内容を確認してください。特に、設定ファイルの書き換え、外部通信、認証情報の扱いがないかを見るのがおすすめです。

## 9. ライセンス

SamoyはMIT Licenseで公開しています。著作権表示とライセンス文を残せば、個人利用、改変、再配布、商用利用ができます。

## 10. 参考

- [Codexの「ペット」の作り方](https://zenn.dev/galirage/articles/codex-custom-pets)
- [Codexでペットを設定＆作成する方法専用スキルを使って、オリジナルのペットも作ってみた](https://note.com/mbbs/n/n18bcbef03bcb)
