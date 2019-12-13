<template>
  <li class="flex flex-col bg-white rounded shadow p-3 mb-2">
      <!-- Task title -->
      <div class="flex flex-row justify-between items-start mb-3">
          <h3 class="text-xs font-medium text-gray-900 leading-tight flex-1">{{ task.title }}</h3>
          <div class="flex items-center justify-center w-4 h-4 bg-green-500 rounded-full ml-4">
          <svg viewBox="0 0 20 20" class="text-green-700 w-2 h-2">
              <path class="fill-current" d="M10 20C7.34784 20 4.8043 18.9464 2.92893 17.0711C1.05357 15.1957 0 12.6522 0 10C0 7.34784 1.05357 4.8043 2.92893 2.92893C4.8043 1.05357 7.34784 0 10 0C12.6522 0 15.1957 1.05357 17.0711 2.92893C18.9464 4.8043 20 7.34784 20 10C20 12.6522 18.9464 15.1957 17.0711 17.0711C15.1957 18.9464 12.6522 20 10 20ZM7 6V8C7 8.79565 7.31607 9.55871 7.87868 10.1213C8.44129 10.6839 9.20435 11 10 11C10.7956 11 11.5587 10.6839 12.1213 10.1213C12.6839 9.55871 13 8.79565 13 8V6C13 5.20435 12.6839 4.44129 12.1213 3.87868C11.5587 3.31607 10.7956 3 10 3C9.20435 3 8.44129 3.31607 7.87868 3.87868C7.31607 4.44129 7 5.20435 7 6ZM3.35 14.44C4.08105 15.5332 5.07031 16.4292 6.23022 17.0489C7.39013 17.6686 8.68493 17.9928 10 17.9928C11.3151 17.9928 12.6099 17.6686 13.7698 17.0489C14.9297 16.4292 15.919 15.5332 16.65 14.44C14.5638 13.4824 12.2955 12.9866 10 12.9866C7.70454 12.9866 5.43616 13.4824 3.35 14.44Z" />
          </svg>
          </div>
      </div>
      <!-- Task data -->
      <div class="flex flex-row justify-between items-center">
          <div class="flex flex-row items-center">
          <span class="text-xs font-normal text-gray-600 leading-none">{{ task.date }}</span>
          <svg viewBox="0 0 12 12" class="text-yellow-400 w-3 h-3 ml-1" v-if="task.important">
              <path class="fill-current" d="M1.83173 10.3157C1.25867 9.76225 0.801575 9.10018 0.487121 8.36816C0.172667 7.63613 0.00714944 6.84881 0.000226541 6.05214C-0.00669636 5.25546 0.145114 4.46538 0.446799 3.72801C0.748485 2.99063 1.194 2.32072 1.75736 1.75736C2.32072 1.194 2.99063 0.748485 3.72801 0.446799C4.46538 0.145114 5.25546 -0.00669636 6.05214 0.000226541C6.84881 0.00714944 7.63613 0.172667 8.36816 0.487121C9.10018 0.801575 9.76225 1.25867 10.3157 1.83173C11.4087 2.96334 12.0134 4.47896 11.9998 6.05214C11.9861 7.62532 11.3551 9.13019 10.2426 10.2426C9.13019 11.3551 7.62532 11.9861 6.05214 11.9998C4.47896 12.0134 2.96334 11.4087 1.83173 10.3157V10.3157ZM5.47373 3.07373V6.67373H6.67373V3.07373H5.47373ZM5.47373 7.87373V9.07373H6.67373V7.87373H5.47373Z" />
          </svg>
          </div>
          <div class="flex flex-row items-center">
          <button class="mr-2" v-if="task.description" @click="toggle">
              <svg viewBox="0 0 16 16" class="text-gray-600 w-4 h-4">
              <path class="fill-current" d="M8 12L4.8 15.2V12H1.6C1.17565 12 0.768687 11.8314 0.468629 11.5314C0.168571 11.2313 0 10.8243 0 10.4V2.4C0 1.52 0.72 0.800003 1.6 0.800003H14.4C14.8243 0.800003 15.2313 0.968574 15.5314 1.26863C15.8314 1.56869 16 1.97566 16 2.4V10.4C16 10.8243 15.8314 11.2313 15.5314 11.5314C15.2313 11.8314 14.8243 12 14.4 12H8ZM4 5.6V7.2H5.6V5.6H4ZM7.2 5.6V7.2H8.8V5.6H7.2ZM10.4 5.6V7.2H12V5.6H10.4Z" />
              </svg>
          </button>
          <button class="flex flex-row items-center bg-gray-400 px-2 py-1 rounded" v-if="task.project">
              <div class="w-1 h-1 bg-gray-600 rounded-full"></div> 
              <span class="text-xxs font-medium text-gray-600 ml-1">{{ task.projectText }}</span>
          </button>
          </div>
      </div>
      <!-- Task description -->
      <div class="flex flex-col border-t mt-3 pt-3" v-show="isActive">
          <span class="text-xs font-normal text-gray-600 leading-tight">{{ task.descriptionText }}</span>
      </div>
  </li>
</template>

<script>
export default {
  name: "inProgressTask",
  props: ['task'],
  data() {
    return {
      isActive: false,
    }
  },
  methods: {
    toggle() {
      this.isActive = !this.isActive
    }
  }
}
</script>