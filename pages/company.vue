<template>
  <!-- 
    会社で行ったこと
    基本、パーツごとに分けてslackに保存。tipsとして使用できるようにする。
    jQueryのfadeIn()のようなものでいい感じにグラデーションを点滅させたい。
  -->
  <v-layout>
    <v-flex class="text-left">
      <p>
        <v-btn @click="plus">+1</v-btn>
        {{counter}}
      </p>
      <p>
        <v-btn outlined :loading="aaa" @click="aaa = !aaa">Continue</v-btn>
      </p>29
      <p :class="{red: true, 'lighten-3': true}">classをbindして複数スタイルを適用する。(true or false)</p>
      <p :class="{red: toggleColor, 'lighten-3': toggleColor}">
        <v-btn @click="toggleColor = !toggleColor">toggleColor ⇒</v-btn>classをbindして複数スタイルを適用する。(変数を指定)
      </p>
      <!--  -->
      <p :class="classObject">
        <v-btn @click="toggleColor = !toggleColor" :class="classObject">toggleColor ⇒</v-btn>classをbindして複数スタイルを適用する。(変数を指定)
      </p>
      <!--  -->
      <p>下これでcolor属性のバインドができる。</p>
      <v-btn :color="toggleColor ? 'purple' : ''"></v-btn>
      <p>この場合はcomputedからreturnするように組めば良い。</p>
      <p>this.を忘れずに。</p>
      <blockquote class="blockquote">
        <footer>
          <small>
            <!-- <v-btn outline round :class="{green: true, 'green-text': true, 'darken-2': ture}">John Johnson</v-btn> -->
            <pre :style="dataText">{{$data}}</pre>
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
      sa: 'aaaa',
      counter: 0,
      dataText: {
        'text-align': 'left',
        border: '1px solid #fff',
        padding: '20px'
      },
      aaa: false,
      toggleColor: false
    }
  },
  computed: {
    classObject: function() {
      return {
        red: this.toggleColor,
        'lighten-3': this.toggleColor
      }
    }
  },
  methods: {
    plus: function() {
      this.counter++
    }
  },
  watch: {
    counter: function() {
      let vm = this
      setTimeout(function() {
        vm.counter = 0
      }, 1000)
    },
    aaa: function() {
      let vm = this
      setTimeout(function() {
        console.log('stu')
        vm.aaa = false
      }, 1000)
    }
  }
}
</script>
<style>
.red {
  color: red;
}
.bg-blue {
  background-color: blue;
}
</style>
