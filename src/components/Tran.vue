<template>
     <transition-group appear 
          name="animate__animated animate__bounce"
          enter-active-class="animate__swing"
          leave-active-class="animate__backOutUp">
        <h1 v-show="!isShow" key="1" @click="show">你好啊！</h1>
        <h1 v-show="isShow" key="2" @click="show">莫菲特</h1>
  </transition-group>
  </template>
  
  <script>
  import 'animate.css';
  export default {
    name: 'Tran',
    data(){
      return {
        isShow: true,
      }
    },
    methods:{
        show(){
            this.isShow=!this.isShow
        }
    },
    props: {
      msg: String
    },
  }
  </script>
  <style scoped> .hello-enter-active{
    animation: hello 3s linear;
  }
  .hello-leave-active{
    animation: hello 3s linear reverse;
  }
  @keyframes hello {
    from{
      transform: translateX(-100%);
    }
    to{
      transform: translateX(0px);
    }
  }
  </style>
  