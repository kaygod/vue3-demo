<template>
    <div class="Product">
          <p class="title">{{title}}</p>
            <div class="item" v-for="item in list" :key="item.id" @click="inquire(item)">
                <p class="item_top box">
                    <i class="lt">{{item.name}}</i>
                    <i class="gt">{{item.price}}</i>
                </p>
                <p class="item_bottom">{{item.desc}}</p>
            </div>
    </div>
</template>
<script>
import { computed } from "vue";

export default {
   props:{
       items:Object
   }, 
   setup(props,context){     
       const title = computed(()=>{   
        return props.items?props.items.title:"";
       })
       const list = computed(()=>{
           return props.items?props.items.data:[];
       })
       function inquire(item){
         context.emit("inquire",item);
       }
       return {
           title,
           list,
           inquire
       }
   }
}
</script>
<style lang="scss" scoped>
    .Product{
      box-sizing: border-box;
      padding-left: 10px;
      padding-right: 10px;
      margin-top: 40px;
      .title{
        margin-bottom: 10px;
        font-size: 16px;
      }
      .item {
         height: 60px;
         box-sizing: border-box;
         border-bottom: 1px solid #eee;
         font-size: 13px;
         color: #005aa0;
         cursor: pointer;
         padding-top: 10px; 
         &:nth-child(2){
          border-top: 1px solid #eee;
         } 
        .item_bottom{
           margin-top: 5px;
        }
      }    
    }
</style>
