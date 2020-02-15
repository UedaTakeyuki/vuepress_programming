<template>
  <div>
    <div　v-for="page in pages_in_tag">
      <a v-bind:href="page.path">{{page.title}}</a>
    </div>
  </div>
</template>

<script>
/* eslint-disable no-console */

export default {
  props: ['tag'],
  data: function() {
    return {
    }
  },
  computed: {
    pages_in_tag() {
      return this.$site.pages.filter(page => String(page.frontmatter.tag).indexOf(this.tag) != -1)
    }
  }
}
</script>
