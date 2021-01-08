<template>
    <div class="clearAllContainer">
        <span class="clearAllBtn" @click="clearTodo">모두 삭제</span>
    </div>
</template>
<script>
export default {
    methods: {
        clearTodo(){
            this.$emit('removeAll');
        }
    },
}
</script>
<style>
    .clearAllContainer{
        width: 7rem;
        height: 2.5rem;
        line-height: 2.5rem;
        background-color: white;
        border-radius: 0.3rem;
        margin: 0 auto;
    }
    .clearAllBtn{
        color: #e20303;
        display:block;
    }
</style>