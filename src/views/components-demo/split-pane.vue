<template>
  <div class="components-container">
    <!--    <aside><strong>SplitPane</strong> If you've used-->
    <!--      <a href="https://codepen.io/" target="_blank"> codepen</a>,-->
    <!--      <a href="https://jsfiddle.net/" target="_blank"> jsfiddle </a>will not be unfamiliar.-->
    <!--      <a href="https://github.com/PanJiaChen/vue-split-pane" target="_blank"> Github repository</a>-->
    <!--    </aside>-->
    <!--    <split-pane split="vertical">-->
    <!--      <template slot="paneL">-->
    <!--        <div class="left-container" />-->
    <!--      </template>-->
    <!--      <template slot="paneR">-->
    <!--        <split-pane split="horizontal">-->
    <!--          <template slot="paneL">-->
    <!--            <div class="top-container" />-->
    <!--          </template>-->
    <!--          <template slot="paneR">-->
    <!--            <div class="bottom-container" />-->
    <!--          </template>-->
    <!--        </split-pane>-->
    <!--      </template>-->
    <!--    </split-pane>-->
  </div>
</template>

<script lang="ts" setup>
  import SplitPane from 'vue-splitpane'

  // export default {
  //   name: 'SplitpaneDemo',
  //   components: { splitPane },
  //   methods: {
  //     resize() {
  //       console.log('resize')
  //     }
  //   }
  // }
</script>

<style scoped>
  .components-container {
    position: relative;
    height: 100vh;
  }

  .left-container {
    background-color: #f38181;
    height: 100%;
  }

  .right-container {
    background-color: #fce38a;
    height: 200px;
  }

  .top-container {
    background-color: #fce38a;
    width: 100%;
    height: 100%;
  }

  .bottom-container {
    width: 100%;
    background-color: #95e1d3;
    height: 100%;
  }
</style>
