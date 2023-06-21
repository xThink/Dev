<template>
  <div ref="editor2" class="svelte-jsoneditor-vue" />
</template>

<script>
import { JSONEditor } from 'vanilla-jsoneditor'

// JSONEditor properties as of version 0.3.60
// const propNames = [
//   'content',
//   'mode',
//   'mainMenuBar',
//   'navigationBar',
//   'statusBar',
//   'readOnly',
//   'indentation',
//   'tabSize',
//   'escapeControlCharacters',
//   'escapeUnicodeCharacters',
//   'validator',
//   'onError',
//   'onChange',
//   'onChangeMode',
//   'onClassName',
//   'onRenderValue',
//   'onRenderMenu',
//   'queryLanguages',
//   'queryLanguageId',
//   'onChangeQueryLanguage',
//   'onFocus',
//   'onBlur'
// ]



export default {
  name: 'VueJSONEditor',
  props: { content: Object, readOnly: Boolean, onChange: Function },
  data() {
    return {
      config: {}
    }
  },
  watch: {
    content: {
      handler (newValue, oldValue) {
        console.log('watch contenttext handle2', JSON.stringify(newValue))
      },
      deep: true, // 是否深度监听
      immediate: false // 是否在组件创建时立即执行回调函数
    }
  },
  mounted () {
    this.editor = new JSONEditor({
      target: this.$refs.editor2,
      props: { content: this.content, readOnly: this.readOnly, onChange: this.onChange }
    })
    console.log('create editor2', this.editor)
  },
  updated () {
    console.log(` Vue json editor2 updated `)
    this.config = { content: this.content, readOnly: this.readOnly, onChange: this.onChange }
    console.log('update props2', JSON.stringify(this.config))
    this.editor.updateProps(this.config)
  },
  beforeUnmount() {
    console.log('destroy editor2')
    this.editor.destroy()
    this.editor = null
  }
}
</script>

<style lang='less'  scoped>
.svelte-jsoneditor-vue {
  display: flex;
  flex: 1;

}
</style>
