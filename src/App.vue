<template>
  <div id="app" class="wrapper">
    <div class="title">Cut A Panel</div>

    <DoorType :type="doorType" :num="numOfDoors" @handleDoorTypeChange="doorTypeChanged" @handleDoorNumChange="doorNumChanged"/>
    <HingeType :type="hingeType" @handleHingeChange="hingeChanged" :doorType="doorType" />

    <div v-if="!calc">
      <Dimensions :inputWidth="width" :inputHeight="height" @handleWidthChange="widthChanged" @handleHeightChange="heightChanged"/>

      <div class="section">
          <input type="button" value="Calculate" class="calculate" @mouseup="calc = {}">
      </div>
    </div>
    
    <Cut v-else :width="width" :height="height" :numOfDoors="numOfDoors" :hingeType="hingeType" @back="handleBack"/>

    <input type="button" value="Reset" class="calculate">
  </div>
</template>

<script>
import DoorType from "./components/DoorType"
import HingeType from "./components/HingeType"
import Dimensions from "./components/Dimensions"
import Cut from "./components/Cut"

export default {
  name: 'Cut-A-Panel',
  components: {
    DoorType,
    HingeType,
    Dimensions,
    Cut
  },
  data(){
    return{
      doorType: "Rear",
      numOfDoors: 2,
      hingeType: "Standard",
      width: null,
      height: null,
      calc: null
    }
  },
  methods:{
    doorTypeChanged: function(val){
      if(val == "Rear" && this.numOfDoors < 2){
        this.numOfDoors = 2
      }

      if(val == "Side"){
        this.numOfDoors = 1
      }
      
      this.doorType = val
    },

    doorNumChanged: function(val){
      this.numOfDoors = val
    },

    hingeChanged: function(val) {
      this.hingeType = val
    },

    widthChanged: function(val) {
      this.width = val
    },

    heightChanged: function(val) {
      this.height = val
    },

    handleBack: function() {
      this.calc = null
    }
  }
}
</script>

<style>
  *{
    margin: 0;
    padding: 0;
  }

  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    
    font-size: 120%;

    background-image: linear-gradient(180deg, #EEE, #CCC)
  }

  .section{
      margin: 15px 0px 0px 0px;
      max-width: 600px;
  }

  .calculate{
    font-size: 150%;
    width: 80%;
    padding: 10px;
    border-radius: .5em;

    background-image: linear-gradient(180deg, #99F, #66E);
    color: aliceblue;

    min-height: max-content;

    margin-bottom: 10px;
  }
  
  .calculate:active{
    background-image: linear-gradient(180deg, #66C, #33B);
  }
  
  .title{
    margin-top: 20px;
    font-size: 180%;
    font-weight: bold;
  }

  .wrapper{
    display: flex;
    flex-flow: column nowrap;
    height: 100vh;
    
    align-items: center;
  }
</style>
