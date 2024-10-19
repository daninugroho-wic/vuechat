<template>
  <div class="min-h-screen flex bg-gray-100">
    <!-- Sidebar -->
    <div
      class="w-[80px] bg-gradient-to-b from-gray-200 to-white shadow-lg p-4 flex flex-col items-center space-y-8 rounded-r-lg">
      <!-- Chat Button -->
      <button class="flex flex-col items-center justify-center p-4 rounded-lg transition-all duration-300"
        @click="setActivePage('chat')" :class="activePage === 'chat'
          ? 'bg-gradient-to-r from-blue-500 to-indigo-600 text-white shadow-lg'
          : 'text-gray-500 hover:bg-gray-300 hover:shadow-lg'
          ">
        <i :class="activePage === 'chat'
          ? 'fas fa-comments h-6 w-6 text-white'
          : 'fas fa-comments h-6 w-6 text-gray-500'
          "></i>
        <span class="text-xs mt-2">Chat</span>
      </button>

      <!-- Siaran Button -->
      <button class="flex flex-col items-center justify-center p-4 rounded-lg transition-all duration-300"
        @click="setActivePage('siaran')" :class="activePage === 'siaran'
          ? 'bg-gradient-to-r from-blue-500 to-indigo-600 text-white shadow-lg'
          : 'text-gray-500 hover:bg-gray-300 hover:shadow-lg'
          ">
        <i :class="activePage === 'siaran'
          ? 'fas fa-video h-6 w-6 text-white'
          : 'fas fa-video h-6 w-6 text-gray-500'
          "></i>
        <span class="text-xs mt-2">Siaran</span>
      </button>
      <!-- Komunitas Button -->
      <button class="flex flex-col items-center justify-center p-4 rounded-lg transition-all duration-300"
        @click="setActivePage('komunitas')" :class="activePage === 'komunitas'
          ? 'bg-gradient-to-r from-blue-500 to-indigo-600 text-white shadow-lg'
          : 'text-gray-500 hover:bg-gray-300 hover:shadow-lg'
          ">
        <i :class="activePage === 'komunitas'
          ? 'fas fa-users h-6 w-6 text-white'
          : 'fas fa-users h-6 w-6 text-gray-500'
          "></i>
        <span class="text-xs mt-2">Siaran</span>
      </button>
    </div>

    <!-- Kontak Sidebar -->
    <aside v-show="isSidebarVisible"
      class="w-full md:w-1/4 bg-white rounded-l-lg p-6 border border-gray-300 shadow-lg transition-all duration-300">
      <h2 class="text-2xl font-bold cursor-pointer mb-6 text-blue-600 flex justify-between items-center">
        Kontak
        <i class="fas fa-ellipsis-v cursor-pointer"></i>
      </h2>

      <!-- Form Pencarian -->
      <div class="mb-6 flex space-x-4 items-center">
        <!-- Input Pencarian -->
        <input v-model="searchQuery" type="text" placeholder="Cari kontak..."
          class="w-full p-2 border border-gray-300 rounded-lg shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500" />

        <!-- Icon Filter -->
        <div class="relative">
          <!-- Tombol untuk Filter -->
          <button @click="toggleDropdown" class="p-2 bg-gray-100 rounded-full hover:bg-gray-200 transition">
            <i class="fas fa-filter text-gray-500"></i>
          </button>

          <!-- Dropdown Filter -->
          <div v-show="isDropdownVisible"
            class="absolute right-0 mt-2 w-40 bg-white border border-gray-300 rounded-lg shadow-lg z-10 transition-all">
            <ul class="py-2">
              <li>
                <button @click="setFilterOption('semua')"
                  class="w-full text-left px-4 py-2 hover:bg-gray-100 transition">
                  Semua
                </button>
              </li>
              <li>
                <button @click="setFilterOption('belum dibaca')"
                  class="w-full text-left px-4 py-2 hover:bg-gray-100 transition">
                  Belum Dibaca
                </button>
              </li>
              <li>
                <button @click="setFilterOption('favorit')"
                  class="w-full text-left px-4 py-2 hover:bg-gray-100 transition">
                  Favorit
                </button>
              </li>
            </ul>
          </div>
        </div>
      </div>


      <!-- Pembatas Grid -->
      <hr class="border-gray-300 mb-6">

      <ul>
        <ul>
          <li v-for="contact in filteredContacts" :key="contact.name"
            class="flex items-center mb-6 p-4 border-b border-gray-300 pb-4 transition-all duration-300 hover:bg-blue-50 rounded-lg">
            <img src="path/to/avatar.jpg" :alt="contact.name" class="w-12 h-12 rounded-full mr-4 shadow-lg" />
            <div class="text-lg font-semibold">{{ contact.name }}</div>
          </li>
        </ul>
        <li
          class="flex items-center mb-6 p-4 border-b border-gray-300 pb-4 transition-all duration-300 hover:bg-blue-50 rounded-lg">
          <img src="path/to/john-doe.jpg" alt="Warno" class="w-12 h-12 rounded-full mr-4 shadow-lg" />
          <div class="text-lg font-semibold">Warno</div>
        </li>
        <li
          class="flex items-center mb-6 p-4 border-b border-gray-300 pb-4 transition-all duration-300 hover:bg-blue-50 rounded-lg">
          <img src="path/to/jane-smith.jpg" alt="Jimun" class="w-12 h-12 rounded-full mr-4 shadow-lg" />
          <div class="text-lg font-semibold">Jimun</div>
        </li>
      </ul>
    </aside>


    <!-- Main Content -->
    <div class="flex-grow bg-white shadow-lg p-8 rounded-lg ml-4">
      <section v-if="activePage === 'page'">
        <PageView />
      </section>

      <!-- Siaran Content -->
      <section v-if="activePage === 'siaran'">
        <h1 class="text-3xl font-bold mb-4 text-blue-600">Siaran Langsung</h1>
        <p class="text-gray-700">Ini adalah halaman siaran langsung.</p>
      </section>

      <!-- Komunitas Content -->
      <section v-if="activePage === 'komunitas'">
        <h1 class="text-3xl font-bold mb-4 text-blue-600">Komunitas</h1>
        <p class="text-gray-700">Ini adalah halaman komunitas.</p>
      </section>

      <!-- Chat Content -->
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
