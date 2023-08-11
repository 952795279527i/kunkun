<template>
  <div class="demo">
     <input type="text" placeholder="请输入" v-model="val" @keyup.enter="addList">
  </div>
 
</template>
  
  <script>
export default {
  name: 'DemoList',
  data() {
    return {
      val:""
    };
  },
  methods:{
    addList(){
      this.$bus.$emit('gitName',this.val)
      this.val = ""
    }
  },
}
</script>
  <style>
  </style>