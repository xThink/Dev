<template>
  <div class="json">
    <div class="editor">
      <VueJSONEditor
        :content="content"
        :mode="text"
        :on-change="onChange"
        :read-only="readOnly"
      />
      <VueJSONEditor2
      ref="vueJSONEditor2"
        :content="content2"
        :mode="tree"
        :read-only="readOnly"
      />
    </div>
    <div>
      <CopyText :content="content2"/>
      </div>
  </div>
</template>

<script>
import VueJSONEditor from './components/VueJSONEditor.vue'
import VueJSONEditor2 from './components/VueJSONEditor2.vue'
import CopyText from './components/CopyText.vue'
export default {
  components: { VueJSONEditor, VueJSONEditor2, CopyText },
  data() {
    return {
      showEditor: true,
      readOnly: false,
      content: {
        json: {
          greeting: 'Hello World',
          color: '#ff3e00',
          ok: true,
          values: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15]
        },
        text: undefined
      },
      content2: {
        json: {
        },
        text: undefined
      }
    }
  },
  mounted () {
    console.log('index mounted')
    console.log('this.$refs index', this.$refs)
  },
  updated () {
    console.log('index updated')
  },
  methods: {
    onChange(content) {
      console.log('onChange', content)
      // this.content = content

      if (content.text) {
        this.content2.text = content.text
      } else if (content.json) {
        this.content2.text = JSON.stringify(content.json)
      }
      this.$refs.vueJSONEditor2.doSomething()

      // this.content2 = { json: JSON.parse(content.text), text: content.text }
    }
  }
}
</script>
<style lang="less" scoped>
.json {
  margin: 0 5%;

  .editor {
    width: 100%;
    height: 350px;
    display: flex;
  }
}
</style>
