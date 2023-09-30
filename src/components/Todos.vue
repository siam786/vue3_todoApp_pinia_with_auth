<script setup>
import { onMounted, ref } from "vue";
import { AppStore } from "../store/store";
const store = AppStore();

const inputData = ref("");

function insertInputData() {
  store.addProject(inputData);
  inputData.value = "";
}

onMounted(() => {
  store.inCompleteProjectsFunction();
  store.completeProjectsFunction();
});
</script>

<template>
  <div
    class="flex items-center justify-center w-full h-screen font-mono bg-gradient-to-r from-indigo-500 to-blue-500"
  >
    <div
      class="w-full p-6 m-4 rounded shadow bg-gradient-to-r from-blue-200 to-cyan-200 lg:w-4/4 lg:max-w-lg"
    >
      <div class="mb-4">
        <h1 class="text-4xl text-red-500">Todo App</h1>
        <div class="flex mt-4">
          <input
            v-model="inputData"
            class="w-full px-3 py-2 mr-4 border rounded shadow appearance-none text-grey-darker"
            placeholder="Add Todo"
          />
          <button
            @click="insertInputData()"
            class="p-2 border-2 border-red-500 rounded flex-no-shrink text-teal hover:text-white hover:bg-red-500"
          >
            Add
          </button>
        </div>
      </div>
      <div>
        <div
          class="flex items-center mb-4"
          v-for="(project, index) in store.inCompleteProject"
          :key="index"
        >
          <p class="w-full text-grey-darkest">{{ project.name }}</p>
          <!-- done check box -->
          <div
            @click="store.doneAsComplete(project.id)"
            class="flex items-center justify-center w-6 h-6 p-1 mr-2 bg-white shadow"
          >
            <input type="checkbox" unchecked />
            <svg
              class="hidden w-4 h-4 text-green-600 pointer-events-none"
              viewBox="0 0 172 172"
            >
              <g
                fill="none"
                stroke-width="none"
                stroke-miterlimit="10"
                font-family="none"
                font-weight="none"
                font-size="none"
                text-anchor="none"
                style="mix-blend-mode: normal"
              >
                <path d="M0 172V0h172v172z" />
                <path
                  d="M145.433 37.933L64.5 118.8658 33.7337 88.0996l-10.134 10.1341L64.5 139.1341l91.067-91.067z"
                  fill="currentColor"
                  stroke-width="1"
                />
              </g>
            </svg>
          </div>

          <button
            type="button"
            @click="store.deleteProject(project.id)"
            class="p-2 ml-2 border-2 border-red-500 rounded flex-no-shrink text-red hover:text-white hover:bg-blue-500"
          >
          <svg xmlns="http://www.w3.org/2000/svg" x="0px" y="0px" width="20" height="20" viewBox="0,0,256,256">
<g fill="#000000" fill-rule="nonzero" stroke="none" stroke-width="1" stroke-linecap="butt" stroke-linejoin="miter" stroke-miterlimit="10" stroke-dasharray="" stroke-dashoffset="0" font-family="none" font-weight="none" font-size="none" text-anchor="none" style="mix-blend-mode: normal"><g transform="scale(8.53333,8.53333)"><path d="M14.98438,2.48633c-0.55152,0.00862 -0.99193,0.46214 -0.98437,1.01367v0.5h-5.5c-0.26757,-0.00363 -0.52543,0.10012 -0.71593,0.28805c-0.1905,0.18793 -0.29774,0.44436 -0.29774,0.71195h-1.48633c-0.36064,-0.0051 -0.69608,0.18438 -0.87789,0.49587c-0.18181,0.3115 -0.18181,0.69676 0,1.00825c0.18181,0.3115 0.51725,0.50097 0.87789,0.49587h18c0.36064,0.0051 0.69608,-0.18438 0.87789,-0.49587c0.18181,-0.3115 0.18181,-0.69676 0,-1.00825c-0.18181,-0.3115 -0.51725,-0.50097 -0.87789,-0.49587h-1.48633c0,-0.26759 -0.10724,-0.52403 -0.29774,-0.71195c-0.1905,-0.18793 -0.44836,-0.29168 -0.71593,-0.28805h-5.5v-0.5c0.0037,-0.2703 -0.10218,-0.53059 -0.29351,-0.72155c-0.19133,-0.19097 -0.45182,-0.29634 -0.72212,-0.29212zM6,9l1.79297,15.23438c0.118,1.007 0.97037,1.76563 1.98438,1.76563h10.44531c1.014,0 1.86538,-0.75862 1.98438,-1.76562l1.79297,-15.23437z"></path></g></g>
</svg>
          </button>
        </div>

        <br /><br />

        <div
          class="flex items-center mb-4"
          v-for="(project, index) in store.completeProject"
          :key="index"
        >
          <p class="w-full text-red-500 line-through">{{ project.name }}</p>

          <div
            @click="store.doneAsInComplete(project.id)"
            class="flex items-center justify-center w-6 h-6 p-1 mr-2 bg-white shadow"
          >
            <input type="checkbox" checked />
            <svg
              class="hidden w-4 h-4 text-green-600 pointer-events-none"
              viewBox="0 0 172 172"
            >
              <g
                fill="none"
                stroke-width="none"
                stroke-miterlimit="10"
                font-family="none"
                font-weight="none"
                font-size="none"
                text-anchor="none"
                style="mix-blend-mode: normal"
              >
                <path d="M0 172V0h172v172z" />
                <path
                  d="M145.433 37.933L64.5 118.8658 33.7337 88.0996l-10.134 10.1341L64.5 139.1341l91.067-91.067z"
                  fill="currentColor"
                  stroke-width="1"
                />
              </g>
            </svg>
          </div>
          <button
            type="button"
            @click="store.deleteProject(project.id)"
            class="p-2 ml-2 border-2 border-red-500 rounded-ml flex-no-shrink text-red hover:text-white hover:bg-blue-500"
          >
          <svg xmlns="http://www.w3.org/2000/svg" x="0px" y="0px" width="20" height="20" viewBox="0,0,256,256">
<g fill="#000000" fill-rule="nonzero" stroke="none" stroke-width="1" stroke-linecap="butt" stroke-linejoin="miter" stroke-miterlimit="10" stroke-dasharray="" stroke-dashoffset="0" font-family="none" font-weight="none" font-size="none" text-anchor="none" style="mix-blend-mode: normal"><g transform="scale(8.53333,8.53333)"><path d="M14.98438,2.48633c-0.55152,0.00862 -0.99193,0.46214 -0.98437,1.01367v0.5h-5.5c-0.26757,-0.00363 -0.52543,0.10012 -0.71593,0.28805c-0.1905,0.18793 -0.29774,0.44436 -0.29774,0.71195h-1.48633c-0.36064,-0.0051 -0.69608,0.18438 -0.87789,0.49587c-0.18181,0.3115 -0.18181,0.69676 0,1.00825c0.18181,0.3115 0.51725,0.50097 0.87789,0.49587h18c0.36064,0.0051 0.69608,-0.18438 0.87789,-0.49587c0.18181,-0.3115 0.18181,-0.69676 0,-1.00825c-0.18181,-0.3115 -0.51725,-0.50097 -0.87789,-0.49587h-1.48633c0,-0.26759 -0.10724,-0.52403 -0.29774,-0.71195c-0.1905,-0.18793 -0.44836,-0.29168 -0.71593,-0.28805h-5.5v-0.5c0.0037,-0.2703 -0.10218,-0.53059 -0.29351,-0.72155c-0.19133,-0.19097 -0.45182,-0.29634 -0.72212,-0.29212zM6,9l1.79297,15.23438c0.118,1.007 0.97037,1.76563 1.98438,1.76563h10.44531c1.014,0 1.86538,-0.75862 1.98438,-1.76562l1.79297,-15.23437z"></path></g></g>
</svg>
          </button>
        </div>
      </div>
    </div>
  </div>
  <footer class="py-4 text-center text-white bg-blue-700">
    <h4>Todo App - All right Reserved &copy;2023</h4>
  </footer>
</template>

<style scoped></style>
