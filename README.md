<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tatka Ful | Premium Floral Concepts</title>
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
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,500;0,600;0,700;0,800;1,400;1,500&family=Plus+Jakarta+Sans:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">

    <style>
        :root {
            --ink-deep: #0b2e22;
            --emerald: #10583f;
            --emerald-soft: #eaf6f0;
            --gold: #c8a13a;
            --gold-deep: #9c7a1f;
            --gold-soft: #f6ecd2;
            --pearl: #faf8f4;
        }

        body {
            background-color: var(--pearl);
            font-family: 'Plus Jakarta Sans', sans-serif;
            overflow-x: hidden;
        }

        .glass-header {
            background: rgba(250, 248, 244, 0.86);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border-bottom: 1px solid rgba(11, 46, 34, 0.05);
        }

        .luxury-card {
            background: #ffffff;
            border: 1px solid rgba(11, 46, 34, 0.06);
            box-shadow: 0 15px 35px -10px rgba(11, 46, 34, 0.06);
            transition: all 0.5s cubic-bezier(0.16, 1, 0.3, 1);
        }
        .luxury-card:hover {
            box-shadow: 0 30px 60px -15px rgba(11, 46, 34, 0.14);
            transform: translateY(-6px);
            border-color: rgba(200, 161, 58, 0.35);
        }

        .premium-btn {
            position: relative;
            overflow: hidden;
            background: linear-gradient(135deg, var(--ink-deep) 0%, var(--emerald) 100%);
            box-shadow: 0 10px 24px -6px rgba(11, 46, 34, 0.35);
            transition: all 0.35s cubic-bezier(0.16, 1, 0.3, 1);
        }
        .premium-btn:hover {
            box-shadow: 0 16px 32px -6px rgba(11, 46, 34, 0.45);
            transform: translateY(-2px);
        }
        .premium-btn::before {
            content: '';
            position: absolute;
            top: 0; left: -75%;
            width: 45%; height: 100%;
            background: linear-gradient(120deg, transparent, rgba(255,255,255,0.35), transparent);
            transform: skewX(-20deg);
            pointer-events: none;
        }
        .premium-btn:hover::before {
            animation: shimmer 1.1s ease forwards;
        }
        @keyframes shimmer { to { left: 130%; } }

        .gold-btn {
            background: linear-gradient(135deg, var(--gold-deep) 0%, var(--gold) 100%);
            box-shadow: 0 10px 22px -6px rgba(156, 122, 31, 0.4);
        }

        .social-badge {
            position: relative;
            width: 3.1rem; height: 3.1rem;
            border-radius: 9999px;
            display: flex; align-items: center; justify-content: center;
            border: 1px solid rgba(11, 46, 34, 0.12);
            color: var(--ink-deep);
            background: #fff;
            transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
        }
        .social-badge:hover {
            color: #fff;
            border-color: transparent;
            background: linear-gradient(135deg, var(--gold-deep), var(--emerald));
            transform: translateY(-4px);
            box-shadow: 0 14px 24px -8px rgba(11, 46, 34, 0.35);
        }

        .eyebrow-flourish {
            display: inline-flex; align-items: center; gap: 0.6rem;
            font-size: 0.68rem; font-weight: 700; letter-spacing: 0.3em;
            text-transform: uppercase; color: var(--gold-deep);
        }
        .eyebrow-flourish::before, .eyebrow-flourish::after {
            content: ''; width: 22px; height: 1px;
            background: linear-gradient(90deg, transparent, var(--gold));
        }
        .eyebrow-flourish::after { background: linear-gradient(90deg, var(--gold), transparent); }

        .gold-divider {
            width: 64px; height: 2px;
            background: linear-gradient(90deg, var(--gold-deep), var(--gold));
            border-radius: 2px;
        }

        .orb {
            position: absolute;
            border-radius: 9999px;
            filter: blur(70px);
            pointer-events: none;
        }

        ::-webkit-scrollbar { width: 6px; height: 6px; }
        ::-webkit-scrollbar-track { background: transparent; }
        ::-webkit-scrollbar-thumb { background: rgba(16, 88, 63, 0.25); border-radius: 10px; }
        ::-webkit-scrollbar-thumb:hover { background: rgba(16, 88, 63, 0.45); }

        .scrollbar-hide::-webkit-scrollbar { display: none; }
        .scrollbar-hide { -ms-overflow-style: none; scrollbar-width: none; }

        @keyframes fadeUp {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .animate-fade-up { animation: fadeUp 1s cubic-bezier(0.16, 1, 0.3, 1) forwards; }

        input:focus, textarea:focus, select:focus { outline: none; }
    </style>
</head>
<body class="text-gray-800 antialiased selection:bg-[#10583f] selection:text-white">

    <div id="loader-screen" class="fixed inset-0 z-50 bg-[#faf8f4] flex flex-col items-center justify-center transition-all duration-700">
        <div class="flex flex-col items-center space-y-4">
            <svg class="animate-spin h-10 w-10 text-[#10583f]" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24">
                <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
                <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
            </svg>
            <h1 class="text-3xl font-serif tracking-wider text-gray-900 animate-pulse">Tatka Ful</h1>
            <p class="text-xs uppercase tracking-[0.2em] text-gray-400 font-semibold">Luxury Floral Design</p>
        </div>
    </div>

    <div id="app-root" class="min-h-screen flex flex-col"></div>

    <script>
        // --- 1. CLOUD SYNC (Firebase Realtime Database — shared across ALL devices) ---
        async function dbSet(key, val) {
            return window.__firebaseSetPath(key, val);
        }

        // --- 2. GLOBAL SYSTEM STATE ---
        let state = {
            currentView: 'home', // 'home' | 'admin_login' | 'admin_dashboard'
            selectedCategory: 'All',
            searchQuery: '',
            selectedBouquet: null,
            bouquets: [],
            reviews: [],
            categories: [
                "🌹 Rose Bouquet", "💐 Mixed Bouquet", "🌸 Lily Bouquet", "🌻 Sunflower Bouquet",
                "💵 Money Bouquet", "❤️ Anniversary Bouquet", "🎂 Birthday Bouquet", "💍 Proposal Bouquet",
                "💖 Valentine's Bouquet", "👰 Wedding Bouquet", "🎓 Graduation Bouquet", "🎉 Congratulations Bouquet",
                "🎁 Surprise Bouquet", "✨ Premium Bouquet", "👑 Luxury Bouquet"
            ],
            settings: {
                logo: 'IMG_0254.png',
                banner: 'IMG_0255.png',
                phone: '01410619501',
                whatsapp: '01410619501',
                instagram: 'https://instagram.com/tatka_ful',
                tiktok: 'https://tiktok.com/@tatka.ful',
                facebook: 'https://facebook.com/tatkaful',
                heroSlogan: 'Elegance in Every Petal.',
                heroDesc: 'Curating luxury floral masterpieces for your most precious memories. Exclusively hand-crafted with passion.',
                deliveryText: '⚡ 3-Hour Delivery Available in Dhaka'
            },
            adminTab: 'bouquets', // 'bouquets' | 'reviews' | 'settings'
            isAddingBouquet: false,
            editingId: null,
            formData: { name: '', category: '', description: '', images: [], bestseller: false, visible: true },
            isUploading: false,
            isAddingReview: false,
            editingReviewId: null,
            reviewFormData: { name: '', stars: 5, text: '', image: '' },
            isUploadingReview: false
        };

        // Secret admin-access counter (7 clicks on footer credit line)
        let secretClickCount = 0;
        let secretClickTimer = null;

        // --- 3. HELPER FUNCTIONS ---
        function formatWhatsApp(number) {
            let formatted = (number || '').replace(/[^0-9]/g, '');
            if (formatted.startsWith('0')) formatted = '88' + formatted;
            return formatted;
        }

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

        function starGlyphs(count) {
            let out = '';
            for (let i = 1; i <= 5; i++) {
                out += `<span class="${i <= count ? 'text-[#c8a13a]' : 'text-gray-200'} text-base leading-none">★</span>`;
            }
            return out;
        }

        function renderStarPicker(current) {
            let html = '<div class="flex gap-2">';
            for (let i = 1; i <= 5; i++) {
                html += `<button type="button" onclick="setReviewStars(${i})" class="text-4xl leading-none transition-transform hover:scale-110 ${i <= current ? 'text-[#c8a13a]' : 'text-gray-200'}">★</button>`;
            }
            html += '</div>';
            return html;
        }

        // Order via WhatsApp — auto-downloads the bouquet photo to the customer's
        // device (so it's ready in their gallery to attach) and opens a prefilled
        // WhatsApp chat. Note: no website can insert an image directly into a
        // WhatsApp chat bubble automatically — that is a WhatsApp platform
        // restriction, not something any client-side code can bypass. This is the
        // closest and most reliable equivalent.
        function orderViaWhatsApp(bouquetId, event) {
            if (event) event.stopPropagation();
            const bouquet = state.bouquets.find(b => b.id === bouquetId);
            if (!bouquet) return;

            if (bouquet.images && bouquet.images[0]) {
                try {
                    const link = document.createElement('a');
                    link.href = bouquet.images[0];
                    link.download = `TatkaFul-${bouquet.name.replace(/[^a-zA-Z0-9]+/g, '-')}.jpg`;
                    document.body.appendChild(link);
                    link.click();
                    document.body.removeChild(link);
                } catch (err) {
                    console.error('Auto-download of bouquet photo failed:', err);
                }
            }

            const message = `Hello Tatka Ful! 🌸 I would love to order the premium "${bouquet.name}" design.\n(📷 Photo saved on my device — attaching it here!)`;
            const url = `https://wa.me/${formatWhatsApp(state.settings.whatsapp)}?text=${encodeURIComponent(message)}`;
            window.open(url, '_blank', 'noreferrer');
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
        function computeFilteredBouquets() {
            const visibleBouquets = state.bouquets.filter(b => b.visible !== false);
            let list = state.selectedCategory === 'All' ? visibleBouquets : visibleBouquets.filter(b => b.category === state.selectedCategory);
            const q = state.searchQuery.trim().toLowerCase();
            if (q) {
                list = list.filter(b =>
                    (b.name || '').toLowerCase().includes(q) ||
                    (b.category || '').toLowerCase().includes(q) ||
                    (b.description || '').toLowerCase().includes(q)
                );
            }
            return list;
        }

        function renderCategoryChipsHTML() {
            return `
                <button onclick="setCategoryFilter('All')" class="snap-start whitespace-nowrap px-6 sm:px-8 py-3 rounded-full transition-all duration-500 text-xs sm:text-sm font-semibold tracking-wider uppercase ${state.selectedCategory === 'All' ? 'bg-[#0b2e22] text-white shadow-md' : 'bg-transparent text-gray-500 hover:text-[#10583f] hover:bg-gray-100'}">
                    All Designs
                </button>
                ${state.categories.map(cat => `
                    <button onclick="setCategoryFilter('${cat.replace(/'/g, "\\'")}')" class="snap-start whitespace-nowrap px-6 sm:px-8 py-3 rounded-full transition-all duration-500 text-xs sm:text-sm font-semibold tracking-wider uppercase ${state.selectedCategory === cat ? 'bg-[#0b2e22] text-white shadow-md' : 'bg-transparent text-gray-500 hover:text-[#10583f] hover:bg-gray-100'}">
                        ${cat}
                    </button>
                `).join('')}
            `;
        }

        function renderBouquetGridHTML(displayedBouquets) {
            if (displayedBouquets.length === 0) {
                return `
                    <div class="text-center py-24 sm:py-32 luxury-card rounded-[2rem] sm:rounded-[3rem] animate-fade-up">
                        <div class="w-20 h-20 sm:w-24 sm:h-24 bg-[#eaf6f0] rounded-full flex items-center justify-center mx-auto mb-8">
                            <svg class="w-9 h-9 sm:w-10 sm:h-10 text-[#10583f]" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M4 16l4.586-4.586a2 2 0 012.828 0L16 16m-2-2l1.586-1.586a2 2 0 012.828 0L20 14m-6-6h.01M6 20h12a2 2 0 002-2V6a2 2 0 00-2-2H6a2 2 0 00-2 2v12a2 2 0 002 2z"></path></svg>
                        </div>
                        <h3 class="text-2xl sm:text-3xl font-serif text-gray-900 mb-3">${state.searchQuery ? 'No matching designs found' : 'Collection is empty'}</h3>
                        <p class="text-gray-500 font-light text-base sm:text-lg px-6">${state.searchQuery ? 'Try a different search term or browse all categories.' : 'Our designers are currently building premium designs.'}</p>
                    </div>
                `;
            }
            return `
                <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-x-4 sm:gap-x-6 md:gap-x-10 gap-y-8 sm:gap-y-10 md:gap-y-16">
                    ${displayedBouquets.map((bouquet, index) => `
                        <div class="group cursor-pointer flex flex-col animate-fade-up" style="animation-delay: ${index * 0.05}s" onclick="openDetailModal('${bouquet.id}')">
                            <div class="relative aspect-[4/5] rounded-[1.25rem] sm:rounded-[2rem] overflow-hidden luxury-card mb-3 sm:mb-6">
                                ${bouquet.images && bouquet.images.length > 0 ? `
                                    <img src="${bouquet.images[0]}" alt="${bouquet.name}" class="w-full h-full object-cover transition-transform duration-[1.5s] group-hover:scale-110" />
                                ` : `
                                    <div class="w-full h-full flex items-center justify-center bg-gray-50 text-gray-300 text-xs">No Image</div>
                                `}
                                <div class="absolute inset-0 bg-gradient-to-t from-black/30 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-500"></div>
                                ${bouquet.bestseller ? `
                                    <div class="absolute top-2 left-2 sm:top-5 sm:left-5 bg-white/95 backdrop-blur-md text-[#9c7a1f] text-[8px] sm:text-[10px] font-bold uppercase tracking-[0.15em] sm:tracking-[0.2em] px-2.5 sm:px-4 py-1.5 sm:py-2 rounded-full flex items-center gap-1.5 shadow-lg">
                                        <span class="w-1.5 h-1.5 bg-[#c8a13a] rounded-full"></span> Signature
                                    </div>
                                ` : ''}
                            </div>
                            <div class="px-1 sm:px-3 flex flex-col flex-1">
                                <p class="text-[9px] sm:text-[11px] font-bold tracking-[0.15em] sm:tracking-[0.2em] text-[#10583f] uppercase mb-1.5 sm:mb-3 truncate">${bouquet.category}</p>
                                <h3 class="text-base sm:text-2xl font-serif text-gray-900 mb-1.5 sm:mb-3 group-hover:text-[#10583f] transition-colors leading-snug">${bouquet.name}</h3>
                                <p class="hidden sm:block text-gray-500 text-sm line-clamp-2 leading-relaxed font-light mb-4">${bouquet.description}</p>
                                <button onclick="orderViaWhatsApp('${bouquet.id}', event)" class="mt-auto premium-btn text-white text-[10px] sm:text-xs font-bold uppercase tracking-[0.12em] sm:tracking-[0.2em] py-2.5 sm:py-3.5 rounded-full flex items-center justify-center gap-1.5 sm:gap-2">
                                    <svg class="w-3.5 h-3.5 sm:w-4 sm:h-4" fill="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946C.06 5.348 5.397.01 12.008.01c3.202.001 6.212 1.246 8.477 3.514 2.266 2.268 3.507 5.28 3.505 8.484-.004 6.657-5.34 11.997-11.953 11.997-2.005-.001-3.973-.502-5.713-1.455L0 24zm6.59-4.846c1.6.95 3.188 1.449 4.625 1.451 5.436 0 9.851-4.398 9.854-9.807.001-2.621-1.013-5.086-2.86-6.935C16.36 1.913 13.9.894 11.285.894c-5.438 0-9.854 4.398-9.858 9.808 0 2.037.533 4.024 1.547 5.765l-.99 3.613 3.73-.973h.001a9.78 9.78 0 0 0 4.332 1.048z"/></svg>
                                    <span class="sm:hidden">Order</span>
                                    <span class="hidden sm:inline">Order Now</span>
                                </button>
                            </div>
                        </div>
                    `).join('')}
                </div>
            `;
        }

        function refreshCollection() {
            const chipsWrap = document.getElementById('category-chips-wrapper');
            const gridWrap = document.getElementById('bouquet-grid-wrapper');
            if (chipsWrap) chipsWrap.innerHTML = renderCategoryChipsHTML();
            if (gridWrap) gridWrap.innerHTML = renderBouquetGridHTML(computeFilteredBouquets());
        }

        function setCategoryFilter(category) {
            state.selectedCategory = category;
            refreshCollection();
            const el = document.getElementById('collection');
            if (el) el.scrollIntoView({ behavior: 'smooth' });
        }

        function handleSearchInput(value) {
            state.searchQuery = value;
            refreshCollection();
        }

        function renderReviewsSectionHTML() {
            if (!state.reviews || state.reviews.length === 0) return '';
            return `
                <section class="px-6 py-20 sm:py-28 max-w-7xl mx-auto">
                    <div class="text-center mb-14 sm:mb-20">
                        <span class="eyebrow-flourish">Client Stories</span>
                        <h2 class="text-3xl sm:text-5xl font-serif text-gray-900 mt-5">What Our Clients Say</h2>
                    </div>
                    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6 sm:gap-8">
                        ${state.reviews.map((r, i) => `
                            <div class="luxury-card rounded-[2rem] p-8 sm:p-10 flex flex-col animate-fade-up" style="animation-delay:${i * 0.06}s">
                                <svg class="w-8 h-8 text-[#f6ecd2] mb-4" fill="currentColor" viewBox="0 0 24 24"><path d="M9.983 3v7.391c0 5.704-3.731 9.57-8.983 10.609l-.995-2.151c2.432-.917 3.995-3.638 3.995-5.849h-4v-10h9.983zm14.017 0v7.391c0 5.704-3.748 9.571-9 10.609l-.996-2.151c2.433-.917 3.996-3.638 3.996-5.849h-3.983v-10h9.983z"/></svg>
                                <div class="flex gap-1 mb-4">${starGlyphs(r.stars || 5)}</div>
                                <p class="text-gray-600 italic font-light mb-8 leading-relaxed flex-1">${r.text}</p>
                                <div class="mt-auto flex items-center gap-4 pt-4 border-t border-gray-50">
                                    <img src="${r.image || state.settings.logo || 'IMG_0254.png'}" onerror="this.src='IMG_0254.png'" class="w-12 h-12 rounded-full object-cover border border-gray-100" />
                                    <span class="font-serif text-lg text-gray-900">${r.name}</span>
                                </div>
                            </div>
                        `).join('')}
                    </div>
                </section>
            `;
        }

        function renderHome(container) {
            container.innerHTML = `
                <nav class="fixed w-full top-0 z-40 glass-header">
                    <div class="max-w-7xl mx-auto px-6 h-24 flex items-center justify-between">
                        <div class="flex items-center gap-4 cursor-pointer group" onclick="window.scrollTo({top:0, behavior:'smooth'})">
                            <img src="${state.settings.logo || 'IMG_0254.png'}" onerror="this.src='IMG_0254.png'" alt="Tatka Ful Logo" class="w-14 h-14 rounded-full object-cover shadow-sm group-hover:scale-105 transition-transform duration-500" />
                            <span class="text-2xl font-serif font-semibold text-gray-900 tracking-wide group-hover:text-[#10583f] transition-colors">Tatka Ful</span>
                        </div>
                        <div class="hidden md:flex items-center gap-10 text-sm font-semibold tracking-widest uppercase text-gray-500">
                            <a href="#collection" class="hover:text-[#10583f] transition-colors">Collections</a>
                            <a href="https://wa.me/${formatWhatsApp(state.settings.whatsapp)}" target="_blank" rel="noreferrer" class="premium-btn text-white px-8 py-3.5 rounded-full tracking-widest text-xs font-bold uppercase">
                                Inquire Now
                            </a>
                        </div>
                    </div>
                </nav>

                <section class="relative pt-32 pb-20 md:pt-48 md:pb-32 px-6 flex items-center justify-center min-h-[75vh] overflow-hidden">
                    <div class="orb w-[28rem] h-[28rem] bg-[#10583f]/10 -top-20 -left-20"></div>
                    <div class="orb w-[24rem] h-[24rem] bg-[#c8a13a]/15 top-32 -right-10"></div>
                    <div class="absolute inset-0 z-0">
                        <img src="${state.settings.banner || 'IMG_0255.png'}" onerror="this.src='IMG_0255.png'" alt="Luxury Floral Banner" class="w-full h-full object-cover opacity-20 scale-105" />
                        <div class="absolute inset-0 bg-gradient-to-b from-[#faf8f4]/90 via-[#faf8f4]/70 to-[#faf8f4]"></div>
                    </div>

                    <div class="max-w-4xl mx-auto text-center relative z-10 animate-fade-up">
                        <span class="eyebrow-flourish">Premium Floral Design</span>
                        <h1 class="text-4xl md:text-7xl lg:text-8xl font-serif text-gray-900 mt-6 mb-8 leading-[1.1] tracking-tight">
                            ${state.settings.heroSlogan}
                        </h1>
                        <p class="text-base md:text-xl text-gray-600 mb-8 max-w-2xl mx-auto font-light leading-relaxed">
                            ${state.settings.heroDesc}
                        </p>
                        ${state.settings.deliveryText ? `
                        <div class="inline-flex items-center gap-2.5 bg-white/80 backdrop-blur-md border border-[#c8a13a]/30 rounded-full px-5 sm:px-6 py-2.5 sm:py-3 mb-10 shadow-sm">
                            <span class="text-sm font-bold tracking-[0.15em] uppercase text-[#0b2e22]">${state.settings.deliveryText}</span>
                        </div>` : ''}
                        <div>
                        <a href="#collection" class="inline-flex items-center gap-3 premium-btn text-white px-10 py-5 rounded-full text-sm uppercase tracking-widest font-semibold">
                            View Gallery
                            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"></path></svg>
                        </a>
                        </div>
                    </div>
                </section>

                <section id="collection" class="px-6 py-6 sticky top-24 glass-header z-30 shadow-sm border-t border-gray-100">
                    <div class="max-w-7xl mx-auto flex flex-col gap-4">
                        <div class="relative max-w-xl w-full">
                            <svg class="w-5 h-5 text-gray-400 absolute left-5 top-1/2 -translate-y-1/2 pointer-events-none" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-4.35-4.35M11 19a8 8 0 100-16 8 8 0 000 16z"></path></svg>
                            <input id="search-input" type="text" value="${state.searchQuery}" oninput="handleSearchInput(this.value)" placeholder="Search bouquets by name or occasion..." class="w-full pl-12 pr-5 py-3.5 bg-white border border-gray-200 rounded-full text-sm font-medium focus:border-[#10583f] focus:ring-2 focus:ring-[#10583f]/10 transition-all placeholder:text-gray-400 placeholder:font-normal" />
                        </div>
                        <div id="category-chips-wrapper" class="flex gap-3 overflow-x-auto pb-2 scrollbar-hide snap-x">
                            ${renderCategoryChipsHTML()}
                        </div>
                    </div>
                </section>

                <section class="px-6 py-16 sm:py-24 max-w-7xl mx-auto min-h-[50vh]">
                    <div id="bouquet-grid-wrapper">
                        ${renderBouquetGridHTML(computeFilteredBouquets())}
                    </div>
                </section>

                ${renderReviewsSectionHTML()}

                <div class="fixed bottom-6 right-6 z-40 flex flex-col gap-4">
                    <a href="https://wa.me/${formatWhatsApp(state.settings.whatsapp)}" target="_blank" rel="noreferrer" class="relative w-16 h-16 bg-[#25D366] text-white rounded-full flex items-center justify-center hover:scale-105 transition-transform shadow-[0_10px_30px_rgba(37,211,102,0.4)]">
                        <span class="absolute inline-flex h-full w-full rounded-full bg-[#25D366] opacity-40 animate-ping"></span>
                        <svg class="w-8 h-8 relative z-10" fill="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946C.06 5.348 5.397.01 12.008.01c3.202.001 6.212 1.246 8.477 3.514 2.266 2.268 3.507 5.28 3.505 8.484-.004 6.657-5.34 11.997-11.953 11.997-2.005-.001-3.973-.502-5.713-1.455L0 24zm6.59-4.846c1.6.95 3.188 1.449 4.625 1.451 5.436 0 9.851-4.398 9.854-9.807.001-2.621-1.013-5.086-2.86-6.935C16.36 1.913 13.9.894 11.285.894c-5.438 0-9.854 4.398-9.858 9.808 0 2.037.533 4.024 1.547 5.765l-.99 3.613 3.73-.973h.001a9.78 9.78 0 0 0 4.332 1.048zM18.15 14.86c-.337-.168-1.996-.983-2.305-1.096-.309-.113-.534-.168-.758.168-.225.337-.871 1.096-1.067 1.32-.197.225-.393.253-.73.084-.337-.168-1.42-.524-2.707-1.671-1.002-.894-1.679-2.001-1.875-2.337-.197-.337-.021-.519.147-.687.152-.151.337-.393.506-.59.168-.197.225-.337.337-.562.113-.225.056-.422-.028-.59-.084-.168-.758-1.825-1.039-2.503-.274-.662-.553-.573-.758-.583-.197-.01-.422-.012-.647-.012-.225 0-.59.084-.9.422-.309.337-1.18 1.151-1.18 2.808 0 1.657 1.208 3.257 1.377 3.482.168.225 2.378 3.63 5.76 5.087.805.347 1.433.554 1.923.71.808.257 1.545.221 2.127.135.649-.096 1.996-.815 2.277-1.601.281-.787.281-1.461.197-1.601-.084-.14-.309-.225-.647-.393z"/></svg>
                    </a>
                </div>

                <footer class="bg-white border-t border-gray-100 pt-20 sm:pt-24 pb-12 px-6">
                    <div class="max-w-7xl mx-auto flex flex-col md:flex-row justify-between items-center gap-12 text-center md:text-left">
                        <div class="flex flex-col items-center md:items-start max-w-sm">
                            <img src="${state.settings.logo || 'IMG_0254.png'}" onerror="this.src='IMG_0254.png'" alt="Logo" class="w-20 h-20 rounded-full mb-6 shadow-sm object-cover" />
                            <h3 class="font-serif text-3xl text-gray-900 mb-4">Tatka Ful</h3>
                            <p class="text-gray-500 text-sm leading-relaxed font-light">
                                Nature's finest expressions of love, premium flower concepts curated flawlessly.
                            </p>
                        </div>
                        <div class="flex flex-col items-center md:items-end">
                            <p class="text-xs font-bold tracking-[0.2em] text-gray-400 uppercase mb-5">Studio Connections</p>
                            <div class="flex gap-4">
                                <a href="${state.settings.instagram}" target="_blank" rel="noreferrer" class="social-badge">
                                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 9a2 2 0 012-2h.93a2 2 0 001.664-.89l.812-1.22A2 2 0 0110.07 4h3.86a2 2 0 011.664.89l.812 1.22A2 2 0 0018.07 7H19a2 2 0 012 2v9a2 2 0 01-2 2H5a2 2 0 01-2-2V9z"></path><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 13a3 3 0 11-6 0 3 3 0 016 0z"></path></svg>
                                </a>
                                ${state.settings.facebook ? `
                                <a href="${state.settings.facebook}" target="_blank" rel="noreferrer" class="social-badge">
                                    <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M14 13.5h2.5l.5-3H14V8.5c0-.75.25-1.5 1.5-1.5H17V4.5c-.5 0-1.5-.1-2.5-.1-2.5 0-4 1.5-4 4.5V10.5H8v3h2.5V21h3.5v-7.5z"></path></svg>
                                </a>` : ''}
                                ${state.settings.tiktok ? `
                                <a href="${state.settings.tiktok}" target="_blank" rel="noreferrer" class="social-badge">
                                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 18V5l12-2v13M9 18a3 3 0 11-6 0 3 3 0 016 0zm12-2a3 3 0 11-6 0 3 3 0 016 0z"></path></svg>
                                </a>` : ''}
                                <a href="tel:${state.settings.phone}" class="social-badge">
                                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.94.725l.548 2.2a1 1 0 01-.321.988l-1.305.98a10.582 10.582 0 004.872 4.872l.98-1.305a1 1 0 01.988-.321l2.2.548a1 1 0 01.725.94V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"></path></svg>
                                </a>
                            </div>
                        </div>
                    </div>
                    <div class="max-w-7xl mx-auto mt-20 pt-8 border-t border-gray-100 text-center">
                        <p id="secret-trigger" class="text-[10px] font-semibold tracking-[0.2em] uppercase text-gray-400 cursor-default select-none hover:text-gray-900 transition-colors">
                            &copy; 2026 Tatka Ful. Crafted with elegance.
                        </p>
                    </div>
                </footer>

                <div id="modal-container"></div>
            `;

            // Secret admin access: 7 clicks on the footer credit line (resets after a short pause)
            const secretEl = document.getElementById('secret-trigger');
            secretEl.addEventListener('click', () => {
                secretClickCount++;
                clearTimeout(secretClickTimer);
                secretClickTimer = setTimeout(() => { secretClickCount = 0; }, 1500);
                if (secretClickCount >= 7) {
                    secretClickCount = 0;
                    state.currentView = 'admin_login';
                    updateView();
                }
            });

            if (state.selectedBouquet) {
                renderDetailModal();
            }
        }

        // ==========================================
        // 7. ULTRA PREMIUM DETAIL MODAL
        // ==========================================
        function openDetailModal(id) {
            const bouquet = state.bouquets.find(b => b.id === id);
            if (bouquet) {
                state.selectedBouquet = bouquet;
                renderDetailModal();
            }
        }

        function closeDetailModal() {
            state.selectedBouquet = null;
            const container = document.getElementById('modal-container');
            if (container) container.innerHTML = '';
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

                        <div class="w-full md:w-1/2 bg-[#faf8f4] h-[50vh] md:h-auto overflow-y-auto snap-y snap-mandatory scrollbar-hide relative">
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

                        <div class="w-full md:w-1/2 p-8 md:p-16 flex flex-col h-[50vh] md:h-auto overflow-y-auto bg-white">
                            <p class="text-[11px] font-bold tracking-[0.3em] text-[#10583f] uppercase mb-4">${bouquet.category}</p>
                            <h2 class="text-4xl md:text-5xl font-serif text-gray-900 mb-6 leading-tight">${bouquet.name}</h2>
                            <div class="gold-divider mb-8"></div>
                            <p class="text-gray-600 leading-relaxed mb-10 font-light text-lg">${bouquet.description}</p>

                            <div class="mt-auto space-y-4">
                                <div class="flex items-center gap-3 text-sm text-gray-500 mb-8 font-medium bg-gray-50 p-4 rounded-xl">
                                    <svg class="w-5 h-5 text-[#10583f] shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg>
                                    <span>100% Fresh premium quality guaranteed. Handcrafted.</span>
                                </div>
                                <button onclick="orderViaWhatsApp('${bouquet.id}')" class="w-full premium-btn text-white py-5 rounded-full flex items-center justify-center gap-3 text-sm font-bold uppercase tracking-[0.2em]">
                                    <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946C.06 5.348 5.397.01 12.008.01c3.202.001 6.212 1.246 8.477 3.514 2.266 2.268 3.507 5.28 3.505 8.484-.004 6.657-5.34 11.997-11.953 11.997-2.005-.001-3.973-.502-5.713-1.455L0 24zm6.59-4.846c1.6.95 3.188 1.449 4.625 1.451 5.436 0 9.851-4.398 9.854-9.807.001-2.621-1.013-5.086-2.86-6.935C16.36 1.913 13.9.894 11.285.894c-5.438 0-9.854 4.398-9.858 9.808 0 2.037.533 4.024 1.547 5.765l-.99 3.613 3.73-.973h.001a9.78 9.78 0 0 0 4.332 1.048z"/></svg>
                                    Order via WhatsApp
                                </button>
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
                <div class="min-h-screen bg-[#faf8f4] flex items-center justify-center px-6">
                    <div class="bg-white p-10 md:p-14 rounded-[3rem] shadow-[0_20px_50px_-20px_rgba(0,0,0,0.1)] w-full max-w-md border border-gray-100">
                        <div class="flex justify-center mb-8">
                            <img src="${state.settings.logo || 'IMG_0254.png'}" onerror="this.src='IMG_0254.png'" alt="Logo" class="w-24 h-24 rounded-full shadow-md object-cover" />
                        </div>
                        <h2 class="text-3xl font-serif text-center text-gray-900 mb-2">Studio Portal</h2>
                        <p class="text-center text-gray-400 mb-10 text-[10px] font-bold tracking-[0.3em] uppercase">Authorized Access</p>

                        <form id="login-form">
                            <div class="mb-8">
                                <input id="passcode-input" type="password" placeholder="PASSCODE" required class="w-full px-6 py-4 bg-gray-50 border border-gray-200 rounded-2xl focus:border-[#10583f] focus:ring-1 focus:ring-[#10583f] transition-all text-center tracking-[0.5em] text-lg font-bold uppercase" />
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
                <div class="min-h-screen bg-[#faf8f4] flex flex-col md:flex-row font-sans text-gray-800">

                    <aside class="w-full md:w-80 bg-white border-r border-gray-100 flex flex-col shrink-0 z-10 shadow-sm">
                        <div class="p-8 border-b border-gray-50 flex items-center gap-4">
                            <img src="${state.settings.logo || 'IMG_0254.png'}" onerror="this.src='IMG_0254.png'" alt="Logo" class="w-14 h-14 rounded-full shadow-sm object-cover" />
                            <div>
                                <span class="font-serif text-2xl text-gray-900 block">Studio</span>
                                <span class="text-[10px] uppercase tracking-widest text-gray-400 font-bold">Tatka Ful Admin</span>
                            </div>
                        </div>
                        <div class="p-6 space-y-2 flex-1">
                            <button onclick="setAdminTab('bouquets')" class="w-full flex items-center gap-4 px-6 py-4 rounded-2xl transition-all font-semibold text-sm tracking-wide ${state.adminTab === 'bouquets' ? 'bg-[#10583f] text-white shadow-md' : 'text-gray-500 hover:bg-gray-50 hover:text-gray-900'}">
                                <span class="w-5 h-5 flex items-center justify-center">📦</span> Masterpieces
                            </button>
                            <button onclick="setAdminTab('reviews')" class="w-full flex items-center gap-4 px-6 py-4 rounded-2xl transition-all font-semibold text-sm tracking-wide ${state.adminTab === 'reviews' ? 'bg-[#10583f] text-white shadow-md' : 'text-gray-500 hover:bg-gray-50 hover:text-gray-900'}">
                                <span class="w-5 h-5 flex items-center justify-center">⭐</span> Client Reviews
                            </button>
                            <button onclick="setAdminTab('settings')" class="w-full flex items-center gap-4 px-6 py-4 rounded-2xl transition-all font-semibold text-sm tracking-wide ${state.adminTab === 'settings' ? 'bg-[#10583f] text-white shadow-md' : 'text-gray-500 hover:bg-gray-50 hover:text-gray-900'}">
                                <span class="w-5 h-5 flex items-center justify-center">⚙️</span> Brand Settings
                            </button>
                        </div>
                        <div class="p-6">
                            <button onclick="state.currentView='home'; updateView();" class="w-full flex items-center justify-center gap-3 px-6 py-4 rounded-2xl bg-gray-50 text-gray-600 hover:bg-red-50 hover:text-red-600 transition-all font-bold text-xs uppercase tracking-widest">
                                Exit Studio
                            </button>
                        </div>
                    </aside>

                    <main id="admin-main-area" class="flex-1 p-6 md:p-12 overflow-y-auto"></main>
                </div>
            `;
            renderAdminMainSection();
        }

        function setAdminTab(tab) {
            state.adminTab = tab;
            state.isAddingBouquet = false;
            state.editingId = null;
            state.isAddingReview = false;
            state.editingReviewId = null;
            renderAdminMainSection();
        }

        function renderAdminMainSection() {
            const container = document.getElementById('admin-main-area');
            if (!container) return;

            if (state.adminTab === 'bouquets') {
                if (state.isAddingBouquet) { renderBouquetForm(container); } else { renderBouquetList(container); }
            } else if (state.adminTab === 'reviews') {
                if (state.isAddingReview) { renderReviewForm(container); } else { renderReviewList(container); }
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

                    <div class="grid grid-cols-1 md:grid-cols-3 gap-6 mb-12">
                        <div class="bg-white p-8 rounded-3xl border border-gray-100 shadow-sm">
                            <p class="text-xs text-gray-400 font-bold tracking-[0.2em] uppercase mb-3">Total Designs</p>
                            <p class="text-5xl font-serif text-gray-900">${state.bouquets.length}</p>
                        </div>
                        <div class="bg-white p-8 rounded-3xl border border-gray-100 shadow-sm">
                            <p class="text-xs text-[#10583f] font-bold tracking-[0.2em] uppercase mb-3">Active Display</p>
                            <p class="text-5xl font-serif text-[#10583f]">${state.bouquets.filter(b => b.visible).length}</p>
                        </div>
                        <div class="bg-white p-8 rounded-3xl border border-gray-100 shadow-sm">
                            <p class="text-xs text-[#9c7a1f] font-bold tracking-[0.2em] uppercase mb-3">Signature (Star)</p>
                            <p class="text-5xl font-serif text-[#9c7a1f]">${state.bouquets.filter(b => b.bestseller).length}</p>
                        </div>
                    </div>

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
                                    <tr><td colspan="4" class="p-12 text-center text-gray-400 font-light text-lg">No inventory found. Click 'New Design' to publish first piece.</td></tr>
                                ` : state.bouquets.map(b => `
                                    <tr class="hover:bg-gray-50/50 transition-colors">
                                        <td class="p-6 flex items-center gap-6">
                                            <div class="w-16 h-16 rounded-2xl bg-gray-100 overflow-hidden shrink-0 border border-gray-200">
                                                ${b.images && b.images[0] ? `<img src="${b.images[0]}" class="w-full h-full object-cover" />` : `<div class="w-full h-full flex items-center justify-center text-gray-300">N/A</div>`}
                                            </div>
                                            <div>
                                                <p class="font-serif text-xl text-gray-900">${b.name}</p>
                                                ${b.bestseller ? `<span class="text-[9px] bg-[#c8a13a]/10 text-[#9c7a1f] px-3 py-1 rounded-full font-bold uppercase tracking-widest mt-2 inline-block">Signature</span>` : ''}
                                            </div>
                                        </td>
                                        <td class="p-6 text-sm text-gray-600 hidden md:table-cell font-medium">${b.category}</td>
                                        <td class="p-6 text-center">
                                            <button onclick="toggleVisibility('${b.id}')" class="p-3 rounded-full transition-all text-xs font-bold uppercase tracking-widest ${b.visible ? 'text-[#10583f] bg-[#eaf6f0] hover:bg-[#d7efe3]' : 'text-gray-400 bg-gray-100 hover:bg-gray-200'}">
                                                ${b.visible ? 'Shown' : 'Hidden'}
                                            </button>
                                        </td>
                                        <td class="p-6 text-right space-x-3">
                                            <button onclick="editBouquet('${b.id}')" class="p-3 text-gray-400 hover:text-[#10583f] hover:bg-[#eaf6f0] rounded-full transition-all inline-block">Edit</button>
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
                        <div class="bg-[#faf8f4] p-8 rounded-[2rem] border border-gray-100">
                            <label class="block text-xs font-bold tracking-[0.2em] text-gray-400 mb-6 uppercase">Gallery Images (Max 5)</label>
                            <div class="grid grid-cols-2 md:grid-cols-5 gap-4">
                                ${state.formData.images.map((img, idx) => `
                                    <div class="relative aspect-[4/5] rounded-2xl overflow-hidden group shadow-sm border border-gray-200">
                                        <img src="${img}" class="w-full h-full object-cover" />
                                        <button type="button" onclick="removeFormImage(${idx})" class="absolute inset-0 bg-red-900/60 text-white flex items-center justify-center opacity-0 group-hover:opacity-100 transition-opacity backdrop-blur-sm font-bold">Remove</button>
                                    </div>
                                `).join('')}
                                ${state.formData.images.length < 5 ? `
                                    <label class="aspect-[4/5] rounded-2xl border-2 border-dashed border-gray-300 hover:border-[#10583f] hover:bg-[#eaf6f0] transition-colors flex flex-col items-center justify-center cursor-pointer text-gray-400 hover:text-[#10583f] bg-white">
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
                                <input required id="form-name" type="text" value="${state.formData.name}" oninput="state.formData.name=this.value" class="w-full px-6 py-5 bg-gray-50 border border-gray-200 rounded-2xl focus:ring-2 focus:ring-[#10583f]/20 focus:border-[#10583f] transition-all font-medium text-lg" placeholder="e.g. Royal Rose" />
                            </div>
                            <div>
                                <label class="block text-xs font-bold tracking-[0.2em] text-gray-400 mb-3 uppercase">Category</label>
                                <select id="form-category" onchange="state.formData.category=this.value" class="w-full px-6 py-5 bg-gray-50 border border-gray-200 rounded-2xl focus:ring-2 focus:ring-[#10583f]/20 focus:border-[#10583f] transition-all font-medium text-lg">
                                    ${state.categories.map(c => `<option value="${c}" ${state.formData.category === c ? 'selected' : ''}>${c}</option>`).join('')}
                                </select>
                            </div>
                        </div>

                        <div>
                            <label class="block text-xs font-bold tracking-[0.2em] text-gray-400 mb-3 uppercase">Description</label>
                            <textarea required id="form-desc" oninput="state.formData.description=this.value" rows="4" class="w-full px-6 py-5 bg-gray-50 border border-gray-200 rounded-2xl focus:ring-2 focus:ring-[#10583f]/20 focus:border-[#10583f] transition-all resize-none font-medium text-lg leading-relaxed">${state.formData.description}</textarea>
                        </div>

                        <div class="flex gap-10 pt-4">
                            <label class="flex items-center gap-4 cursor-pointer group">
                                <input id="form-bestseller" type="checkbox" ${state.formData.bestseller ? 'checked' : ''} onchange="state.formData.bestseller=this.checked" class="w-6 h-6 text-[#10583f] focus:ring-[#10583f]" />
                                <span class="text-xs font-bold tracking-[0.2em] text-gray-600 uppercase">Mark Signature</span>
                            </label>
                            <label class="flex items-center gap-4 cursor-pointer group">
                                <input id="form-visible" type="checkbox" ${state.formData.visible ? 'checked' : ''} onchange="state.formData.visible=this.checked" class="w-6 h-6 text-[#10583f] focus:ring-[#10583f]" />
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
                    renderAdminMainSection();
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

                await dbSet('tf_bouquets_v3', state.bouquets);
                state.isAddingBouquet = false;
                state.editingId = null;
                renderAdminMainSection();
            };
        }

        function openNewBouquetForm() {
            state.formData = { name: '', category: state.categories[0] || '', description: '', images: [], bestseller: false, visible: true };
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
        // 12. ADMIN: CLIENT REVIEWS (FULLY FAKE / CUSTOM)
        // ==========================================
        function renderReviewList(container) {
            const avg = state.reviews.length ? (state.reviews.reduce((s, r) => s + (r.stars || 0), 0) / state.reviews.length).toFixed(1) : '0.0';
            container.innerHTML = `
                <div class="animate-fade-up max-w-6xl mx-auto">
                    <div class="flex flex-col md:flex-row justify-between items-start md:items-center mb-12 gap-6">
                        <div>
                            <h1 class="text-4xl font-serif text-gray-900 mb-2">Client Reviews</h1>
                            <p class="text-gray-500 font-light">Fully custom testimonials shown on your homepage.</p>
                        </div>
                        <button onclick="openNewReviewForm()" class="premium-btn text-white px-8 py-4 rounded-full flex items-center gap-3 font-bold uppercase tracking-[0.2em] text-xs">
                            New Review
                        </button>
                    </div>

                    <div class="grid grid-cols-1 md:grid-cols-2 gap-6 mb-12">
                        <div class="bg-white p-8 rounded-3xl border border-gray-100 shadow-sm">
                            <p class="text-xs text-gray-400 font-bold tracking-[0.2em] uppercase mb-3">Total Reviews</p>
                            <p class="text-5xl font-serif text-gray-900">${state.reviews.length}</p>
                        </div>
                        <div class="bg-white p-8 rounded-3xl border border-gray-100 shadow-sm">
                            <p class="text-xs text-[#9c7a1f] font-bold tracking-[0.2em] uppercase mb-3">Average Rating</p>
                            <p class="text-5xl font-serif text-[#9c7a1f]">${avg} ★</p>
                        </div>
                    </div>

                    <div class="bg-white border border-gray-100 rounded-3xl overflow-hidden shadow-sm">
                        <table class="w-full text-left border-collapse">
                            <thead>
                                <tr class="border-b border-gray-100 bg-gray-50/50">
                                    <th class="p-6 text-xs font-bold text-gray-400 uppercase tracking-[0.2em]">Reviewer</th>
                                    <th class="p-6 text-xs font-bold text-gray-400 uppercase tracking-[0.2em] hidden md:table-cell">Review</th>
                                    <th class="p-6 text-xs font-bold text-gray-400 uppercase tracking-[0.2em] text-center">Rating</th>
                                    <th class="p-6 text-xs font-bold text-gray-400 uppercase tracking-[0.2em] text-right">Actions</th>
                                </tr>
                            </thead>
                            <tbody class="divide-y divide-gray-50">
                                ${state.reviews.length === 0 ? `
                                    <tr><td colspan="4" class="p-12 text-center text-gray-400 font-light text-lg">No reviews yet. Click 'New Review' to add your first testimonial.</td></tr>
                                ` : state.reviews.map(r => `
                                    <tr class="hover:bg-gray-50/50 transition-colors">
                                        <td class="p-6 flex items-center gap-5">
                                            <div class="w-14 h-14 rounded-full bg-gray-100 overflow-hidden shrink-0 border border-gray-200">
                                                ${r.image ? `<img src="${r.image}" class="w-full h-full object-cover" />` : `<div class="w-full h-full flex items-center justify-center text-gray-300 text-xs">N/A</div>`}
                                            </div>
                                            <p class="font-serif text-lg text-gray-900">${r.name}</p>
                                        </td>
                                        <td class="p-6 text-sm text-gray-500 hidden md:table-cell font-light max-w-sm truncate">${r.text}</td>
                                        <td class="p-6 text-center whitespace-nowrap">${starGlyphs(r.stars || 5)}</td>
                                        <td class="p-6 text-right space-x-3">
                                            <button onclick="editReview('${r.id}')" class="p-3 text-gray-400 hover:text-[#10583f] hover:bg-[#eaf6f0] rounded-full transition-all inline-block">Edit</button>
                                            <button onclick="deleteReview('${r.id}')" class="p-3 text-gray-400 hover:text-red-600 hover:bg-red-50 rounded-full transition-all inline-block">Delete</button>
                                        </td>
                                    </tr>
                                `).join('')}
                            </tbody>
                        </table>
                    </div>
                </div>
            `;
        }

        function renderReviewForm(container) {
            container.innerHTML = `
                <div class="animate-fade-up max-w-3xl mx-auto bg-white p-8 md:p-14 border border-gray-100 rounded-[3rem] shadow-sm">
                    <div class="flex items-center gap-6 mb-12 border-b border-gray-100 pb-8">
                        <button onclick="cancelReviewForm()" class="p-4 bg-gray-50 rounded-full hover:bg-gray-100 text-gray-600 transition-colors">
                            <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 19l-7-7m0 0l7-7m-7 7h18"></path></svg>
                        </button>
                        <h2 class="text-4xl font-serif text-gray-900">${state.editingReviewId ? 'Edit Review' : 'Add Review'}</h2>
                    </div>

                    <form id="review-form" class="space-y-10">
                        <div class="bg-[#faf8f4] p-8 rounded-[2rem] border border-gray-100 text-center">
                            <label class="block text-xs font-bold tracking-[0.2em] text-gray-400 mb-6 uppercase">Reviewer Photo (optional)</label>
                            <div class="w-28 h-28 mx-auto rounded-full bg-white shadow-sm border border-gray-200 mb-6 overflow-hidden flex items-center justify-center">
                                <img id="review-photo-preview" src="${state.reviewFormData.image || 'IMG_0254.png'}" onerror="this.src='IMG_0254.png'" class="w-full h-full object-cover" />
                            </div>
                            <label class="bg-white px-6 py-3 rounded-full text-xs font-bold uppercase tracking-widest border border-gray-200 cursor-pointer hover:bg-gray-100 shadow-sm inline-block">
                                ${state.isUploadingReview ? 'Compressing...' : 'Upload Photo'}
                                <input id="review-photo-input" type="file" accept="image/*" class="hidden" />
                            </label>
                        </div>

                        <div>
                            <label class="block text-xs font-bold tracking-[0.2em] text-gray-400 mb-3 uppercase">Customer Name</label>
                            <input required id="review-name" type="text" value="${state.reviewFormData.name}" oninput="state.reviewFormData.name=this.value" class="w-full px-6 py-5 bg-gray-50 border border-gray-200 rounded-2xl focus:ring-2 focus:ring-[#10583f]/20 focus:border-[#10583f] transition-all font-medium text-lg" placeholder="e.g. Nusrat Jahan" />
                        </div>

                        <div>
                            <label class="block text-xs font-bold tracking-[0.2em] text-gray-400 mb-3 uppercase">Star Rating</label>
                            <div id="review-star-picker">${renderStarPicker(state.reviewFormData.stars)}</div>
                        </div>

                        <div>
                            <label class="block text-xs font-bold tracking-[0.2em] text-gray-400 mb-3 uppercase">Review Text</label>
                            <textarea required id="review-text" oninput="state.reviewFormData.text=this.value" rows="4" class="w-full px-6 py-5 bg-gray-50 border border-gray-200 rounded-2xl focus:ring-2 focus:ring-[#10583f]/20 focus:border-[#10583f] transition-all resize-none font-medium text-lg leading-relaxed" placeholder="Absolutely loved the bouquet, fresh and elegant...">${state.reviewFormData.text}</textarea>
                        </div>

                        <div class="pt-10 border-t border-gray-100 flex justify-end">
                            <button type="submit" class="premium-btn text-white px-12 py-5 rounded-full font-bold tracking-[0.2em] uppercase text-sm">
                                ${state.editingReviewId ? 'Save Review' : 'Publish Review'}
                            </button>
                        </div>
                    </form>
                </div>
            `;

            const photoInput = document.getElementById('review-photo-input');
            if (photoInput) {
                photoInput.onchange = async (e) => {
                    const file = e.target.files[0];
                    if (!file) return;
                    state.isUploadingReview = true;
                    renderAdminMainSection();
                    try {
                        const compressed = await compressImage(file, 400, 0.85);
                        state.reviewFormData.image = compressed;
                    } catch (err) {
                        alert("Error uploading photo.");
                    }
                    state.isUploadingReview = false;
                    renderAdminMainSection();
                };
            }

            document.getElementById('review-form').onsubmit = async (e) => {
                e.preventDefault();
                state.reviewFormData.name = document.getElementById('review-name').value;
                state.reviewFormData.text = document.getElementById('review-text').value;

                if (state.editingReviewId) {
                    state.reviews = state.reviews.map(r => r.id === state.editingReviewId ? { ...state.reviewFormData, id: state.editingReviewId } : r);
                } else {
                    state.reviews = [{ ...state.reviewFormData, id: Date.now().toString() }, ...state.reviews];
                }

                await dbSet('tf_reviews_v3', state.reviews);
                state.isAddingReview = false;
                state.editingReviewId = null;
                renderAdminMainSection();
            };
        }

        function setReviewStars(n) {
            state.reviewFormData.stars = n;
            const picker = document.getElementById('review-star-picker');
            if (picker) picker.innerHTML = renderStarPicker(n);
        }

        function openNewReviewForm() {
            state.reviewFormData = { name: '', stars: 5, text: '', image: '' };
            state.editingReviewId = null;
            state.isAddingReview = true;
            renderAdminMainSection();
        }

        function cancelReviewForm() {
            state.isAddingReview = false;
            state.editingReviewId = null;
            renderAdminMainSection();
        }

        async function editReview(id) {
            const r = state.reviews.find(item => item.id === id);
            if (r) {
                state.reviewFormData = { ...r };
                state.editingReviewId = id;
                state.isAddingReview = true;
                renderAdminMainSection();
            }
        }

        async function deleteReview(id) {
            if (confirm("Delete this review permanently?")) {
                state.reviews = state.reviews.filter(r => r.id !== id);
                await dbSet('tf_reviews_v3', state.reviews);
                renderAdminMainSection();
            }
        }

        // ==========================================
        // 13. ADMIN: BRAND SETTINGS PANEL
        // ==========================================
        function renderSettingsPanel(container) {
            container.innerHTML = `
                <div class="animate-fade-up max-w-4xl mx-auto">
                    <div class="mb-10">
                        <h1 class="text-4xl font-serif text-gray-900 mb-2">Brand Settings</h1>
                        <p class="text-gray-500 font-light">Tailor your high-end brand assets and slogans dynamically.</p>
                    </div>

                    <div class="bg-white p-10 md:p-14 border border-gray-100 rounded-[3rem] shadow-sm space-y-14">

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

                        <form id="settings-form" class="space-y-8">
                            <div>
                                <h3 class="text-2xl font-serif text-gray-900 mb-8 border-b border-gray-100 pb-4">Messaging</h3>
                                <div class="space-y-6">
                                    <div>
                                        <label class="block text-xs font-bold tracking-[0.2em] text-gray-400 mb-3 uppercase">Main Slogan</label>
                                        <input required id="sett-slogan" type="text" value="${state.settings.heroSlogan}" class="w-full px-6 py-5 bg-gray-50 border border-gray-200 rounded-2xl focus:border-[#10583f] font-medium text-lg" />
                                    </div>
                                    <div>
                                        <label class="block text-xs font-bold tracking-[0.2em] text-gray-400 mb-3 uppercase">Description</label>
                                        <textarea required id="sett-desc" rows="3" class="w-full px-6 py-5 bg-gray-50 border border-gray-200 rounded-2xl focus:border-[#10583f] font-medium text-lg leading-relaxed">${state.settings.heroDesc}</textarea>
                                    </div>
                                    <div>
                                        <label class="block text-xs font-bold tracking-[0.2em] text-gray-400 mb-3 uppercase">Delivery Badge Text</label>
                                        <input id="sett-delivery" type="text" value="${state.settings.deliveryText || ''}" class="w-full px-6 py-5 bg-gray-50 border border-gray-200 rounded-2xl focus:border-[#10583f] font-medium text-lg" placeholder="⚡ 3-Hour Delivery Available in Dhaka" />
                                    </div>
                                </div>
                            </div>

                            <div>
                                <h3 class="text-2xl font-serif text-gray-900 mb-8 border-b border-gray-100 pb-4">Contacts</h3>
                                <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                                    <div>
                                        <label class="block text-xs font-bold tracking-[0.2em] text-gray-400 mb-3 uppercase">WhatsApp</label>
                                        <input required id="sett-whatsapp" type="text" value="${state.settings.whatsapp}" class="w-full px-6 py-5 bg-gray-50 border border-gray-200 rounded-2xl font-bold text-lg" />
                                    </div>
                                    <div>
                                        <label class="block text-xs font-bold tracking-[0.2em] text-gray-400 mb-3 uppercase">Phone</label>
                                        <input required id="sett-phone" type="text" value="${state.settings.phone}" class="w-full px-6 py-5 bg-gray-50 border border-gray-200 rounded-2xl font-bold text-lg" />
                                    </div>
                                    <div class="md:col-span-2">
                                        <label class="block text-xs font-bold tracking-[0.2em] text-gray-400 mb-3 uppercase">Instagram</label>
                                        <input required id="sett-instagram" type="text" value="${state.settings.instagram}" class="w-full px-6 py-5 bg-gray-50 border border-gray-200 rounded-2xl font-medium text-lg" />
                                    </div>
                                    <div>
                                        <label class="block text-xs font-bold tracking-[0.2em] text-gray-400 mb-3 uppercase">TikTok</label>
                                        <input id="sett-tiktok" type="text" value="${state.settings.tiktok || ''}" class="w-full px-6 py-5 bg-gray-50 border border-gray-200 rounded-2xl font-medium text-lg" />
                                    </div>
                                    <div>
                                        <label class="block text-xs font-bold tracking-[0.2em] text-gray-400 mb-3 uppercase">Facebook Page</label>
                                        <input id="sett-facebook" type="text" value="${state.settings.facebook || ''}" class="w-full px-6 py-5 bg-gray-50 border border-gray-200 rounded-2xl font-medium text-lg" />
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

            document.getElementById('settings-form').onsubmit = async (e) => {
                e.preventDefault();
                state.settings.heroSlogan = document.getElementById('sett-slogan').value;
                state.settings.heroDesc = document.getElementById('sett-desc').value;
                state.settings.deliveryText = document.getElementById('sett-delivery').value;
                state.settings.whatsapp = document.getElementById('sett-whatsapp').value;
                state.settings.phone = document.getElementById('sett-phone').value;
                state.settings.instagram = document.getElementById('sett-instagram').value;
                state.settings.tiktok = document.getElementById('sett-tiktok').value;
                state.settings.facebook = document.getElementById('sett-facebook').value;

                await dbSet('tf_settings_v3', state.settings);
                alert("Settings Saved Successfully!");
                updateView();
            };
        }

        // ==========================================
        // 14. SYSTEM BOOTSTRAP (Initialization)
        // ==========================================
        function hideLoader() {
            const loader = document.getElementById('loader-screen');
            if (loader) loader.classList.add('opacity-0', 'pointer-events-none');
        }

        function bootstrap() {
            if (typeof window.__firebaseOnValue !== 'function') {
                console.error('Firebase did not load — showing default content only.');
                hideLoader();
                updateView();
                return;
            }

            const firstLoad = { bouquets: false, categories: false, settings: false, reviews: false };
            function markFirstLoad(key) {
                if (firstLoad[key]) return;
                firstLoad[key] = true;
                if (firstLoad.bouquets && firstLoad.categories && firstLoad.settings && firstLoad.reviews) hideLoader();
            }

            window.__firebaseOnValue('tf_bouquets_v3', (val) => {
                state.bouquets = val || [];
                markFirstLoad('bouquets');
                updateView();
            });
            window.__firebaseOnValue('tf_categories_v3', (val) => {
                if (val) state.categories = val;
                markFirstLoad('categories');
                updateView();
            });
            window.__firebaseOnValue('tf_settings_v3', (val) => {
                if (val) state.settings = { ...state.settings, ...val };
                markFirstLoad('settings');
                updateView();
            });
            window.__firebaseOnValue('tf_reviews_v3', (val) => {
                state.reviews = val || [];
                markFirstLoad('reviews');
                updateView();
            });

            setTimeout(hideLoader, 8000);
        }

        window.onload = () => { bootstrap(); };
    </script>

    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/12.15.0/firebase-app.js";
        import { getDatabase, ref, set, onValue } from "https://www.gstatic.com/firebasejs/12.15.0/firebase-database.js";
        import { getAnalytics } from "https://www.gstatic.com/firebasejs/12.15.0/firebase-analytics.js";

        const firebaseConfig = {
          apiKey: "AIzaSyAereTM0WIEvfWEI7x3tLCyuv7RK23FLF4",
          authDomain: "tatka3056-d9c8d.firebaseapp.com",
          databaseURL: "https://tatka3056-d9c8d-default-rtdb.firebaseio.com",
          projectId: "tatka3056-d9c8d",
          storageBucket: "tatka3056-d9c8d.firebasestorage.app",
          messagingSenderId: "484843738326",
          appId: "1:484843738326:web:ecac79b1ebffe98ebbe577",
          measurementId: "G-NNLT4QZQEQ"
        };

        try {
            const fbApp = initializeApp(firebaseConfig);
            const analytics = getAnalytics(fbApp);
            const db = getDatabase(fbApp);

            window.__firebaseSetPath = (path, value) => set(ref(db, path), value);
            window.__firebaseOnValue = (path, callback) => {
                onValue(ref(db, path), (snapshot) => {
                    callback(snapshot.exists() ? snapshot.val() : null);
                }, (error) => {
                    console.error('Firebase sync error on "' + path + '":', error);
                });
            };
        } catch (err) {
            console.error('Firebase failed to initialize — check firebaseConfig.', err);
        }
    </script>
</body>
</html>
