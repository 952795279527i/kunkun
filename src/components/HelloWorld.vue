<template>
  <div class="hello">
    <ul class="ul_1">
      <li v-for="(star,i) in dataList" :key="i" gitName="fun" @click="getval(i)">{{ star }} <el-button type="danger" icon="el-icon-delete" circle @click="del(i)"></el-button></li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data(){
    return {
      dataList:["吃饭","在吃饭","睡觉"],
      ser:null
    }
  },
  props: {
    msg: String
  },
  methods:{
    del(i){
      this.dataList.splice(i,1);
    },
    getval(i){
      this.$bus.$emit('gainval',this.dataList[i])
      this.ser = i
      console.log(this.ser);
    },
    update(i) {
      // this.dataList[this.ser]= i
      this.$set(this.dataList, this.ser, i);//在this.update方法中使用Vue.set或者this.$set方法来更新this.dataList，Vue会检测到数据的变化，并重新渲染相关的DOM。
      console.log(this.dataList);
    },
  },
  mounted(){
    console.log(this.dataList);
    this.$bus.$on('gitName', (Newval) => {
    this.dataList.push(Newval);
  }),
  this.$bus.$on('gitupdate',this.update)
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.ul_1{
  width: 200px;
  height: 100%;
  margin: 0 auto;
}
li{
  width: 200px;
  list-style: none;
  cursor: pointer;
}
</style>
