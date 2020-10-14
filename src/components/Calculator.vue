<template>
  <div class="Calculator">
    <div id="cal-title">
      <h1>{{ msg }}</h1>
    </div>

    <div id="main-cal">
      <div id="input-div">
        <input id="input-string" v-model='calString'><br>
        <button @click="append('+')">+</button>
        <button @click="append('-')">-</button>
        <button @click="append('*')">*</button>
        <button @click="append('/')">/</button>
        <button @click="getTotalResult">=</button>
        <button id='clear-button' @click="clear">Clear</button>
      </div>
    </div>

    <div id="cal-result">
      <div id="result-div">
        <span>Result: </span>
        <span>{{ total }}</span>
      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: 'Calculator',
  props: {
    msg: String
  },
  data(){
    return{
      tmpResult:'',
      calString:'',
      total:0
    }
  },
  methods:{
    append(value){
      this.calString += value.toString()
    },
    getTotalResult(){
      if(this.calString != '' && this.calString != undefined){
        if(!isNaN(this.calString.slice(-1))){
          this.total = eval(this.calString)
        }
        else{
          this.total = eval(this.calString.slice(0,-1))
        }
      }

    },
    clear(){
      this.calString = ''
      this.tmpResult = ''
      this.total = 0
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

h1{
  margin-block-start: 0em;
  margin-block-end: 0em;
}

h3 {
  margin: 40px 0 0;
}
input{
 height:35px;
 width: 245px;
 border: 2px solid darkblue;
}
button{
  font-size: medium;
  background-color: darkblue;
  height: 11%;
  width: 5%;
  margin: 6px 2px 9px 4px;
  color: white;
  border: 0px;
}
#clear-button{
  width:8% !important;
}
#cal-title{
  background-color: darkblue;
  color: white;
  font-weight: bolder;
  font-family: cursive;
  height: 38Px;
}
#main-cal{
  border-radius: 10px;
  border: 1px solid darkblue;
  width: 50%;
  position: absolute;
  left: 0;
  top: 14%;
  right: 0;
  margin: auto;
  height: 20%;
}
#cal-result{
  border-radius: 10px;
  border: 1px solid darkblue;
  width: 50%;
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  margin: auto;
  height:15%;
  
}
#input-div{
  position: absolute;
  margin-top: 20px;
  left: 0;
  right: 0;
  height: 261px;
}
#result-div{
  position: absolute;
  margin-top: 35px;
  left: 0;
  right: 0;
}
</style>
