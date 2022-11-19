---
lang: ja
title: Vivliostyleプロジェクトの今までとこれから
author: Shinyu Murakami
---

# Vivliostyleプロジェクトの<br>今までとこれから {.cover}

2022-11-20 \
Shinyu Murakami \
Vivliostyle Foundation

# 目次 {.toc role="doc-toc"}

1.  [Vivliostyleプロジェクトの今まで](#vivliostyleプロジェクトの今まで)
1.  [Vivliostyleプロジェクトのこれから](#vivliostyleプロジェクトのこれから)

# Vivliostyleプロジェクトの今まで

## Vivliostyle各プロジェクトの充実

- Vivliostyle Pub、アルファ版公開！
  - https://vivliostyle-pub-develop.vercel.app/
- Vivliostyle Themes スタイルテーマ
- Vivliostyle CLI コマンドラインツール
- VFM (Vivliostyle Flavored Markdown)
- Vivliostyle.js CSS組版エンジン(Core) 
  - [Vivliostyle.jsにおけるWeb標準、CSSサポートの大改善](https://vivliostyle.org/viewer/#src=https://murakamishinyu.github.io/vivliostyle-dev2022autumn/slide.html&spread=false)
- Vivliostyle Viewer—CSS組版プレビュー、電子出版ビューア

# Vivliostyleプロジェクトのこれから

## VFM v2—Markdown拡張仕様の改良

VFM v1→v2で、[セクション分け](https://vivliostyle.github.io/vfm/#/ja/vfm#%E3%82%BB%E3%82%AF%E3%82%B7%E3%83%A7%E3%83%B3%E5%88%86%E3%81%91-sectionization)での属性の扱いの仕様変更：

```md
# Welcome {.title}
```
というMarkdownに対して、VFM v1で生成されるHTMLは
```html
<section class="level1 title" id="welcome">
  <h1 class="title">Welcome</h1>
```
VFM v2では
```html
<section class="level1" aria-labelledby="welcome">
  <h1 class="title" id="welcome">Welcome</h1>
```

## Themes のスタイルシートの刷新

- CSS変数を活用してよりカスタマイズがしやすいように

