<template>
    <div class="container">
        <h2 class="text-center mt-5">My Vue todo App</h2>
    
        <!-- Input -->
        <div class="d-flex">
            <input v-model="task" type="text" placeholder="enter text" class="form-control">
            <button @click="submitTask" class="btn btn-warning rounded-0">Submit</button>
        </div>

     <!-- Task Table -->
     <table class="table table-bordered mt-5">
  <thead>
    <tr>
      <th scope="col">Task</th>
      <th scope="col">Status</th>
      <th scope="col">#</th>
      <th scope="col">#</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="(task,index) in tasks" :key="index">
      <td>{{task.name}}</td>
      <td style="width: 120px"><span @click="changeStatus(index)" class="pointer">{{task.status}}</span></td>
      <td>
          <div @click="editTask(index)" class="text-center">
            <span class="fa fa-pen"></span>
          </div>
     </td>
      <td>
          <div @click="deleteTask(index)" class="text-center">
            <span class="fa fa-trash"></span>
          </div>
      </td>
    </tr>
  </tbody>
</table>
    </div>
</template>

<script>
export default {
    name: 'HelloWorld',
    props:{
        msg:String
    },
    data() {
        return {
            task:'',
            editedTask : null,
            availableStatuses:['to-do','in-progress','finished'],
            tasks :[
                {
                    name : 'Steal banans from the store',
                    status: 'to-do'
                },
                 {
                    name : 'Eat 1kg chocolate in 1 hour',
                    status: 'in-progress'
                }
            ]
        }
    },

    methods: {
        submitTask(){
            if(this.task.length === 0) return;
            
            if(this.editedTask === null){
                this.tasks.push({
                name:this.task,
                status: 'to-do'
            });
            }else{
                this.tasks[this.editedTask].name = this.task;
                this.editedTask = null;
            }

            this.task='';
            
        },
        deleteTask(index){
            this.tasks.splice(index,1);
        },
        editTask(index){
            this.task = this.tasks[index].name;
            this.editedTask = index;
        },
        changeStatus(index){
            let newIndex = this.availableStatuses.indexOf(this.tasks[index].status);
            if(++newIndex>2) newIndex=0;
            this.tasks[index].status = this.availableStatuses[newIndex];
        },
    }
};
</script>
<style scoped>
    .pointer{
        cursor: pointer;
    }
</style>
