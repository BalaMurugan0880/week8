<template>
  <div id="app">
    <h1>Hello World</h1>
    <p>{{ msg }}</p>
    <p>My Name is {{ name }}</p>
    <!--This is how u create onclick using v-on:click -->
    <button v-on:click='greet'>Click</button>
    <hr>
    <h2>Counter Section</h2>
    <p>{{ counter }}</p>
    <p style="color:red">{{ error }}</p>
    <button v-on:click='increment'>Increment</button>
    <button v-on:click='decrement'>Decrement</button>
    <button v-on:click='reset'>Reset</button>
    <hr>
    <h2>Form Example</h2>
    <input v-model="userName" type="text" name="name" placeholder="Enter Your Name">
    <button v-on:click='sayHello'>Say Hello</button>
    <hr>
    <h2>My Students</h2>
    <ul>
      <li v-for="student in students" :key="student"> {{ student }} </li>
    </ul>
    <hr>
    <h2>v If</h2>
    <p v-if="user.gender == 'male'">Hello MR {{user.name }}</p>
    <p v-else>Hello Ms {{user.name }}</p>
    <hr>
    <h2>My To Do List</h2>
    <input v-model="newtodo" type="text" name="todo"><button v-on:click='addtodo'>Add New Item</button>
    <ul>
      <li v-for="todo in todolist" :key="todo">{{ todo }}<button  v-on:click="deleteEvent(todo)">Delete</button></li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'App',
  data(){
    return{
      //THis is how u create a variable
      msg: "Welcome To My Website",
      name: "BalaMurugan",
      counter: 0,
      error: "",
      userName: "",
      students:["Rachel","Ing yeen","Bala","Haikal","Greg"],
      user: {name:"BalaMurugan", gender:"male"},
      todolist:["test"],
      newtodo:"",

    }
  },
  methods: {

    sayHello: function(){
     alert("Hello "+this.userName);

    },
    //This is how you create a method
    greet: function(){
      alert("Hello World");

    },

     increment: function(){
      this.counter++
      this.error = ""

    },
    decrement: function(){
      if (this.counter == 0) {
        this.error = "Number Cannot Less Than 0"
      }else{
        this.error = ""
        this.counter--
      }
     

    },
    reset: function(){
     this.counter = 0
     this.error = ""

    },
    addtodo: function(){
      this.todolist.push(this.newtodo);

    },
    deleteEvent: function(item) {
      for (var i =0; i<this.todolist.length;i++) {
        if (this.todolist[i] == item) {
          this.todolist.splice(i,1)
        }
      }
             console.log(item)
        },
  }
};
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
