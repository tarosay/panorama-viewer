# panorama-viewer

正距円筒画像（360°パノラマ画像）をブラウザで表示・確認・書き出しするためのシンプルなビューアです。GitHub Pages にそのまま配置して使えます。現在は、公開用の `viewer.html` に加えて、ローカル画像を読み込んで切り出し保存できる `local-viewer.html` も含まれています。fileciteturn2file0L72-L74 fileciteturn2file1L285-L316 fileciteturn2file2L37-L46

## 構成

- `index.html`  
  案内ページです。`viewer.html` のURL表示、iframe埋め込みコード表示、コピーボタン、プレビュー表示があります。あわせて、目立たない小さなリンクで `local-viewer.html` を開けます。fileciteturn2file0L72-L74 fileciteturn2file0L76-L104

- `viewer.html`  
  公開用のシンプルな360°ビューア本体です。`pano.jpg` を読み込み、ドラッグで回転、マウスホイールで拡大縮小できます。`pano.jpg` が見つからない場合はエラー表示になります。fileciteturn2file2L37-L46 fileciteturn2file2L63-L83 fileciteturn2file2L97-L105

- `local-viewer.html`  
  ローカル画像対応の高機能ビューアです。画像のアップロード、ドラッグ&ドロップ、保存範囲の指定、PNG書き出し、Cube-map書き出しに対応しています。fileciteturn2file1L285-L316 fileciteturn2file1L526-L546 fileciteturn2file1L548-L604

- `pano.jpg`  
  `viewer.html` と `local-viewer.html` のサンプル画像です。`viewer.html` はこのファイル名を前提に読み込みます。fileciteturn2file2L63-L76 fileciteturn2file1L342-L344

## ファイル構成

```text
panorama-viewer/
  ├─ index.html
  ├─ viewer.html
  ├─ local-viewer.html
  ├─ pano.jpg
  └─ README.md
```

## 各ページ

### 1. 公開用ビューア

- 案内ページ  
  `https://YOUR_GITHUB_USERNAME.github.io/panorama-viewer/`

- 実際の埋め込み先  
  `https://YOUR_GITHUB_USERNAME.github.io/panorama-viewer/viewer.html`

`index.html` では、現在のURLから `viewer.html` のURLを自動生成し、iframeコードも表示します。fileciteturn2file0L111-L129

### 2. ローカル画像ビューア

- ローカル画像ビューア  
  `https://YOUR_GITHUB_USERNAME.github.io/panorama-viewer/local-viewer.html`

`index.html` から小さなリンクで開けます。fileciteturn2file0L72-L74

## 使い方

### 公開用 `viewer.html`

1. 表示したい正距円筒画像を `pano.jpg` という名前で配置します。fileciteturn2file2L63-L76
2. `viewer.html` を開きます。fileciteturn2file2L37-L46
3. ドラッグで視点回転、ホイールでズームできます。fileciteturn2file2L23-L33 fileciteturn2file2L97-L105

### ローカル用 `local-viewer.html`

1. `画像を選択` ボタン、またはドラッグ&ドロップでローカル画像を読み込みます。サンプル画像へ戻すボタンもあります。fileciteturn2file1L285-L291 fileciteturn2file1L391-L398 fileciteturn2file1L419-L429
2. ドラッグで向きを決め、ホイールでズームします。初期の表示画角は垂直115°です。fileciteturn2file1L337-L344 fileciteturn2file1L463-L472
3. 保存用の水平画角・垂直画角は初期値 90° / 90° です。入力欄で直接変更でき、マウスホイールでも 1° 単位で変更できます。fileciteturn2file1L299-L302 fileciteturn2file1L446-L458
4. 白枠で保存範囲を確認できます。4隅ハンドルをドラッグして範囲を直接変更すると、画角の数値にも反映されます。白枠表示のON/OFFも可能です。fileciteturn2file1L266-L275 fileciteturn2file1L279-L283 fileciteturn2file1L300-L306 fileciteturn2file1L431-L444 fileciteturn2file1L500-L524
5. ダイアログは半透明で、ドラッグ移動できます。fileciteturn2file1L22-L31 fileciteturn2file1L33-L69 fileciteturn2file1L460-L490

## 書き出し機能

### PNG保存

現在向いている方向を、指定した水平画角・垂直画角で PNG として保存します。保存サイズは元画像の画素密度から自動計算し、最大辺が大きすぎる場合は縮小されます。fileciteturn2file1L305-L310 fileciteturn2file1L492-L498 fileciteturn2file1L526-L546

保存サイズの考え方:

- 横幅: 元画像幅 × 水平画角 / 360
- 高さ: 元画像高さ × 垂直画角 / 180
- 最大辺: 4096px に制限fileciteturn2file1L492-L498

### Cube-map保存

現在の向きを基準に、6面のキューブマップをそれぞれ PNG で保存します。面名は `front / right / back / left / up / down` です。各面は 90° x 90° の正方形で、サイズは元画像幅を元に自動計算され、最大 2048px に制限されます。fileciteturn2file1L548-L571

### Cube-map展開図保存

6面を1枚のPNGとして保存します。配置は以下です。fileciteturn2file1L573-L604

```text
        [up]
[left][front][right][back]
       [down]
```

展開図全体は `4 x 3` 面サイズのキャンバスで保存されます。fileciteturn2file1L588-L597

## iframe 埋め込みコード

```html
<iframe
  src="https://YOUR_GITHUB_USERNAME.github.io/panorama-viewer/viewer.html"
  width="100%"
  height="600"
  style="border:none;"
  allowfullscreen
  loading="lazy">
</iframe>
```

このコードは `index.html` 上でも自動表示されます。fileciteturn2file0L84-L92 fileciteturn2file0L111-L129

## GitHub Pages での公開

GitHub の `Settings` → `Pages` で以下を設定します。

- Source: `Deploy from a branch`
- Branch: `main`
- Folder: `/ (root)`

公開後は `index.html` を入口にして、
- `viewer.html` を埋め込み用に利用
- `local-viewer.html` をローカル画像確認用に利用

という使い分けができます。README の旧版では `viewer.html` のみ前提でしたが、現状は `local-viewer.html` も含む構成です。fileciteturn1file0L34-L53 fileciteturn2file0L72-L74

## 操作方法

### `viewer.html`

- ドラッグ: 視点回転
- マウスホイール: 拡大縮小fileciteturn2file2L23-L33

### `local-viewer.html`

- ドラッグ: 視点回転
- マウスホイール: 拡大縮小
- 画像ドラッグ&ドロップ: ローカル画像読み込み
- 入力欄上でホイール: 画角変更
- 白枠4隅ドラッグ: 保存範囲変更
- ダイアログヘッダドラッグ: パネル移動fileciteturn2file1L314-L316 fileciteturn2file1L446-L458 fileciteturn2file1L431-L444 fileciteturn2file1L460-L490

## 注意

- 画像は正距円筒画像を使用してください。fileciteturn1file0L72-L75
- `viewer.html` は `pano.jpg` 固定読み込みです。ローカル画像アップロードには対応していません。fileciteturn2file2L63-L76
- ローカル画像の確認・切り出し・Cube-map保存は `local-viewer.html` を使ってください。fileciteturn2file1L285-L316
- ブラウザによっては、Cube-map 6枚保存時に連続ダウンロード確認が表示される場合があります。これは各面を個別PNGで保存しているためです。fileciteturn2file1L548-L571

## 使用ライブラリ

- [three.js](https://threejs.org/)fileciteturn2file2L37-L46

## ライセンス

MIT License
