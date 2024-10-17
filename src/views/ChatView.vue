<template>
  <div class="flex flex-col h-screen bg-gray-100">
    <!-- Navbar -->
    <nav class="bg-blue-600 p-4 text-white">
      <div class="flex justify-between items-center">
        <h1 class="text-xl font-bold">Chat App</h1>
        <button
          class="bg-red-500 hover:bg-red-700 text-white px-4 py-2 rounded-md"
        >
          Logout
        </button>
      </div>
    </nav>

    <!-- Main Container for Chat -->
    <div class="flex-grow p-4">
      <div class="max-w-4xl mx-auto bg-white p-6 rounded-lg shadow-md">
        <div class="flex flex-col h-[500px] overflow-hidden">
          <!-- Messages Area -->
          <div class="flex-grow overflow-y-auto mb-4">
            <div v-for="(msg, index) in messages" :key="index" class="mb-2">
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

          <!-- Input Area -->
          <div class="flex items-center">
            <input
              v-model="newMessage"
              type="text"
              placeholder="Type a message..."
              class="flex-grow border border-gray-300 p-2 rounded-lg mr-2"
            />
            <button
              @click="sendMessage"
              class="bg-blue-500 text-white px-4 py-2 rounded-lg"
            >
              Send
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

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
