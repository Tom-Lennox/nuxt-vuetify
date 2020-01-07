<template>
  <v-layout>
    <v-flex class="text-center">
      <img src="/v.png" alt="Vuetify.js" class="mb-5" />
      <blockquote class="blockquote">
        <v-btn @click="callMethod">+1</v-btn>
        <p>{{ counter }}{{ lesstThan3Computed }}</p>
        <p>{{ counter }}{{ lesstThan3Method() }}</p>
        <p>aaa</p>
        <div v-html="log"></div>
        <footer>
          <small>
            <em>&mdash;John Johnson</em>
            <pre>{{ $data }}</pre>
          </small>
        </footer>
      </blockquote>
    </v-flex>
  </v-layout>
</template>
<script>
export default {
  data() {
    return {
      counter: 0,
      log: ''
    }
  },
  computed: {
    lesstThan3Computed: function() {
      this.log += 'computedが呼ばれました<br>'
      return this.counter > 3 ? ' > 3 ' : ' <= 3 '
    }
  },
  methods: {
    callMethod: function() {
      this.counter++
    },
    lesstThan3Method: function() {
      this.log += 'methodが呼ばれました<br>'
      return this.counter > 3 ? ' > 3 ' : ' <= 3 '
    }
    //lesstThan3Methodが無駄に呼ばれることを阻止したい。
  }
}
</script>
