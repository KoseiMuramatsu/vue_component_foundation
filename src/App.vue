<template>
  <div id="app">
    <!-- 命名はパスカルケースorケバブケース -->
    {{ message }}
    <emit @from-child="receiveMessage"></emit>
    <direct-emit @click='directAlertMessage'></direct-emit>
    <!-- Slotの勉強 -->
    <!-- <user> -->
      <!-- <template v-slot:default>John Due</template>
      <template v-slot:age>25</template>
      <template v-slot:sex>男性</template> -->
    <!-- </user> -->

    <!-- Scoped Slot データプロパティ渡すパターン(子データを親で受け取る) -->
    <user v-slot="dataAll">
      {{ dataAll }}
    </user>

    <Menu>
      <template v-slot:activator="{ on }">
        <button v-on:click="on">
          click it
        </button>
      </template>
      <ul>
        <li>List1</li>
        <li>List2</li>
        <li>List3</li>
      </ul>
    </Menu>

    <!-- this.$slotsからSlotの値を取得 -->
    <div>
      <BlogPost>
        <template #title>vue.js</template>
          I'd like to know about $vm.slots.
      </BlogPost>
    </div>

    <Table :header="header" :items="items"></Table>
  </div>
</template>

<script>
import Emit from './components/Emit.vue'
import DirectEmit from './components/DirectEmit.vue'
import User from './components/User.vue'
import Menu from './components/Menu.vue'
import Table from './components/Table.vue'
import BlogPost from './components/BlogPost.vue'

export default {
  // パスカルケースのみ
  components: {
    Emit,
    DirectEmit,
    User,
    Menu,
    Table,
    BlogPost
  },
  data: function() {
    return {
      header: ['ID', 'FIRSTNAME', 'LASTNAME', 'EMAIL'],
      items: [
        {
          id: 1,
          firstName: 'John',
          lastName: 'Doe',
          email: 'john@example.com'
        },
        {
          id: 2,
          firstName: 'Kevin',
          lastName: 'Wood',
          email: 'kevin@example.com'
        },
        {
          id: 3,
          firstName: 'Harry',
          lastName: 'Bosch',
          email: 'harry@test.com'
        },
      ],
      message: ''
    }
  },
  methods: {
    // emitの第二引数(値)をmessageの中に入れている
    receiveMessage: function(message) {
      this.message = message;
    },
    directAlertMessage: function() {
      alert('子から直接イベントを受け取ったよ')
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
