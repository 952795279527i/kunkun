<template>
    <div class="TheadNav">
        <div class="TheadNav1" >
          <span class="TheadNav-zuo">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1024 1024"><path fill="currentColor" d="M609.408 149.376 277.76 489.6a32 32 0 0 0 0 44.672l331.648 340.352a29.12 29.12 0 0 0 41.728 0 30.592 30.592 0 0 0 0-42.752L339.264 511.936l311.872-319.872a30.592 30.592 0 0 0 0-42.688 29.12 29.12 0 0 0-41.728 0z"></path></svg>
        </span>
        <ul>
        <li 
        v-for="(item,index) in nav_users1"
        :class="{ active:item.pattern.state }"
        :key="index"
        @click="changeCon(item)"
        >{{item.pattern.platform}}</li>
        </ul>
        <span class="TheadNav-you">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1024 1024"><path fill="currentColor" d="M340.864 149.312a30.592 30.592 0 0 0 0 42.752L652.736 512 340.864 831.872a30.592 30.592 0 0 0 0 42.752 29.12 29.12 0 0 0 41.728 0L714.24 534.336a32 32 0 0 0 0-44.672L382.592 149.376a29.12 29.12 0 0 0-41.728 0z"></path></svg>
        </span>
        </div>
    </div>
  </template>
  
  <script>
  import dataList from './data.json'
  export default {
    name: 'TheadNav',
    components: {
  },
    data(){
        return {
          users:[],
          nav_users:[],
          nav_users1:[],
        }
      },
      methods:{
        changeCon(item){
          item.pattern.state = !item.pattern.state
          this.nav_users1.forEach((listItem) => {
            listItem.pattern.state = (listItem.pattern === item.pattern);
        });
         let filteredArray = this.nav_users1.filter((place)=>{
          return place.pattern.state === true;
        })
       this.$bus.$emit('changeCon',filteredArray)
        }
      },
      mounted(){
        this.users = dataList
        this.users[0].tag_nameson.filter((item)=>{
          this.nav_users.push(item)
        })
        this.users.filter((item)=>{
          this.nav_users.unshift(item)
        })
        const ser = document.querySelector(".TheadNav").clientWidth
        if (ser == 1000) {
          this.nav_users1=(this.nav_users.slice(0,13))
        }
      }
  }
  </script>
  
  <style>
.TheadNav{
    width: 100%;
    height: 60px;
    border-bottom: 1px solid #252527;
    margin-bottom: 8px;
}
.TheadNav1{
  width: 96%;
  height: 45px;
  margin: 0 auto;
  border-bottom: 3px solid #414243;
}
.TheadNav1 ul{
  width: 95%;
  height: 48px;
  line-height: 45px;
  float: left;
  display: flex;
  /* overflow: hidden; */
}
.TheadNav1 ul li{
  list-style: none;
  color: #fff;
  font-size: 14px;
  margin:0 18.5px;
  cursor: pointer;
}
.TheadNav1 ul li:hover{
  color:#1a82ff
}
.TheadNav-zuo{
  width: 20px;
  height: 45px;
  float: left;
  color: #8d8f95;
}
.TheadNav-zuo svg,.TheadNav-you svg{
  width: 12px;
  height: 12px;
  margin: 16px 0;
}
.TheadNav-you{
  width: 20px;
  height: 45px;
  float: right;
  color: #8d8f95;
}
.active{
  border-bottom: 3px solid #1a82ff;
  color:#1a82ff !important;
}
  </style>