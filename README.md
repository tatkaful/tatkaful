<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tatkaful - Premium Bouquets</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <style>
        .fade-in { animation: fadeIn 0.5s ease-in; }
        @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }
    </style>
</head>
<body class="bg-gray-50 font-sans">

    <!-- Header -->
    <header class="bg-white shadow-sm sticky top-0 z-50">
        <div class="max-w-7xl mx-auto px-4 py-4 flex justify-between items-center">
            <h1 class="text-2xl font-bold text-pink-600"><i class="fas fa-seedling mr-2"></i>Tatkaful</h1>
            <a href="#products" class="bg-pink-600 text-white px-5 py-2 rounded-full font-medium hover:bg-pink-700 transition">Shop Now</a>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="bg-pink-50 py-16 text-center px-4">
        <h2 class="text-4xl font-bold text-gray-800 mb-4">Send Love With Fresh Flowers</h2>
        <p class="text-gray-600 mb-8 max-w-xl mx-auto">Premium bouquets for your loved ones. Handpicked, beautifully crafted, and delivered with care.</p>
    </section>

    <!-- Products Section -->
    <section id="products" class="max-w-7xl mx-auto px-4 py-12">
        <h3 class="text-2xl font-bold text-gray-800 mb-8 text-center">Our Collections</h3>
        
        <!-- Loading Spinner -->
        <div id="loading" class="text-center py-10">
            <i class="fas fa-spinner fa-spin text-4xl text-pink-500"></i>
            <p class="text-gray-500 mt-3">Loading fresh collections...</p>
        </div>

        <!-- Product Grid -->
        <div id="productGrid" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6 hidden">
            <!-- Products will be injected here by Firebase -->
        </div>
    </section>

    <!-- Firebase Integration (Modular SDK) -->
    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/10.8.1/firebase-app.js";
        import { getDatabase, ref, onValue } from "https://www.gstatic.com/firebasejs/10.8.1/firebase-database.js";

        // Your Exact Firebase Config (with databaseURL added)
        const firebaseConfig = {
            apiKey: "AIzaSyAufJDfUyVtIDYkKULmtEtFHY6FJBwI_RQ",
            authDomain: "taktaful.firebaseapp.com",
            databaseURL: "https://taktaful-default-rtdb.firebaseio.com", 
            projectId: "taktaful",
            storageBucket: "taktaful.firebasestorage.app",
            messagingSenderId: "79913462603",
            appId: "1:79913462603:web:4637eba0de80cf7e1956ce",
            measurementId: "G-F7NC3TP665"
        };

        const app = initializeApp(firebaseConfig);
        const db = getDatabase(app);
        const productsRef = ref(db, 'products');

        const productGrid = document.getElementById('productGrid');
        const loading = document.getElementById('loading');
        
        // Change this to your actual WhatsApp Number
        const whatsappNumber = "8801XXXXXXXXX"; 

        onValue(productsRef, (snapshot) => {
            loading.style.display = 'none';
            productGrid.classList.remove('hidden');
            productGrid.innerHTML = ''; 

            const data = snapshot.val();
            if(data) {
                Object.keys(data).forEach(key => {
                    const product = data[key];
                    const waMessage = `Hello Tatkaful! I want to order: ${product.name} (Price: ৳${product.price})`;
                    const waLink = `https://wa.me/${whatsappNumber}?text=${encodeURIComponent(waMessage)}`;

                    const card = `
                        <div class="bg-white rounded-2xl shadow-md overflow-hidden hover:shadow-xl transition-shadow duration-300 fade-in flex flex-col">
                            <img src="${product.imageUrl}" alt="${product.name}" class="w-full h-56 object-cover">
                            <div class="p-5 flex-grow flex flex-col justify-between">
                                <div>
                                    <h4 class="text-lg font-bold text-gray-800">${product.name}</h4>
                                    <p class="text-pink-600 font-bold text-xl mt-2">৳${product.price}</p>
                                    ${product.description ? `<p class="text-gray-500 text-sm mt-2 line-clamp-2">${product.description}</p>` : ''}
                                </div>
                                <a href="${waLink}" target="_blank" class="mt-4 block text-center w-full bg-green-500 text-white py-2 rounded-lg hover:bg-green-600 transition">
                                    <i class="fab fa-whatsapp mr-2"></i> Order on WhatsApp
                                </a>
                            </div>
                        </div>
                    `;
                    productGrid.insertAdjacentHTML('beforeend', card);
                });
            } else {
                productGrid.innerHTML = '<p class="text-gray-500 col-span-full text-center">No products available right now. Check back later!</p>';
            }
        });
    </script>
</body>
</html>
