<template>
  <div class="m-screenful">
    <svg-icon :icon-class="isFullscreen?'exit-fullscreen':'fullscreen'" @click="click" class="full-screen"/>
  </div>
</template>

<script lang="ts" setup>
  import screenfull from './index'
  import { ElMessage } from 'element-plus'
  import { onBeforeUnmount, onMounted, ref } from 'vue'

  let isFullscreen = ref(false)
  const click = () => {
    if (!screenfull.isEnabled) {
      ElMessage({
        message: '你的浏览器不支持',
        type: 'warning',
      })
      return false
    }
    screenfull.toggle()
  }
  const change = () => {
    isFullscreen.value = screenfull.isFullscreen
  }
  const init = () => {
    if (screenfull.isEnabled) {
      screenfull.on('change', change)
    }
  }

  const destroy = () => {
    if (screenfull.isEnabled) {
      screenfull.off('change', change)
    }
  }
  onMounted(() => {
    init()
  })

  onBeforeUnmount(() => {
    destroy()
  })
</script>

<style lang="scss" scoped>
  .m-screenful {
    display: flex;
    align-items: center;
    padding-right: 0;
    justify-content: center;
    cursor: pointer;
    transition: all 0.3s;
  }
  .transverseMenu {
    .full-screen {
      color: white;
    }
  }
</style>
