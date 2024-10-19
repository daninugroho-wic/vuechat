<template>
  <aside v-show="isVisible"
    class="w-full md:w-1/4 bg-white rounded-l-lg p-6 border border-gray-300 shadow-lg transition-all duration-300">
    <h2 class="text-2xl font-bold cursor-pointer mb-6 text-blue-600 flex justify-between items-center">
      Chat
      <i class="fas fa-ellipsis-v cursor-pointer"></i>
    </h2>

    <!-- Form Pencarian -->
    <div class="mb-6 flex space-x-4 items-center">
      <!-- Input Pencarian -->
      <input v-model="searchQuery" type="text" placeholder="Cari kontak..."
        class="w-full p-2 border border-gray-300 rounded-lg shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500" />

      <!-- Icon Filter -->
      <div class="relative">
        <button @click="toggleDropdown" class="p-2 bg-gray-100 rounded-full hover:bg-gray-200 transition">
          <i class="fas fa-filter text-gray-500"></i>
        </button>

        <!-- Dropdown Filter -->
        <div v-show="isDropdownVisible"
          class="absolute right-0 mt-2 w-40 bg-white border border-gray-300 rounded-lg shadow-lg z-10 transition-all">
          <ul class="py-2">
            <li>
              <button @click="setFilterOption('semua')" class="w-full text-left px-4 py-2 hover:bg-gray-100 transition">
                Semua
              </button>
            </li>
            <li>
              <button @click="setFilterOption('belum dibaca')" class="w-full text-left px-4 py-2 hover:bg-gray-100 transition">
                Belum Dibaca
              </button>
            </li>
            <li>
              <button @click="setFilterOption('favorit')" class="w-full text-left px-4 py-2 hover:bg-gray-100 transition">
                Favorit
              </button>
            </li>
          </ul>
        </div>
      </div>
    </div>

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
</template>

<script>
export default {
  props: {
    isVisible: {
      type: Boolean,
      default: false,
    }
  },
  data() {
    return {
      searchQuery: "",
      filterOption: "semua",
      isDropdownVisible: false
    };
  },
  methods: {
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
