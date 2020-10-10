<template>
  <!-- Scoped Slot(関数渡す.ver) -->
  <div>
    <!-- <button @click="on">Click</button> -->
    <slot name="activator" v-bind:on="on">
    </slot>
    <slot v-if="display">
    </slot>
  </div>
</template>

<script>
export default {
  data() {
    return {
      display: true
    }
  },
  methods: {
    on() {
      return this.display = !this.display;
    }
  }

}
</script>
