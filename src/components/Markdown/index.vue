<template>
  <div id="content">
    <div v-html="md"></div>
  </div>
</template>
<script>
import Prism from 'prismjs'
//引入marked
const marked = require('marked')

export default {
  created() {
    // 调用marked函数，传入markdown格式的内容，返回一段html
    let mdFile = this.mdFile
    let md = marked(mdFile)
    this.md = marked(mdFile)
    this.$nextTick(() => {
      $('#content code').map(function() {
        Prism.highlightElement(this)
      })
    })
  },
  props: {
    mdFile: {}
  }
}
</script>
<style>
#content {
  width: 100%;
  padding-left: 330px;
  padding-top: 10px;
  padding-bottom: 150px;
  margin-left: 20px;
  margin-right: 20px;
  counter-reset: section;
}
#content {
  line-height: 1.3rem;
}
#content pre {
  margin-left: auto;
  margin-right: auto;
  padding-top: 10px;
  padding-bottom: 10px;
  padding-left: 0.7rem;
  line-height: 1.2;
  color: #fff;
  background: #111;
  border-radius: 5px;
}
#content code {
  color: #a6e22e;
  font-size: 0.7rem;
  font-weight: normal;
  font-family: Consolas, 'Courier New', Courier, FreeMono, monospace;
  background: #111;
  border-radius: 2px;
}
#content p .language-none,
#content li > code,
#content h2 > code,
#content h3 > code {
  padding-left: 3px;
  padding-right: 3px;
  color: #c7254e;
  background: #f9f2f4;
}
#content h2 {
  margin-top: 50px;
  margin-bottom: 0px;
  padding-top: 20px;
  padding-bottom: 0px;
  font-size: 18px;
  text-align: left;
  border-top: 2px solid #666;
  counter-increment: section;
}
#content h2:before {
  content: counter(section) '. ';
}
#content h3 {
  margin-top: 50px;
  margin-bottom: 0px;
  padding-top: 20px;
  padding-bottom: 0px;
  text-align: left;
  border-top: 1px dotted #777;
}
#content h2:hover,
#content h3:hover {
  color: #ed1c24;
}
#content img {
  max-width: 90%;
  display: block;
  margin-left: auto;
  margin-right: auto;
  margin-top: 40px;
  margin-bottom: 40px;
  border-radius: 5px;
}
#content ul {
  display: block;
  list-style-type: none;
  padding-top: 0.5rem;
  padding-bottom: 0.5rem;
}
#content ol {
  display: block;
  padding-top: 0.5rem;
  padding-bottom: 0.5rem;
}
#content ul li:before {
  /* a hack to have dashes as a list style */
  content: '-';
  position: relative;
  left: -5px;
}
#content ul li,
#content ol li {
  text-indent: -5px; /* to compensate for the padding for the dash */
  font-size: 0.8rem;
}
#content ul li.link,
#content ol li.link {
  color: #2980b9;
  text-decoration: none;
  font-size: 0.7rem;
  font-weight: bold;
  cursor: pointer;
}
#content a:link,
#content a:visited {
  color: #4682be;
  text-decoration: none;
}
#content .content-toc {
  background: #bdc3c7;
  border-radius: 5px;
}
#content table {
  display: block;
  width: 100%;
  overflow: auto;
  word-break: normal;
  word-break: keep-all;
}
#content table th {
  font-weight: bold;
}
#content table th,
#content table td {
  padding: 6px 13px;
  border: 1px solid #ddd;
}
#content table tr {
  background-color: #fff;
  border-top: 1px solid #ccc;
}
#content table tr:nth-child(2n) {
  background-color: #f8f8f8;
}
#back_to_top {
  display: none;
  position: fixed;
  height: 20px;
  width: 70px;
  top: 20px;
  margin-left: 930px;
  margin-top: 0px;
  color: #fff;
  line-height: 20px;
  text-align: center;
  font-size: 10px;
  border-radius: 5px;
  background-color: #aaa;
}
#back_to_top:hover {
  background-color: #444;
  cursor: pointer;
}
#edit {
  display: none;
  position: fixed;
  height: 17px;
  width: 70px;
  top: 45px;
  margin-left: 930px;
  margin-top: 0px;
  color: #fff;
  line-height: 17px;
  text-align: center;
  font-size: 10px;
  border-radius: 5px;
  background-color: #aaa;
}
#edit:hover {
  background-color: #444;
  cursor: pointer;
}
#loading,
#error {
  display: none;
  position: fixed;
  top: 0;
  height: 17px;
  font-size: 14px;
}
#flip {
  position: fixed;
  height: 20px;
  width: 100%;
  bottom: 10px;
  font-size: 10px;
  text-align: center;
}
#pageup,
#pagedown {
  height: 20px;
  width: 70px;
  display: inline-block;
  border-radius: 5px;
  background-color: #aaa;
  text-align: center;
  line-height: 20px;
  color: #fff;
}
#pageup {
  margin-right: 5px;
}
#pageup:hover,
#pagedown:hover {
  background-color: #444;
  cursor: pointer;
}
#pagedown {
  margin-left: 5px;
}
.progress-indicator-2 {
  position: fixed;
  top: 0;
  left: 0;
  height: 3px;
  background-color: #0a74da;
}
code[class='language-'],
pre[class='language-'] {
  color: #a6e22e;
  text-shadow: 0 1px rgba(0, 0, 0, 0.3);
  font-family: Consolas, Monaco, 'Andale Mono', monospace;
  direction: ltr;
  text-align: left;
  white-space: pre;
  word-spacing: normal;
  word-break: normal;
  -moz-tab-size: 4;
  -o-tab-size: 4;
  tab-size: 4;
  -webkit-hyphens: none;
  -moz-hyphens: none;
  -ms-hyphens: none;
  hyphens: none;
}
pre[class*='language-'] {
  padding: 1em;
  margin: 0.5em 0;
  overflow: auto;
  border-radius: 0.3em;
}
:not(pre) > code[class='language-'],
pre[class='language-'] {
  background: #272822;
}
:not(pre) > code[class*='language-'] {
  padding: 0.1em;
  border-radius: 0.3em;
}
.token.comment,
.token.prolog,
.token.doctype,
.token.cdata {
  color: #75715e;
}
.token.punctuation {
  color: #f8f8f2;
}
.namespace {
  opacity: 0.7;
}
.token.property,
.token.tag,
.token.constant,
.token.symbol {
  color: #f92672;
}
.token.boolean,
.token.number {
  color: #ae81ff;
}
.token.selector,
.token.attr-name,
.token.string,
.token.builtin {
  color: #a6e22e;
}
.token.operator,
.token.entity,
.token.url,
.language-css .token.string,
.style .token.string,
.token.variable {
  color: #f92672;
}
.token.atrule,
.token.attr-value {
  color: #e6db74;
}
.token.keyword {
  color: #66d9ef;
}
.token.regex,
.token.important {
  color: #fd971f;
}
.token.important {
  font-weight: bold;
}
.token.entity {
  cursor: help;
}
</style>
