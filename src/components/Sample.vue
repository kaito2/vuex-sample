<template>
    <div class="sample">
      <h1>{{ msg }}</h1>
      <p>message length = {{ msgLength }}</p>
      <input type="text" v-model="newMsg" />
      <button v-on:click="update">Update</button>
      <button v-on:click="repeat">Repeat</button>
    </div>
</template>

<script>
import { mapState } from 'vuex'
import { UPDATE_MESSAGE } from '../store/mutation-types'

export default {
  name: 'Sample',
  data () {
    return {
      // msg: 'Welcome to My Vuex Sample'
      newMsg: ''
    }
  },
  computed: {
    // replace with `...mapState()`
    // msg () {
    //  return this.$store.state.msg
    // }
    ...mapState({
      msg: state => state.msg
    }),
    msgLength () {
      return this.msg.length
    }
  },
  methods: {
    update () {
      // this.$store.state.msg = this.newMsg
      this.$store.commit(UPDATE_MESSAGE, this.newMsg)
    },
    repeat () {
      this.$store.dispatch('repeat')
    }
  }
}
</script>
nn
