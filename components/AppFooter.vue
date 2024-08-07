<template>
  <footer>
    Copyright {{ now }} 淳渔影视 Inc. All Rights Reserved.
  </footer>
</template>

<script setup lang="ts">

const { $dayjs } = useNuxtApp();

const now = ref($dayjs().format('YYYY'))
</script>

<style scoped lang="scss">
footer {
  padding: 40px 0;
  text-align: center;
}
</style>
