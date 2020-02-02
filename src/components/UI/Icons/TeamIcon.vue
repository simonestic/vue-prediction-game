<template>

<span class="iconHolder">
    
  <img v-if="need==='titans'" src="../../../assets/images/titans.png" alt="">
  <img v-if="need==='patriots'" src="../../../assets/images/patriots.png" alt="">
  <img v-if="need==='ravens'" src="../../../assets/images/ravens.png" alt="">
  <img v-if="need==='steelers'" src="../../../assets/images/steelers.png" alt="">
  <img v-if="need==='chiefs'" src="../../../assets/images/chiefs.png" alt="">
  <img v-if="need==='chargers'" src="../../../assets/images/chargers.png" alt="">
  <img v-if="need==='bills'" src="../../../assets/images/bills.jpg" alt="">
  <img v-if="need==='texans'" src="../../../assets/images/texans.jpg" alt="">
  <img v-if="need==='vikings'" src="../../../assets/images/vikings.jpg" alt="">
  <img v-if="need==='saints'" src="../../../assets/images/saints.jpg" alt="">
  <img v-if="need==='49ers'" src="../../../assets/images/fniners.png" alt="">
  <img v-if="need==='packers'" src="../../../assets/images/packers.jpg" alt="">
  <img v-if="need==='lions'" src="../../../assets/images/lions.jpg" alt="">
  <img v-if="need==='hawks'" src="../../../assets/images/hawks.png" alt="">
  <img v-if="need==='eagles'" src="../../../assets/images/eagles.png" alt="">

</span>

</template>

<script>

export default {
  name: 'TeamIcon',
  props: {
    need: String,
  },
};

</script>

<style scoped>
  .iconHolder{        
    width: 20px;
    height: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .iconHolder img{
    width: 100%;
    height: 100%;
  }
</style>
