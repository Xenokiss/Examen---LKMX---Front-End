<template>
  <div class="main-box">
    <h2>To Do List</h2>
    <div class="add">
      <input class="add-input" type="text" placeholder="Agregar un nuevo task" v-model="newTask">
      <button class="add-btn" v-on:click="addItem()">Agregar</button>
    </div>
    <div v-for="(task, index) in tasks" :key="task.id">
      <div v-if="task.id != 0">
        <div class="row" v-if="task.status == true">
          <input class="text-simple" disabled v-model="task.text">
          <button class="action-btn" v-on:click="editItem(task)"><img src="../assets/icon-pen.svg"></button>
          <button class="action-btn" v-on:click="delItem(index)"><img src="../assets/icon-trash.svg"></button>
        </div>
        <div class="row" v-if="task.status == false">
          <input class="text-edi" type="text" v-model="task.text">
          <button class="action-btn" v-on:click="saveItem(task)"><img src="../assets/icon-disk.svg"></button>
        </div>
      </div>
    </div>
    <div v-if="idForTask == 1">
        <input class="text-empty" disabled value="No has agregado tareas">
      </div>
  </div>
</template>

<script>
export default {
  name: 'List',
  data(){
    return{
      newTask:'',
      idForTask:1,
      tasks:[{
        'id':0,
        'text': '',
        'status': true
      }]
    }
  },
  methods:{
    addItem(){
      if(this.newTask.trim().length == 0)  {
        return
      }else{
        this.tasks.push({
        id: this.idForTask,
        text: this.newTask,
        status: true
        })
        this.newTask = ''
        this.idForTask++
      }
    },
    delItem(index){
      this.tasks.splice(index,1)
      this.idForTask--
    },
    editItem(task){
      task.status = false
    },
    saveItem(task){
      task.status = true
    }
  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.main-box{
  background-color: white;
  width: 550px;
  height: auto;
  padding: 5px;
  border-radius: 10px;
}
.add{
  display:inline;
}
.add-input{
  outline: #5657E6;
  margin: 2px;
  width: 435px;
  font-size: 25px;
  border-radius: 10px;
  
}
input:focus{
  border-color:#5657E6;
}
.add-btn{
  border-color: none;
  outline: none;
  background-color: #5657E6;
  padding: 4px;
  font-size: 23px;
  border-radius: 8px;
  margin-right: 5px;
}input{
  outline: #5657E6;
  background: transparent;
  margin: 2px;
  font-size: 25px;
  border-radius: 10px;
  box-sizing: border-box;
}
.text{
  width: 450px;
}
.text-simple{
  width: 430px;
  border: transparent;
}
.text-empty{
  width: 535px;
  background: rgb(188, 188, 255);
}
.text-edi{
  width: 470px;
  border: transparent;
}
.action-btn{
  outline: none;
  margin-right: 2px;
  border-radius: 10px;
  transition: 1s;
}
button:hover{
  background-color: #c9c9c9;
}
h2{
  display: flex;
  margin: 0px;
  font-size: 30px;
  padding-left: 5px;
}
.row{
  background-color: rgb(188, 188, 255);
  border-radius: 10px;
  margin-top: 1px;
  width: 535px;
}


</style>
