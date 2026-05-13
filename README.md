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
                            50: '#faf5ff', 100: '#f3e8ff', 500: '#a855f7',
                            600: '#9333ea', 700: '#7e22ce', 900: '#581c87',
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
<body class="bg-purple-50 text-purple-900 min-h-screen pb-20">

    <!-- View Pembeli -->
    <div id="customerView" class="block">
        <header class="bg-white shadow-sm sticky top-0 z-50">
            <div class="max-w-md mx-auto px-4 py-3 flex items-center justify-center gap-3">
                <img src="./LL.png" alt="Lumi Choice Logo" class="h-12 w-auto object-contain drop-shadow-md rounded-full bg-purple-100" onerror="this.src='https://placehold.co/100x100/f3e8ff/9333ea?text=LC'">
                <div class="text-center">
                    <h1 class="text-xl font-bold text-purple-700 leading-tight">Lumi Choice</h1>
                    <p class="text-xs text-purple-500 font-medium tracking-widest">CHOICE YOUR TASTE</p>
                </div>
            </div>
        </header>

        <main class="max-w-md mx-auto mt-6 px-4">
            <div class="bg-purple-100 rounded-xl p-4 mb-6 text-sm text-purple-800 border border-purple-200 text-center shadow-sm">
                🌟 <b>Pre-Order Dibuka!</b> Yuk, pesan menu favoritmu sekarang sebelum kehabisan!
            </div>

            <h2 class="text-lg font-bold mb-3 flex items-center gap-2">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-purple-600" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253" /></svg>
                Pilih Menu
            </h2>
            
            <!-- Tempat Menu Dimuat -->
            <div id="loadingMenu" class="text-center py-8 text-purple-500 text-sm font-medium animate-pulse">
                Memuat menu dari server...
            </div>
            <div id="menuContainer" class="grid grid-cols-2 gap-4 mb-8 hidden">
                <!-- Card Menu Otomatis -->
            </div>

            <!-- Form Pemesanan -->
            <h2 class="text-lg font-bold mb-3 flex items-center gap-2">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-purple-600" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12h6m-6 4h6m2 5H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z" /></svg>
                Detail Pemesan
            </h2>
            
            <form id="orderForm" class="space-y-4 bg-white p-5 rounded-2xl shadow-sm border border-purple-100">
                <div>
                    <label class="block text-sm font-medium mb-1">Nama Lengkap</label>
                    <input type="text" id="custName" required placeholder="Masukkan nama Anda" class="w-full border border-gray-300 rounded-lg px-3 py-2 focus:ring-2 focus:ring-purple-500 outline-none transition-all">
                </div>
                <div>
                    <label class="block text-sm font-medium mb-1">Nomor WhatsApp</label>
                    <input type="tel" id="custWa" required placeholder="08xxxxxxxxxx" class="w-full border border-gray-300 rounded-lg px-3 py-2 focus:ring-2 focus:ring-purple-500 outline-none transition-all">
                </div>
                <div class="grid grid-cols-2 gap-3">
                    <div>
                        <label class="block text-sm font-medium mb-1">Tgl Pengambilan</label>
                        <input type="date" id="pickupDate" required class="w-full border border-gray-300 rounded-lg px-3 py-2 focus:ring-2 focus:ring-purple-500 outline-none transition-all" onchange="checkQuotaUI()">
                    </div>
                    <div>
                        <label class="block text-sm font-medium mb-1">Waktu (STID)</label>
                        <select id="pickupTime" required class="w-full border border-gray-300 rounded-lg px-3 py-2 focus:ring-2 focus:ring-purple-500 outline-none transition-all">
                            <option value="" disabled selected>Pilih Waktu</option>
                            <option value="10.00 - 10.30">10.00 - 10.30</option>
                            <option value="13.00 - 14.00">13.00 - 14.00</option>
                        </select>
                    </div>
                </div>
                
                <div id="loadingQuota" class="hidden text-xs text-purple-600 bg-purple-50 p-2 rounded border border-purple-200 text-center">
                    ⏳ Memeriksa kuota harian...
                </div>
                <div id="quotaWarning" class="hidden text-xs text-red-600 bg-red-50 p-2 rounded border border-red-200">
                    Maaf, kuota tanggal tersebut penuh (Tersisa <span id="quotaSisa">0</span> pcs). Pilih tanggal lain.
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

            <div class="mt-8 text-center">
                <button onclick="document.getElementById('adminLoginModal').classList.remove('hidden')" class="text-purple-300 hover:text-purple-600">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 15v2m-6 4h12a2 2 0 002-2v-6a2 2 0 00-2-2H6a2 2 0 00-2 2v6a2 2 0 002 2zm10-10V7a4 4 0 00-8 0v4h8V7z" /></svg>
                </button>
            </div>
        </main>

        <div class="fixed bottom-0 left-0 right-0 bg-white border-t border-purple-100 shadow-[0_-4px_6px_-1px_rgba(0,0,0,0.05)] z-40">
            <div class="max-w-md mx-auto px-4 py-3 flex items-center justify-between gap-4">
                <div class="flex-1">
                    <p class="text-xs text-gray-500 mb-0.5">Total Harga (<span id="totalItems">0</span> pcs)</p>
                    <p class="text-lg font-bold text-purple-700" id="totalPriceDisplay">Rp 0</p>
                </div>
                <button type="button" id="submitBtn" onclick="processOrder()" class="flex-1 bg-purple-600 hover:bg-purple-700 text-white font-semibold py-3 px-4 rounded-xl shadow-md transition-all flex justify-center items-center gap-2 opacity-50 cursor-not-allowed" disabled>
                    Pesan WA
                </button>
            </div>
        </div>
    </div>

    <!-- Modal Admin -->
    <div id="adminLoginModal" class="hidden fixed inset-0 bg-black/60 z-[100] flex items-center justify-center px-4 backdrop-blur-sm">
        <div class="bg-white rounded-2xl p-6 w-full max-w-sm shadow-2xl">
            <h3 class="text-xl font-bold text-center mb-2">Login Admin</h3>
            <input type="password" id="adminPin" placeholder="PIN" class="w-full border-2 border-purple-100 rounded-xl px-4 py-3 mb-4 text-center text-2xl tracking-[0.5em] font-bold">
            <div class="flex gap-3">
                <button onclick="document.getElementById('adminLoginModal').classList.add('hidden')" class="flex-1 py-3 bg-gray-100 font-semibold rounded-xl hover:bg-gray-200">Batal</button>
                <button onclick="verifyAdmin()" class="flex-1 py-3 bg-purple-600 text-white font-semibold rounded-xl hover:bg-purple-700">Masuk</button>
            </div>
        </div>
    </div>

    <!-- View Admin -->
    <div id="adminView" class="hidden bg-gray-50 min-h-screen pb-10">
        <div class="bg-purple-700 text-white px-4 py-4 sticky top-0 z-50 flex justify-between items-center shadow-md">
            <h2 class="font-bold text-lg">Panel Admin</h2>
            <button onclick="logoutAdmin()" class="bg-purple-900/50 hover:bg-purple-900 px-3 py-1.5 rounded-lg text-sm font-medium">Keluar</button>
        </div>

        <main class="max-w-md mx-auto mt-6 px-4">
            <div class="bg-white rounded-2xl shadow-sm border border-gray-200 p-5 mb-6">
                <h3 class="font-bold text-purple-700 mb-4">Tambah Menu Baru</h3>
                <div class="space-y-4">
                    <input type="text" id="newMenuName" placeholder="Nama Produk (Misal: Ayam Suwir)" class="w-full border border-gray-300 rounded-lg px-3 py-2 text-sm outline-none">
                    <input type="number" id="newMenuPrice" placeholder="Harga (Misal: 5000)" class="w-full border border-gray-300 rounded-lg px-3 py-2 text-sm outline-none">
                    <div>
                        <label class="block text-xs font-semibold text-gray-600 mb-1">Foto Produk (Akan dikompres otomatis)</label>
                        <input type="file" id="newMenuImage" accept="image/*" onchange="compressAndPreviewImage(event)" class="w-full text-sm">
                        <img id="imagePreview" src="" class="hidden mt-3 w-full h-32 object-cover rounded-xl border border-gray-200">
                    </div>
                    <button id="btnSimpanMenu" onclick="saveNewMenu()" class="w-full bg-purple-600 text-white font-bold py-2.5 rounded-lg hover:bg-purple-700">Simpan Menu ke Database</button>
                </div>
            </div>
            
            <h3 class="font-bold text-gray-800 mb-3 ml-1">Menu Saat Ini (Database)</h3>
            <div id="adminMenuList" class="space-y-3"></div>
        </main>
    </div>

    <script>
        const WA_NUMBER = "6288298576228"; 
        const ADMIN_PIN = "060426";
        const GOOGLE_APPS_SCRIPT_URL = "https://script.google.com/macros/s/AKfycbwGhMCIckZY1l2Jy1ioVARclXAUAXU2EwKnfQMr0Ksk8B_GmiwXH_QHuqa5j6y2gJ4/exec"; 

        // Menu Bawaan (Akan tergabung dengan data dari Sheet)
        let menus = [
            { id: 'beef', name: 'Beef Mayo', price: 5000, image: './6332342968131457389.jpg' },
            { id: 'choco', name: 'Pisang Coklat', price: 5000, image: './6332477323298411452.jpg' }
        ];
        
        let orderState = {};
        let tempBase64Image = "";

        // Inisialisasi
        document.addEventListener('DOMContentLoaded', () => {
            const today = new Date().toISOString().split('T')[0];
            document.getElementById('pickupDate').setAttribute('min', today);
            fetchMenusFromDatabase();
        });

        // 1. MENGAMBIL DATA MENU DARI SPREADSHEET
        async function fetchMenusFromDatabase() {
            try {
                const res = await fetch(`${GOOGLE_APPS_SCRIPT_URL}?action=getMenus`);
                const data = await res.json();
                
                // Gabungkan menu bawaan HTML dengan menu baru dari Database
                if(data.menus && data.menus.length > 0) {
                    menus = [...menus, ...data.menus];
                }
            } catch (e) {
                console.log("Gagal memuat menu dari DB, menggunakan menu lokal.");
            }

            // Inisialisasi keranjang
            menus.forEach(m => orderState[m.id] = 0);
            
            document.getElementById('loadingMenu').classList.add('hidden');
            document.getElementById('menuContainer').classList.remove('hidden');
            renderCustomerMenus();
            renderAdminMenus();
        }

        function formatRp(angka) {
            return new Intl.NumberFormat('id-ID', { style: 'currency', currency: 'IDR', minimumFractionDigits: 0 }).format(angka);
        }

        // 2. RENDER MENU UNTUK PEMBELI
        function renderCustomerMenus() {
            const container = document.getElementById('menuContainer');
            container.innerHTML = '';
            menus.forEach(menu => {
                container.innerHTML += `
                <div class="bg-white rounded-2xl shadow-md overflow-hidden border border-purple-100 flex flex-col">
                    <img src="${menu.image}" alt="${menu.name}" class="h-32 w-full object-cover bg-gray-100">
                    <div class="p-3 flex-grow flex flex-col justify-between">
                        <div>
                            <h3 class="font-semibold text-sm mb-1">${menu.name}</h3>
                            <p class="text-purple-600 font-bold text-sm mb-3">${formatRp(menu.price)}</p>
                        </div>
                        <div class="flex items-center justify-between bg-purple-50 rounded-lg p-1">
                            <button type="button" onclick="updateQty('${menu.id}', -1)" class="w-8 h-8 rounded-md bg-white text-purple-600 shadow font-bold text-lg">-</button>
                            <span id="qty-${menu.id}" class="font-semibold text-sm w-8 text-center">${orderState[menu.id]}</span>
                            <button type="button" onclick="updateQty('${menu.id}', 1)" class="w-8 h-8 rounded-md bg-purple-600 text-white shadow font-bold text-lg">+</button>
                        </div>
                    </div>
                </div>`;
            });
        }

        function renderAdminMenus() {
            const list = document.getElementById('adminMenuList');
            list.innerHTML = '';
            menus.forEach(menu => {
                list.innerHTML += `
                <div class="bg-white p-3 rounded-xl border border-gray-200 flex items-center gap-3">
                    <img src="${menu.image}" class="w-12 h-12 rounded-lg object-cover bg-gray-100">
                    <div class="flex-1">
                        <h4 class="font-bold text-sm">${menu.name}</h4>
                        <p class="text-xs text-purple-600">${formatRp(menu.price)}</p>
                    </div>
                </div>`;
            });
        }

        // 3. LOGIKA ADMIN (KOMPRESI GAMBAR & UPLOAD KE DATABASE)
        function verifyAdmin() {
            if(document.getElementById('adminPin').value === ADMIN_PIN) {
                document.getElementById('adminLoginModal').classList.add('hidden');
                document.getElementById('customerView').classList.add('hidden');
                document.getElementById('customerView').classList.remove('block');
                document.getElementById('adminView').classList.remove('hidden');
                document.getElementById('adminPin').value = '';
            } else { alert('PIN Salah!'); }
        }

        function logoutAdmin() {
            document.getElementById('adminView').classList.add('hidden');
            document.getElementById('customerView').classList.remove('hidden');
            document.getElementById('customerView').classList.add('block');
        }

        // Fungsi Canggih: Mengecilkan foto di HP admin agar tidak membuat Spreadsheet lag
        function compressAndPreviewImage(event) {
            const file = event.target.files[0];
            if(!file) return;
            
            const reader = new FileReader();
            reader.onload = function(e) {
                const img = new Image();
                img.onload = function() {
                    const canvas = document.createElement('canvas');
                    const MAX_WIDTH = 400; // Resolusi kecil agar enteng
                    const scaleSize = MAX_WIDTH / img.width;
                    canvas.width = MAX_WIDTH;
                    canvas.height = img.height * scaleSize;
                    
                    const ctx = canvas.getContext('2d');
                    ctx.drawImage(img, 0, 0, canvas.width, canvas.height);
                    
                    // Convert ke Base64 dengan kualitas 60% (Sangat kecil size-nya)
                    tempBase64Image = canvas.toDataURL('image/jpeg', 0.6); 
                    
                    document.getElementById('imagePreview').src = tempBase64Image;
                    document.getElementById('imagePreview').classList.remove('hidden');
                }
                img.src = e.target.result;
            }
            reader.readAsDataURL(file);
        }

        async function saveNewMenu() {
            const name = document.getElementById('newMenuName').value.trim();
            const price = parseInt(document.getElementById('newMenuPrice').value);
            const btn = document.getElementById('btnSimpanMenu');
            
            if(!name || !price || !tempBase64Image) {
                alert("Mohon isi Nama, Harga, dan upload Foto!"); return;
            }

            btn.innerText = "⏳ Sedang Menyimpan ke Database...";
            btn.disabled = true;

            const newId = 'menu_' + Date.now();
            
            try {
                // Kirim ke Google Sheets
                await fetch(GOOGLE_APPS_SCRIPT_URL, {
                    method: 'POST',
                    mode: 'no-cors',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify({
                        action: "addMenu",
                        id: newId,
                        nama: name,
                        harga: price,
                        image: tempBase64Image
                    })
                });

                alert("Menu Berhasil Ditambahkan ke Server! Refresh halaman depan untuk melihat.");
                
                // Reset form
                document.getElementById('newMenuName').value = '';
                document.getElementById('newMenuPrice').value = '';
                document.getElementById('newMenuImage').value = '';
                document.getElementById('imagePreview').classList.add('hidden');
                tempBase64Image = "";
                
            } catch(e) {
                alert("Gagal menyimpan ke server.");
            }
            btn.innerText = "Simpan Menu ke Database";
            btn.disabled = false;
        }

        // 4. LOGIKA PEMESANAN KONSUMEN
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

            warningBox.classList.add('hidden');
            submitBtn.disabled = true;
            submitBtn.classList.add('opacity-50', 'cursor-not-allowed');

            if (!dateStr) return; 

            loadingBox.classList.remove('hidden');
            try {
                const res = await fetch(`${GOOGLE_APPS_SCRIPT_URL}?action=checkQuota&date=${dateStr}`);
                const data = await res.json();
                loadingBox.classList.add('hidden');

                if (currentTotalItems > data.sisaQuota) {
                    warningBox.classList.remove('hidden');
                    document.getElementById('quotaSisa').innerText = data.sisaQuota;
                } else if (currentTotalItems > 0) {
                    submitBtn.disabled = false;
                    submitBtn.classList.remove('opacity-50', 'cursor-not-allowed');
                }
            } catch (e) {
                loadingBox.classList.add('hidden');
                if (currentTotalItems > 0) {
                    submitBtn.disabled = false;
                    submitBtn.classList.remove('opacity-50', 'cursor-not-allowed');
                }
            }
        }

        async function processOrder() {
            const custName = document.getElementById('custName').value.trim();
            const custWa = document.getElementById('custWa').value.trim();
            const pickupDate = document.getElementById('pickupDate').value;
            const pickupTime = document.getElementById('pickupTime').value;
            const paymentMethod = document.querySelector('input[name="payment"]:checked').value;
            
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

            const waText = `Halo *Lumi Choice*! 🌟\nSaya ingin melakukan Pre-Order:\n\n*Identitas*\nNama: ${custName}\nNo. WA: ${custWa}\n\n*Pesanan*\n${detailPesanan}*Total: ${formatRp(totalPrice)}*\n\n*Pengambilan*\nTgl: ${pickupDate}\nWaktu: ${pickupTime} (STID)\nBayar: ${paymentMethod}\n\nMohon konfirmasinya ya Kak. 🙏`;
            const waLink = `https://wa.me/${WA_NUMBER}?text=${encodeURIComponent(waText)}`;

            // Kirim Data Penjualan ke Sheet
            try {
                fetch(GOOGLE_APPS_SCRIPT_URL, {
                    method: 'POST',
                    mode: 'no-cors',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify({
                        action: "order", // Tandai ini sebagai pesanan
                        nama: custName,
                        wa: custWa,
                        detail_pesanan: detailPesanan.trim(),
                        total_item: totalItems,
                        total_harga: totalPrice,
                        tgl_ambil: pickupDate,
                        waktu_ambil: pickupTime,
                        pembayaran: paymentMethod
                    })
                });
            } catch (e) { console.log(e); }

            window.location.href = waLink;
            
            setTimeout(() => { location.reload(); }, 1500);
        }
    </script>
</body>
</html>
