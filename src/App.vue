<template>
  <my-content>
    <h2>2</h2>
    <div v-html="md"></div>
  </my-content>
</template>

<script>
import test from './test.md'
import Prism from 'prismjs'
import content from '@/components/content'
//引入marked
const marked = require('marked')
export default {
  components: {
    'my-content': content
  },
  data() {
    return {
      md: ''
    }
  },
  created() {
    // 调用marked函数，传入markdown格式的内容，返回一段html
    let md = marked(test)
    this.md = marked(test)
    this.$nextTick(() => {
      $('#content code').map(function() {
        Prism.highlightElement(this)
      })
    })
  }
}
</script>
