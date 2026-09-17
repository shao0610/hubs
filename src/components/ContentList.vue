<template>
  <section class="content-list">
    <div class="controls">
      <label>排序：</label>
      <select v-model="sortBy">
        <option value="time">时间</option>
        <option value="name">名称</option>
      </select>
      <button @click="toggleOrder">{{ orderText }}</button>
    </div>

    <ul class="items">
      <li v-for="item in sortedItems" :key="item.id" class="item">
        <div class="item-left">
          <div class="item-title">{{ item.title }}</div>
          <div class="item-meta">{{ item.author }} • {{ item.date }}</div>
        </div>
      </li>
    </ul>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'

const props = defineProps({ items: { type: Array, required: true } })

const sortBy = ref('time')
const asc = ref(false)

const sortedItems = computed(() => {
  const arr = [...props.items]
  if (sortBy.value === 'time') {
    arr.sort((a, b) => new Date(a.date) - new Date(b.date))
  } else {
    arr.sort((a, b) => a.title.localeCompare(b.title))
  }
  return asc.value ? arr : arr.reverse()
})

const orderText = computed(() => (asc.value ? '升序' : '降序'))
function toggleOrder() {
  asc.value = !asc.value
}
</script>
