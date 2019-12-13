<template>
    <div class="flex relative">
        <div @click="notificationsClosed = !notificationsClosed" class="bg-transparent w-screen h-screen top-0 left-0" :class="{ 'fixed' : !notificationsClosed , 'hidden' : notificationsClosed }"></div>
        <button @click="notificationsClosed = !notificationsClosed" class="flex justify-center items-center mr-4 z-10">
            <svg viewBox="0 0 20 20" class="text-gray-600 w-6 h-6">
                <path class="fill-current" d="M6 8.00001V15H14V8.00001C14 6.93914 13.5786 5.92173 12.8284 5.17158C12.0783 4.42144 11.0609 4.00001 10 4.00001C8.93913 4.00001 7.92172 4.42144 7.17157 5.17158C6.42143 5.92173 6 6.93914 6 8.00001ZM8.03 2.33001C7.9844 2.04432 8.00132 1.75214 8.0796 1.47362C8.15788 1.19511 8.29565 0.93689 8.48341 0.716787C8.67117 0.496684 8.90444 0.319935 9.16714 0.198735C9.42983 0.0775356 9.71569 0.0147705 10.005 0.0147705C10.2943 0.0147705 10.5802 0.0775356 10.8429 0.198735C11.1056 0.319935 11.3388 0.496684 11.5266 0.716787C11.7143 0.93689 11.8521 1.19511 11.9304 1.47362C12.0087 1.75214 12.0256 2.04432 11.98 2.33001C13.1557 2.741 14.1743 3.50765 14.8946 4.52364C15.615 5.53962 16.0013 6.75458 16 8.00001V14L19 16V17H1V16L4 14V8.00001C3.99945 6.75337 4.38723 5.53751 5.10945 4.52138C5.83167 3.50526 6.85247 2.73932 8.03 2.33001ZM12 18C12 18.5304 11.7893 19.0391 11.4142 19.4142C11.0391 19.7893 10.5304 20 10 20C9.46957 20 8.96086 19.7893 8.58579 19.4142C8.21071 19.0391 8 18.5304 8 18H12Z" />
            </svg>
        </button>
        <div class="flex flex-col justify-start items-start absolute top-0 right-0 w-64 h-auto bg-white shadow-xl rounded p-3 mt-8 mr-4 z-10" :class="{ 'block' : !notificationsClosed , 'hidden' : notificationsClosed }">
            <span class="text-normal font-medium text-gray-900 mb-2">Notifications</span>
            <div class="flex flex-col justify-start items-start py-2 border-b w-full">
                <span class="text-sm font-medium text-gray-600 mb-2 leading-none">You have a new notification!</span>
                <span class="text-xs font-normal text-gray-600 leading-none">Dec 27</span>
            </div>
            <div class="flex flex-col justify-start items-start py-2 border-b w-full">
                <span class="text-sm font-medium text-gray-600 mb-2 leading-none">You have a new notification!</span>
                <span class="text-xs font-normal text-gray-600 leading-none">Dec 27</span>
            </div>
            <div class="flex flex-col justify-start items-start py-2 border-b w-full">
                <span class="text-sm font-medium text-gray-600 mb-2 leading-none">You have a new notification!</span>
                <span class="text-xs font-normal text-gray-600 leading-none">Dec 27</span>
            </div>
        </div>
    </div>
</template>

<script>

export default {
  name: "notifications",
  data() {
    return {
       notificationsClosed: true,
    }
  }
}
</script>