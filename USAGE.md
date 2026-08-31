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

うまく表示されない場合は、以下を確認してください。

- `~/.codex/pets/samoy/pet.json` が存在すること
- `~/.codex/pets/samoy/spritesheet.webp` が存在すること
- Codex Desktopを再起動していること

## 3. iPhoneでSamoyを表示する

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

## 4. iPhoneのホーム画面に追加する

SafariでSamoyページを開いたあと、共有ボタンから `ホーム画面に追加` を選ぶと、アプリのように起動できます。

## 5. PiP表示を試す

PiP表示用ページをSafariで開きます。

```text
http://<MacのLAN IP>:8000/pip.html
```

PiPはiOS側の制限があるため、ページ内ボタンだけで必ず小窓化できるとは限りません。Safariで動画を再生し、iPhone標準プレイヤーのPiPボタンを押すか、`設定 > 一般 > ピクチャインピクチャ > 自動的に開始` をONにしたうえで再生中にホーム画面へ戻してください。

## 6. よくある問題

### iPhoneからページが開けない

以下を確認してください。

- MacとiPhoneが同じWi-Fiに接続されていること
- URLが `http://` で始まっていること
- MacのHTTPサーバーが起動したままになっていること
- macOSのファイアウォールやWi-Fiルーターの端末間通信制限が邪魔していないこと

### PiPにならない

iOSやSafariの仕様により、Webページから必ずPiPへ移行できるとは限りません。まず動画を再生し、標準プレイヤーのPiPボタンを使ってください。

## 7. ライセンス

SamoyはMIT Licenseで公開しています。著作権表示とライセンス文を残せば、個人利用、改変、再配布、商用利用ができます。
