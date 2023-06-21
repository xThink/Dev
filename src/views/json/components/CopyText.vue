<template>
 <div ref="copyText">
 {{ content }}
 </div>
</template>

<script>
export default {
  props: { content: Object },
  // data () {
  //   return {
  //     contenttext: this.content
  //   }
  // },
  mounted () {
    console.log(` CopyText mounted ${JSON.stringify(this.content)}`)
    // this.contenttext = this.text
  },
  updated () {
    console.log(` CopyText updated `)
    // console.log(` CopyText updated ${JSON.stringify(this.content)}`)
  }
}
</script>
<style lang='less' scoped>

</style>
