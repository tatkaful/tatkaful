
<html lang="en" class="scroll-smooth overflow-x-hidden">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>TATKA-FUL | Luxury Floral Concepts</title>
    <!-- Tailwind CSS CDN -->
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
                            100: '#fbf8eb',
                            500: '#ffd700',
                            600: '#d4af37',
                            700: '#b8860b'
                        },
                        emerald: {
                            950: '#022c22',
                            900: '#064e3b',
                            50: '#ecfdf5'
                        }
                    }
                }
            }
        }
    </script>
    <!-- Google Fonts Playfair Display & Plus Jakarta Sans -->
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,500;0,600;0,700;1,400&family=Plus+Jakarta+Sans:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    
    <!-- Lucide Vector Icons Integration -->
    <script src="https://unpkg.com/lucide@latest"></script>

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
            color: var(--luxury-black);
            overflow-x: hidden;
            width: 100%;
            -webkit-tap-highlight-color: transparent;
        }

        .glass-header {
            background: rgba(252, 251, 249, 0.82);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border-bottom: 1px solid rgba(17, 17, 17, 0.03);
        }

        .luxury-card {
            background: #ffffff;
            border: 1px solid rgba(17, 17, 17, 0.03);
            box-shadow: 0 10px 30px -10px rgba(0, 0, 0, 0.03);
            transition: all 0.5s cubic-bezier(0.16, 1, 0.3, 1);
        }

        @media (hover: hover) {
            .luxury-card:hover {
                box-shadow: 0 30px 60px -15px rgba(6, 78, 59, 0.07);
                transform: translateY(-8px);
            }
        }

        .premium-btn-primary {
            background: var(--luxury-black);
            color: #ffffff;
            border: 1px solid var(--luxury-black);
            transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
        }

        .premium-btn-primary:hover {
            background: transparent;
            color: var(--luxury-black);
        }

        .premium-btn-gold {
            background: linear-gradient(135deg, var(--gold-accent) 0%, #b8860b 100%);
            color: #ffffff;
            box-shadow: 0 10px 25px -5px rgba(212, 175, 55, 0.25);
            transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
        }

        .premium-btn-gold:hover {
            box-shadow: 0 15px 30px -5px rgba(212, 175, 55, 0.4);
            transform: translateY(-1px);
        }

        /* Custom Scrollbar */
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
            from { opacity: 0; transform: translateY(25px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .animate-fade-up {
            animation: fadeUp 0.8s cubic-bezier(0.16, 1, 0.3, 1) forwards;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        .animate-fade-in {
            animation: fadeIn 0.4s ease-out forwards;
        }
    </style>
</head>
<body class="antialiased selection:bg-[#064e3b] selection:text-white overflow-x-hidden">

    <!-- Brand Preloader -->
    <div id="loader-screen" class="fixed inset-0 z-50 bg-[#fcfbf9] flex flex-col items-center justify-center transition-all duration-700">
        <div class="flex flex-col items-center space-y-4">
            <svg class="animate-spin h-8 w-8 text-[#064e3b]" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24">
                <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
                <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
            </svg>
            <h1 class="text-4xl font-serif tracking-[0.15em] text-gray-950 uppercase font-light">TATKA-FUL</h1>
            <p class="text-[9px] uppercase tracking-[0.3em] text-[#d4af37] font-semibold">Premium Floral Studio</p>
        </div>
    </div>

    <!-- MAIN SPA WRAPPER CONTAINER -->
    <div id="app-root" class="min-h-screen flex flex-col justify-between overflow-x-hidden w-full">
        <!-- Inside here we mount the SPA architecture via JavaScript -->
    </div>

    <!-- Native replacements of system prompts (No alert / No confirm) -->
    <div id="custom-alert-container" class="fixed top-6 right-6 z-50 flex flex-col gap-3 max-w-sm pointer-events-none"></div>
    <div id="custom-confirm-modal" class="fixed inset-0 z-50 flex items-center justify-center p-4 bg-black/50 backdrop-blur-sm transition-opacity hidden"></div>

    <script>
        // --- INDEXEDDB STORAGE CONFIGS ---
        const DB_NAME = 'TatkaFulPremiumDB';
        const STORE_NAME = 'store';

        function initDB() {
            return new Promise((resolve, reject) => {
                const request = indexedDB.open(DB_NAME, 4); // Database version updated to reflect schema expansion
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

        // Exact exclusive luxury bouquet category configurations
        const EXCLUSIVE_CATEGORIES = [
            '🌹 Rose Bouquet',
            '🌻 Sunflower Bouquet',
            '💐 Mixed Bouquet',
            '🍫 Chocolate Bouquet',
            '💵 Money Bouquet',
            '🎁 Gift Combo'
        ];

        // Global State Tree
        let state = {
            currentView: 'home', // 'home' | 'admin_login' | 'admin_dashboard'
            selectedCategory: 'All',
            selectedBouquet: null,
            searchQuery: '',
            isMobileMenuOpen: false,
            activeDetailImageIndex: 0,
            bouquets: [],
            categories: EXCLUSIVE_CATEGORIES,
            settings: {
                logo: '', 
                banner: '', 
                phone: '01410619501',
                whatsapp: '01410619501',
                instagram: 'https://instagram.com/tatka_ful',
                tiktok: 'https://tiktok.com/@tatka.ful',
                facebook: 'https://facebook.com',
                heroSlogan: 'Elegance in Every Petal.',
                heroDesc: 'Curating premium visual flower concepts and luxury, minimal botanical architectures tailored to preserve your memories.'
            },
            adminTab: 'bouquets', // 'bouquets' | 'settings'
            isAddingBouquet: false,
            editingId: null,
            formData: {
                name: '',
                category: EXCLUSIVE_CATEGORIES[0],
                description: '',
                flowersUsed: '',
                deliveryInfo: 'Bespoke hand-delivery across Dhaka. Custom requirements require a 24-hour request buffer.',
                images: [],
                bestseller: false,
                newArrival: true,
                visible: true
            },
            isUploading: false
        };

        // UI Toast Mechanism (Premium look and feel)
        function showToast(message, isError = false) {
            const container = document.getElementById('custom-alert-container');
            if (!container) return;

            const toast = document.createElement('div');
            toast.className = `p-4 rounded-2xl shadow-xl border text-sm font-semibold pointer-events-auto flex items-center gap-3 transition-all transform translate-y-2 opacity-0 ${isError ? 'bg-red-50 text-red-800 border-red-200' : 'bg-emerald-50 text-emerald-950 border-emerald-100'}`;
            toast.innerHTML = `
                <span class="w-2.5 h-2.5 rounded-full ${isError ? 'bg-red-500' : 'bg-emerald-700'} animate-pulse"></span>
                <span>${message}</span>
            `;
            container.appendChild(toast);

            // Trigger Transition In
            setTimeout(() => {
                toast.classList.remove('translate-y-2', 'opacity-0');
            }, 10);

            // Auto Dismantle after 3.2s
            setTimeout(() => {
                toast.classList.add('translate-y-2', 'opacity-0');
                setTimeout(() => toast.remove(), 400);
            }, 3200);
        }

        // Custom Confirm Dialogue Mechanism (Modern, no default alert popups)
        function askConfirmation(message, onConfirm) {
            const modal = document.getElementById('custom-confirm-modal');
            if (!modal) return;

            modal.innerHTML = `
                <div class="bg-white p-8 rounded-[2rem] max-w-sm w-full border border-gray-100 shadow-2xl text-center animate-fade-up">
                    <h3 class="text-xl font-serif text-gray-950 mb-3 font-semibold">Please Confirm</h3>
                    <p class="text-gray-500 text-sm font-light mb-8 leading-relaxed">${message}</p>
                    <div class="flex gap-4">
                        <button id="confirm-btn-cancel" class="flex-1 py-3.5 bg-gray-100 rounded-xl text-xs font-bold text-gray-600 hover:bg-gray-200 transition-all uppercase tracking-wider">Cancel</button>
                        <button id="confirm-btn-yes" class="flex-1 py-3.5 bg-red-600 rounded-xl text-xs font-bold text-white hover:bg-red-700 transition-all uppercase tracking-wider">Yes, Delete</button>
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

        // Phone formatter for WhatsApp
        function formatWhatsApp(number) {
            let formatted = number.replace(/[^0-9]/g, '');
            if (formatted.startsWith('0')) formatted = '88' + formatted;
            return formatted;
        }

        // High Fidelity Canvas Image Downscaling & Compression
        function compressImage(file, maxWidth = 1000, quality = 0.82) {
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

        async function updateView() {
            const root = document.getElementById('app-root');
            if (state.currentView === 'home') {
                renderHome(root);
            } else if (state.currentView === 'admin_login') {
                renderAdminLogin(root);
            } else if (state.currentView === 'admin_dashboard') {
                renderAdminDashboard(root);
            }
            // Trigger Lucide parsing on dynamic additions
            lucide.createIcons();
        }

        // Handle Hamburger Mobile Drawer
        function toggleMobileMenu() {
            state.isMobileMenuOpen = !state.isMobileMenuOpen;
            const mobileMenu = document.getElementById('mobile-menu-drawer');
            if (mobileMenu) {
                if (state.isMobileMenuOpen) {
                    mobileMenu.classList.remove('hidden');
                    setTimeout(() => mobileMenu.classList.remove('opacity-0', '-translate-y-4'), 10);
                } else {
                    mobileMenu.classList.add('opacity-0', '-translate-y-4');
                    setTimeout(() => mobileMenu.classList.add('hidden'), 300);
                }
            }
        }

        // Double Click is upgraded to 4-Clicks (Quadruple Click) access tracker
        let clickCount = 0;
        let clickTimer;
        function handleSecretClick() {
            clickCount++;
            clearTimeout(clickTimer);
            if (clickCount >= 4) {
                clickCount = 0;
                state.currentView = 'admin_login';
                updateView();
                showToast("Opening Secure Studio Workshop...");
            } else {
                clickTimer = setTimeout(() => {
                    clickCount = 0;
                }, 1500); // 1.5 seconds threshold to complete 4 clicks
            }
        }

        // WhatsApp Order triggering
        function triggerWhatsAppOrder(event, bouquetName) {
            if (event) event.stopPropagation();
            const rawMessage = `Hello TATKA-FUL! I'm interested in ordering the '${bouquetName}'. Please share the price and details.`;
            const encoded = encodeURIComponent(rawMessage);
            const waUrl = `https://wa.me/${formatWhatsApp(state.settings.whatsapp)}?text=${encoded}`;
            window.open(waUrl, '_blank');
        }

        // Dynamic categories selector filter
        function setCategoryFilter(category) {
            state.selectedCategory = category;
            updateView();
            const target = document.getElementById('featured');
            if (target) {
                target.scrollIntoView({ behavior: 'smooth', block: 'start' });
            }
        }

        // Live Search implementation
        let searchTimeout;
        function debounceSearch() {
            clearTimeout(searchTimeout);
            searchTimeout = setTimeout(() => {
                updateView();
                const searchInput = document.getElementById('live-search-input');
                if (searchInput) {
                    searchInput.focus();
                    searchInput.setSelectionRange(searchInput.value.length, searchInput.value.length);
                }
            }, 300);
        }

        // Details Modal triggering
        function openDetailModal(id) {
            const b = state.bouquets.find(item => item.id === id);
            if (b) {
                state.selectedBouquet = b;
                state.activeDetailImageIndex = 0; // reset carousel
                updateView();
            }
        }

        function closeDetailModal() {
            state.selectedBouquet = null;
            updateView();
        }

        // Slider Navigation inside Product Modal
        function setDetailImage(index) {
            state.activeDetailImageIndex = index;
            const previewImg = document.getElementById('detail-active-img');
            if (previewImg && state.selectedBouquet.images[index]) {
                previewImg.src = state.selectedBouquet.images[index];
            }
            // Update thumbs boundary
            const thumbs = document.querySelectorAll('.detail-thumb');
            thumbs.forEach((th, i) => {
                if (i === index) {
                    th.classList.add('ring-2', 'ring-emerald-900', 'ring-offset-2', 'opacity-100');
                    th.classList.remove('opacity-60');
                } else {
                    th.classList.remove('ring-2', 'ring-emerald-900', 'ring-offset-2', 'opacity-100');
                    th.classList.add('opacity-60');
                }
            });
        }

        // Accordion function
        function toggleFaqAccordion(btn) {
            const content = btn.nextElementSibling;
            const icon = btn.querySelector('.accordion-icon');
            if (content.classList.contains('hidden')) {
                content.classList.remove('hidden');
                icon.style.transform = 'rotate(180deg)';
            } else {
                content.classList.add('hidden');
                icon.style.transform = 'rotate(0deg)';
            }
        }

        function renderHome(container) {
            const visibleBouquets = state.bouquets.filter(b => b.visible !== false);
            
            // Dynamic Filtering Configuration
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

            const bestSellers = visibleBouquets.filter(b => b.bestseller);
            const newArrivals = visibleBouquets.filter(b => b.newArrival);

            container.innerHTML = `
                <!-- Navigation -->
                <nav class="fixed w-full top-0 z-40 glass-header">
                    <div class="max-w-7xl mx-auto px-4 sm:px-6 h-20 sm:h-24 flex items-center justify-between">
                        <!-- Left Brand Logo -->
                        <div class="flex items-center gap-2.5 sm:gap-3.5 cursor-pointer group" onclick="window.scrollTo({top:0, behavior:'smooth'})">
                            <div class="w-10 h-10 sm:w-12 sm:h-12 rounded-full overflow-hidden shadow-md border border-gray-100 transition-transform group-hover:scale-105">
                                <img src="${state.settings.logo || 'IMG_1382.png'}" onerror="this.src='IMG_1382.png'" alt="TATKA-FUL Studio Logo" class="w-full h-full object-cover" />
                            </div>
                            <span class="text-lg sm:text-xl md:text-2xl font-serif tracking-[0.1em] text-gray-950 uppercase font-light">TATKA-FUL</span>
                        </div>

                        <!-- Center Desktop Navigation Items -->
                        <div class="hidden lg:flex items-center gap-10 text-xs font-bold tracking-[0.2em] uppercase text-gray-500">
                            <a href="#hero" class="hover:text-black transition-colors">Home</a>
                            <a href="#featured" class="hover:text-black transition-colors">Shop</a>
                            <a href="#why-choose" class="hover:text-black transition-colors">About Us</a>
                            <a href="#faq" class="hover:text-black transition-colors">FAQ</a>
                            <a href="#contact" class="hover:text-black transition-colors">Contact</a>
                        </div>

                        <!-- Right CTA elements -->
                        <div class="flex items-center gap-4">
                            <a href="https://wa.me/${formatWhatsApp(state.settings.whatsapp)}" target="_blank" rel="noreferrer" class="hidden md:inline-flex premium-btn-gold text-white px-7 py-3 rounded-full text-[10px] font-bold uppercase tracking-[0.15em]">
                                Studio WhatsApp
                            </a>
                            <button onclick="toggleMobileMenu()" class="lg:hidden p-2.5 bg-white border border-gray-100 rounded-full text-gray-900 flex items-center justify-center">
                                <i data-lucide="menu" class="w-5 h-5"></i>
                            </button>
                        </div>
                    </div>

                    <!-- Mobile Slide Drawer Navigation (Fixed sideways margin overflow) -->
                    <div id="mobile-menu-drawer" class="hidden lg:hidden bg-white/95 backdrop-blur-xl border-b border-gray-100 px-4 py-6 flex flex-col space-y-5 transition-all duration-300 transform opacity-0 -translate-y-4 shadow-lg w-full max-w-full">
                        <div class="flex flex-col gap-4 text-xs font-bold tracking-widest uppercase text-gray-600">
                            <a href="#hero" onclick="toggleMobileMenu()" class="hover:text-black py-1">Home</a>
                            <a href="#featured" onclick="toggleMobileMenu()" class="hover:text-black py-1">Shop</a>
                            <a href="#why-choose" onclick="toggleMobileMenu()" class="hover:text-black py-1">About Us</a>
                            <a href="#faq" onclick="toggleMobileMenu()" class="hover:text-black py-1">FAQ</a>
                            <a href="#contact" onclick="toggleMobileMenu()" class="hover:text-black py-1">Contact</a>
                        </div>
                        <div class="pt-3 border-t border-gray-100">
                            <a href="https://wa.me/${formatWhatsApp(state.settings.whatsapp)}" target="_blank" rel="noreferrer" class="w-full flex justify-center items-center gap-2.5 premium-btn-gold text-white py-3.5 rounded-full text-[10px] font-bold uppercase tracking-widest shadow-xl shadow-amber-500/10">
                                <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946C.06 5.348 5.397.01 12.008.01c3.202.001 6.212 1.246 8.477 3.514 2.266 2.268 3.507 5.28 3.505 8.484-.004 6.657-5.34 11.997-11.953 11.997-2.005-.001-3.973-.502-5.713-1.455L0 24zm6.59-4.846c1.6.95 3.188 1.449 4.625 1.451 5.436 0 9.851-4.398 9.854-9.807.001-2.621-1.013-5.086-2.86-6.935C16.36 1.913 13.9.894 11.285.894c-5.438 0-9.854 4.398-9.858 9.808 0 2.037.533 4.024 1.547 5.765l-.99 3.613 3.73-.973h.001a9.78 9.78 0 0 0 4.332 1.048z"/></svg> WhatsApp Order
                            </a>
                        </div>
                    </div>
                </nav>

                <!-- Hero Section (Strict layout constraints sideways) -->
                <section id="hero" class="relative pt-32 pb-20 md:pt-48 md:pb-32 px-4 flex items-center justify-center min-h-[75vh] overflow-hidden w-full max-w-full">
                    <div class="absolute inset-0 z-0">
                        <img src="${state.settings.banner || 'IMG_1382.png'}" onerror="this.src='IMG_1382.png'" alt="Luxury Flower Studio Setup" class="w-full h-full object-cover opacity-[0.14] scale-105" />
                        <div class="absolute inset-0 bg-gradient-to-b from-[#fcfbf9]/95 via-[#fcfbf9]/50 to-[#fcfbf9]"></div>
                    </div>

                    <div class="max-w-4xl mx-auto text-center relative z-10 animate-fade-up w-full px-2">
                        <span class="inline-block py-1.5 px-4 rounded-full bg-[#064e3b]/5 text-[#064e3b] text-[9px] sm:text-[10px] font-bold uppercase tracking-[0.3em] mb-5 border border-[#064e3b]/10">
                            Premium Flower Atelier
                        </span>
                        <h1 class="text-3xl sm:text-5xl md:text-7xl lg:text-8xl font-serif text-gray-950 mb-6 leading-[1.2] tracking-tight font-light uppercase">
                            ${state.settings.heroSlogan}
                        </h1>
                        <p class="text-xs sm:text-base text-gray-600 mb-10 max-w-2xl mx-auto font-light leading-relaxed">
                            ${state.settings.heroDesc}
                        </p>
                        <a href="#featured" class="inline-flex items-center gap-3 premium-btn-primary text-white px-8 py-4 rounded-full text-[11px] uppercase tracking-widest font-semibold shadow-xl shadow-black/5">
                            Browse Catalog 
                            <i data-lucide="chevron-right" class="w-4 h-4"></i>
                        </a>
                    </div>
                </section>

                <!-- Featured Shop Section -->
                <section id="featured" class="px-4 sm:px-6 py-20 max-w-7xl mx-auto border-t border-gray-100 w-full overflow-hidden">
                    <div class="flex flex-col md:flex-row justify-between items-start md:items-end gap-6 mb-12 w-full">
                        <div class="max-w-full">
                            <span class="text-[9px] sm:text-[10px] uppercase font-bold tracking-[0.3em] text-[#d4af37] block mb-2">TATKA-FUL Collections</span>
                            <h2 class="text-2xl sm:text-3xl md:text-5xl font-serif text-gray-950 font-light uppercase tracking-wide leading-tight">Featured Bouquets</h2>
                        </div>
                        
                        <!-- Premium Filter-Search Combo -->
                        <div class="relative w-full md:w-80 shrink-0 max-w-full">
                            <span class="absolute inset-y-0 left-0 pl-4 flex items-center pointer-events-none">
                                <svg class="w-4 h-4 text-emerald-800" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"></path>
                                </svg>
                            </span>
                            <input id="live-search-input" type="text" placeholder="Search curated bouquet..." value="${state.searchQuery}" class="w-full pl-11 pr-5 py-3.5 bg-white border border-gray-100 rounded-full focus:outline-none focus:border-[#d4af37] focus:ring-2 focus:ring-[#d4af37]/20 text-xs sm:text-sm tracking-wide transition-all shadow-[0_4px_20px_rgba(6,78,59,0.03)]" />
                        </div>
                    </div>

                    <!-- Horizontal Categorical Quick Filters with Scroll Protection -->
                    <div class="w-full overflow-hidden mb-10">
                        <div class="flex gap-2.5 overflow-x-auto pb-4 scrollbar-hide snap-x border-b border-gray-50 w-full max-w-full">
                            <button onclick="setCategoryFilter('All')" class="snap-start whitespace-nowrap px-6 py-3 rounded-full transition-all duration-300 text-[10px] font-bold tracking-widest uppercase ${state.selectedCategory === 'All' ? 'bg-[#111111] text-white shadow-md' : 'bg-white text-gray-500 hover:text-black border border-gray-100'}">
                                All Designs
                            </button>
                            ${state.categories.map(cat => `
                                <button onclick="setCategoryFilter('${cat}')" class="snap-start whitespace-nowrap px-6 py-3 rounded-full transition-all duration-300 text-[10px] font-bold tracking-widest uppercase ${state.selectedCategory === cat ? 'bg-[#111111] text-white shadow-md' : 'bg-white text-gray-500 hover:text-black border border-gray-100'}">
                                    ${cat}
                                </button>
                            `).join('')}
                        </div>
                    </div>

                    <!-- Compact Double Column Portfolio Grid on Mobile Device (Ultra Premium) -->
                    ${filteredBouquets.length === 0 ? `
                        <div class="text-center py-16 bg-white rounded-3xl border border-gray-100 px-4">
                            <i data-lucide="info" class="w-8 h-8 text-gray-300 mx-auto mb-3"></i>
                            <h3 class="text-lg font-serif text-gray-950 mb-1 font-medium">No results found</h3>
                            <p class="text-gray-400 font-light text-xs sm:text-sm">Modify your search query or pick another floral category.</p>
                        </div>
                    ` : `
                        <div class="grid grid-cols-2 md:grid-cols-2 lg:grid-cols-3 gap-3 sm:gap-6 md:gap-8 w-full">
                            ${filteredBouquets.map((b) => `
                                <div class="group flex flex-col cursor-pointer w-full bg-white rounded-2xl sm:rounded-[2rem] p-2 sm:p-4 border border-gray-100 shadow-sm hover:shadow-md transition-all duration-300" onclick="openDetailModal('${b.id}')">
                                    <div class="relative aspect-[4/5] rounded-xl sm:rounded-[1.5rem] overflow-hidden bg-stone-100 w-full mb-3">
                                        <img src="${b.images[0] || 'IMG_1382.png'}" onerror="this.src='IMG_1382.png'" alt="${b.name}" class="w-full h-full object-cover transition-transform duration-[1.5s] group-hover:scale-105" loading="lazy" />
                                        <div class="absolute inset-0 bg-gradient-to-t from-black/40 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-500 flex items-end p-4">
                                            <span class="text-white text-[8px] font-bold uppercase tracking-widest border border-white/20 bg-black/20 backdrop-blur-md px-4 py-2 rounded-full hidden sm:inline-block">Examine Design</span>
                                        </div>
                                        ${b.bestseller ? `
                                            <div class="absolute top-2 left-2 sm:top-4 sm:left-4 bg-white/95 backdrop-blur-md text-[#b8860b] text-[7px] sm:text-[8px] font-bold uppercase tracking-[0.2em] px-2.5 py-1 sm:px-3.5 sm:py-2 rounded-full flex items-center gap-1 shadow-md">
                                                <span class="w-1 h-1 sm:w-1.5 sm:h-1.5 bg-[#b8860b] rounded-full animate-pulse"></span> Signature
                                            </div>
                                        ` : ''}
                                    </div>
                                    <div class="px-1 flex flex-col flex-grow">
                                        <p class="text-[7px] sm:text-[9px] font-bold tracking-[0.15em] sm:tracking-[0.25em] text-[#064e3b] uppercase mb-1">${b.category}</p>
                                        <h3 class="text-xs sm:text-lg font-serif text-gray-950 mb-1 group-hover:text-[#064e3b] transition-colors leading-tight font-medium uppercase truncate">${b.name}</h3>
                                        <p class="text-gray-500 text-[9px] sm:text-xs font-light leading-snug mb-3 line-clamp-1 sm:line-clamp-2">${b.description}</p>
                                        
                                        <!-- Compact Order Button -->
                                        <button onclick="triggerWhatsAppOrder(event, '${b.name}')" class="mt-auto w-full flex items-center justify-center gap-1 py-2 sm:py-3 bg-[#022c22] hover:bg-[#d4af37] text-white hover:text-white transition-all text-[8px] sm:text-[10px] font-bold uppercase tracking-wider rounded-full shadow-md">
                                            <svg class="w-3 h-3 sm:w-4 sm:h-4 shrink-0" fill="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946C.06 5.348 5.397.01 12.008.01c3.202.001 6.212 1.246 8.477 3.514 2.266 2.268 3.507 5.28 3.505 8.484-.004 6.657-5.34 11.997-11.953 11.997-2.005-.001-3.973-.502-5.713-1.455L0 24zm6.59-4.846c1.6.95 3.188 1.449 4.625 1.451 5.436 0 9.851-4.398 9.854-9.807.001-2.621-1.013-5.086-2.86-6.935C16.36 1.913 13.9.894 11.285.894c-5.438 0-9.854 4.398-9.858 9.808 0 2.037.533 4.024 1.547 5.765l-.99 3.613 3.73-.973h.001a9.78 9.78 0 0 0 4.332 1.048z"/></svg>
                                            <span>Order on WhatsApp</span>
                                        </button>
                                    </div>
                                </div>
                            `).join('')}
                        </div>
                    `}
                </section>

                <!-- Best Sellers Section -->
                <section class="bg-stone-50 py-20 px-4 sm:px-6 border-t border-gray-100 w-full overflow-hidden">
                    <div class="max-w-7xl mx-auto">
                        <div class="mb-12 text-center">
                            <span class="text-[9px] sm:text-[10px] uppercase font-bold tracking-[0.3em] text-[#d4af37] block mb-2">Exquisite Choices</span>
                            <h2 class="text-2xl sm:text-3xl md:text-5xl font-serif text-gray-950 font-light uppercase tracking-wide">Signature Best Sellers</h2>
                        </div>
                        ${bestSellers.length === 0 ? `
                            <p class="text-center text-gray-400 font-light text-xs sm:text-sm">No design curated as bestseller yet.</p>
                        ` : `
                            <div class="grid grid-cols-2 md:grid-cols-2 lg:grid-cols-3 gap-3 sm:gap-6 md:gap-8 w-full">
                                ${bestSellers.slice(0, 3).map(b => `
                                    <div class="bg-white p-2.5 sm:p-5 rounded-2xl sm:rounded-[2.5rem] luxury-card flex flex-col cursor-pointer w-full" onclick="openDetailModal('${b.id}')">
                                        <div class="relative aspect-square rounded-xl sm:rounded-2xl overflow-hidden mb-3.5 sm:mb-5 bg-stone-100">
                                            <img src="${b.images[0] || 'IMG_1382.png'}" onerror="this.src='IMG_1382.png'" class="w-full h-full object-cover" />
                                        </div>
                                        <div class="px-1 flex-grow flex flex-col">
                                            <p class="text-[7px] sm:text-[9px] font-bold tracking-[0.15em] sm:tracking-[0.25em] text-[#064e3b] uppercase mb-1">${b.category}</p>
                                            <h3 class="text-xs sm:text-lg font-serif text-gray-950 mb-1 font-semibold uppercase truncate">${b.name}</h3>
                                            <p class="text-gray-500 text-[9px] sm:text-sm font-light mb-3 line-clamp-1 sm:line-clamp-2">${b.description}</p>
                                            <button onclick="triggerWhatsAppOrder(event, '${b.name}')" class="mt-auto w-full flex items-center justify-center gap-1 py-2 sm:py-3 bg-gradient-to-r from-emerald-950 to-emerald-900 text-white hover:from-[#d4af37] hover:to-[#b8860b] transition-all duration-300 text-[8px] sm:text-[10px] font-bold uppercase tracking-widest rounded-full shadow-lg">
                                                <svg class="w-3 h-3 sm:w-4 sm:h-4 shrink-0" fill="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946C.06 5.348 5.397.01 12.008.01c3.202.001 6.212 1.246 8.477 3.514 2.266 2.268 3.507 5.28 3.505 8.484-.004 6.657-5.34 11.997-11.953 11.997-2.005-.001-3.973-.502-5.713-1.455L0 24zm6.59-4.846c1.6.95 3.188 1.449 4.625 1.451 5.436 0 9.851-4.398 9.854-9.807.001-2.621-1.013-5.086-2.86-6.935C16.36 1.913 13.9.894 11.285.894c-5.438 0-9.854 4.398-9.858 9.808 0 2.037.533 4.024 1.547 5.765l-.99 3.613 3.73-.973h.001a9.78 9.78 0 0 0 4.332 1.048z"/></svg> <span>ORDER VIA WHATSAPP</span>
                                            </button>
                                        </div>
                                    </div>
                                `).join('')}
                            </div>
                        `}
                    </div>
                </section>

                <!-- New Seasonal Arrivals -->
                <section class="py-20 px-4 sm:px-6 border-t border-gray-100 w-full overflow-hidden">
                    <div class="max-w-7xl mx-auto">
                        <div class="mb-12 text-center">
                            <span class="text-[9px] sm:text-[10px] uppercase font-bold tracking-[0.3em] text-[#d4af37] block mb-2">Fresh From Studio</span>
                            <h2 class="text-2xl sm:text-3xl md:text-5xl font-serif text-gray-950 font-light uppercase tracking-wide">New Seasonal Arrivals</h2>
                        </div>
                        ${newArrivals.length === 0 ? `
                            <p class="text-center text-gray-400 font-light text-xs sm:text-sm">No new design uploads published recently.</p>
                        ` : `
                            <div class="grid grid-cols-2 md:grid-cols-2 lg:grid-cols-3 gap-3 sm:gap-6 md:gap-8 w-full">
                                ${newArrivals.slice(0, 3).map(b => `
                                    <div class="group cursor-pointer flex flex-col w-full bg-white p-2.5 sm:p-4 rounded-2xl sm:rounded-[2rem] border border-gray-100 shadow-sm" onclick="openDetailModal('${b.id}')">
                                        <div class="relative aspect-[4/5] rounded-xl sm:rounded-[1.5rem] overflow-hidden bg-stone-100 mb-3.5">
                                            <img src="${b.images[0] || 'IMG_1382.png'}" onerror="this.src='IMG_1382.png'" class="w-full h-full object-cover transition-transform duration-700 group-hover:scale-105" />
                                            <div class="absolute top-2 left-2 bg-emerald-950 text-white text-[7px] sm:text-[8px] font-bold uppercase tracking-[0.2em] px-2 py-1 rounded-full shadow-md">
                                                New Harvest
                                            </div>
                                        </div>
                                        <div class="px-1">
                                            <h3 class="text-xs sm:text-lg font-serif text-gray-900 mb-1 font-medium uppercase tracking-wide truncate">${b.name}</h3>
                                            <p class="text-gray-500 text-[9px] sm:text-sm font-light line-clamp-1 mb-3">${b.description}</p>
                                            <button onclick="triggerWhatsAppOrder(event, '${b.name}')" class="w-full flex items-center justify-center gap-1 py-2 sm:py-3 border border-emerald-900 text-emerald-900 hover:bg-[#022c22] hover:text-white transition-all text-[8px] sm:text-[10px] font-bold uppercase tracking-widest rounded-full">
                                                Order on WhatsApp
                                            </button>
                                        </div>
                                    </div>
                                `).join('')}
                            </div>
                        `}
                    </div>
                </section>

                <!-- Why Choose Us -->
                <section id="why-choose" class="bg-[#f0f2ee] py-20 px-4 sm:px-6 border-t border-gray-100 w-full overflow-hidden">
                    <div class="max-w-7xl mx-auto">
                        <div class="max-w-3xl mb-12">
                            <span class="text-[9px] sm:text-[10px] uppercase font-bold tracking-[0.3em] text-[#d4af37] block mb-2">Our Manifesto</span>
                            <h2 class="text-2xl sm:text-3xl md:text-5xl font-serif text-gray-950 leading-tight font-light uppercase tracking-wide">Why Choose TATKA-FUL</h2>
                        </div>
                        <div class="grid grid-cols-1 md:grid-cols-3 gap-6 sm:gap-8 w-full">
                            <div class="bg-white p-8 sm:p-10 rounded-[2rem] sm:rounded-[2.5rem] border border-black/5 shadow-sm">
                                <span class="text-2xl sm:text-3xl font-serif text-[#d4af37] block mb-4">01</span>
                                <h3 class="text-lg sm:text-xl font-serif mb-3 text-gray-900 uppercase font-medium">Bespoke Design</h3>
                                <p class="text-gray-500 text-xs sm:text-sm leading-relaxed font-light">Every setup is a customized visual art piece curated to match your aesthetic specification perfectly.</p>
                            </div>
                            <div class="bg-white p-8 sm:p-10 rounded-[2rem] sm:rounded-[2.5rem] border border-black/5 shadow-sm">
                                <span class="text-2xl sm:text-3xl font-serif text-[#d4af37] block mb-4">02</span>
                                <h3 class="text-lg sm:text-xl font-serif mb-3 text-gray-900 uppercase font-medium">Eco Presentation</h3>
                                <p class="text-gray-500 text-xs sm:text-sm leading-relaxed font-light">We say NO to single-use plastics. All creations are wrapped elegantly in clean premium linen-paper containers.</p>
                            </div>
                            <div class="bg-white p-8 sm:p-10 rounded-[2rem] sm:rounded-[2.5rem] border border-black/5 shadow-sm">
                                <span class="text-2xl sm:text-3xl font-serif text-[#d4af37] block mb-4">03</span>
                                <h3 class="text-lg sm:text-xl font-serif mb-3 text-gray-900 uppercase font-medium">Direct Atelier Feed</h3>
                                <p class="text-gray-500 text-xs sm:text-sm leading-relaxed font-light">Direct real-time studio coordination on WhatsApp. We share live pictures of the custom setup prior to delivery.</p>
                            </div>
                        </div>
                    </div>
                </section>

                <!-- Customer Appraisals Section -->
                <section class="py-20 px-4 sm:px-6 bg-white border-t border-gray-100 w-full overflow-hidden">
                    <div class="max-w-7xl mx-auto text-center">
                        <span class="text-[9px] sm:text-[10px] uppercase font-bold tracking-[0.3em] text-[#d4af37] block mb-2">Atelier Appraisals</span>
                        <h2 class="text-2xl sm:text-3xl md:text-5xl font-serif text-gray-950 mb-12 sm:mb-16 font-light uppercase tracking-wide">Customer Experiences</h2>
                        <div class="grid grid-cols-1 md:grid-cols-3 gap-6 sm:gap-8 text-left w-full">
                            <div class="p-6 sm:p-8 rounded-[1.75rem] sm:rounded-[2rem] bg-[#fcfbf9] border border-gray-100 shadow-sm">
                                <div class="flex text-amber-500 gap-1 mb-3">
                                    <i data-lucide="star" class="w-3.5 h-3.5 fill-current"></i>
                                    <i data-lucide="star" class="w-3.5 h-3.5 fill-current"></i>
                                    <i data-lucide="star" class="w-3.5 h-3.5 fill-current"></i>
                                    <i data-lucide="star" class="w-3.5 h-3.5 fill-current"></i>
                                    <i data-lucide="star" class="w-3.5 h-3.5 fill-current"></i>
                                </div>
                                <p class="text-gray-600 font-light italic mb-4 sm:mb-5 text-xs sm:text-sm leading-relaxed">"The design was stunningly minimalist. No tacky wraps, just fresh natural lilies encased beautifully in gold paper wraps. Handcrafted elements were obvious."</p>
                                <p class="text-[9px] sm:text-xs font-bold uppercase tracking-widest text-gray-900">Humaira Chowdhury</p>
                            </div>
                            <div class="p-6 sm:p-8 rounded-[1.75rem] sm:rounded-[2rem] bg-[#fcfbf9] border border-gray-100 shadow-sm">
                                <div class="flex text-amber-500 gap-1 mb-3">
                                    <i data-lucide="star" class="w-3.5 h-3.5 fill-current"></i>
                                    <i data-lucide="star" class="w-3.5 h-3.5 fill-current"></i>
                                    <i data-lucide="star" class="w-3.5 h-3.5 fill-current"></i>
                                    <i data-lucide="star" class="w-3.5 h-3.5 fill-current"></i>
                                    <i data-lucide="star" class="w-3.5 h-3.5 fill-current"></i>
                                </div>
                                <p class="text-gray-600 font-light italic mb-4 sm:mb-5 text-xs sm:text-sm leading-relaxed">"Requested a bespoke money arrangement combo. The designers mapped it accurately, kept constant communication, and delivered inside Dhaka flawlessly."</p>
                                <p class="text-[9px] sm:text-xs font-bold uppercase tracking-widest text-gray-900">Arifur Rahman</p>
                            </div>
                            <div class="p-6 sm:p-8 rounded-[1.75rem] sm:rounded-[2rem] bg-[#fcfbf9] border border-gray-100 shadow-sm">
                                <div class="flex text-amber-500 gap-1 mb-3">
                                    <i data-lucide="star" class="w-3.5 h-3.5 fill-current"></i>
                                    <i data-lucide="star" class="w-3.5 h-3.5 fill-current"></i>
                                    <i data-lucide="star" class="w-3.5 h-3.5 fill-current"></i>
                                    <i data-lucide="star" class="w-3.5 h-3.5 fill-current"></i>
                                    <i data-lucide="star" class="w-3.5 h-3.5 fill-current"></i>
                                </div>
                                <p class="text-gray-600 font-light italic mb-4 sm:mb-5 text-xs sm:text-sm leading-relaxed">"No annoying checkout clicks, just clicked 'Order on WhatsApp' and spoke directly to their visual florists. Unbelievably smooth and highly recommended!"</p>
                                <p class="text-[9px] sm:text-xs font-bold uppercase tracking-widest text-gray-900">Naila Tasnim</p>
                            </div>
                        </div>
                    </div>
                </section>

                <!-- FAQs Section -->
                <section id="faq" class="py-20 px-4 sm:px-6 bg-stone-50 border-t border-gray-100 w-full overflow-hidden">
                    <div class="max-w-4xl mx-auto">
                        <div class="text-center mb-12">
                            <span class="text-[9px] sm:text-[10px] uppercase font-bold tracking-[0.3em] text-[#d4af37] block mb-2">Common Queries</span>
                            <h2 class="text-2xl sm:text-3xl md:text-5xl font-serif text-gray-950 font-light uppercase tracking-wide">Frequently Asked</h2>
                        </div>
                        <div class="space-y-4 w-full">
                            <div class="bg-white rounded-2xl border border-gray-100 overflow-hidden shadow-sm">
                                <button onclick="toggleFaqAccordion(this)" class="w-full flex justify-between items-center px-6 sm:px-8 py-5 text-left focus:outline-none">
                                    <span class="font-serif text-sm sm:text-lg text-gray-950 font-medium">How do I purchase an artwork?</span>
                                    <i data-lucide="chevron-down" class="w-4 h-4 text-gray-400 transition-transform duration-300 accordion-icon shrink-0 ml-2"></i>
                                </button>
                                <div class="px-6 sm:px-8 pb-5 text-gray-500 font-light text-xs sm:text-sm leading-relaxed hidden">
                                    Simply browse through our collections, choose your perfect piece, and tap "Order on WhatsApp". It opens up a direct secure link with our visual florists to finalize delivery slots and customized stems.
                                </div>
                            </div>
                            <div class="bg-white rounded-2xl border border-gray-100 overflow-hidden shadow-sm">
                                <button onclick="toggleFaqAccordion(this)" class="w-full flex justify-between items-center px-6 sm:px-8 py-5 text-left focus:outline-none">
                                    <span class="font-serif text-sm sm:text-lg text-gray-950 font-medium">Why do you not state item prices?</span>
                                    <i data-lucide="chevron-down" class="w-4 h-4 text-gray-400 transition-transform duration-300 accordion-icon shrink-0 ml-2"></i>
                                </button>
                                <div class="px-6 sm:px-8 pb-5 text-gray-500 font-light text-xs sm:text-sm leading-relaxed hidden">
                                    Our visual works are entirely organic. Stems and flowers rates adjust daily according to imports. Moreover, we allow complete bespoke scaling of any design which alters pricing dynamically.
                                </div>
                            </div>
                            <div class="bg-white rounded-2xl border border-gray-100 overflow-hidden shadow-sm">
                                <button onclick="toggleFaqAccordion(this)" class="w-full flex justify-between items-center px-6 sm:px-8 py-5 text-left focus:outline-none">
                                    <span class="font-serif text-sm sm:text-lg text-gray-950 font-medium">What is your delivery coverage?</span>
                                    <i data-lucide="chevron-down" class="w-4 h-4 text-gray-400 transition-transform duration-300 accordion-icon shrink-0 ml-2"></i>
                                </button>
                                <div class="px-6 sm:px-8 pb-5 text-gray-500 font-light text-xs sm:text-sm leading-relaxed hidden">
                                    We cover entire Dhaka city with secure, temperature-controlled delivery vans to ensure no petals lose their scent or structural beauty during transportation.
                                </div>
                            </div>
                        </div>
                    </div>
                </section>

                <!-- Contact Section -->
                <section id="contact" class="bg-[#111111] text-white py-20 px-4 sm:px-6 relative overflow-hidden border-t border-gray-800 w-full">
                    <div class="max-w-4xl mx-auto text-center relative z-10 w-full">
                        <span class="inline-block border border-white/10 bg-white/5 py-1.5 px-4 rounded-full text-[#d4af37] text-[8px] sm:text-[9px] font-bold uppercase tracking-[0.25em] mb-5">
                            Direct Atelier Access
                        </span>
                        <h2 class="text-2xl sm:text-3xl md:text-5xl font-serif text-white mb-5 font-light uppercase tracking-wide leading-tight">Bespoke Floral Commissioning</h2>
                        <p class="text-gray-400 font-light max-w-xl mx-auto mb-10 leading-relaxed text-xs sm:text-sm">
                            Request direct customization of any seasonal cuts. Connect with our principal florists instantly.
                        </p>
                        <div class="flex flex-col sm:flex-row justify-center items-center gap-3 w-full">
                            <a href="https://wa.me/${formatWhatsApp(state.settings.whatsapp)}" target="_blank" rel="noreferrer" class="w-full sm:w-auto premium-btn-gold text-white px-8 py-4 rounded-full text-[10px] uppercase tracking-widest font-bold flex items-center justify-center gap-2.5">
                                <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946C.06 5.348 5.397.01 12.008.01c3.202.001 6.212 1.246 8.477 3.514 2.266 2.268 3.507 5.28 3.505 8.484-.004 6.657-5.34 11.997-11.953 11.997-2.005-.001-3.973-.502-5.713-1.455L0 24zm6.59-4.846c1.6.95 3.188 1.449 4.625 1.451 5.436 0 9.851-4.398 9.854-9.807.001-2.621-1.013-5.086-2.86-6.935C16.36 1.913 13.9.894 11.285.894c-5.438 0-9.854 4.398-9.858 9.808 0 2.037.533 4.024 1.547 5.765l-.99 3.613 3.73-.973h.001a9.78 9.78 0 0 0 4.332 1.048z"/></svg> WhatsApp Studio
                            </a>
                            <a href="tel:${state.settings.phone}" class="w-full sm:w-auto bg-transparent border border-white/20 text-white px-8 py-4 rounded-full text-[10px] uppercase tracking-widest font-semibold hover:bg-white/5 transition-all flex items-center justify-center gap-2.5">
                                <i data-lucide="phone" class="w-4 h-4"></i> Call Atelier
                            </a>
                        </div>
                    </div>
                </section>

                <!-- Footer with Secret 4-Tap Access Tracker -->
                <footer class="bg-black text-white pt-16 pb-10 px-4 sm:px-6 w-full overflow-hidden border-t border-white/5">
                    <div class="max-w-7xl mx-auto grid grid-cols-1 md:grid-cols-4 gap-10 text-center md:text-left mb-12 w-full">
                        <div class="md:col-span-2 space-y-4">
                            <div class="flex items-center gap-2.5 justify-center md:justify-start">
                                <img src="${state.settings.logo || 'IMG_1382.png'}" onerror="this.src='IMG_1382.png'" class="w-12 h-12 rounded-full object-cover border border-white/10" alt="" />
                                <span class="font-serif text-xl tracking-[0.1em] text-white uppercase font-light">TATKA-FUL</span>
                            </div>
                            <p class="text-gray-400 font-light text-xs sm:text-sm leading-relaxed max-w-sm mx-auto md:mx-0">
                                Minimalist luxury floral architecture. Designing pure and memorable botanical arrangements for beautiful visual statements.
                            </p>
                        </div>
                        <div>
                            <p class="text-[10px] font-bold uppercase tracking-[0.2em] text-[#d4af37] mb-4">Contact Studio</p>
                            <ul class="space-y-2.5 text-xs sm:text-sm font-light text-gray-400">
                                <li>WhatsApp: ${state.settings.whatsapp}</li>
                                <li>Direct: ${state.settings.phone}</li>
                                <li>Dhaka, Bangladesh</li>
                            </ul>
                        </div>
                        <div>
                            <p class="text-[10px] font-bold uppercase tracking-[0.2em] text-[#d4af37] mb-4">Social Portfolios</p>
                            <div class="flex justify-center md:justify-start gap-3.5">
                                <!-- Instagram Logo (100% stable inline SVG) -->
                                <a href="${state.settings.instagram}" target="_blank" rel="noreferrer" class="w-9 h-9 rounded-full bg-white/5 hover:bg-white/10 flex items-center justify-center text-gray-300 hover:text-white transition-all">
                                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="2" xmlns="http://www.w3.org/2000/svg">
                                        <rect x="2" y="2" width="20" height="20" rx="5" ry="5"></rect>
                                        <path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"></path>
                                        <line x1="17.5" y1="6.5" x2="17.51" y2="6.5"></line>
                                    </svg>
                                </a>
                                <!-- TikTok Logo (100% stable inline SVG) -->
                                <a href="${state.settings.tiktok}" target="_blank" rel="noreferrer" class="w-9 h-9 rounded-full bg-white/5 hover:bg-white/10 flex items-center justify-center text-gray-300 hover:text-white transition-all">
                                    <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                                        <path d="M12.525.02c1.31-.02 2.61-.01 3.91-.02.08 1.53.63 3.02 1.63 4.14 1.12 1.21 2.67 1.97 4.29 2.2v3.7c-1.89-.03-3.7-.63-5.22-1.74-.14-.1-.28-.2-.41-.31v7.65c.06 1.76-.45 3.51-1.48 4.93-1.42 1.94-3.79 3.12-6.22 3.12-3.13 0-5.99-1.99-7.07-4.93-1.22-3.23-.27-7.04 2.45-9.15 1.58-1.24 3.63-1.8 5.66-1.57v3.78c-1.12-.22-2.31.06-3.19.82-.94.79-1.39 2.05-1.14 3.24.28 1.41 1.52 2.47 2.97 2.47 1.64.01 3.04-1.27 3.12-2.91.01-.46 0-.91.01-1.37V.02z"/>
                                    </svg>
                                </a>
                                <!-- Facebook Logo (100% stable inline SVG) -->
                                <a href="${state.settings.facebook}" target="_blank" rel="noreferrer" class="w-9 h-9 rounded-full bg-white/5 hover:bg-white/10 flex items-center justify-center text-gray-300 hover:text-white transition-all">
                                    <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                                        <path d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"/>
                                    </svg>
                                </a>
                            </div>
                        </div>
                    </div>
                    <div class="max-w-7xl mx-auto pt-6 border-t border-white/5 text-center">
                        <p onclick="handleSecretClick()" id="secret-trigger" class="text-[9px] sm:text-[10px] font-semibold tracking-[0.2em] uppercase text-gray-500 cursor-default select-none hover:text-white transition-colors" title="Tap 4 times sequentially to open Studio Workspace Management">
                            &copy; 2026 TATKA-FUL. Designed with passion & elegance.
                        </p>
                    </div>
                </footer>

                <!-- Floating Sticky WhatsApp Utility (Mobile friendly size) -->
                <div class="fixed bottom-6 right-6 z-40">
                    <a href="https://wa.me/${formatWhatsApp(state.settings.whatsapp)}" target="_blank" rel="noreferrer" class="relative w-14 h-14 bg-[#25D366] text-white rounded-full flex items-center justify-center hover:scale-105 transition-transform shadow-[0_10px_25px_rgba(37,211,102,0.35)]">
                        <span class="absolute inline-flex h-full w-full rounded-full bg-[#25D366] opacity-45 animate-ping"></span>
                        <svg class="w-6 h-6 relative z-10" fill="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946C.06 5.348 5.397.01 12.008.01c3.202.001 6.212 1.246 8.477 3.514 2.266 2.268 3.507 5.28 3.505 8.484-.004 6.657-5.34 11.997-11.953 11.997-2.005-.001-3.973-.502-5.713-1.455L0 24zm6.59-4.846c1.6.95 3.188 1.449 4.625 1.451 5.436 0 9.851-4.398 9.854-9.807.001-2.621-1.013-5.086-2.86-6.935C16.36 1.913 13.9.894 11.285.894c-5.438 0-9.854 4.398-9.858 9.808 0 2.037.533 4.024 1.547 5.765l-.99 3.613 3.73-.973h.001a9.78 9.78 0 0 0 4.332 1.048z"/></svg>
                    </a>
                </div>

                <!-- Product Details Canvas Modal Placement Container -->
                <div id="modal-wrapper"></div>
            `;

            // Active listener to dynamic search inputs
            const searchInput = document.getElementById('live-search-input');
            if (searchInput) {
                searchInput.oninput = (e) => {
                    state.searchQuery = e.target.value;
                    debounceSearch();
                };
            }

            // Render detail modal overlay if active bouquet state exists
            if (state.selectedBouquet) {
                renderDetailModal();
            }
        }

        function renderDetailModal() {
            const b = state.selectedBouquet;
            const container = document.getElementById('modal-wrapper');
            if (!container) return;

            // Related listings matching current category (excluding self, active displays only)
            const related = state.bouquets.filter(item => item.category === b.category && item.id !== b.id && item.visible !== false).slice(0, 3);

            container.innerHTML = `
                <div class="fixed inset-0 z-50 flex items-center justify-center p-0 sm:p-4 md:p-8">
                    <!-- Overlay blurred container -->
                    <div class="absolute inset-0 bg-black/75 backdrop-blur-md transition-opacity animate-fade-in" onclick="closeDetailModal()"></div>
                    
                    <!-- Main dynamic window viewport -->
                    <div class="relative bg-[#fcfbf9] w-full h-full md:h-auto md:max-h-[92vh] md:max-w-6xl md:rounded-[2.5rem] shadow-2xl overflow-y-auto flex flex-col animate-fade-up z-10">
                        
                        <!-- Tap to close icon -->
                        <button onclick="closeDetailModal()" class="absolute top-4 right-4 sm:top-6 sm:right-6 z-20 w-10 h-10 sm:w-12 sm:h-12 bg-white/90 backdrop-blur-md rounded-full flex items-center justify-center text-gray-900 hover:bg-gray-100 transition-colors shadow-lg">
                            <i data-lucide="x" class="w-5 h-5"></i>
                        </button>

                        <div class="flex flex-col lg:flex-row flex-grow w-full">
                            <!-- Visual Gallery Panel (Carousel) -->
                            <div class="w-full lg:w-1/2 bg-white h-[40vh] sm:h-[45vh] lg:h-auto min-h-[30vh] sm:min-h-[40vh] relative border-b lg:border-b-0 lg:border-r border-gray-100 flex flex-col justify-between">
                                <div class="w-full h-full relative overflow-hidden flex items-center justify-center">
                                    <img id="detail-active-img" src="${b.images[state.activeDetailImageIndex] || 'IMG_1382.png'}" onerror="this.src='IMG_1382.png'" alt="${b.name}" class="w-full h-full object-cover transition-all duration-500" />
                                </div>
                                
                                <!-- Multi-image Bullet indicators / Thumbnails -->
                                ${b.images && b.images.length > 1 ? `
                                    <div class="absolute bottom-4 left-0 right-0 flex justify-center gap-1.5 px-4">
                                        <div class="flex gap-1.5 p-1.5 bg-black/25 backdrop-blur-md rounded-full">
                                            ${b.images.map((img, idx) => `
                                                <button onclick="setDetailImage(${idx})" class="w-2 h-2 rounded-full transition-all ${idx === state.activeDetailImageIndex ? 'bg-white scale-110' : 'bg-white/40 hover:bg-white/75'}"></button>
                                            `).join('')}
                                        </div>
                                    </div>
                                ` : ''}
                            </div>

                            <!-- Structural Detailed Metadata Info Panel -->
                            <div class="w-full lg:w-1/2 p-6 sm:p-8 md:p-14 flex flex-col bg-white justify-between">
                                <div class="w-full">
                                    <span class="text-[9px] sm:text-[10px] font-bold tracking-[0.3em] text-[#064e3b] uppercase mb-3 sm:mb-4 block">${b.category}</span>
                                    <h2 class="text-2xl sm:text-3xl md:text-4xl font-serif text-gray-950 mb-4 sm:mb-6 leading-tight font-light uppercase tracking-wide">${b.name}</h2>
                                    <div class="w-12 h-[2px] bg-[#d4af37] mb-6"></div>
                                    <p class="text-gray-600 leading-relaxed mb-6 sm:mb-8 font-light text-xs sm:text-base">${b.description}</p>
                                    
                                    <div class="space-y-4 mb-8">
                                        <!-- Custom flowers used specs -->
                                        <div class="bg-[#f0f2ee] p-4 sm:p-5 rounded-2xl border border-black/5 w-full">
                                            <h4 class="text-[9px] sm:text-[10px] font-bold uppercase tracking-wider text-gray-900 mb-1 flex items-center gap-2">
                                                <i data-lucide="flower" class="w-3.5 h-3.5 text-[#064e3b]"></i> Flowers Used
                                            </h4>
                                            <p class="text-gray-600 text-xs font-light leading-relaxed">${b.flowersUsed || 'Premium handpicked organic stems wrapped carefully with matching visual botanical elements.'}</p>
                                        </div>
                                        <!-- Custom secure shipping information specs -->
                                        <div class="bg-[#fcfbf9] p-4 sm:p-5 rounded-2xl border border-gray-100 w-full">
                                            <h4 class="text-[9px] sm:text-[10px] font-bold uppercase tracking-wider text-[#d4af37] mb-1 flex items-center gap-2">
                                                <i data-lucide="truck" class="w-3.5 h-3.5 text-[#d4af37]"></i> Delivery Information
                                            </h4>
                                            <p class="text-gray-500 text-xs font-light leading-relaxed">${b.deliveryInfo || 'Bespoke delivery transport across Dhaka City to protect visual setup and freshness.'}</p>
                                        </div>
                                    </div>
                                </div>

                                <div class="w-full">
                                    <button onclick="triggerWhatsAppOrder(null, '${b.name}')" class="w-full premium-btn-gold text-white py-3.5 sm:py-4.5 rounded-full flex items-center justify-center gap-2.5 text-[10px] sm:text-xs font-bold uppercase tracking-widest shadow-xl shadow-amber-500/10">
                                        <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946C.06 5.348 5.397.01 12.008.01c3.202.001 6.212 1.246 8.477 3.514 2.266 2.268 3.507 5.28 3.505 8.484-.004 6.657-5.34 11.997-11.953 11.997-2.005-.001-3.973-.502-5.713-1.455L0 24zm6.59-4.846c1.6.95 3.188 1.449 4.625 1.451 5.436 0 9.851-4.398 9.854-9.807.001-2.621-1.013-5.086-2.86-6.935C16.36 1.913 13.9.894 11.285.894c-5.438 0-9.854 4.398-9.858 9.808 0 2.037.533 4.024 1.547 5.765l-.99 3.613 3.73-.973h.001a9.78 9.78 0 0 0 4.332 1.048z"/></svg> Order on WhatsApp
                                    </button>
                                </div>
                            </div>
                        </div>

                        <!-- Horizontal related list container -->
                        ${related.length > 0 ? `
                            <div class="bg-stone-50 p-6 sm:p-8 md:p-12 border-t border-gray-100 w-full">
                                <h4 class="text-[10px] font-bold uppercase tracking-[0.25em] text-[#d4af37] mb-5">Related Masterpieces</h4>
                                <div class="grid grid-cols-2 sm:grid-cols-3 gap-3 sm:gap-6 w-full">
                                    ${related.map(item => `
                                        <div class="bg-white p-3 rounded-2xl border border-gray-100 shadow-sm hover:shadow-md transition-all cursor-pointer flex flex-col w-full" onclick="openDetailModal('${item.id}')">
                                            <div class="relative aspect-square rounded-xl overflow-hidden mb-3.5 bg-stone-100 w-full">
                                                <img src="${item.images[0] || 'IMG_1382.png'}" onerror="this.src='IMG_1382.png'" class="w-full h-full object-cover" />
                                            </div>
                                            <div class="flex-grow flex flex-col justify-between">
                                                <div>
                                                    <h5 class="text-xs sm:text-base font-serif text-gray-900 font-semibold mb-1 uppercase tracking-wide leading-tight">${item.name}</h5>
                                                    <p class="text-gray-400 text-[10px] font-light line-clamp-1 mb-3">${item.description}</p>
                                                </div>
                                                <span class="text-[9px] font-bold uppercase tracking-wider text-[#064e3b] inline-flex items-center gap-1">Examine <i data-lucide="arrow-right" class="w-3 h-3"></i></span>
                                            </div>
                                        </div>
                                    `).join('')}
                                </div>
                            </div>
                        ` : ''}

                    </div>
                </div>
            `;
            // Refresh lucide icons inside dynamic details content
            lucide.createIcons();
        }

        // ==========================================
        // ADMIN PANEL ARCHITECTURE
        // ==========================================
        function renderAdminLogin(container) {
            container.innerHTML = `
                <div class="min-h-screen bg-[#fcfbf9] flex items-center justify-center px-4 py-12 w-full">
                    <div class="bg-white p-6 sm:p-10 md:p-14 rounded-[2.5rem] sm:rounded-[3rem] shadow-xl w-full max-w-md border border-gray-100 animate-fade-up">
                        <div class="flex justify-center mb-6">
                            <div class="w-16 h-16 sm:w-20 sm:h-20 rounded-full overflow-hidden shadow-sm border border-gray-200">
                                <img src="${state.settings.logo || 'IMG_1382.png'}" onerror="this.src='IMG_1382.png'" alt="Brand Logo" class="w-full h-full object-cover" />
                            </div>
                        </div>
                        <h2 class="text-2xl sm:text-3xl font-serif text-center text-gray-900 mb-1 font-semibold">Studio Atelier</h2>
                        <p class="text-center text-gray-400 mb-6 sm:mb-8 text-[9px] font-bold tracking-[0.3em] uppercase">Authorized Studio Operations</p>
                        
                        <form id="login-form" class="space-y-5 sm:space-y-6 w-full">
                            <div>
                                <input id="passcode-input" type="password" placeholder="Passcode" required class="w-full px-5 py-3.5 bg-gray-50 border border-gray-200 rounded-xl focus:outline-none focus:border-[#064e3b] transition-all text-center tracking-[0.4em] text-base sm:text-lg font-bold uppercase" />
                                <p id="login-error" class="text-red-500 text-xs mt-2.5 text-center font-semibold hidden"></p>
                            </div>
                            <button type="submit" class="w-full premium-btn-gold text-white py-3.5 sm:py-4.5 rounded-xl font-bold uppercase tracking-[0.2em] text-[11px] sm:text-xs shadow-lg">
                                Unlock Panel
                            </button>
                            <button type="button" onclick="state.currentView='home'; updateView();" class="w-full mt-2 text-gray-400 hover:text-gray-900 py-1 text-[10px] transition-colors flex items-center justify-center gap-2 font-bold uppercase tracking-widest">
                                <i data-lucide="arrow-left" class="w-3.5 h-3.5"></i> Back to Website
                            </button>
                        </form>
                    </div>
                </div>
            `;

            document.getElementById('login-form').onsubmit = (e) => {
                e.preventDefault();
                const input = document.getElementById('passcode-input').value;
                const errorEl = document.getElementById('login-error');
                if (input === 'gym') {
                    state.currentView = 'admin_dashboard';
                    updateView();
                    showToast("Workspace Unlocked.");
                } else {
                    errorEl.textContent = 'Invalid Passcode';
                    errorEl.classList.remove('hidden');
                }
            };
        }

        function renderAdminDashboard(container) {
            container.innerHTML = `
                <div class="min-h-screen bg-[#fcfbf9] flex flex-col md:flex-row font-sans text-gray-800 w-full overflow-x-hidden">
                    
                    <!-- Sidebar menu panel (Strict responsive sizing constraints) -->
                    <aside class="w-full md:w-80 bg-white border-b md:border-b-0 md:border-r border-gray-100 flex flex-col justify-between shrink-0 z-10 shadow-sm p-4 sm:p-6">
                        <div class="space-y-6 sm:space-y-8">
                            <div class="flex items-center gap-3 sm:gap-4 py-2 sm:py-4 border-b border-gray-50">
                                <div class="w-10 h-10 sm:w-12 sm:h-12 rounded-full overflow-hidden border border-gray-200">
                                    <img src="${state.settings.logo || 'IMG_1382.png'}" onerror="this.src='IMG_1382.png'" class="w-full h-full object-cover" />
                                </div>
                                <div>
                                    <span class="font-serif text-lg sm:text-xl text-gray-950 font-semibold block">TATKA-FUL</span>
                                    <span class="text-[9px] uppercase tracking-widest text-gray-400 font-bold">Studio Dashboard</span>
                                </div>
                            </div>
                            <div class="flex flex-row md:flex-col gap-1.5 sm:gap-2 overflow-x-auto scrollbar-hide pb-2 md:pb-0">
                                <button onclick="setAdminTab('bouquets')" class="flex items-center gap-3 px-4 py-3 rounded-xl transition-all font-semibold text-[10px] sm:text-xs uppercase tracking-wider shrink-0 whitespace-nowrap ${state.adminTab === 'bouquets' ? 'bg-[#111111] text-white shadow-md' : 'text-gray-500 hover:bg-gray-50 hover:text-gray-900'}">
                                    <i data-lucide="package" class="w-4 h-4"></i> Masterpieces
                                </button>
                                <button onclick="setAdminTab('settings')" class="flex items-center gap-3 px-4 py-3 rounded-xl transition-all font-semibold text-[10px] sm:text-xs uppercase tracking-wider shrink-0 whitespace-nowrap ${state.adminTab === 'settings' ? 'bg-[#111111] text-white shadow-md' : 'text-gray-500 hover:bg-gray-50 hover:text-gray-900'}">
                                    <i data-lucide="settings" class="w-4 h-4"></i> Brand Settings
                                </button>
                            </div>
                        </div>
                        <div class="pt-4 sm:pt-6 border-t border-gray-50 mt-4 md:mt-0">
                            <button onclick="state.currentView='home'; updateView();" class="w-full flex items-center justify-center gap-2.5 px-4 py-3.5 rounded-xl bg-gray-50 hover:bg-red-50 text-gray-600 hover:text-red-600 transition-all font-bold text-[10px] sm:text-xs uppercase tracking-widest">
                                <i data-lucide="log-out" class="w-3.5 h-3.5"></i> Lock Atelier
                            </button>
                        </div>
                    </aside>

                    <!-- Core Active Workspace Area (Wrapped with responsive overflow protections) -->
                    <main id="admin-main-area" class="flex-1 p-4 sm:p-6 md:p-12 overflow-y-auto overflow-x-hidden max-w-full">
                        <!-- Filled dynamically -->
                    </main>
                </div>
            `;

            renderAdminMainSection();
        }

        function setAdminTab(tab) {
            state.adminTab = tab;
            state.isAddingBouquet = false;
            state.editingId = null;
            renderAdminMainSection();
        }

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
            lucide.createIcons();
        }

        function renderBouquetList(container) {
            container.innerHTML = `
                <div class="animate-fade-up max-w-6xl mx-auto w-full overflow-hidden">
                    <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center mb-8 gap-4 w-full">
                        <div>
                            <h1 class="text-2xl sm:text-3xl font-serif text-gray-950 font-medium mb-1">Catalog Management</h1>
                            <p class="text-gray-500 text-xs font-light">Add, update, or unpublish your bespoke works dynamically.</p>
                        </div>
                        <button onclick="openNewBouquetForm()" class="premium-btn-gold text-white px-6 py-3 rounded-full flex items-center gap-2.5 font-bold uppercase tracking-widest text-[10px] sm:text-xs shadow-lg shrink-0">
                            <i data-lucide="plus" class="w-3.5 h-3.5"></i> Add New Design
                        </button>
                    </div>

                    <!-- Inventory Metrics Counters -->
                    <div class="grid grid-cols-1 sm:grid-cols-3 gap-4 sm:gap-6 mb-8 w-full">
                        <div class="bg-white p-6 sm:p-8 rounded-2xl sm:rounded-3xl border border-gray-100 shadow-sm">
                            <p class="text-[8px] sm:text-[9px] text-gray-400 font-bold tracking-[0.2em] uppercase mb-1.5">Total Masterpieces</p>
                            <p class="text-3xl sm:text-4xl font-serif text-gray-950">${state.bouquets.length}</p>
                        </div>
                        <div class="bg-white p-6 sm:p-8 rounded-2xl sm:rounded-3xl border border-gray-100 shadow-sm">
                            <p class="text-[8px] sm:text-[9px] text-emerald-900 font-bold tracking-[0.2em] uppercase mb-1.5">Active Display</p>
                            <p class="text-3xl sm:text-4xl font-serif text-emerald-900">${state.bouquets.filter(b => b.visible).length}</p>
                        </div>
                        <div class="bg-white p-6 sm:p-8 rounded-2xl sm:rounded-3xl border border-gray-100 shadow-sm">
                            <p class="text-[8px] sm:text-[9px] text-[#b8860b] font-bold tracking-[0.2em] uppercase mb-1.5">Signature Masterworks</p>
                            <p class="text-3xl sm:text-4xl font-serif text-[#b8860b]">${state.bouquets.filter(b => b.bestseller).length}</p>
                        </div>
                    </div>

                    <!-- Catalog Datatable with Strict Overflow Protection for Mobile -->
                    <div class="bg-white border border-gray-100 rounded-2xl sm:rounded-3xl shadow-sm w-full overflow-hidden">
                        <div class="w-full overflow-x-auto scrollbar-hide">
                            <table class="w-full text-left border-collapse min-w-[600px]">
                                <thead>
                                    <tr class="border-b border-gray-100 bg-gray-50/50">
                                        <th class="p-5 text-[9px] sm:text-[10px] font-bold text-gray-400 uppercase tracking-[0.2em]">Floral Design</th>
                                        <th class="p-5 text-[9px] sm:text-[10px] font-bold text-gray-400 uppercase tracking-[0.2em]">Category</th>
                                        <th class="p-5 text-[9px] sm:text-[10px] font-bold text-gray-400 uppercase tracking-[0.2em] text-center">Active Display</th>
                                        <th class="p-5 text-[9px] sm:text-[10px] font-bold text-gray-400 uppercase tracking-[0.2em] text-right">Actions</th>
                                    </tr>
                                </thead>
                                <tbody class="divide-y divide-gray-50 text-sm">
                                    ${state.bouquets.length === 0 ? `
                                        <tr>
                                            <td colSpan="4" class="p-10 text-center text-gray-400 font-light text-sm sm:text-base">Your design portfolio is currently empty. Click "Add New Design" to upload.</td>
                                        </tr>
                                    ` : state.bouquets.map(b => `
                                        <tr class="hover:bg-gray-50/40 transition-colors">
                                            <td class="p-5 flex items-center gap-4">
                                                <div class="w-12 h-12 rounded-xl bg-stone-50 overflow-hidden shrink-0 border border-gray-100">
                                                    <img src="${b.images[0] || 'IMG_1382.png'}" onerror="this.src='IMG_1382.png'" class="w-full h-full object-cover" />
                                                </div>
                                                <div>
                                                    <p class="font-serif text-sm sm:text-base text-gray-950 font-medium uppercase tracking-wide leading-tight">${b.name}</p>
                                                    <div class="flex gap-2 mt-1">
                                                        ${b.bestseller ? `<span class="text-[7px] bg-amber-50 text-[#b8860b] border border-amber-100 px-2 py-0.5 rounded-full font-bold uppercase tracking-widest">Signature</span>` : ''}
                                                        ${b.newArrival ? `<span class="text-[7px] bg-emerald-50 text-emerald-950 border border-emerald-100 px-2 py-0.5 rounded-full font-bold uppercase tracking-widest">Seasonal</span>` : ''}
                                                    </div>
                                                </div>
                                            </td>
                                            <td class="p-5 text-xs text-gray-600 font-semibold">${b.category}</td>
                                            <td class="p-5 text-center">
                                                <button onclick="toggleVisibility('${b.id}')" class="px-4 py-1.5 text-[9px] font-bold uppercase tracking-widest rounded-full border transition-all ${b.visible ? 'text-emerald-900 bg-emerald-50 border-emerald-100 hover:bg-emerald-100' : 'text-gray-400 bg-gray-50 border-gray-100 hover:bg-gray-100'}">
                                                    ${b.visible ? 'Published' : 'Unpublished'}
                                                </button>
                                            </td>
                                            <td class="p-5 text-right space-x-1.5">
                                                <button onclick="editBouquet('${b.id}')" class="p-2 text-gray-400 hover:text-emerald-900 hover:bg-emerald-50 rounded-lg transition-all inline-flex items-center justify-center">
                                                    <i data-lucide="edit" class="w-4 h-4"></i>
                                                </button>
                                                <button onclick="deleteBouquet('${b.id}')" class="p-2 text-gray-400 hover:text-red-600 hover:bg-red-50 rounded-lg transition-all inline-flex items-center justify-center">
                                                    <i data-lucide="trash-2" class="w-4 h-4"></i>
                                                </button>
                                            </td>
                                        </tr>
                                    `).join('')}
                                </tbody>
                            </table>
                        </div>
                    </div>
                </div>
            `;
        }

        function renderBouquetForm(container) {
            container.innerHTML = `
                <div class="animate-fade-up max-w-4xl mx-auto bg-white p-5 sm:p-8 md:p-14 border border-gray-100 rounded-[2rem] sm:rounded-[3rem] shadow-sm w-full">
                    <div class="flex items-center gap-4 sm:gap-6 mb-8 border-b border-gray-100 pb-6">
                        <button onclick="cancelBouquetForm()" class="p-3 bg-gray-50 hover:bg-gray-100 rounded-full text-gray-600 transition-colors">
                            <i data-lucide="arrow-left" class="w-4 h-4"></i>
                        </button>
                        <h2 class="text-xl sm:text-3xl font-serif text-gray-950 font-medium">${state.editingId ? 'Modify Curator Piece' : 'Register Curated Design'}</h2>
                    </div>

                    <form id="bouquet-form" class="space-y-6 sm:space-y-8 w-full">
                        <!-- Multiple base64 gallery framework (Limit 5 max) -->
                        <div class="bg-[#fcfbf9] p-4 sm:p-8 rounded-2xl sm:rounded-[2rem] border border-gray-100 w-full">
                            <label class="block text-[8px] sm:text-[9px] font-bold tracking-[0.2em] text-gray-400 mb-4 uppercase">Curator Gallery Images (Up to 5 images)</label>
                            <div class="grid grid-cols-2 sm:grid-cols-5 gap-3.5 w-full">
                                ${state.formData.images.map((img, idx) => `
                                    <div class="relative aspect-[4/5] rounded-xl overflow-hidden border border-gray-200 group shadow-sm bg-white">
                                        <img src="${img}" class="w-full h-full object-cover" />
                                        <button type="button" onclick="removeFormImage(${idx})" class="absolute inset-0 bg-red-950/70 text-white flex items-center justify-center opacity-0 group-hover:opacity-100 transition-opacity font-bold text-[10px] uppercase tracking-wider backdrop-blur-sm">Remove</button>
                                    </div>
                                `).join('')}
                                ${state.formData.images.length < 5 ? `
                                    <label class="aspect-[4/5] rounded-xl border-2 border-dashed border-gray-200 hover:border-[#064e3b] hover:bg-emerald-50/30 transition-all flex flex-col items-center justify-center cursor-pointer text-gray-400 hover:text-[#064e3b] bg-white">
                                        <i data-lucide="upload-cloud" class="w-6 h-6 sm:w-8 sm:h-8 mb-2"></i>
                                        <span class="text-[8px] sm:text-[9px] font-bold tracking-widest uppercase text-center">${state.isUploading ? 'Scaling...' : 'Add Image'}</span>
                                        <input id="gallery-input" type="file" accept="image/*" multiple class="hidden" />
                                    </label>
                                ` : ''}
                            </div>
                        </div>

                        <!-- Basic fields -->
                        <div class="grid grid-cols-1 md:grid-cols-2 gap-5 sm:gap-8 w-full">
                            <div>
                                <label class="block text-[8px] sm:text-[9px] font-bold tracking-[0.2em] text-gray-400 mb-2 uppercase">Design Name</label>
                                <input required id="form-name" type="text" value="${state.formData.name}" class="w-full px-4 py-3 sm:py-4 bg-gray-50 border border-gray-200 rounded-xl focus:border-emerald-900 focus:bg-white outline-none transition-all font-serif text-sm sm:text-base text-gray-950 uppercase tracking-wide" placeholder="e.g. Crimson Atélier" />
                            </div>
                            <div>
                                <label class="block text-[8px] sm:text-[9px] font-bold tracking-[0.2em] text-gray-400 mb-2 uppercase">Floral Category</label>
                                <select id="form-category" class="w-full px-4 py-3 sm:py-4 bg-gray-50 border border-gray-200 rounded-xl outline-none focus:border-emerald-900 focus:bg-white font-semibold text-xs sm:text-sm text-gray-700">
                                    ${state.categories.map(c => `<option value="${c}" ${state.formData.category === c ? 'selected' : ''}>${c}</option>`).join('')}
                                </select>
                            </div>
                        </div>

                        <div>
                            <label class="block text-[8px] sm:text-[9px] font-bold tracking-[0.2em] text-gray-400 mb-2 uppercase">Design Narrative (Description)</label>
                            <textarea required id="form-desc" rows="4" class="w-full px-4 py-3 sm:py-4 bg-gray-50 border border-gray-200 rounded-xl focus:border-emerald-900 focus:bg-white outline-none transition-all resize-none font-light text-xs sm:text-sm leading-relaxed" placeholder="Write luxury product description details...">${state.formData.description}</textarea>
                        </div>

                        <!-- Bespoke specifications details fields -->
                        <div class="grid grid-cols-1 md:grid-cols-2 gap-5 sm:gap-8 w-full">
                            <div>
                                <label class="block text-[8px] sm:text-[9px] font-bold tracking-[0.2em] text-gray-400 mb-2 uppercase">Flowers Used (Botanical Specs)</label>
                                <input id="form-flowers" type="text" value="${state.formData.flowersUsed || ''}" class="w-full px-4 py-3 sm:py-4 bg-gray-50 border border-gray-200 rounded-xl outline-none focus:border-emerald-900 focus:bg-white font-light text-xs sm:text-sm" placeholder="e.g. 24 Premium Red Roses" />
                            </div>
                            <div>
                                <label class="block text-[8px] sm:text-[9px] font-bold tracking-[0.2em] text-gray-400 mb-2 uppercase">Special Packaging/Delivery Notes</label>
                                <input id="form-delivery" type="text" value="${state.formData.deliveryInfo || ''}" class="w-full px-4 py-3 sm:py-4 bg-gray-50 border border-gray-200 rounded-xl outline-none focus:border-emerald-900 focus:bg-white font-light text-xs sm:text-sm" placeholder="e.g. Transported in protective organic linen boxes." />
                            </div>
                        </div>

                        <!-- Metadata switches toggles -->
                        <div class="flex flex-wrap gap-5 pt-2">
                            <label class="flex items-center gap-2.5 cursor-pointer select-none">
                                <input id="form-bestseller" type="checkbox" ${state.formData.bestseller ? 'checked' : ''} class="w-5 h-5 text-emerald-900 focus:ring-emerald-900 border-gray-300 rounded" />
                                <span class="text-[10px] font-bold tracking-widest text-gray-600 uppercase">Featured Bestseller</span>
                            </label>
                            <label class="flex items-center gap-2.5 cursor-pointer select-none">
                                <input id="form-newarrival" type="checkbox" ${state.formData.newArrival ? 'checked' : ''} class="w-5 h-5 text-emerald-900 focus:ring-emerald-900 border-gray-300 rounded" />
                                <span class="text-[10px] font-bold tracking-widest text-gray-600 uppercase">Seasonal Arrival</span>
                            </label>
                            <label class="flex items-center gap-2.5 cursor-pointer select-none">
                                <input id="form-visible" type="checkbox" ${state.formData.visible ? 'checked' : ''} class="w-5 h-5 text-emerald-900 focus:ring-emerald-900 border-gray-300 rounded" />
                                <span class="text-[10px] font-bold tracking-widest text-gray-600 uppercase">Public visibility</span>
                            </label>
                        </div>

                        <!-- Form actions -->
                        <div class="pt-6 border-t border-gray-100 flex justify-end gap-3">
                            <button type="button" onclick="cancelBouquetForm()" class="px-5 py-3 rounded-full border border-gray-200 text-[10px] font-bold uppercase tracking-widest text-gray-500 hover:bg-gray-50">Cancel</button>
                            <button type="submit" class="premium-btn-gold text-white px-7 py-3 rounded-full text-[10px] font-bold uppercase tracking-widest shadow-lg">
                                ${state.editingId ? 'Apply Modifications' : 'Publish Design'}
                            </button>
                        </div>
                    </form>
                </div>
            `;

            // Setup multi image files handler
            const fileInput = document.getElementById('gallery-input');
            if (fileInput) {
                fileInput.onchange = async (e) => {
                    const files = Array.from(e.target.files);
                    if (!files.length) return;
                    if (state.formData.images.length + files.length > 5) {
                        showToast("Up to 5 images can be loaded.", true);
                        return;
                    }
                    state.isUploading = true;
                    renderAdminMainSection();

                    try {
                        const processed = await Promise.all(files.map(f => compressImage(f, 1000, 0.82)));
                        state.formData.images = [...state.formData.images, ...processed];
                        showToast("Visual assets scaled successfully.");
                    } catch (err) {
                        showToast("Error compressing uploaded images.", true);
                    }

                    state.isUploading = false;
                    renderAdminMainSection();
                };
            }

            // Submit handling logic
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
                    showToast("Atelier design modified.");
                } else {
                    state.bouquets = [{ ...state.formData, id: Date.now().toString() }, ...state.bouquets];
                    showToast("Atelier design registered.");
                }

                await dbSet('tf_bouquets_v3', state.bouquets);
                state.isAddingBouquet = false;
                state.editingId = null;
                renderAdminMainSection();
            };
        }

        function openNewBouquetForm() {
            state.formData = {
                name: '',
                category: state.categories[0],
                description: '',
                flowersUsed: '',
                deliveryInfo: 'Bespoke hand-delivery across Dhaka. Custom requirements require a 24-hour request buffer.',
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

        function editBouquet(id) {
            const b = state.bouquets.find(item => item.id === id);
            if (b) {
                state.formData = { ...b, images: [...b.images] };
                state.editingId = id;
                state.isAddingBouquet = true;
                renderAdminMainSection();
            }
        }

        function deleteBouquet(id) {
            askConfirmation("Permanently delete this curated masterwork from your design workspace registry?", async () => {
                state.bouquets = state.bouquets.filter(b => b.id !== id);
                await dbSet('tf_bouquets_v3', state.bouquets);
                showToast("Portfolio design removed.");
                renderAdminMainSection();
            });
        }

        async function toggleVisibility(id) {
            state.bouquets = state.bouquets.map(b => b.id === id ? { ...b, visible: !b.visible } : b);
            await dbSet('tf_bouquets_v3', state.bouquets);
            showToast("Listing state updated.");
            renderAdminMainSection();
        }

        function renderSettingsPanel(container) {
            container.innerHTML = `
                <div class="animate-fade-up max-w-4xl mx-auto w-full">
                    <div class="mb-8">
                        <h1 class="text-2xl sm:text-3xl font-serif text-gray-900 mb-2">Brand Customization</h1>
                        <p class="text-gray-500 text-xs font-light">Customize your signature slogans, logo headers, and WhatsApp delivery channels.</p>
                    </div>

                    <div class="bg-white p-5 sm:p-8 md:p-14 border border-gray-100 rounded-[2rem] sm:rounded-[3rem] shadow-sm space-y-10 w-full">
                        
                        <!-- Header custom files mapping -->
                        <div class="grid grid-cols-1 md:grid-cols-2 gap-6 w-full">
                            <div class="bg-gray-50 rounded-2xl p-5 text-center border border-gray-100">
                                <p class="text-[9px] font-bold tracking-[0.2em] text-gray-400 uppercase mb-3">Header Logo</p>
                                <div class="w-20 h-20 mx-auto rounded-full bg-white shadow-sm border border-gray-200 mb-4 overflow-hidden flex items-center justify-center">
                                    <img id="logo-preview-img" src="${state.settings.logo || 'IMG_1382.png'}" onerror="this.src='IMG_1382.png'" class="w-full h-full object-cover" />
                                </div>
                                <label class="bg-white px-4 py-2 rounded-full text-[9px] font-bold uppercase tracking-widest border border-gray-200 cursor-pointer hover:bg-gray-100 shadow-sm inline-block">
                                    Change Logo 
                                    <input id="logo-uploader" type="file" accept="image/*" class="hidden" />
                                </label>
                            </div>

                            <div class="bg-gray-50 rounded-2xl p-5 text-center border border-gray-100">
                                <p class="text-[9px] font-bold tracking-[0.2em] text-gray-400 uppercase mb-3">Hero Visual Banner</p>
                                <div class="w-full h-20 mx-auto rounded-xl bg-white shadow-sm border border-gray-200 mb-4 overflow-hidden flex items-center justify-center">
                                    <img id="banner-preview-img" src="${state.settings.banner || 'IMG_1382.png'}" onerror="this.src='IMG_1382.png'" class="w-full h-full object-cover" />
                                </div>
                                <label class="bg-white px-4 py-2 rounded-full text-[9px] font-bold uppercase tracking-widest border border-gray-200 cursor-pointer hover:bg-gray-100 shadow-sm inline-block">
                                    Change Banner 
                                    <input id="banner-uploader" type="file" accept="image/*" class="hidden" />
                                </label>
                            </div>
                        </div>

                        <!-- Copy details configs -->
                        <form id="settings-form" class="space-y-6 w-full">
                            <div>
                                <h3 class="text-base sm:text-lg font-serif text-gray-900 mb-4 border-b border-gray-50 pb-2 uppercase tracking-wider">Brand Voice</h3>
                                <div class="space-y-4">
                                    <div>
                                        <label class="block text-[9px] font-bold tracking-[0.2em] text-gray-400 mb-2 uppercase">Hero Slogan</label>
                                        <input required id="sett-slogan" type="text" value="${state.settings.heroSlogan}" class="w-full px-4 py-3 bg-gray-50 border border-gray-200 rounded-xl focus:border-emerald-900 focus:bg-white outline-none font-serif text-sm text-gray-950 uppercase tracking-wide" />
                                    </div>
                                    <div>
                                        <label class="block text-[9px] font-bold tracking-[0.2em] text-gray-400 mb-2 uppercase">Narrative Description</label>
                                        <textarea required id="sett-desc" rows="3" class="w-full px-4 py-3 bg-gray-50 border border-gray-200 rounded-xl focus:border-emerald-900 focus:bg-white outline-none font-light text-xs sm:text-sm leading-relaxed">${state.settings.heroDesc}</textarea>
                                    </div>
                                </div>
                            </div>

                            <!-- Integration properties -->
                            <div>
                                <h3 class="text-base sm:text-lg font-serif text-gray-900 mb-4 border-b border-gray-50 pb-2 uppercase tracking-wider">Touch Channels</h3>
                                <div class="grid grid-cols-1 md:grid-cols-2 gap-4 w-full">
                                    <div>
                                        <label class="block text-[9px] font-bold tracking-[0.2em] text-gray-400 mb-2 uppercase">WhatsApp Number</label>
                                        <input required id="sett-whatsapp" type="text" value="${state.settings.whatsapp}" class="w-full px-4 py-3 bg-gray-50 border border-gray-200 rounded-xl outline-none focus:border-emerald-900 focus:bg-white font-bold text-xs sm:text-sm" />
                                    </div>
                                    <div>
                                        <label class="block text-[9px] font-bold tracking-[0.2em] text-gray-400 mb-2 uppercase">Phone Line</label>
                                        <input required id="sett-phone" type="text" value="${state.settings.phone}" class="w-full px-4 py-3 bg-gray-50 border border-gray-200 rounded-xl outline-none focus:border-emerald-900 focus:bg-white font-bold text-xs sm:text-sm" />
                                    </div>
                                    <div class="md:col-span-2">
                                        <label class="block text-[9px] font-bold tracking-[0.2em] text-gray-400 mb-2 uppercase">Instagram Profile URL</label>
                                        <input required id="sett-instagram" type="text" value="${state.settings.instagram}" class="w-full px-4 py-3 bg-gray-50 border border-gray-200 rounded-xl outline-none focus:border-emerald-900 focus:bg-white font-light text-xs sm:text-sm" />
                                    </div>
                                    <div class="md:col-span-2">
                                        <label class="block text-[9px] font-bold tracking-[0.2em] text-gray-400 mb-2 uppercase">TikTok Profile URL</label>
                                        <input required id="sett-tiktok" type="text" value="${state.settings.tiktok}" class="w-full px-4 py-3 bg-gray-50 border border-gray-200 rounded-xl outline-none focus:border-emerald-900 focus:bg-white font-light text-xs sm:text-sm" />
                                    </div>
                                    <div class="md:col-span-2">
                                        <label class="block text-[9px] font-bold tracking-[0.2em] text-gray-400 mb-2 uppercase">Facebook Page URL</label>
                                        <input required id="sett-facebook" type="text" value="${state.settings.facebook}" class="w-full px-4 py-3 bg-gray-50 border border-gray-200 rounded-xl outline-none focus:border-emerald-900 focus:bg-white font-light text-xs sm:text-sm" />
                                    </div>
                                </div>
                            </div>

                            <div class="pt-6 border-t border-gray-100 flex justify-end">
                                <button type="submit" class="premium-btn-gold text-white px-8 py-3 rounded-full text-[10px] font-bold uppercase tracking-widest shadow-lg">
                                    Save Configurations
                                </button>
                            </div>
                        </form>
                    </div>
                </div>
            `;

            // Handle direct config updates
            document.getElementById('logo-uploader').onchange = async (e) => {
                const file = e.target.files[0];
                if (!file) return;
                try {
                    const compressed = await compressImage(file, 400, 0.9);
                    state.settings.logo = compressed;
                    document.getElementById('logo-preview-img').src = compressed;
                    await dbSet('tf_settings_v3', state.settings);
                    showToast("Brand logo customized successfully.");
                } catch (err) {
                    showToast("Error processing logo asset.", true);
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
                    showToast("Banner customized successfully.");
                } catch (err) {
                    showToast("Error processing banner asset.", true);
                }
            };

            document.getElementById('settings-form').onsubmit = async (e) => {
                e.preventDefault();
                state.settings.heroSlogan = document.getElementById('sett-slogan').value;
                state.settings.heroDesc = document.getElementById('sett-desc').value;
                state.settings.whatsapp = document.getElementById('sett-whatsapp').value;
                state.settings.phone = document.getElementById('sett-phone').value;
                state.settings.instagram = document.getElementById('sett-instagram').value;
                state.settings.tiktok = document.getElementById('sett-tiktok').value;
                state.settings.facebook = document.getElementById('sett-facebook').value;

                await dbSet('tf_settings_v3', state.settings);
                showToast("Configurations saved successfully!");
                updateView();
            };
        }

        async function bootstrap() {
            try {
                const savedBouquets = await dbGet('tf_bouquets_v3');
                const savedCategories = await dbGet('tf_categories_v3');
                const savedSettings = await dbGet('tf_settings_v3');

                if (savedBouquets && savedBouquets.length > 0) {
                    state.bouquets = savedBouquets;
                } else {
                    // Seed initial beautifully-structured luxury catalog pieces using fallback high-res visual IMG_1382.png
                    state.bouquets = [
                        {
                            id: 'demo-1',
                            name: 'Crimson Love Bouquet',
                            category: '🌹 Rose Bouquet',
                            description: 'An outstanding elegant curation of fresh premium crimson red roses, structured with aromatic sprigs and soft visual linen boundaries.',
                            flowersUsed: '24 Premium Red Roses, eucalyptus branches, baby breath highlights',
                            deliveryInfo: 'Protected hand-delivery across Dhaka City. Cold visual blocks included to maintain freshness.',
                            images: ['IMG_1382.png'],
                            bestseller: true,
                            newArrival: true,
                            visible: true
                        },
                        {
                            id: 'demo-2',
                            name: 'Rustic Sunflower Curation',
                            category: '🌻 Sunflower Bouquet',
                            description: 'Fresh organic visual sunshine elements arranged within earthy rustic paper layouts. Delivers instant bright emotional highlights.',
                            flowersUsed: '5 Premium Golden Sunflowers, seasonal green leaves filler, rustic brown paper wraps',
                            deliveryInfo: 'Protected hand-delivery across Dhaka City. Freshness guaranteed.',
                            images: ['IMG_1382.png'],
                            bestseller: false,
                            newArrival: true,
                            visible: true
                        },
                        {
                            id: 'demo-3',
                            name: 'Bespoke Chocolate Bloom',
                            category: '🍫 Chocolate Bouquet',
                            description: 'A luxurious curation where imported rich dark chocolate bites nestle perfectly alongside fresh visual white lilies inside cream-colored structures.',
                            flowersUsed: '12 imported luxury chocolates, 5 white lilies, cream wrap ties',
                            deliveryInfo: 'Climate-controlled transportation across Dhaka City to eliminate heat issues.',
                            images: ['IMG_1382.png'],
                            bestseller: true,
                            newArrival: false,
                            visible: true
                        }
                    ];
                    await dbSet('tf_bouquets_v3', state.bouquets);
                }

                if (savedCategories) {
                    state.categories = Array.from(new Set([...EXCLUSIVE_CATEGORIES, ...savedCategories]));
                }
                if (savedSettings) {
                    state.settings = savedSettings;
                }
            } catch (err) {
                console.error("IndexedDB bootstrap issues, loading state inside clean memory boundaries...", err);
            } finally {
                // Dissolve loader screen seamlessly
                const loader = document.getElementById('loader-screen');
                if (loader) {
                    loader.classList.add('opacity-0', 'pointer-events-none');
                }
                updateView();
            }
        }

        // Initialize App on Page Load
        window.onload = () => {
            bootstrap();
        };
    </script>
</body>
</html>
