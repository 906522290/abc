<template>
  <div >
    <span @click='select(`大连`)'>大连</span>
  </div>
</template>

<script>
export default {
      name:'TrainCity',
  methods:{
     select(val) {
       let data = {
         cityname: val
       };
       alert(data.cityname);
       this.$emit('showCityName',data);//select事件触发后，自动触发showCityName事件
     }
   }
}
</script>
