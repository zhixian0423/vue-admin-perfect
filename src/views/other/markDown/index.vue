<template>
  <u-container-layout class="mark-down">
    <el-alert
        title="Markdown 是基于 md-editor-v3 插件完成， 官方文档请查看 ：https://imzbf.github.io/md-editor-v3/index"
        type="warning"
        :closable="false"
    />
    <div class="" style="flex: 1">
      <md-editor v-model="text" />
    </div>
    <div style="margin-top: 20px; flex-shrink: 0">
      <el-button type="primary" @click="submit">提交</el-button>
    </div>
  </u-container-layout>
</template>
<script lang="ts">
//
// https://www.jianshu.com/p/0b06128a6117
import { defineComponent } from 'vue'
import MdEditor from 'md-editor-v3'
import 'md-editor-v3/lib/style.css'

export default defineComponent({
  components: { MdEditor },
  data() {
    return { text: '## 你好呀,欢迎！' }
  },
  methods: {
    submit() {
      console.log('this.text', this.text)
    },
  },
})
</script>

<style lang="scss">
.mark-down {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  .md {
    height: 600px;
  }
}
</style>
