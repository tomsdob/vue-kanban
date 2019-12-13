<template>
  <div class="flex h-screen overflow-hidden">
    <Menu class="xl:block xl:relative z-10" id="Menu" />
    <div class="flex-1 flex flex-col">
      <!-- User navigation -->
      <div class="flex flex-row justify-between xl:justify-end items-center p-4 border-b bg-white">
        <button @click="openMenu" class="focus:outline-none xl:hidden">
            <svg viewBox="0 0 20 20" class="text-gray-600 w-6 h-6">
                <path class="fill-current" d="M0 3H20V5H0V3ZM0 9H20V11H0V9ZM0 15H20V17H0V15Z" />
            </svg>
        </button>
        <div class="flex flex-row justify-center items-center">
          <Notifications class="z-0" />
          <div class="flex items-center justify-center w-10 h-10 bg-green-500 rounded-full">
            <svg viewBox="0 0 20 20" class="text-green-700 w-6 h-6">
              <path class="fill-current" d="M10 20C7.34784 20 4.8043 18.9464 2.92893 17.0711C1.05357 15.1957 0 12.6522 0 10C0 7.34784 1.05357 4.8043 2.92893 2.92893C4.8043 1.05357 7.34784 0 10 0C12.6522 0 15.1957 1.05357 17.0711 2.92893C18.9464 4.8043 20 7.34784 20 10C20 12.6522 18.9464 15.1957 17.0711 17.0711C15.1957 18.9464 12.6522 20 10 20ZM7 6V8C7 8.79565 7.31607 9.55871 7.87868 10.1213C8.44129 10.6839 9.20435 11 10 11C10.7956 11 11.5587 10.6839 12.1213 10.1213C12.6839 9.55871 13 8.79565 13 8V6C13 5.20435 12.6839 4.44129 12.1213 3.87868C11.5587 3.31607 10.7956 3 10 3C9.20435 3 8.44129 3.31607 7.87868 3.87868C7.31607 4.44129 7 5.20435 7 6ZM3.35 14.44C4.08105 15.5332 5.07031 16.4292 6.23022 17.0489C7.39013 17.6686 8.68493 17.9928 10 17.9928C11.3151 17.9928 12.6099 17.6686 13.7698 17.0489C14.9297 16.4292 15.919 15.5332 16.65 14.44C14.5638 13.4824 12.2955 12.9866 10 12.9866C7.70454 12.9866 5.43616 13.4824 3.35 14.44Z" />
            </svg>
          </div>
        </div>
      </div>
      <!-- Add task header -->
      <div class="flex flex-row flex-shrink-0 justify-between items-center border-b p-4">
        <h1 class="text-3xl text-gray-900 font-medium">Tasks</h1>
        <button class="flex flex-row bg-gray-800 justify-center items-center text-white text-sm rounded px-3 py-2">
          <svg viewBox="0 0 14 14" class="w-4 h-4 text-white mr-3">
            <path class="fill-current" d="M7.69989 6.30011L7.69989 -0.699825H6.30011L6.30011 6.30011L-0.699826 6.30011L-0.699827 7.6999L6.30011 7.6999L6.3001 14.6998H7.6999L7.69989 7.6999L14.6998 7.6999L14.6998 6.30011L7.69989 6.30011Z" />
          </svg>
          <span>Add task</span>
        </button>
      </div>
      <!-- Tasks -->
      <div class="flex-1 flex flex-row overflow-auto h-full p-4" style="max-width:100vw;">
        <div class="flex flex-col flex-shrink-0 bg-gray-200 rounded p-3 mr-2 w-64">
          <h2 class="flex-shrink-0 text-sm font-medium text-gray-600 leading-none mb-3">To-do</h2>
          <div class="flex-1 min-h-0 overflow-y-auto">
            <!-- Task list -->
            <draggable :options="{ animation: 250, group: 'tasks' }" tag="ul" class="min-h-full -mb-2 overflow-x-hidden">
              <toDoTask v-for="task in toDoList" :key="task.id" :task="task"/>
            </draggable>
          </div>
        </div>
        <div class="flex flex-col flex-shrink-0 bg-gray-200 rounded p-3 mr-2 w-64">
          <h2 class="flex-shrink-0 text-sm font-medium text-gray-600 leading-none mb-3">In progress</h2>
          <div class="flex-1 min-h-0 overflow-y-auto">
            <!-- Task list -->
            <draggable :options="{ animation: 250, group: 'tasks' }" tag="ul" class="min-h-full -mb-2 overflow-x-hidden">
              <inProgressTask v-for="task in inProgressList" :key="task.id" :task="task"/>
            </draggable>
          </div>
        </div>
        <div class="flex flex-col flex-shrink-0 bg-gray-200 rounded p-3 mr-2 w-64">
          <h2 class="flex-shrink-0 text-sm font-medium text-gray-600 leading-none mb-3">Completed</h2>
          <div class="flex-1 min-h-0 overflow-y-auto">
            <!-- Task list -->
            <draggable :options="{ animation: 250, group: 'tasks' }" tag="ul" class="min-h-full -mb-2 overflow-x-hidden">
              <CompletedTask v-for="task in completedList" :key="task.id" :task="task"/>
            </draggable>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Draggable from 'vuedraggable'
import Menu from './Menu.vue'
import Notifications from './Notifications.vue'

//Tasks
import ToDoTask from './Tasks/ToDoTask.vue'
import InProgressTask from './Tasks/InProgressTask.vue'
import CompletedTask from './Tasks/CompletedTask.vue'

export default {
  name: "Tasks",
  components: {
    Draggable,
    Menu,
    Notifications,
    ToDoTask,
    InProgressTask,
    CompletedTask
  },
  methods: {
    openMenu(){
      const menu = document.getElementById("Menu");
      menu.classList.remove("hidden");
    }
  },
  data() {
    return {
      menuOpen: false,
      toDoList: [
        {
          id: 0,
          title: "Create a Kanban board design with TailwindCSS elements",
          date: "Dec 27",
          important: true,
          project: true,
          projectText: "All projects",
          description: false,
          descriptionText: "",
        },
        {
          id: 1,
          title: "Write the Kanban board design with TailwindCSS and VueJS",
          date: "Dec 29",
          important: false,
          project: true,
          projectText: "All projects",
          description: true,
          descriptionText: "Search the internet for some additional frameworks and VueJS plugins."
        },
        {
          id: 2,
          title: "Look through the statistics which include Ukraine",
          date: "Jan 12",
          important: false,
          project: true,
          projectText: "Goodaff",
          description: false,
          descriptionText: ""
        },
      ],
      inProgressList: [
        {
          id: 0,
          title: "Create the design for the new landing page",
          date: "Nov 27",
          important: true,
          project: true,
          projectText: "All projects",
          description: false,
          descriptionText: ""
        },
        {
          id: 1,
          title: "Look at the coding examples on VueJS tutorials",
          date: "Nov 28",
          important: false,
          project: false,
          projectText: "",
          description: false,
          descriptionText: ""
        },
        {
          id: 2,
          title: "Write the new landing page design",
          date: "Nov 28",
          important: false,
          project: true,
          projectText: "All projects",
          description: true,
          descriptionText: "Look up on the internet what is the difference."
        },
        {
          id: 3,
          title: "Read about the new Figma update",
          date: "Dec 1",
          important: false,
          project: false,
          projectText: "",
          description: false,
          descriptionText: ""
        },
      ],
      completedList: [
        {
          id: 0,
          title: "Learn Vue",
          date: "Nov 2",
          important: true,
          project: false,
          projectText: "",
          description: true,
          descriptionText: "Look at examples on Google."
        },
        {
          id: 1,
          title: "Check out the new TailwindCSS update",
          date: "Nov 1",
          important: true,
          project: false,
          projectText: "",
          description: true,
          descriptionText: "There's supposed to be a new update coming soon."
        },
      ],
    }
  }
}
</script>
