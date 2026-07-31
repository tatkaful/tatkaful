<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tatka Ful | Premium Floral Concepts</title>

    <!-- Tailwind CSS -->
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

        // Your provided Firebase Configuration
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

        const DEFAULT_STATE = {
            searchQuery: '',
            selectedBouquet: null,
            bouquets: [],
            reviews: [],
            settings: {
                logo: 'https://placehold.co/400x400/10583f/ffffff?text=TF',
                banner: 'https://images.unsplash.com/photo-1519225421980-715cb0215aed?auto=format&fit=crop&w=1200&q=80',
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

        // Ultra-Fast Cache Load (0 lag on Instagram/TikTok click)
        let cached = localStorage.getItem('tatkaful_live_cache');
        window.state = cached ? JSON.parse(cached) : DEFAULT_STATE;
        window.state.searchQuery = '';
        window.state.selectedBouquet = null;

        const dataRef = ref(db, 'tatkaful_data');
        onValue(dataRef, (snapshot) => {
            const val = snapshot.val();
            if (val) {
                // Ensure array format for robust rendering
                if (val.bouquets) {
                    window.state.bouquets = Array.isArray(val.bouquets) ? val.bouquets : Object.values(val.bouquets);
                }
                if (val.reviews) {
                    window.state.reviews = Array.isArray(val.reviews) ? val.reviews : Object.values(val.reviews);
                }
                if (val.settings) window.state.settings = { ...DEFAULT_STATE.settings, ...val.settings };
                
                // Save updated state to local cache for instant future loads
                localStorage.setItem('tatkaful_live_cache', JSON.stringify({
                    bouquets: window.state.bouquets,
                    reviews: window.state.reviews,
                    settings: window.state.settings
                }));

                // Re-render immediately on live admin changes without refreshing page
                if(!window.state.selectedBouquet) { // Don't interrupt if user is viewing a modal
                    renderHome();
                } else {
                    refreshCollection(); // Only refresh background
                }
            }
        }, (err) => {
            console.warn("Firebase live sync fallback to cached data:", err);
        });

        // Initialize view instantly
        window.addEventListener('DOMContentLoaded', () => {
            renderHome();
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
            const bouquet = window.state.bouquets.find(b => b.id === bouquetId);
            if (!bouquet) return;

            const priceNote = bouquet.currentPrice ? ` (৳${bouquet.currentPrice})` : '';
            const message = `Hello Tatka Ful! 🌸 I would love to order the premium "${bouquet.name || 'Bouquet'}" design${priceNote}.\n\n*Product ID:* ${bouquet.id}`;
            const url = `https://wa.me/${window.formatWhatsApp(window.state.settings.whatsapp)}?text=${encodeURIComponent(message)}`;
            window.open(url, '_blank', 'noreferrer');
        };

        window.sortByPosition = function(list) {
            return [...list].sort((a, b) => {
                const pa = (a.position === '' || a.position === undefined || a.position === null || isNaN(Number(a.position))) ? Number.POSITIVE_INFINITY : Number(a.position);
                const pb = (b.position === '' || b.position === undefined || b.position === null || isNaN(Number(b.position))) ? Number.POSITIVE_INFINITY : Number(b.position);
                if (pa !== pb) return pa - pb;
                return String(a.id).localeCompare(String(b.id));
            });
        };

        window.computeFilteredBouquets = function() {
            const visibleBouquets = window.state.bouquets.filter(b => b.visible !== false);
            let list = visibleBouquets;
            const q = window.state.searchQuery.trim().toLowerCase();
            if (q) {
                list = list.filter(b =>
                    (b.name || '').toLowerCase().includes(q) ||
                    (b.description || '').toLowerCase().includes(q)
                );
            }
            return window.sortByPosition(list);
        };

        window.renderBouquetGridHTML = function(displayedBouquets) {
            if (displayedBouquets.length === 0) {
                return `
                    <div class="text-center py-20 luxury-card rounded-[2rem] animate-fade-up">
                        <div class="w-20 h-20 bg-[#eaf6f0] rounded-full flex items-center justify-center mx-auto mb-6">
                            <svg class="w-9 h-9 text-[#10583f]" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M4 16l4.586-4.586a2 2 0 012.828 0L16 16m-2-2l1.586-1.586a2 2 0 012.828 0L20 14m-6-6h.01M6 20h12a2 2 0 002-2V6a2 2 0 00-2-2H6a2 2 0 00-2 2v12a2 2 0 002 2z"></path></svg>
                        </div>
                        <h3 class="text-2xl font-serif text-gray-900 mb-2">${window.state.searchQuery ? 'No matching designs found' : 'Collection is empty'}</h3>
                        <p class="text-gray-500 font-light text-sm px-6">${window.state.searchQuery ? 'Try searching with another floral keyword.' : 'Our floral artisans are crafting new designs.'}</p>
                    </div>
                `;
            }
            return `
                <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-x-4 sm:gap-x-6 md:gap-x-10 gap-y-8 sm:gap-y-10 md:gap-y-16">
                    ${displayedBouquets.map((bouquet, index) => `
                        <div class="group cursor-pointer flex flex-col animate-fade-up" style="animation-delay: ${Math.min(index, 8) * 0.04}s" onclick="openDetailModal('${bouquet.id}')">
                            <div class="relative aspect-[4/5] rounded-[1.25rem] sm:rounded-[2rem] overflow-hidden luxury-card mb-3 sm:mb-6 bg-gray-50">
                                ${bouquet.images && bouquet.images.length > 0 ? `
                                    <img src="${bouquet.images[0]}" alt="${bouquet.name || 'Bouquet'}" loading="lazy" class="w-full h-full object-cover transition-transform duration-[1.2s] group-hover:scale-105" onerror="this.src='https://placehold.co/800x1000/10583f/ffffff?text=Tatka+Ful'" />
                                ` : `
                                    <div class="w-full h-full flex items-center justify-center text-gray-300 text-xs">No Image</div>
                                `}
                                <div class="absolute inset-0 bg-gradient-to-t from-black/40 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
                                ${bouquet.bestseller ? `
                                    <div class="absolute top-2 left-2 sm:top-4 sm:left-4 bg-white/95 backdrop-blur-md text-[#9c7a1f] text-[8px] sm:text-[10px] font-bold uppercase tracking-[0.15em] px-2.5 sm:px-3.5 py-1.5 rounded-full flex items-center gap-1.5 shadow-md">
                                        <span class="w-1.5 h-1.5 bg-[#c8a13a] rounded-full"></span> Signature
                                    </div>
                                ` : ''}
                            </div>
                            <div class="px-1 sm:px-2 flex flex-col flex-1">
                                <h3 class="text-base sm:text-2xl font-serif text-gray-900 mb-1.5 group-hover:text-[#10583f] transition-colors leading-snug">${bouquet.name || 'Fresh Bouquet'}</h3>
                                ${window.renderPriceHTML(bouquet, 'card')}
                                ${bouquet.description ? `<p class="hidden sm:block text-gray-500 text-sm line-clamp-2 leading-relaxed font-light mb-4">${bouquet.description}</p>` : `<div class="hidden sm:block mb-4"></div>`}
                                <button onclick="orderViaWhatsApp('${bouquet.id}', event)" class="mt-auto premium-btn text-white text-[10px] sm:text-xs font-bold uppercase tracking-[0.12em] sm:tracking-[0.2em] py-2.5 sm:py-3.5 rounded-full flex items-center justify-center gap-1.5 sm:gap-2">
                                    <svg class="w-3.5 h-3.5 sm:w-4 sm:h-4" fill="currentColor" viewBox="0 0 24 24"><path d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946C.06 5.348 5.397.01 12.008.01c3.202.001 6.212 1.246 8.477 3.514 2.266 2.268 3.507 5.28 3.505 8.484-.004 6.657-5.34 11.997-11.953 11.997-2.005-.001-3.973-.502-5.713-1.455L0 24zm6.59-4.846c1.6.95 3.188 1.449 4.625 1.451 5.436 0 9.851-4.398 9.854-9.807.001-2.621-1.013-5.086-2.86-6.935C16.36 1.913 13.9.894 11.285.894c-5.438 0-9.854 4.398-9.858 9.808 0 2.037.533 4.024 1.547 5.765l-.99 3.613 3.73-.973h.001a9.78 9.78 0 0 0 4.332 1.048z"/></svg>
                                    <span class="sm:hidden">Order</span>
                                    <span class="hidden sm:inline">Order Now</span>
                                </button>
                            </div>
                        </div>
                    `).join('')}
                </div>
            `;
        };

        window.refreshCollection = function() {
            const gridWrap = document.getElementById('bouquet-grid-wrapper');
            if (gridWrap) gridWrap.innerHTML = window.renderBouquetGridHTML(window.computeFilteredBouquets());
        };

        window.handleSearchInput = function(value) {
            window.state.searchQuery = value;
            window.refreshCollection();
        };

        window.renderHome = function() {
            const container = document.getElementById('app-root');
            if (!container) return;

            container.innerHTML = `
                <nav class="fixed w-full top-0 z-40 glass-header">
                    <div class="max-w-7xl mx-auto px-6 h-20 md:h-24 flex items-center justify-between">
                        <div class="flex items-center gap-3.5 cursor-pointer group" onclick="window.scrollTo({top:0, behavior:'smooth'})">
                            <img src="${window.state.settings.logo}" onerror="this.src='https://placehold.co/100x100/10583f/ffffff'" alt="Tatka Ful Logo" class="w-12 h-12 md:w-14 md:h-14 rounded-full object-cover shadow-sm group-hover:scale-105 transition-transform duration-300 bg-white" />
                            <span class="text-2xl font-serif font-semibold text-gray-900 tracking-wide group-hover:text-[#10583f] transition-colors">Tatka Ful</span>
                        </div>
                        <div class="hidden md:flex items-center gap-10 text-sm font-semibold tracking-widest uppercase text-gray-500">
                            <a href="#collection" class="hover:text-[#10583f] transition-colors">Collections</a>
                            <a href="https://wa.me/${window.formatWhatsApp(window.state.settings.whatsapp)}" target="_blank" rel="noreferrer" class="premium-btn text-white px-8 py-3.5 rounded-full tracking-widest text-xs font-bold uppercase shadow-lg">
                                Inquire Now
                            </a>
                        </div>
                    </div>
                </nav>

                <section class="relative pt-32 pb-20 md:pt-48 md:pb-32 px-6 flex items-center justify-center min-h-[75vh] overflow-hidden">
                    <div class="orb w-[28rem] h-[28rem] bg-[#10583f]/10 -top-20 -left-20"></div>
                    <div class="orb w-[24rem] h-[24rem] bg-[#c8a13a]/15 top-32 -right-10"></div>
                    <div class="absolute inset-0 z-0">
                        <img src="${window.state.settings.banner}" onerror="this.src='https://placehold.co/1200x600/faf8f4/10583f'" alt="Luxury Floral Banner" class="w-full h-full object-cover opacity-20 scale-105" />
                        <div class="absolute inset-0 bg-gradient-to-b from-[#faf8f4]/90 via-[#faf8f4]/70 to-[#faf8f4]"></div>
                    </div>

                    <div class="max-w-4xl mx-auto text-center relative z-10 animate-fade-up">
                        <span class="eyebrow-flourish">Premium Floral Design</span>
                        <h1 class="text-4xl md:text-7xl lg:text-8xl font-serif text-gray-900 mt-6 mb-8 leading-[1.1] tracking-tight">
                            ${window.state.settings.heroSlogan || 'Elegance in Every Petal.'}
                        </h1>
                        <p class="text-base md:text-xl text-gray-600 mb-8 max-w-2xl mx-auto font-light leading-relaxed">
                            ${window.state.settings.heroDesc || 'Curating luxury floral masterpieces for your most precious memories.'}
                        </p>
                        ${window.state.settings.deliveryText ? `
                        <div class="inline-flex items-center gap-2.5 bg-white/80 backdrop-blur-md border border-[#c8a13a]/30 rounded-full px-5 sm:px-6 py-2.5 sm:py-3 mb-10 shadow-sm">
                            <span class="text-sm font-bold tracking-[0.15em] uppercase text-[#0b2e22]">${window.state.settings.deliveryText}</span>
                        </div>` : ''}
                        <div>
                        <a href="#collection" class="inline-flex items-center gap-3 premium-btn text-white px-10 py-5 rounded-full text-sm uppercase tracking-widest font-semibold">
                            View Gallery
                            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"></path></svg>
                        </a>
                        </div>
                    </div>
                </section>

                <section id="collection" class="px-6 py-5 sticky top-20 md:top-24 glass-header z-30 shadow-sm border-t border-gray-100">
                    <div class="max-w-7xl mx-auto">
                        <div class="relative max-w-xl w-full mx-auto">
                            <svg class="w-5 h-5 text-gray-400 absolute left-5 top-1/2 -translate-y-1/2 pointer-events-none" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-4.35-4.35M11 19a8 8 0 100-16 8 8 0 000 16z"></path></svg>
                            <input id="search-input" type="text" value="${window.state.searchQuery}" oninput="handleSearchInput(this.value)" placeholder="Search bouquets by name..." class="w-full pl-12 pr-5 py-3.5 bg-white border border-gray-200 rounded-full text-sm font-medium focus:border-[#10583f] focus:ring-2 focus:ring-[#10583f]/10 transition-all placeholder:text-gray-400 placeholder:font-normal" />
                        </div>
                    </div>
                </section>

                <section class="px-6 py-12 sm:py-20 max-w-7xl mx-auto min-h-[50vh]">
                    <div id="bouquet-grid-wrapper">
                        ${window.renderBouquetGridHTML(window.computeFilteredBouquets())}
                    </div>
                </section>

                <div class="fixed bottom-6 right-6 z-40 flex flex-col gap-4">
                    <a href="https://wa.me/${window.formatWhatsApp(window.state.settings.whatsapp)}" target="_blank" rel="noreferrer" class="relative w-16 h-16 bg-[#25D366] text-white rounded-full flex items-center justify-center hover:scale-105 transition-transform shadow-[0_10px_30px_rgba(37,211,102,0.4)]">
                        <span class="absolute inline-flex h-full w-full rounded-full bg-[#25D366] opacity-40 animate-ping"></span>
                        <svg class="w-8 h-8 relative z-10" fill="currentColor" viewBox="0 0 24 24"><path d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946C.06 5.348 5.397.01 12.008.01c3.202.001 6.212 1.246 8.477 3.514 2.266 2.268 3.507 5.28 3.505 8.484-.004 6.657-5.34 11.997-11.953 11.997-2.005-.001-3.973-.502-5.713-1.455L0 24zm6.59-4.846c1.6.95 3.188 1.449 4.625 1.451 5.436 0 9.851-4.398 9.854-9.807.001-2.621-1.013-5.086-2.86-6.935C16.36 1.913 13.9.894 11.285.894c-5.438 0-9.854 4.398-9.858 9.808 0 2.037.533 4.024 1.547 5.765l-.99 3.613 3.73-.973h.001a9.78 9.78 0 0 0 4.332 1.048zM18.15 14.86c-.337-.168-1.996-.983-2.305-1.096-.309-.113-.534-.168-.758.168-.225.337-.871 1.096-1.067 1.32-.197.225-.393.253-.73.084-.337-.168-1.42-.524-2.707-1.671-1.002-.894-1.679-2.001-1.875-2.337-.197-.337-.021-.519.147-.687.152-.151.337-.393.506-.59.168-.197.225-.337.337-.562.113-.225.056-.422-.028-.59-.084-.168-.758-1.825-1.039-2.503-.274-.662-.553-.573-.758-.583-.197-.01-.422-.012-.647-.012-.225 0-.59.084-.9.422-.309.337-1.18 1.151-1.18 2.808 0 1.657 1.208 3.257 1.377 3.482.168.225 2.378 3.63 5.76 5.087.805.347 1.433.554 1.923.71.808.257 1.545.221 2.127.135.649-.096 1.996-.815 2.277-1.601.281-.787.281-1.461.197-1.601-.084-.14-.309-.225-.647-.393z"/></svg>
                    </a>
                </div>

                <footer class="bg-white border-t border-gray-100 pt-20 sm:pt-24 pb-12 px-6">
                    <div class="max-w-7xl mx-auto flex flex-col md:flex-row justify-between items-center gap-12 text-center md:text-left">
                        <div class="flex flex-col items-center md:items-start max-w-sm">
                            <img src="${window.state.settings.logo}" onerror="this.src='https://placehold.co/100x100/10583f/ffffff'" alt="Logo" class="w-20 h-20 rounded-full mb-6 shadow-sm object-cover bg-white" />
                            <h3 class="font-serif text-3xl text-gray-900 mb-4">Tatka Ful</h3>
                            <p class="text-gray-500 text-sm leading-relaxed font-light">
                                Nature's finest expressions of love, premium flower concepts curated flawlessly.
                            </p>
                        </div>
                        <div class="flex flex-col items-center md:items-end">
                            <p class="text-xs font-bold tracking-[0.2em] text-gray-400 uppercase mb-5">Studio Connections</p>
                            <div class="flex gap-4">
                                ${window.state.settings.instagram ? `
                                <a href="${window.state.settings.instagram}" target="_blank" rel="noreferrer" class="social-badge">
                                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 9a2 2 0 012-2h.93a2 2 0 001.664-.89l.812-1.22A2 2 0 0110.07 4h3.86a2 2 0 011.664.89l.812 1.22A2 2 0 0018.07 7H19a2 2 0 012 2v9a2 2 0 01-2 2H5a2 2 0 01-2-2V9z"></path><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 13a3 3 0 11-6 0 3 3 0 016 0z"></path></svg>
                                </a>` : ''}
                                ${window.state.settings.facebook ? `
                                <a href="${window.state.settings.facebook}" target="_blank" rel="noreferrer" class="social-badge">
                                    <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M14 13.5h2.5l.5-3H14V8.5c0-.75.25-1.5 1.5-1.5H17V4.5c-.5 0-1.5-.1-2.5-.1-2.5 0-4 1.5-4 4.5V10.5H8v3h2.5V21h3.5v-7.5z"></path></svg>
                                </a>` : ''}
                                ${window.state.settings.tiktok ? `
                                <a href="${window.state.settings.tiktok}" target="_blank" rel="noreferrer" class="social-badge">
                                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 18V5l12-2v13M9 18a3 3 0 11-6 0 3 3 0 016 0zm12-2a3 3 0 11-6 0 3 3 0 016 0z"></path></svg>
                                </a>` : ''}
                                <a href="tel:${window.state.settings.phone}" class="social-badge">
                                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.94.725l.548 2.2a1 1 0 01-.321.988l-1.305.98a10.582 10.582 0 004.872 4.872l.98-1.305a1 1 0 01.988-.321l2.2.548a1 1 0 01.725.94V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"></path></svg>
                                </a>
                            </div>
                        </div>
                    </div>
                    <div class="max-w-7xl mx-auto mt-20 pt-8 border-t border-gray-100 text-center">
                        <p class="text-[10px] font-semibold tracking-[0.2em] uppercase text-gray-400 cursor-default select-none">
                            &copy; ${new Date().getFullYear()} Tatka Ful. Crafted with elegance.
                        </p>
                    </div>
                </footer>
            `;

            if (window.state.selectedBouquet) {
                window.renderDetailModal();
            }
        };

        window.openDetailModal = function(id) {
            const bouquet = window.state.bouquets.find(b => b.id === id);
            if (bouquet) {
                window.state.selectedBouquet = bouquet;
                window.renderDetailModal();
            }
        };

        window.closeDetailModal = function() {
            window.state.selectedBouquet = null;
            const container = document.getElementById('modal-container');
            if (container) container.innerHTML = '';
        };

        window.renderDetailModal = function() {
            const bouquet = window.state.selectedBouquet;
            const container = document.getElementById('modal-container');
            if (!container || !bouquet) return;

            container.innerHTML = `
                <div class="fixed inset-0 z-50 flex items-center justify-center p-0 md:p-8">
                    <div class="absolute inset-0 bg-black/60 backdrop-blur-md transition-opacity" onclick="closeDetailModal()"></div>
                    <div class="relative bg-white w-full h-full md:h-auto md:max-h-[90vh] md:max-w-6xl md:rounded-[2rem] shadow-2xl overflow-hidden flex flex-col md:flex-row animate-fade-up">

                        <button onclick="closeDetailModal()" class="absolute top-6 right-6 z-20 w-12 h-12 bg-white/90 backdrop-blur-md rounded-full flex items-center justify-center text-gray-900 hover:bg-gray-100 transition-colors shadow-lg">
                            <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path></svg>
                        </button>

                        <div class="w-full md:w-1/2 bg-[#faf8f4] h-[50vh] md:h-auto overflow-y-auto snap-y snap-mandatory scrollbar-hide relative">
                            ${bouquet.images && bouquet.images.length > 0 ? bouquet.images.map((img, i) => `
                                <div class="w-full h-full min-h-[50vh] md:min-h-full snap-center relative bg-gray-50 flex items-center justify-center">
                                    <img src="${img}" alt="${bouquet.name || 'Bouquet'} ${i+1}" class="w-full h-full object-cover" onerror="this.src='https://placehold.co/800x1000/10583f/ffffff?text=Tatka+Ful'" />
                                </div>
                            `).join('') : `
                                <div class="w-full h-full flex items-center justify-center text-gray-300 font-light">No Gallery Images</div>
                            `}
                            ${bouquet.images && bouquet.images.length > 1 ? `
                                <div class="absolute bottom-6 left-0 right-0 flex justify-center gap-2 pointer-events-none">
                                    <span class="bg-black/40 backdrop-blur-md text-white text-[10px] tracking-wider px-4 py-2 rounded-full uppercase font-semibold shadow-lg">Scroll for more images</span>
                                </div>
                            ` : ''}
                        </div>

                        <div class="w-full md:w-1/2 p-8 md:p-16 flex flex-col h-[50vh] md:h-auto overflow-y-auto bg-white">
                            <h2 class="text-4xl md:text-5xl font-serif text-gray-900 mb-4 leading-tight">${bouquet.name || 'Fresh Bouquet'}</h2>
                            ${window.renderPriceHTML(bouquet, 'modal')}
                            <div class="gold-divider mb-8"></div>
                            ${bouquet.description ? `<p class="text-gray-600 leading-relaxed mb-10 font-light text-lg">${bouquet.description}</p>` : ''}

                            <div class="mt-auto space-y-4">
                                <div class="flex items-center gap-3 text-sm text-gray-500 mb-8 font-medium bg-gray-50 p-4 rounded-xl">
                                    <svg class="w-5 h-5 text-[#10583f] shrink-0" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg>
                                    <span>100% Fresh premium quality guaranteed. Handcrafted.</span>
                                </div>
                                <button onclick="orderViaWhatsApp('${bouquet.id}')" class="w-full premium-btn text-white py-5 rounded-full flex items-center justify-center gap-3 text-sm font-bold uppercase tracking-[0.2em] shadow-lg hover:shadow-xl transition-all">
                                    <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946C.06 5.348 5.397.01 12.008.01c3.202.001 6.212 1.246 8.477 3.514 2.266 2.268 3.507 5.28 3.505 8.484-.004 6.657-5.34 11.997-11.953 11.997-2.005-.001-3.973-.502-5.713-1.455L0 24zm6.59-4.846c1.6.95 3.188 1.449 4.625 1.451 5.436 0 9.851-4.398 9.854-9.807.001-2.621-1.013-5.086-2.86-6.935C16.36 1.913 13.9.894 11.285.894c-5.438 0-9.854 4.398-9.858 9.808 0 2.037.533 4.024 1.547 5.765l-.99 3.613 3.73-.973h.001a9.78 9.78 0 0 0 4.332 1.048z"/></svg>
                                    Order via WhatsApp
                                </button>
                                <a href="tel:${window.state.settings.phone}" class="w-full bg-white text-gray-900 py-5 rounded-full flex items-center justify-center gap-3 text-sm font-bold uppercase tracking-[0.2em] border border-gray-200 hover:bg-gray-50 transition-colors text-center block">
                                    Call Studio
                                </a>
                            </div>
                        </div>
                    </div>
                </div>
            `;
        };
    </script>
</body>
</html>
