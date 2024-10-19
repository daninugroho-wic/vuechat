<template>
  <div class="min-h-screen flex bg-gray-100 width=device-width, initial-scale=1.0">
    <!-- Sidebar -->
    <div
      class="flex flex-col h-screen justify-between w-[80px] bg-gradient-to-b from-gray-200 to-white shadow-lg p-4 rounded-r-lg">
      <!-- TOP SECTION -->
      <div class="flex flex-col items-center space-y-8">
        <!-- Chat Button -->
        <button class="flex flex-col items-center justify-center p-4 rounded-lg transition-all duration-300"
          @click="setActivePage('chat')" :class="activePage === 'chat'
            ? 'bg-gradient-to-r from-blue-500 to-indigo-600 text-white shadow-lg'
            : 'text-gray-500 hover:bg-gray-300 hover:shadow-lg'">
          <i :class="activePage === 'chat'
            ? 'fas fa-comments h-6 w-6 text-white'
            : 'fas fa-comments h-6 w-6 text-gray-500'"></i>
        </button>

        <!-- Siaran Button -->
        <button class="flex flex-col items-center justify-center p-4 rounded-lg transition-all duration-300"
          @click="setActivePage('siaran')" :class="activePage === 'siaran'
            ? 'bg-gradient-to-r from-blue-500 to-indigo-600 text-white shadow-lg'
            : 'text-gray-500 hover:bg-gray-300 hover:shadow-lg'">
          <i :class="activePage === 'siaran'
            ? 'fas fa-video h-6 w-6 text-white'
            : 'fas fa-video h-6 w-6 text-gray-500'"></i>
        </button>

        <!-- Komunitas Button -->
        <button class="flex flex-col items-center justify-center p-4 rounded-lg transition-all duration-300"
          @click="setActivePage('komunitas')" :class="activePage === 'komunitas'
            ? 'bg-gradient-to-r from-blue-500 to-indigo-600 text-white shadow-lg'
            : 'text-gray-500 hover:bg-gray-300 hover:shadow-lg'">
          <i :class="activePage === 'komunitas'
            ? 'fas fa-users h-6 w-6 text-white'
            : 'fas fa-users h-6 w-6 text-gray-500'"></i>
        </button>
      </div>

      <!-- BOTTOM SECTION -->
      <div class="flex flex-col items-center space-y-8">
        <!-- Settings Button -->
        <button class="flex flex-col items-center justify-center p-4 rounded-lg transition-all duration-300"
          @click="setActivePage('settings')" :class="activePage === 'settings'
            ? 'bg-gradient-to-r from-blue-500 to-indigo-600 text-white shadow-lg'
            : 'text-gray-500 hover:bg-gray-300 hover:shadow-lg'">
          <i :class="activePage === 'settings'
            ? 'fas fa-cog h-6 w-6 text-white'
            : 'fas fa-cog h-6 w-6 text-gray-500'"></i>
        </button>
      </div>
    </div>

    <!-- ASIDE CONTACT-->
    <SideView :isVisible="isSidebarVisible" />



    <!-- MAIN CONTENT -->
    <div class="flex-grow bg-black ">
      <section v-if="activePage === 'page'">
        <PageView />
      </section>

      <!-- Chat -->
      <section v-if="activePage === 'chat'">
        <ChatView :contactName="selectedContact" />
      </section>

      <!-- Siaran -->
      <section v-if="activePage === 'siaran'">
        <h1 class="text-3xl font-bold mb-4 text-blue-600">Siaran Langsung</h1>
        <p class="text-gray-700">Ini adalah halaman siaran langsung.</p>
      </section>

      <!-- Komunitas -->
      <section v-if="activePage === 'komunitas'">
        <h1 class="text-3xl font-bold mb-4 text-blue-600">Komunitas</h1>
        <p class="text-gray-700">Ini adalah halaman komunitas.</p>
      </section>

      <!-- Chat -->
      <section v-if="activePage === 'settings'">
        <h1 class="text-3xl font-bold mb-4 text-blue-600">Settings</h1>
        <p class="text-gray-700">Ini adalah halaman settings.</p>
      </section>
    </div>
  </div>
</template>

<script>
import PageView from "./PageView.vue";
import ChatView from "./ChatView.vue";
import SideView from "./aside/AsideChat.vue";


export default {
  components: {
    PageView,
    ChatView,
    SideView,
  },
  data() {
    return {
      activePage: "page", // Halaman aktif default
      isSidebarVisible: false, // Kontrol visibilitas sidebar
      searchQuery: "", // Menyimpan input pencarian
      filterOption: "semua",
      isDropdownVisible: false
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

    // FILTER
    toggleDropdown() {
      this.isDropdownVisible = !this.isDropdownVisible;
    },
    setFilterOption(option) {
      this.filterOption = option;
      this.isDropdownVisible = false;
    },
  },
};
</script>
