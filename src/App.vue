<template>
  <div class="container">
    <Header @show_add="show" title="task traker" :showAddTask="showAddTask" />
    <div v-show="showAddTask">
      <Addtask @onSubmit="add_task"/>
    </div>
    <Tasks @delete_task="delete_task" :tasks="tasks" />
  </div>
</template>

<script>
import Header from './components/Header'
import Tasks from './components/Tasks' 
import Addtask from './components/Addtask'

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    Addtask
  },
  data() {
    return {
      tasks: [],
      showAddTask:false,
    }
  },
  methods: {
    add_task(task) {
      this.tasks = [task, ...this.tasks];
    localStorage.setItem("tasks", JSON.stringify(this.tasks));
    },
    delete_task(id) {
      if(confirm("are you sure about that ?!!")) {
        this.tasks = this.tasks.filter(t => t.id !== id) 
        localStorage.setItem("tasks", JSON.stringify(this.tasks));
      }
    },
    show() {
      this.showAddTask = !this.showAddTask;
    },
  }
  ,
  created() {
    this.tasks = JSON.parse(localStorage.getItem("tasks"));
    //   [{
    //   id: 1,
    //   text: "doctors appointment",
    //   day: "march 1st at 2:30pm",
    //   reminder: true,
    // },
    // {
    //   id: 2,
    //   text: "work appointment",
    //   day: "march 2st at 3:30pm",
    //   reminder: true,
    // },
    // {
    //   id: 3,
    //   text: "rest appointment",
    //   day: "march 3st at 4:30pm",
    //   reminder: true,
    // },
    // {
    //   id: 4,
    //   text: "dance party ",
    //   day: "march 4st at 00:30pm",
    //   reminder: true,
    // }]
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: Arial, Helvetica, sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}

</style>