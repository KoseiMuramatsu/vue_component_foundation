<template>
  <div>
    <h1><slot name="title">Title</slot></h1>
    <p><slot></slot></p>
    <p>Slot:{{ slotValue }}</p>
  </div>
</template>

<script>
  export default {
    computed:{
      slotValue(){
        console.log(this.$slots.default[0].text)
        return this.$slots;
      }
    }
  }
</script>
