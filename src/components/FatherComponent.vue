<template>
  <div>
    <h1>父组件2222</h1>
    <TrainCity  @showCityName="updateCity" :index="goOrtoCity"></TrainCity>
  </div>
</template>

<script>
  import TrainCity from './TrainCity.vue'
  export default {
    name:'FatherComponent',
    components: {
      TrainCity
    },
    data () {
      return {
        toCity:"北京"
      }
    },
    methods:{
      updateCity(data){
        this.toCity = data.cityname;
        console.log('toCity:'+this.toCity)
        alert(this.toCity)
      }
    }
  }
</script>
