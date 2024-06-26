<!-- app.vue -->
<template>
  <div class="container">
    <h1 class="completed">APLIKASI INPUT DATA</h1>
    <input type="text" v-model="newTodo" placeholder="Masukkan Inputan di Sini">
    <button @click="addTodo">MASUKKAN DATA</button>

    <h2 :style="{ 'color': todos.length > 0 ? '#007bff' : 'red' }">HASIL INPUTAN:</h2>
    <ul>
      <li v-for="(todo, index) in todos" :key="index" :class="{ 'completed': todo.completed }">
        <span @click="toggleCompletion(index)">{{ todo.text }}</span>
        <button @click="removeTodo(index)">HAPUS</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: '',
      todos: []
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() !== '') {
        this.todos.push({ text: this.newTodo, completed: false });
        this.newTodo = '';
      }
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    },
    toggleCompletion(index) {
      this.todos[index].completed = !this.todos[index].completed;
    }
  }
};
</script>

<style>

.container {
  border: 5px solid #ccc;
  padding: 20px;
  border-radius: 5px;
  max-width: 500px;
  margin: 0 auto;
  background-image: url('https://t3.ftcdn.net/jpg/03/15/92/42/240_F_315924231_ARwuFaPa1NzlsYbnFQfQukX4QxY6MNNM.jpg');
  background-size: cover;  /* Menyesuaikan ukuran gambar dengan ukuran kontainer */
  background-position: center;  /* Menengahkan gambar */
}


h1 {
  font-size: 24px;
  color: #333;
  margin-bottom: 20px;
  border-bottom: 1px solid #ccc;
  padding-bottom: 10px;
}


.completed {
  color: #fff;
}


input[type="text"] {
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-bottom: 10px;
  width: calc(100% - 22px);
}


button {
  padding: 10px 20px;
  font-size: 16px;
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}


button:hover {
  background-color: #0056b3;
}


h2 {
  font-size: 20px;
  margin-top: 30px;
  border-bottom: 1px solid #ccc;
  padding-bottom: 10px;
}


ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin-bottom: 10px;
  border-bottom: 1px solid #ccc;
  padding-bottom: 10px;
}


.completed span {
  text-decoration: line-through;
  color: #999;
}


button.remove {
  margin-left: 10px;
  margin-top: 5px;
  background-color: #dc3545;
}


button.remove:hover {
  background-color: #c82333;
}

</style>
