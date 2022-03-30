<template>
  <div>
    <form @submit.prevent="addTaskToList" class="form">
      <input v-model="addTaskTitle" placeholder="Task" required/>
      <input type="url" v-model="addTaskSource" placeholder="Source" required   />
      <button>Add Task</button>
    </form>
    <ul v-if="tasks.length">
      <li v-for="task in tasks" :key="task.id">
        <p>{{ task.task }}</p>
        <a :href="task.source" target=blank>{{ task.source }}</a>
        <button @click="removeTask(task)"> Delete Task</button>
      </li>
    </ul>
    <p id="noTasks" v-else>No sources yet</p>
  </div>
</template>

<script>
let storedTasks =  JSON.parse(localStorage.getItem("tasks")) || [];
let id = storedTasks.length;

export default {
  data() {
    return {
      tasks:   storedTasks
    };
  },
  methods: {
    addTaskToList() {
        this.tasks.push({
          id: id++,
          task: this.addTaskTitle,
            source: this.addTaskSource,
          completed: false,
        });
        this.addTaskTitle = "";
        this.addTaskSource = "";
        localStorage.setItem("tasks", JSON.stringify(this.tasks));
    },
     removeTask(task) {
      this.tasks = this.tasks.filter((t) => t !== task)
        let updateArray = this.tasks;
        localStorage.setItem("tasks", JSON.stringify(updateArray));
    }
  },
};
</script>


<style lang="scss" scoped>
@import "./../assets/_variables.scss";

    #noTasks {
        font-family: $mainTextFont;
        font-size: 1.5rem;
        text-align: center;
        padding: 1rem;
    }    
    .form {
        font-family: $mainTextFont;
        input {
            height: 3rem;
            min-width: 300px;
            width: calc(50%  - 50px);
            font-size: 1rem;
            
        }
        button {
            height: 3rem;
            width: 100px;
            border-radius: 0;
            background-color: $accentColor;
            border: none;
            color: $textColor;
        }
    }
    ul {
        margin-top: 2rem;
        list-style: none;
        width: 100%;
        font-family: $mainTextFont;
        li {
            padding: 1rem;
            border: 1px solid $borderColor;
            display: flex;
            justify-content: space-between;
            &:nth-child(odd){
                background-color: $backgroundColor;
            }   
            button {
                height: 2rem;
            width: 100px;
            border-radius: 0;
            background-color: $dangerColor;
            border: none;
            color: $textColor;
            }
        }
    }
</style>
