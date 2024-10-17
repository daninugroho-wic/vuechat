<template>
  <div class="min-h-screen flex bg-gray-100">
    <div
      class="w-[80px] bg-white shadow-lg p-4 flex flex-col items-center space-y-6"
    >
      <button
        class="flex flex-col items-center justify-center p-4 rounded-lg transition-all duration-300"
        @click="setActivePage('chat')"
        :class="
          activePage === 'chat'
            ? 'bg-gradient-to-r from-blue-400 to-blue-600 text-white shadow-lg'
            : 'text-gray-500 hover:bg-gray-200 hover:shadow-md'
        "
      >
        <i
          :class="
            activePage === 'chat'
              ? 'fas fa-comments h-6 w-6 text-white'
              : 'fas fa-comments h-6 w-6 text-gray-500'
          "
        ></i>
      </button>

      <button
        class="flex flex-col items-center justify-center p-4 rounded-lg transition-all duration-300"
        @click="setActivePage('siaran')"
        :class="
          activePage === 'siaran'
            ? 'bg-gradient-to-r from-blue-400 to-blue-600 text-white shadow-lg'
            : 'text-gray-500 hover:bg-gray-200 hover:shadow-md'
        "
      >
        <i
          :class="
            activePage === 'siaran'
              ? 'fas fa-video h-6 w-6 text-white'
              : 'fas fa-video h-6 w-6 text-gray-500'
          "
        ></i>
      </button>

      <button
        class="flex flex-col items-center justify-center p-4 rounded-lg transition-all duration-300"
        @click="setActivePage('komunitas')"
        :class="
          activePage === 'komunitas'
            ? 'bg-gradient-to-r from-blue-400 to-blue-600 text-white shadow-lg'
            : 'text-gray-500 hover:bg-gray-200 hover:shadow-md'
        "
      >
        <i
          :class="
            activePage === 'komunitas'
              ? 'fas fa-users h-6 w-6 text-white'
              : 'fas fa-users h-6 w-6 text-gray-500'
          "
        ></i>
      </button>
    </div>

    <div class="flex-grow bg-white shadow p-6">
      <section v-if="activePage === 'chat'">
        <ChatView />
      </section>

      <section v-if="activePage === 'siaran'">
        <h1 class="text-2xl font-bold mb-4">Siaran Langsung</h1>
        <p>Ini adalah halaman siaran langsung.</p>
      </section>

      <section v-if="activePage === 'komunitas'">
        <h1 class="text-2xl font-bold mb-4">Komunitas</h1>
        <p>Ini adalah halaman komunitas.</p>
      </section>
    </div>
  </div>
</template>

<script>
import ChatView from "./ChatView.vue"; // Import ChatView

export default {
  components: {
    ChatView, // Daftarkan ChatView sebagai komponen
  },
  data() {
    return {
      activePage: "chat", // Default halaman yang aktif
    };
  },
  methods: {
    setActivePage(page) {
      this.activePage = page;
    },
  },
};
</script>
