<template>
  <!-- 直接受け取るパターン -->
  <button v-on:click="$emit('click')">ボタン</button>
</template>

<script>
export default {
}
</script>

<style scoped lang="scss">
</style>
