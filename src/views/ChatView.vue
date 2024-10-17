<template>
  <div class="min-h-screen flex bg-gray-100">
    <aside v-show="isSidebarVisible" class="w-1/4 bg-white shadow p-4">
      <h2 class="text-lg font-bold">Kontak</h2>
      <ul>
        <li class="flex items-center mb-2 border-b pb-2">
          <img
            src="path/to/john-doe.jpg"
            alt="John Doe"
            class="w-8 h-8 rounded-full mr-2"
          />
          <span>John Doe</span>
        </li>
        <li class="flex items-center mb-2 border-b pb-2">
          <img
            src="path/to/jane-smith.jpg"
            alt="Jane Smith"
            class="w-8 h-8 rounded-full mr-2"
          />
          <span>Jane Smith</span>
        </li>
        <!-- Add more contacts here -->
      </ul>
      <button
        @click="toggleSidebar"
        class="mt-4 bg-blue-500 text-white px-4 py-2 rounded-lg"
      >
        Toggle Sidebar
      </button>
    </aside>

    <div class="flex-grow flex flex-col">
      <header class="bg-white shadow p-4">
        <h1 class="text-lg font-bold">Welcome, {{ username }}</h1>
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

      <footer class="bg-white p-4 flex">
        <input
          v-model="newMessage"
          type="text"
          placeholder="Type a message"
          class="flex-grow border p-2 rounded-lg mr-2"
        />
        <button
          @click="sendMessage"
          class="bg-blue-500 text-white px-4 py-2 rounded-lg"
        >
          Send
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
const isSidebarVisible = ref(true);

const sendMessage = () => {
  if (newMessage.value.trim()) {
    messages.value.push({ text: newMessage.value, isUser: true });
    newMessage.value = "";
  }
};

const toggleSidebar = () => {
  isSidebarVisible.value = !isSidebarVisible.value;
};
</script>

<style scoped>
@media (max-width: 768px) {
  aside {
    display: none; /* Hide sidebar on small screens */
  }
}
</style>
