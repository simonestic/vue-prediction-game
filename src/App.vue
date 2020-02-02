<template>
  <div id="app">    
    <BracketWeb v-show="showWeb"/>
    <BracketMobile v-show="!showWeb"/>
  </div>
</template>

<script>
import BracketWeb from './components/BracketWeb.vue'
import BracketMobile from './components/BracketMobile'

export default {
  name: 'app',
  components: {
    BracketWeb,
    BracketMobile
  },
  data(){
    return {
      showWeb: true,
      windowWidth: 0,
    }
  },
  mounted(){    
    this.$nextTick(function(){
      window.addEventListener("resize", this.checkWindowWidth);
      
      //init
      this.checkWindowWidth();
    })    
  },
  methods: {
    checkWindowWidth(){
      this.windowWidth = document.documentElement.clientWidth;      
      if(this.windowWidth <= 750){
        this.showWeb = false;
      }else{
        this.showWeb = true;
      }
    }
  },  
  beforeDestroy() {
    window.removeEventListener("resize", this.checkWindowWidth);
  },
}
</script>
