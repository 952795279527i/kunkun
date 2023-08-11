<template>
  <div id="app">
    <!-- <ModiFication/> -->
    <!-- <DemoList/> -->
    <!-- <HelloWorld/> -->
    <!-- <NextTick/> -->
    <!-- <Tran/> -->
    <div class="SlotData">
        <child-componment>
            <div>11</div>
        </child-componment>
    </div>
  </div>
</template>

<script>
    // import HelloWorld from './components/HelloWorld.vue'
    // import DemoList from './components/DemoList.vue';
    // import ModiFication from './components/ModiFication.vue';
    // import NextTick from './components/NextTick.vue'
    // import Tran from './components/Tran.vue'
    import SlotData from './components/SlotData.vue';
export default {
  name: 'App',
  components: {
    // HelloWorld,
    // DemoList,
    // ModiFication
    // NextTick
    // Tran
    SlotData
  },
  data(){
        return {
        message: ''
        }
    }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
