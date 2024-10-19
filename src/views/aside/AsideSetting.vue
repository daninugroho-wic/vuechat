<template>
    <aside class="w-full md:w-1/4 bg-white rounded-lg p-6 border border-gray-300 shadow-lg">
        <!-- Bagian Profil -->
        <div class="flex items-center mb-6">
            <img src="https://example.com/avatar.jpg" alt="Profile Picture"
                class="w-16 h-16 rounded-full mr-4 shadow-lg" />
            <div>
                <h2 class="text-xl font-semibold">~ dannn</h2>
                <span class="text-2xl">🦋</span>
            </div>
        </div>

        <!-- Input Pencarian -->
        <div class="mb-6">
            <input type="text" placeholder="Cari di setelan"
                class="w-full p-2 border border-gray-300 rounded-lg shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500" />
        </div>

        <!-- Daftar Pengaturan -->
        <ul class="space-y-4">
            <li class="flex items-center space-x-3 cursor-pointer">
                <i class="fas fa-user text-lg text-gray-500"></i>
                <span class="text-lg">Akun</span>
            </li>
            <li class="flex items-center space-x-3 cursor-pointer">
                <i class="fas fa-lock text-lg text-gray-500"></i>
                <span class="text-lg">Privasi</span>
            </li>
            <li class="flex items-center space-x-3 cursor-pointer">
                <i class="fas fa-comment text-lg text-gray-500"></i>
                <span class="text-lg">Chat</span>
            </li>
            <li class="flex items-center space-x-3 cursor-pointer">
                <i class="fas fa-bell text-lg text-gray-500"></i>
                <span class="text-lg">Notifikasi</span>
            </li>
            <li class="flex items-center space-x-3 cursor-pointer">
                <i class="fas fa-keyboard text-lg text-gray-500"></i>
                <span class="text-lg">Pintasan keyboard</span>
            </li>
            <li class="flex items-center space-x-3 cursor-pointer">
                <i class="fas fa-question-circle text-lg text-gray-500"></i>
                <span class="text-lg">Bantuan</span>
            </li>
        </ul>

        <!-- Tombol Keluar -->
        <div class="mt-8">
            <button class="flex items-center space-x-3 text-red-500 hover:bg-red-100 p-2 rounded-lg transition">
                <i class="fas fa-sign-out-alt text-lg"></i>
                <span class="text-lg">Keluar</span>
            </button>
        </div>
    </aside>
</template>

<script>
export default {
    name: "AsideSetting",
};
</script>

<style scoped>
aside {
    width: 100%;
    max-width: 300px;
}
</style>