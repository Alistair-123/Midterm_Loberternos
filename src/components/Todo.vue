<template>
  <div class="todo-container">
    <h1>Vue Todo List</h1>

    <div class="input-container">
      <input v-model="newTodo" type="text" placeholder="Add a new task" />
      <button @click="addTodo">Add</button>
    </div>

    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        <div v-if="editingIndex === index">
          <input v-model="editedTodo" />
          <button @click="saveTodo(index)">Save</button>
        </div>
        <div v-else>
          <span>{{ todo.text }}</span>
          <button @click="editTodo(index)">Edit</button>
          <button @click="deleteTodo(index)">Delete</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Todo',
  data() {
    return {
      newTodo: '',
      todos: [],
      editingIndex: null,
      editedTodo: ''
    }
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() !== '') {
        this.todos.push({ text: this.newTodo.trim() })
        this.newTodo = ''
      }
    },
    deleteTodo(index) {
      this.todos.splice(index, 1)
    },
    editTodo(index) {
      this.editingIndex = index
      this.editedTodo = this.todos[index].text
    },
    saveTodo(index) {
      if (this.editedTodo.trim() !== '') {
        this.todos[index].text = this.editedTodo.trim()
        this.editingIndex = null
        this.editedTodo = ''
      }
    }
  }
}
</script>

<style scoped>
body {
  background-color: #f0f8ff;
  font-family: Arial, sans-serif;
}

.todo-container {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  background-color: #fff;
  border-radius: 10px;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
}

h1 {
  text-align: center;
  color: #333;
}

.input-container {
  display: flex;
  justify-content: space-between;
  margin-bottom: 20px;
}

input {
  flex: 1;
  padding: 10px;
  border-radius: 5px;
  border: 1px solid #ccc;
  margin-right: 10px;
}

button {
  padding: 10px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #f8f9fa;
  padding: 10px;
  margin-bottom: 10px;
  border-radius: 5px;
  box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.1);
}

li span {
  flex: 1;
}

li button {
  margin-left: 10px;
}
</style>
