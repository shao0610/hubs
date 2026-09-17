<template>
  <div class="app-root">
    <HeaderBar :currentTab="tab" @change-tab="(v) => tab = v" @logout="handleLogout" />
    <main class="main-area">
      <ContentList :items="currentItems" />
    </main>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import HeaderBar from './components/HeaderBar.vue'
import ContentList from './components/ContentList.vue'
import { blogs, communities } from './data/sampleData'

const tab = ref('博客')
const blogsRef = ref(blogs)
const communitiesRef = ref(communities)

const currentItems = computed(() => (tab.value === '博客' ? blogsRef.value : communitiesRef.value))

function handleLogout() {
  alert('已退出')
}
</script>
