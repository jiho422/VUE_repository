<template>
  <div class="inputBox shadow">
      <input type="text" v-model="newTodoItem" placeholder="Type what you have to do" v-on:keyup.enter="addTodo">
      <span class="addContainer" v-on:click="addTodo">
        <i class="far fa-plus-square addBtn" aria-hidden="true"></i>
      </span>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodoItem: ""
    }
  },
  methods: {
    addTodo() {
      console.log(this.newTodoItem);
      //저장하는 로직
      alert('list added');
      if(this.newTodoItem !== ""){
          let value = this.newTodoItem && this.newTodoItem.trim(); /* 빈 공백값이 없는 데이터를 받아오기(trim 사용) */
          localStorage.setItem(value, value);
          this.$emit('addTodo', value);
          this.clearInput();
      }  
    },

    clearInput() {
      this.newTodoItem=""; //비워주기(초기화)
    }
  }
}
</script>

<style scoped>
input:focus {
  outline: none;
}
.inputBox {
  background: white;
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
}
.inputBox input {
  border-style: none;
  font-size: 0.9rem;
}
.addContainer {
  float: right;
  background: linear-gradient(to right, #62EAC6, #32CEE6);
  display: block;
  width: 3rem;
  border-radius: 0 5px 5px 0;
}
.addBtn {
  color: white;
  vertical-align: middle;
}

.addBtn:hover{
    cursor: pointer;
}
</style>