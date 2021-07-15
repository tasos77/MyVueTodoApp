<template>
    <div class="container">
        <h2 class="text-center mt-5">My Vue todo App</h2>
    
        <!-- Input -->
        <div class="d-flex">
            <input type="text" placeholder="enter text" class="form-control">
            <button class="btn btn-warning rounded-0">Submit</button>
        </div>

     <!-- Task Table -->
     <table class="table table-bordered">
  <thead>
    <tr>
      <th scope="col">Task</th>
      <th scope="col">Status</th>
      <th scope="col">#</th>
      <th scope="col">#</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Steal bananas from the store.</th>
      <td>Mark</td>
      <td>Otto</td>
      <td>Momdo</td>
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
    }
}
</script>
<style scoped>
    
</style>