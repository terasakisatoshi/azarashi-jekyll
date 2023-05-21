# azarashi-jekyll
For debugging jekyll

`_config.yml` は下記のようになっているとします．

```yml
remote_theme: pages-themes/cayman@v0.2.0
plugins:
- jekyll-remote-theme # add this line to the plugins list if you already have one

title: ごま's homepage
description: Just for debugging
locale: "ja"
```

`index.md` として次のように書くと `_config.yml` に記載されている設定項目を展開することができます.

```md
---
---

# Description 

このページのタイトルは {{ site.title }} です. description は下記の通りです．

{{ site.description }}
```

例えば `{{ site.title }}` の部分は `ごま's homepage` のようになります．
