<div class="mb-6 flex space-x-4 items-center">
    <!-- Input Pencarian -->
    <input
      v-model="searchQuery"
      type="text"
      placeholder="Cari kontak..."
      class="w-full p-2 border border-gray-300 rounded-lg shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500"
    />
  
    <!-- Icon Filter -->
    <div class="relative">
      <!-- Tombol untuk Filter -->
      <button @click="toggleDropdown" class="p-2 bg-gray-100 rounded-full hover:bg-gray-200 transition">
        <i class="fas fa-filter text-gray-500"></i>
      </button>
  
      <!-- Dropdown Filter -->
      <div
        v-show="isDropdownVisible"
        class="absolute right-0 mt-2 w-40 bg-white border border-gray-300 rounded-lg shadow-lg z-10 transition-all"
      >
        <ul class="py-2">
          <li>
            <button
              @click="setFilterOption('semua')"
              class="w-full text-left px-4 py-2 hover:bg-gray-100 transition"
            >
              Semua
            </button>
          </li>
          <li>
            <button
              @click="setFilterOption('belum dibaca')"
              class="w-full text-left px-4 py-2 hover:bg-gray-100 transition"
            >
              Belum Dibaca
            </button>
          </li>
          <li>
            <button
              @click="setFilterOption('favorit')"
              class="w-full text-left px-4 py-2 hover:bg-gray-100 transition"
            >
              Favorit
            </button>
          </li>
        </ul>
      </div>
</div>
