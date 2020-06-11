<template>
  <div class="home">
    <Header/>
    <Product :items="likes" @inquire="inquire"/>
    <Product :items="recommends" @inquire="inquire"/>
  </div>
</template>

<script>
// @ is an alias to /src
import Header from '@/components/Header.vue'
import axios from 'axios';
import { ref,onMounted } from "vue";
import Product from "../components/Product";

export default {
  name: 'Home',
  components: {
    Header,
    Product
  },
  setup(){
      const { likes,recommends } = useData();

      function inquire(data){
        const {name,price} = data;
        alert(`今天${name}的价格是${price}元`);
      }

      return {
        likes,
        recommends,
        inquire
      }
  }
}

function useData(){
 let likes = ref({});
 let recommends = ref({});

 onMounted(() => {
   init();
 })

 function init(){
    return new Promise((resolve)=>{
      axios.get('/api/home').then((data)=>{
       const result = data.data; 
       likes.value =  result.likes;
       recommends.value = result.recommends;
      })
    })
  }

  return {
    likes,
    recommends
  }  
  
}
</script>
