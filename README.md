
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tatka Ful | Premium Floral Concepts</title>
    <!-- Tailwind CSS Engine -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        serif: ['Playfair Display', 'serif'],
                        sans: ['Plus Jakarta Sans', 'sans-serif'],
                    }
                }
            }
        }
    </script>
    <!-- Google Fonts Import for Luxury Appeal -->
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,500;0,600;0,700;1,400&family=Plus+Jakarta+Sans:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    
    <!-- Custom CSS Variables and Glassmorphism Styles -->
    <style>
        :root {
            --emerald-dark: #022c22;
            --emerald-main: #064e3b;
            --emerald-light: #ecfdf5;
            --gold-accent: #d4af37;
            --bg-pearl: #fcfbf9;
        }

        body {
            background-color: var(--bg-pearl);
            font-family: 'Plus Jakarta Sans', sans-serif;
            overflow-x: hidden;
        }

        .glass-header {
            background: rgba(252, 251, 249, 0.85);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border-bottom: 1px solid rgba(0, 0, 0, 0.03);
        }

        .luxury-card {
            background: #ffffff;
            border: 1px solid rgba(0, 0, 0, 0.04);
            box-shadow: 0 15px 35px -10px rgba(0, 0, 0, 0.04);
            transition: all 0.5s cubic-bezier(0.16, 1, 0.3, 1);
        }

        .luxury-card:hover {
            box-shadow: 0 30px 60px -15px rgba(6, 78, 59, 0.08);
            transform: translateY(-6px);
        }

        .premium-btn {
            background: linear-gradient(135deg, var(--emerald-dark) 0%, var(--emerald-main) 100%);
            box-shadow: 0 10px 20px -5px rgba(6, 78, 59, 0.25);
            transition: all 0.3s cubic-bezier(0.16, 1, 0.3, 1);
        }

        .premium-btn:hover {
            box-shadow: 0 15px 30px -5px rgba(6, 78, 59, 0.35);
            transform: translateY(-2px);
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        ::-webkit-scrollbar-track {
            background: transparent;
        }
        ::-webkit-scrollbar-thumb {
            background: rgba(6, 78, 59, 0.2);
            border-radius: 10px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: rgba(6, 78, 59, 0.4);
        }

        /* Hide scrollbar utility */
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
<body class="text-gray-800 antialiased selection:bg-[#064e3b] selection:text-white">

    <!-- ==========================================
         LOADER PAGE (Elegant Custom Welcome Screen)
         ========================================== -->
    <div id="loader-screen" class="fixed inset-0 z-50 bg-[#fcfbf9] flex flex-col items-center justify-center transition-all duration-700">
        <div class="flex flex-col items-center space-y-4">
            <svg class="animate-spin h-10 w-10 text-[#064e3b]" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24">
                <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
                <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
            </svg>
            <h1 class="text-3xl font-serif tracking-wider text-gray-900 animate-pulse">Tatka Ful</h1>
            <p class="text-xs uppercase tracking-[0.2em] text-gray-400 font-semibold">Luxury Floral Design</p>
        </div>
    </div>

    <!-- ==========================================
         MAIN WRAPPER FOR BOTH CUSTOMER & ADMIN VIEWS
         ========================================== -->
    <div id="app-root" class="min-h-screen flex flex-col">
        <!-- Content gets rendered here dynamically using JavaScript -->
    </div>

    <!-- ==========================================
         JAVASCRIPT PERSISTENCE & ARCHITECTURE
         ========================================== -->
    <script>
        // --- 1. INDEXEDDB IMPLEMENTATION (Infinite Local Capacity to prevent 5MB loss) ---
        const DB_NAME = 'TatkaFulPremiumDB';
        const STORE_NAME = 'store';

        function initDB() {
            return new Promise((resolve, reject) => {
                const request = indexedDB.open(DB_NAME, 2);
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

        // --- 2. GLOBAL SYSTEM STATE ---
        let state = {
            currentView: 'home', // 'home' | 'admin_login' | 'admin_dashboard'
            selectedCategory: 'All',
            selectedBouquet: null,
            bouquets: [],
            categories: ['Rose Bouquet', 'Sunflower Bouquet', 'Lily Bouquet', 'Mixed Bouquet', 'Birthday', 'Wedding'],
            settings: {
                logo: 'IMG_0254.png', // Default high-res watercolor logo
                banner: 'IMG_0255.png', // Default horizontal panoramic banner
                phone: '01410619501',
                whatsapp: '01410619501',
                instagram: 'https://instagram.com/tatka_ful',
                tiktok: 'https://tiktok.com/@tatka.ful',
                heroSlogan: 'Elegance in Every Petal.',
                heroDesc: 'Curating luxury floral masterpieces for your most precious memories. Exclusively hand-crafted with passion.'
            },
            adminTab: 'bouquets', // 'bouquets' | 'settings'
            isAddingBouquet: false,
            editingId: null,
            formData: {
                name: '',
                category: '',
                description: '',
                images: [],
                bestseller: false,
                visible: true
            },
            isUploading: false
        };

        // --- 3. HELPER FUNCTIONS ---
        function formatWhatsApp(number) {
            let formatted = number.replace(/[^0-9]/g, '');
            if (formatted.startsWith('0')) formatted = '88' + formatted;
            return formatted;
        }

        // High Fidelity Canvas Image Compression
        function compressImage(file, maxWidth = 1200, quality = 0.85) {
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

        // --- 4. VIEW RENDERING PIPELINE ---
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
        // 5. RENDERING THE CUSTOMER HOME PORTAL
        // ==========================================
        function renderHome(container) {
            const visibleBouquets = state.bouquets.filter(b => b.visible !== false);
            const displayedBouquets = state.selectedCategory === 'All' 
                ? visibleBouquets 
                : visibleBouquets.filter(b => b.category === state.selectedCategory);

            container.innerHTML = `
                <!-- Navigation -->
                <nav class="fixed w-full top-0 z-40 glass-header">
                    <div class="max-w-7xl mx-auto px-6 h-24 flex items-center justify-between">
                        <div class="flex items-center gap-4 cursor-pointer group" onclick="window.scrollTo({top:0, behavior:'smooth'})">
                            <img src="${state.settings.logo || 'IMG_0254.png'}" onerror="this.src='IMG_0254.png'" alt="Tatka Ful Logo" class="w-14 h-14 rounded-full object-cover shadow-sm group-hover:scale-105 transition-transform duration-500" />
                            <span class="text-2xl font-serif font-semibold text-gray-900 tracking-wide group-hover:text-[#064e3b] transition-colors">Tatka Ful</span>
                        </div>
                        <div class="hidden md:flex items-center gap-10 text-sm font-semibold tracking-widest uppercase text-gray-500">
                            <a href="#collection" class="hover:text-[#064e3b] transition-colors">Collections</a>
                            <a href="https://wa.me/${formatWhatsApp(state.settings.whatsapp)}" target="_blank" rel="noreferrer" class="premium-btn text-white px-8 py-3.5 rounded-full tracking-widest text-xs font-bold uppercase">
                                Inquire Now
                            </a>
                        </div>
                    </div>
                </nav>

                <!-- Hero Section with Premium Watercolor Canvas Backdrop -->
                <section class="relative pt-32 pb-24 md:pt-48 md:pb-36 px-6 flex items-center justify-center min-h-[75vh] overflow-hidden">
                    <div class="absolute inset-0 z-0">
                        <img src="${state.settings.banner || 'IMG_0255.png'}" onerror="this.src='IMG_0255.png'" alt="Luxury Floral Banner" class="w-full h-full object-cover opacity-25 scale-105" />
                        <div class="absolute inset-0 bg-gradient-to-b from-[#fcfbf9]/90 via-[#fcfbf9]/60 to-[#fcfbf9]"></div>
                    </div>

                    <div class="max-w-4xl mx-auto text-center relative z-10 animate-fade-up">
                        <span class="inline-block py-1.5 px-4 rounded-full bg-[#064e3b]/5 text-[#064e3b] text-xs font-bold uppercase tracking-[0.3em] mb-6 border border-[#064e3b]/10">
                            Premium Floral Design
                        </span>
                        <h1 class="text-5xl md:text-7xl lg:text-8xl font-serif text-gray-900 mb-8 leading-[1.1] tracking-tight">
                            ${state.settings.heroSlogan}
                        </h1>
                        <p class="text-lg md:text-xl text-gray-600 mb-12 max-w-2xl mx-auto font-light leading-relaxed">
                            ${state.settings.heroDesc}
                        </p>
                        <a href="#collection" class="inline-flex items-center gap-3 premium-btn text-white px-10 py-5 rounded-full text-sm uppercase tracking-widest font-semibold">
                            View Gallery 
                            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"></path></svg>
                        </a>
                    </div>
                </section>

                <!-- Pills Collections Navigation (Sticky Interface) -->
                <section id="collection" class="px-6 py-6 sticky top-24 glass-header z-30 shadow-sm border-t border-gray-100">
                    <div class="max-w-7xl mx-auto flex gap-4 overflow-x-auto pb-2 scrollbar-hide snap-x">
                        <button onclick="setCategoryFilter('All')" class="snap-start whitespace-nowrap px-8 py-3 rounded-full transition-all duration-500 text-sm font-semibold tracking-wider uppercase ${state.selectedCategory === 'All' ? 'bg-[#022c22] text-white shadow-md' : 'bg-transparent text-gray-500 hover:text-[#064e3b] hover:bg-gray-100'}">
                            All Designs
                        </button>
                        ${state.categories.map(cat => `
                            <button onclick="setCategoryFilter('${cat}')" class="snap-start whitespace-nowrap px-8 py-3 rounded-full transition-all duration-500 text-sm font-semibold tracking-wider uppercase ${state.selectedCategory === cat ? 'bg-[#022c22] text-white shadow-md' : 'bg-transparent text-gray-500 hover:text-[#064e3b] hover:bg-gray-100'}">
                                ${cat}
                            </button>
                        `).join('')}
                    </div>
                </section>

                <!-- Floral Gallery Layout -->
                <section class="px-6 py-24 max-w-7xl mx-auto min-h-[50vh]">
                    ${displayedBouquets.length === 0 ? `
                        <div class="text-center py-32 luxury-card rounded-[3rem] animate-fade-up">
                            <div class="w-24 h-24 bg-[#ecfdf5] rounded-full flex items-center justify-center mx-auto mb-8">
                                <svg class="w-10 h-10 text-[#064e3b]" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M4 16l4.586-4.586a2 2 0 012.828 0L16 16m-2-2l1.586-1.586a2 2 0 012.828 0L20 14m-6-6h.01M6 20h12a2 2 0 002-2V6a2 2 0 00-2-2H6a2 2 0 00-2 2v12a2 2 0 002 2z"></path></svg>
                            </div>
                            <h3 class="text-3xl font-serif text-gray-900 mb-3">Collection is empty</h3>
                            <p class="text-gray-500 font-light text-lg">Our designers are currently building premium designs.</p>
                        </div>
                    ` : `
                        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-x-10 gap-y-16">
                            ${displayedBouquets.map((bouquet, index) => `
                                <div class="group cursor-pointer flex flex-col animate-fade-up" style="animation-delay: ${index * 0.05}s" onclick="openDetailModal('${bouquet.id}')">
                                    <div class="relative aspect-[4/5] rounded-[2rem] overflow-hidden luxury-card mb-6">
                                        ${bouquet.images && bouquet.images.length > 0 ? `
                                            <img src="${bouquet.images[0]}" alt="${bouquet.name}" class="w-full h-full object-cover transition-transform duration-[1.5s] group-hover:scale-110" />
                                        ` : `
                                            <div class="w-full h-full flex items-center justify-center bg-gray-50 text-gray-300">No Image Preview</div>
                                        `}
                                        <div class="absolute inset-0 bg-gradient-to-t from-black/30 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-500"></div>
                                        
                                        ${bouquet.bestseller ? `
                                            <div class="absolute top-5 left-5 bg-white/95 backdrop-blur-md text-[#b8860b] text-[10px] font-bold uppercase tracking-[0.2em] px-4 py-2 rounded-full flex items-center gap-1.5 shadow-lg">
                                                <span class="w-1.5 h-1.5 bg-[#b8860b] rounded-full"></span> Signature Art
                                            </div>
                                        ` : ''}
                                    </div>
                                    <div class="px-3">
                                        <p class="text-[11px] font-bold tracking-[0.2em] text-[#064e3b] uppercase mb-3">${bouquet.category}</p>
                                        <h3 class="text-2xl font-serif text-gray-900 mb-3 group-hover:text-[#064e3b] transition-colors">${bouquet.name}</h3>
                                        <p class="text-gray-500 text-sm line-clamp-2 leading-relaxed font-light mb-4">${bouquet.description}</p>
                                    </div>
                                </div>
                            `).join('')}
                        </div>
                    `}
                </section>

                <!-- 100% Working Pulse Action (Floating WhatsApp) -->
                <div class="fixed bottom-6 right-6 z-40 flex flex-col gap-4">
                    <a href="https://wa.me/${formatWhatsApp(state.settings.whatsapp)}" target="_blank" rel="noreferrer" class="relative w-16 h-16 bg-[#25D366] text-white rounded-full flex items-center justify-center hover:scale-105 transition-transform shadow-[0_10px_30px_rgba(37,211,102,0.4)]">
                        <span class="absolute inline-flex h-full w-full rounded-full bg-[#25D366] opacity-40 animate-ping"></span>
                        <svg class="w-8 h-8 relative z-10" fill="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946C.06 5.348 5.397.01 12.008.01c3.202.001 6.212 1.246 8.477 3.514 2.266 2.268 3.507 5.28 3.505 8.484-.004 6.657-5.34 11.997-11.953 11.997-2.005-.001-3.973-.502-5.713-1.455L0 24zm6.59-4.846c1.6.95 3.188 1.449 4.625 1.451 5.436 0 9.851-4.398 9.854-9.807.001-2.621-1.013-5.086-2.86-6.935C16.36 1.913 13.9.894 11.285.894c-5.438 0-9.854 4.398-9.858 9.808 0 2.037.533 4.024 1.547 5.765l-.99 3.613 3.73-.973h.001a9.78 9.78 0 0 0 4.332 1.048zM18.15 14.86c-.337-.168-1.996-.983-2.305-1.096-.309-.113-.534-.168-.758.168-.225.337-.871 1.096-1.067 1.32-.197.225-.393.253-.73.084-.337-.168-1.42-.524-2.707-1.671-1.002-.894-1.679-2.001-1.875-2.337-.197-.337-.021-.519.147-.687.152-.151.337-.393.506-.59.168-.197.225-.337.337-.562.113-.225.056-.422-.028-.59-.084-.168-.758-1.825-1.039-2.503-.274-.662-.553-.573-.758-.583-.197-.01-.422-.012-.647-.012-.225 0-.59.084-.9.422-.309.337-1.18 1.151-1.18 2.808 0 1.657 1.208 3.257 1.377 3.482.168.225 2.378 3.63 5.76 5.087.805.347 1.433.554 1.923.71.808.257 1.545.221 2.127.135.649-.096 1.996-.815 2.277-1.601.281-.787.281-1.461.197-1.601-.084-.14-.309-.225-.647-.393z"/></svg>
                    </a>
                </div>

                <!-- Footer System with Hidden Entrance Integration -->
                <footer class="bg-white border-t border-gray-100 pt-24 pb-12 px-6">
                    <div class="max-w-7xl mx-auto flex flex-col md:flex-row justify-between items-center gap-12 text-center md:text-left">
                        <div class="flex flex-col items-center md:items-start max-w-sm">
                            <img src="${state.settings.logo || 'IMG_0254.png'}" onerror="this.src='IMG_0254.png'" alt="Logo" class="w-20 h-20 rounded-full mb-6 shadow-sm object-cover" />
                            <h3 class="font-serif text-3xl text-gray-900 mb-4">Tatka Ful</h3>
                            <p class="text-gray-500 text-sm leading-relaxed font-light">
                                Nature's finest expressions of love, premium flower concepts curated flawlessly.
                            </p>
                        </div>
                        <div class="flex flex-col items-center md:items-end">
                            <p class="text-xs font-bold tracking-[0.2em] text-gray-400 uppercase mb-4">Studio Connections</p>
                            <div class="flex gap-4">
                                <a href="${state.settings.instagram}" target="_blank" rel="noreferrer" class="w-12 h-12 rounded-full border border-gray-200 flex items-center justify-center text-gray-600 hover:text-[#064e3b] hover:border-[#064e3b] transition-all">
                                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 9a2 2 0 012-2h.93a2 2 0 001.664-.89l.812-1.22A2 2 0 0110.07 4h3.86a2 2 0 011.664.89l.812 1.22A2 2 0 0018.07 7H19a2 2 0 012 2v9a2 2 0 01-2 2H5a2 2 0 01-2-2V9z"></path><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 13a3 3 0 11-6 0 3 3 0 016 0z"></path></svg>
                                </a>
                                <a href="tel:${state.settings.phone}" class="w-12 h-12 rounded-full border border-gray-200 flex items-center justify-center text-gray-600 hover:text-[#064e3b] hover:border-[#064e3b] transition-all">
                                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.94.725l.548 2.2a1 1 0 01-.321.988l-1.305.98a10.582 10.582 0 004.872 4.872l.98-1.305a1 1 0 01.988-.321l2.2.548a1 1 0 01.725.94V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"></path></svg>
                                </a>
                            </div>
                        </div>
                    </div>
                    <div class="max-w-7xl mx-auto mt-20 pt-8 border-t border-gray-100 text-center">
                        <p id="secret-trigger" class="text-[10px] font-semibold tracking-[0.2em] uppercase text-gray-400 cursor-default select-none hover:text-gray-900 transition-colors" title="Double click to access hidden admin panel">
                            &copy; 2026 Tatka Ful. Crafted with elegance.
                        </p>
                    </div>
                </footer>

                <!-- Render Detail Modal if selected -->
                <div id="modal-container"></div>
            `;

            // Double Click dynamic listener definition
            document.getElementById('secret-trigger').addEventListener('dblclick', () => {
                state.currentView = 'admin_login';
                updateView();
            });

            // If selected bouquet is open
            if (state.selectedBouquet) {
                renderDetailModal();
            }
        }

        // ==========================================
        // 6. CATEGORY FILTER ACTION
        // ==========================================
        function setCategoryFilter(category) {
            state.selectedCategory = category;
            updateView();
            const el = document.getElementById('collection');
            if (el) el.scrollIntoView({ behavior: 'smooth' });
        }

        // ==========================================
        // 7. ULTRA PREMIUM DETAIL MODAL
        // ==========================================
        function openDetailModal(id) {
            const bouquet = state.bouquets.find(b => b.id === id);
            if (bouquet) {
                state.selectedBouquet = bouquet;
                updateView();
            }
        }

        function closeDetailModal() {
            state.selectedBouquet = null;
            updateView();
        }

        function renderDetailModal() {
            const bouquet = state.selectedBouquet;
            const container = document.getElementById('modal-container');
            if (!container) return;

            container.innerHTML = `
                <div class="fixed inset-0 z-50 flex items-center justify-center p-0 md:p-8">
                    <div class="absolute inset-0 bg-black/60 backdrop-blur-md transition-opacity" onclick="closeDetailModal()"></div>
                    <div class="relative bg-white w-full h-full md:h-auto md:max-h-[90vh] md:max-w-6xl md:rounded-[2rem] shadow-2xl overflow-hidden flex flex-col md:flex-row animate-fade-up">
                        
                        <button onclick="closeDetailModal()" class="absolute top-6 right-6 z-20 w-12 h-12 bg-white/90 backdrop-blur-md rounded-full flex items-center justify-center text-gray-900 hover:bg-gray-100 transition-colors shadow-lg">
                            <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path></svg>
                        </button>

                        <!-- Gallery View Panel -->
                        <div class="w-full md:w-1/2 bg-[#fcfbf9] h-[50vh] md:h-auto overflow-y-auto snap-y snap-mandatory scrollbar-hide relative">
                            ${bouquet.images && bouquet.images.length > 0 ? bouquet.images.map((img, i) => `
                                <div class="w-full h-full min-h-[50vh] md:min-h-full snap-center relative">
                                    <img src="${img}" alt="${bouquet.name} ${i+1}" class="w-full h-full object-cover" />
                                </div>
                            `).join('') : `
                                <div class="w-full h-full flex items-center justify-center text-gray-300 font-light">No Gallery Images</div>
                            `}
                            ${bouquet.images && bouquet.images.length > 1 ? `
                                <div class="absolute bottom-6 left-0 right-0 flex justify-center gap-2 pointer-events-none">
                                    <span class="bg-black/40 backdrop-blur-md text-white text-[10px] tracking-wider px-4 py-2 rounded-full uppercase font-semibold">Scroll for more images</span>
                                </div>
                            ` : ''}
                        </div>

                        <!-- Details Section and CTAs -->
                        <div class="w-full md:w-1/2 p-8 md:p-16 flex flex-col h-[50vh] md:h-auto overflow-y-auto bg-white">
                            <p class="text-[11px] font-bold tracking-[0.3em] text-[#064e3b] uppercase mb-4">${bouquet.category}</p>
                            <h2 class="text-4xl md:text-5xl font-serif text-gray-900 mb-6 leading-tight">${bouquet.name}</h2>
                            <div class="w-16 h-[2px] bg-[#d4af37] mb-8"></div>
                            <p class="text-gray-600 leading-relaxed mb-10 font-light text-lg">${bouquet.description}</p>
                            
                            <div class="mt-auto space-y-4">
                                <div class="flex items-center gap-3 text-sm text-gray-500 mb-8 font-medium bg-gray-50 p-4 rounded-xl">
                                    <svg class="w-5 h-5 text-[#064e3b] shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg>
                                    <span>100% Fresh premium quality guaranteed. Handcrafted.</span>
                                </div>
                                <a href="https://wa.me/${formatWhatsApp(state.settings.whatsapp)}?text=${encodeURIComponent(`Hello Tatka Ful! I would love to order the premium "${bouquet.name}" design.`)}" target="_blank" rel="noreferrer" class="w-full premium-btn text-white py-5 rounded-full flex items-center justify-center gap-3 text-sm font-bold uppercase tracking-[0.2em]">
                                    Order via WhatsApp
                                </a>
                                <a href="tel:${state.settings.phone}" class="w-full bg-white text-gray-900 py-5 rounded-full flex items-center justify-center gap-3 text-sm font-bold uppercase tracking-[0.2em] border border-gray-200 hover:bg-gray-50 transition-colors text-center block">
                                    Call Studio
                                </a>
                            </div>
                        </div>
                    </div>
                </div>
            `;
        }

        // ==========================================
        // 8. ADMIN LOGIN VIEW
        // ==========================================
        function renderAdminLogin(container) {
            container.innerHTML = `
                <div class="min-h-screen bg-[#fcfbf9] flex items-center justify-center px-6">
                    <div class="bg-white p-10 md:p-14 rounded-[3rem] shadow-[0_20px_50px_-20px_rgba(0,0,0,0.1)] w-full max-w-md border border-gray-100">
                        <div class="flex justify-center mb-8">
                            <img src="${state.settings.logo || 'IMG_0254.png'}" onerror="this.src='IMG_0254.png'" alt="Logo" class="w-24 h-24 rounded-full shadow-md object-cover" />
                        </div>
                        <h2 class="text-3xl font-serif text-center text-gray-900 mb-2">Studio Portal</h2>
                        <p class="text-center text-gray-400 mb-10 text-[10px] font-bold tracking-[0.3em] uppercase">Authorized Access</p>
                        
                        <form id="login-form">
                            <div class="mb-8">
                                <input id="passcode-input" type="password" placeholder="PASSCODE" required class="w-full px-6 py-4 bg-gray-50 border border-gray-200 rounded-2xl focus:outline-none focus:border-[#064e3b] focus:ring-1 focus:ring-[#064e3b] transition-all text-center tracking-[0.5em] text-lg font-bold uppercase" />
                                <p id="login-error" class="text-red-500 text-sm mt-3 text-center font-medium hidden"></p>
                            </div>
                            <button type="submit" class="w-full premium-btn text-white py-4 rounded-2xl font-bold uppercase tracking-[0.2em] text-sm">
                                Unlock Studio
                            </button>
                            <button type="button" onclick="state.currentView='home'; updateView();" class="w-full mt-6 text-gray-400 hover:text-gray-900 py-2 text-xs transition-colors flex items-center justify-center gap-2 font-bold uppercase tracking-widest">
                                Return to Website
                            </button>
                        </form>
                    </div>
                </div>
            `;

            document.getElementById('login-form').onsubmit = (e) => {
                e.preventDefault();
                const input = document.getElementById('passcode-input').value;
                const error = document.getElementById('login-error');
                if (input === 'gym') {
                    state.currentView = 'admin_dashboard';
                    updateView();
                } else {
                    error.textContent = 'Invalid passcode';
                    error.classList.remove('hidden');
                }
            };
        }

        // ==========================================
        // 9. ADMIN DASHBOARD WORKSPACE
        // ==========================================
        function renderAdminDashboard(container) {
            container.innerHTML = `
                <div class="min-h-screen bg-[#fcfbf9] flex flex-col md:flex-row font-sans text-gray-800">
                    
                    <!-- Sidebar Navigation -->
                    <aside class="w-full md:w-80 bg-white border-r border-gray-100 flex flex-col shrink-0 z-10 shadow-sm">
                        <div class="p-8 border-b border-gray-50 flex items-center gap-4">
                            <img src="${state.settings.logo || 'IMG_0254.png'}" onerror="this.src='IMG_0254.png'" alt="Logo" class="w-14 h-14 rounded-full shadow-sm object-cover" />
                            <div>
                                <span class="font-serif text-2xl text-gray-900 block">Studio</span>
                                <span class="text-[10px] uppercase tracking-widest text-gray-400 font-bold">Tatka Ful Admin</span>
                            </div>
                        </div>
                        <div class="p-6 space-y-2 flex-1">
                            <button onclick="setAdminTab('bouquets')" class="w-full flex items-center gap-4 px-6 py-4 rounded-2xl transition-all font-semibold text-sm tracking-wide ${state.adminTab === 'bouquets' ? 'bg-[#064e3b] text-white shadow-md' : 'text-gray-500 hover:bg-gray-50 hover:text-gray-900'}">
                                <span class="w-5 h-5 flex items-center justify-center bg-gray-200/50 rounded-md text-inherit">📦</span> Masterpieces
                            </button>
                            <button onclick="setAdminTab('settings')" class="w-full flex items-center gap-4 px-6 py-4 rounded-2xl transition-all font-semibold text-sm tracking-wide ${state.adminTab === 'settings' ? 'bg-[#064e3b] text-white shadow-md' : 'text-gray-500 hover:bg-gray-50 hover:text-gray-900'}">
                                <span class="w-5 h-5 flex items-center justify-center bg-gray-200/50 rounded-md text-inherit">⚙️</span> Brand Settings
                            </button>
                        </div>
                        <div class="p-6">
                            <button onclick="state.currentView='home'; updateView();" class="w-full flex items-center justify-center gap-3 px-6 py-4 rounded-2xl bg-gray-50 text-gray-600 hover:bg-red-50 hover:text-red-600 transition-all font-bold text-xs uppercase tracking-widest">
                                Exit Studio
                            </button>
                        </div>
                    </aside>

                    <!-- Main Dynamic Area -->
                    <main id="admin-main-area" class="flex-1 p-6 md:p-12 overflow-y-auto">
                        <!-- Dashboard components go here -->
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

        // Render interior dashboard tabs
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

        // ==========================================
        // 10. ADMIN: INVENTORY LIST
        // ==========================================
        function renderBouquetList(container) {
            container.innerHTML = `
                <div class="animate-fade-up max-w-6xl mx-auto">
                    <div class="flex flex-col md:flex-row justify-between items-start md:items-center mb-12 gap-6">
                        <div>
                            <h1 class="text-4xl font-serif text-gray-900 mb-2">Inventory Management</h1>
                            <p class="text-gray-500 font-light">Curate and publish natural artwork.</p>
                        </div>
                        <button onclick="openNewBouquetForm()" class="premium-btn text-white px-8 py-4 rounded-full flex items-center gap-3 font-bold uppercase tracking-[0.2em] text-xs">
                            New Design
                        </button>
                    </div>

                    <!-- Dashboard Stats -->
                    <div class="grid grid-cols-1 md:grid-cols-3 gap-6 mb-12">
                        <div class="bg-white p-8 rounded-3xl border border-gray-100 shadow-sm">
                            <p class="text-xs text-gray-400 font-bold tracking-[0.2em] uppercase mb-3">Total Designs</p>
                            <p class="text-5xl font-serif text-gray-900">${state.bouquets.length}</p>
                        </div>
                        <div class="bg-white p-8 rounded-3xl border border-gray-100 shadow-sm">
                            <p class="text-xs text-[#064e3b] font-bold tracking-[0.2em] uppercase mb-3">Active Display</p>
                            <p class="text-5xl font-serif text-[#064e3b]">${state.bouquets.filter(b => b.visible).length}</p>
                        </div>
                        <div class="bg-white p-8 rounded-3xl border border-gray-100 shadow-sm">
                            <p class="text-xs text-[#b8860b] font-bold tracking-[0.2em] uppercase mb-3">Signature (Star)</p>
                            <p class="text-5xl font-serif text-[#b8860b]">${state.bouquets.filter(b => b.bestseller).length}</p>
                        </div>
                    </div>

                    <!-- Table List -->
                    <div class="bg-white border border-gray-100 rounded-3xl overflow-hidden shadow-sm">
                        <table class="w-full text-left border-collapse">
                            <thead>
                                <tr class="border-b border-gray-100 bg-gray-50/50">
                                    <th class="p-6 text-xs font-bold text-gray-400 uppercase tracking-[0.2em]">Item</th>
                                    <th class="p-6 text-xs font-bold text-gray-400 uppercase tracking-[0.2em] hidden md:table-cell">Category</th>
                                    <th class="p-6 text-xs font-bold text-gray-400 uppercase tracking-[0.2em] text-center">Status</th>
                                    <th class="p-6 text-xs font-bold text-gray-400 uppercase tracking-[0.2em] text-right">Actions</th>
                                </tr>
                            </thead>
                            <tbody class="divide-y divide-gray-50">
                                ${state.bouquets.length === 0 ? `
                                    <tr>
                                        <td colSpan="4" class="p-12 text-center text-gray-400 font-light text-lg">No inventory found. Click 'New Design' to publish first piece.</td>
                                    </tr>
                                ` : state.bouquets.map(b => `
                                    <tr class="hover:bg-gray-50/50 transition-colors">
                                        <td class="p-6 flex items-center gap-6">
                                            <div class="w-16 h-16 rounded-2xl bg-gray-100 overflow-hidden shrink-0 border border-gray-200">
                                                ${b.images && b.images[0] ? `<img src="${b.images[0]}" class="w-full h-full object-cover" />` : `<div class="w-full h-full flex items-center justify-center text-gray-300">N/A</div>`}
                                            </div>
                                            <div>
                                                <p class="font-serif text-xl text-gray-900">${b.name}</p>
                                                ${b.bestseller ? `<span class="text-[9px] bg-[#b8860b]/10 text-[#b8860b] px-3 py-1 rounded-full font-bold uppercase tracking-widest mt-2 inline-block">Signature</span>` : ''}
                                            </div>
                                        </td>
                                        <td class="p-6 text-sm text-gray-600 hidden md:table-cell font-medium">${b.category}</td>
                                        <td class="p-6 text-center">
                                            <button onclick="toggleVisibility('${b.id}')" class="p-3 rounded-full transition-all ${b.visible ? 'text-[#064e3b] bg-[#ecfdf5] hover:bg-[#d1fae5]' : 'text-gray-400 bg-gray-100 hover:bg-gray-200'}">
                                                ${b.visible ? 'Show' : 'Hide'}
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
        // 11. ADMIN: ADD / EDIT BOUQUET FORM
        // ==========================================
        function renderBouquetForm(container) {
            container.innerHTML = `
                <div class="animate-fade-up max-w-4xl mx-auto bg-white p-8 md:p-14 border border-gray-100 rounded-[3rem] shadow-sm">
                    <div class="flex items-center gap-6 mb-12 border-b border-gray-100 pb-8">
                        <button onclick="cancelBouquetForm()" class="p-4 bg-gray-50 rounded-full hover:bg-gray-100 text-gray-600 transition-colors">
                            <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 19l-7-7m0 0l7-7m-7 7h18"></path></svg>
                        </button>
                        <h2 class="text-4xl font-serif text-gray-900">${state.editingId ? 'Edit Design' : 'Create Design'}</h2>
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
                                <input required id="form-name" type="text" value="${state.formData.name}" class="w-full px-6 py-5 bg-gray-50 border border-gray-200 rounded-2xl focus:ring-2 focus:ring-[#064e3b]/20 focus:border-[#064e3b] outline-none transition-all font-medium text-lg" placeholder="e.g. Royal Rose" />
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

                        <div class="flex gap-10 pt-4">
                            <label class="flex items-center gap-4 cursor-pointer group">
                                <input id="form-bestseller" type="checkbox" ${state.formData.bestseller ? 'checked' : ''} class="w-6 h-6 text-[#064e3b] focus:ring-[#064e3b]" />
                                <span class="text-xs font-bold tracking-[0.2em] text-gray-600 uppercase">Mark Signature</span>
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
                        alert("Max 5 images allowed per bouquet.");
                        return;
                    }
                    state.isUploading = true;
                    renderAdminMainSection(); // Refreshes to show upload loading status
                    
                    try {
                        const processed = await Promise.all(files.map(f => compressImage(f, 1000, 0.82)));
                        state.formData.images = [...state.formData.images, ...processed].slice(0, 5);
                    } catch (err) {
                        alert("Error uploading images.");
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
                state.formData.bestseller = document.getElementById('form-bestseller').checked;
                state.formData.visible = document.getElementById('form-visible').checked;

                if (state.editingId) {
                    state.bouquets = state.bouquets.map(b => b.id === state.editingId ? { ...state.formData, id: state.editingId } : b);
                } else {
                    state.bouquets = [{ ...state.formData, id: Date.now().toString() }, ...state.bouquets];
                }

                // Sync data directly to database
                await dbSet('tf_bouquets_v3', state.bouquets);
                state.isAddingBouquet = false;
                state.editingId = null;
                renderAdminMainSection();
            };
        }

        function openNewBouquetForm() {
            state.formData = {
                name: '',
                category: state.categories[0] || '',
                description: '',
                images: [],
                bestseller: false,
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

        async function deleteBouquet(id) {
            if (confirm("Delete this design permanently from gallery?")) {
                state.bouquets = state.bouquets.filter(b => b.id !== id);
                await dbSet('tf_bouquets_v3', state.bouquets);
                renderAdminMainSection();
            }
        }

        async function toggleVisibility(id) {
            state.bouquets = state.bouquets.map(b => b.id === id ? { ...b, visible: !b.visible } : b);
            await dbSet('tf_bouquets_v3', state.bouquets);
            renderAdminMainSection();
        }

        // ==========================================
        // 12. ADMIN: BRAND SETTINGS PANEL
        // ==========================================
        function renderSettingsPanel(container) {
            container.innerHTML = `
                <div class="animate-fade-up max-w-4xl mx-auto">
                    <div class="mb-10">
                        <h1 class="text-4xl font-serif text-gray-900 mb-2">Brand Settings</h1>
                        <p class="text-gray-500 font-light">Tailor your high-end brand assets and slogans dynamically.</p>
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
                                <h3 class="text-2xl font-serif text-gray-900 mb-8 border-b border-gray-100 pb-4">Messaging</h3>
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
                                <h3 class="text-2xl font-serif text-gray-900 mb-8 border-b border-gray-100 pb-4">Contacts</h3>
                                <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                                    <div>
                                        <label class="block text-xs font-bold tracking-[0.2em] text-gray-400 mb-3 uppercase">WhatsApp</label>
                                        <input required id="sett-whatsapp" type="text" value="${state.settings.whatsapp}" class="w-full px-6 py-5 bg-gray-50 border border-gray-200 rounded-2xl outline-none font-bold text-lg" />
                                    </div>
                                    <div>
                                        <label class="block text-xs font-bold tracking-[0.2em] text-gray-400 mb-3 uppercase">Phone</label>
                                        <input required id="sett-phone" type="text" value="${state.settings.phone}" class="w-full px-6 py-5 bg-gray-50 border border-gray-200 rounded-2xl outline-none font-bold text-lg" />
                                    </div>
                                    <div class="md:col-span-2">
                                        <label class="block text-xs font-bold tracking-[0.2em] text-gray-400 mb-3 uppercase">Instagram</label>
                                        <input required id="sett-instagram" type="text" value="${state.settings.instagram}" class="w-full px-6 py-5 bg-gray-50 border border-gray-200 rounded-2xl outline-none font-medium text-lg" />
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
                } catch (err) {
                    alert("Error scaling logo image.");
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
                } catch (err) {
                    alert("Error scaling banner image.");
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

                await dbSet('tf_settings_v3', state.settings);
                alert("Settings Saved Successfully!");
                updateView();
            };
        }

        // ==========================================
        // 13. SYSTEM BOOTSTRAP (Initialization)
        // ==========================================
        async function bootstrap() {
            try {
                // Read from IndexedDB safely on bootup
                const savedBouquets = await dbGet('tf_bouquets_v3');
                const savedCategories = await dbGet('tf_categories_v3');
                const savedSettings = await dbGet('tf_settings_v3');
                
                if (savedBouquets) state.bouquets = savedBouquets;
                if (savedCategories) state.categories = savedCategories;
                if (savedSettings) state.settings = savedSettings;
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
