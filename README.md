import React, { useState, useEffect, useRef } from 'react';
import { 
  Phone, MessageCircle, Instagram, ChevronRight, 
  LayoutDashboard, Image as ImageIcon, Settings, 
  Plus, Trash2, Edit, Star, Eye, EyeOff, Upload, ArrowLeft, LogOut, Loader2, Search, X
} from 'lucide-react';

// ==========================================
// 1. FIREBASE CLOUD SETUP (Global Live Sync)
// ==========================================
import { initializeApp } from 'firebase/app';
import { getAuth, signInWithCustomToken, signInAnonymously, onAuthStateChanged } from 'firebase/auth';
import { getFirestore, collection, onSnapshot, doc, setDoc, deleteDoc } from 'firebase/firestore';

// Initialize Firebase safely
let app, auth, db, appId;
try {
  const firebaseConfig = typeof __firebase_config !== 'undefined' ? JSON.parse(__firebase_config) : null;
  if (firebaseConfig) {
    app = initializeApp(firebaseConfig);
    auth = getAuth(app);
    db = getFirestore(app);
    appId = typeof __app_id !== 'undefined' ? __app_id : 'tatkaful-live-app';
  }
} catch (error) {
  console.error("Firebase init error:", error);
}

// ==========================================
// 2. STYLES (Optimized for 2GB RAM & Premium UI)
// ==========================================
const STYLES = `
  @import url('https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,500;0,600;0,700;1,400&family=Plus+Jakarta+Sans:wght@300;400;500;600;700&display=swap');
  
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
  }
  
  .font-serif { font-family: 'Playfair Display', serif; }
  .font-sans { font-family: 'Plus Jakarta Sans', sans-serif; }
  
  /* GPU Acceleration for smooth mobile scrolling (No hang on 2GB RAM) */
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
  }
  .premium-btn:hover {
    box-shadow: 0 12px 20px -5px rgba(6, 78, 59, 0.4);
    transform: translateY(-2px);
  }

  ::-webkit-scrollbar { display: none; }
  
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(15px); }
    to { opacity: 1; transform: translateY(0); }
  }
  .animate-fade-up { animation: fadeUp 0.4s ease-out forwards; }
`;

const INITIAL_CATEGORIES = [
  'Rose Bouquet', 'Sunflower Bouquet', 'Mixed Bouquet', 
  'Chocolate Bouquet', 'Money Bouquet', 'Gift Combo', 
  'Anniversary', 'Valentine'
];

const DEFAULT_SETTINGS = {
  logo: 'IMG_0254.png', 
  banner: 'IMG_0255.png', 
  phone: '01410619501', 
  whatsapp: '01410619501', 
  instagram: 'https://instagram.com/tatka_ful',
  heroSlogan: 'Elegance in Every Petal.',
  heroDesc: 'Curating luxury floral masterpieces for your most precious memories.'
};

const formatWhatsApp = (number) => {
  let formatted = number?.replace(/[^0-9]/g, '') || '';
  if (formatted.startsWith('0')) formatted = '88' + formatted;
  return formatted;
};

// ==========================================
// 3. MAIN APP COMPONENT
// ==========================================
export default function TatkaFulApp() {
  const [user, setUser] = useState(null);
  const [isInitializing, setIsInitializing] = useState(true);
  
  // Data State (Synced from Cloud)
  const [bouquets, setBouquets] = useState([]);
  const [settings, setSettings] = useState(DEFAULT_SETTINGS);
  
  // UI State
  const [currentView, setCurrentView] = useState('home');
  const [selectedCategory, setSelectedCategory] = useState('All');
  const [searchQuery, setSearchQuery] = useState('');
  const [selectedBouquet, setSelectedBouquet] = useState(null);
  
  // Admin State
  const [password, setPassword] = useState('');
  const [loginError, setLoginError] = useState('');
  const [clickCount, setClickCount] = useState(0);
  const clickTimeout = useRef(null);

  // --- 4. FIREBASE AUTH & LIVE SYNC ---
  useEffect(() => {
    if (!auth) {
      setIsInitializing(false);
      return;
    }
    
    const initAuth = async () => {
      try {
        if (typeof __initial_auth_token !== 'undefined' && __initial_auth_token) {
          await signInWithCustomToken(auth, __initial_auth_token);
        } else {
          await signInAnonymously(auth);
        }
      } catch (error) {
        console.error("Auth Error:", error);
        setIsInitializing(false);
      }
    };
    initAuth();

    const unsubscribe = onAuthStateChanged(auth, (currentUser) => {
      setUser(currentUser);
      if (!currentUser) setIsInitializing(false);
    });
    return () => unsubscribe();
  }, []);

  useEffect(() => {
    if (!user || !db) return;

    // Listen to Bouquets globally
    const bouquetsRef = collection(db, 'artifacts', appId, 'public', 'data', 'bouquets');
    const unsubBouquets = onSnapshot(bouquetsRef, 
      (snapshot) => {
        const fetched = snapshot.docs.map(doc => ({ id: doc.id, ...doc.data() }));
        fetched.sort((a, b) => (b.createdAt || 0) - (a.createdAt || 0));
        setBouquets(fetched);
        setIsInitializing(false);
      },
      (error) => { 
        console.error("Sync Error", error); 
        setIsInitializing(false); 
      }
    );

    // Listen to Settings globally (Logo, Banner, Contacts)
    const settingsRef = collection(db, 'artifacts', appId, 'public', 'data', 'settings');
    const unsubSettings = onSnapshot(settingsRef, 
      (snapshot) => {
        if (!snapshot.empty) {
          const fetchedSettings = snapshot.docs[0].data();
          setSettings(fetchedSettings);
        }
      },
      (error) => console.error("Settings Sync Error", error)
    );

    return () => { unsubBouquets(); unsubSettings(); };
  }, [user]);

  // --- 5. 4-CLICK SECRET ADMIN TRIGGER ---
  const handleSecretTrigger = () => {
    setClickCount(prev => {
      const newCount = prev + 1;
      if (newCount >= 4) {
        setCurrentView('admin_login');
        window.scrollTo(0, 0);
        return 0;
      }
      return newCount;
    });

    if (clickTimeout.current) clearTimeout(clickTimeout.current);
    clickTimeout.current = setTimeout(() => setClickCount(0), 1000); 
  };

  useEffect(() => { window.scrollTo(0, 0); }, [currentView, selectedBouquet]);

  // ==========================================
  // LOADING SCREEN
  // ==========================================
  if (isInitializing) {
    return (
      <div className="min-h-screen bg-[#fcfbf9] flex flex-col items-center justify-center font-serif gpu-accel">
         <Loader2 className="w-10 h-10 animate-spin text-[#064e3b] mb-4" />
         <h1 className="text-2xl text-gray-900 tracking-wider">Tatka Ful</h1>
         <p className="text-[10px] text-gray-400 uppercase tracking-[0.2em] mt-2">Connecting to Live Cloud...</p>
      </div>
    );
  }

  // ==========================================
  // CUSTOMER WEBSITE VIEW (Mobile Friendly)
  // ==========================================
  if (currentView === 'home') {
    const visibleBouquets = bouquets.filter(b => b.visible !== false);
    let displayedBouquets = visibleBouquets;
    
    if (selectedCategory !== 'All') {
      displayedBouquets = displayedBouquets.filter(b => b.category === selectedCategory);
    }
    if (searchQuery) {
      displayedBouquets = displayedBouquets.filter(b => 
        b.name.toLowerCase().includes(searchQuery.toLowerCase()) || 
        b.category.toLowerCase().includes(searchQuery.toLowerCase())
      );
    }

    return (
      <div className="min-h-screen font-sans text-gray-800 selection:bg-emerald-900 selection:text-white pb-20 md:pb-0">
        <style dangerouslySetInnerHTML={{ __html: STYLES }} />
        
        {/* Luxury Navbar */}
        <nav className="fixed w-full top-0 z-40 glass-header gpu-accel">
          <div className="max-w-7xl mx-auto px-4 md:px-6 h-16 md:h-24 flex items-center justify-between">
            <div className="flex items-center gap-3 cursor-pointer" onClick={() => {window.scrollTo({top:0}); setSelectedCategory('All'); setSearchQuery('');}}>
              {settings.logo ? (
                <img src={settings.logo} alt="Logo" className="w-10 h-10 md:w-12 md:h-12 rounded-full object-cover shadow-sm bg-white" />
              ) : (
                <div className="w-10 h-10 md:w-12 md:h-12 rounded-full bg-[#064e3b] text-white flex items-center justify-center font-serif text-lg shadow-sm">TF</div>
              )}
              <span className="text-xl md:text-2xl font-serif font-semibold text-gray-900 tracking-wide">Tatka Ful</span>
            </div>
            <div className="flex items-center gap-4">
              <a 
                href={`https://wa.me/${formatWhatsApp(settings.whatsapp)}`} 
                target="_blank" rel="noreferrer"
                className="premium-btn text-white px-5 py-2 md:py-2.5 rounded-full tracking-widest text-[10px] md:text-xs font-bold uppercase shadow-md"
              >
                Inquire
              </a>
            </div>
          </div>
        </nav>

        {/* Hero Banner Section */}
        <section className="relative pt-24 pb-12 md:pt-36 md:pb-24 px-4 flex items-center justify-center min-h-[45vh] md:min-h-[55vh] overflow-hidden gpu-accel">
          {settings.banner ? (
            <div className="absolute inset-0 z-0">
              <img src={settings.banner} alt="Banner" className="w-full h-full object-cover opacity-30" loading="lazy" />
              <div className="absolute inset-0 bg-gradient-to-b from-[#fcfbf9]/90 via-[#fcfbf9]/50 to-[#fcfbf9]"></div>
            </div>
          ) : (
            <div className="absolute inset-0 z-0 bg-gradient-to-br from-[#ecfdf5]/50 to-[#fcfbf9]"></div>
          )}

          <div className="max-w-3xl mx-auto text-center relative z-10 animate-fade-up w-full">
            <h1 className="text-3xl md:text-6xl font-serif text-gray-900 mb-4 md:mb-6 leading-tight tracking-tight">
              {settings.heroSlogan}
            </h1>
            <p className="text-sm md:text-lg text-gray-600 mb-8 max-w-xl mx-auto font-light leading-relaxed px-2">
              {settings.heroDesc}
            </p>
            
            {/* Search Bar */}
            <div className="max-w-md mx-auto relative px-2">
               <input 
                 type="text" 
                 placeholder="Search for Rose, Chocolate..." 
                 value={searchQuery}
                 onChange={(e) => setSearchQuery(e.target.value)}
                 className="w-full pl-10 pr-10 py-3.5 md:py-4 bg-white/95 border border-gray-200 rounded-full shadow-lg outline-none focus:border-[#064e3b] focus:ring-2 focus:ring-[#064e3b]/20 transition-all font-medium text-sm"
               />
               <Search size={18} className="absolute left-6 top-1/2 -translate-y-1/2 text-gray-400" />
               {searchQuery && (
                 <button onClick={() => setSearchQuery('')} className="absolute right-6 top-1/2 -translate-y-1/2 text-gray-400 hover:text-gray-900 bg-gray-100 rounded-full p-1">
                    <X size={14} />
                 </button>
               )}
            </div>
          </div>
        </section>

        {/* Collections Filter */}
        <section id="collection" className="px-2 py-3 sticky top-16 md:top-24 glass-header z-30 shadow-sm gpu-accel w-full overflow-hidden">
          <div className="max-w-7xl mx-auto flex gap-2 overflow-x-auto pb-1 snap-x px-2 scrollbar-hide">
            <button 
              onClick={() => setSelectedCategory('All')}
              className={`snap-start whitespace-nowrap px-4 py-2 md:py-2.5 rounded-full transition-all text-[10px] md:text-xs font-bold tracking-widest uppercase border ${selectedCategory === 'All' ? 'bg-[#022c22] text-white border-[#022c22] shadow-md' : 'bg-white text-gray-600 border-gray-200 hover:text-[#064e3b] hover:bg-gray-50'}`}
            >
              All Designs
            </button>
            {INITIAL_CATEGORIES.map(cat => (
              <button 
                key={cat}
                onClick={() => setSelectedCategory(cat)}
                className={`snap-start whitespace-nowrap px-4 py-2 md:py-2.5 rounded-full transition-all text-[10px] md:text-xs font-bold tracking-widest uppercase border ${selectedCategory === cat ? 'bg-[#022c22] text-white border-[#022c22] shadow-md' : 'bg-white text-gray-600 border-gray-200 hover:text-[#064e3b] hover:bg-gray-50'}`}
              >
                {cat}
              </button>
            ))}
          </div>
        </section>

        {/* Masterpiece Grid (2 Columns on Mobile) */}
        <section className="px-3 md:px-6 py-8 md:py-10 max-w-7xl mx-auto min-h-[50vh]">
          {displayedBouquets.length === 0 ? (
            <div className="text-center py-16 bg-white border border-gray-100 rounded-2xl animate-fade-up mx-2 shadow-sm">
              <div className="w-12 h-12 bg-[#ecfdf5] rounded-full flex items-center justify-center mx-auto mb-3">
                <ImageIcon className="text-[#064e3b] w-5 h-5" />
              </div>
              <h3 className="text-lg md:text-2xl font-serif text-gray-900 mb-2">No bouquets found</h3>
              <p className="text-gray-500 font-light text-xs md:text-sm">Try a different category or search term.</p>
            </div>
          ) : (
            <div className="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-x-3 gap-y-6 md:gap-x-6 md:gap-y-10">
              {displayedBouquets.map((bouquet, index) => (
                <div 
                  key={bouquet.id} 
                  className="group cursor-pointer flex flex-col animate-fade-up gpu-accel"
                  onClick={() => setSelectedBouquet(bouquet)}
                >
                  <div className="relative aspect-[4/5] rounded-xl overflow-hidden luxury-card mb-2 bg-gray-50">
                    {bouquet.images && bouquet.images.length > 0 ? (
                      <img 
                        src={bouquet.images[0]} 
                        alt={bouquet.name} 
                        loading="lazy"
                        className="w-full h-full object-cover transition-transform duration-500 group-hover:scale-105"
                      />
                    ) : (
                      <div className="w-full h-full flex items-center justify-center text-gray-300 text-[10px]">No Image</div>
                    )}
                    
                    <div className="absolute inset-0 bg-gradient-to-t from-black/30 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity"></div>

                    {bouquet.bestseller && (
                      <div className="absolute top-2 left-2 md:top-3 md:left-3 bg-white/95 backdrop-blur-md text-[#b8860b] text-[8px] md:text-[10px] font-bold uppercase tracking-widest px-2 md:px-3 py-1 rounded-md shadow-sm">
                        Signature
                      </div>
                    )}
                  </div>
                  <div className="px-1">
                    <p className="text-[8px] md:text-[10px] font-bold tracking-[0.2em] text-[#064e3b] uppercase mb-1 truncate">{bouquet.category}</p>
                    <h3 className="text-sm md:text-lg font-serif text-gray-900 mb-1 group-hover:text-[#064e3b] transition-colors truncate">{bouquet.name}</h3>
                    <p className="text-gray-500 text-[10px] md:text-xs line-clamp-2 leading-relaxed font-light hidden md:block">{bouquet.description}</p>
                  </div>
                </div>
              ))}
            </div>
          )}
        </section>

        {/* Floating WhatsApp Action */}
        <div className="fixed bottom-4 right-4 md:bottom-8 md:right-8 z-40 flex flex-col gap-3">
           <a href={`https://wa.me/${formatWhatsApp(settings.whatsapp)}`} target="_blank" rel="noreferrer" className="w-12 h-12 md:w-16 md:h-16 bg-[#25D366] text-white rounded-full flex items-center justify-center hover:scale-105 transition-transform shadow-[0_8px_20px_rgba(37,211,102,0.4)] gpu-accel">
            <MessageCircle size={24} className="md:w-8 md:h-8" />
          </a>
        </div>

        {/* Premium Footer */}
        <footer className="bg-white border-t border-gray-100 pt-12 pb-8 px-4 mt-8">
          <div className="max-w-7xl mx-auto flex flex-col md:flex-row justify-between items-center gap-8 text-center md:text-left">
            <div className="flex flex-col items-center md:items-start max-w-sm">
              {settings.logo ? (
                <img src={settings.logo} alt="Logo" className="w-14 h-14 rounded-full mb-3 shadow-sm object-cover bg-white" loading="lazy" />
              ) : (
                 <div className="w-14 h-14 rounded-full bg-[#064e3b] text-white flex items-center justify-center font-serif text-xl mb-3 shadow-sm">TF</div>
              )}
              <h3 className="font-serif text-xl md:text-2xl text-gray-900 mb-2">Tatka Ful</h3>
              <p className="text-gray-500 text-[11px] md:text-xs leading-relaxed font-light">
                The ultimate destination for luxury floral design. Transforming nature's beauty into unforgettable emotions.
              </p>
            </div>
            <div className="flex flex-col items-center md:items-end">
              <p className="text-[9px] md:text-[10px] font-bold tracking-[0.2em] text-gray-400 uppercase mb-3">Connect With Us</p>
              <div className="flex gap-3">
                <a href={settings.instagram} target="_blank" rel="noreferrer" className="w-9 h-9 md:w-10 md:h-10 rounded-full border border-gray-200 flex items-center justify-center text-gray-600 hover:text-[#064e3b] hover:border-[#064e3b] transition-all bg-gray-50">
                  <Instagram size={16} />
                </a>
                <a href={`tel:${settings.phone}`} className="w-9 h-9 md:w-10 md:h-10 rounded-full border border-gray-200 flex items-center justify-center text-gray-600 hover:text-[#064e3b] hover:border-[#064e3b] transition-all bg-gray-50">
                  <Phone size={16} />
                </a>
              </div>
            </div>
          </div>
          <div className="max-w-7xl mx-auto mt-10 pt-6 border-t border-gray-100 text-center">
            {/* 4-TAP SECRET ADMIN TRIGGER */}
            <p 
              className="text-[9px] md:text-[10px] font-medium tracking-widest uppercase text-gray-400 select-none cursor-pointer hover:text-gray-600 py-2 inline-block"
              onClick={handleSecretTrigger}
            >
              &copy; {new Date().getFullYear()} Tatka Ful. Crafted with elegance.
            </p>
          </div>
        </footer>

        {/* Detail Modal */}
        {selectedBouquet && (
          <div className="fixed inset-0 z-50 flex items-end md:items-center justify-center p-0 md:p-8 gpu-accel">
            <div className="absolute inset-0 bg-black/60 backdrop-blur-sm transition-opacity" onClick={() => setSelectedBouquet(null)}></div>
            <div className="relative bg-white w-full h-[85vh] md:h-auto md:max-h-[85vh] md:max-w-4xl rounded-t-2xl md:rounded-2xl shadow-2xl overflow-hidden flex flex-col md:flex-row animate-fade-up">
              
              <button 
                onClick={() => setSelectedBouquet(null)}
                className="absolute top-3 right-3 z-20 w-8 h-8 md:w-10 md:h-10 bg-white/90 shadow-md rounded-full flex items-center justify-center text-gray-900 hover:bg-gray-100 transition-colors"
              >
                <X size={18} />
              </button>

              {/* Gallery Side */}
              <div className="w-full md:w-1/2 bg-[#fcfbf9] h-[40vh] md:h-[60vh] overflow-x-auto md:overflow-y-auto flex md:flex-col snap-x md:snap-y snap-mandatory relative border-b md:border-b-0 md:border-r border-gray-100 scrollbar-hide">
                {selectedBouquet.images && selectedBouquet.images.length > 0 ? (
                  selectedBouquet.images.map((img, i) => (
                    <div key={i} className="w-full h-full min-w-full md:min-h-full snap-center relative shrink-0">
                      <img src={img} alt={`${selectedBouquet.name} ${i+1}`} className="w-full h-full object-cover" loading="lazy" />
                    </div>
                  ))
                ) : (
                  <div className="w-full h-full min-w-full flex items-center justify-center text-gray-300 text-xs">No Images</div>
                )}
                {selectedBouquet.images?.length > 1 && (
                  <div className="absolute bottom-3 left-0 right-0 flex justify-center gap-2 pointer-events-none">
                    <span className="bg-black/50 text-white text-[8px] md:text-[9px] px-3 py-1.5 rounded-full tracking-widest uppercase backdrop-blur-sm">Swipe for more</span>
                  </div>
                )}
              </div>

              {/* Info Side */}
              <div className="w-full md:w-1/2 p-5 md:p-10 flex flex-col h-[45vh] md:h-[60vh] overflow-y-auto bg-white">
                <p className="text-[9px] md:text-[10px] font-bold tracking-[0.3em] text-[#064e3b] uppercase mb-1.5">{selectedBouquet.category}</p>
                <h2 className="text-2xl md:text-3xl font-serif text-gray-900 mb-3 leading-tight">{selectedBouquet.name}</h2>
                <div className="w-8 h-[2px] bg-[#d4af37] mb-4"></div>
                <p className="text-gray-600 leading-relaxed mb-6 font-light text-[11px] md:text-sm whitespace-pre-line">{selectedBouquet.description}</p>
                
                <div className="mt-auto space-y-2.5 pb-4 md:pb-0">
                  <a 
                    href={`https://wa.me/${formatWhatsApp(settings.whatsapp)}?text=${encodeURIComponent(`Hello TATKA-FUL! I'm interested in ordering the '${selectedBouquet.name}'. Please share the price and details.`)}`}
                    target="_blank" rel="noreferrer"
                    className="w-full premium-btn text-white py-3.5 rounded-xl flex items-center justify-center gap-2 text-[11px] md:text-xs font-bold uppercase tracking-widest"
                  >
                    <MessageCircle size={16} /> Order on WhatsApp
                  </a>
                  <a 
                    href={`tel:${settings.phone}`}
                    className="w-full bg-gray-50 text-gray-900 py-3.5 rounded-xl flex items-center justify-center gap-2 text-[11px] md:text-xs font-bold uppercase tracking-widest border border-gray-200 hover:bg-gray-100 transition-colors"
                  >
                    <Phone size={16} /> Call Studio
                  </a>
                </div>
              </div>
            </div>
          </div>
        )}
      </div>
    );
  }

  // ==========================================
  // ADMIN LOGIN (Secure Entry)
  // ==========================================
  if (currentView === 'admin_login') {
    return (
      <div className="min-h-screen bg-[#fcfbf9] flex items-center justify-center px-4">
        <style dangerouslySetInnerHTML={{ __html: STYLES }} />
        <div className="bg-white p-8 rounded-2xl shadow-xl w-full max-w-xs md:max-w-sm border border-gray-100">
          <div className="flex justify-center mb-5">
            <div className="w-16 h-16 rounded-full bg-[#064e3b] text-white flex items-center justify-center font-serif text-2xl shadow-md">TF</div>
          </div>
          <h2 className="text-xl font-serif text-center text-gray-900 mb-1">Studio Portal</h2>
          <p className="text-center text-gray-400 mb-6 text-[9px] font-bold tracking-[0.2em] uppercase">Live Cloud Connect</p>
          
          <form onSubmit={(e) => {
            e.preventDefault();
            if (password === 'gym') {
              setCurrentView('admin_dashboard');
              setLoginError('');
              setPassword('');
            } else {
              setLoginError('Invalid Passcode');
            }
          }}>
            <div className="mb-5">
              <input 
                type="password" 
                placeholder="PASSCODE"
                value={password}
                onChange={(e) => setPassword(e.target.value)}
                className="w-full px-4 py-3 bg-gray-50 border border-gray-200 rounded-xl focus:outline-none focus:border-[#064e3b] focus:ring-1 focus:ring-[#064e3b] transition-all text-center tracking-[0.5em] text-sm md:text-base font-bold uppercase"
              />
              {loginError && <p className="text-red-500 text-[10px] mt-2 text-center font-medium">{loginError}</p>}
            </div>
            <button type="submit" className="w-full premium-btn text-white py-3 rounded-xl font-bold uppercase tracking-widest text-[10px] md:text-xs">
              Connect to Cloud
            </button>
            <button 
              type="button" 
              onClick={() => setCurrentView('home')}
              className="w-full mt-3 text-gray-400 hover:text-gray-900 py-2 text-[9px] md:text-[10px] transition-colors flex items-center justify-center gap-1 font-bold uppercase tracking-widest"
            >
              <ArrowLeft size={12} /> Cancel
            </button>
          </form>
        </div>
      </div>
    );
  }

  // ==========================================
  // ADMIN DASHBOARD (Live Cloud Management)
  // ==========================================
  if (currentView === 'admin_dashboard') {
    return (
      <AdminDashboard 
        bouquets={bouquets} 
        db={db} appId={appId} user={user}
        categories={INITIAL_CATEGORIES}
        settings={settings} setSettings={setSettings}
        onLogout={() => setCurrentView('home')}
        STYLES={STYLES}
      />
    );
  }
  
  return null;
}

// --- CLOUD ADMIN DASHBOARD SUB-COMPONENT ---
function AdminDashboard({ bouquets, db, appId, user, categories, settings, setSettings, onLogout, STYLES }) {
  const [activeTab, setActiveTab] = useState('bouquets');
  const [isAddingBouquet, setIsAddingBouquet] = useState(false);
  const [editingId, setEditingId] = useState(null);
  const [formData, setFormData] = useState({ name: '', category: categories[0], description: '', images: [], bestseller: false, visible: true });
  const [isUploading, setIsUploading] = useState(false);
  const [isSaving, setIsSaving] = useState(false);

  // Aggressive Image Compression (Fast Load & Safe Sync)
  const processImageUpload = (file, maxWidth = 600, quality = 0.6) => {
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
  };

  const handleFileChange = async (e) => {
    const files = Array.from(e.target.files);
    if (!files.length) return;
    if (formData.images.length + files.length > 5) return alert("Max 5 images allowed.");
    
    setIsUploading(true);
    try {
      const processed = await Promise.all(files.map(f => processImageUpload(f, 600, 0.6)));
      setFormData(prev => ({ ...prev, images: [...prev.images, ...processed].slice(0, 5) }));
    } catch (err) { alert("Upload error."); }
    setIsUploading(false);
  };

  const handleLogoUpload = async (e) => {
    const file = e.target.files[0];
    if(!file) return;
    try {
      const imgData = await processImageUpload(file, 300, 0.8);
      setSettings({...settings, logo: imgData});
    } catch(err) { alert("Failed to process Logo"); }
  };

  const handleBannerUpload = async (e) => {
    const file = e.target.files[0];
    if(!file) return;
    try {
      const imgData = await processImageUpload(file, 1200, 0.7);
      setSettings({...settings, banner: imgData});
    } catch(err) { alert("Failed to process Banner"); }
  };

  // Firebase Global Save
  const saveBouquet = async (e) => {
    e.preventDefault();
    if (!user || !db) return alert("Not connected to Cloud.");
    setIsSaving(true);
    
    try {
      const bouquetsRef = collection(db, 'artifacts', appId, 'public', 'data', 'bouquets');
      if (editingId) {
        await setDoc(doc(bouquetsRef, editingId), { ...formData, updatedAt: Date.now() }, { merge: true });
      } else {
        const newDocRef = doc(bouquetsRef, Date.now().toString());
        await setDoc(newDocRef, { ...formData, createdAt: Date.now() });
      }
      setIsAddingBouquet(false);
      setEditingId(null);
    } catch (error) {
      alert("Failed to save to cloud.");
    }
    setIsSaving(false);
  };

  const deleteBouquet = async (id) => {
    if (!user || !db) return;
    if (window.confirm('Delete permanently from cloud?')) {
      await deleteDoc(doc(db, 'artifacts', appId, 'public', 'data', 'bouquets', id));
    }
  };

  const toggleVisibility = async (id, currentVis) => {
    if (!user || !db) return;
    await setDoc(doc(db, 'artifacts', appId, 'public', 'data', 'bouquets', id), { visible: !currentVis }, { merge: true });
  };

  const saveSettings = async (e) => {
    e.preventDefault();
    if (!user || !db) return alert("Not connected to Cloud.");
    setIsSaving(true);
    
    try {
      await setDoc(doc(db, 'artifacts', appId, 'public', 'data', 'settings', 'main'), settings, { merge: true });
      alert("Brand settings synced to all devices!");
    } catch (e) {
      alert("Failed to sync settings.");
    }
    setIsSaving(false);
  };

  return (
    <div className="min-h-screen bg-gray-50 flex flex-col md:flex-row font-sans text-gray-800">
      <style dangerouslySetInnerHTML={{ __html: STYLES }} />
      
      {/* Sidebar Navigation */}
      <aside className="w-full md:w-64 bg-white border-b md:border-b-0 md:border-r border-gray-200 flex flex-col shrink-0 z-10 shadow-sm">
        <div className="p-4 md:p-6 border-b border-gray-100 flex items-center justify-between md:justify-start gap-3">
          <div className="flex items-center gap-3">
            <div className="w-8 h-8 md:w-10 md:h-10 rounded-full bg-[#064e3b] text-white flex items-center justify-center font-serif text-sm md:text-lg">TF</div>
            <div>
              <span className="font-serif text-sm md:text-lg text-gray-900 block leading-tight">Studio Admin</span>
              <span className="text-[7px] md:text-[8px] uppercase tracking-widest text-emerald-600 font-bold flex items-center gap-1 mt-0.5">
                <span className="w-1.5 h-1.5 rounded-full bg-emerald-500 animate-pulse"></span> Cloud Sync Active
              </span>
            </div>
          </div>
          <button onClick={onLogout} className="md:hidden p-2 text-gray-500 hover:text-red-500"><LogOut size={16}/></button>
        </div>
        <div className="p-2 md:p-4 flex flex-row md:flex-col gap-2 overflow-x-auto flex-1">
          <button onClick={() => setActiveTab('bouquets')} className={`flex-1 md:flex-none flex items-center justify-center md:justify-start gap-2 px-3 md:px-4 py-2.5 md:py-3 rounded-lg md:rounded-xl transition-all font-semibold text-[10px] md:text-xs tracking-wide uppercase whitespace-nowrap ${activeTab === 'bouquets' ? 'bg-[#064e3b] text-white shadow-sm' : 'text-gray-500 hover:bg-gray-100'}`}>
            <LayoutDashboard size={14} /> Designs
          </button>
          <button onClick={() => setActiveTab('settings')} className={`flex-1 md:flex-none flex items-center justify-center md:justify-start gap-2 px-3 md:px-4 py-2.5 md:py-3 rounded-lg md:rounded-xl transition-all font-semibold text-[10px] md:text-xs tracking-wide uppercase whitespace-nowrap ${activeTab === 'settings' ? 'bg-[#064e3b] text-white shadow-sm' : 'text-gray-500 hover:bg-gray-100'}`}>
            <Settings size={14} /> Brand Settings
          </button>
        </div>
        <div className="hidden md:block p-4 border-t border-gray-100">
          <button onClick={onLogout} className="w-full flex items-center justify-center gap-2 px-4 py-3 rounded-xl bg-gray-100 text-gray-600 hover:bg-red-50 hover:text-red-600 transition-all font-bold text-[10px] uppercase tracking-widest">
            <LogOut size={14} /> Exit Admin
          </button>
        </div>
      </aside>

      {/* Main Admin Area */}
      <main className="flex-1 p-3 md:p-8 overflow-y-auto">
        
        {/* BOUQUETS LIST */}
        {activeTab === 'bouquets' && !isAddingBouquet && (
          <div className="animate-fade-up max-w-5xl mx-auto">
            <div className="flex flex-col sm:flex-row justify-between items-start sm:items-center mb-4 md:mb-6 gap-3">
              <div>
                <h1 className="text-xl md:text-3xl font-serif text-gray-900">Cloud Inventory</h1>
                <p className="text-gray-500 text-[10px] md:text-xs font-medium mt-1">Updates instantly sync to all mobile & desktop devices.</p>
              </div>
              <button onClick={() => { setFormData({name: '', category: categories[0], description: '', images: [], bestseller: false, visible: true}); setEditingId(null); setIsAddingBouquet(true); }}
                className="premium-btn text-white px-4 md:px-6 py-2.5 md:py-3 rounded-full flex items-center gap-1.5 md:gap-2 font-bold uppercase tracking-widest text-[9px] md:text-[10px]"
              >
                <Plus size={12} /> Add New
              </button>
            </div>

            {/* List Table */}
            <div className="bg-white border border-gray-200 rounded-xl md:rounded-2xl overflow-hidden shadow-sm">
              <div className="overflow-x-auto">
                <table className="w-full text-left border-collapse min-w-[300px] md:min-w-[500px]">
                  <thead>
                    <tr className="border-b border-gray-100 bg-gray-50">
                      <th className="p-3 md:p-4 text-[9px] md:text-[10px] font-bold text-gray-400 uppercase tracking-widest">Item</th>
                      <th className="p-3 md:p-4 text-[9px] md:text-[10px] font-bold text-gray-400 uppercase tracking-widest hidden sm:table-cell">Category</th>
                      <th className="p-3 md:p-4 text-[9px] md:text-[10px] font-bold text-gray-400 uppercase tracking-widest text-center">Visible</th>
                      <th className="p-3 md:p-4 text-[9px] md:text-[10px] font-bold text-gray-400 uppercase tracking-widest text-right">Actions</th>
                    </tr>
                  </thead>
                  <tbody className="divide-y divide-gray-100">
                    {bouquets.map(bouquet => (
                      <tr key={bouquet.id} className="hover:bg-gray-50/50">
                        <td className="p-3 md:p-4 flex items-center gap-2 md:gap-3">
                          <div className="w-10 h-10 md:w-12 md:h-12 rounded-md md:rounded-lg bg-gray-100 overflow-hidden shrink-0">
                            {bouquet.images && bouquet.images[0] ? <img src={bouquet.images[0]} className="w-full h-full object-cover" loading="lazy" /> : null}
                          </div>
                          <div>
                            <p className="font-serif text-xs md:text-sm text-gray-900 truncate max-w-[100px] md:max-w-[150px]">{bouquet.name}</p>
                            {bouquet.bestseller && <span className="text-[7px] md:text-[8px] bg-[#b8860b]/10 text-[#b8860b] px-1.5 py-0.5 rounded font-bold uppercase tracking-widest">Star</span>}
                          </div>
                        </td>
                        <td className="p-3 md:p-4 text-[10px] md:text-xs text-gray-600 font-medium hidden sm:table-cell">{bouquet.category}</td>
                        <td className="p-3 md:p-4 text-center">
                          <button onClick={() => toggleVisibility(bouquet.id, bouquet.visible)} className={`p-1.5 md:p-2 rounded-full ${bouquet.visible ? 'text-[#064e3b] bg-green-50' : 'text-gray-400 bg-gray-100'}`}>
                            {bouquet.visible ? <Eye size={14} /> : <EyeOff size={14} />}
                          </button>
                        </td>
                        <td className="p-3 md:p-4 text-right space-x-1.5 md:space-x-2">
                          <button onClick={() => { setFormData(bouquet); setEditingId(bouquet.id); setIsAddingBouquet(true); }} className="p-1.5 md:p-2 text-blue-600 bg-blue-50 rounded-full inline-block"><Edit size={12} /></button>
                          <button onClick={() => deleteBouquet(bouquet.id)} className="p-1.5 md:p-2 text-red-600 bg-red-50 rounded-full inline-block"><Trash2 size={12} /></button>
                        </td>
                      </tr>
                    ))}
                    {bouquets.length === 0 && (
                      <tr><td colSpan="4" className="p-6 md:p-8 text-center text-gray-400 text-xs md:text-sm">No items in cloud database.</td></tr>
                    )}
                  </tbody>
                </table>
              </div>
            </div>
          </div>
        )}

        {/* ADD/EDIT FORM */}
        {activeTab === 'bouquets' && isAddingBouquet && (
          <div className="animate-fade-up max-w-2xl mx-auto bg-white p-5 md:p-8 border border-gray-200 rounded-2xl md:rounded-3xl shadow-sm">
            <div className="flex items-center gap-3 md:gap-4 mb-5 md:mb-6 border-b border-gray-100 pb-3 md:pb-4">
              <button onClick={() => setIsAddingBouquet(false)} className="p-1.5 md:p-2 bg-gray-100 rounded-full text-gray-600"><ArrowLeft size={14} /></button>
              <h2 className="text-xl md:text-2xl font-serif text-gray-900">{editingId ? 'Edit Design' : 'Create New'}</h2>
            </div>

            <form onSubmit={saveBouquet} className="space-y-4 md:space-y-6">
              <div className="bg-gray-50 p-3 md:p-4 rounded-lg md:rounded-xl border border-gray-200">
                <label className="block text-[9px] md:text-[10px] font-bold tracking-widest text-gray-500 mb-2 md:mb-3 uppercase">Gallery Images (Max 5)</label>
                <div className="grid grid-cols-3 sm:grid-cols-5 gap-2 md:gap-3">
                  {formData.images.map((img, idx) => (
                    <div key={idx} className="relative aspect-[4/5] rounded-md md:rounded-lg overflow-hidden group border border-gray-300">
                      <img src={img} className="w-full h-full object-cover" />
                      <button type="button" onClick={() => setFormData(prev => ({...prev, images: prev.images.filter((_, i) => i !== idx)}))} className="absolute inset-0 bg-red-900/60 text-white flex items-center justify-center opacity-0 group-hover:opacity-100"><Trash2 size={14} /></button>
                    </div>
                  ))}
                  {formData.images.length < 5 && (
                    <label className="aspect-[4/5] rounded-md md:rounded-lg border-2 border-dashed border-gray-400 hover:border-[#064e3b] hover:bg-green-50 flex flex-col items-center justify-center cursor-pointer text-gray-500 bg-white transition-colors">
                      <Upload size={14} className="mb-1" />
                      <span className="text-[7px] md:text-[8px] font-bold uppercase text-center leading-tight">
                        {isUploading ? 'Wait...' : 'Add'}
                      </span>
                      <input type="file" accept="image/*" multiple className="hidden" onChange={handleFileChange} disabled={isUploading || isSaving} />
                    </label>
                  )}
                </div>
              </div>

              <div className="space-y-3 md:space-y-4">
                <div>
                  <label className="block text-[9px] md:text-[10px] font-bold tracking-widest text-gray-500 mb-1 uppercase">Name</label>
                  <input required type="text" value={formData.name} onChange={e=>setFormData({...formData, name: e.target.value})} className="w-full px-3 py-2 md:px-4 md:py-3 bg-white border border-gray-300 rounded-lg md:rounded-xl focus:border-[#064e3b] outline-none text-xs md:text-sm" />
                </div>
                <div>
                  <label className="block text-[9px] md:text-[10px] font-bold tracking-widest text-gray-500 mb-1 uppercase">Category</label>
                  <select required value={formData.category} onChange={e=>setFormData({...formData, category: e.target.value})} className="w-full px-3 py-2 md:px-4 md:py-3 bg-white border border-gray-300 rounded-lg md:rounded-xl focus:border-[#064e3b] outline-none text-xs md:text-sm">
                    {categories.map(c => <option key={c} value={c}>{c}</option>)}
                  </select>
                </div>
                <div>
                  <label className="block text-[9px] md:text-[10px] font-bold tracking-widest text-gray-500 mb-1 uppercase">Description</label>
                  <textarea required rows="3" value={formData.description} onChange={e=>setFormData({...formData, description: e.target.value})} className="w-full px-3 py-2 md:px-4 md:py-3 bg-white border border-gray-300 rounded-lg md:rounded-xl focus:border-[#064e3b] outline-none resize-none text-xs md:text-sm leading-relaxed"></textarea>
                </div>
              </div>

              <div className="flex gap-4 md:gap-6 pt-1 md:pt-2">
                <label className="flex items-center gap-1.5 md:gap-2 cursor-pointer">
                  <input type="checkbox" checked={formData.bestseller} onChange={e=>setFormData({...formData, bestseller: e.target.checked})} className="w-4 h-4 md:w-5 md:h-5 rounded accent-[#064e3b]" />
                  <span className="text-[10px] md:text-xs font-bold text-gray-600 uppercase">Signature</span>
                </label>
                <label className="flex items-center gap-1.5 md:gap-2 cursor-pointer">
                  <input type="checkbox" checked={formData.visible} onChange={e=>setFormData({...formData, visible: e.target.checked})} className="w-4 h-4 md:w-5 md:h-5 rounded accent-[#064e3b]" />
                  <span className="text-[10px] md:text-xs font-bold text-gray-600 uppercase">Public Display</span>
                </label>
              </div>

              <div className="pt-4 md:pt-6 border-t border-gray-100">
                <button type="submit" disabled={isUploading || isSaving} className="w-full premium-btn text-white py-3 md:py-4 rounded-lg md:rounded-xl font-bold uppercase tracking-widest text-[10px] md:text-xs disabled:opacity-50 flex justify-center items-center gap-2">
                  {isSaving ? <><Loader2 size={14} className="animate-spin"/> Syncing to Cloud...</> : (editingId ? 'Save to Cloud' : 'Publish to Cloud')}
                </button>
              </div>
            </form>
          </div>
        )}

        {/* BRAND SETTINGS TAB (Logo & Banner Options Restored) */}
        {activeTab === 'settings' && (
          <div className="animate-fade-up max-w-2xl mx-auto bg-white p-5 md:p-8 border border-gray-200 rounded-2xl md:rounded-3xl shadow-sm">
             <h2 className="text-xl md:text-2xl font-serif text-gray-900 mb-4 md:mb-6 border-b border-gray-100 pb-3 md:pb-4">Brand Config</h2>
             
             {/* Logo & Banner Handlers */}
             <div className="grid grid-cols-1 sm:grid-cols-2 gap-4 mb-6">
                <div className="bg-gray-50 p-4 rounded-xl border border-gray-200 text-center">
                  <p className="text-[10px] font-bold tracking-widest text-gray-500 mb-2 uppercase">Brand Logo</p>
                  <div className="w-16 h-16 mx-auto bg-white rounded-full border border-gray-300 mb-3 overflow-hidden">
                    {settings.logo ? <img src={settings.logo} className="w-full h-full object-cover" /> : null}
                  </div>
                  <label className="text-[9px] font-bold uppercase bg-white border border-gray-300 px-3 py-1.5 rounded-full cursor-pointer hover:bg-gray-100">
                    Upload Logo
                    <input type="file" accept="image/*" className="hidden" onChange={handleLogoUpload} />
                  </label>
                </div>
                <div className="bg-gray-50 p-4 rounded-xl border border-gray-200 text-center">
                  <p className="text-[10px] font-bold tracking-widest text-gray-500 mb-2 uppercase">Hero Banner</p>
                  <div className="w-full h-16 mx-auto bg-white rounded-lg border border-gray-300 mb-3 overflow-hidden">
                    {settings.banner ? <img src={settings.banner} className="w-full h-full object-cover" /> : null}
                  </div>
                  <label className="text-[9px] font-bold uppercase bg-white border border-gray-300 px-3 py-1.5 rounded-full cursor-pointer hover:bg-gray-100">
                    Upload Banner
                    <input type="file" accept="image/*" className="hidden" onChange={handleBannerUpload} />
                  </label>
                </div>
             </div>

             <form onSubmit={saveSettings} className="space-y-4 md:space-y-5">
                <div>
                  <label className="block text-[9px] md:text-[10px] font-bold tracking-widest text-gray-500 mb-1 uppercase">Hero Slogan</label>
                  <input value={settings.heroSlogan} onChange={(e) => setSettings({...settings, heroSlogan: e.target.value})} className="w-full px-3 py-2 md:px-4 md:py-3 bg-gray-50 border border-gray-200 rounded-lg md:rounded-xl text-xs md:text-sm outline-none focus:border-[#064e3b] focus:bg-white transition-colors" />
                </div>
                <div>
                  <label className="block text-[9px] md:text-[10px] font-bold tracking-widest text-gray-500 mb-1 uppercase">Hero Description</label>
                  <textarea rows="2" value={settings.heroDesc} onChange={(e) => setSettings({...settings, heroDesc: e.target.value})} className="w-full px-3 py-2 md:px-4 md:py-3 bg-gray-50 border border-gray-200 rounded-lg md:rounded-xl text-xs md:text-sm outline-none focus:border-[#064e3b] focus:bg-white transition-colors resize-none"></textarea>
                </div>
                <div className="grid grid-cols-1 sm:grid-cols-2 gap-3 md:gap-4">
                  <div>
                    <label className="block text-[9px] md:text-[10px] font-bold tracking-widest text-gray-500 mb-1 uppercase">WhatsApp</label>
                    <input value={settings.whatsapp} onChange={(e) => setSettings({...settings, whatsapp: e.target.value})} className="w-full px-3 py-2 md:px-4 md:py-3 bg-gray-50 border border-gray-200 rounded-lg md:rounded-xl text-xs md:text-sm outline-none focus:border-[#064e3b] focus:bg-white transition-colors" />
                  </div>
                  <div>
                    <label className="block text-[9px] md:text-[10px] font-bold tracking-widest text-gray-500 mb-1 uppercase">Phone</label>
                    <input value={settings.phone} onChange={(e) => setSettings({...settings, phone: e.target.value})} className="w-full px-3 py-2 md:px-4 md:py-3 bg-gray-50 border border-gray-200 rounded-lg md:rounded-xl text-xs md:text-sm outline-none focus:border-[#064e3b] focus:bg-white transition-colors" />
                  </div>
                </div>
                <div>
                  <label className="block text-[9px] md:text-[10px] font-bold tracking-widest text-gray-500 mb-1 uppercase">Instagram Link</label>
                  <input value={settings.instagram} onChange={(e) => setSettings({...settings, instagram: e.target.value})} className="w-full px-3 py-2 md:px-4 md:py-3 bg-gray-50 border border-gray-200 rounded-lg md:rounded-xl text-xs md:text-sm outline-none focus:border-[#064e3b] focus:bg-white transition-colors" />
                </div>
                <button type="submit" disabled={isSaving} className="w-full premium-btn text-white py-3 md:py-4 rounded-lg md:rounded-xl font-bold uppercase tracking-widest text-[10px] md:text-xs mt-4 md:mt-6 flex justify-center items-center gap-2">
                  {isSaving ? <><Loader2 size={14} className="animate-spin"/> Syncing...</> : 'Sync Settings Globally'}
                </button>
             </form>
          </div>
        )}
      </main>
    </div>
  );
}
