<template>
  <div class="home">
    <ul>
      <li v-for="item in banner" :key="item.id">
        {{item.id}}--{{item.title}}<br>
        <img :src="item.img_url" alt=""></li>
    </ul>
  </div>
</template>

<script>
// @ is an alias to /src
import { onMounted, ref } from 'vue';
import { getHomeAllData } from "../network/home.js";
export default {
  name: 'Home',
  setup(){
    const banner = ref([]);
    onMounted(()=>{
      
      getHomeAllData().then(res=>{
        banner.value = res.slides;
        console.log(res.slides);
      }).catch(err=>{

      })
    })
    return {
      banner
    }
  },
  components:{

  }
}
</script>
