<template>
  <div ref="editor" class="svelte-jsoneditor-vue" />
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
  mounted () {
    this.editor = new JSONEditor({
      target: this.$refs.editor,
      props: { content: this.content, readOnly: this.readOnly, onChange: this.onChange, mode: 'text' }
    })
    console.log('mounted create editor', this.editor)
  },
  updated () {
    console.log(` Vue json editor updated ${JSON.stringify(this.content)}`)
    this.config = { content: this.content, readOnly: this.readOnly, onChange: this.onChange }
    console.log('update props', JSON.stringify(this.config))
    this.editor.updateProps(this.config)
  },
  beforeUnmount() {
    console.log('destroy editor')
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
