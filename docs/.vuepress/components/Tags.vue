<template>
  <div>
    <div　v-for="page in $site.pages.filter(page => String(page.frontmatter.tag).indexOf(tag) != -1)">
      <a v-bind:href="page.path">{{page.title}}</a>
    </div>
  </div>
</template>

<script>
export default {
  props: ['tag'],
}
</script>
