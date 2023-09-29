<script setup>
    import store from '../store/loginRegister';
    import {reactive} from 'vue'

    const state = store()

    const LoginInput = reactive({});

    function LoginData(){
      state.login(LoginInput)
    }

</script>

<template>
   <div class="h-200 w-full flex items-center justify-center bg-teal-lightest font-sans" style="height: 600px;">
      <div class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4 flex flex-col mb-20 mt-20">
         <div class="mb-4">
            <label class="block text-grey-darker text-sm font-bold mb-2" for="username">
               Username
            </label>
            <input v-model="LoginInput.email" class="shadow appearance-none border rounded w-full py-2 px-3 text-grey-darker" id="username"
               type="email" placeholder="Email">
         </div>
         <div class="mb-6">
            <label class="block text-grey-darker text-sm font-bold mb-2" for="password">
               Password
            </label>
            <input v-model="LoginInput.password" class="shadow appearance-none border rounded w-full py-2 px-3 text-grey-darker"
               id="password" type="password" placeholder="******************">
         </div>
         <div class="flex items-center justify-between">
            <button @click="LoginData()" class="bg-blue hover:bg-blue-dark text-white font-bold py-2 px-4 rounded" type="button">
               Sign In
            </button>
            <router-link class="inline-block align-baseline font-bold text-sm text-blue hover:text-blue-darker" :to="{name: 'Register'}">
               Registration
            </router-link>
         </div>
      </div>
   </div>
</template>

<style scoped>

</style>