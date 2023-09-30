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
    <div class="flex items-center justify-center w-full h-screen font-mono bg-gradient-to-r from-indigo-500 to-blue-500">
      <div class="w-full p-6 m-4 rounded shadow bg-gradient-to-r from-blue-200 to-cyan-200 lg:w-4/4 lg:max-w-lg">
        <div class="mb-4">
          <h1 class="text-4xl text-red-500">Todo App</h1>
          <div class="flex mt-4">
            <input v-model="inputData" class="w-full px-3 py-2 mr-4 border rounded shadow appearance-none text-grey-darker"
              placeholder="Add Todo">
            <button @click="insertInputData()"
              class="p-2 border-2 border-red-500 rounded flex-no-shrink text-teal hover:text-white hover:bg-red-500">Add</button>
          </div>
        </div>
        <div>

          
           <div class="flex items-center mb-4" v-for="(project, index) in store.inCompleteProject" :key="index">
            <p class="w-full text-grey-darkest">{{ project.name }}</p>
            
            <div @click="store.doneAsComplete(project.id)" class="flex items-center justify-center w-6 h-6 p-1 mr-2 bg-white shadow">
                <input type="checkbox"  unchecked>
                <svg class="hidden w-4 h-4 text-green-600 pointer-events-none" viewBox="0 0 172 172"><g fill="none" stroke-width="none" stroke-miterlimit="10" font-family="none" font-weight="none" font-size="none" text-anchor="none" style="mix-blend-mode:normal"><path d="M0 172V0h172v172z"/><path d="M145.433 37.933L64.5 118.8658 33.7337 88.0996l-10.134 10.1341L64.5 139.1341l91.067-91.067z" fill="currentColor" stroke-width="1"/></g></svg>
            </div>
             
            <button type="button" @click="store.deleteProject(project.id)"
              class="p-2 ml-2 border-2 border-red-500 rounded flex-no-shrink text-red hover:text-white hover:bg-blue-500">Remove</button>
          </div>
          
          <br><br>
          
          <div class="flex items-center mb-4" v-for="(project, index) in store.completeProject" :key="index">
            <p class="w-full text-red-500 line-through">{{ project.name }}</p>
            
          <div @click="store.doneAsInComplete(project.id)" class="flex items-center justify-center w-6 h-6 p-1 mr-2 bg-white shadow">
                <input type="checkbox"  checked>
                <svg class="hidden w-4 h-4 text-green-600 pointer-events-none" viewBox="0 0 172 172"><g fill="none" stroke-width="none" stroke-miterlimit="10" font-family="none" font-weight="none" font-size="none" text-anchor="none" style="mix-blend-mode:normal"><path d="M0 172V0h172v172z"/><path d="M145.433 37.933L64.5 118.8658 33.7337 88.0996l-10.134 10.1341L64.5 139.1341l91.067-91.067z" fill="currentColor" stroke-width="1"/></g></svg>
            </div>
            <button type="button" @click="store.deleteProject(project.id)"
              class="p-2 ml-2 border-2 border-red-500 rounded-ml flex-no-shrink text-red hover:text-white hover:bg-blue-500">Remove</button>
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