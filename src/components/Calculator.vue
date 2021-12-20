<template>
<div id="app">
  <div class="calculator">
    <div class="in" type='text' placeholder="0">{{prev}}</div>
    <div class="num">
      <button v-on:click="input(numb)" :value="numb" class="number_button1" v-for="numb in number" :key="numb.id">{{numb}}</button>
      <button v-on:click="sign()" class="number_button1">+/-</button>
      <button v-on:click="decimal()" class="number_button1">.</button>
    </div>
    <div class='operat'>
      <button v-on:click="sum()" class="nu">+</button>
      <button v-on:click="mult()" class="nu">-</button>
      <button v-on:click="divide()" class="nu">/</button>
      <button v-on:click="sub()" class="nu">*</button>
    </div>
    <div class="bot-pan">
      <button v-on:click="reset()" @keydown.backspace="reset()" class="outc">C</button>
      <button v-on:click="cal()" v-on:keydown.enter="cal()" class="outc">=</button>    
    </div>
  </div>
</div>
</template>

<script>

export default {
  name: 'Calculator',
  data: function() {
  return {
      result:'',
      number: [1,2,3,4,5,6,7,8,9,0],
      operationClick: false,
      prev:'',
      current:''
    };},
  methods:{
    input: function(numb){
      if(this.operationClick){
        this.prev='';
        this.operationClick = false;
      }
      this.prev+=numb;
    },
    decimal:function() {
      if (this.prev.indexOf('.') === -1) {
        this.input('.');
      }
    },
    reset: function(){
      this.prev='';
    },
    sign:function() {
      this.prev =
        this.prev < 0
          ? (this.prev = this.prev - this.prev * 2)
          : (this.prev = this.prev - this.prev * 2);
    },
    divide:function(){
      this.operator = (a,b) => a/b;
      this.current = this.prev
      this.operationClick=true
    },
    sub:function(){
      this.operator = (a,b) => a*b;
      this.current = this.prev
      this.operationClick=true
    },
    mult:function(){
      this.operator = (a,b) => a-b;
      this.current = this.prev
      this.operationClick=true
    },
    sum:function(){
      this.operator = (a,b) => a+b
      this.current = this.prev
      this.operationClick=true
    },
    cal:function(){
     this.prev=this.operator(Number(this.current), Number(this.prev))
     this.current=null
     this.operatorClicked = true;
     console.log(this.result)
    }
  }
}
</script>

<style scoped>
.bot-pan{
  float: left;
  width: 100%;
  height: 15%;
  display: flex;
  flex-wrap: wrap;
}
.outc:hover{
  background-color: rgb(36, 80, 41);
  color: white;
}
.nu:hover{
  background-color: rgb(36, 80, 41);
  color: white;
}
.number_button1:hover{
  background-color: rgb(36, 80, 41);
  color: white;
}
.outc{
  width: 13vw;
  height: 80%;
  border: none; 
  outline: none;
  margin: 0.3vw 0.1vw 0vw 0.2vw;
  border-radius: 3vw;
  font-size: 1.8vw;
}
.operat{
  display: block;
  height: 65%;
}
.nu{
  width: 6vw;
  height: 20%;
  border: none; 
  outline: none;
  margin: 0.3vw 0.1vw 0.7vw;
  border-radius: 3vw;
  font-size: 1.8vw;
}
.num{
  display: flex;
  flex-wrap: wrap;
  height: 65%;
  width: 76%;
  float: left;
}
.calculator{
  height: 30vw;
  width: 27%;
  padding: 1%;
  background-color: rgba(187, 230, 187, 0.856);
  border: solid 1px rgb(68, 119, 85);
  box-shadow: 0 0 2.5vw rgb(116, 177, 141);
}
.number_button1{
  width: 6vw;
  height: 20%;
  border: none; 
  outline: none;
  margin: 0.3vw;
  border-radius: 3vw;
  font-size: 1.8vw;
}
.in{
  font-size: 2.4vw;
  position: relative;
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
  top: 4%;
  left: 5%;
  height: 18%;
  width: 100%;
}
</style>
