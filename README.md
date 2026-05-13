<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lumi Choice - Pre-Order</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        purple: {
                            50: '#faf5ff',
                            100: '#f3e8ff',
                            500: '#a855f7',
                            600: '#9333ea',
                            700: '#7e22ce',
                            900: '#581c87',
                        }
                    }
                }
            }
        }
    </script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap');
        body { font-family: 'Poppins', sans-serif; }
        ::-webkit-scrollbar { width: 8px; }
        ::-webkit-scrollbar-track { background: #f3e8ff; }
        ::-webkit-scrollbar-thumb { background: #a855f7; border-radius: 4px; }
    </style>
</head>
<body class="bg-purple-50 text-purple-900 min-h-screen">

    <header class="bg-white shadow-sm sticky top-0 z-50">
        <div class="max-w-md mx-auto px-4 py-3 flex items-center justify-center gap-3">
            <img src="LL.png" alt="Lumi Choice Logo" class="h-12 w-auto object-contain drop-shadow-md rounded-full bg-purple-100" onerror="this.src='data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSI0OCIgaGVpZ2h0PSI0OCIgdmlld0JveD0iMCAwIDI0IDI0IiBmaWxsPSJub25lIiBzdHJva2U9IiM5MzMzZWEiIHN0cm9rZS13aWR0aD0iMiIgY3Vyb3ItbGluZWNhcD0icm91bmQiIHN0cm9rZS1saW5lam9pbj0icm91bmQiPjxjaXJjbGUgY3g9IjEyIiBjeT0iMTIiIHI9IjEwIi8+PHBhdGggZD0iTThgMTJoOCIvPjwvc3ZnPg=='">
            <div class="text-center">
                <h1 class="text-xl font-bold text-purple-700 leading-tight">Lumi Choice</h1>
                <p class="text-xs text-purple-500 font-medium tracking-widest">CHOICE YOUR TASTE</p>
            </div>
        </div>
    </header>

    <div id="customerView" class="block pb-24">
        <main class="max-w-md mx-auto mt-6 px-4">
            
            <!-- Banner/Info -->
            <div class="bg-purple-100 rounded-xl p-4 mb-6 text-sm text-purple-800 border border-purple-200 text-center shadow-sm">
                🌟 <b>Pre-Order Dibuka!</b> Yuk, pesan menu favoritmu sekarang sebelum kehabisan!
            </div>

            <!-- Tempat Menu Render Otomatis -->
            <h2 class="text-lg font-bold mb-3 flex items-center gap-2">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-purple-600" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253" /></svg>
                Pilih Menu
            </h2>
            
            <!-- Grid Dinamis -->
            <div id="menuContainer" class="grid grid-cols-2 gap-4 mb-8">
                <!-- Daftar menu akan dimuat oleh JavaScript di sini -->
            </div>

            <!-- Form Pemesanan -->
            <h2 class="text-lg font-bold mb-3 flex items-center gap-2">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-purple-600" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12h6m-6 4h6m2 5H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z" /></svg>
                Detail Pemesan
            </h2>
            
            <form id="orderForm" class="space-y-4 bg-white p-5 rounded-2xl shadow-sm border border-purple-100">
                <div>
                    <label class="block text-sm font-medium mb-1">Nama Lengkap</label>
                    <input type="text" id="custName" required placeholder="Masukkan nama Anda" class="w-full border border-gray-300 rounded-lg px-3 py-2 focus:ring-2 focus:ring-purple-500 focus:border-purple-500 outline-none transition-all">
                </div>

                <div>
                    <label class="block text-sm font-medium mb-1">Nomor WhatsApp</label>
                    <input type="tel" id="custWa" required placeholder="08xxxxxxxxxx" class="w-full border border-gray-300 rounded-lg px-3 py-2 focus:ring-2 focus:ring-purple-500 focus:border-purple-500 outline-none transition-all">
                </div>

                <div class="grid grid-cols-2 gap-3">
                    <div>
                        <label class="block text-sm font-medium mb-1">Tgl Pengambilan</label>
                        <input type="date" id="pickupDate" required class="w-full border border-gray-300 rounded-lg px-3 py-2 focus:ring-2 focus:ring-purple-500 focus:border-purple-500 outline-none transition-all" onchange="checkQuotaUI()">
                    </div>
                    <div>
                        <label class="block text-sm font-medium mb-1">Waktu (STID)</label>
                        <select id="pickupTime" required class="w-full border border-gray-300 rounded-lg px-3 py-2 focus:ring-2 focus:ring-purple-500 focus:border-purple-500 outline-none transition-all">
                            <option value="" disabled selected>Pilih Waktu</option>
                            <option value="10.00 - 10.30">10.00 - 10.30</option>
                            <option value="13.00 - 14.00">13.00 - 14.00</option>
                        </select>
                    </div>
                </div>
                
                <div id="quotaWarning" class="hidden text-xs text-red-600 bg-red-50 p-2 rounded border border-red-200">
                    Maaf, kuota untuk tanggal tersebut penuh (Tersisa <span id="quotaSisa">0</span> pcs). Silakan pilih tanggal lain.
                </div>

                <div id="loadingQuota" class="hidden text-xs text-purple-600 bg-purple-50 p-2 rounded border border-purple-200 flex items-center gap-2">
                    <svg class="animate-spin h-4 w-4 text-purple-600" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"><circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle><path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path></svg>
                    Memeriksa ketersediaan kuota...
                </div>

                <div>
                    <label class="block text-sm font-medium mb-1">Metode Pembayaran</label>
                    <div class="grid grid-cols-2 gap-3">
                        <label class="flex items-center justify-center gap-2 border border-gray-300 rounded-lg px-3 py-3 cursor-pointer hover:bg-purple-50 has-[:checked]:border-purple-600 has-[:checked]:bg-purple-50 transition-all">
                            <input type="radio" name="payment" value="QRIS" class="w-4 h-4 text-purple-600 focus:ring-purple-500" checked>
                            <span class="text-sm font-medium">QRIS</span>
                        </label>
                        <label class="flex items-center justify-center gap-2 border border-gray-300 rounded-lg px-3 py-3 cursor-pointer hover:bg-purple-50 has-[:checked]:border-purple-600 has-[:checked]:bg-purple-50 transition-all">
                            <input type="radio" name="payment" value="Cash" class="w-4 h-4 text-purple-600 focus:ring-purple-500">
                            <span class="text-sm font-medium">Cash</span>
                        </label>
                    </div>
                </div>
            </form>
        </main>

        <!-- Footer / Tombol Admin Rahasia -->
        <footer class="mt-12 mb-6 text-center text-xs text-purple-300 flex justify-center items-center gap-2">
            &copy; 2026 Lumi Choice. 
            <button onclick="document.getElementById('adminLoginModal').classList.remove('hidden')" class="hover:text-purple-600 transition-colors">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-3 w-3" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 15v2m-6 4h12a2 2 0 002-2v-6a2 2 0 00-2-2H6a2 2 0 00-2 2v6a2 2 0 002 2zm10-10V7a4 4 0 00-8 0v4h8V7z" /></svg>
            </button>
        </footer>

        <!-- Floating Checkout Bar -->
        <div class="fixed bottom-0 left-0 right-0 bg-white border-t border-purple-100 shadow-[0_-4px_6px_-1px_rgba(0,0,0,0.05)] z-40">
            <div class="max-w-md mx-auto px-4 py-3 flex items-center justify-between gap-4">
                <div class="flex-1">
                    <p class="text-xs text-gray-500 mb-0.5">Total Harga (<span id="totalItems">0</span> pcs)</p>
                    <p class="text-lg font-bold text-purple-700" id="totalPriceDisplay">Rp 0</p>
                </div>
                <button type="button" id="submitBtn" onclick="processOrder()" class="flex-1 bg-purple-600 hover:bg-purple-700 text-white font-semibold py-3 px-4 rounded-xl shadow-md transition-all flex justify-center items-center gap-2 opacity-50 cursor-not-allowed" disabled>
                    <i class="fab fa-whatsapp"></i> Pesan WA
                </button>
            </div>
        </div>
    </div>

    <div id="adminLoginModal" class="hidden fixed inset-0 bg-black/60 z-[100] flex items-center justify-center px-4 backdrop-blur-sm">
        <div class="bg-white rounded-2xl p-6 w-full max-w-sm shadow-2xl transform transition-all">
            <h3 class="text-xl font-bold text-center mb-2">Login Admin</h3>
            <p class="text-xs text-gray-500 text-center mb-6">Masukkan PIN rahasia untuk mengelola menu.</p>
            
            <input type="password" id="adminPin" placeholder="Masukkan PIN" class="w-full border-2 border-purple-100 rounded-xl px-4 py-3 mb-4 focus:ring-0 focus:border-purple-500 text-center text-2xl tracking-[0.5em] font-bold">
            <p id="adminError" class="text-red-500 text-xs text-center mb-4 hidden">PIN Salah!</p>
            
            <div class="flex gap-3">
                <button onclick="document.getElementById('adminLoginModal').classList.add('hidden')" class="flex-1 py-3 rounded-xl bg-gray-100 text-gray-600 font-semibold hover:bg-gray-200">Batal</button>
                <button onclick="verifyAdmin()" class="flex-1 py-3 rounded-xl bg-purple-600 text-white font-semibold hover:bg-purple-700">Masuk</button>
            </div>
        </div>
    </div>

    <div id="adminView" class="hidden bg-gray-50 min-h-screen pb-10">
        <div class="bg-purple-700 text-white px-4 py-4 sticky top-0 z-50 flex justify-between items-center shadow-md">
            <div>
                <h2 class="font-bold text-lg">Panel Admin</h2>
                <p class="text-xs opacity-80">Pengelola Menu Lumi Choice</p>
            </div>
            <button onclick="logoutAdmin()" class="bg-purple-900/50 hover:bg-purple-900 px-3 py-1.5 rounded-lg text-sm font-medium transition-colors">
                Keluar
            </button>
        </div>

        <main class="max-w-md mx-auto mt-6 px-4">
            <!-- Tambah Menu Card -->
            <div class="bg-white rounded-2xl shadow-sm border border-gray-200 p-5 mb-6">
                <h3 class="font-bold text-purple-700 mb-4 flex items-center gap-2">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor"><path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm1-11a1 1 0 10-2 0v2H7a1 1 0 100 2h2v2a1 1 0 102 0v-2h2a1 1 0 100-2h-2V7z" clip-rule="evenodd" /></svg>
                    Tambah Menu Baru
                </h3>
                <div class="space-y-4">
                    <div>
                        <label class="block text-xs font-semibold text-gray-600 mb-1">Nama Produk</label>
                        <input type="text" id="newMenuName" placeholder="Contoh: Goguma Cheese" class="w-full border border-gray-300 rounded-lg px-3 py-2 text-sm focus:border-purple-500 outline-none">
                    </div>
                    <div>
                        <label class="block text-xs font-semibold text-gray-600 mb-1">Harga (Rp)</label>
                        <input type="number" id="newMenuPrice" placeholder="5000" class="w-full border border-gray-300 rounded-lg px-3 py-2 text-sm focus:border-purple-500 outline-none">
                    </div>
                    <div>
                        <label class="block text-xs font-semibold text-gray-600 mb-1">Foto Produk (Maks 1MB)</label>
                        <input type="file" id="newMenuImage" accept="image/*" onchange="previewImage(event)" class="w-full text-sm file:mr-4 file:py-2 file:px-4 file:rounded-full file:border-0 file:text-sm file:font-semibold file:bg-purple-50 file:text-purple-700 hover:file:bg-purple-100">
                        <img id="imagePreview" src="" class="hidden mt-3 w-full h-32 object-cover rounded-xl border border-gray-200">
                    </div>
                    <button onclick="saveNewMenu()" class="w-full bg-purple-600 text-white font-bold py-2.5 rounded-lg hover:bg-purple-700 transition-colors">Simpan Menu</button>
                </div>
            </div>

            <!-- Daftar Menu Aktif -->
            <h3 class="font-bold text-gray-800 mb-3 ml-1">Daftar Menu Saat Ini</h3>
            <div id="adminMenuList" class="space-y-3">
                <!-- List akan dirender oleh JS -->
            </div>
        </main>
    </div>

    <script>
        // Konfigurasi Global
        const MAX_QUOTA_PER_DAY = 120;
        const WA_NUMBER = "6288298576228";
        const GOOGLE_APPS_SCRIPT_URL = "https://script.google.com/macros/s/AKfycbxCkZgZnBwpRAWwBQK5AdfAFChwCkjWTBufGLTBHRJJEqTQuAiNimkRV6e2ZSHtAGM/exec";
        const ADMIN_PIN = "060426"; // PASSWORD ADMIN DIPERBARUI

        // Default Menu jika kosong
        const defaultMenus = [
            { id: 'beef', name: 'Beef Mayo', price: 5000, image: '6332342968131457389.jpg' },
            { id: 'choco', name: 'Pisang Coklat', price: 5000, image: '6332477323298411452.jpg' }
        ];

        // State Management
        let menus = [];
        let orderState = {};
        let tempBase64Image = "";
        let quotaCache = {};

        // Inisialisasi saat web dimuat
        document.addEventListener('DOMContentLoaded', () => {
            const today = new Date().toISOString().split('T')[0];
            document.getElementById('pickupDate').setAttribute('min', today);
            
            // Load menu dari sistem lokal
            loadMenus();
        });

        // Format Rupiah
        const formatRp = (angka) => new Intl.NumberFormat('id-ID', { style: 'currency', currency: 'IDR', minimumFractionDigits: 0 }).format(angka);

        /* =========================================
           SISTEM DINAMIS MENU (ADMIN & CUSTOMER)
        ========================================= */
        function loadMenus() {
            const saved = localStorage.getItem('lumiChoice_Menus');
            if(saved) {
                menus = JSON.parse(saved);
            } else {
                menus = [...defaultMenus];
                localStorage.setItem('lumiChoice_Menus', JSON.stringify(menus));
            }

            // Reset Keranjang
            menus.forEach(m => { if(orderState[m.id] === undefined) orderState[m.id] = 0; });
            
            renderCustomerMenus();
            renderAdminMenus();
        }

        // Render Tampilan untuk Pembeli
        function renderCustomerMenus() {
            const container = document.getElementById('menuContainer');
            container.innerHTML = ''; // Bersihkan

            menus.forEach(menu => {
                const qty = orderState[menu.id] || 0;
                container.innerHTML += `
                <div class="bg-white rounded-2xl shadow-md overflow-hidden border border-purple-100 flex flex-col">
                    <img src="${menu.image}" alt="${menu.name}" class="h-32 w-full object-cover" onerror="this.src='https://placehold.co/300x200/f3e8ff/9333ea?text=No+Photo'">
                    <div class="p-3 flex-grow flex flex-col justify-between">
                        <div>
                            <h3 class="font-semibold text-sm mb-1">${menu.name}</h3>
                            <p class="text-purple-600 font-bold text-sm mb-3">${formatRp(menu.price)}</p>
                        </div>
                        <div class="flex items-center justify-between bg-purple-50 rounded-lg p-1">
                            <button type="button" onclick="updateQty('${menu.id}', -1)" class="w-8 h-8 rounded-md bg-white text-purple-600 shadow flex items-center justify-center font-bold text-lg focus:outline-none active:bg-purple-100">-</button>
                            <span id="qty-${menu.id}" class="font-semibold text-sm w-8 text-center">${qty}</span>
                            <button type="button" onclick="updateQty('${menu.id}', 1)" class="w-8 h-8 rounded-md bg-purple-600 text-white shadow flex items-center justify-center font-bold text-lg focus:outline-none active:bg-purple-700">+</button>
                        </div>
                    </div>
                </div>`;
            });
        }

        // Render Tampilan List di Admin Panel
        function renderAdminMenus() {
            const list = document.getElementById('adminMenuList');
            list.innerHTML = '';
            
            menus.forEach(menu => {
                list.innerHTML += `
                <div class="bg-white p-3 rounded-xl border border-gray-200 flex items-center gap-3">
                    <img src="${menu.image}" class="w-12 h-12 rounded-lg object-cover bg-gray-100">
                    <div class="flex-1">
                        <h4 class="font-bold text-sm text-gray-800">${menu.name}</h4>
                        <p class="text-xs text-purple-600 font-medium">${formatRp(menu.price)}</p>
                    </div>
                    <button onclick="deleteMenu('${menu.id}')" class="bg-red-50 text-red-500 hover:bg-red-100 p-2 rounded-lg transition-colors">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor"><path fill-rule="evenodd" d="M9 2a1 1 0 00-.894.553L7.382 4H4a1 1 0 000 2v10a2 2 0 002 2h8a2 2 0 002-2V6a1 1 0 100-2h-3.382l-.724-1.447A1 1 0 0011 2H9zM7 8a1 1 0 012 0v6a1 1 0 11-2 0V8zm5-1a1 1 0 00-1 1v6a1 1 0 102 0V8a1 1 0 00-1-1z" clip-rule="evenodd" /></svg>
                    </button>
                </div>`;
            });
        }

        /* =========================================
           LOGIKA ADMIN PANEL
        ========================================= */
        function verifyAdmin() {
            const pin = document.getElementById('adminPin').value;
            if(pin === ADMIN_PIN) {
                document.getElementById('adminLoginModal').classList.add('hidden');
                document.getElementById('customerView').classList.add('hidden');
                document.getElementById('customerView').classList.remove('block');
                document.getElementById('adminView').classList.remove('hidden');
                document.getElementById('adminPin').value = '';
                document.getElementById('adminError').classList.add('hidden');
            } else {
                document.getElementById('adminError').classList.remove('hidden');
            }
        }

        function logoutAdmin() {
            document.getElementById('adminView').classList.add('hidden');
            document.getElementById('customerView').classList.remove('hidden');
            document.getElementById('customerView').classList.add('block');
        }

        function previewImage(event) {
            const file = event.target.files[0];
            if(!file) return;
            
            const reader = new FileReader();
            reader.onload = function(e) {
                tempBase64Image = e.target.result;
                const img = document.getElementById('imagePreview');
                img.src = tempBase64Image;
                img.classList.remove('hidden');
            }
            reader.readAsDataURL(file);
        }

        function saveNewMenu() {
            const name = document.getElementById('newMenuName').value.trim();
            const price = parseInt(document.getElementById('newMenuPrice').value);
            
            if(!name || !price) {
                alert("Mohon isi Nama dan Harga produk!"); return;
            }
            if(!tempBase64Image) {
                alert("Mohon upload foto produk!"); return;
            }

            const newId = 'menu_' + Date.now();
            menus.push({ id: newId, name: name, price: price, image: tempBase64Image });
            
            // Simpan ke LocalStorage
            localStorage.setItem('lumiChoice_Menus', JSON.stringify(menus));
            
            // Reset Form Admin
            document.getElementById('newMenuName').value = '';
            document.getElementById('newMenuPrice').value = '';
            document.getElementById('newMenuImage').value = '';
            document.getElementById('imagePreview').classList.add('hidden');
            tempBase64Image = "";

            loadMenus(); // Refresh UI
            alert("Berhasil menambahkan menu!");
        }

        function deleteMenu(id) {
            if(confirm("Yakin ingin menghapus menu ini?")) {
                menus = menus.filter(m => m.id !== id);
                delete orderState[id];
                localStorage.setItem('lumiChoice_Menus', JSON.stringify(menus));
                loadMenus();
            }
        }

        /* =========================================
           LOGIKA CHECKOUT KONSUMEN
        ========================================= */
        function updateQty(id, change) {
            const newQty = (orderState[id] || 0) + change;
            if (newQty >= 0) {
                orderState[id] = newQty;
                document.getElementById(`qty-${id}`).innerText = newQty;
                calculateTotal();
            }
        }

        function calculateTotal() {
            let totalItems = 0;
            let totalPrice = 0;

            menus.forEach(menu => {
                const qty = orderState[menu.id] || 0;
                totalItems += qty;
                totalPrice += (qty * menu.price);
            });

            document.getElementById('totalItems').innerText = totalItems;
            document.getElementById('totalPriceDisplay').innerText = formatRp(totalPrice);
            checkQuotaUI(totalItems);
        }

        async function checkQuotaUI(currentTotalItems = null) {
            if(currentTotalItems === null) {
                currentTotalItems = 0;
                menus.forEach(m => currentTotalItems += (orderState[m.id] || 0));
            }

            const dateStr = document.getElementById('pickupDate').value;
            const submitBtn = document.getElementById('submitBtn');
            const warningBox = document.getElementById('quotaWarning');
            const loadingBox = document.getElementById('loadingQuota');
            const sisaSpan = document.getElementById('quotaSisa');

            warningBox.classList.add('hidden');
            submitBtn.disabled = true;
            submitBtn.classList.add('opacity-50', 'cursor-not-allowed');

            if (!dateStr) return; 

            if (quotaCache[dateStr] === undefined) {
                loadingBox.classList.remove('hidden');
                try {
                    const res = await fetch(`${GOOGLE_APPS_SCRIPT_URL}?action=checkQuota&date=${dateStr}`);
                    const data = await res.json();
                    quotaCache[dateStr] = data.sisaQuota;
                } catch (e) {
                    console.error("Gagal terhubung ke database", e);
                    quotaCache[dateStr] = MAX_QUOTA_PER_DAY; 
                }
                loadingBox.classList.add('hidden');
            }

            let sisa = quotaCache[dateStr];

            if (currentTotalItems > sisa) {
                warningBox.classList.remove('hidden');
                sisaSpan.innerText = sisa;
            } else if (currentTotalItems > 0 && currentTotalItems <= sisa) {
                submitBtn.disabled = false;
                submitBtn.classList.remove('opacity-50', 'cursor-not-allowed');
            }
        }

        async function processOrder() {
            const custName = document.getElementById('custName').value.trim();
            const custWa = document.getElementById('custWa').value.trim();
            const pickupDate = document.getElementById('pickupDate').value;
            const pickupTime = document.getElementById('pickupTime').value;
            const paymentMethod = document.querySelector('input[name="payment"]:checked').value;
            
            if(!custName || !custWa || !pickupDate || !pickupTime) {
                alert("Mohon lengkapi data pemesan dan waktu pengambilan!");
                return;
            }

            let detailPesanan = "";
            let totalItems = 0;
            let totalPrice = 0;

            menus.forEach(menu => {
                const qty = orderState[menu.id] || 0;
                if(qty > 0) {
                    detailPesanan += `- ${qty}x ${menu.name} (Rp ${formatRp(qty * menu.price)})\n`;
                    totalItems += qty;
                    totalPrice += (qty * menu.price);
                }
            });

            if(totalItems === 0) return;

            // Kurangi cache lokal
            if(quotaCache[pickupDate] !== undefined) {
                quotaCache[pickupDate] -= totalItems;
            }

            // Template WA Dinamis
            const waText = `Halo *Lumi Choice*! 🌟
Saya ingin melakukan Pre-Order:

*Identitas Pemesan*
Nama: ${custName}
No. WA: ${custWa}

*Detail Pesanan*
${detailPesanan}
*Total Pembayaran: ${formatRp(totalPrice)}*

*Pengambilan*
Tanggal: ${pickupDate}
Waktu: ${pickupTime} (STID)
Metode Bayar: ${paymentMethod}

Mohon konfirmasinya ya Kak. Terima kasih! 🙏`;

            const encodedWaText = encodeURIComponent(waText);
            const waLink = `https://wa.me/${WA_NUMBER}?text=${encodedWaText}`;

            // Kirim Data ke Google Sheets
            if(GOOGLE_APPS_SCRIPT_URL !== "") {
                try {
                    fetch(GOOGLE_APPS_SCRIPT_URL, {
                        method: 'POST',
                        mode: 'no-cors',
                        headers: { 'Content-Type': 'application/json' },
                        body: JSON.stringify({
                            tanggal_order: new Date().toISOString(),
                            nama: custName,
                            wa: custWa,
                            detail_pesanan: detailPesanan.trim(), // Format baru gabungan
                            total_item: totalItems,               // Format baru
                            total_harga: totalPrice,
                            tgl_ambil: pickupDate,
                            waktu_ambil: pickupTime,
                            pembayaran: paymentMethod
                        })
                    });
                } catch (e) { console.error("Gagal kirim ke sheets", e); }
            }

            // Redirect ke WhatsApp
            window.location.href = waLink;
            
            // Reset
            setTimeout(() => {
                document.getElementById('orderForm').reset();
                menus.forEach(m => orderState[m.id] = 0);
                renderCustomerMenus();
                calculateTotal();
            }, 1000);
        }
    </script>
</body>
</html>
