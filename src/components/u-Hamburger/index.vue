<template>
  <el-breadcrumb class="app-breadcrumb" separator="/">
    <transition-group name="breadcrumb">
      <el-breadcrumb-item v-for="(item, index) in obj.levelList" :key="item.path">
        <span
          v-if="item.redirect === 'noRedirect' || index == obj.levelList.length - 1"
          class="no-redirect"
          >{{ item.meta.title }}</span
        >
        <a v-else @click.prevent="handleLink(item)">{{ item.meta.title }}</a>
      </el-breadcrumb-item>
    </transition-group>
  </el-breadcrumb>
</template>

<script lang="ts" setup>
  import pathToRegexp from 'path-to-regexp'
  import { onMounted, reactive, watch } from 'vue'
  import { useRoute } from 'vue-router'

  const obj = reactive({ levelList: {} })
  const route = useRoute()

  // 获取面包屑
  const getBreadcrumb = () => {
    let matched = route.matched.filter((item) => item.meta && item.meta.title)
    const first = matched[0]
    obj.levelList = matched.filter(
      (item) => item.meta && item.meta.title && item.meta.breadcrumb !== false,
    )
  }
  onMounted(() => {
    getBreadcrumb()
    watch(route, () => {
      if (route.path.startsWith('/redirect/')) {
        return
      }
      getBreadcrumb()
    })
  })
</script>

<style lang="scss" scoped>
  .app-breadcrumb.el-breadcrumb {
    margin-left: 10px;
    display: inline-block;
    font-size: 14px;
    margin-bottom: 4px;
    .no-redirect {
      cursor: text;
    }
  }
</style>
