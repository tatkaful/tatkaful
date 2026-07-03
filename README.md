<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TATKA-FUL | Luxury Floral Concepts</title>
    <!-- Tailwind CSS Engine -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        serif: ['Playfair Display', 'serif'],
                        sans: ['Plus Jakarta Sans', 'sans-serif'],
                    },
                    colors: {
                        gold: {
                            100: '#fcf8ec',
                            500: '#ffd700',
                            600: '#d4af37',
                            700: '#b8860b'
                        }
                    }
                }
            }
        }
    </script>
    <!-- Google Fonts for Ultra Premium Editorial Vibe -->
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,500;0,600;0,700;1,400&family=Plus+Jakarta+Sans:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    
    <!-- Premium Tailored CSS Animations & Structural Styling -->
    <style>
        :root {
            --emerald-dark: #022c22;
            --emerald-main: #064e3b;
            --emerald-light: #ecfdf5;
            --gold-accent: #d4af37;
            --bg-pearl: #fcfbf9;
            --luxury-black: #111111;
        }

        body {
            background-color: var(--bg-pearl);
            font-family: 'Plus Jakarta Sans', sans-serif;
            overflow-x: hidden;
            color: var(--luxury-black);
        }

        .glass-header {
            background: rgba(252, 251, 249, 0.85);
            backdrop-filter: blur(24px);
            -webkit-backdrop-filter: blur(24px);
            border-bottom: 1px solid rgba(17, 17, 17, 0.04);
        }

        .luxury-card {
            background: #ffffff;
            border: 1px solid rgba(17, 17, 17, 0.04);
            box-shadow: 0 10px 30px -10px rgba(0, 0, 0, 0.03);
            transition: all 0.6s cubic-bezier(0.16, 1, 0.3, 1);
        }

        .luxury-card:hover {
            box-shadow: 0 30px 60px -15px rgba(6, 78, 59, 0.06);
            transform: translateY(-8px);
        }

        .premium-btn-primary {
            background: var(--luxury-black);
            color: #ffffff;
            transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
            border: 1px solid var(--luxury-black);
        }

        .premium-btn-primary:hover {
            background: transparent;
            color: var(--luxury-black);
            transform: translateY(-2px);
        }

        .premium-btn-gold {
            background: linear-gradient(135deg, var(--gold-accent) 0%, #b8860b 100%);
            color: #ffffff;
            box-shadow: 0 10px 20px -5px rgba(212, 175, 55, 0.3);
            transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
        }

        .premium-btn-gold:hover {
            box-shadow: 0 15px 30px -5px rgba(212, 175, 55, 0.45);
            transform: translateY(-2px);
        }

        .gold-border {
            border-color: var(--gold-accent);
        }

        /* Custom luxury scrollbar for fluid aesthetic */
        ::-webkit-scrollbar {
            width: 5px;
            height: 5px;
        }
        ::-webkit-scrollbar-track {
            background: transparent;
        }
        ::-webkit-scrollbar-thumb {
            background: rgba(17, 17, 17, 0.1);
            border-radius: 10px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: var(--gold-accent);
        }

        .scrollbar-hide::-webkit-scrollbar {
            display: none;
        }
        .scrollbar-hide {
            -ms-overflow-style: none;
            scrollbar-width: none;
        }

        @keyframes fadeUp {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .animate-fade-up {
            animation: fadeUp 1s cubic-bezier(0.16, 1, 0.3, 1) forwards;
        }
    </style>
</head>
<body class="text-[#111111] antialiased selection:bg-[#064e3b] selection:text-white">

    <!-- ==========================================
         LOADER PAGE (Premium Minimal Welcome)
         ========================================== -->
    <div id="loader-screen" class="fixed inset-0 z-50 bg-[#fcfbf9] flex flex-col items-center justify-center transition-all duration-700">
        <div class="flex flex-col items-center space-y-4">
            <svg class="animate-spin h-8 w-8 text-[#064e3b]" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24">
                <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
                <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
            </svg>
            <h1 class="text-4xl font-serif tracking-[0.15em] text-gray-950 uppercase font-light">TATKA-FUL</h1>
            <p class="text-[9px] uppercase tracking-[0.3em] text-[#d4af37] font-semibold">Premium Floral Architecture</p>
        </div>
    </div>

    <!-- ==========================================
         MAIN WRAPPER FOR Dynamic UI Rendering
         ========================================== -->
    <div id="app-root" class="min-h-screen flex flex-col">
        <!-- Core interface elements are programmatically generated here -->
    </div>

    <!-- Custom Modal/Toast Alerts (replaces alert/confirm) -->
    <div id="custom-alert-container" class="fixed top-6 right-6 z-50 flex flex-col gap-3 max-w-sm pointer-events-none"></div>
    <div id="custom-confirm-modal" class="fixed inset-0 z-50 flex items-center justify-center p-4 bg-black/60 backdrop-blur-sm transition-opacity hidden"></div>

    <!-- ==========================================
         DATABASE LAYER & APPLICATION STATE
         ========================================== -->
    <script>
        const DB_NAME = 'TatkaFulPremiumDB';
        const STORE_NAME = 'store';

        function initDB() {
            return new Promise((resolve, reject) => {
                const request = indexedDB.open(DB_NAME, 3); // Upgrade to version 3 for new structural properties
                request.onupgradeneeded = (e) => {
                    const db = e.target.result;
                    if (!db.objectStoreNames.contains(STORE_NAME)) {
                        db.createObjectStore(STORE_NAME);
                    }
                };
                request.onsuccess = () => resolve(request.result);
                request.onerror = () => reject(request.error);
            });
        }

        async function dbSet(key, val) {
            const db = await initDB();
            return new Promise((resolve, reject) => {
                const tx = db.transaction(STORE_NAME, 'readwrite');
                tx.objectStore(STORE_NAME).put(val, key);
                tx.oncomplete = () => resolve();
                tx.onerror = () => reject(tx.error);
            });
        }

        async function dbGet(key) {
            const db = await initDB();
            return new Promise((resolve, reject) => {
                const tx = db.transaction(STORE_NAME, 'readonly');
                const req = tx.objectStore(STORE_NAME).get(key);
                req.onsuccess = () => resolve(req.result);
                req.onerror = () => reject(req.error);
            });
        }

        const EXCLUSIVE_CATEGORIES = [
            '🌹 Rose Bouquet',
            '🌻 Sunflower Bouquet',
            '💐 Mixed Bouquet',
            '🍫 Chocolate Bouquet',
            '💵 Money Bouquet',
            '🎁 Gift Combo'
        ];

        let state = {
            currentView: 'home', // 'home' | 'admin_login' | 'admin_dashboard'
            selectedCategory: 'All',
            selectedBouquet: null,
            searchQuery: '',
            bouquets: [],
            categories: EXCLUSIVE_CATEGORIES,
            settings: {
                logo: 'IMG_0254.png',
                banner: 'IMG_0255.png',
                phone: '01410619501',
                whatsapp: '01410619501',
                instagram: 'https://instagram.com/tatka_ful',
                tiktok: 'https://tiktok.com/@tatka.ful',
                facebook: 'https://facebook.com',
                heroSlogan: 'Fresh Petals, Beautiful Moments.',
                heroDesc: 'Designing custom-tailored, minimal luxury arrangements to elevate your precious memories.'
            },
            adminTab: 'bouquets', // 'bouquets' | 'settings'
            isAddingBouquet: false,
            editingId: null,
            formData: {
                name: '',
                category: EXCLUSIVE_CATEGORIES[0],
                description: '',
                flowersUsed: '',
                deliveryInfo: 'Fresh delivery across Dhaka. Custom arrangements require 24 hours specification notice.',
                images: [],
                bestseller: false,
                newArrival: true,
                visible: true
            },
            isUploading: false
        };

        // Custom Toast Controller (Eliminates Browser alerts)
        function showToast(message, isError = false) {
            const container = document.getElementById('custom-alert-container');
            if (!container) return;

            const toast = document.createElement('div');
            toast.className = `p-4 rounded-2xl shadow-xl border text-sm font-semibold pointer-events-auto flex items-center gap-3 transition-all transform translate-y-2 opacity-0 ${isError ? 'bg-red-50 text-red-800 border-red-200' : 'bg-[#ecfdf5] text-[#064e3b] border-emerald-100'}`;
            toast.innerHTML = `
                <span class="w-2 h-2 rounded-full ${isError ? 'bg-red-500' : 'bg-[#064e3b]'} animate-ping"></span>
                <span>${message}</span>
            `;
            container.appendChild(toast);

            // Trigger enter transition
            setTimeout(() => {
                toast.classList.remove('translate-y-2', 'opacity-0');
            }, 10);

            // Auto dismiss
            setTimeout(() => {
                toast.classList.add('translate-y-2', 'opacity-0');
                setTimeout(() => toast.remove(), 400);
            }, 3000);
        }

        // Custom Confirm Dialogue Box (Eliminates confirm dialogs)
        function askConfirmation(message, onConfirm) {
            const modal = document.getElementById('custom-confirm-modal');
            if (!modal) return;

            modal.innerHTML = `
                <div class="bg-white p-8 rounded-[2rem] max-w-sm w-full border border-gray-100 shadow-2xl text-center animate-fade-up">
                    <h3 class="text-xl font-serif text-gray-900 mb-4">Please Confirm</h3>
                    <p class="text-gray-500 text-sm font-light mb-8">${message}</p>
                    <div class="flex gap-4">
                        <button id="confirm-btn-cancel" class="flex-1 py-3 bg-gray-100 rounded-xl text-sm font-bold text-gray-600 hover:bg-gray-200 transition-all">Cancel</button>
                        <button id="confirm-btn-yes" class="flex-1 py-3 bg-red-600 rounded-xl text-sm font-bold text-white hover:bg-red-700 transition-all">Confirm</button>
                    </div>
                </div>
            `;
            modal.classList.remove('hidden');

            document.getElementById('confirm-btn-cancel').onclick = () => {
                modal.classList.add('hidden');
            };

            document.getElementById('confirm-btn-yes').onclick = () => {
                modal.classList.add('hidden');
                onConfirm();
            };
        }

        // Helper formatting functions
        function formatWhatsApp(number) {
            let formatted = number.replace(/[^0-9]/g, '');
            if (formatted.startsWith('0')) formatted = '88' + formatted;
            return formatted;
        }

        // High Quality Image Compression
        function compressImage(file, maxWidth = 1000, quality = 0.8) {
            return new Promise((resolve) => {
                const reader = new FileReader();
                reader.onload = (event) => {
                    const img = new Image();
                    img.onload = () => {
                        const canvas = document.createElement('canvas');
                        let scale = maxWidth / img.width;
                        if (scale > 1) scale = 1;
                        canvas.width = img.width * scale;
                        canvas.height = img.height * scale;
                        const ctx = canvas.getContext('2d');
                        ctx.drawImage(img, 0, 0, canvas.width, canvas.height);
                        resolve(canvas.toDataURL('image/jpeg', quality));
                    };
                    img.src = event.target.result;
                };
                reader.readAsDataURL(file);
            });
        }

        // ==========================================
        // VIEW SWITCHER RENDER PIPELINE
        // ==========================================
        async function updateView() {
            const root = document.getElementById('app-root');
            if (state.currentView === 'home') {
                renderHome(root);
            } else if (state.currentView === 'admin_login') {
                renderAdminLogin(root);
            } else if (state.currentView === 'admin_dashboard') {
                renderAdminDashboard(root);
            }
        }

        // ==========================================
        // HOME PAGE RENDERING PIPELINE
        // ==========================================
        function renderHome(container) {
            const visibleBouquets = state.bouquets.filter(b => b.visible !== false);
            
            // Apply Live Search and Category Filtering
            let filteredBouquets = visibleBouquets;
            if (state.selectedCategory !== 'All') {
                filteredBouquets = filteredBouquets.filter(b => b.category === state.selectedCategory);
            }
            if (state.searchQuery.trim() !== '') {
                const query = state.searchQuery.toLowerCase();
                filteredBouquets = filteredBouquets.filter(b => 
                    b.name.toLowerCase().includes(query) || 
                    b.description.toLowerCase().includes(query) ||
                    b.category.toLowerCase().includes(query)
                );
            }

            // Segment Bestsellers & New Arrivals
            const bestSellers = visibleBouquets.filter(b => b.bestseller);
            const newArrivals = visibleBouquets.filter(b => b.newArrival);

            container.innerHTML = `
                <!-- Navigation Menu Header -->
                <nav class="fixed w-full top-0 z-40 glass-header">
                    <div class="max-w-7xl mx-auto px-6 h-24 flex items-center justify-between">
                        <div class="flex items-center gap-4 cursor-pointer group animate-fade-up" onclick="window.scrollTo({top:0, behavior:'smooth'})">
                            <img src="${state.settings.logo || 'IMG_0254.png'}" onerror="this.src='IMG_0254.png'" alt="TATKA-FUL Logo" class="w-14 h-14 rounded-full object-cover shadow-sm group-hover:scale-105 transition-transform duration-500" />
                            <span class="text-2xl font-serif tracking-[0.1em] text-gray-950 uppercase font-light">TATKA-FUL</span>
                        </div>
                        <div class="hidden lg:flex items-center gap-10 text-xs font-bold tracking-[0.2em] uppercase text-gray-500">
                            <a href="#hero" class="hover:text-black transition-colors">Home</a>
                            <a href="#featured" class="hover:text-black transition-colors">Shop</a>
                            <a href="#featured" class="hover:text-black transition-colors">Categories</a>
                            <a href="#why-choose" class="hover:text-black transition-colors">About Us</a>
                            <a href="#faq" class="hover:text-black transition-colors">FAQ</a>
                            <a href="#contact" class="hover:text-black transition-colors">Contact</a>
                        </div>
                        <div>
                            <a href="https://wa.me/${formatWhatsApp(state.settings.whatsapp)}" target="_blank" rel="noreferrer" class="premium-btn text-white px-7 py-3 rounded-full tracking-widest text-[10px] font-bold uppercase shrink-0">
                                Connect WhatsApp
                            </a>
                        </div>
                    </div>
                </nav>

                <!-- 1. Hero Banner with Multi-layered backdrop -->
                <section id="hero" class="relative pt-36 pb-24 md:pt-48 md:pb-36 px-6 flex items-center justify-center min-h-[75vh] overflow-hidden">
                    <div class="absolute inset-0 z-0">
                        <img src="${state.settings.banner || 'IMG_0255.png'}" onerror="this.src='IMG_0255.png'" alt="Floral Banner Background" class="w-full h-full object-cover opacity-20 scale-105" />
                        <div class="absolute inset-0 bg-gradient-to-b from-[#fcfbf9]/95 via-[#fcfbf9]/60 to-[#fcfbf9]"></div>
                    </div>

                    <div class="max-w-4xl mx-auto text-center relative z-10 animate-fade-up">
                        <span class="inline-block py-1.5 px-4 rounded-full bg-black/5 text-[#064e3b] text-[10px] font-bold uppercase tracking-[0.3em] mb-6 border border-black/5">
                            Premium Minimalist Design
                        </span>
                        <h1 class="text-5xl md:text-7xl lg:text-8xl font-serif text-gray-950 mb-8 leading-[1.1] tracking-tight font-light uppercase">
                            ${state.settings.heroSlogan}
                        </h1>
                        <p class="text-base md:text-lg text-gray-600 mb-12 max-w-2xl mx-auto font-light leading-relaxed">
                            ${state.settings.heroDesc}
                        </p>
                        <a href="#featured" class="inline-flex items-center gap-3 premium-btn-primary text-white px-10 py-5 rounded-full text-xs uppercase tracking-widest font-semibold shadow-xl shadow-black/5">
                            Explore Collection 
                            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"></path></svg>
                        </a>
                    </div>
                </section>

                <!-- 2. Featured Bouquets with Category selector and Live Search -->
                <section id="featured" class="px-6 py-24 max-w-7xl mx-auto border-t border-gray-100">
                    <div class="flex flex-col md:flex-row justify-between items-start md:items-end gap-6 mb-12">
                        <div>
                            <span class="text-[10px] uppercase font-bold tracking-[0.3em] text-[#d4af37]">Exclusive Shop</span>
                            <h2 class="text-4xl font-serif text-gray-950 mt-2 font-light uppercase tracking-wide">Featured Bouquets</h2>
                        </div>
                        
                        <!-- Live Search bar -->
                        <div class="relative w-full md:w-80">
                            <input id="live-search-input" type="text" placeholder="Search collection..." value="${state.searchQuery}" class="w-full px-6 py-3 bg-white border border-gray-200 rounded-full focus:outline-none focus:border-[#d4af37] text-sm tracking-wide transition-all shadow-sm" />
                            <svg class="w-4 h-4 absolute right-5 top-4 text-gray-400" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"></path></svg>
                        </div>
                    </div>

                    <!-- Category Pills Section -->
                    <div class="flex gap-4 overflow-x-auto pb-4 scrollbar-hide snap-x mb-12">
                        <button onclick="setCategoryFilter('All')" class="snap-start whitespace-nowrap px-8 py-3 rounded-full transition-all duration-500 text-xs font-bold tracking-widest uppercase ${state.selectedCategory === 'All' ? 'bg-[#111111] text-white shadow-md' : 'bg-white text-gray-500 hover:text-black border border-gray-100'}">
                            All Masterpieces
                        </button>
                        ${state.categories.map(cat => `
                            <button onclick="setCategoryFilter('${cat}')" class="snap-start whitespace-nowrap px-8 py-3 rounded-full transition-all duration-500 text-xs font-bold tracking-widest uppercase ${state.selectedCategory === cat ? 'bg-[#111111] text-white shadow-md' : 'bg-white text-gray-500 hover:text-black border border-gray-100'}">
                                ${cat}
                            </button>
                        `).join('')}
                    </div>

                    <!-- Bouquets Responsive Grid -->
                    ${filteredBouquets.length === 0 ? `
                        <div class="text-center py-20 bg-white rounded-3xl border border-gray-100">
                            <svg class="w-12 h-12 text-gray-300 mx-auto mb-4" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M4 16l4.586-4.586a2 2 0 012.828 0L16 16m-2-2l1.586-1.586a2 2 0 012.828 0L20 14m-6-6h.01M6 20h12a2 2 0 002-2V6a2 2 0 00-2-2H6a2 2 0 00-2 2v12a2 2 0 002 2z"></path></svg>
                            <h3 class="text-xl font-serif text-gray-950 mb-2">No matching masterpieces found</h3>
                            <p class="text-gray-400 font-light text-sm">Please refine your filter or search keywords.</p>
                        </div>
                    ` : `
                        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-x-10 gap-y-16">
                            ${filteredBouquets.map((b, i) => `
                                <div class="group flex flex-col cursor-pointer" onclick="openDetailModal('${b.id}')">
                                    <div class="relative aspect-[4/5] rounded-[2rem] overflow-hidden luxury-card mb-6">
                                        <img src="${b.images[0] || 'IMG_1382.png'}" onerror="this.src='IMG_1382.png'" class="w-full h-full object-cover transition-transform duration-[1.5s] group-hover:scale-110" />
                                        <div class="absolute inset-0 bg-gradient-to-t from-black/40 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-500 flex items-end p-8">
                                            <span class="text-white text-xs font-semibold uppercase tracking-widest border border-white/20 bg-black/20 backdrop-blur-md px-6 py-3 rounded-full">View Details</span>
                                        </div>
                                        ${b.bestseller ? `
                                            <div class="absolute top-5 left-5 bg-white/95 backdrop-blur-md text-[#b8860b] text-[10px] font-bold uppercase tracking-[0.2em] px-4 py-2 rounded-full flex items-center gap-1.5 shadow-lg">
                                                <span class="w-1.5 h-1.5 bg-[#b8860b] rounded-full"></span> Signature
                                            </div>
                                        ` : ''}
                                    </div>
                                    <div class="px-3 flex flex-col flex-grow">
                                        <p class="text-[10px] font-bold tracking-[0.2em] text-[#064e3b] uppercase mb-2">${b.category}</p>
                                        <h3 class="text-xl font-serif text-gray-950 mb-3 group-hover:text-[#064e3b] transition-colors leading-snug font-medium">${b.name}</h3>
                                        <p class="text-gray-500 text-sm font-light leading-relaxed mb-6 line-clamp-2">${b.description}</p>
                                        
                                        <!-- Order on WhatsApp prominent CTA -->
                                        <button onclick="triggerWhatsAppOrder(event, '${b.name}')" class="mt-auto w-full flex items-center justify-center gap-3 py-4 border border-emerald-900 bg-emerald-950/5 text-emerald-900 hover:bg-emerald-950 hover:text-white transition-all text-xs font-bold uppercase tracking-widest rounded-full">
                                            <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946C.06 5.348 5.397.01 12.008.01c3.202.001 6.212 1.246 8.477 3.514 2.266 2.268 3.507 5.28 3.505 8.484-.004 6.657-5.34 11.997-11.953 11.997-2.005-.001-3.973-.502-5.713-1.455L0 24zm6.59-4.846c1.6.95 3.188 1.449 4.625 1.451 5.436 0 9.851-4.398 9.854-9.807.001-2.621-1.013-5.086-2.86-6.935C16.36 1.913 13.9.894 11.285.894c-5.438 0-9.854 4.398-9.858 9.808 0 2.037.533 4.024 1.547 5.765l-.99 3.613 3.73-.973h.001a9.78 9.78 0 0 0 4.332 1.048z"/></svg>
                                            Order on WhatsApp
                                        </button>
                                    </div>
                                </div>
                            `).join('')}
                        </div>
                    `}
                </section>

                <!-- 3. Best Sellers Segment -->
                <section class="bg-stone-50 py-24 px-6 border-t border-gray-100">
                    <div class="max-w-7xl mx-auto">
                        <div class="mb-16 text-center">
                            <span class="text-[10px] uppercase font-bold tracking-[0.3em] text-[#d4af37]">Owner's Recommendation</span>
                            <h2 class="text-4xl font-serif text-gray-950 mt-2 font-light uppercase tracking-wide">Signature Best Sellers</h2>
                        </div>
                        ${bestSellers.length === 0 ? `
                            <p class="text-center text-gray-400 font-light text-sm">No signature masterpieces currently marked.</p>
                        ` : `
                            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-10">
                                ${bestSellers.slice(0,3).map(b => `
                                    <div class="bg-white p-4 rounded-[2rem] luxury-card flex flex-col" onclick="openDetailModal('${b.id}')">
                                        <div class="relative aspect-square rounded-2xl overflow-hidden mb-6">
                                            <img src="${b.images[0] || 'IMG_1382.png'}" class="w-full h-full object-cover" />
                                        </div>
                                        <div class="px-2 flex-grow flex flex-col">
                                            <h3 class="text-xl font-serif text-gray-950 mb-2 font-medium">${b.name}</h3>
                                            <p class="text-gray-500 text-sm font-light mb-6 line-clamp-2">${b.description}</p>
                                            <button onclick="triggerWhatsAppOrder(event, '${b.name}')" class="mt-auto w-full flex items-center justify-center gap-3 py-4 bg-emerald-900 text-white hover:bg-emerald-950 transition-all text-xs font-bold uppercase tracking-widest rounded-full">
                                                Order on WhatsApp
                                            </button>
                                        </div>
                                    </div>
                                `).join('')}
                            </div>
                        `}
                    </div>
                </section>

                <!-- 4. New Arrivals Segment -->
                <section class="py-24 px-6 border-t border-gray-100">
                    <div class="max-w-7xl mx-auto">
                        <div class="mb-16 text-center">
                            <span class="text-[10px] uppercase font-bold tracking-[0.3em] text-[#d4af37]">Fresh Arrivals</span>
                            <h2 class="text-4xl font-serif text-gray-950 mt-2 font-light uppercase tracking-wide">New Seasonal Cuts</h2>
                        </div>
                        ${newArrivals.length === 0 ? `
                            <p class="text-center text-gray-400 font-light text-sm">New masterworks are currently being prepared.</p>
                        ` : `
                            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-10">
                                ${newArrivals.slice(0,3).map(b => `
                                    <div class="group cursor-pointer" onclick="openDetailModal('${b.id}')">
                                        <div class="relative aspect-[4/5] rounded-[2rem] overflow-hidden luxury-card mb-6">
                                            <img src="${b.images[0] || 'IMG_1382.png'}" class="w-full h-full object-cover transition-transform duration-[1.5s] group-hover:scale-105" />
                                            <div class="absolute top-5 left-5 bg-emerald-900 text-white text-[10px] font-semibold uppercase tracking-[0.25em] px-4 py-2 rounded-full">
                                                New Cut
                                            </div>
                                        </div>
                                        <div class="px-2">
                                            <h3 class="text-xl font-serif text-gray-900 mb-2 font-medium">${b.name}</h3>
                                            <p class="text-gray-500 text-sm font-light line-clamp-2 mb-4">${b.description}</p>
                                            <button onclick="triggerWhatsAppOrder(event, '${b.name}')" class="w-full flex items-center justify-center gap-3 py-4 border border-emerald-900 text-emerald-900 hover:bg-emerald-950 hover:text-white transition-all text-xs font-bold uppercase tracking-widest rounded-full">
                                                Order on WhatsApp
                                            </button>
                                        </div>
                                    </div>
                                `).join('')}
                            </div>
                        `}
                    </div>
                </section>

                <!-- 5. Why Choose TATKA-FUL Value Proposition -->
                <section id="why-choose" class="bg-[#f0f2ee] py-24 px-6 border-t border-gray-100">
                    <div class="max-w-7xl mx-auto">
                        <div class="max-w-3xl mb-20">
                            <span class="text-[10px] uppercase font-bold tracking-[0.3em] text-[#d4af37]">Elegance Redefined</span>
                            <h2 class="text-4xl md:text-5xl font-serif text-gray-950 mt-4 leading-tight font-light uppercase tracking-wide">Why Choose TATKA-FUL</h2>
                        </div>
                        <div class="grid grid-cols-1 md:grid-cols-3 gap-12">
                            <div class="bg-white p-10 rounded-[2.5rem] border border-black/5">
                                <span class="text-3xl font-serif text-[#d4af37] block mb-6">01</span>
                                <h3 class="text-xl font-serif mb-4 text-gray-900">Artisan Curation</h3>
                                <p class="text-gray-500 text-sm leading-relaxed font-light">Every petal is carefully hand-selected and custom-arranged by award-winning visual designers.</p>
                            </div>
                            <div class="bg-white p-10 rounded-[2.5rem] border border-black/5">
                                <span class="text-3xl font-serif text-[#d4af37] block mb-6">02</span>
                                <h3 class="text-xl font-serif mb-4 text-gray-900">Zero Plastic Waste</h3>
                                <p class="text-gray-500 text-sm leading-relaxed font-light">We rely entirely on luxury organic materials, recyclable canvas wrap, and ecological presentation craft.</p>
                            </div>
                            <div class="bg-white p-10 rounded-[2.5rem] border border-black/5">
                                <span class="text-3xl font-serif text-[#d4af37] block mb-6">03</span>
                                <h3 class="text-xl font-serif mb-4 text-gray-900">Real-Time Design</h3>
                                <p class="text-gray-500 text-sm leading-relaxed font-light">Direct interaction with our florists via WhatsApp to tailor any minor element to your precise satisfaction.</p>
                            </div>
                        </div>
                    </div>
                </section>

                <!-- 6. Customer Reviews Slider -->
                <section class="py-24 px-6 bg-white border-t border-gray-100">
                    <div class="max-w-7xl mx-auto text-center">
                        <span class="text-[10px] uppercase font-bold tracking-[0.3em] text-[#d4af37]">Verified Appraisals</span>
                        <h2 class="text-4xl font-serif text-gray-900 mt-2 mb-16 font-light uppercase tracking-wide">Customer Reviews</h2>
                        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                            <div class="p-8 rounded-[2rem] bg-[#fcfbf9] border border-gray-100 text-left">
                                <div class="flex text-amber-500 gap-1 mb-4">★★★★★</div>
                                <p class="text-gray-600 font-light italic mb-6">"Ordering from TATKA-FUL was incredibly simple. The WhatsApp process took under two minutes, and the rose arrangement was a true masterwork."</p>
                                <p class="text-xs font-bold uppercase tracking-wider text-gray-900">Zarin Tasnim</p>
                            </div>
                            <div class="p-8 rounded-[2rem] bg-[#fcfbf9] border border-gray-100 text-left">
                                <div class="flex text-amber-500 gap-1 mb-4">★★★★★</div>
                                <p class="text-gray-600 font-light italic mb-6">"Stunningly elegant. No plastic wraps, just raw beauty and exquisite gold canvas framing. Handcrafted details were immediately clear."</p>
                                <p class="text-xs font-bold uppercase tracking-wider text-gray-900">Aditya Rahman</p>
                            </div>
                            <div class="p-8 rounded-[2rem] bg-[#fcfbf9] border border-gray-100 text-left">
                                <div class="flex text-amber-500 gap-1 mb-4">★★★★★</div>
                                <p class="text-gray-600 font-light italic mb-6">"We requested custom flowers for our anniversary. The design team was super interactive, sending pictures of the setup before delivery."</p>
                                <p class="text-xs font-bold uppercase tracking-wider text-gray-900">Nadia Karim</p>
                            </div>
                        </div>
                    </div>
                </section>

                <!-- 7. FAQ Accordion Dropdowns -->
                <section id="faq" class="py-24 px-6 bg-stone-50 border-t border-gray-100">
                    <div class="max-w-4xl mx-auto">
                        <div class="text-center mb-16">
                            <span class="text-[10px] uppercase font-bold tracking-[0.3em] text-[#d4af37]">Common Queries</span>
                            <h2 class="text-4xl font-serif text-gray-900 mt-2 font-light uppercase tracking-wide">Frequently Asked</h2>
                        </div>
                        <div class="space-y-4">
                            <div class="bg-white rounded-2xl border border-gray-100 overflow-hidden">
                                <button onclick="toggleFaqAccordion(this)" class="w-full flex justify-between items-center px-8 py-6 text-left focus:outline-none">
                                    <span class="font-serif text-lg text-gray-950 font-medium">How do I place an order?</span>
                                    <span class="text-gray-400 font-light text-2xl transition-transform duration-300 select-none">+</span>
                                </button>
                                <div class="px-8 pb-6 text-gray-500 font-light text-sm hidden">
                                    Simply browse our collections, choose a masterpiece, and click "Order on WhatsApp". Our direct channel opens up immediately with the preset item description, where a florist consultant will confirm your slot, customization requests, and payment options.
                                </div>
                            </div>
                            <div class="bg-white rounded-2xl border border-gray-100 overflow-hidden">
                                <button onclick="toggleFaqAccordion(this)" class="w-full flex justify-between items-center px-8 py-6 text-left focus:outline-none">
                                    <span class="font-serif text-lg text-gray-950 font-medium">Why do you not show product prices?</span>
                                    <span class="text-gray-400 font-light text-2xl transition-transform duration-300 select-none">+</span>
                                </button>
                                <div class="px-8 pb-6 text-gray-500 font-light text-sm hidden">
                                    Our visual bouquets are fully organic and seasonal. Flower rates and premium cuts vary daily. Moreover, because every arrangement is bespoke and can be upgraded with specific floral density, we define prices dynamically to ensure you get the absolute best visual arrangement.
                                </div>
                            </div>
                            <div class="bg-white rounded-2xl border border-gray-100 overflow-hidden">
                                <button onclick="toggleFaqAccordion(this)" class="w-full flex justify-between items-center px-8 py-6 text-left focus:outline-none">
                                    <span class="font-serif text-lg text-gray-950 font-medium">What areas do you deliver to?</span>
                                    <span class="text-gray-400 font-light text-2xl transition-transform duration-300 select-none">+</span>
                                </button>
                                <div class="px-8 pb-6 text-gray-500 font-light text-sm hidden">
                                    We deliver across Dhaka. Special protective delivery trucks ensure your bespoke luxury cuts arrive in optimal climate-controlled conditions without losing their scent or presentation integrity.
                                </div>
                            </div>
                        </div>
                    </div>
                </section>

                <!-- 8. Contact & WhatsApp Direct Block -->
                <section id="contact" class="bg-stone-900 text-white py-24 px-6 relative overflow-hidden border-t border-gray-800">
                    <div class="max-w-5xl mx-auto text-center relative z-10">
                        <span class="inline-block border border-white/15 bg-white/5 py-1.5 px-4 rounded-full text-[#d4af37] text-[10px] font-bold uppercase tracking-[0.25em] mb-6">
                            Direct Studio Access
                        </span>
                        <h2 class="text-4xl md:text-5xl font-serif text-white mb-6 font-light uppercase tracking-wide">Ready to design your custom floral art?</h2>
                        <p class="text-gray-400 font-light max-w-xl mx-auto mb-10 leading-relaxed text-sm md:text-base">
                            Get in touch directly with our visual artists. We design to match your requirements instantly.
                        </p>
                        <div class="flex flex-col sm:flex-row justify-center items-center gap-4">
                            <a href="https://wa.me/${formatWhatsApp(state.settings.whatsapp)}" target="_blank" rel="noreferrer" class="premium-btn-gold text-white px-10 py-5 rounded-full text-xs uppercase tracking-widest font-bold flex items-center gap-3">
                                <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946C.06 5.348 5.397.01 12.008.01c3.202.001 6.212 1.246 8.477 3.514 2.266 2.268 3.507 5.28 3.505 8.484-.004 6.657-5.34 11.997-11.953 11.997-2.005-.001-3.973-.502-5.713-1.455L0 24zm6.59-4.846c1.6.95 3.188 1.449 4.625 1.451 5.436 0 9.851-4.398 9.854-9.807.001-2.621-1.013-5.086-2.86-6.935C16.36 1.913 13.9.894 11.285.894c-5.438 0-9.854 4.398-9.858 9.808 0 2.037.533 4.024 1.547 5.765l-.99 3.613 3.73-.973h.001a9.78 9.78 0 0 0 4.332 1.048z"/></svg>
                                Order on WhatsApp
                            </a>
                            <a href="tel:${state.settings.phone}" class="bg-transparent border border-white/20 text-white px-10 py-5 rounded-full text-xs uppercase tracking-widest font-semibold hover:bg-white/5 transition-all">
                                Call Studio
                            </a>
                        </div>
                    </div>
                </section>

                <!-- Footer Segment -->
                <footer class="bg-black text-white pt-24 pb-12 px-6">
                    <div class="max-w-7xl mx-auto grid grid-cols-1 md:grid-cols-4 gap-12 text-center md:text-left">
                        <div class="md:col-span-2 space-y-6">
                            <div class="flex items-center gap-4 justify-center md:justify-start">
                                <img src="${state.settings.logo || 'IMG_0254.png'}" onerror="this.src='IMG_0254.png'" class="w-16 h-16 rounded-full object-cover border border-white/10" alt="" />
                                <span class="font-serif text-2xl tracking-[0.1em] text-white uppercase font-light">TATKA-FUL</span>
                            </div>
                            <p class="text-gray-400 font-light text-sm leading-relaxed max-w-sm">
                                Designing exquisite floral art with absolute minimalism. Simple, visual, fresh, and hand-tailored.
                            </p>
                        </div>
                        <div>
                            <p class="text-xs font-bold uppercase tracking-[0.2em] text-[#d4af37] mb-6">Contact Studio</p>
                            <ul class="space-y-3 text-sm font-light text-gray-400">
                                <li>WhatsApp: ${state.settings.whatsapp}</li>
                                <li>Phone: ${state.settings.phone}</li>
                                <li>Dhaka, Bangladesh</li>
                            </ul>
                        </div>
                        <div>
                            <p class="text-xs font-bold uppercase tracking-[0.2em] text-[#d4af37] mb-6">Brand Portfolio</p>
                            <div class="flex justify-center md:justify-start gap-4">
                                <a href="${state.settings.instagram}" target="_blank" rel="noreferrer" class="w-10 h-10 rounded-full bg-white/5 hover:bg-white/10 flex items-center justify-center text-gray-300 hover:text-white transition-colors">
                                    <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 9a2 2 0 012-2h.93a2 2 0 001.664-.89l.812-1.22A2 2 0 0110.07 4h3.86a2 2 0 011.664.89l.812 1.22A2 2 0 0018.07 7H19a2 2 0 012 2v9a2 2 0 01-2 2H5a2 2 0 01-2-2V9z"></path><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 13a3 3 0 11-6 0 3 3 0 016 0z"></path></svg>
                                </a>
                                <a href="${state.settings.tiktok}" target="_blank" rel="noreferrer" class="w-10 h-10 rounded-full bg-white/5 hover:bg-white/10 flex items-center justify-center text-gray-300 hover:text-white transition-colors">
                                    <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"></path></svg>
                                </a>
                            </div>
                        </div>
                    </div>
                    <div class="max-w-7xl mx-auto mt-20 pt-8 border-t border-white/5 text-center">
                        <p id="secret-trigger" class="text-[10px] font-semibold tracking-[0.2em] uppercase text-gray-500 cursor-default select-none hover:text-white transition-colors" title="Double click to access studio management">
                            &copy; 2026 TATKA-FUL. Crafted with elegance.
                        </p>
                    </div>
                </footer>

                <!-- Floating Sticky WhatsApp CTA button -->
                <div class="fixed bottom-6 right-6 z-40">
                    <a href="https://wa.me/${formatWhatsApp(state.settings.whatsapp)}" target="_blank" rel="noreferrer" class="relative w-16 h-16 bg-[#25D366] text-white rounded-full flex items-center justify-center hover:scale-105 transition-transform shadow-[0_10px_30px_rgba(37,211,102,0.4)]">
                        <span class="absolute inline-flex h-full w-full rounded-full bg-[#25D366] opacity-40 animate-ping text-emerald-950"></span>
                        <svg class="w-8 h-8 relative z-10" fill="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946C.06 5.348 5.397.01 12.008.01c3.202.001 6.212 1.246 8.477 3.514 2.266 2.268 3.507 5.28 3.505 8.484-.004 6.657-5.34 11.997-11.953 11.997-2.005-.001-3.973-.502-5.713-1.455L0 24zm6.59-4.846c1.6.95 3.188 1.449 4.625 1.451 5.436 0 9.851-4.398 9.854-9.807.001-2.621-1.013-5.086-2.86-6.935C16.36 1.913 13.9.894 11.285.894c-5.438 0-9.854 4.398-9.858 9.808 0 2.037.533 4.024 1.547 5.765l-.99 3.613 3.73-.973h.001a9.78 9.78 0 0 0 4.332 1.048zM18.15 14.86c-.337-.168-1.996-.983-2.305-1.096-.309-.113-.534-.168-.758.168-.225.337-.871 1.096-1.067 1.32-.197.225-.393.253-.73.084-.337-.168-1.42-.524-2.707-1.671-1.002-.894-1.679-2.001-1.875-2.337-.197-.337-.021-.519.147-.687.152-.151.337-.393.506-.59.168-.197.225-.337.337-.562.113-.225.056-.422-.028-.59-.084-.168-.758-1.825-1.039-2.503-.274-.662-.553-.573-.758-.583-.197-.01-.422-.012-.647-.012-.225 0-.59.084-.9.422-.309.337-1.18 1.151-1.18 2.808 0 1.657 1.208 3.257 1.377 3.482.168.225 2.378 3.63 5.76 5.087.805.347 1.433.554 1.923.71.808.257 1.545.221 2.127.135.649-.096 1.996-.815 2.277-1.601.281-.787.281-1.461.197-1.601-.084-.14-.309-.225-.647-.393z"/></svg>
                    </a>
                </div>

                <!-- Product Details Canvas Wrapper -->
                <div id="modal-wrapper"></div>
            `;

            // Setup dynamic dynamic doubleclick trigger
            document.getElementById('secret-trigger').ondblclick = () => {
                state.currentView = 'admin_login';
                updateView();
            };

            // Setup dynamic live search handler
            const searchInput = document.getElementById('live-search-input');
            if (searchInput) {
                searchInput.oninput = (e) => {
                    state.searchQuery = e.target.value;
                    // Dynamically update view (keeps active element state stable without full reload if targeted correctly, but for simplicity of SPA architecture, complete update is safe)
                    debounceSearch();
                };
            }

            if (state.selectedBouquet) {
                renderDetailModal();
            }
        }

        // Search debounce mechanics
        let searchTimeout;
        function debounceSearch() {
            clearTimeout(searchTimeout);
            searchTimeout = setTimeout(() => {
                updateView();
                // Retain focus on search input after redraw
                const searchInput = document.getElementById('live-search-input');
                if (searchInput) {
                    searchInput.focus();
                    searchInput.setSelectionRange(searchInput.value.length, searchInput.value.length);
                }
            }, 300);
        }

        // WhatsApp Order Generation Mechanics
        function triggerWhatsAppOrder(event, bouquetName) {
            if (event) event.stopPropagation();
            const rawMessage = `Hello TATKA-FUL! I'm interested in ordering the '${bouquetName}'. Please share the price and details.`;
            const encoded = encodeURIComponent(rawMessage);
            const waUrl = `https://wa.me/${formatWhatsApp(state.settings.whatsapp)}?text=${encoded}`;
            window.open(waUrl, '_blank');
        }

        // Accordion functionality
        function toggleFaqAccordion(btn) {
            const content = btn.nextElementSibling;
            const icon = btn.querySelector('span:last-child');
            if (content.classList.contains('hidden')) {
                content.classList.remove('hidden');
                icon.textContent = '−';
                icon.classList.add('rotate-180');
            } else {
                content.classList.add('hidden');
                icon.textContent = '+';
                icon.classList.remove('rotate-180');
            }
        }

        // ==========================================
        // 11. PORTFOLIO PRODUCT DETAILS MODAL VIEW
        // ==========================================
        function renderDetailModal() {
            const b = state.selectedBouquet;
            const container = document.getElementById('modal-wrapper');
            if (!container) return;

            // Related Bouquets list (same category, excluding this product)
            const related = state.bouquets.filter(item => item.category === b.category && item.id !== b.id && item.visible !== false).slice(0, 3);

            container.innerHTML = `
                <div class="fixed inset-0 z-50 flex items-center justify-center p-0 md:p-8">
                    <div class="absolute inset-0 bg-black/70 backdrop-blur-md transition-opacity animate-fade-in" onclick="closeDetailModal()"></div>
                    <div class="relative bg-[#fcfbf9] w-full h-full md:h-auto md:max-h-[95vh] md:max-w-6xl md:rounded-[2.5rem] shadow-2xl overflow-y-auto flex flex-col animate-fade-up">
                        
                        <button onclick="closeDetailModal()" class="absolute top-6 right-6 z-20 w-12 h-12 bg-white/90 backdrop-blur-md rounded-full flex items-center justify-center text-gray-900 hover:bg-gray-100 transition-colors shadow-lg">
                            <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path></svg>
                        </button>

                        <div class="flex flex-col lg:flex-row flex-grow">
                            <!-- Visual Gallery Panel -->
                            <div class="w-full lg:w-1/2 bg-white h-[50vh] lg:h-auto overflow-y-auto snap-y snap-mandatory scrollbar-hide relative border-b lg:border-b-0 lg:border-r border-gray-100">
                                ${b.images && b.images.length > 0 ? b.images.map((img, idx) => `
                                    <div class="w-full h-full min-h-[50vh] lg:min-h-full snap-center relative">
                                        <img src="${img}" alt="${b.name}" class="w-full h-full object-cover" />
                                    </div>
                                `).join('') : `
                                    <div class="w-full h-full flex items-center justify-center text-gray-300 font-light">No Visual Assets Created</div>
                                `}
                                ${b.images && b.images.length > 1 ? `
                                    <div class="absolute bottom-6 left-0 right-0 flex justify-center gap-2 pointer-events-none">
                                        <span class="bg-black/50 backdrop-blur-md text-white text-[9px] tracking-widest px-4 py-2 rounded-full uppercase font-bold">Scroll Down for Gallery</span>
                                    </div>
                                ` : ''}
                            </div>

                            <!-- Structural Detailed Metadata -->
                            <div class="w-full lg:w-1/2 p-8 md:p-16 flex flex-col bg-white">
                                <p class="text-[10px] font-bold tracking-[0.3em] text-[#064e3b] uppercase mb-4">${b.category}</p>
                                <h2 class="text-4xl md:text-5xl font-serif text-gray-950 mb-6 leading-tight font-light uppercase tracking-wide">${b.name}</h2>
                                <div class="w-16 h-[2px] bg-[#d4af37] mb-8"></div>
                                <p class="text-gray-600 leading-relaxed mb-8 font-light text-base">${b.description}</p>
                                
                                <div class="space-y-6 mb-10">
                                    <!-- Custom added field: Flowers Used -->
                                    <div class="bg-[#f0f2ee] p-6 rounded-2xl border border-black/5">
                                        <h4 class="text-xs font-bold uppercase tracking-wider text-gray-900 mb-2">Flowers Used</h4>
                                        <p class="text-gray-600 text-sm font-light">${b.flowersUsed || 'Selected premium seasonal stems and matching botanical foliage.'}</p>
                                    </div>
                                    <!-- Custom added field: Delivery Info -->
                                    <div class="bg-[#fcfbf9] p-6 rounded-2xl border border-gray-100">
                                        <h4 class="text-xs font-bold uppercase tracking-wider text-[#d4af37] mb-2">Delivery Details</h4>
                                        <p class="text-gray-500 text-sm font-light">${b.deliveryInfo || 'Secure, protected box shipment across Dhaka. Orders must be submitted at least 24 hours in advance.'}</p>
                                    </div>
                                </div>

                                <div class="space-y-4">
                                    <button onclick="triggerWhatsAppOrder(null, '${b.name}')" class="w-full premium-btn text-white py-5 rounded-full flex items-center justify-center gap-3 text-xs font-bold uppercase tracking-widest">
                                        <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946C.06 5.348 5.397.01 12.008.01c3.202.001 6.212 1.246 8.477 3.514 2.266 2.268 3.507 5.28 3.505 8.484-.004 6.657-5.34 11.997-11.953 11.997-2.005-.001-3.973-.502-5.713-1.455L0 24zm6.59-4.846c1.6.95 3.188 1.449 4.625 1.451 5.436 0 9.851-4.398 9.854-9.807.001-2.621-1.013-5.086-2.86-6.935C16.36 1.913 13.9.894 11.285.894c-5.438 0-9.854 4.398-9.858 9.808 0 2.037.533 4.024 1.547 5.765l-.99 3.613 3.73-.973h.001a9.78 9.78 0 0 0 4.332 1.048z"/></svg>
                                        Order on WhatsApp
                                    </button>
                                </div>
                            </div>
                        </div>

                        <!-- Related Bouquets Horizontal Grid -->
                        ${related.length > 0 ? `
                            <div class="bg-stone-50 p-8 md:p-16 border-t border-gray-100">
                                <h4 class="text-xs font-bold uppercase tracking-[0.25em] text-[#d4af37] mb-8">Related Masterpieces</h4>
                                <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                                    ${related.map(item => `
                                        <div class="bg-white p-4 rounded-2xl border border-gray-100 shadow-sm hover:shadow-md transition-all cursor-pointer flex flex-col" onclick="openDetailModal('${item.id}')">
                                            <div class="relative aspect-square rounded-xl overflow-hidden mb-4">
                                                <img src="${item.images[0] || 'IMG_1382.png'}" class="w-full h-full object-cover" />
                                            </div>
                                            <div class="flex-grow flex flex-col">
                                                <h5 class="text-lg font-serif text-gray-900 font-medium mb-1">${item.name}</h5>
                                                <p class="text-gray-500 text-xs font-light line-clamp-2 mb-4">${item.description}</p>
                                                <span class="text-xs font-bold uppercase tracking-wider text-[#064e3b] mt-auto">View Item</span>
                                            </div>
                                        </div>
                                    `).join('')}
                                </div>
                            </div>
                        ` : ''}

                    </div>
                </div>
            `;
        }

        // ==========================================
        // ADMIN PANEL INVENTORY CONTROLLER
        // ==========================================
        function renderAdminMainSection() {
            const container = document.getElementById('admin-main-area');
            if (!container) return;

            if (state.adminTab === 'bouquets') {
                if (state.isAddingBouquet) {
                    renderBouquetForm(container);
                } else {
                    renderBouquetList(container);
                }
            } else if (state.adminTab === 'settings') {
                renderSettingsPanel(container);
            }
        }

        function renderBouquetList(container) {
            container.innerHTML = `
                <div class="animate-fade-up max-w-6xl mx-auto">
                    <div class="flex flex-col md:flex-row justify-between items-start md:items-center mb-12 gap-6">
                        <div>
                            <h1 class="text-4xl font-serif text-gray-950 mb-2 font-light">Inventory Management</h1>
                            <p class="text-gray-500 font-light text-sm">Upload, customize, and publish flower collections.</p>
                        </div>
                        <button onclick="openNewBouquetForm()" class="premium-btn text-white px-8 py-4 rounded-full flex items-center gap-3 font-bold uppercase tracking-[0.2em] text-xs">
                            New Design
                        </button>
                    </div>

                    <div class="grid grid-cols-1 md:grid-cols-3 gap-6 mb-12">
                        <div class="bg-white p-8 rounded-3xl border border-gray-100 shadow-sm">
                            <p class="text-xs text-gray-400 font-bold tracking-[0.2em] uppercase mb-3">Total Catalog</p>
                            <p class="text-5xl font-serif text-gray-900">${state.bouquets.length}</p>
                        </div>
                        <div class="bg-white p-8 rounded-3xl border border-gray-100 shadow-sm">
                            <p class="text-xs text-[#064e3b] font-bold tracking-[0.2em] uppercase mb-3">Active Displays</p>
                            <p class="text-5xl font-serif text-[#064e3b]">${state.bouquets.filter(b => b.visible).length}</p>
                        </div>
                        <div class="bg-white p-8 rounded-3xl border border-gray-100 shadow-sm">
                            <p class="text-xs text-[#b8860b] font-bold tracking-[0.2em] uppercase mb-3">Signature Stars</p>
                            <p class="text-5xl font-serif text-[#b8860b]">${state.bouquets.filter(b => b.bestseller).length}</p>
                        </div>
                    </div>

                    <div class="bg-white border border-gray-100 rounded-3xl overflow-hidden shadow-sm">
                        <table class="w-full text-left border-collapse">
                            <thead>
                                <tr class="border-b border-gray-100 bg-gray-50/50">
                                    <th class="p-6 text-xs font-bold text-gray-400 uppercase tracking-[0.2em]">Masterpiece Name</th>
                                    <th class="p-6 text-xs font-bold text-gray-400 uppercase tracking-[0.2em] hidden md:table-cell">Category</th>
                                    <th class="p-6 text-xs font-bold text-gray-400 uppercase tracking-[0.2em] text-center">Status</th>
                                    <th class="p-6 text-xs font-bold text-gray-400 uppercase tracking-[0.2em] text-right">Actions</th>
                                </tr>
                            </thead>
                            <tbody class="divide-y divide-gray-50">
                                ${state.bouquets.length === 0 ? `
                                    <tr>
                                        <td colSpan="4" class="p-12 text-center text-gray-400 font-light text-lg">No inventory cataloged. Click 'New Design' to post first piece.</td>
                                    </tr>
                                ` : state.bouquets.map(b => `
                                    <tr class="hover:bg-gray-50/50 transition-colors">
                                        <td class="p-6 flex items-center gap-6">
                                            <div class="w-16 h-16 rounded-2xl bg-gray-100 overflow-hidden shrink-0 border border-gray-200">
                                                <img src="${b.images[0] || 'IMG_1382.png'}" onerror="this.src='IMG_1382.png'" class="w-full h-full object-cover" />
                                            </div>
                                            <div>
                                                <p class="font-serif text-xl text-gray-900">${b.name}</p>
                                                <div class="flex gap-2 mt-2">
                                                    ${b.bestseller ? `<span class="text-[8px] bg-[#b8860b]/10 text-[#b8860b] px-3 py-1 rounded-full font-bold uppercase tracking-widest">Bestseller</span>` : ''}
                                                    ${b.newArrival ? `<span class="text-[8px] bg-[#064e3b]/10 text-[#064e3b] px-3 py-1 rounded-full font-bold uppercase tracking-widest">New Arrival</span>` : ''}
                                                </div>
                                            </div>
                                        </td>
                                        <td class="p-6 text-sm text-gray-600 hidden md:table-cell font-medium">${b.category}</td>
                                        <td class="p-6 text-center">
                                            <button onclick="toggleVisibility('${b.id}')" class="p-3 rounded-full transition-all ${b.visible ? 'text-[#064e3b] bg-[#ecfdf5] hover:bg-[#d1fae5]' : 'text-gray-400 bg-gray-100 hover:bg-gray-200'}">
                                                ${b.visible ? 'Visible' : 'Hidden'}
                                            </button>
                                        </td>
                                        <td class="p-6 text-right space-x-3">
                                            <button onclick="editBouquet('${b.id}')" class="p-3 text-gray-400 hover:text-[#064e3b] hover:bg-[#ecfdf5] rounded-full transition-all inline-block">Edit</button>
                                            <button onclick="deleteBouquet('${b.id}')" class="p-3 text-gray-400 hover:text-red-600 hover:bg-red-50 rounded-full transition-all inline-block">Delete</button>
                                        </td>
                                    </tr>
                                `).join('')}
                            </tbody>
                        </table>
                    </div>
                </div>
            `;
        }

        // ==========================================
        // FORM ARCHITECTURE FOR NEW / EDIT BOUQUET
        // ==========================================
        function renderBouquetForm(container) {
            container.innerHTML = `
                <div class="animate-fade-up max-w-4xl mx-auto bg-white p-8 md:p-14 border border-gray-100 rounded-[3rem] shadow-sm">
                    <div class="flex items-center gap-6 mb-12 border-b border-gray-100 pb-8">
                        <button onclick="cancelBouquetForm()" class="p-4 bg-gray-50 rounded-full hover:bg-gray-100 text-gray-600 transition-colors">
                            <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 19l-7-7m0 0l7-7m-7 7h18"></path></svg>
                        </button>
                        <h2 class="text-4xl font-serif text-gray-900">${state.editingId ? 'Edit Masterpiece' : 'Publish Masterpiece'}</h2>
                    </div>

                    <form id="bouquet-form" class="space-y-10">
                        <!-- Direct Device Upload Framework with compression -->
                        <div class="bg-[#fcfbf9] p-8 rounded-[2rem] border border-gray-100">
                            <label class="block text-xs font-bold tracking-[0.2em] text-gray-400 mb-6 uppercase">Gallery Images (Max 5)</label>
                            <div class="grid grid-cols-2 md:grid-cols-5 gap-4">
                                ${state.formData.images.map((img, idx) => `
                                    <div class="relative aspect-[4/5] rounded-2xl overflow-hidden group shadow-sm border border-gray-200">
                                        <img src="${img}" class="w-full h-full object-cover" />
                                        <button type="button" onclick="removeFormImage(${idx})" class="absolute inset-0 bg-red-900/60 text-white flex items-center justify-center opacity-0 group-hover:opacity-100 transition-opacity backdrop-blur-sm font-bold">Remove</button>
                                    </div>
                                `).join('')}
                                ${state.formData.images.length < 5 ? `
                                    <label class="aspect-[4/5] rounded-2xl border-2 border-dashed border-gray-300 hover:border-[#064e3b] hover:bg-[#ecfdf5] transition-colors flex flex-col items-center justify-center cursor-pointer text-gray-400 hover:text-[#064e3b] bg-white">
                                        <svg class="w-8 h-8 mb-3" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-8l-4-4m0 0L8 8m4-4v12"></path></svg>
                                        <span class="text-[10px] font-bold tracking-widest uppercase">${state.isUploading ? 'Compressing...' : 'Upload File'}</span>
                                        <input id="gallery-input" type="file" accept="image/*" multiple class="hidden" />
                                    </label>
                                ` : ''}
                            </div>
                        </div>

                        <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                            <div>
                                <label class="block text-xs font-bold tracking-[0.2em] text-gray-400 mb-3 uppercase">Bouquet Name</label>
                                <input required id="form-name" type="text" value="${state.formData.name}" class="w-full px-6 py-5 bg-gray-50 border border-gray-200 rounded-2xl focus:ring-2 focus:ring-[#064e3b]/20 focus:border-[#064e3b] outline-none transition-all font-medium text-lg" placeholder="e.g. Royal Crimson" />
                            </div>
                            <div>
                                <label class="block text-xs font-bold tracking-[0.2em] text-gray-400 mb-3 uppercase">Category</label>
                                <select id="form-category" class="w-full px-6 py-5 bg-gray-50 border border-gray-200 rounded-2xl focus:ring-2 focus:ring-[#064e3b]/20 focus:border-[#064e3b] outline-none transition-all font-medium text-lg">
                                    ${state.categories.map(c => `<option value="${c}" ${state.formData.category === c ? 'selected' : ''}>${c}</option>`).join('')}
                                </select>
                            </div>
                        </div>

                        <div>
                            <label class="block text-xs font-bold tracking-[0.2em] text-gray-400 mb-3 uppercase">Description</label>
                            <textarea required id="form-desc" rows="4" class="w-full px-6 py-5 bg-gray-50 border border-gray-200 rounded-2xl focus:ring-2 focus:ring-[#064e3b]/20 focus:border-[#064e3b] outline-none transition-all resize-none font-medium text-lg leading-relaxed">${state.formData.description}</textarea>
                        </div>

                        <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                            <div>
                                <label class="block text-xs font-bold tracking-[0.2em] text-gray-400 mb-3 uppercase">Flowers Used</label>
                                <input id="form-flowers" type="text" value="${state.formData.flowersUsed || ''}" class="w-full px-6 py-5 bg-gray-50 border border-gray-200 rounded-2xl focus:ring-2 focus:ring-[#064e3b]/20 focus:border-[#064e3b] outline-none transition-all font-medium text-lg" placeholder="e.g. Premium Red Roses, Eucalyptus" />
                            </div>
                            <div>
                                <label class="block text-xs font-bold tracking-[0.2em] text-gray-400 mb-3 uppercase">Delivery Information</label>
                                <input id="form-delivery" type="text" value="${state.formData.deliveryInfo || ''}" class="w-full px-6 py-5 bg-gray-50 border border-gray-200 rounded-2xl focus:ring-2 focus:ring-[#064e3b]/20 focus:border-[#064e3b] outline-none transition-all font-medium text-lg" placeholder="e.g. Fresh delivery across Dhaka." />
                            </div>
                        </div>

                        <div class="flex flex-wrap gap-10 pt-4">
                            <label class="flex items-center gap-4 cursor-pointer group">
                                <input id="form-bestseller" type="checkbox" ${state.formData.bestseller ? 'checked' : ''} class="w-6 h-6 text-[#064e3b] focus:ring-[#064e3b]" />
                                <span class="text-xs font-bold tracking-[0.2em] text-gray-600 uppercase">Mark Signature Bestseller</span>
                            </label>
                            <label class="flex items-center gap-4 cursor-pointer group">
                                <input id="form-newarrival" type="checkbox" ${state.formData.newArrival ? 'checked' : ''} class="w-6 h-6 text-[#064e3b] focus:ring-[#064e3b]" />
                                <span class="text-xs font-bold tracking-[0.2em] text-gray-600 uppercase">Mark New Arrival</span>
                            </label>
                            <label class="flex items-center gap-4 cursor-pointer group">
                                <input id="form-visible" type="checkbox" ${state.formData.visible ? 'checked' : ''} class="w-6 h-6 text-[#064e3b] focus:ring-[#064e3b]" />
                                <span class="text-xs font-bold tracking-[0.2em] text-gray-600 uppercase">Public Display</span>
                            </label>
                        </div>

                        <div class="pt-10 border-t border-gray-100 flex justify-end">
                            <button type="submit" class="premium-btn text-white px-12 py-5 rounded-full font-bold tracking-[0.2em] uppercase text-sm">
                                ${state.editingId ? 'Save Updates' : 'Publish Design'}
                            </button>
                        </div>
                    </form>
                </div>
            `;

            // Hook direct file uploads on gallery input
            const fileInput = document.getElementById('gallery-input');
            if (fileInput) {
                fileInput.onchange = async (e) => {
                    const files = Array.from(e.target.files);
                    if (!files.length) return;
                    if (state.formData.images.length + files.length > 5) {
                        showToast("Max 5 images allowed per bouquet.", true);
                        return;
                    }
                    state.isUploading = true;
                    renderAdminMainSection(); // Refreshes to show upload loading status
                    
                    try {
                        const processed = await Promise.all(files.map(f => compressImage(f, 1000, 0.82)));
                        state.formData.images = [...state.formData.images, ...processed].slice(0, 5);
                        showToast("Images processed successfully.");
                    } catch (err) {
                        showToast("Error uploading images.", true);
                    }
                    
                    state.isUploading = false;
                    renderAdminMainSection();
                };
            }

            // Form Submit Controller
            document.getElementById('bouquet-form').onsubmit = async (e) => {
                e.preventDefault();
                state.formData.name = document.getElementById('form-name').value;
                state.formData.category = document.getElementById('form-category').value;
                state.formData.description = document.getElementById('form-desc').value;
                state.formData.flowersUsed = document.getElementById('form-flowers').value;
                state.formData.deliveryInfo = document.getElementById('form-delivery').value;
                state.formData.bestseller = document.getElementById('form-bestseller').checked;
                state.formData.newArrival = document.getElementById('form-newarrival').checked;
                state.formData.visible = document.getElementById('form-visible').checked;

                if (state.editingId) {
                    state.bouquets = state.bouquets.map(b => b.id === state.editingId ? { ...state.formData, id: state.editingId } : b);
                    showToast("Masterpiece updated successfully.");
                } else {
                    state.bouquets = [{ ...state.formData, id: Date.now().toString() }, ...state.bouquets];
                    showToast("New masterpiece published successfully.");
                }

                // Sync data directly to database
                await dbSet('tf_bouquets_v3', state.bouquets);
                state.isAddingBouquet = false;
                state.editingId = null;
                renderAdminMainSection();
            };
        }

        // Action controllers
        function openNewBouquetForm() {
            state.formData = {
                name: '',
                category: state.categories[0] || '',
                description: '',
                flowersUsed: '',
                deliveryInfo: 'Fresh delivery across Dhaka. Custom arrangements require 24 hours specification notice.',
                images: [],
                bestseller: false,
                newArrival: true,
                visible: true
            };
            state.editingId = null;
            state.isAddingBouquet = true;
            renderAdminMainSection();
        }

        function cancelBouquetForm() {
            state.isAddingBouquet = false;
            state.editingId = null;
            renderAdminMainSection();
        }

        function removeFormImage(idx) {
            state.formData.images = state.formData.images.filter((_, i) => i !== idx);
            renderAdminMainSection();
        }

        async function editBouquet(id) {
            const b = state.bouquets.find(item => item.id === id);
            if (b) {
                state.formData = { ...b, images: [...b.images] };
                state.editingId = id;
                state.isAddingBouquet = true;
                renderAdminMainSection();
            }
        }

        function deleteBouquet(id) {
            askConfirmation("Are you sure you want to permanently delete this bouquet from your studio catalog?", async () => {
                state.bouquets = state.bouquets.filter(b => b.id !== id);
                await dbSet('tf_bouquets_v3', state.bouquets);
                showToast("Masterpiece deleted.");
                renderAdminMainSection();
            });
        }

        // ==========================================
        // ADMIN BRAND SETTINGS CONTROLLERS
        // ==========================================
        function renderSettingsPanel(container) {
            container.innerHTML = `
                <div class="animate-fade-up max-w-4xl mx-auto">
                    <div class="mb-10">
                        <h1 class="text-4xl font-serif text-gray-900 mb-2 font-light">Brand Settings</h1>
                        <p class="text-gray-500 font-light text-sm">Tailor your luxury slogans, logos, and contacts.</p>
                    </div>
                    
                    <div class="bg-white p-10 md:p-14 border border-gray-100 rounded-[3rem] shadow-sm space-y-14">
                        
                        <!-- Logo & Banner Asset Customizer -->
                        <div class="grid grid-cols-1 md:grid-cols-2 gap-10">
                            <div class="bg-gray-50 rounded-[2rem] p-8 text-center border border-gray-100">
                                <p class="text-xs font-bold tracking-[0.2em] text-gray-400 uppercase mb-6">Studio Logo</p>
                                <div class="w-32 h-32 mx-auto rounded-full bg-white shadow-sm border border-gray-200 mb-6 overflow-hidden flex items-center justify-center">
                                    <img id="logo-preview-img" src="${state.settings.logo || 'IMG_0254.png'}" onerror="this.src='IMG_0254.png'" class="w-full h-full object-cover" />
                                </div>
                                <label class="bg-white px-6 py-3 rounded-full text-xs font-bold uppercase tracking-widest border border-gray-200 cursor-pointer hover:bg-gray-100 shadow-sm inline-block">
                                    Change Logo 
                                    <input id="logo-uploader" type="file" accept="image/*" class="hidden" />
                                </label>
                            </div>

                            <div class="bg-gray-50 rounded-[2rem] p-8 text-center border border-gray-100">
                                <p class="text-xs font-bold tracking-[0.2em] text-gray-400 uppercase mb-6">Hero Banner</p>
                                <div class="w-full h-32 mx-auto rounded-2xl bg-white shadow-sm border border-gray-200 mb-6 overflow-hidden flex items-center justify-center">
                                    <img id="banner-preview-img" src="${state.settings.banner || 'IMG_0255.png'}" onerror="this.src='IMG_0255.png'" class="w-full h-full object-cover" />
                                </div>
                                <label class="bg-white px-6 py-3 rounded-full text-xs font-bold uppercase tracking-widest border border-gray-200 cursor-pointer hover:bg-gray-100 shadow-sm inline-block">
                                    Change Banner 
                                    <input id="banner-uploader" type="file" accept="image/*" class="hidden" />
                                </label>
                            </div>
                        </div>

                        <!-- Brand Slogans and Content -->
                        <form id="settings-form" class="space-y-8">
                            <div>
                                <h3 class="text-xl font-serif text-gray-900 mb-8 border-b border-gray-100 pb-4">Studio Slogan</h3>
                                <div class="space-y-6">
                                    <div>
                                        <label class="block text-xs font-bold tracking-[0.2em] text-gray-400 mb-3 uppercase">Main Slogan</label>
                                        <input required id="sett-slogan" type="text" value="${state.settings.heroSlogan}" class="w-full px-6 py-5 bg-gray-50 border border-gray-200 rounded-2xl focus:border-[#064e3b] outline-none font-medium text-lg" />
                                    </div>
                                    <div>
                                        <label class="block text-xs font-bold tracking-[0.2em] text-gray-400 mb-3 uppercase">Description</label>
                                        <textarea required id="sett-desc" rows="3" class="w-full px-6 py-5 bg-gray-50 border border-gray-200 rounded-2xl focus:border-[#064e3b] outline-none font-medium text-lg leading-relaxed">${state.settings.heroDesc}</textarea>
                                    </div>
                                </div>
                            </div>

                            <!-- Integrated Contact CTAs -->
                            <div>
                                <h3 class="text-xl font-serif text-gray-900 mb-8 border-b border-gray-100 pb-4">Contact Integrations</h3>
                                <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                                    <div>
                                        <label class="block text-xs font-bold tracking-[0.2em] text-gray-400 mb-3 uppercase">WhatsApp</label>
                                        <input required id="sett-whatsapp" type="text" value="${state.settings.whatsapp}" class="w-full px-6 py-5 bg-gray-50 border border-gray-200 rounded-2xl outline-none font-bold text-lg" />
                                    </div>
                                    <div>
                                        <label class="block text-xs font-bold tracking-[0.2em] text-gray-400 mb-3 uppercase">Phone Call</label>
                                        <input required id="sett-phone" type="text" value="${state.settings.phone}" class="w-full px-6 py-5 bg-gray-50 border border-gray-200 rounded-2xl outline-none font-bold text-lg" />
                                    </div>
                                    <div class="md:col-span-2">
                                        <label class="block text-xs font-bold tracking-[0.2em] text-gray-400 mb-3 uppercase">Instagram Link</label>
                                        <input required id="sett-instagram" type="text" value="${state.settings.instagram}" class="w-full px-6 py-5 bg-gray-50 border border-gray-200 rounded-2xl outline-none font-medium text-lg" />
                                    </div>
                                    <div class="md:col-span-2">
                                        <label class="block text-xs font-bold tracking-[0.2em] text-gray-400 mb-3 uppercase">TikTok Link</label>
                                        <input required id="sett-tiktok" type="text" value="${state.settings.tiktok}" class="w-full px-6 py-5 bg-gray-50 border border-gray-200 rounded-2xl outline-none font-medium text-lg" />
                                    </div>
                                </div>
                            </div>
                            
                            <div class="flex justify-end pt-10 border-t border-gray-100">
                                <button type="submit" class="premium-btn text-white px-12 py-5 rounded-full font-bold uppercase tracking-[0.2em] text-sm">
                                    Save Brand Settings
                                </button>
                            </div>
                        </form>
                    </div>
                </div>
            `;

            // Logo & Banner Direct Select Logic
            document.getElementById('logo-uploader').onchange = async (e) => {
                const file = e.target.files[0];
                if (!file) return;
                try {
                    const compressed = await compressImage(file, 400, 0.9);
                    state.settings.logo = compressed;
                    document.getElementById('logo-preview-img').src = compressed;
                    await dbSet('tf_settings_v3', state.settings);
                    showToast("Studio Logo updated successfully.");
                } catch (err) {
                    showToast("Error scaling logo image.", true);
                }
            };

            document.getElementById('banner-uploader').onchange = async (e) => {
                const file = e.target.files[0];
                if (!file) return;
                try {
                    const compressed = await compressImage(file, 1600, 0.85);
                    state.settings.banner = compressed;
                    document.getElementById('banner-preview-img').src = compressed;
                    await dbSet('tf_settings_v3', state.settings);
                    showToast("Studio Banner updated successfully.");
                } catch (err) {
                    showToast("Error scaling banner image.", true);
                }
            };

            // Forms Submit logic
            document.getElementById('settings-form').onsubmit = async (e) => {
                e.preventDefault();
                state.settings.heroSlogan = document.getElementById('sett-slogan').value;
                state.settings.heroDesc = document.getElementById('sett-desc').value;
                state.settings.whatsapp = document.getElementById('sett-whatsapp').value;
                state.settings.phone = document.getElementById('sett-phone').value;
                state.settings.instagram = document.getElementById('sett-instagram').value;
                state.settings.tiktok = document.getElementById('sett-tiktok').value;

                await dbSet('tf_settings_v3', state.settings);
                showToast("Settings Saved Successfully!");
                updateView();
            };
        }

        // Router triggers
        function setCategoryFilter(category) {
            state.selectedCategory = category;
            updateView();
        }

        function openDetailModal(id) {
            const b = state.bouquets.find(item => item.id === id);
            if (b) {
                state.selectedBouquet = b;
                updateView();
            }
        }

        function closeDetailModal() {
            state.selectedBouquet = null;
            updateView();
        }

        // ==========================================
        // 13. SYSTEM BOOTSTRAP (Data Load Mechanics)
        // ==========================================
        async function bootstrap() {
            try {
                // Read from IndexedDB safely on bootup
                const savedBouquets = await dbGet('tf_bouquets_v3');
                const savedCategories = await dbGet('tf_categories_v3');
                const savedSettings = await dbGet('tf_settings_v3');
                
                if (savedBouquets && savedBouquets.length > 0) {
                    state.bouquets = savedBouquets;
                } else {
                    // Pre-populate with beautiful, professional default pieces to ensure direct visual appeal on first load
                    state.bouquets = [
                        {
                            id: 'demo-1',
                            name: 'Crimson Love Bouquet',
                            category: '🌹 Rose Bouquet',
                            description: 'A timeless expression of deep affection, structured elegantly with premium long-stemmed red roses and soft eucalyptus branches.',
                            flowersUsed: 'Premium Red Roses, Baby Breath, eucalyptus foliage',
                            deliveryInfo: 'Bespoke hand delivery in Dhaka. Freshness guaranteed for 7 days.',
                            images: ['IMG_1382.png'],
                            bestseller: true,
                            newArrival: true,
                            visible: true
                        },
                        {
                            id: 'demo-2',
                            name: 'Summer Sun Radiance',
                            category: '🌻 Sunflower Bouquet',
                            description: 'Bright and energetic. Capturing the warm organic essence of summer sun rays using handpicked sunflowers and rustic wrapping.',
                            flowersUsed: 'Fresh Sunflowers, gold wrapping paper, seasonal green leaves',
                            deliveryInfo: 'Protected visual canvas frame wrap, delivered with ice blocks.',
                            images: ['IMG_1382.png'],
                            bestseller: false,
                            newArrival: true,
                            visible: true
                        },
                        {
                            id: 'demo-3',
                            name: 'Chocolate Bloom Curation',
                            category: '🍫 Chocolate Bouquet',
                            description: 'A luxurious fusion of exquisite dark cocoa elements nestled beautifully inside fresh white lilies and luxury cream wrapping canvas.',
                            flowersUsed: 'Imported Dark Chocolates, White Lilies, satin cream wrapping',
                            deliveryInfo: 'Climate-controlled van delivery to prevent chocolate melting.',
                            images: ['IMG_1382.png'],
                            bestseller: true,
                            newArrival: false,
                            visible: true
                        }
                    ];
                    await dbSet('tf_bouquets_v3', state.bouquets);
                }

                if (savedCategories) {
                    // Securely merge categories
                    state.categories = Array.from(new Set([...EXCLUSIVE_CATEGORIES, ...savedCategories]));
                }
                if (savedSettings) {
                    state.settings = savedSettings;
                }
            } catch (err) {
                console.error("IndexedDB initial load error, falling back to clean slate", err);
            } finally {
                // Dissolve loader screen seamlessly
                const loader = document.getElementById('loader-screen');
                if (loader) {
                    loader.classList.add('opacity-0', 'pointer-events-none');
                }
                updateView();
            }
        }

        // Bootstrap on screen completion
        window.onload = () => {
            bootstrap();
        };
    </script>
</body>
</html>
