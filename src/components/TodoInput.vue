<template>
    <div class="inputBox shadow">
        <input type="text" v-model="newTodoItem" placeholder="해야 할 일을 입력해주세요." v-on:keyup.enter="addTodo">
        <span class="addContainer" @click="addTodo">
            <i class="addBtn fas fa-plus" aria-hidden="true"></i>
        </span>
        
        <modal v-if="showModal" @close="showModal = false">
            <h3 class="warning" slot="header">경고</h3>
            <span slot="footer" @click="showModal = false">
                할 일을 입력하셔야합니다.
                <i class="closeModalBtn fas fa-times" aria-hidden="true"></i>
            </span>
        </modal>
    </div>
</template>
<script>
import Modal from './common/Modal.vue'
export default {
    data(){
        return {
            newTodoItem: '',
            showModal: false
        }
    },
    methods: {
        addTodo(){
            if(this.newTodoItem !== ""){
                var value = this.newTodoItem && this.newTodoItem.trim();
                this.$emit('addTodo', value);
                this.clearInput()
            } else {
                this.showModal = !this.showModal;
            }
        },
        clearInput(){
            this.newTodoItem = '';
        },
    },
    components:{
        Modal:Modal
    }
}
</script>
<style>
    input:focus{
        outline: none;
    }
    .inputBox{
        background-color: white;
        height: 3rem;
        line-height: 3rem;
        border-radius: 0.5rem;
    }
    .inputBox input{
        text-align: center;
        border-style: none;
        font-size: 0.9rem;
    }
    .addContainer{
        float: right;
        background: linear-gradient(to right, #6478FB, #8763FB);
        display : block;
        width: 3rem;
        border-radius: 0 0.5rem 0.5rem 0;
    }
    .addBtn{
        color: white;
        vertical-align: middle;
    }
    .closeModalBtn {
        color: #62acde;
    }
    .warning{
        color: red;
    }
</style>