<template>
  <div>
    <div　v-for="page in part_of_pages(current, current + shows)">
      <a v-bind:href="page.path">{{page.title}}</a>
    </div>
    <button @click="back"><-</button>
    total: {{pages_num}}, current: {{current}}
    <button @click="next">-></button>
  </div>
</template>

<script>
/* eslint-disable no-console */

export default {
  props: ['tag', 'shows'],
  data: function() {
    return {
//      shows: 5,
      current: 0,
    }
  },
  methods: {
    part_of_pages(start, end){
      return this.pages_in_tag.slice(start, end)
    },
    next(){
      this.current = this.current + this.shows
      if (this.current > this.pages_num){
        this.current = this.pages_num - this.shows
      }
      if (this.current < 0){
        this.current = 0
      }

    },
    back(){
      this.current = this.current - this.shows
      if (this.current < 0){
        this.current = 0
      }
    }
  },
  computed: {
    pages_in_tag() {
      return this.$site.pages.filter(page => String(page.frontmatter.tag).indexOf(this.tag) != -1)
    },
    pages_num() {
      return this.$site.pages.filter(page => String(page.frontmatter.tag).indexOf(this.tag) != -1).length
    }
  }
}
</script>
