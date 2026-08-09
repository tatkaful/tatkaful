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
            box-shadow: 0 8px 18px -8px rgba(11, 46, 34, 0.3);
            transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
        }
        .social-badge svg { width: 1.3rem; height: 1.3rem; }
        .social-badge:hover {
            transform: translateY(-4px) scale(1.06);
            box-shadow: 0 16px 28px -8px rgba(11, 46, 34, 0.4);
        }
        .social-badge-ig {
            background: radial-gradient(circle at 30% 107%, #fdf497 0%, #fdf497 5%, #fd5949 45%, #d6249f 60%, #285AEB 90%);
        }
        .social-badge-fb { background: #1877F2; }
        .social-badge-tiktok { background: #000000; }
        .social-badge-call { background: linear-gradient(135deg, var(--gold-deep), var(--emerald)); }

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

        /* Custom Toast CSS */
        #toast-container { position: fixed; top: 20px; right: 20px; z-index: 1000; display: flex; flex-direction: column; gap: 10px; }
        .toast { padding: 12px 20px; border-radius: 8px; color: white; font-weight: 500; font-size: 14px; background-color: #10583f; box-shadow: 0 10px 25px -5px rgba(0,0,0,0.2); animation: slideIn 0.3s ease-out; }
        @keyframes slideIn { from { transform: translateX(100%); opacity: 0; } to { transform: translateX(0); opacity: 1; } }
    </style>
</head>
<body class="text-gray-800 antialiased selection:bg-[#10583f] selection:text-white">

    <div id="toast-container"></div>
    <div id="app-root" class="min-h-screen flex flex-col"></div>
    <div id="modal-container"></div>

    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getDatabase, ref, onValue } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-database.js";

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
            reviews: [
                { id: 'default-1', name: 'Aisha Rahman', location: 'Gulshan, Dhaka', rating: 5, text: 'Absolutely breathtaking! The attention to detail and the freshness of the blooms were beyond my expectations. A true luxury experience from start to finish.', avatar: 'https://i.pravatar.cc/150?img=47', position: 1, visible: true },
                { id: 'default-2', name: 'Fahim Ahmed', location: 'Banani, Dhaka', rating: 5, text: 'I ordered a signature bouquet for my anniversary, and it was a masterpiece. The packaging, the premium feel, and the delivery were absolutely flawless.', avatar: 'https://i.pravatar.cc/150?img=12', position: 2, visible: true },
                { id: 'default-3', name: 'Nusrat Jahan', location: 'Dhanmondi, Dhaka', rating: 5, text: 'Tatka Ful is my go-to for all floral needs. Their designs are so unique and elegant, and the flowers stay perfectly fresh for days. Highly recommended!', avatar: 'https://i.pravatar.cc/150?img=32', position: 3, visible: true }
            ],
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

        let cached = localStorage.getItem('tatkaful_live_cache');
        window.state = cached ? JSON.parse(cached) : DEFAULT_STATE;
        window.state.searchQuery = '';
        window.state.selectedBouquet = null;

        const dataRef = ref(db, 'tatkaful_data');
        onValue(dataRef, (snapshot) => {
            const val = snapshot.val();
            if (val) {
                if (val.bouquets) {
                    window.state.bouquets = Array.isArray(val.bouquets) ? val.bouquets : Object.values(val.bouquets);
                }
                if (val.reviews) {
                    window.state.reviews = Array.isArray(val.reviews) ? val.reviews : Object.values(val.reviews);
                }
                if (val.settings) window.state.settings = { ...DEFAULT_STATE.settings, ...val.settings };
                
                localStorage.setItem('tatkaful_live_cache', JSON.stringify({
                    bouquets: window.state.bouquets,
                    reviews: window.state.reviews,
                    settings: window.state.settings
                }));

                if(!window.state.selectedBouquet) {
                    renderHome();
                } else {
                    refreshCollection();
                }
            }
        }, (err) => {
            console.warn("Firebase live sync fallback to cached data:", err);
        });

        window.addEventListener('DOMContentLoaded', () => {
            renderHome();
        });

        window.showToast = function(msg) {
            const container = document.getElementById('toast-container');
            const toast = document.createElement('div');
            toast.className = 'toast';
            toast.innerHTML = `<svg class="w-5 h-5 inline-block mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path></svg> ${msg}`;
            container.appendChild(toast);
            setTimeout(() => {
                toast.style.opacity = '0';
                toast.style.transition = 'opacity 0.3s ease';
                setTimeout(() => toast.remove(), 300);
            }, 3000);
        };

        // NEW: Share Feature added here!
        window.shareWebsite = async function() {
            const shareData = {
                title: 'Tatka Ful - Premium Floral Concepts',
                text: 'Experience luxury floral masterpieces by Tatka Ful. Order fresh bouquets for your loved ones!',
                url: 'https://tatkaful.github.io/tatkaful/'
            };
            try {
                if (navigator.share) {
                    await navigator.share(shareData);
                } else {
                    // Fallback to copying clipboard if Web Share API is not supported
                    const textarea = document.createElement('textarea');
                    textarea.value = shareData.url;
                    document.body.appendChild(textarea);
                    textarea.select();
                    document.execCommand('copy');
                    document.body.removeChild(textarea);
                    window.showToast('Website link copied to clipboard!');
                }
            } catch (err) {
                console.error('Error sharing:', err);
            }
        };

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

        window.formatMoney = function(amount) {
            return new Intl.NumberFormat('en-IN').format(amount);
        };

        // Some image hosts (like imgbb) don't return a real HTTP error when an
        // uploaded image expires or gets deleted — they return a small valid
        // "image not found" graphic instead, so the normal onerror handler
        // never fires. This checks the actual pixel size of the loaded image
        // and swaps in our branded fallback if it looks like one of those
        // tiny placeholder graphics rather than a real product photo.
        window.handleProductImgLoad = function(imgEl, fallbackSrc) {
            try {
                if (imgEl.naturalWidth && imgEl.naturalHeight && (imgEl.naturalWidth < 200 || imgEl.naturalHeight < 200)) {
                    imgEl.src = fallbackSrc;
                }
            } catch (e) { /* ignore */ }
        };

        // iOS in-app browsers (Instagram, Facebook, TikTok, WhatsApp) and Safari
        // all run on WebKit, which treats any "http://" resource on an "https://"
        // page as insecure "mixed content". This can make the whole page appear
        // dimmed/unresponsive with a warning icon in the address bar — and since
        // product images use loading="lazy", it often only shows up once you
        // scroll down to the offending image. This helper force-upgrades any
        // stray http:// image link (e.g. accidentally pasted in the admin panel)
        // to https:// so this never gets triggered.
        window.secureUrl = function(url) {
            if (!url || typeof url !== 'string') return url;
            if (url.trim().toLowerCase().startsWith('http://')) {
                return 'https://' + url.trim().slice(7);
            }
            return url;
        };

        window.renderPriceHTML = function(bouquet, size = 'card') {
            const current = Number(bouquet.currentPrice) || 0;
            const old = Number(bouquet.oldPrice) || 0;
            const hasOld = old > current;
            const hasCurrent = current > 0;
            
            if (!hasOld && !hasCurrent) return '';
            
            let discountPct = null;
            if (hasOld && hasCurrent) {
                discountPct = Math.round((1 - (current / old)) * 100);
            }
            
            const currentSize = size === 'modal' ? 'text-3xl md:text-4xl' : 'text-base sm:text-xl';
            const oldSize = size === 'modal' ? 'text-lg' : 'text-xs sm:text-sm';
            
            return `
                <div class="${size === 'modal' ? 'mb-6' : 'mb-1.5'}">
                    <div class="flex items-baseline flex-nowrap gap-1.5 sm:gap-2 overflow-hidden">
                        ${hasCurrent ? `<span class="font-sans ${currentSize} text-[#0b2e22] font-extrabold leading-none tracking-tight whitespace-nowrap" style="font-variant-numeric: lining-nums tabular-nums;">৳${window.formatMoney(current)}</span>` : ''}
                        ${hasOld ? `<span class="font-sans ${oldSize} text-gray-400 line-through font-semibold leading-none whitespace-nowrap" style="font-variant-numeric: lining-nums tabular-nums;">৳${window.formatMoney(old)}</span>` : ''}
                    </div>
                    ${discountPct > 0 ? `<div class="mt-1"><span class="inline-block bg-[#c8a13a]/10 text-[#9c7a1f] border border-[#c8a13a]/30 text-[9px] sm:text-[10px] font-bold px-1.5 py-0.5 rounded-md uppercase tracking-widest shadow-sm">Save ${discountPct}%</span></div>` : ''}
                </div>
            `;
        };

        window.getSecretCode = function(bouquet) {
            if (bouquet.secretCode) return bouquet.secretCode;
            const namePart = (bouquet.name || 'FLR').replace(/[^a-zA-Z]/g, '').toUpperCase().slice(0, 3) || 'FLR';
            const idPart = String(bouquet.id || '').replace(/[^a-zA-Z0-9]/g, '').slice(-4).toUpperCase() || '0000';
            return `${namePart}-${idPart}`;
        };

        window.orderViaWhatsApp = function(bouquetId, event) {
            if (event) event.stopPropagation();
            const bouquet = window.state.bouquets.find(b => b.id === bouquetId);
            if (!bouquet) return;

            const secretCode = window.getSecretCode(bouquet);
            const priceNote = bouquet.currentPrice ? ` (৳${window.formatMoney(bouquet.currentPrice)})` : '';
            const message = `Hello Tatka Ful! 🌸 I would love to order the premium "${bouquet.name || 'Bouquet'}" design${priceNote}.\n\n*Secret Code:* ${secretCode}\n*Product ID:* ${bouquet.id}`;
            const url = `https://wa.me/${window.formatWhatsApp(window.state.settings.whatsapp)}?text=${encodeURIComponent(message)}`;
            window.location.href = url;
        };

        window.sortByPosition = function(list) {
            return [...list].sort((a, b) => {
                const pa = (a.position === '' || a.position === undefined || a.position === null || isNaN(Number(a.position))) ? Number.POSITIVE_INFINITY : Number(a.position);
                const pb = (b.position === '' || b.position === undefined || b.position === null || isNaN(Number(b.position))) ? Number.POSITIVE_INFINITY : Number(b.position);
                if (pa !== pb) return pa - pb;
                return String(a.id).localeCompare(String(b.id));
            });
        };

        window.computeFilteredReviews = function() {
            const list = (window.state.reviews || []).filter(r => r.visible !== false);
            return window.sortByPosition(list);
        };

        window.renderReviewsHTML = function() {
            const reviews = window.computeFilteredReviews();
            if (reviews.length === 0) return '';
            return reviews.map(r => `
                <div class="bg-white p-8 rounded-[2rem] shadow-sm border border-gray-100 hover:shadow-xl transition-shadow relative">
                    <div class="text-[#c8a13a] mb-5 flex gap-1">${window.starGlyphs(Number(r.rating) || 5)}</div>
                    <p class="text-gray-600 font-light mb-8 italic leading-relaxed">"${r.text || r.comment || r.message || r.review || ''}"</p>
                    <div class="flex items-center gap-4 mt-auto">
                        <div class="w-12 h-12 bg-gray-200 rounded-full overflow-hidden border border-gray-100"><img src="${window.secureUrl(r.avatar || r.image || 'https://i.pravatar.cc/150')}" onerror="this.src='https://i.pravatar.cc/150'" class="w-full h-full object-cover"></div>
                        <div>
                            <h4 class="font-bold text-gray-900 text-sm">${r.name || 'Happy Client'}</h4>
                            <p class="text-xs text-gray-500">${r.location || ''}</p>
                        </div>
                    </div>
                </div>
            `).join('');
        };

        window.refreshReviews = function() {
            const reviewsWrap = document.getElementById('reviews-grid-wrapper');
            if (reviewsWrap) reviewsWrap.innerHTML = window.renderReviewsHTML();
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
                <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-x-4 sm:gap-x-6 md:gap-x-8 gap-y-6 sm:gap-y-10 md:gap-y-12">
                    ${displayedBouquets.map((bouquet, index) => `
                        <div class="group cursor-pointer flex flex-col animate-fade-up bg-white rounded-[1.5rem] p-2.5 sm:p-3 shadow-sm hover:shadow-2xl transition-all duration-400 border border-gray-100 hover:border-[#c8a13a]/30" style="animation-delay: ${Math.min(index, 8) * 0.04}s" onclick="openDetailModal('${bouquet.id}')">
                            <div class="relative aspect-[4/5] rounded-[1rem] overflow-hidden mb-3 sm:mb-4 bg-gray-50">
                                ${bouquet.images && bouquet.images.length > 0 ? `
                                    <img src="${window.secureUrl(bouquet.images[0])}" alt="${bouquet.name || 'Bouquet'}" loading="eager" fetchpriority="high" decoding="async" class="w-full h-full object-cover transition-transform duration-[1.2s] group-hover:scale-110" onerror="this.src='https://placehold.co/800x1000/10583f/ffffff?text=Tatka+Ful'" onload="handleProductImgLoad(this, 'https://placehold.co/800x1000/10583f/ffffff?text=Tatka+Ful')" />
                                ` : `
                                    <div class="w-full h-full flex items-center justify-center text-gray-300 text-xs">No Image</div>
                                `}
                                <div class="absolute inset-0 bg-gradient-to-t from-[#0b2e22]/50 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
                                ${bouquet.bestseller ? `
                                    <div class="absolute top-2 left-2 sm:top-2.5 sm:left-2.5 bg-white/95 backdrop-blur-md text-[#9c7a1f] text-[7px] sm:text-[8px] font-bold uppercase tracking-[0.1em] px-1.5 py-1 rounded-full flex items-center gap-1 shadow-md">
                                        <span class="w-1 h-1 bg-[#c8a13a] rounded-full"></span> Signature
                                    </div>
                                ` : ''}
                            </div>
                            <div class="px-1.5 pb-1 flex flex-col flex-1 justify-between">
                                <div>
                                    <h3 class="text-[12px] sm:text-sm font-serif text-gray-900 mb-1 group-hover:text-[#10583f] transition-colors leading-snug line-clamp-2 min-h-[2.3em] sm:min-h-[2.5em]">${bouquet.name || 'Fresh Bouquet'}</h3>
                                    ${window.renderPriceHTML(bouquet, 'card')}
                                </div>
                                <button onclick="orderViaWhatsApp('${bouquet.id}', event)" class="mt-2.5 w-full bg-[#0b2e22] hover:bg-[#10583f] text-white text-[10px] sm:text-[11px] font-bold uppercase tracking-[0.15em] py-2.5 rounded-xl flex items-center justify-center gap-1.5 transition-all shadow-md hover:shadow-lg">
                                    <svg class="w-3.5 h-3.5 sm:w-4 sm:h-4" fill="currentColor" viewBox="0 0 24 24"><path d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946C.06 5.348 5.397.01 12.008.01c3.202.001 6.212 1.246 8.477 3.514 2.266 2.268 3.507 5.28 3.505 8.484-.004 6.657-5.34 11.997-11.953 11.997-2.005-.001-3.973-.502-5.713-1.455L0 24zm6.59-4.846c1.6.95 3.188 1.449 4.625 1.451 5.436 0 9.851-4.398 9.854-9.807.001-2.621-1.013-5.086-2.86-6.935C16.36 1.913 13.9.894 11.285.894c-5.438 0-9.854 4.398-9.858 9.808 0 2.037.533 4.024 1.547 5.765l-.99 3.613 3.73-.973h.001a9.78 9.78 0 0 0 4.332 1.048z"/></svg>
                                    Order
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
                            <img src="${window.secureUrl(window.state.settings.logo)}" onerror="this.src='https://placehold.co/100x100/10583f/ffffff'" alt="Tatka Ful Logo" class="w-12 h-12 md:w-14 md:h-14 rounded-full object-cover shadow-sm group-hover:scale-105 transition-transform duration-300 bg-white" />
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

                <section class="relative pt-24 pb-6 md:pt-32 md:pb-8 px-6 overflow-hidden">
                    <div class="orb w-[28rem] h-[28rem] bg-[#10583f]/10 -top-20 -left-20"></div>
                    <div class="orb w-[24rem] h-[24rem] bg-[#c8a13a]/15 top-32 -right-10"></div>
                    <div class="absolute inset-0 z-0">
                        <img src="${window.secureUrl(window.state.settings.banner)}" onerror="this.src='https://placehold.co/1200x600/faf8f4/10583f'" alt="Luxury Floral Banner" class="w-full h-full object-cover opacity-20 scale-105" />
                        <div class="absolute inset-0 bg-gradient-to-b from-[#faf8f4]/90 via-[#faf8f4]/70 to-[#faf8f4]"></div>
                    </div>

                    <div class="max-w-4xl mx-auto text-center relative z-10 animate-fade-up">
                        <span class="eyebrow-flourish">Premium Floral Design</span>
                        <h1 class="text-4xl md:text-7xl lg:text-8xl font-serif text-gray-900 mt-5 mb-6 leading-[1.1] tracking-tight">
                            ${window.state.settings.heroSlogan || 'Elegance in Every Petal.'}
                        </h1>
                        <p class="text-base md:text-xl text-gray-600 mb-6 max-w-2xl mx-auto font-light leading-relaxed">
                            ${window.state.settings.heroDesc || 'Curating luxury floral masterpieces for your most precious memories.'}
                        </p>
                        ${window.state.settings.deliveryText ? `
                        <div class="inline-flex items-center gap-2.5 bg-white/80 backdrop-blur-md border border-[#c8a13a]/30 rounded-full px-5 sm:px-6 py-2.5 sm:py-3 mb-6 shadow-sm">
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

                <section class="px-6 pt-6 pb-12 sm:pt-8 sm:pb-20 max-w-7xl mx-auto min-h-[50vh]">
                    <div id="bouquet-grid-wrapper">
                        ${window.renderBouquetGridHTML(window.computeFilteredBouquets())}
                    </div>
                </section>

                <!-- Fake Reviews Section -->
                <section class="py-20 bg-[#faf8f4] border-t border-[#c8a13a]/10 relative overflow-hidden">
                    <div class="orb w-[20rem] h-[20rem] bg-[#c8a13a]/5 -top-10 -left-10"></div>
                    <div class="max-w-7xl mx-auto px-6 text-center relative z-10">
                        <span class="eyebrow-flourish mb-4">Client Love</span>
                        <h2 class="text-3xl md:text-5xl font-serif text-gray-900 mb-12">Words from our Patrons</h2>
                        <div class="grid grid-cols-1 md:grid-cols-3 gap-6 md:gap-8 text-left" id="reviews-grid-wrapper">
                            ${window.renderReviewsHTML()}
                        </div>
                    </div>
                </section>

                <div class="fixed bottom-6 right-6 z-40 flex flex-col gap-4 items-center">
                    <!-- Share Button (Highlighted Feature) -->
                    <button onclick="shareWebsite()" title="Share Website" class="relative w-12 h-12 bg-gradient-to-br from-[#c8a13a] to-[#9c7a1f] text-white rounded-full flex items-center justify-center hover:scale-110 transition-transform shadow-lg border-2 border-white group cursor-pointer">
                        <span class="absolute inset-0 rounded-full bg-[#c8a13a] opacity-50 animate-pulse"></span>
                        <svg class="w-5 h-5 relative z-10 group-hover:-rotate-12 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8.684 13.342C8.886 12.938 9 12.482 9 12c0-.482-.114-.938-.316-1.342m0 2.684a3 3 0 110-2.684m0 2.684l6.632 3.316m-6.632-6l6.632-3.316m0 0a3 3 0 105.367-2.684 3 3 0 00-5.367 2.684zm0 9.316a3 3 0 105.368 2.684 3 3 0 00-5.368-2.684z"></path></svg>
                    </button>

                    <!-- WhatsApp Button -->
                    <a href="https://wa.me/${window.formatWhatsApp(window.state.settings.whatsapp)}" target="_blank" rel="noreferrer" title="Chat on WhatsApp" class="relative w-16 h-16 bg-[#25D366] text-white rounded-full flex items-center justify-center hover:scale-105 transition-transform shadow-[0_10px_30px_rgba(37,211,102,0.4)]">
                        <span class="absolute inline-flex h-full w-full rounded-full bg-[#25D366] opacity-40 animate-ping"></span>
                        <svg class="w-8 h-8 relative z-10" fill="currentColor" viewBox="0 0 24 24"><path d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946C.06 5.348 5.397.01 12.008.01c3.202.001 6.212 1.246 8.477 3.514 2.266 2.268 3.507 5.28 3.505 8.484-.004 6.657-5.34 11.997-11.953 11.997-2.005-.001-3.973-.502-5.713-1.455L0 24zm6.59-4.846c1.6.95 3.188 1.449 4.625 1.451 5.436 0 9.851-4.398 9.854-9.807.001-2.621-1.013-5.086-2.86-6.935C16.36 1.913 13.9.894 11.285.894c-5.438 0-9.854 4.398-9.858 9.808 0 2.037.533 4.024 1.547 5.765l-.99 3.613 3.73-.973h.001a9.78 9.78 0 0 0 4.332 1.048zM18.15 14.86c-.337-.168-1.996-.983-2.305-1.096-.309-.113-.534-.168-.758.168-.225.337-.871 1.096-1.067 1.32-.197.225-.393.253-.73.084-.337-.168-1.42-.524-2.707-1.671-1.002-.894-1.679-2.001-1.875-2.337-.197-.337-.021-.519.147-.687.152-.151.337-.393.506-.59.168-.197.225-.337.337-.562.113-.225.056-.422-.028-.59-.084-.168-.758-1.825-1.039-2.503-.274-.662-.553-.573-.758-.583-.197-.01-.422-.012-.647-.012-.225 0-.59.084-.9.422-.309.337-1.18 1.151-1.18 2.808 0 1.657 1.208 3.257 1.377 3.482.168.225 2.378 3.63 5.76 5.087.805.347 1.433.554 1.923.71.808.257 1.545.221 2.127.135.649-.096 1.996-.815 2.277-1.601.281-.787.281-1.461.197-1.601-.084-.14-.309-.225-.647-.393z"/></svg>
                    </a>
                </div>

                <footer class="bg-white border-t border-gray-100 pt-20 sm:pt-24 pb-12 px-6">
                    <div class="max-w-7xl mx-auto flex flex-col md:flex-row justify-between items-center gap-12 text-center md:text-left">
                        <div class="flex flex-col items-center md:items-start max-w-sm">
                            <img src="${window.secureUrl(window.state.settings.logo)}" onerror="this.src='https://placehold.co/100x100/10583f/ffffff'" alt="Logo" class="w-20 h-20 rounded-full mb-6 shadow-sm object-cover bg-white" />
                            <h3 class="font-serif text-3xl text-gray-900 mb-4">Tatka Ful</h3>
                            <p class="text-gray-500 text-sm leading-relaxed font-light">
                                Nature's finest expressions of love, premium flower concepts curated flawlessly.
                            </p>
                        </div>
                        <div class="flex flex-col items-center md:items-end">
                            <p class="text-xs font-bold tracking-[0.2em] text-gray-400 uppercase mb-5">Studio Connections</p>
                            <div class="flex gap-4">
                                ${window.state.settings.instagram ? `
                                <a href="${window.state.settings.instagram}" target="_blank" rel="noreferrer" aria-label="Instagram" class="social-badge social-badge-ig">
                                    <svg class="text-white" fill="currentColor" viewBox="0 0 24 24"><path d="M12 2.163c3.204 0 3.584.012 4.849.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.265.058-1.644.07-4.849.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zM12 5.838a6.162 6.162 0 100 12.324 6.162 6.162 0 000-12.324zm0 10.162a4 4 0 110-8 4 4 0 010 8zm6.406-10.845a1.44 1.44 0 11-2.881.001 1.44 1.44 0 012.881-.001z"></path></svg>
                                </a>` : ''}
                                ${window.state.settings.facebook ? `
                                <a href="${window.state.settings.facebook}" target="_blank" rel="noreferrer" aria-label="Facebook" class="social-badge social-badge-fb">
                                    <svg class="text-white" fill="currentColor" viewBox="0 0 24 24"><path d="M22.675 0h-21.35C.595 0 0 .595 0 1.325v21.351C0 23.405.595 24 1.325 24H12.82v-9.294H9.692v-3.622h3.128V8.413c0-3.1 1.893-4.788 4.659-4.788 1.325 0 2.463.099 2.795.143v3.24l-1.918.001c-1.504 0-1.795.715-1.795 1.763v2.313h3.587l-.467 3.622h-3.12V24h6.116C23.405 24 24 23.405 24 22.676V1.325C24 .595 23.405 0 22.675 0z"></path></svg>
                                </a>` : ''}
                                ${window.state.settings.tiktok ? `
                                <a href="${window.state.settings.tiktok}" target="_blank" rel="noreferrer" aria-label="TikTok" class="social-badge social-badge-tiktok">
                                    <svg class="text-white" fill="currentColor" viewBox="0 0 24 24"><path d="M16.6 5.82c-1.01-.87-1.65-2.15-1.65-3.57h-3.09v12.4c0 1.43-1.16 2.6-2.6 2.6a2.6 2.6 0 01-2.6-2.6c0-1.72 1.66-3.01 3.37-2.48V9.03c-3.45-.46-6.47 2.22-6.47 5.64a5.66 5.66 0 005.7 5.7c3.13 0 5.68-2.55 5.68-5.7V9.01a7.35 7.35 0 004.3 1.38V7.3c-.98 0-1.9-.34-2.64-.98z"></path></svg>
                                </a>` : ''}
                                <a href="tel:${window.state.settings.phone}" aria-label="Call" class="social-badge social-badge-call">
                                    <svg class="text-white" fill="currentColor" viewBox="0 0 24 24"><path d="M6.62 10.79a15.05 15.05 0 006.59 6.59l2.2-2.2a1 1 0 011.01-.24c1.12.37 2.33.57 3.58.57a1 1 0 011 1V20a1 1 0 01-1 1C10.4 21 3 13.6 3 4.5a1 1 0 011-1h3.5a1 1 0 011 1c0 1.25.2 2.46.57 3.58a1 1 0 01-.25 1.01l-2.2 2.2z"></path></svg>
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
                                    <img src="${window.secureUrl(img)}" alt="${bouquet.name || 'Bouquet'} ${i+1}" class="w-full h-full object-cover" onerror="this.src='https://placehold.co/800x1000/10583f/ffffff?text=Tatka+Ful'" onload="handleProductImgLoad(this, 'https://placehold.co/800x1000/10583f/ffffff?text=Tatka+Ful')" />
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
                                    <svg class="w-5 h-5 text-[#10583f]" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg>
                                    Delivery usually takes 2-4 hours.
                                </div>
                                <button onclick="orderViaWhatsApp('${bouquet.id}', event)" class="w-full bg-[#0b2e22] hover:bg-[#10583f] text-white py-5 rounded-full uppercase tracking-widest text-sm font-bold shadow-xl hover:shadow-2xl hover:-translate-y-1 transition-all flex justify-center items-center gap-3">
                                    <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946C.06 5.348 5.397.01 12.008.01c3.202.001 6.212 1.246 8.477 3.514 2.266 2.268 3.507 5.28 3.505 8.484-.004 6.657-5.34 11.997-11.953 11.997-2.005-.001-3.973-.502-5.713-1.455L0 24zm6.59-4.846c1.6.95 3.188 1.449 4.625 1.451 5.436 0 9.851-4.398 9.854-9.807.001-2.621-1.013-5.086-2.86-6.935C16.36 1.913 13.9.894 11.285.894c-5.438 0-9.854 4.398-9.858 9.808 0 2.037.533 4.024 1.547 5.765l-.99 3.613 3.73-.973h.001a9.78 9.78 0 0 0 4.332 1.048z"/></svg>
                                    Order on WhatsApp
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
            `;
        };
    </script>
</body>
</html>
