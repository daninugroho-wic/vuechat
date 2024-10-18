<template>
  <div class="min-h-screen flex bg-gray-100">
    <div class="flex-grow flex flex-col">
      <header
        class="bg-blue-300 p-4 flex flex-col md:flex-row items-center justify-between"
      >
        <h1
          class="text-lg font-bold cursor-pointer mb-2 md:mb-0"
          @click="toggleSidebar"
        >
          Welcome, {{ username }}
        </h1>
        <div class="flex items-center space-x-4 ml-auto">
          <button class="text-blue-500 hover:text-blue-700">
            <i class="fas fa-phone-alt text-lg"></i>
          </button>
          <button class="text-green-500 hover:text-green-700">
            <i class="fas fa-video text-lg"></i>
          </button>
        </div>
      </header>

      <div class="flex-grow p-4 overflow-y-auto">
        <div v-for="(msg, index) in messages" :key="index" class="mb-4">
          <div :class="msg.isUser ? 'text-right' : 'text-left'">
            <p
              :class="
                msg.isUser
                  ? 'bg-blue-500 text-white p-2 rounded-lg inline-block'
                  : 'bg-gray-300 p-2 rounded-lg inline-block'
              "
            >
              {{ msg.text }}
            </p>
          </div>
        </div>
      </div>

      <footer class="bg-white p-4 flex flex-col md:flex-row items-center">
        <div class="flex space-x-2 mb-2 md:mb-0">
          <button class="p-2 bg-gray-200 rounded-full">
            <i class="fas fa-smile text-gray-500 h-6 w-6"></i>
          </button>
          <button class="p-2 bg-gray-200 rounded-full">
            <i class="fas fa-thumbtack text-gray-500 h-6 w-6"></i>
          </button>
          <button class="p-2 bg-gray-200 rounded-full">
            <i class="fas fa-camera text-gray-500 h-6 w-6"></i>
          </button>
        </div>
        <input
          v-model="newMessage"
          type="text"
          placeholder="Type a message"
          class="flex-grow border p-2 rounded-lg mr-2 mb-2 md:mb-0"
        />
        <button
          @click="sendMessage"
          class="bg-blue-500 text-white px-4 py-2 rounded-lg flex items-center mb-2 md:mb-0"
        >
          <i class="fas fa-paper-plane mr-2"></i> Send
        </button>
        <button
          @click="startRecording"
          class="bg-red-500 text-white px-4 py-2 rounded-lg ml-0 md:ml-2 flex items-center"
        >
          <i class="fas fa-record-vinyl mr-2"></i> Record
        </button>
      </footer>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const username = localStorage.getItem("username");
const newMessage = ref("");
const messages = ref([
  { text: "Hello! How are you?", isUser: false },
  { text: "I am fine, thanks!", isUser: true },
]);

const sendMessage = () => {
  if (newMessage.value.trim()) {
    messages.value.push({ text: newMessage.value, isUser: true });
    newMessage.value = "";
  }
};
</script>

<style scoped>
@media (max-width: 768px) {
  aside {
    width: 100px;
    /* Show only profile picture */
    transition: width 0.3s;
  }

  aside img {
    width: 40px;
    /* Adjust profile picture size */
    height: 40px;
  }

  aside ul {
    display: none;
    /* Hide the list when sidebar is collapsed */
  }
}
</style>
