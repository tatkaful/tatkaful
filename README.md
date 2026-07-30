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
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
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
            -webkit-tap-highlight-color: transparent;
        }

        .glass-header {
            background: rgba(250, 248, 244, 0.88);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border-bottom: 1px solid rgba(11, 46, 34, 0.05);
        }

        .luxury-card {
            background: #ffffff;
            border: 1px solid rgba(11, 46, 34, 0.06);
            box-shadow: 0 15px 35px -10px rgba(11, 46, 34, 0.06);
            transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
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
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .animate-fade-up { animation: fadeUp 0.5s cubic-bezier(0.16, 1, 0.3, 1) forwards; }

        input:focus, textarea:focus, select:focus { outline: none; }

        .price-old { color: #a3a3a3; text-decoration: line-through; font-weight: 500; }
        .price-current { color: var(--emerald); font-weight: 800; }
        .discount-pill { background: linear-gradient(135deg, var(--gold-deep), var(--gold)); color: #fff; font-weight: 700; letter-spacing: 0.05em; }
    </style>
</head>
<body class="text-gray-800 antialiased selection:bg-[#10583f] selection:text-white">

    <div id="app-root" class="min-h-screen flex flex-col"></div>
    <div id="modal-container"></div>

    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getDatabase, ref, onValue } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-database.js";

        // --- FIREBASE CONFIGURATION ---
        const firebaseConfig = {
            apiKey: "AIzaSyAufJDfUyVtIDYkKULmtEtFHY6FJBwI_RQ",
            authDomain: "taktaful.firebaseapp.com",
            databaseURL: "https://taktaful-default-rtdb.asia-southeast1.firebasedatabase.app",
            projectId: "taktaful",
            storageBucket: "taktaful.firebasestorage.app",
            messagingSenderId: "79913462603",
            appId: "1:79913462603:web:45cf414a6601292f1956ce",
            measurementId: "G-76F4T17ML3"
        };

        const app = initializeApp(firebaseConfig);
        const db = getDatabase(app);

        const LOCAL_STORAGE_KEY = 'tatkaful_cached_data_v2';

        const defaultState = {
            searchQuery: '',
            selectedBouquet: null,
            bouquets: [
                { id: '1', name: 'Royal Crimson', description: 'Deep red premium roses hand-tied with elegant greenery.', images: ['https://placehold.co/800x1000/10583f/ffffff?text=Royal+Crimson'], bestseller: true, visible: true, currentPrice: '1200', oldPrice: '1500', position: 1 },
                { id: '2', name: 'Morning Dew', description: 'Fresh white lilies and soft pink tulips.', images: ['https://placehold.co/800x1000/c8a13a/ffffff?text=Morning+Dew'], bestseller: false, visible: true, currentPrice: '850', position: 2 }
            ],
            reviews: [
                { id: 'r1', name: 'Nusrat Jahan', stars: 5, text: 'Absolutely loved the bouquet, fresh and elegant. The delivery was right on time!', image: 'https://placehold.co/400x400/eeeeee/333333?text=NJ' }
            ],
            settings: {
                logo: 'https://placehold.co/400x400/10583f/ffffff?text=TF',
                banner: 'https://placehold.co/1200x600/faf8f4/10583f?text=Luxury+Floral+Design',
                phone: '01410619501',
                whatsapp: '01410619501',
                instagram: 'https://instagram.com/tatka_ful',
                tiktok: 'https://tiktok.com/@tatka.ful',
                facebook: 'https://facebook.com/tatkaful',
                heroSlogan: 'Elegance in Every Petal.',
                heroDesc: 'Curating luxury floral masterpieces for your most precious memories. Exclusively hand-crafted with passion.',
                deliveryText: '⚡ 3-Hour Delivery Available in Dhaka'
            }
        };

        // Load cached state immediately for 0ms cold start
        let state = loadFromCache() || defaultState;

        function loadFromCache() {
            try {
                const cached = localStorage.getItem(LOCAL_STORAGE_KEY);
                if (cached) return JSON.parse(cached);
            } catch (e) {
                console.warn('Cache load failed:', e);
            }
            return null;
        }

        function saveToCache(data) {
            try {
                localStorage.setItem(LOCAL_STORAGE_KEY, JSON.stringify(data));
            } catch (e) {
                console.warn('Cache save failed:', e);
            }
        }

        const storeRef = ref(db, 'tatkaful_store_data');
        onValue(storeRef, (snapshot) => {
            const cloudData = snapshot.val();
            if (cloudData) {
                if (cloudData.bouquets) state.bouquets = cloudData.bouquets;
                if (cloudData.reviews) state.reviews = cloudData.reviews;
                if (cloudData.settings) state.settings = { ...state.settings, ...cloudData.settings };
                
                // Cache updated cloud state
                saveToCache({
                    bouquets: state.bouquets,
                    reviews: state.reviews,
                    settings: state.settings
                });

                // Re-render immediately on backend changes
                renderHome();
            }
        }, (error) => {
            console.log('Firebase sync note:', error.message);
        });

        window.formatWhatsApp = function(number) {
            let formatted = (number || '').replace(/[^0-9]/g, '');
            if (formatted.startsWith('0')) formatted = '88' + formatted;
            return formatted;
        };

        window.starGlyphs = function(count) {
            let out = '';
            for (let i = 1; i <= 5; i++) {
                out += `<span class="${i <= count ? 'text-[#c8a13a]' : 'text-gray-200'} text-base leading-none">★</span>`;
            }
            return out;
        };

        window.renderPriceHTML = function(bouquet, size = 'card') {
            const hasOld = bouquet.oldPrice !== undefined && bouquet.oldPrice !== null && bouquet.oldPrice !== '';
            const hasCurrent = bouquet.currentPrice !== undefined && bouquet.currentPrice !== null && bouquet.currentPrice !== '';
            if (!hasOld && !hasCurrent) return '';
            let discountPct = null;
            if (hasOld && hasCurrent && Number(bouquet.oldPrice) > Number(bouquet.currentPrice) && Number(bouquet.oldPrice) > 0) {
                discountPct = Math.round((1 - (Number(bouquet.currentPrice) / Number(bouquet.oldPrice))) * 100);
            }
            const currentSize = size === 'modal' ? 'text-3xl md:text-4xl' : 'text-lg sm:text-xl';
            const oldSize = size === 'modal' ? 'text-base' : 'text-xs sm:text-sm';
            return `
                <div class="flex items-center flex-wrap gap-2 sm:gap-3 ${size === 'modal' ? 'mb-6' : 'mb-2 sm:mb-3'}">
                    ${hasCurrent ? `<span class="price-current font-serif ${currentSize}">৳${bouquet.currentPrice}</span>` : ''}
                    ${hasOld ? `<span class="price-old ${oldSize}">৳${bouquet.oldPrice}</span>` : ''}
                    ${discountPct && discountPct > 0 ? `<span class="discount-pill text-[9px] sm:text-[10px] px-2 py-1 rounded-full uppercase">${discountPct}% Off</span>` : ''}
                </div>
            `;
        };

        window.orderViaWhatsApp = function(bouquetId, event) {
            if (event) event.stopPropagation();
            const bouquet = state.bouquets.find(b => b.id === bouquetId);
            if (!bouquet) return;

            if (bouquet.images && bouquet.images[0]) {
                try {
                    const link = document.createElement('a');
                    link.href = bouquet.images[0];
                    link.download = `TatkaFul-${(bouquet.name || 'Design').replace(/[^a-zA-Z0-9]+/g, '-')}.jpg`;
                    document.body.appendChild(link);
                    link.click();
                    document.body.removeChild(link);
                } catch (err) {
                    console.error('Auto-download of bouquet photo failed:', err);
                }
            }

            const priceNote = bouquet.currentPrice ? ` (৳${bouquet.currentPrice})` : '';
            const message = `Hello Tatka Ful! 🌸 I would love to order the premium "${bouquet.name || 'Bouquet'}" design${priceNote}.\n(📷 Photo saved on my device — attaching it here!)`;
            const url = `https://wa.me/${window.formatWhatsApp(state.settings.whatsapp)}?text=${encodeURIComponent(message)}`;
            window.open(url, '_blank', 'noreferrer');
        };

        function sortByPosition(list) {
            return [...list].sort((a, b) => {
                const pa = (a.position === '' || a.position === undefined || a.position === null || isNaN(Number(a.position))) ? Number.POSITIVE_INFINITY : Number(a.position);
                const pb = (b.position === '' || b.position === undefined || b.position === null || isNaN(Number(b.position))) ? Number.POSITIVE_INFINITY : Number(b.position);
                if (pa !== pb) return pa - pb;
                return String(a.id).localeCompare(String(b.id));
            });
        }

        function computeFilteredBouquets() {
            const visibleBouquets = (state.bouquets || []).filter(b => b.visible !== false);
            let list = visibleBouquets;
            const q = (state.searchQuery || '').trim().toLowerCase();
            if (q) {
                list = list.filter(b =>
                    (b.name || '').toLowerCase().includes(q) ||
                    (b.description || '').toLowerCase().includes(q)
                );
            }
            return sortByPosition(list);
        }

        function renderBouquetGridHTML(displayedBouquets) {
            if (displayedBouquets.length === 0) {
                return `
                    <div class="text-center py-20 sm:py-28 luxury-card rounded-[2rem] sm:rounded-[3rem] animate-fade-up">
                        <div class="w-16 h-16 sm:w-20 sm:h-20 bg-[#eaf6f0] rounded-full flex items-center justify-center mx-auto mb-6">
                            <svg class="w-8 h-8 sm:w-10 sm:h-10 text-[#10583f]" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M4 16l4.586-4.586a2 2 0 012.828 0L16 16m-2-2l1.586-1.586a2 2 0 012.828 0L20 14m-6-6h.01M6 20h12a2 2 0 002-2V6a2 2 0 00-2-2H6a2 2 0 00-2 2v12a2 2 0 002 2z"></path></svg>
                        </div>
                        <h3 class="text-2xl sm:text-3xl font-serif text-gray-900 mb-3">${state.searchQuery ? 'No matching designs found' : 'Collection is empty'}</h3>
                        <p class="text-gray-500 font-light text-base sm:text-lg px-6">${state.searchQuery ? 'Try a different search term.' : 'Our designers are currently building premium designs.'}</p>
                    </div>
                `;
            }
            return `
                <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-x-3 sm:gap-x-6 md:gap-x-10 gap-y-6 sm:gap-y-10 md:gap-y-16">
                    ${displayedBouquets.map((bouquet, index) => `
                        <div class="group cursor-pointer flex flex-col animate-fade-up" style="animation-delay: ${Math.min(index, 8) * 0.04}s" onclick="openDetailModal('${bouquet.id}')">
                            <div class="relative aspect-[4/5] rounded-[1.25rem] sm:rounded-[2rem] overflow-hidden luxury-card mb-3 sm:mb-6">
                                ${bouquet.images && bouquet.images.length > 0 ? `
                                    <img src="${bouquet.images[0]}" alt="${bouquet.name || 'Bouquet'}" loading="lazy" class="w-full h-full object-cover transition-transform duration-700 group-hover:scale-105" />
                                ` : `
                                    <div class="w-full h-full flex items-center justify-center bg-gray-50 text-gray-300 text-xs">No Image</div>
                                `}
                                <div class="absolute inset-0 bg-gradient-to-t from-black/30 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
                                ${bouquet.bestseller ? `
                                    <div class="absolute top-2 left-2 sm:top-4 sm:left-4 bg-white/95 backdrop-blur-md text-[#9c7a1f] text-[8px] sm:text-[10px] font-bold uppercase tracking-[0.15em] sm:tracking-[0.2em] px-2 sm:px-3 py-1 sm:py-1.5 rounded-full flex items-center gap-1.5 shadow-md">
                                        <span class="w-1.5 h-1.5 bg-[#c8a13a] rounded-full"></span> Signature
                                    </div>
                                ` : ''}
                            </div>
                            <div class="px-1 sm:px-2 flex flex-col flex-1">
                                <h3 class="text-sm sm:text-2xl font-serif text-gray-900 mb-1 sm:mb-2 group-hover:text-[#10583f] transition-colors leading-tight">${bouquet.name || 'Fresh Bouquet'}</h3>
                                ${window.renderPriceHTML(bouquet, 'card')}
                                ${bouquet.description ? `<p class="hidden sm:block text-gray-500 text-sm line-clamp-2 leading-relaxed font-light mb-4">${bouquet.description}</p>` : `<div class="hidden sm:block mb-4"></div>`}
                                <button onclick="orderViaWhatsApp('${bouquet.id}', event)" class="mt-auto premium-btn text-white text-[10px] sm:text-xs font-bold uppercase tracking-[0.12em] sm:tracking-[0.2em] py-2 sm:py-3.5 rounded-full flex items-center justify-center gap-1.5 sm:gap-2">
                                    <svg class="w-3.5 h-3.5 sm:w-4 sm:h-4" fill="currentColor" viewBox="0 0 24 24"><path d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946C.06 5.348 5.397.01 12.008.01c3.202.001 6.212 1.246 8.477 3.514 2.266 2.268 3.507 5.28 3.505 8.484-.004 6.657-5.34 11.997-11.953 11.997-2.005-.001-3.973-.502-5.713-1.455L0 24zm6.59-4.846c1.6.95 3.188 1.449 4.625 1.451 5.436 0 9.851-4.398 9.854-9.807.001-2.621-1.013-5.086-2.86-6.935C16.36 1.913 13.9.894 11.285.894c-5.438 0-9.854 4.398-9.858 9.808 0 2.037.533 4.024 1.547 5.765l-.99 3.613 3.73-.973h.001a9.78 9.78 0 0 0 4.332 1.048z"/></svg>
                                    <span class="sm:hidden">Order</span>
                                    <span class="hidden sm:inline">Order Now</span>
                                </button>
                            </div>
                        </div>
                    `).join('')}
                </div>
            `;
        }

        window.refreshCollection = function() {
            const gridWrap = document.getElementById('bouquet-grid-wrapper');
            if (gridWrap) gridWrap.innerHTML = renderBouquetGridHTML(computeFilteredBouquets());
        };

        window.handleSearchInput = function(value) {
            state.searchQuery = value;
            window.refreshCollection();
        };

        function renderReviewsSectionHTML() {
            if (!state.reviews || state.reviews.length === 0) return '';
            return `
                <section class="px-6 py-16 sm:py-24 max-w-7xl mx-auto">
                    <div class="text-center mb-12 sm:mb-16">
                        <span class="eyebrow-flourish">Client Stories</span>
                        <h2 class="text-3xl sm:text-5xl font-serif text-gray-900 mt-4">What Our Clients Say</h2>
                    </div>
                    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6 sm:gap-8">
                        ${state.reviews.map((r, i) => `
                            <div class="luxury-card rounded-[2rem] p-6 sm:p-8 flex flex-col animate-fade-up" style="animation-delay:${Math.min(i, 8) * 0.05}s">
                                <svg class="w-8 h-8 text-[#f6ecd2] mb-3" fill="currentColor" viewBox="0 0 24 24"><path d="M9.983 3v7.391c0 5.704-3.731 9.57-8.983 10.609l-.995-2.151c2.432-.917 3.995-3.638 3.995-5.849h-4v-10h9.983zm14.017 0v7.391c0 5.704-3.748 9.571-9 10.609l-.996-2.151c2.433-.917 3.996-3.638 3.996-5.849h-3.983v-10h9.983z"/></svg>
                                <div class="flex gap-1 mb-3">${window.starGlyphs(r.stars || 5)}</div>
                                <p class="text-gray-600 italic font-light mb-6 leading-relaxed flex-1 text-sm sm:text-base">${r.text}</p>
                                <div class="mt-auto flex items-center gap-3 pt-4 border-t border-gray-50">
                                    <img src="${r.image || state.settings.logo}" onerror="this.src='https://placehold.co/100x100/10583f/ffffff'" class="w-10 h-10 rounded-full object-cover border border-gray-100" />
                                    <span class="font-serif text-base text-gray-900 font-semibold">${r.name}</span>
                                </div>
                            </div>
                        `).join('')}
                    </div>
                </section>
            `;
        }

        window.renderHome = function() {
            const container = document.getElementById('app-root');
            if (!container) return;

            container.innerHTML = `
                <nav class="fixed w-full top-0 z-40 glass-header">
                    <div class="max-w-7xl mx-auto px-4 sm:px-6 h-20 sm:h-24 flex items-center justify-between">
                        <div class="flex items-center gap-3 sm:gap-4 cursor-pointer group" onclick="window.scrollTo({top:0, behavior:'smooth'})">
                            <img src="${state.settings.logo}" onerror="this.src='https://placehold.co/100x100/10583f/ffffff'" alt="Tatka Ful Logo" class="w-11 h-11 sm:w-14 sm:h-14 rounded-full object-cover shadow-sm group-hover:scale-105 transition-transform duration-500" />
                            <span class="text-xl sm:text-2xl font-serif font-semibold text-gray-900 tracking-wide group-hover:text-[#10583f] transition-colors">Tatka Ful</span>
                        </div>
                        <div class="flex items-center gap-4 sm:gap-10">
                            <a href="#collection" class="hidden md:inline text-sm font-semibold tracking-widest uppercase text-gray-500 hover:text-[#10583f] transition-colors">Collections</a>
                            <a href="https://wa.me/${window.formatWhatsApp(state.settings.whatsapp)}" target="_blank" rel="noreferrer" class="premium-btn text-white px-5 sm:px-8 py-2.5 sm:py-3.5 rounded-full tracking-widest text-[10px] sm:text-xs font-bold uppercase">
                                Inquire Now
                            </a>
                        </div>
                    </div>
                </nav>

                <section class="relative pt-28 pb-16 md:pt-48 md:pb-32 px-6 flex items-center justify-center min-h-[70vh] overflow-hidden">
                    <div class="orb w-[22rem] sm:w-[28rem] h-[22rem] sm:h-[28rem] bg-[#10583f]/10 -top-20 -left-20"></div>
                    <div class="orb w-[18rem] sm:w-[24rem] h-[18rem] sm:h-[24rem] bg-[#c8a13a]/15 top-32 -right-10"></div>
                    <div class="absolute inset-0 z-0">
                        <img src="${state.settings.banner}" onerror="this.src='https://placehold.co/1200x600/faf8f4/10583f'" alt="Luxury Floral Banner" class="w-full h-full object-cover opacity-20 scale-105" />
                        <div class="absolute inset-0 bg-gradient-to-b from-[#faf8f4]/90 via-[#faf8f4]/70 to-[#faf8f4]"></div>
                    </div>

                    <div class="max-w-4xl mx-auto text-center relative z-10 animate-fade-up">
                        <span class="eyebrow-flourish">Premium Floral Design</span>
                        <h1 class="text-3xl sm:text-7xl lg:text-8xl font-serif text-gray-900 mt-5 mb-6 sm:mb-8 leading-[1.15] tracking-tight">
                            ${state.settings.heroSlogan || 'Elegance in Every Petal.'}
                        </h1>
                        <p class="text-sm sm:text-xl text-gray-600 mb-6 sm:mb-8 max-w-2xl mx-auto font-light leading-relaxed">
                            ${state.settings.heroDesc || 'Curating luxury floral masterpieces for your most precious memories.'}
                        </p>
                        ${state.settings.deliveryText ? `
                        <div class="inline-flex items-center gap-2 bg-white/80 backdrop-blur-md border border-[#c8a13a]/30 rounded-full px-4 sm:px-6 py-2 sm:py-3 mb-8 shadow-sm">
                            <span class="text-xs sm:text-sm font-bold tracking-[0.12em] uppercase text-[#0b2e22]">${state.settings.deliveryText}</span>
                        </div>` : ''}
                        <div>
                        <a href="#collection" class="inline-flex items-center gap-2 sm:gap-3 premium-btn text-white px-8 sm:px-10 py-3.5 sm:py-5 rounded-full text-xs sm:text-sm uppercase tracking-widest font-semibold">
                            View Gallery
                            <svg class="w-4 h-4 sm:w-5 sm:h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"></path></svg>
                        </a>
                        </div>
                    </div>
                </section>

                <section id="collection" class="px-4 sm:px-6 py-4 sm:py-6 sticky top-20 sm:top-24 glass-header z-30 shadow-sm border-t border-gray-100">
                    <div class="max-w-7xl mx-auto">
                        <div class="relative max-w-xl w-full mx-auto">
                            <svg class="w-4 h-4 sm:w-5 sm:h-5 text-gray-400 absolute left-4 sm:left-5 top-1/2 -translate-y-1/2 pointer-events-none" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-4.35-4.35M11 19a8 8 0 100-16 8 8 0 000 16z"></path></svg>
                            <input id="search-input" type="text" value="${state.searchQuery}" oninput="handleSearchInput(this.value)" placeholder="Search bouquets by name..." class="w-full pl-10 sm:pl-12 pr-4 sm:pr-5 py-2.5 sm:py-3.5 bg-white border border-gray-200 rounded-full text-xs sm:text-sm font-medium focus:border-[#10583f] focus:ring-2 focus:ring-[#10583f]/10 transition-all placeholder:text-gray-400" />
                        </div>
                    </div>
                </section>

                <section class="px-4 sm:px-6 py-12 sm:py-20 max-w-7xl mx-auto min-h-[40vh]">
                    <div id="bouquet-grid-wrapper">
                        ${renderBouquetGridHTML(computeFilteredBouquets())}
                    </div>
                </section>

                ${renderReviewsSectionHTML()}

                <div class="fixed bottom-5 right-5 z-40 flex flex-col gap-3">
                    <a href="https://wa.me/${window.formatWhatsApp(state.settings.whatsapp)}" target="_blank" rel="noreferrer" class="relative w-14 h-14 sm:w-16 sm:h-16 bg-[#25D366] text-white rounded-full flex items-center justify-center hover:scale-105 transition-transform shadow-[0_10px_30px_rgba(37,211,102,0.4)]">
                        <span class="absolute inline-flex h-full w-full rounded-full bg-[#25D366] opacity-40 animate-ping"></span>
                        <svg class="w-7 h-7 sm:w-8 sm:h-8 relative z-10" fill="currentColor" viewBox="0 0 24 24"><path d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946C.06 5.348 5.397.01 12.008.01c3.202.001 6.212 1.246 8.477 3.514 2.266 2.268 3.507 5.28 3.505 8.484-.004 6.657-5.34 11.997-11.953 11.997-2.005-.001-3.973-.502-5.713-1.455L0 24zm6.59-4.846c1.6.95 3.188 1.449 4.625 1.451 5.436 0 9.851-4.398 9.854-9.807.001-2.621-1.013-5.086-2.86-6.935C16.36 1.913 13.9.894 11.285.894c-5.438 0-9.854 4.398-9.858 9.808 0 2.037.533 4.024 1.547 5.765l-.99 3.613 3.73-.973h.001a9.78 9.78 0 0 0 4.332 1.048zM18.15 14.86c-.337-.168-1.996-.983-2.305-1.096-.309-.113-.534-.168-.758.168-.225.337-.871 1.096-1.067 1.32-.197.225-.393.253-.73.084-.337-.168-1.42-.524-2.707-1.671-1.002-.894-1.679-2.001-1.875-2.337-.197-.337-.021-.519.147-.687.152-.151.337-.393.506-.59.168-.197.225-.337.337-.562.113-.225.056-.422-.028-.59-.084-.168-.758-1.825-1.039-2.503-.274-.662-.553-.573-.758-.583-.197-.01-.422-.012-.647-.012-.225 0-.59.084-.9.422-.309.337-1.18 1.151-1.18 2.808 0 1.657 1.208 3.257 1.377 3.482.168.225 2.378 3.63 5.76 5.087.805.347 1.433.554 1.923.71.808.257 1.545.221 2.127.135.649-.096 1.996-.815 2.277-1.601.281-.787.281-1.461.197-1.601-.084-.14-.309-.225-.647-.393z"/></svg>
                    </a>
                </div>

                <footer class="bg-white border-t border-gray-100 pt-16 sm:pt-20 pb-10 px-6">
                    <div class="max-w-7xl mx-auto flex flex-col md:flex-row justify-between items-center gap-10 text-center md:text-left">
                        <div class="flex flex-col items-center md:items-start max-w-sm">
                            <img src="${state.settings.logo}" onerror="this.src='https://placehold.co/100x100/10583f/ffffff'" alt="Logo" class="w-16 h-16 rounded-full mb-4 shadow-sm object-cover" />
                            <h3 class="font-serif text-2xl sm:text-3xl text-gray-900 mb-3">Tatka Ful</h3>
                            <p class="text-gray-500 text-xs sm:text-sm leading-relaxed font-light">
                                Nature's finest expressions of love, premium flower concepts curated flawlessly.
                            </p>
                        </div>
                        <div class="flex flex-col items-center md:items-end">
                            <p class="text-xs font-bold tracking-[0.2em] text-gray-400 uppercase mb-4">Studio Connections</p>
                            <div class="flex gap-3 sm:gap-4">
                                <a href="${state.settings.instagram}" target="_blank" rel="noreferrer" class="social-badge">
                                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 9a2 2 0 012-2h.93a2 2 0 001.664-.89l.812-1.22A2 2 0 0110.07 4h3.86a2 2 0 011.664.89l.812 1.22A2 2 0 0018.07 7H19a2 2 0 012 2v9a2 2 0 01-2 2H5a2 2 0 01-2-2V9z"></path><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 13a3 3 0 11-6 0 3 3 0 016 0z"></path></svg>
                                </a>
                                ${state.settings.facebook ? `
                                <a href="${state.settings.facebook}" target="_blank" rel="noreferrer" class="social-badge">
                                    <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M14 13.5h2.5l.5-3H14V8.5c0-.75.25-1.5 1.5-1.5H17V4.5c-.5 0-1.5-.1-2.5-.1-2.5 0-4 1.5-4 4.5V10.5H8v3h2.5V21h3.5v-7.5z"></path></svg>
                                </a>` : ''}
                                ${state.settings.tiktok ? `
                                <a href="${state.settings.tiktok}" target="_blank" rel="noreferrer" class="social-badge">
                                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 18V5l12-2v13M9 18a3 3 0 11-6 0 3 3 0 016 0zm12-2a3 3 0 11-6 0 3 3 0 016 0z"></path></svg>
                                </a>` : ''}
                                <a href="tel:${state.settings.phone}" class="social-badge">
                                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.94.725l.548 2.2a1 1 0 01-.321.988l-1.305.98a10.582 10.582 0 004.872 4.872l.98-1.305a1 1 0 01.988-.321l2.2.548a1 1 0 01.725.94V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"></path></svg>
                                </a>
                            </div>
                        </div>
                    </div>
                    <div class="max-w-7xl mx-auto mt-12 pt-6 border-t border-gray-100 text-center">
                        <p class="text-[10px] font-semibold tracking-[0.2em] uppercase text-gray-400 select-none">
                            &copy; 2026 Tatka Ful. Crafted with elegance.
                        </p>
                    </div>
                </footer>
            `;

            if (state.selectedBouquet) {
                renderDetailModal();
            }
        };

        window.openDetailModal = function(id) {
            const bouquet = state.bouquets.find(b => b.id === id);
            if (bouquet) {
                state.selectedBouquet = bouquet;
                renderDetailModal();
            }
        };

        window.closeDetailModal = function() {
            state.selectedBouquet = null;
            const container = document.getElementById('modal-container');
            if (container) container.innerHTML = '';
        };

        function renderDetailModal() {
            const bouquet = state.selectedBouquet;
            const container = document.getElementById('modal-container');
            if (!container) return;

            container.innerHTML = `
                <div class="fixed inset-0 z-50 flex items-center justify-center p-0 md:p-8">
                    <div class="absolute inset-0 bg-black/60 backdrop-blur-md transition-opacity" onclick="closeDetailModal()"></div>
                    <div class="relative bg-white w-full h-full md:h-auto md:max-h-[90vh] md:max-w-5xl md:rounded-[2rem] shadow-2xl overflow-hidden flex flex-col md:flex-row animate-fade-up">

                        <button onclick="closeDetailModal()" class="absolute top-4 right-4 z-20 w-10 h-10 bg-white/90 backdrop-blur-md rounded-full flex items-center justify-center text-gray-900 hover:bg-gray-100 transition-colors shadow-lg">
                            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path></svg>
                        </button>

                        <div class="w-full md:w-1/2 bg-[#faf8f4] h-[45vh] md:h-auto overflow-y-auto snap-y snap-mandatory scrollbar-hide relative">
                            ${bouquet.images && bouquet.images.length > 0 ? bouquet.images.map((img, i) => `
                                <div class="w-full h-full min-h-[45vh] md:min-h-full snap-center relative">
                                    <img src="${img}" alt="${bouquet.name || 'Bouquet'} ${i+1}" class="w-full h-full object-cover" />
                                </div>
                            `).join('') : `
                                <div class="w-full h-full flex items-center justify-center text-gray-300 font-light">No Gallery Images</div>
                            `}
                            ${bouquet.images && bouquet.images.length > 1 ? `
                                <div class="absolute bottom-4 left-0 right-0 flex justify-center gap-2 pointer-events-none">
                                    <span class="bg-black/40 backdrop-blur-md text-white text-[9px] tracking-wider px-3 py-1.5 rounded-full uppercase font-semibold">Scroll for details</span>
                                </div>
                            ` : ''}
                        </div>

                        <div class="w-full md:w-1/2 p-6 md:p-12 flex flex-col h-[55vh] md:h-auto overflow-y-auto bg-white">
                            <h2 class="text-2xl md:text-4xl font-serif text-gray-900 mb-3 leading-tight">${bouquet.name || 'Fresh Bouquet'}</h2>
                            ${window.renderPriceHTML(bouquet, 'modal')}
                            <div class="gold-divider mb-6"></div>
                            ${bouquet.description ? `<p class="text-gray-600 leading-relaxed mb-8 font-light text-sm md:text-base">${bouquet.description}</p>` : ''}

                            <div class="mt-auto space-y-3">
                                <div class="flex items-center gap-2.5 text-xs text-gray-500 mb-6 font-medium bg-gray-50 p-3.5 rounded-xl">
                                    <svg class="w-4 h-4 text-[#10583f] shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg>
                                    <span>100% Fresh premium quality guaranteed. Handcrafted.</span>
                                </div>
                                <button onclick="orderViaWhatsApp('${bouquet.id}')" class="w-full premium-btn text-white py-4 rounded-full flex items-center justify-center gap-2 text-xs font-bold uppercase tracking-[0.2em]">
                                    <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24"><path d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946C.06 5.348 5.397.01 12.008.01c3.202.001 6.212 1.246 8.477 3.514 2.266 2.268 3.507 5.28 3.505 8.484-.004 6.657-5.34 11.997-11.953 11.997-2.005-.001-3.973-.502-5.713-1.455L0 24zm6.59-4.846c1.6.95 3.188 1.449 4.625 1.451 5.436 0 9.851-4.398 9.854-9.807.001-2.621-1.013-5.086-2.86-6.935C16.36 1.913 13.9.894 11.285.894c-5.438 0-9.854 4.398-9.858 9.808 0 2.037.533 4.024 1.547 5.765l-.99 3.613 3.73-.973h.001a9.78 9.78 0 0 0 4.332 1.048z"/></svg>
                                    Order via WhatsApp
                                </button>
                                <a href="tel:${state.settings.phone}" class="w-full bg-white text-gray-900 py-4 rounded-full flex items-center justify-center gap-2 text-xs font-bold uppercase tracking-[0.2em] border border-gray-200 hover:bg-gray-50 transition-colors text-center block">
                                    Call Studio
                                </a>
                            </div>
                        </div>
                    </div>
                </div>
            `;
        }

        window.addEventListener('DOMContentLoaded', () => {
            renderHome();
        });
    </script>
</body>
</html>
