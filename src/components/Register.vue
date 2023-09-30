<script setup>
   import {reactive} from 'vue'
   import store from '../store/loginRegister'
   const state = store()

   const registerForm = reactive({});

   function submitData(){
      state.registration(registerForm)
   }

</script>

<template>
 
<div class="flex flex-col justify-center min-h-full px-6 py-12 lg:px-8">
  <div class="sm:mx-auto sm:w-full sm:max-w-sm">
    <img class="w-auto h-10 mx-auto" src="https://tailwindui.com/img/logos/mark.svg?color=indigo&shade=600" alt="Your Company">
    <h2 class="mt-10 text-2xl font-bold leading-9 tracking-tight text-center text-gray-900">Sign in to your account</h2>
  </div>

  <div class="mt-10 sm:mx-auto sm:w-full sm:max-w-sm">

      <div>
        <label for="username" class="block text-sm font-medium leading-6 text-gray-900">UserName</label>
        <div class="mb-2">
          <input v-model="registerForm.name" id="username" name="username" type="username" placeholder="Enter UserName" autocomplete="username" required class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6">
        </div>
      </div>
	  
	  <div>
        <label for="email" class="block text-sm font-medium leading-6 text-gray-900">Email</label>
        <div class="mb-2">
          <input v-model="registerForm.email" id="email" name="email" type="email" autocomplete="email" placeholder="Enter Email" required class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6">
        </div>
      </div>

      <div>
        <div class="flex items-center justify-between">
          <label for="password" class="block text-sm font-medium leading-6 text-gray-900">Password</label>
          
        </div>
        <div class="mt-2">
          <input v-model="registerForm.password" id="password" name="password" type="password" autocomplete="current-password" placeholder="Enter Password" required class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6">
        </div>
		<div class="mt-2">
          <input v-model="registerForm.confirm_password" id="confirm-password" name="confirm-password" type="password"  autocomplete="current-password" placeholder="Enter Password" required class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6">
        </div>
      </div>

      <div>
        <button @click="submitData()" type="submit" class="flex w-full justify-center rounded-md bg-indigo-600 px-3 py-1.5 text-sm font-semibold leading-6 text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 my-4">Register</button>
      </div>
   <router-link class="inline-block text-sm font-bold align-baseline text-blue hover:text-blue-darker" :to="{name: 'Login'}">
               Login
            </router-link>

    
  </div>
</div>

</template>

<style scoped>

</style>