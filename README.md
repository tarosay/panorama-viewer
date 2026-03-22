# panorama-viewer

正距円筒画像（360度カメラ画像）をブラウザで表示するためのシンプルなパノラマビューアです。

GitHub Pages にそのまま配置して使えます。

## 構成

- `index.html`
  - 案内ページ
  - `viewer.html` のURL表示
  - iframe埋め込みコード表示
  - コピーボタン
  - プレビュー表示

- `viewer.html`
  - 実際の360°ビューア本体
  - 正距円筒画像をドラッグで回転
  - マウスホイールで拡大縮小

- `pano.jpg`
  - 表示対象の正距円筒画像

## ファイル構成

```text
panorama-viewer/
  ├─ index.html
  ├─ viewer.html
  ├─ pano.jpg
  └─ README.md
```

## 使い方

### 1. 画像を配置する

表示したい正距円筒画像を `pano.jpg` という名前で配置してください。

### 2. GitHub Pages で公開する

GitHub の `Settings` → `Pages` で以下を設定します。

- Source: `Deploy from a branch`
- Branch: `main`
- Folder: `/ (root)`

公開URLの例:

```text
https://YOUR_GITHUB_USERNAME.github.io/panorama-viewer/
```

## URL

### 案内ページ

```text
https://YOUR_GITHUB_USERNAME.github.io/panorama-viewer/
```

### 実際の埋め込み先

```text
https://YOUR_GITHUB_USERNAME.github.io/panorama-viewer/viewer.html
```

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

## 操作方法

- ドラッグ: 視点回転
- マウスホイール: 拡大縮小

## 注意

- 画像は正距円筒画像を使用してください
- 画像ファイル名は現在 `pano.jpg` 固定です
- `viewer.html` は埋め込み専用ページです
- `index.html` は説明と埋め込みコード確認用ページです

## ライブラリ

- [three.js](https://threejs.org/)

## ライセンス

MIT License

Copyright (c) 2026

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND.

