<script setup lang="ts">
import { ExpandLeft as IconExpandLeft } from '@icon-park/vue-next'
import { useSidebar } from '../composables/sidebar'
defineOptions({
  name: 'vp-nav'
})
const { switchOpen, open, isOpen } = useSidebar()
</script>

<template>
  <header>
    <div class="title">
      <IconExpandLeft
        size="20"
        v-show="!open"
        @click="switchOpen"
        :class="isOpen ? 'reversal' : ''"
      />
      <a href="/" class="app_name">
        <h1>Hypotension treatment</h1>
      </a>
      <span class="segmentation">|</span>
      <a href="/">
        <h1>低血压治疗</h1>
      </a>
    </div>
    <div class="links">
      <a href="/">首页</a>
      <a href="mailto:admin@lolinya.net">联系我们</a>
    </div>
  </header>
</template>

<style lang="less" scoped>
header {
  position: sticky;
  top: 0;
  flex-shrink: 0;
  height: 0;
  width: 100%;
  height: @nav-height;
  border-bottom: 1px solid #aaaa;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 20px;
  background-image: radial-gradient(transparent 1px, #fff 1px);
  background-size: 4px 4px;
  backdrop-filter: saturate(50%) blur(4px);
  -webkit-backdrop-filter: saturate(50%) blur(4px);
  z-index: 100;
  .title {
    display: flex;
    align-items: center;
    .i-icon {
      margin-right: 10px;
      transition: all 0.5s;
      &.reversal {
        transform: rotateZ(180deg);
      }
    }
    h1 {
      font-size: 18px;
      font-weight: 600;
    }
    .segmentation {
      margin: 0 10px;
    }
    .min-width(500px, {
      .app_name {
        display: none;
      }
    });
  }
  .links {
    a {
      margin-left: 7px;

      &:hover {
        text-decoration: underline;
        color: var(--vp-c-brand);
      }
    }
  }
}
</style>
