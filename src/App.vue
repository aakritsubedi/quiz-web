<template>
  <div id="app">
    <quiz-main v-bind:points="points" v-bind:message="message"></quiz-main>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import quizMain from './components/quizMain.vue';

export default {
  components: {
    'quiz-main': quizMain
},
  data(){
    return{
      points:20,
      message:"This is the Section For Messages"
    }
  }
}
</script>

<style>
.bg-nav{
    background: #DA4453;
    background: -webkit-linear-gradient(to right,#89216B, #DA4453);
    background: linear-gradient(to right,#89216B, #DA4453);
}
</style>
