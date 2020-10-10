<template>
  <!-- methodを介して受け取るパターン -->
  <div>
    <input type="text" v-model="inputText">
    <button v-on:click="clickEvent">ボタン</button>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      inputText: ''
    }
  },
  methods: {
    clickEvent: function() {
      console.log(this.$emit);
      // from-childイベントを渡している。親に渡すイベント名は自分で自由に付けられる。
      // 第一引数イベント名、第二引数渡す値(複数渡すときは{}オブジェクトにする)
      this.$emit('from-child', this.inputText);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
