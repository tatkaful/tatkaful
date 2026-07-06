<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
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
    
    <!-- Premium Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,500;0,600;0,700;1,400&family=Plus+Jakarta+Sans:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    
    <!-- Custom GPU-Accelerated CSS for 2GB RAM Devices -->
    <style>
        :root {
            --emerald-dark: #022c22;
            --emerald-main: #064e3b;
            --gold-accent: #d4af37;
            --bg-pearl: #fcfbf9;
        }
        body { 
            background-color: var(--bg-pearl); 
            -webkit-font-smoothing: antialiased; 
            overflow-x: hidden;
            font-family: 'Plus Jakarta Sans', sans-serif;
        }
        .font-serif { font-family: 'Playfair Display', serif; }
        
        /* Hardware Acceleration Classes */
        .gpu-accel { transform: translateZ(0); will-change: transform, opacity; }
        
        .glass-header { 
            background: rgba(252, 251, 249, 0.95); 
            border-bottom: 1px solid rgba(0,0,0,0.05); 
            box-shadow: 0 4px 20px -10px rgba(0,0,0,0.05);
            backdrop-filter: blur(8px);
            -webkit-backdrop-filter: blur(8px);
        }
        
        .luxury-card {
            background: #ffffff;
            border: 1px solid rgba(0, 0, 0, 0.04);
            box-shadow: 0 8px 15px -8px rgba(0, 0, 0, 0.05);
            transition: transform 0.2s ease, box-shadow 0.2s ease;
        }
        .luxury-card:hover {
            box-shadow: 0 12px 25px -10px rgba(6, 78, 59, 0.1);
            transform: translateY(-2px);
        }
        
        .premium-btn {
            background: linear-gradient(135deg, var(--emerald-dark) 0%, var(--emerald-main) 100%);
            box-shadow: 0 8px 15px -5px rgba(6, 78, 59, 0.3);
            transition: transform 0.2s ease, box-shadow 0.2s ease;
            color: white;
        }
        .premium-btn:hover {
            box-shadow: 0 12px 20px -5px rgba(6, 78, 59, 0.4);
            transform: translateY(-2px);
        }

        /* Hiding Scrollbars for Clean Mobile Look */
        ::-webkit-scrollbar { display: none; }
        .scrollbar-hide { -ms-overflow-style: none; scrollbar-width: none; }

        @keyframes fadeUp {
            from { opacity: 0; transform: translateY(15px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .animate-fade-up { animation: fadeUp 0.4s ease-out forwards; }
        
        @keyframes spin { 100% { transform: rotate(360deg); } }
        .animate-spin { animation: spin 1s linear infinite; }
        
        /* Custom Toast Setup */
        #toast-container {
            position: fixed;
            bottom: 20px; left: 50%;
            transform: translateX(-50%);
            z-index: 9999; display: flex; flex-direction: column; gap: 10px;
        }
        .toast {
            background: #022c22; color: white; padding: 12px 24px;
            border-radius: 50px; font-size: 12px; font-weight: 600;
            letter-spacing: 1px; text-transform: uppercase;
            box-shadow: 0 10px 20px rgba(0,0,0,0.2);
            animation: fadeUp 0.3s ease forwards;
        }
    </style>
</head>
<body class="text-gray-800 selection:bg-[#064e3b] selection:text-white">

    <!-- Toast Notification Container -->
    <div id="toast-container"></div>

    <!-- Loading Screen -->
    <div id="loader-screen" class="fixed inset-0 z-[100] bg-[#fcfbf9] flex flex-col items-center justify-center font-serif gpu-accel transition-opacity duration-500">
        <svg class="w-10 h-10 animate-spin text-[#064e3b] mb-4" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"><circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle><path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path></svg>
        <h1 class="text-2xl text-gray-900 tracking-wider">Tatka Ful</h1>
        <p class="text-[10px] text-gray-400 uppercase tracking-[0.2em] mt-2">Connecting to Live Cloud...</p>
    </div>

    <!-- Main App Container -->
    <div id="app-root" class="min-h-screen flex flex-col pb-20 md:pb-0"></div>

    <!-- SVG Icon Helpers -->
    <script>
        const ICONS = {
            search: '<svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="11" cy="11" r="8"></circle><line x1="21" y1="21" x2="16.65" y2="16.65"></line></svg>',
            x: '<svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="18" y1="6" x2="6" y2="18"></line><line x1="6" y1="6" x2="18" y2="18"></line></svg>',
            whatsapp: '<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51a12.8 12.8 0 0 0-.57-.01c-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.299 1.262.478 1.694.611.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 0 1-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 0 1-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 0 1 2.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0 0 12.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 0 0 5.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 0 0-3.48-8.413z"/></svg>',
            phone: '<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"></path></svg>',
            instagram: '<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="2" width="20" height="20" rx="5" ry="5"></rect><path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"></path><line x1="17.5" y1="6.5" x2="17.51" y2="6.5"></line></svg>',
            dashboard: '<svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="3" width="7" height="9"></rect><rect x="14" y="3" width="7" height="5"></rect><rect x="14" y="12" width="7" height="9"></rect><rect x="3" y="16" width="7" height="5"></rect></svg>',
            settings: '<svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="3"></circle><path d="M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 0 1 0 2.83 2 2 0 0 1-2.83 0l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 0 1-2 2 2 2 0 0 1-2-2v-.09A1.65 1.65 0 0 0 9 19.4a1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 0 1-2.83 0 2 2 0 0 1 0-2.83l.06-.06a1.65 1.65 0 0 0 .33-1.82 1.65 1.65 0 0 0-1.51-1H3a2 2 0 0 1-2-2 2 2 0 0 1 2-2h.09A1.65 1.65 0 0 0 4.6 9a1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 0 1 0-2.83 2 2 0 0 1 2.83 0l.06.06a1.65 1.65 0 0 0 1.82.33H9a1.65 1.65 0 0 0 1-1.51V3a2 2 0 0 1 2-2 2 2 0 0 1 2 2v.09a1.65 1.65 0 0 0 1 1.51 1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 0 1 2.83 0 2 2 0 0 1 0 2.83l-.06.06a1.65 1.65 0 0 0-.33 1.82V9a1.65 1.65 0 0 0 1.51 1H21a2 2 0 0 1 2 2 2 2 0 0 1-2 2h-.09a1.65 1.65 0 0 0-1.51 1z"></path></svg>',
            logout: '<svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M9 21H5a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h4"></path><polyline points="16 17 21 12 16 7"></polyline><line x1="21" y1="12" x2="9" y2="12"></line></svg>',
            plus: '<svg xmlns="http://www.w3.org/2000/svg" width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3"><line x1="12" y1="5" x2="12" y2="19"></line><line x1="5" y1="12" x2="19" y2="12"></line></svg>',
            edit: '<svg xmlns="http://www.w3.org/2000/svg" width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M11 4H4a2 2 0 0 0-2 2v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2v-7"></path><path d="M18.5 2.5a2.121 2.121 0 0 1 3 3L12 15l-4 1 1-4 9.5-9.5z"></path></svg>',
            trash: '<svg xmlns="http://www.w3.org/2000/svg" width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="3 6 5 6 21 6"></polyline><path d="M19 6v14a2 2 0 0 1-2 2H7a2 2 0 0 1-2-2V6m3 0V4a2 2 0 0 1 2-2h4a2 2 0 0 1 2 2v2"></path></svg>',
            eye: '<svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M1 12s4-8 11-8 11 8 11 8-4 8-11 8-11-8-11-8z"></path><circle cx="12" cy="12" r="3"></circle></svg>',
            eyeOff: '<svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M17.94 17.94A10.07 10.07 0 0 1 12 20c-7 0-11-8-11-8a18.45 18.45 0 0 1 5.06-5.94M9.9 4.24A9.12 9.12 0 0 1 12 4c7 0 11 8 11 8a18.5 18.5 0 0 1-2.16 3.19m-6.72-1.07a3 3 0 1 1-4.24-4.24"></path><line x1="1" y1="1" x2="23" y2="23"></line></svg>',
            upload: '<svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path><polyline points="17 8 12 3 7 8"></polyline><line x1="12" y1="3" x2="12" y2="15"></line></svg>',
            arrowLeft: '<svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="19" y1="12" x2="5" y2="12"></line><polyline points="12 19 5 12 12 5"></polyline></svg>'
        };

        function showToast(msg) {
            const container = document.getElementById('toast-container');
            const toast = document.createElement('div');
            toast.className = 'toast';
            toast.innerText = msg;
            container.appendChild(toast);
            setTimeout(() => {
                toast.style.opacity = '0';
                setTimeout(() => toast.remove(), 300);
            }, 3000);
        }
    </script>

    <!-- FIREBASE LIVE CLOUD SYNC LOGIC -->
    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInAnonymously, signInWithCustomToken, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { getFirestore, collection, onSnapshot, doc, setDoc, deleteDoc } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";

        // GLOBAL STATE
        window.AppState = {
            currentView: 'home', // 'home', 'admin_login', 'admin_dashboard'
            adminTab: 'bouquets', // 'bouquets', 'settings'
            bouquets: [],
            categories: ['Rose Bouquet', 'Sunflower Bouquet', 'Mixed Bouquet', 'Chocolate Bouquet', 'Money Bouquet', 'Gift Combo', 'Anniversary', 'Valentine'],
            settings: {
                logo: '', banner: '', phone: '01410619501', whatsapp: '01410619501', instagram: 'https://instagram.com/tatka_ful',
                heroSlogan: 'Elegance in Every Petal.', heroDesc: 'Curating luxury floral masterpieces for your most precious memories.'
            },
            selectedCategory: 'All',
            searchQuery: '',
            selectedBouquet: null,
            isAddingBouquet: false,
            editingId: null,
            formData: { name: '', category: 'Rose Bouquet', description: '', images: [], bestseller: false, visible: true },
            isUploading: false,
            isSaving: false,
            clickCount: 0,
            clickTimeout: null
        };

        let app, auth, db, appId, userObj = null;

        // INITIALIZE FIREBASE (Cloud Connect)
        try {
            // NOTE: If deploying outside, replace this block with your actual Firebase config object:
            // const firebaseConfig = { apiKey: "...", authDomain: "...", projectId: "...", ... };
            const firebaseConfig = typeof __firebase_config !== 'undefined' ? JSON.parse(__firebase_config) : null;
            appId = typeof __app_id !== 'undefined' ? __app_id : 'tatkaful-live-app';
            
            if (firebaseConfig) {
                app = initializeApp(firebaseConfig);
                auth = getAuth(app);
                db = getFirestore(app);
                
                // Auth Rule 3
                const initAuth = async () => {
                    try {
                        if (typeof __initial_auth_token !== 'undefined' && __initial_auth_token) {
                            await signInWithCustomToken(auth, __initial_auth_token);
                        } else {
                            await signInAnonymously(auth);
                        }
                    } catch (e) { console.error("Auth Err", e); }
                };
                initAuth();

                onAuthStateChanged(auth, (u) => {
                    userObj = u;
                    if(u) attachListeners();
                });
            } else {
                console.warn("No Firebase Config found. App will run in offline demo mode.");
                setTimeout(() => { document.getElementById('loader-screen').classList.add('opacity-0', 'pointer-events-none'); renderApp(); }, 1000);
            }
        } catch (error) {
            console.error("Firebase Error:", error);
        }

        function attachListeners() {
            if (!userObj || !db) return;
            
            // Listen Bouquets
            const bouquetsRef = collection(db, 'artifacts', appId, 'public', 'data', 'bouquets');
            onSnapshot(bouquetsRef, (snapshot) => {
                const fetched = snapshot.docs.map(doc => ({ id: doc.id, ...doc.data() }));
                fetched.sort((a, b) => (b.createdAt || 0) - (a.createdAt || 0));
                window.AppState.bouquets = fetched;
                document.getElementById('loader-screen').classList.add('opacity-0', 'pointer-events-none');
                renderApp();
            }, (error) => console.error(error));

            // Listen Settings
            const settingsRef = collection(db, 'artifacts', appId, 'public', 'data', 'settings');
            onSnapshot(settingsRef, (snapshot) => {
                if (!snapshot.empty) {
                    window.AppState.settings = snapshot.docs[0].data();
                    renderApp();
                }
            }, (error) => console.error(error));
        }

        // ==========================================
        // UI RENDERING ENGINE
        // ==========================================
        function renderApp() {
            const root = document.getElementById('app-root');
            if (window.AppState.currentView === 'home') renderHome(root);
            else if (window.AppState.currentView === 'admin_login') renderAdminLogin(root);
            else if (window.AppState.currentView === 'admin_dashboard') renderAdminDashboard(root);
            
            if (window.AppState.selectedBouquet && window.AppState.currentView === 'home') {
                renderDetailModal();
            }
        }

        // FORMAT WHATSAPP NUMBER
        function getWaNum() {
            let n = window.AppState.settings.whatsapp.replace(/[^0-9]/g, '');
            if (n.startsWith('0')) n = '88' + n;
            return n;
        }

        // --- RENDER 1: HOME PAGE ---
        function renderHome(container) {
            const s = window.AppState;
            let displayBq = s.bouquets.filter(b => b.visible !== false);
            if (s.selectedCategory !== 'All') displayBq = displayBq.filter(b => b.category === s.selectedCategory);
            if (s.searchQuery) {
                const q = s.searchQuery.toLowerCase();
                displayBq = displayBq.filter(b => b.name.toLowerCase().includes(q) || b.category.toLowerCase().includes(q));
            }

            container.innerHTML = `
                <!-- Navbar -->
                <nav class="fixed w-full top-0 z-40 glass-header gpu-accel">
                    <div class="max-w-7xl mx-auto px-4 md:px-6 h-16 md:h-24 flex items-center justify-between">
                        <div class="flex items-center gap-3 cursor-pointer" onclick="window.navHome()">
                            ${s.settings.logo ? `<img src="${s.settings.logo}" class="w-10 h-10 md:w-12 md:h-12 rounded-full object-cover shadow-sm bg-white" />` : `<div class="w-10 h-10 md:w-12 md:h-12 rounded-full bg-[#064e3b] text-white flex items-center justify-center font-serif text-lg shadow-sm">TF</div>`}
                            <span class="text-xl md:text-2xl font-serif font-semibold text-gray-900 tracking-wide">Tatka Ful</span>
                        </div>
                        <a href="https://wa.me/${getWaNum()}" target="_blank" class="premium-btn px-5 py-2 md:py-2.5 rounded-full tracking-widest text-[10px] md:text-xs font-bold uppercase shadow-md">Inquire</a>
                    </div>
                </nav>

                <!-- Hero -->
                <section class="relative pt-24 pb-12 md:pt-36 md:pb-24 px-4 flex items-center justify-center min-h-[45vh] md:min-h-[55vh] overflow-hidden gpu-accel">
                    <div class="absolute inset-0 z-0">
                        ${s.settings.banner ? `<img src="${s.settings.banner}" class="w-full h-full object-cover opacity-30" loading="lazy" />` : `<div class="w-full h-full bg-gradient-to-br from-[#ecfdf5]/50 to-[#fcfbf9]"></div>`}
                        <div class="absolute inset-0 bg-gradient-to-b from-[#fcfbf9]/90 via-[#fcfbf9]/50 to-[#fcfbf9]"></div>
                    </div>
                    <div class="max-w-3xl mx-auto text-center relative z-10 animate-fade-up w-full">
                        <h1 class="text-3xl md:text-6xl font-serif text-gray-900 mb-4 md:mb-6 leading-tight tracking-tight">${s.settings.heroSlogan}</h1>
                        <p class="text-sm md:text-lg text-gray-600 mb-8 max-w-xl mx-auto font-light leading-relaxed px-2">${s.settings.heroDesc}</p>
                        
                        <div class="max-w-md mx-auto relative px-2">
                           <input type="text" placeholder="Search designs..." value="${s.searchQuery}" oninput="window.setSearch(this.value)" class="w-full pl-10 pr-10 py-3.5 md:py-4 bg-white/95 border border-gray-200 rounded-full shadow-lg outline-none focus:border-[#064e3b] focus:ring-2 focus:ring-[#064e3b]/20 transition-all font-medium text-sm" />
                           <div class="absolute left-6 top-1/2 -translate-y-1/2 text-gray-400">${ICONS.search}</div>
                           ${s.searchQuery ? `<button onclick="window.setSearch('')" class="absolute right-6 top-1/2 -translate-y-1/2 text-gray-400 bg-gray-100 rounded-full p-1">${ICONS.x}</button>` : ''}
                        </div>
                    </div>
                </section>

                <!-- Filters -->
                <section class="px-2 py-3 sticky top-16 md:top-24 glass-header z-30 shadow-sm gpu-accel w-full overflow-hidden">
                    <div class="max-w-7xl mx-auto flex gap-2 overflow-x-auto pb-1 snap-x px-2 scrollbar-hide">
                        <button onclick="window.setCat('All')" class="snap-start whitespace-nowrap px-4 py-2 md:py-2.5 rounded-full transition-all text-[10px] md:text-xs font-bold tracking-widest uppercase border ${s.selectedCategory === 'All' ? 'bg-[#022c22] text-white border-[#022c22] shadow-md' : 'bg-white text-gray-600 border-gray-200'}">All Designs</button>
                        ${s.categories.map(cat => `<button onclick="window.setCat('${cat}')" class="snap-start whitespace-nowrap px-4 py-2 md:py-2.5 rounded-full transition-all text-[10px] md:text-xs font-bold tracking-widest uppercase border ${s.selectedCategory === cat ? 'bg-[#022c22] text-white border-[#022c22] shadow-md' : 'bg-white text-gray-600 border-gray-200'}">${cat}</button>`).join('')}
                    </div>
                </section>

                <!-- Grid -->
                <section class="px-3 md:px-6 py-8 md:py-10 max-w-7xl mx-auto min-h-[50vh]">
                    ${displayBq.length === 0 ? `
                        <div class="text-center py-16 bg-white border border-gray-100 rounded-2xl shadow-sm mx-2">
                            <h3 class="text-lg font-serif text-gray-900">No bouquets found</h3>
                        </div>
                    ` : `
                        <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-x-3 gap-y-6 md:gap-x-6 md:gap-y-10">
                            ${displayBq.map(bq => `
                                <div class="group cursor-pointer flex flex-col animate-fade-up gpu-accel" onclick="window.openDetail('${bq.id}')">
                                    <div class="relative aspect-[4/5] rounded-xl overflow-hidden luxury-card mb-2 bg-gray-50">
                                        ${bq.images && bq.images[0] ? `<img src="${bq.images[0]}" class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-105" loading="lazy" />` : `<div class="w-full h-full flex items-center justify-center text-gray-300 text-[10px]">No Image</div>`}
                                        ${bq.bestseller ? `<div class="absolute top-2 left-2 bg-white/95 backdrop-blur-md text-[#b8860b] text-[8px] font-bold uppercase tracking-widest px-2 py-1 rounded-md shadow-sm">Signature</div>` : ''}
                                    </div>
                                    <div class="px-1">
                                        <p class="text-[8px] md:text-[10px] font-bold tracking-[0.2em] text-[#064e3b] uppercase mb-1 truncate">${bq.category}</p>
                                        <h3 class="text-sm md:text-lg font-serif text-gray-900 mb-1 group-hover:text-[#064e3b] transition-colors truncate">${bq.name}</h3>
                                        <p class="text-gray-500 text-[10px] md:text-xs line-clamp-2 leading-relaxed hidden md:block">${bq.description}</p>
                                    </div>
                                </div>
                            `).join('')}
                        </div>
                    `}
                </section>

                <!-- Floating WA -->
                <div class="fixed bottom-4 right-4 md:bottom-8 md:right-8 z-40">
                   <a href="https://wa.me/${getWaNum()}" target="_blank" class="w-12 h-12 md:w-16 md:h-16 bg-[#25D366] text-white rounded-full flex items-center justify-center hover:scale-105 transition-transform shadow-[0_8px_20px_rgba(37,211,102,0.4)] gpu-accel">
                    ${ICONS.whatsapp}
                  </a>
                </div>

                <!-- Footer -->
                <footer class="bg-white border-t border-gray-100 pt-12 pb-8 px-4 mt-8">
                    <div class="max-w-7xl mx-auto flex flex-col md:flex-row justify-between items-center gap-8 text-center md:text-left">
                        <div class="flex flex-col items-center md:items-start max-w-sm">
                            ${s.settings.logo ? `<img src="${s.settings.logo}" class="w-14 h-14 rounded-full mb-3 shadow-sm object-cover bg-white" loading="lazy" />` : `<div class="w-14 h-14 rounded-full bg-[#064e3b] text-white flex items-center justify-center font-serif text-xl mb-3 shadow-sm">TF</div>`}
                            <h3 class="font-serif text-xl md:text-2xl text-gray-900 mb-2">Tatka Ful</h3>
                            <p class="text-gray-500 text-[11px] md:text-xs leading-relaxed font-light">The ultimate destination for luxury floral design.</p>
                        </div>
                        <div class="flex flex-col items-center md:items-end">
                            <div class="flex gap-3 mt-3">
                                <a href="${s.settings.instagram}" target="_blank" class="w-9 h-9 rounded-full border border-gray-200 flex items-center justify-center text-gray-600 hover:text-[#064e3b] bg-gray-50">${ICONS.instagram}</a>
                                <a href="tel:${s.settings.phone}" class="w-9 h-9 rounded-full border border-gray-200 flex items-center justify-center text-gray-600 hover:text-[#064e3b] bg-gray-50">${ICONS.phone}</a>
                            </div>
                        </div>
                    </div>
                    <div class="max-w-7xl mx-auto mt-10 pt-6 border-t border-gray-100 text-center">
                        <p onclick="window.secretTap()" class="text-[9px] md:text-[10px] font-medium tracking-widest uppercase text-gray-400 select-none cursor-pointer py-2 inline-block">
                            &copy; ${new Date().getFullYear()} Tatka Ful. Crafted with elegance.
                        </p>
                    </div>
                </footer>
                
                <div id="modal-root"></div>
            `;
        }

        // --- RENDER MODAL ---
        function renderDetailModal() {
            const bq = window.AppState.selectedBouquet;
            if(!bq) return;
            const root = document.getElementById('modal-root');
            root.innerHTML = `
                <div class="fixed inset-0 z-50 flex items-end md:items-center justify-center p-0 md:p-8 gpu-accel">
                    <div class="absolute inset-0 bg-black/60 backdrop-blur-sm" onclick="window.closeDetail()"></div>
                    <div class="relative bg-white w-full h-[85vh] md:h-auto md:max-h-[85vh] md:max-w-4xl rounded-t-2xl md:rounded-2xl shadow-2xl overflow-hidden flex flex-col md:flex-row animate-fade-up">
                        <button onclick="window.closeDetail()" class="absolute top-3 right-3 z-20 w-8 h-8 bg-white/90 shadow-md rounded-full flex items-center justify-center text-gray-900">${ICONS.x}</button>
                        
                        <div class="w-full md:w-1/2 bg-[#fcfbf9] h-[40vh] md:h-[60vh] overflow-x-auto md:overflow-y-auto flex md:flex-col snap-x md:snap-y snap-mandatory relative border-b md:border-b-0 md:border-r border-gray-100 scrollbar-hide">
                            ${bq.images && bq.images.length > 0 ? bq.images.map(img => `<div class="w-full h-full min-w-full md:min-h-full snap-center relative shrink-0"><img src="${img}" class="w-full h-full object-cover" /></div>`).join('') : '<div class="w-full h-full flex items-center justify-center text-gray-300 text-xs">No Images</div>'}
                            ${bq.images?.length > 1 ? '<div class="absolute bottom-3 left-0 right-0 flex justify-center pointer-events-none"><span class="bg-black/50 text-white text-[8px] px-3 py-1.5 rounded-full tracking-widest uppercase">Swipe for more</span></div>' : ''}
                        </div>
                        
                        <div class="w-full md:w-1/2 p-5 md:p-10 flex flex-col h-[45vh] md:h-[60vh] overflow-y-auto bg-white">
                            <p class="text-[9px] font-bold tracking-[0.3em] text-[#064e3b] uppercase mb-1.5">${bq.category}</p>
                            <h2 class="text-2xl md:text-3xl font-serif text-gray-900 mb-3">${bq.name}</h2>
                            <div class="w-8 h-[2px] bg-[#d4af37] mb-4"></div>
                            <p class="text-gray-600 text-[11px] md:text-sm whitespace-pre-line mb-6">${bq.description}</p>
                            
                            <div class="mt-auto space-y-2.5 pb-4 md:pb-0">
                                <a href="https://wa.me/${getWaNum()}?text=${encodeURIComponent(`Hello TATKA-FUL! I'm interested in ordering the '${bq.name}'. Please share the price and details.`)}" target="_blank" class="w-full premium-btn text-white py-3.5 rounded-xl flex items-center justify-center gap-2 text-[11px] font-bold uppercase tracking-widest">
                                    WhatsApp Order
                                </a>
                                <a href="tel:${window.AppState.settings.phone}" class="w-full bg-gray-50 text-gray-900 py-3.5 rounded-xl flex items-center justify-center gap-2 text-[11px] font-bold uppercase tracking-widest border border-gray-200 hover:bg-gray-100">
                                    Call Studio
                                </a>
                            </div>
                        </div>
                    </div>
                </div>
            `;
        }

        // --- RENDER 2: ADMIN LOGIN ---
        function renderAdminLogin(container) {
            container.innerHTML = `
                <div class="min-h-screen bg-[#fcfbf9] flex items-center justify-center px-4">
                    <div class="bg-white p-8 rounded-2xl shadow-xl w-full max-w-xs md:max-w-sm border border-gray-100">
                        <div class="flex justify-center mb-5"><div class="w-16 h-16 rounded-full bg-[#064e3b] text-white flex items-center justify-center font-serif text-2xl">TF</div></div>
                        <h2 class="text-xl font-serif text-center text-gray-900 mb-1">Studio Portal</h2>
                        <p class="text-center text-gray-400 mb-6 text-[9px] font-bold tracking-[0.2em] uppercase">Live Cloud Connect</p>
                        
                        <div class="mb-5">
                            <input id="admin-pass" type="password" placeholder="PASSCODE" class="w-full px-4 py-3 bg-gray-50 border border-gray-200 rounded-xl focus:border-[#064e3b] text-center tracking-[0.5em] text-sm font-bold uppercase outline-none" />
                        </div>
                        <button onclick="window.checkLogin()" class="w-full premium-btn text-white py-3 rounded-xl font-bold uppercase tracking-widest text-[10px]">Connect</button>
                        <button onclick="window.navHome()" class="w-full mt-3 text-gray-400 hover:text-gray-900 py-2 text-[9px] uppercase tracking-widest font-bold">Cancel</button>
                    </div>
                </div>
            `;
        }

        // --- RENDER 3: ADMIN DASHBOARD ---
        function renderAdminDashboard(container) {
            const s = window.AppState;
            container.innerHTML = `
                <div class="min-h-screen bg-gray-50 flex flex-col md:flex-row">
                    <!-- Sidebar -->
                    <aside class="w-full md:w-64 bg-white border-b md:border-b-0 md:border-r border-gray-200 flex flex-col shrink-0 z-10 shadow-sm">
                        <div class="p-4 md:p-6 border-b border-gray-100 flex items-center justify-between md:justify-start gap-3">
                            <div class="flex items-center gap-3">
                                <div class="w-8 h-8 md:w-10 md:h-10 rounded-full bg-[#064e3b] text-white flex items-center justify-center font-serif text-sm">TF</div>
                                <div>
                                    <span class="font-serif text-sm md:text-lg text-gray-900 block leading-tight">Admin</span>
                                    <span class="text-[7px] md:text-[8px] uppercase tracking-widest text-emerald-600 font-bold flex items-center gap-1 mt-0.5"><span class="w-1.5 h-1.5 rounded-full bg-emerald-500 animate-pulse"></span> Cloud Sync Active</span>
                                </div>
                            </div>
                        </div>
                        <div class="p-2 md:p-4 flex flex-row md:flex-col gap-2 overflow-x-auto flex-1">
                            <button onclick="window.setAdminTab('bouquets')" class="flex-1 md:flex-none flex items-center justify-center md:justify-start gap-2 px-3 py-2.5 rounded-lg transition-all font-semibold text-[10px] tracking-wide uppercase ${s.adminTab === 'bouquets' ? 'bg-[#064e3b] text-white shadow-sm' : 'text-gray-500 hover:bg-gray-100'}">${ICONS.dashboard} Designs</button>
                            <button onclick="window.setAdminTab('settings')" class="flex-1 md:flex-none flex items-center justify-center md:justify-start gap-2 px-3 py-2.5 rounded-lg transition-all font-semibold text-[10px] tracking-wide uppercase ${s.adminTab === 'settings' ? 'bg-[#064e3b] text-white shadow-sm' : 'text-gray-500 hover:bg-gray-100'}">${ICONS.settings} Brand</button>
                        </div>
                        <div class="hidden md:block p-4 border-t border-gray-100">
                            <button onclick="window.navHome()" class="w-full flex items-center justify-center gap-2 px-4 py-3 rounded-xl bg-gray-100 text-gray-600 font-bold text-[10px] uppercase tracking-widest hover:text-red-600">${ICONS.logout} Exit Admin</button>
                        </div>
                    </aside>

                    <!-- Main -->
                    <main class="flex-1 p-3 md:p-8 overflow-y-auto" id="admin-main">
                        ${s.adminTab === 'bouquets' && !s.isAddingBouquet ? renderAdminList() : ''}
                        ${s.adminTab === 'bouquets' && s.isAddingBouquet ? renderAdminForm() : ''}
                        ${s.adminTab === 'settings' ? renderAdminSettings() : ''}
                    </main>
                </div>
            `;
        }

        function renderAdminList() {
            const bqs = window.AppState.bouquets;
            return `
                <div class="max-w-5xl mx-auto animate-fade-up">
                    <div class="flex justify-between items-center mb-4 gap-3">
                        <h1 class="text-xl md:text-3xl font-serif text-gray-900">Cloud Inventory</h1>
                        <button onclick="window.openAddForm()" class="premium-btn px-4 py-2.5 rounded-full flex items-center gap-1.5 font-bold uppercase tracking-widest text-[9px]">${ICONS.plus} Add New</button>
                    </div>
                    <div class="bg-white border border-gray-200 rounded-xl overflow-hidden shadow-sm">
                        <div class="overflow-x-auto">
                            <table class="w-full text-left border-collapse min-w-[400px]">
                                <thead>
                                    <tr class="border-b border-gray-100 bg-gray-50">
                                        <th class="p-3 text-[9px] font-bold text-gray-400 uppercase tracking-widest">Item</th>
                                        <th class="p-3 text-[9px] font-bold text-gray-400 uppercase tracking-widest text-center">Visible</th>
                                        <th class="p-3 text-[9px] font-bold text-gray-400 uppercase tracking-widest text-right">Actions</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    ${bqs.map(b => `
                                        <tr class="hover:bg-gray-50/50 border-b border-gray-50">
                                            <td class="p-3 flex items-center gap-2">
                                                <div class="w-10 h-10 rounded-md bg-gray-100 overflow-hidden shrink-0">${b.images && b.images[0] ? `<img src="${b.images[0]}" class="w-full h-full object-cover" />` : ''}</div>
                                                <div>
                                                    <p class="font-serif text-xs text-gray-900 truncate max-w-[120px]">${b.name}</p>
                                                    <p class="text-[8px] text-gray-500">${b.category}</p>
                                                </div>
                                            </td>
                                            <td class="p-3 text-center">
                                                <button onclick="window.toggleVis('${b.id}', ${b.visible})" class="p-1.5 rounded-full ${b.visible ? 'text-[#064e3b] bg-green-50' : 'text-gray-400 bg-gray-100'}">${b.visible ? ICONS.eye : ICONS.eyeOff}</button>
                                            </td>
                                            <td class="p-3 text-right space-x-1.5">
                                                <button onclick="window.editBq('${b.id}')" class="p-1.5 text-blue-600 bg-blue-50 rounded-full inline-block">${ICONS.edit}</button>
                                                <button onclick="window.deleteBq('${b.id}')" class="p-1.5 text-red-600 bg-red-50 rounded-full inline-block">${ICONS.trash}</button>
                                            </td>
                                        </tr>
                                    `).join('')}
                                    ${bqs.length === 0 ? '<tr><td colspan="3" class="p-6 text-center text-gray-400 text-xs">No items in cloud.</td></tr>' : ''}
                                </tbody>
                            </table>
                        </div>
                    </div>
                </div>
            `;
        }

        function renderAdminForm() {
            const f = window.AppState.formData;
            const s = window.AppState;
            return `
                <div class="max-w-2xl mx-auto bg-white p-5 border border-gray-200 rounded-2xl shadow-sm animate-fade-up">
                    <div class="flex items-center gap-3 mb-5 border-b border-gray-100 pb-3">
                        <button onclick="window.closeForm()" class="p-1.5 bg-gray-100 rounded-full text-gray-600">${ICONS.arrowLeft}</button>
                        <h2 class="text-xl font-serif text-gray-900">${s.editingId ? 'Edit Design' : 'Create New'}</h2>
                    </div>
                    
                    <div class="bg-gray-50 p-3 rounded-lg border border-gray-200 mb-4">
                        <label class="block text-[9px] font-bold tracking-widest text-gray-500 mb-2 uppercase">Images (Max 5)</label>
                        <div class="grid grid-cols-3 sm:grid-cols-5 gap-2">
                            ${f.images.map((img, idx) => `
                                <div class="relative aspect-[4/5] rounded-md overflow-hidden group border border-gray-300">
                                    <img src="${img}" class="w-full h-full object-cover" />
                                    <button type="button" onclick="window.removeImg(${idx})" class="absolute inset-0 bg-red-900/60 text-white flex items-center justify-center opacity-0 group-hover:opacity-100">${ICONS.trash}</button>
                                </div>
                            `).join('')}
                            ${f.images.length < 5 ? `
                                <label class="aspect-[4/5] rounded-md border-2 border-dashed border-gray-400 hover:border-[#064e3b] flex flex-col items-center justify-center cursor-pointer text-gray-500 bg-white">
                                    ${ICONS.upload}
                                    <span class="text-[7px] font-bold uppercase mt-1">${s.isUploading ? 'Wait...' : 'Add'}</span>
                                    <input type="file" accept="image/*" multiple class="hidden" onchange="window.handleUpload(event, 'images')" disabled="${s.isUploading}" />
                                </label>
                            ` : ''}
                        </div>
                    </div>

                    <div class="space-y-3">
                        <input id="f-name" type="text" placeholder="Name" value="${f.name}" class="w-full px-3 py-2 border rounded-lg text-sm outline-none focus:border-[#064e3b]" />
                        <select id="f-cat" class="w-full px-3 py-2 border rounded-lg text-sm outline-none focus:border-[#064e3b]">
                            ${s.categories.map(c => `<option value="${c}" ${f.category === c ? 'selected' : ''}>${c}</option>`).join('')}
                        </select>
                        <textarea id="f-desc" rows="3" placeholder="Description" class="w-full px-3 py-2 border rounded-lg text-sm outline-none focus:border-[#064e3b] resize-none">${f.description}</textarea>
                    </div>

                    <div class="flex gap-4 pt-3">
                        <label class="flex items-center gap-1.5 text-[10px] font-bold text-gray-600 uppercase"><input id="f-star" type="checkbox" ${f.bestseller ? 'checked' : ''} class="w-4 h-4 accent-[#064e3b]" /> Signature</label>
                        <label class="flex items-center gap-1.5 text-[10px] font-bold text-gray-600 uppercase"><input id="f-vis" type="checkbox" ${f.visible ? 'checked' : ''} class="w-4 h-4 accent-[#064e3b]" /> Public Display</label>
                    </div>

                    <button onclick="window.submitForm()" class="w-full mt-5 premium-btn py-3 rounded-lg font-bold uppercase tracking-widest text-[10px] disabled:opacity-50">
                        ${s.isSaving ? 'Syncing...' : 'Save to Cloud'}
                    </button>
                </div>
            `;
        }

        function renderAdminSettings() {
            const set = window.AppState.settings;
            return `
                <div class="max-w-2xl mx-auto bg-white p-5 border border-gray-200 rounded-2xl shadow-sm animate-fade-up">
                    <h2 class="text-xl font-serif text-gray-900 mb-4 border-b border-gray-100 pb-2">Brand Config</h2>
                    
                    <div class="grid grid-cols-2 gap-4 mb-5">
                        <div class="bg-gray-50 p-3 rounded-xl border border-gray-200 text-center">
                            <p class="text-[9px] font-bold tracking-widest text-gray-500 mb-2 uppercase">Brand Logo</p>
                            <div class="w-12 h-12 mx-auto bg-white rounded-full border border-gray-300 mb-2 overflow-hidden">${set.logo ? `<img src="${set.logo}" class="w-full h-full object-cover"/>` : ''}</div>
                            <label class="text-[8px] font-bold uppercase bg-white border border-gray-300 px-2 py-1 rounded cursor-pointer">Change Logo<input type="file" accept="image/*" class="hidden" onchange="window.handleUpload(event, 'logo')" /></label>
                        </div>
                        <div class="bg-gray-50 p-3 rounded-xl border border-gray-200 text-center">
                            <p class="text-[9px] font-bold tracking-widest text-gray-500 mb-2 uppercase">Hero Banner</p>
                            <div class="w-full h-12 mx-auto bg-white border border-gray-300 mb-2 overflow-hidden rounded">${set.banner ? `<img src="${set.banner}" class="w-full h-full object-cover"/>` : ''}</div>
                            <label class="text-[8px] font-bold uppercase bg-white border border-gray-300 px-2 py-1 rounded cursor-pointer">Change Banner<input type="file" accept="image/*" class="hidden" onchange="window.handleUpload(event, 'banner')" /></label>
                        </div>
                    </div>

                    <div class="space-y-3">
                        <input id="s-slogan" value="${set.heroSlogan}" placeholder="Slogan" class="w-full px-3 py-2 bg-gray-50 border rounded-lg text-xs outline-none focus:border-[#064e3b]" />
                        <textarea id="s-desc" rows="2" placeholder="Description" class="w-full px-3 py-2 bg-gray-50 border rounded-lg text-xs outline-none focus:border-[#064e3b]">${set.heroDesc}</textarea>
                        <div class="grid grid-cols-2 gap-2">
                            <input id="s-wa" value="${set.whatsapp}" placeholder="WhatsApp" class="w-full px-3 py-2 bg-gray-50 border rounded-lg text-xs outline-none" />
                            <input id="s-phone" value="${set.phone}" placeholder="Phone" class="w-full px-3 py-2 bg-gray-50 border rounded-lg text-xs outline-none" />
                        </div>
                        <input id="s-insta" value="${set.instagram}" placeholder="Insta Link" class="w-full px-3 py-2 bg-gray-50 border rounded-lg text-xs outline-none" />
                    </div>

                    <button onclick="window.saveSet()" class="w-full mt-4 premium-btn py-3 rounded-lg font-bold uppercase tracking-widest text-[10px]">Sync Settings</button>
                </div>
            `;
        }


        // ==========================================
        // EVENT HANDLERS (Attached to Window for HTML logic)
        // ==========================================
        window.navHome = () => { window.AppState.currentView = 'home'; renderApp(); };
        window.setSearch = (val) => { window.AppState.searchQuery = val; renderApp(); };
        window.setCat = (val) => { window.AppState.selectedCategory = val; renderApp(); };
        window.openDetail = (id) => { window.AppState.selectedBouquet = window.AppState.bouquets.find(b=>b.id===id); renderApp(); };
        window.closeDetail = () => { window.AppState.selectedBouquet = null; document.getElementById('modal-root').innerHTML = ''; };

        // 4-Tap Logic
        window.secretTap = () => {
            let s = window.AppState;
            s.clickCount++;
            if(s.clickCount >= 4) { s.currentView = 'admin_login'; s.clickCount = 0; renderApp(); window.scrollTo(0,0); return; }
            if(s.clickTimeout) clearTimeout(s.clickTimeout);
            s.clickTimeout = setTimeout(() => s.clickCount = 0, 1500);
        };

        window.checkLogin = () => {
            const pass = document.getElementById('admin-pass').value;
            if(pass === 'gym') { window.AppState.currentView = 'admin_dashboard'; renderApp(); }
            else { showToast("Invalid Passcode"); }
        };

        window.setAdminTab = (tab) => { window.AppState.adminTab = tab; window.AppState.isAddingBouquet = false; renderApp(); };
        window.openAddForm = () => { 
            window.AppState.formData = { name:'', category: window.AppState.categories[0], description:'', images:[], bestseller:false, visible:true };
            window.AppState.editingId = null; window.AppState.isAddingBouquet = true; renderApp(); 
        };
        window.closeForm = () => { window.AppState.isAddingBouquet = false; renderApp(); };
        
        // Form & DB Actions
        window.toggleVis = async (id, cur) => {
            if(!userObj || !db) return showToast("No Cloud Connection");
            await setDoc(doc(db, 'artifacts', appId, 'public', 'data', 'bouquets', id), { visible: !cur }, { merge: true });
        };
        window.deleteBq = async (id) => {
            if(!userObj || !db) return;
            if(confirm("Delete from cloud permanently?")) {
                await deleteDoc(doc(db, 'artifacts', appId, 'public', 'data', 'bouquets', id));
                showToast("Deleted");
            }
        };
        window.editBq = (id) => {
            const b = window.AppState.bouquets.find(x=>x.id===id);
            window.AppState.formData = {...b, images: [...b.images]};
            window.AppState.editingId = id; window.AppState.isAddingBouquet = true; renderApp();
        };
        
        window.removeImg = (idx) => {
            window.AppState.formData.images.splice(idx, 1);
            renderApp();
        };

        // AGGRESSIVE COMPRESSION (Crucial for 2GB RAM & Firestore limits)
        const processImage = (file, maxWidth, quality) => {
            return new Promise((resolve) => {
                const reader = new FileReader();
                reader.onload = (e) => {
                    const img = new Image();
                    img.onload = () => {
                        const canvas = document.createElement('canvas');
                        let scale = maxWidth / img.width;
                        if (scale > 1) scale = 1;
                        canvas.width = img.width * scale; canvas.height = img.height * scale;
                        const ctx = canvas.getContext('2d');
                        ctx.drawImage(img, 0, 0, canvas.width, canvas.height);
                        resolve(canvas.toDataURL('image/jpeg', quality)); 
                    };
                    img.src = e.target.result;
                };
                reader.readAsDataURL(file);
            });
        };

        window.handleUpload = async (e, type) => {
            const files = Array.from(e.target.files);
            if(!files.length) return;
            window.AppState.isUploading = true; renderApp();
            
            try {
                if(type === 'images') {
                    if (window.AppState.formData.images.length + files.length > 5) { showToast("Max 5 images"); return; }
                    const processed = await Promise.all(files.map(f => processImage(f, 600, 0.5))); // Highly compressed
                    window.AppState.formData.images.push(...processed);
                } else if(type === 'logo') {
                    window.AppState.settings.logo = await processImage(files[0], 300, 0.8);
                } else if(type === 'banner') {
                    window.AppState.settings.banner = await processImage(files[0], 1000, 0.6);
                }
            } catch(err) { showToast("Upload Failed"); }
            
            window.AppState.isUploading = false; renderApp();
        };

        window.submitForm = async () => {
            if(!userObj || !db) return showToast("No Cloud Connection");
            window.AppState.isSaving = true; renderApp();
            
            const f = window.AppState.formData;
            f.name = document.getElementById('f-name').value;
            f.category = document.getElementById('f-cat').value;
            f.description = document.getElementById('f-desc').value;
            f.bestseller = document.getElementById('f-star').checked;
            f.visible = document.getElementById('f-vis').checked;

            try {
                const bRef = collection(db, 'artifacts', appId, 'public', 'data', 'bouquets');
                if (window.AppState.editingId) {
                    await setDoc(doc(bRef, window.AppState.editingId), { ...f, updatedAt: Date.now() }, { merge: true });
                } else {
                    await setDoc(doc(bRef, Date.now().toString()), { ...f, createdAt: Date.now() });
                }
                showToast("Saved to Cloud!");
                window.AppState.isAddingBouquet = false;
            } catch(e) { showToast("Error Saving"); }
            
            window.AppState.isSaving = false; renderApp();
        };

        window.saveSet = async () => {
            if(!userObj || !db) return showToast("No Cloud Connection");
            window.AppState.isSaving = true; renderApp();
            
            const s = window.AppState.settings;
            s.heroSlogan = document.getElementById('s-slogan').value;
            s.heroDesc = document.getElementById('s-desc').value;
            s.whatsapp = document.getElementById('s-wa').value;
            s.phone = document.getElementById('s-phone').value;
            s.instagram = document.getElementById('s-insta').value;

            try {
                await setDoc(doc(db, 'artifacts', appId, 'public', 'data', 'settings', 'main'), s, { merge: true });
                showToast("Settings Synced");
            } catch(e) { showToast("Error Syncing"); }
            window.AppState.isSaving = false; renderApp();
        };

    </script>
</body>
</html>


