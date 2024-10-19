<template>
  <div class="min-h-screen flex bg-gray-100">
    <div class="flex-grow flex flex-col bg-white border-l border-gray-200 overflow-hidden">
      <!-- Header -->
      <header class="bg-blue-500 p-4 flex items-center justify-between border-b border-gray-200">
        <!-- Bagian Welcome dan Profil -->
        <div class="flex items-center space-x-4">
          <!-- Profil Icon -->
          <div class="relative">
            <img src="profile-picture-url.jpg" alt="Profile Picture"
              class="w-10 h-10 rounded-full border-2 border-white cursor-pointer hover:opacity-80 transition-opacity duration-300">
          </div>
          <h1 class="text-white text-2xl font-semibold cursor-pointer">
            {{ username }}
          </h1>
        </div>

        <!-- Bagian tombol telepon, video call, search, dan titik tiga -->
        <div class="flex items-center space-x-6">
          <!-- Telepon -->
          <button class="text-white hover:text-gray-300">
            <i class="fas fa-phone-alt text-lg"></i>
          </button>

          <!-- Video Call -->
          <button class="text-white hover:text-gray-300">
            <i class="fas fa-video text-lg"></i>
          </button>

          <!-- Pencarian -->
          <button class="text-white hover:text-gray-300">
            <i class="fas fa-search text-lg"></i>
          </button>

          <!-- Titik Tiga (More options) -->
          <button class="text-white hover:text-gray-300">
            <i class="fas fa-ellipsis-v text-lg"></i>
          </button>
        </div>
      </header>

      <!-- Chat Messages -->
      <div class="flex-grow p-4 overflow-y-auto">
        <div class="space-y-4">
          <div v-for="(msg, index) in messages" :key="index"
            :class="{ 'text-right': msg.isUser, 'text-left': !msg.isUser }" class="flex items-start space-x-2">
            <!-- Message from the user -->
            <div v-if="msg.isUser" class="ml-auto">
              <div class="bg-blue-500 text-white p-3 rounded-lg max-w-xs break-words">
                {{ msg.text }}
              </div>
            </div>
            <!-- Message from the other party -->
            <div v-else class="mr-auto rounded-lg">
              <div class="bg-gray-200 text-gray-700 p-3 rounded-lg max-w-xs break-words">
                {{ msg.text }}
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Footer - Input Area -->
      <footer class="bg-blue-50 p-4 flex items-center border-t border-gray-200 rounded-lg space-x-4">
        <div class="flex space-x-2 items-center">
          <!-- Emoji, Attachments, Camera Icons -->
          <button class="p-2 bg-gray-100 rounded-full hover:bg-gray-200 transition ease-in-out duration-150">
            <i class="fas fa-smile text-gray-500"></i>
          </button>
          <button class="p-2 bg-gray-100 rounded-full hover:bg-gray-200 transition ease-in-out duration-150">
            <i class="fas fa-paperclip text-gray-500"></i>
          </button>
          <button class="p-2 bg-gray-100 rounded-full hover:bg-gray-200 transition ease-in-out duration-150">
            <i class="fas fa-camera text-gray-500"></i>
          </button>
        </div>

        <!-- Message Input and Send Button -->
        <input v-model="newMessage" type="text" placeholder="Type a message..."
          class="flex-grow bg-gray-100 border border-gray-300 p-2 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 transition duration-150 ease-in-out" />

        <button @click="sendMessage"
          class="ml-2 bg-blue-500 text-white px-4 py-2 rounded-lg hover:bg-blue-600 transition duration-150 ease-in-out focus:outline-none">
          <i class="fas fa-paper-plane"></i>
        </button>
      </footer>

    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: "User",
      messages: [],
      newMessage: "",
    };
  },
  methods: {
    sendMessage() {
      if (this.newMessage.trim() !== "") {
        this.messages.push({ text: this.newMessage, isUser: true });
        this.newMessage = "";
      }
    },
  },
};
</script>

<style scoped>
/* Custom styles if needed */
</style>

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
