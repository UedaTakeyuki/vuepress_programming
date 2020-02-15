---
tag: control vue
title: pages
---
# pages
## ページ
<div　v-for="page in $site.pages">
  <a v-bind:href="page.path">{{page.title}}</a>
  {{page.tags}}
</div>

### vue
<div　v-for="page in $site.pages.filter(page => String(page.frontmatter.tag).match(/vue/))">
  <a v-bind:href="page.path">{{page.title}}</a>
  {{page.tags}}
</div>

## さらにページ
