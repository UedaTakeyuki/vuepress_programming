---
tag: control vue
title: pages
posted: 2020-02-15
---
# pages
## ページ
<div　v-for="page in $site.pages">
  <a v-bind:href="page.path">{{page.title}}</a>
  {{page.tags}}
</div>

### control
<div　v-for="page in $site.pages.filter(page => String(page.frontmatter.tag).match(/control/))">
  <a v-bind:href="page.path">{{page.title}}</a>
  {{page.tags}}
</div>

### vue
<Tags tag="vue" shows="5"/>
## さらにページ
