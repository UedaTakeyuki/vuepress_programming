<template>
  <div>
    <div　v-for="page in part_of_pages(current, current + shows)">
      <a v-bind:href="page.path">{{page.title}}</a>
      <div style="font-size:10px;">{{normalizedDate(page.frontmatter.posted)}} posted</div>
    </div>
    <button v-show="current != 0" @click="back">&#x25c0</button>
    total: {{pages_num}}, current: {{current}}
    <button v-show="current < pages_num - shows" @click="next">&#x25b6</button>
  </div>
</template>

<script>
/* eslint-disable no-console */

export default {
  /** 
   * tag   - tag name which is as serch key for pages.
   * shows - number of showing pages.
  */
  props: ['tag', 'shows'],
  data: function() {
    return {
      current: 0, // current start number of showing.
    }
  },
  methods: {
    // slice of page which is showing.
    part_of_pages(start, end){
      return this.pages_in_tag_sorted.slice(start, end)
    },
    // go slice ahed.
    next(){
      this.current = this.current + this.shows
      if (this.current > this.pages_num){
        this.current = this.pages_num - this.shows
      }
      if (this.current < 0){
        this.current = 0
      }

    },
    // back slice
    back(){
      this.current = this.current - this.shows
      if (this.current < 0){
        this.current = 0
      }
    },
    // date str -> normalize -> year-month-date
    normalizedDate(date_str) {
      return new Date(Date.parse(date_str)).toISOString().slice(0,10)
    }
  },
  computed: {
    // The Array of the page which include the tag specified by prop.
    pages_in_tag() {
      return this.$site.pages.filter(page => String(page.frontmatter.tag).indexOf(this.tag) != -1)
    },
    // The number of pages_in_tag
    pages_num() {
      return this.pages_in_tag.length
    },
    // pages array sorted by posted
    pages_in_tag_sorted() {
      return this.pages_in_tag.sort(function(a,b){return (Date.parse(a.frontmatter.posted) <= Date.parse(b.frontmatter.posted) ? 1: -1);})
    },

  }
}
</script>
