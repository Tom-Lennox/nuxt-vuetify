<template>
  <!-- 
    会社で行ったこと
    基本、パーツごとに分けてslackに保存。tipsとして使用できるようにする。
    jQueryのfadeIn()のようなものでいい感じにグラデーションを点滅させたい。

     ■ Vue　codeを表示したいのだが
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
      <p :class="{green: true, 'lighten-1': true}">classをbindして複数スタイルを適用する。(true or false)</p>
      <p :class="{red: toggleColor, 'lighten-3': toggleColor}">
        <v-btn @click="toggleColor = !toggleColor">toggleColor ⇒</v-btn>classをbindして複数スタイルを適用する。(変数を指定)
      </p>
      <!--  -->
      <p :class="classObject">
        <v-btn @click="toggleColor = !toggleColor" :class="classObject">toggleColor ⇒</v-btn>classをbindして複数スタイルを適用する。(変数を指定)
      </p>
      <p>この場合はcomputedからreturnするように組めば良い。</p>
      <p>this.を忘れずに。</p>
      <!--  -->
      <p>下これでcolor属性のバインドができる。</p>
      <v-btn :color="toggleColor ? 'purple' : ''"></v-btn>
      <!-- 30-1 -->
      <p :class="[textColor, bg]">[30-1]classを動的に。</p>
      <!-- 30-2 -->
      <!-- 
        配列内ではcssをtfで切り替え。
        data内でclass名を指定して切り替えはできない？
      -->
      <p :class="[{'bg-blue': toggleColor}]"></p>
      <p :class="[{red: toggleColor}, 'lighten-3']">
        <v-btn @click="toggleColor = !toggleColor">toggleColor ⇒</v-btn>[30-2]classを動的に2。
      </p>
      <!-- 31-1 -->
      <p :style="{color: textColor}">[31-1]styleを変数で指定</p>
      <!-- 32 -->
      <p :style="{color: textColor, background: bgColor}">[32]styleをobjectで指定</p>
      <!--  -->
      <!-- 33-1（独自） -->
      <p :style="[pText, pBackground]">[33-1（独自）]styleを複数objectで指定（compuredでreturn）</p>
      <!-- 33-2 -->
      <p :style="[pText02, pBackground02]">[33-2]styleを複数objectで指定（data指定）</p>
      <p>この場合はdataプロパティに変数は使用できない？</p>
      <p>x color: this.textColor,</p>
      <p>o color: 'red',</p>
      <!-- 34, 35, 36 -->
      <p v-if="showVif % 3 === 0">v-if = true</p>
      <p v-else-if="showVif % 3 === 1">v-else-if = true</p>
      <p v-else>v-else = true</p>
      <v-btn @click="plus">+1</v-btn>
      <!--  -->
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
      toggleColor: false,
      textColor: 'red',
      bg: 'bg-blue',
      bgColor: 'blue',
      pText02: {
        color: 'red',
        'font-size': '2rem'
      },
      pBackground02: {
        background: 'blue'
      },
      showVif: 0
    }
  },
  computed: {
    classObject: function() {
      return {
        red: this.toggleColor,
        'lighten-3': this.toggleColor
      }
    },
    pText: function() {
      return {
        color: this.textColor,
        'font-size': '2rem'
      }
    },
    pBackground: function() {
      return {
        background: this.bgColor
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
