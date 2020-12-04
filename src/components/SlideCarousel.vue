<template>
  <div>
   <div class="flex flex-wrap w-full relative">
  <div class="absolute w-full" v-for="(color,index) in colors" :key="color">
    <transition name="fade">
      <div v-if="count==index" :class="color" style="height:350px">
    </div>
    </transition>
    
  </div>
  <div class="w-full" style="height:345px">
      <div class="absolute bottom-0 flex w-full justify-center">
        <div @click="makeActive(index)" v-for="(color,index) in colors" :key="color" :class="count==index?'bg-gray-600':'bg-yellow-800'" class="rounded-full h-4 w-4 mx-2 cursor-pointer"></div>
      </div>
      
  </div>

</div>

  </div>
</template>

<script>
export default {
  name: 'SlideCarousel',
  props: {
    msg: String
  },
  data(){
    return{
      count:0,
      interval:"",
      colors:["bg-purple-600","bg-green-800","bg-pink-700"],
    }
  },
  methods:{
    makeActive:function(index){
      this.count=index;
    }
  },
  mounted(){
    this.interval=setInterval(()=>{
      this.count==2?this.count=0:this.count++;
      }, 2000);
  },
  beforeUnmount(){
    clearInterval(this.interval);
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

.fade-enter-active,
.fade-leave-active {
  transition: all 1s ease;
}

.fade-enter-from{
  opacity: 0;
  transform:translateX(-100%);
}
.fade-leave-to {
  opacity: 0;
  transform:translateX(100%);
}
</style>
