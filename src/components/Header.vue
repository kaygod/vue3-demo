<template>
 <div class="header">
     {{title}}
    <a class="login">登录</a>
 </div>
</template>
<script> 
  export default {
     props:{
         title:{
             type:String,
             default:"首页"
         }
     }
  }
</script>
<style lang="scss" scoped>
 .header{
    width: 100%;
    height: 70px;
    border-bottom: 1px solid #eee;
    font-size: 18px;
    color: #333;
    text-align: center;
    line-height: 70px;
    position: relative;
    .login{
            position: absolute;
    right: 20px;
    top: 2px;
    font-size: 14px;
    color: #005aa0;
    }
 }
</style>
