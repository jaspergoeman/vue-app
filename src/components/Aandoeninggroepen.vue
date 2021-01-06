<script>
import aandoeningen from "../assets/data/aandoeninggroepen.json";
import Aandoening from './Aandoening';

export default {
  name: "Aandoeninggroepen",
  props: ["selectedTopic", "selectedSubgroup", "doelgroep"],

  data: () => {
    return {
      aandoeningen: aandoeningen,
      selectedAandoening: "",
      showAandoening: false
    };
    
  },
  components: {
        Aandoening
    },
  methods: {
    show: function (aandoening) {
     this.selectedAandoening = aandoening;
     this.showAandoening = !this.showAandoening;
     console.log(this.showAandoening);
    },
    close(){
        this.showAandoening = false;
        console.log(this.showAandoening);
    }
  } 
};
</script>
<template>
  <section class="App-section">
    <div class="App-container App-container--xl">
      <div v-for="a in aandoeningen" :key="a.name">
        <div
          v-if="
            a.doelgroep === doelgroep &&
            a.topics.includes(selectedTopic) &&
            a.subgroups.includes(selectedSubgroup)
          "
        >
          <div class="card">
            <div class="card-title">
              {{ a.name }}
            </div>
            <div class="card-content">
                <ul class="card-content-list" >
                    <li v-for="aandoening in a.aandoeningen" :key="aandoening"><a v-on:click="show(aandoening)">{{aandoening}}</a></li>
                </ul>
                    
            </div>
          </div>
        </div>
        
      </div>
    </div>
    <div v-if="showAandoening">
      <Aandoening :selectedAandoening="selectedAandoening" @close="close"/>
  </div>
  </section>
  
</template>
<style lang="scss" scoped>
@import "../scss/Variables.scss";

.card {
  display: block;
  width: calc(33.3% - 15px * 2);
  margin: 15px;
  border: 2px solid $color-light;
  &-title {
    color: $color-primary;
    font-size: 1.5rem;
    font-weight: 700;
    background-color: #e9f1fc;
    padding: 1rem;
  }
  &-content{
      display: flex;
  }
  &-content-list{
      padding: 1rem;
      li {
          a{
              text-decoration: none;
                font-size: 1.2rem;
                word-break: break-all;
                color: #565656;
          }
      }
  }
  &-show{
      position: absolute;
      top: 0;
      left: 50;
      background-color: red;
  }
}
</style>