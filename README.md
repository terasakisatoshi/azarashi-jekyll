# azarashi-jekyll

For debugging jekyll

## Description

GitHub Pages の機能でホームページを作成する際のデバッグ場所.

https://terasakisatoshi.github.io/azarashi-jekyll/

で確認できる.

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

[Jekyll を使用して GitHub Pages サイトをローカルでテストする](https://docs.github.com/ja/pages/setting-up-a-github-pages-site-with-jekyll/testing-your-github-pages-site-locally-with-jekyll) に書いてあるようにすれば良い．が，Jekll のインストールに戸惑うので [`asdf`](https://asdf-vm.com/guide/getting-started.html) を用いてシステムに付属している Ruby とは別の Ruby を入れることにする. bundle コマンドも前記インストールした Ruby に紐づいている bundle コマンドを使うことにする.

## Step1: asdf のインストール

asdf コマンドをすでに導入していれば次のステップに進む.
各自の動作環境を理解し [こちらのインストール手順に従う](https://asdf-vm.com/guide/getting-started.html)

`asdf` コマンドがつかれば良い.

## Step2: asdf の Ruby プラグインを導入

[asdf-vm/asdf-ruby](https://github.com/asdf-vm/asdf-ruby) が提供する asdf のプラグインを導入する. 下記を実行すれば良い.

```console
$ asdf plugin add ruby https://github.com/asdf-vm/asdf-ruby.git
```

すでに導入済みであれば下記のコマンドで ruby プラグインをアップデートしておく.

```console
$ asdf plugin update ruby
```

## Step3: asdf から Ruby のインストールをする

次のコマンドで ruby をインストールする.

```console
$ asdf install ruby 3.2.2
```

上記のコマンドを実行後 

```console
asdf global ruby 3.2.2
```

とすると `ruby` コマンドは `~/.asdf/shims/ruby` の `ruby` を指すことになる. これでシステムに付属している ruby の環境を汚すことがなくなる.

## Step4: reshim の実行

```console
$ asdf reshim
```

コマンドによって `bundle` などのコマンドをターミナルから認識できるようにする.

```console
$ which bundle
$ ~/.asdf/shims/bundle
```

## Step5: Gemfile に記述されている依存関係を導入する.

`bundle` コマンドを使うと Gemfile に記述している Ruby パッケージをインストールすることができる.

```console
$ bundle install
```

## Step6: ローカル環境でページを表示

下記のコマンドを実行する:

```console
$ bundle exec jekyll serve
 Server address: http://127.0.0.1:4000
  Server running... press ctrl-c to stop.
```

ログにあるように http://127.0.0.1:4000 に移動するとページが表示できる.

Ctrl-C でローカル環境で起動しているサーバを終了する.

以降は Step6 から出発しページの更新とプレビューの睨めっこをする.

