<template>
  <div
    class="bg-slate-200 duration-500 h-auto div_css"
    :style="{ 'max-height': maxHeihgt }"
  >
    <table>
      <thead>
        <tr>
          <th class="p-2">標題</th>
          <th class="p-2">內容</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in showData" :key="index">
          <td class="p-2">{{ item.title }}</td>
          <td class="p-2">{{ item.content }}</td>
        </tr>
      </tbody>
    </table>
  </div>
  <button type="button" class="border p-5 m-5" @click="isShow = !isShow">
    {{ !isShow ? 'showAll' : 'hidden' }}
  </button>
</template>

<script setup>
import { ref, computed } from 'vue';

const isShow = ref(false);

const data = [
  {
    title: 'lorem1',
    content: '  Lorem ipsum dolor sit amet.',
  },
  {
    title: 'lorem2',
    content: '  Lorem ipsum dolor sit amet.',
  },
  {
    title: 'lorem3',
    content: '  Lorem ipsum dolor sit amet.',
  },
  {
    title: 'lorem4',
    content: '  Lorem ipsum dolor sit amet.',
  },
  {
    title: 'lorem5',
    content: '  Lorem ipsum dolor sit amet.',
  },
];

const showData = computed(() => {
  if (isShow.value) {
    return data;
  }

  return data.slice(0, 3);
});

const maxHeihgt = computed(() => {
  if (!isShow.value) {
    return '300px';
  }
  const table = document.querySelector('table');
  const tbody = document.querySelector('tbody');
  const rows = tbody.children;
  console.log(rows);
  const height = Array.from(rows).reduce((total, row) => {
    return total + row.offsetHeight;
  }, 0);
  return `${height + table.offsetTop}px`;
});
</script>

<style>
.div_css {
  overflow: hidden;
  transition: max-height 500ms ease-in-out;
}
</style>
