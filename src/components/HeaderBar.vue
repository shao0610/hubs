<template>
  <header class="header-bar">
    <div class="left">
      <div class="logo">
        <svg width="28" height="28" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
          <circle cx="12" cy="12" r="10" stroke="#4f46e5" stroke-width="2" />
          <path d="M8 12h8" stroke="#4f46e5" stroke-width="2" stroke-linecap="round" />
        </svg>
      </div>
      <div class="title">我的站点</div>
    </div>

    <nav class="right">
      <div class="menu">
        <button
          v-for="m in menus"
          :key="m"
          :class="['menu-item', { active: m === currentTab } ]"
          @click="emit('change-tab', m)">
          {{ m }}
        </button>
      </div>
      <button class="logout" @click="emit('logout')">退出</button>
    </nav>
  </header>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue'

const props = defineProps({ currentTab: { type: String, required: true } })
const emit = defineEmits(['change-tab', 'logout'])

const menus = ['博客', '社区']
</script>
