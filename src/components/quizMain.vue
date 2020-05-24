<template>
    <div>
      <div class="card mt-100">

      <div class="announcement">
        <h1>{{points}}</h1>
      </div>
    </div>

      <div class='message'>
          <h3 class="text-light">{{message}}</h3>
      </div>  
        
      <input type="button" class="button Replay" value="Replay" v-on:click="showReplayMsg"/>
      <input type="button" class="button Category" value="Category" v-on:click="showCategoryMsg"/>

    </div>
</template>

<script>
export default {
    props:{
      points:{
        type:Number 
      },
      message:{
        type:String
      }
    },
    data(){
      return{
   
      }
    },
    methods:{
      showReplayMsg:function(){
        this.message = 'This is replay Message'
      },
      showCategoryMsg:function(){
        this.message = 'This is category Message'
      }
    }
}
</script>

<style scoped>
.button {
  background-color: blueviolet;
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  border-radius: 15px;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  margin-top: 50px;
  cursor: pointer;
}

.Replay{
  margin-left: 200px;
}

.Category{
  margin-left: 628px;
}

.message{
  margin-top: 20px;
  margin-left: 200px;
  margin-right: 210px;
  text-align: center;
  font-size: 25px;
  color: #fff;
  border: 1px solid black;
  background: linear-gradient(rgb(233, 141, 104), rgb(110, 54, 110), rgb(48, 8, 25));
}

h1 {
  font-size: 60px;
}
h3 {
  font-size: 26px;
}

.italic {
  font-style: italic;
}

.card {
  position: relative;
  margin: auto;
  margin-top: 50px;
  height: 350px;
  width: 600px;
  text-align: center;
  background: linear-gradient(#E96874, #6E3663, #2B0830);
  border-radius: 10px;
  box-shadow: 0 6px 12px -3px rgba(0,0,0,.3);
  color: #fff;
  padding: 30px;
}

.card header {
  position: absolute;
  top: 31px;
  left: 0;
  width: 100%;
  padding: 0 10%;
  transform: translateY(-50%);
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  align-items: center;
}

.card header > *:first-child {
  text-align: left;
}
.card header > *:last-child {
  text-align: right;
}

.announcement {
  position: relative;
  border: 3px solid currentColor;
  border-top: 0;
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

h1, h2, h3, h4 {
  margin: .15em 0;
}

div{
  border-radius: 20px;
}

</style>