<template>
  <div>
    <Transition name="fade" mode="out-in">
      <div v-if="!isMenuExpand">
        <div
          :class="menuIcons[0].label"
          un-hover:opacity-100
          cursor-pointer
          opacity-50
          @click="menuIcons[0].method"
        ></div>
      </div>
      <div v-else space-y-3>
        <div
          v-for="menuIcon in menuIcons.slice(1)"
          :class="menuIcon.label"
          un-hover:opacity-100
          cursor-pointer
          opacity-50
          @click="menuIcon.method"
        ></div>
      </div>
    </Transition>
  </div>
</template>
<script lang="ts" setup>
const isMenuExpand = ref(false);
const menuIcons = ref([
  {
    label: 'i-ri-menu-fill',
    method: () => {
      isMenuExpand.value = true;
    },
  },
  {
    label: 'i-ri-close-circle-line',
    method: () => {
      isMenuExpand.value = false;
    },
  },
  {
    label: 'i-ri-home-8-line',
    method: async () => {
      await navigateTo('/');
    },
  },
  {
    label: 'i-ri-file-list-line',
    method: async () => {
      await navigateTo({
        path: '/',
        query: {
          type: 'article',
        },
      });
    },
  },
  {
    label: 'i-ri-book-2-line',
    method: async () => {
      await navigateTo({
        path: '/',
        query: {
          type: 'book',
        },
      });
    },
  },
]);
</script>
<style scoped></style>
