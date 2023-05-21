# azarashi-jekyll

For debugging jekyll

## Description

GitHub Pages の機能でホームページを作成する際のデバッグ場所.

# ファイル

ファイルは下記のようになっているはずです:

```console
$ tree
.
├── Gemfile
├── Gemfile.lock
├── README.md
├── _config.yml
└── index.md
```

`_config.yml` は下記のようになっているとします．

```yml
remote_theme: pages-themes/cayman@v0.2.0
plugins:
  - jekyll-remote-theme # add this line to the plugins list if you already have one

description: Just for debugging

title: config title something
locale: "ja"

```

このとき `index.md` として次のように書くと `_config.yml` に記載されている設定項目を展開することができます.

```md
---
title: ごま's homepage
---

# Description 

このページのタイトルは {{ page.title }} です. 

{{ site.title }} はこのウェブサイトのタイトルです．ページのタイトルとは区別されます．ページのタイトルは `index.md` ファイルの冒頭の設定を編集することで更新することができます．

このページの description は下記の通りです．`_config.yml` に記載の description の値が表示されるはずです:

{{ site.description }}

以上
```

例えば `{{ page.title }}` の部分は `ごま's homepage` のようになります．

# ローカル環境で確かめる

```zsh
$ bundle exec jekyll serve
```
