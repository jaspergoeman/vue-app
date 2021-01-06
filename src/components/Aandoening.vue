<script>
import aandoening from "../assets/data/aandoening.json";
import antibioticas from "../assets/data/antibioticas.json";

export default {
  name: "Aandoening",
  props: ["selectedAandoening"],

  data: () => {
    return {
      aandoening: aandoening,
      antibioticas: antibioticas,
      selectedAntibioticas: [],
      selectedAntibiotica: null
    };
  },
  methods: {
      getAntibioticas: function(){
          this.aandoening.forEach(a => {
              if(a.name === this.selectedAandoening){
                  this.selectedAntibioticas = a.antibiotica;
              }
          });
          return this.selectedAntibioticas;
      } ,
        getAntibiotica: function(name){
          this.antibioticas.forEach(a => {
              if(a.name === name){
                  this.selectedAntibiotica = a;
              }
          });
          return this.selectedAntibiotica;
      } ,
      close: function(){
          this.$emit('close', false);
      }
  },
};
</script>
<template>
  <div class="box">
      <div class="close"><a v-on:click="close()">close X</a></div>
      <div class="box-title"><h2>{{ selectedAandoening }}</h2></div>
      <div class="box-content">
          <div class="box-content-title"><h4>Variant 2</h4></div>
          <div class="box-columns">
          <div class="box-first">
              <div class="box-subtitle"><h5>Eerste keuze</h5></div>
              <div class="box-item" v-for="a in getAntibioticas()" :key="a">
                  <ul v-bind="getAntibiotica(a)" >
                      <li class="item-name">{{selectedAntibiotica.name}}</li>
                      <li class="item-dosis">{{selectedAntibiotica.dosis}}</li>
                      <li class="item-remark">{{selectedAntibiotica.remark}}</li>
                  </ul>
              </div>
          </div>
          <div class="box-second"><div class="box-subtitle"><h5>Tweede keuze</h5></div></div>
          <div class="box-third"><div class="box-subtitle"><h5>Alergie</h5></div></div>
      </div>
      </div>
      </div>
</template>
<style lang="scss" scoped>
@import '../scss/Variables.scss';
.box{
    position: absolute;
    padding:   20rem calc(40vw /2);
    background: rgba(0, 0, 0, 0.7);
    top: 0;
    overflow: hidden;
    background-size: cover;
    &-title{
        position: relative;
        background-color: $color-white;
        width: 60vw;
        text-align: center;
        color: $color-primary;
        text-transform: uppercase;
        font-size: 1.4rem;
        padding:  1rem 0;
        h2{
        margin: 0;}
    }
    &-content{
        background-color: $color-white;
        width: 60vw;
            box-sizing: border-box;
    padding: 5rem 2rem;
    outline: 2px solid $color-secondary;
    outline-offset:  -2rem;
    
    }
    &-columns{

        display: flex;
        justify-content: space-between;
        margin-left: 2rem;
        margin-right: 4rem;
    }
    &-subtitle{
        font-size: 1.4rem;
        color: $color-grey;
    }
    &-content-title{
        margin-top: -3.1rem;
        margin-left: -.1rem;
        margin-right: -.1rem;
        height: 4rem;
        background-color: $color-secondary;
        display: flex;
        align-content: center;
        h4{
            margin:0;
            font-size: 1.4rem;
            margin-top: 1.3rem;
            margin-left: 2rem;
        }
    }
    &-item{
        margin-bottom: 2rem;
    }
    &-item:last-child{
        margin-bottom: 0;
    }
}
.item{
    &-name{
        font-weight: 500;
    }
    &-remark{
        font-style: italic;
        color: goldenrod;
    }
    &-dosis{
        font-weight: 300;
    }
}
.close{
       display: flex;
    justify-content: flex-end;
    padding-right: 1.4rem;
    padding-top: .6rem;
    background: $color-white;
}
</style>