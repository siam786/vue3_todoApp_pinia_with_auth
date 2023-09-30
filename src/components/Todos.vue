<script setup>
  import { AppStore } from '../store/store';
  import { onMounted, reactive,ref } from 'vue';
  const store = AppStore();

  const inputData = ref('')
  
  function insertInputData(){
      store.addProject(inputData)
      inputData.value = ''
   
  }

  onMounted(()=>{
    store.inCompleteProjectsFunction();
    store.completeProjectsFunction();
  });
</script>

<template>
    <div class="flex items-center justify-center w-full h-screen font-sans bg-blue-500">
      <div class="w-full p-6 m-4 rounded shadow bg-gradient-to-r from-blue-200 to-cyan-200 lg:w-4/4 lg:max-w-lg">
        <div class="mb-4">
          <h1 class="text-4xl text-red-500">Todo App</h1>
          <div class="flex mt-4">
            <input v-model="inputData" class="w-full px-3 py-2 mr-4 border rounded shadow appearance-none text-grey-darker"
              placeholder="Add Todo">
            <button @click="insertInputData()"
              class="p-2 border-2 rounded flex-no-shrink text-teal border-red hover:text-white hover:bg-red-500">Add</button>
          </div>
        </div>
        <div>

          
           <div class="flex items-center mb-4" v-for="(project, index) in store.inCompleteProject" :key="index">
            <p class="w-full text-grey-darkest">{{ project.name }}</p>
            <button
             @click="store.doneAsComplete(project.id)" type="button" class="p-2 ml-4 mr-2 border-2 rounded flex-no-shrink hover:text-white text-green border-green hover:bg-blue-500">Done</button>
            <button type="button" @click="store.deleteProject(project.id)"
              class="p-2 ml-2 border-2 rounded flex-no-shrink text-red border-red hover:text-white hover:bg-blue-500">Remove</button>
          </div>
          
          <br><br>
          
          <div class="flex items-center mb-4" v-for="(project, index) in store.completeProject" :key="index">
            <p class="w-full text-red-500 line-through">{{ project.name }}</p>
            <button
            @click="store.doneAsInComplete(project.id)" type="button" class="p-2 ml-4 mr-2 border-2 rounded flex-no-shrink hover:text-white text-grey border-grey hover:bg-grey">Not
              Done</button>
            <button type="button" @click="store.deleteProject(project.id)"
              class="p-2 ml-2 border-2 rounded-ml flex-no-shrink text-red border-red hover:text-white hover:bg-blue-500">Remove</button>
          </div>

        </div>
      </div>
    </div>
    <footer class="py-4 text-center text-white bg-blue-700">
    <h4>Todo App - All right Reserved &copy;2023</h4>
  </footer>
</template>

<style scoped>

</style>