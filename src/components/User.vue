<template>
  <!-- Scoped Slot(スコープ付きSlot) -->
  <span>
    <slot v-bind:user="user" v-bind:message="message">
      {{user.lastName}}
    </slot>
  </span>

  <!-- v-slotの使い方練習 -->
  <!-- 親のコンテンツがslotの中に入る -->
  <!-- slotタグ内にデフォルトでテキストを記述しておけば親から何も渡されない時に表示される -->
  <!-- <ul>
    <li>名前：<slot>名無しの権兵衛</slot></li>
    <li>年齢：<slot name="age">記入なし</slot></li>
    <li>性別：<slot name="sex">不明</slot></li>
  </ul> -->
</template>

<script>
export default {
  data() {
    return {
      user: {
        firstName: 'John',
        lastName: 'Doe',
        age: '25',
        sex: '男性',
      },
      message: 'Hello Scoped Slot',
    }
  },
  methods: {
    on() {
      return this.display = !this.display;
    }
  }
}
</script>
