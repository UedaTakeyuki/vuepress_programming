<template>
  <div>
    <div　v-for="page in $site.pages">
      <a v-bind:href="page.path">{{page.title}}</a>
      {{page.tags}}
    </div>
  </div>
</template>
<script>
/* eslint-disable no-console */
console.log(this)
export default {
  mounted() {
    console.log(this)
  }
}
</script>
