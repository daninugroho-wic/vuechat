<template>
  <div class="min-h-screen flex bg-gray-100">
    <!-- Sidebar -->
    <div
      class="w-[80px] bg-white shadow-lg p-4 flex flex-col items-center space-y-6"
    >
      <!-- Chat Button -->
      <button
        class="flex flex-col items-center justify-center p-4 rounded-lg transition-all duration-300"
        @click="toggleSidebar"
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
    <!-- kontak -->
    <aside
      v-show="isSidebarVisible"
      class="w-full md:w-1/4 bg-white rounded-sm p-6 border border-blue-300 shadow-lg transition-all duration-300"
    >
      <h2 class="text-xl font-bold cursor-pointer mb-6" @click="toggleSidebar">
        Kontak
      </h2>
      <ul>
        <li
          class="flex items-center mb-6 p-4 border-b border-blue-300 pb-4 transition-all duration-300 hover:bg-gray-100 rounded-lg"
        >
          <img
            src="path/to/john-doe.jpg"
            alt="Warno"
            class="w-12 h-12 rounded-full mr-4 shadow-md"
          />
          <div class="text-lg font-semibold">Warno</div>
        </li>
        <li
          class="flex items-center mb-6 p-4 border-b border-blue-300 pb-4 transition-all duration-300 hover:bg-gray-100 rounded-lg"
        >
          <img
            src="path/to/jane-smith.jpg"
            alt="Jimun"
            class="w-12 h-12 rounded-full mr-4 shadow-md"
          />
          <div class="text-lg font-semibold">Jimun</div>
        </li>
      </ul>
    </aside>

    <div class="flex-grow bg-white shadow p-6">
      <section v-if="activePage === 'page'">
        <PageView />
      </section>

      <section v-if="activePage === 'siaran'">
        <h1 class="text-2xl font-bold mb-4">Siaran Langsung</h1>
        <p>Ini adalah halaman siaran langsung.</p>
      </section>

      <section v-if="activePage === 'komunitas'">
        <h1 class="text-2xl font-bold mb-4">Komunitas</h1>
        <p>Ini adalah halaman komunitas.</p>
      </section>

      <section v-if="activePage === 'chat'">
        <ChatView :contactName="selectedContact" />
      </section>
    </div>
  </div>
</template>

<script>
import PageView from "./PageView.vue";
import ChatView from "./ChatView.vue";

export default {
  components: {
    PageView,
    ChatView,
  },
  data() {
    return {
      activePage: "page", // Halaman aktif default
      isSidebarVisible: false, // Kontrol visibilitas sidebar
      selectedContact: null, // Untuk menyimpan nama kontak yang dipilih
    };
  },
  methods: {
    setActivePage(page) {
      this.activePage = page;
      if (page === "chat") {
        this.isSidebarVisible = true; // Sidebar muncul saat halaman chat aktif
      } else {
        this.isSidebarVisible = false; // Sembunyikan sidebar di halaman lain
      }
    },
    toggleSidebar() {
      this.isSidebarVisible = !this.isSidebarVisible;
      this.setActivePage("chat"); // Set halaman menjadi 'chat'
    },
  },
};
</script>
