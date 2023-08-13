<template>
    <div class="LeftBox">
        <input type="text" placeholder="搜索" class="search_div">
        <ul>
            <li 
            v-for="(item,index) in msg" 
            :key="index"
            @click="changeColumn(item)"
            :class="{ actives:item.state }"
            >
                
                <div class="optionList">
                    <!-- <span class="spSvg"><svg data-v-d7b5176e="" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 24 24"><path d="M11 18c0 1.1-.9 2-2 2s-2-.9-2-2s.9-2 2-2s2 .9 2 2zm-2-8c-1.1 0-2 .9-2 2s.9 2 2 2s2-.9 2-2s-.9-2-2-2zm0-6c-1.1 0-2 .9-2 2s.9 2 2 2s2-.9 2-2s-.9-2-2-2zm6 4c1.1 0 2-.9 2-2s-.9-2-2-2s-2 .9-2 2s.9 2 2 2zm0 2c-1.1 0-2 .9-2 2s.9 2 2 2s2-.9 2-2s-.9-2-2-2zm0 6c-1.1 0-2 .9-2 2s.9 2 2 2s2-.9 2-2s-.9-2-2-2z" fill="currentColor"></path></svg></span> -->
                    <div class="platform" >
                        <img :src="item.image" width="20px" height="20px"><span> {{item.name}}</span>
                    </div>
                    <!-- <span class="spSvg1"><svg data-v-d7b5176e="" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1024 1024"><path fill="currentColor" d="M176 416a112 112 0 1 1 0 224 112 112 0 0 1 0-224zm336 0a112 112 0 1 1 0 224 112 112 0 0 1 0-224zm336 0a112 112 0 1 1 0 224 112 112 0 0 1 0-224z"></path></svg></span> -->
                    <span class="spSvg"><svg data-v-d7b5176e="" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 576 512"><path d="M528.1 171.5L382 150.2L316.7 17.8c-11.7-23.6-45.6-23.9-57.4 0L194 150.2L47.9 171.5c-26.2 3.8-36.7 36.1-17.7 54.6l105.7 103l-25 145.5c-4.5 26.3 23.2 46 46.4 33.7L288 439.6l130.7 68.7c23.2 12.2 50.9-7.4 46.4-33.7l-25-145.5l105.7-103c19-18.5 8.5-50.8-17.7-54.6zM388.6 312.3l23.7 138.4L288 385.4l-124.3 65.3l23.7-138.4l-100.6-98l139-20.2l62.2-126l62.2 126l139 20.2l-100.6 98z" fill="currentColor"></path></svg></span>
                </div>
               
            </li>
        </ul>
    </div>
  </template>
  
  <script>
  export default {
    name: 'LeftBox',
    data(){
        return {
            msg:[],
            dataList:[]
        }
      },
      methods:{
        add(msg){
            this.msg = msg[0].tag_nameson
                if (this.msg.length == 16) {
                    this.msg.forEach((item)=>{
                        if (item.tag_nameson!=undefined) {
                            item.tag_nameson.forEach((item2)=>{
                            this.dataList.push(item2)
                        })
                        }
                    })
                    this.msg = Array.from(new Set(this.dataList));
                }else{
                    this.msg = msg[0].tag_nameson
                    console.log(this.msg);
                    item.state = !item.state
                }
        },
        changeColumn(item){
            this.msg.forEach((listItem) => {
            listItem.state = (listItem.name === item.name);
        });
        this.$bus.$emit('changeColumn',item)
        }
      },
      mounted(){
        this.$bus.$on('changeCon',this.add)
      }
  }
  </script>
  
  <style>
.LeftBox{
    width: 24%;
    min-width: 100px;
    height: calc(97% - 110px);
    border-right: 1px solid #252527;
    overflow: auto;
    float: left;
}
::-webkit-scrollbar {
  width: 1px;
  height: 1px; 
}
.LeftBox ul li{
    list-style: none;
    width: 100%;
    height: 38px;
    cursor: pointer;
}
.search_div{
    width: 85%;
    height: 25px;
    border-radius: 10px;
    padding-left: 10px;
    background-color: #25252c;
    border: 1px solid #25252c;
    margin-bottom: 15px;
}
.search_div:focus,
textarea:focus {
  border-color: #5e5f63;
  outline: none;
}
.optionList{
    width: 75%;
    height: 100%;
    padding-left: 10%;
    /* background-color: #1890ff; */
}
.spSvg svg{
    width: 14px;
    height: 14px;
    color: #fff;
}
.spSvg{
   margin: 9px 0;
    float: left;
}
.platform{
    width: 75%;
    height: 100%;
    float: left;
}
.platform span{
    line-height: 38px;
    color: #fff;
    font-size: 14px;
    float: left;
}
.platform img{
    margin: 8px 5px;
    border-radius: 6px;
    float: left;
}
.LeftBox ul li:hover .platform:hover span{
    color: #196ebe;
}
.LeftBox ul li:hover .spSvg svg path{
    fill: #196ebe;
}
.actives .optionList{
  background-color:#196ebe ;
}
.actives .optionList .spSvg svg path{
    fill: #fff;
}
  </style>