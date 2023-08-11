<template>
    <div class="mod">
      事件<input type="text" gainval="getval" v-model="gin"><br>
      <button @click="update">更新</button>
      <button>取消</button>
    </div>
   
  </template>
    
    <script>
  export default {
    name: 'ModiFication',
    data() {
      return {
        gin:""
      };
    },
    methods:{
        val(fun){
            this.gin = fun
        },
        update(){
            this.$bus.$emit('gitupdate',this.gin)
            this.gin=""
        }
    },
    mounted() {
        this.$bus.$on('gainval',this.val)
    },
  }
  </script>
    <style>
    </style>