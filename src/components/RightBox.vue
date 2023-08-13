<template>
    <div class="RightBox">
        <div class="head_nav">
            <img :src="this.infor.image">
            <span class="fo">{{this.infor.name + "·热搜榜"}}</span>
            <span class="spaSvg"><svg data-v-d7b5176e="" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1024 1024"><path fill="currentColor" d="M512 64a448 448 0 1 1 0 896.064A448 448 0 0 1 512 64zm67.2 275.072c33.28 0 60.288-23.104 60.288-57.344s-27.072-57.344-60.288-57.344c-33.28 0-60.16 23.104-60.16 57.344s26.88 57.344 60.16 57.344zM590.912 699.2c0-6.848 2.368-24.64 1.024-34.752l-52.608 60.544c-10.88 11.456-24.512 19.392-30.912 17.28a12.992 12.992 0 0 1-8.256-14.72l87.68-276.992c7.168-35.136-12.544-67.2-54.336-71.296-44.096 0-108.992 44.736-148.48 101.504 0 6.784-1.28 23.68.064 33.792l52.544-60.608c10.88-11.328 23.552-19.328 29.952-17.152a12.8 12.8 0 0 1 7.808 16.128L388.48 728.576c-10.048 32.256 8.96 63.872 55.04 71.04 67.84 0 107.904-43.648 147.456-100.416z"></path></svg></span>
        </div>
        <ul class="journa">
            <li v-for="(item,index) in this.infor.search"
            >
                <span>{{item.index}}</span>
                <span>{{item.title}}</span>
                <span>{{ item.hotValue }}</span>
            </li>
        </ul>
    </div>
  </template>
  
  <script>
  export default {
    name: 'RightBox',
    data(){
        return {
            infor:[]
        }
      },
      methods:{
        alters(infor){
            this.infor = infor;
            console.log(this.infor);
        }
      },
      mounted(){
        this.$bus.$on('changeColumn',this.alters)
       
      }
  }
  </script>
  
  <style>
.RightBox{
    width: 75.9%;
    min-width: 100px;
    height: calc(97% - 110px);
    float: left;
}
.head_nav{
    width: 100%;
    height: 45px;
    border-bottom: 1px solid #252527;
}
.head_nav img{
    width: 20px;
    height: 20px;
    border-radius:50% ;
    margin: 11px ;
    float: left;
}
.fo{
    font-size: 19px;
    height: 40px;
    float: left;
    display: block;
    line-height: 40px;
    color: #fff;
}
.spaSvg svg{
    width: 16px;
    height: 16px;
    margin: 14px;
    float: right;
}
.journa li{
    width: 100%;
    height: 35px;
    margin-bottom:10px ;
    list-style: none;
}
.journa li span:first-child{
    display: block;
    background-color: #ccc;
}
.journa li span:nth-child(1){
    width: 22px;
    height: 22px;
    border-radius: 5px;
    margin: 6px 10px;
    /* background-color: red; */
    color: #fff;
   float: left;
}
.journa li span:nth-child(2){
   float: left;
   line-height: 35px;
   font-size: 13px;
   color: #cccccd;
}
.journa li span:nth-child(3){
   float: right;
   line-height: 35px;
   font-size: 12px;
   color: #cccccd;
   margin-right: 10px;
}
.journa li:hover span:nth-child(2){
    color: #1985ea;
}
.journa li:first-child span:nth-child(1){
    background-color: #fe2d46;
}
.journa li:nth-child(2) span:nth-child(1){
    background-color: #f60;
}
.journa li:nth-child(3) span:nth-child(1){
    background-color: #faa90e;
}
  </style>