<template>
    <div class="SlotData">
    <h2>这是子组件childComponment!</h2>
    <slot>
      <span style="color: red;">如果父组件没有插入内容，我这样可以设置默认的显示内容</span>
    </slot>
    </div>
</template>

<script>
export default {
    name: 'SlotData',

    data() {
        return {
            message: ''
        };
    },
};
</script>

<style lang="scss" scoped>

</style>