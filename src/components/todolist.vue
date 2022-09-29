<template >
<div class="container" style="background-color: blanchedalmond; max-width:600px">
  <h2 class="text-center mt-5"> 待辦事項</h2>
  
<!--Input-->
<div class="d-flex mt-5" >
  <input v-model="task"  type="text" placeholder="輸入待辦事項" class="w-100 form-control">
  <button @click="submitTask"  class="btn btn-warning rounded-0">提交</button>
</div>
<!--Task table-->
<table class="table table-bordered mt-5">
  <thead>
    <tr>
      <th scope="col" style="width: 400px;">任務</th>
      <!-- <th scope="col" style="width:120px">Status</th> -->
      <th scope="col" class="text-center" style="width: 100px;">編輯</th>
      <th scope="col" class="text-center" style="width: 100px;">刪除</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="(task,index) in tasks" :key="index">
     <td>
            <!-- <span :class="{ 'line-through': task.status === 'finished' }"> -->
              {{ task.name }}
            <!-- </span> -->
          </td>
     <!-- <td>
          <span @click="changeStatus(index)" class="pointer">{{ task.status}}</span>
      </td> -->
      <td>
        <div class="text-center" @click="editTask(index)">
          <span class="fa fa-pen"></span>
        </div>
      </td>
      <td>
        <div class="text-center" @click="deleteTask(index)">
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
  props: {
    msg: String
  },

  data(){
    return{
      task:'',
      editedTask: null,

      tasks: [
        {
          name:'採買日用品',
        },
         {
          name:'洗衣服',
        },
        {
          name:'打掃廚房',
        },
      ],
    };
    
  },

methods:{
capitalizeFirstChar(str) {
      return str.charAt(0).toUpperCase() + str.slice(1);
    },

  submitTask(){
 if(this.task.length === 0) return;
//  this.tasks.push({
//         name: this.task,
//         status:"todo",
//       });

if(this.editedTask === null){
  this.tasks.push({
    name:this.task,
  });
}else{
  this.tasks[this.editedTask].name = this.task;
  this.editedTask = null;
}


this.task= '';
},



deleteTask(index){
  this.tasks.splice(index, 1);
},

editTask(index){
  this.task = this.tasks[index].name;
  this.editedTask = index;
},




}
};


</script>

<style scoped>



</style>
