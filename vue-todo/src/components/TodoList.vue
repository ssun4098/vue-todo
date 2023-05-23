<template>
  <section>
    <TransitionGroup name="list" tag="ul">
      <li v-for="(todoItem, index) in propsdata" :key="todoItem" class="shadow">
        <i class="checkBtn fa fa-check" aria-hidden="true"></i>
        {{todoItem}}
        <span class="removeBtn" @click="removeTodo(todoItem, index)">
          <i class="fa fa-trash" aria-hidden="true"></i>
        </span>
      </li>
    </TransitionGroup>
  </section>
</template>

<script>
export default {
  name: "TodoList",
  props: ['propsdata'],
  methods: {
    removeTodo(todoItem, index) {
      this.$emit('removeTodo', todoItem, index)
    }
  }
}
</script>

<style scoped>

li {
  display: flex;
  min-height: 50px;
  height: 50px;
  line-height: 50px;
  margin: 0.5rem 0;
  padding: 0 0.9rem;
  background: white;
  border-radius: 5px;
}

.list-enter-active,
.list-leave-active {
  transition: all 0.5s ease;
}
.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateX(30px);
}

.checkBtn {
  line-height: 45px;
  color: #62acde;
  margin-right: 5px;
}

.removeBtn {
  margin-left: auto;
  color: #de4343;
}
</style>