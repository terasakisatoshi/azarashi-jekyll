# azarashi-jekyll
For debugging jekyll

`_config.yml` は下記のようになっているとします．

```yml
remote_theme: pages-themes/cayman@v0.2.0
plugins:
  - jekyll-remote-theme # add this line to the plugins list if you already have one

description: Just for debugging

title: config title something
locale: "ja"

```

`index.md` として次のように書くと `_config.yml` に記載されている設定項目を展開することができます.

```md
---
title: ごま's homepage
---

# Description 

このページのタイトルは {{ page.title }} です. 

{{ site.title }} はこのウェブサイトのタイトルです．ページとは区別されます．

description は下記の通りです．

{{ site.description }}

```

例えば `{{ page.title }}` の部分は `ごま's homepage` のようになります．
