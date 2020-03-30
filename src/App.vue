<template>
  <my-markdown :mdFile="test"></my-markdown>
</template>

<script>
import test from './test1.md'
import Markdown from '@/components/Markdown'
export default {
  components: {
    'my-markdown': Markdown
  },
  data() {
    return {
      test
    }
  }
}
</script>
