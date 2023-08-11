<template>
    <div class="nextick">
        <input ref="editInp" v-if="isEdit" type="text" v-model="msg">  
        <p v-else>{{msg}}</p>  
        <button @click="edit">编辑</button>  
    </div>
  </template>
    
    <script>
  export default {
    name: 'NextTick',
    data() {
      return {
        msg:'我天呀',  
        isEdit:false  
      };
    },
    methods:{  
    edit(){  
      this.isEdit = !this.isEdit;  
       this.$nextTick(function(){  
        this.$refs.editInp.focus();  
      });  
    }  
  },  
  }
  </script>
    <style>
    </style>