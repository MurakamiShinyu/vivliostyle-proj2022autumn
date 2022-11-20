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

### [セクション分け](https://vivliostyle.github.io/vfm/#/ja/vfm#%E3%82%BB%E3%82%AF%E3%82%B7%E3%83%A7%E3%83%B3%E5%88%86%E3%81%91-sectionization)での属性の扱いの仕様変更

VFM v1の次の仕様が廃止：
> - 見出しの属性は基本的にセクションへコピーされます
> - id 属性はセクションに移動します

VFM v2の仕様では：
> - 見出しの id 属性値をセクションの aria-labelledby 属性へ値をコピーします




例：
```md
# Welcome {.title}
```
というMarkdownに対して、VFM v1で生成されるHTMLは
```html
<section class="level1 title" id="welcome">
  <h1 class="title">Welcome</h1>
</section>
```
VFM v2では
```html
<section class="level1" aria-labelledby="welcome">
  <h1 class="title" id="welcome">Welcome</h1>
</section>
```

#### 仕様変更理由

VFM v1で、見出しに指定された属性を、HTMLの見出し要素(h1-h6)だけでなく自動生成されるsection要素にも重複して出力（ただしidはsectionのみに出力）していたのは次の理由：

- 参考にした[Pandocの --section-divs オプション](https://pandoc.org/MANUAL.html#option--section-divs)の仕様から。
- CSSでsectionに対してスタイル指定したいとき、sectionにidやclass属性がないと不便だったため。

しかしこの仕様では、見出しだけに指定したいスタイルがsection全体にも適用されてしまう問題があり、これも不便。

CSSで `:has()` 擬似クラスが使えるようになったことにより、「sectionにidやclass属性がないと不便」は解消されてる。

例：見出しのclass名が "title" であるsectionのスタイルを指定

```css
section:has(> .title) {
    ...
}
```

したがって、これまでの仕様の利点はなくなったので廃止。Markdownの見出しに指定した属性はHTMLの見出し要素にだけ出力という分かりやすい仕様に。詳しくは [VFM issue #151](https://github.com/vivliostyle/vfm/issues/151)。

ほかにも仕様改良予定あり。[VFM issues](https://github.com/vivliostyle/vfm/issues) をご覧ください。 

## Themes のスタイルシートの刷新

- CSS変数を活用してよりカスタマイズがしやすいように

