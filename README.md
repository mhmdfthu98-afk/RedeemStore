<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title>Redeem Store | متجر الخدمات الرقمية</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;500;600;700;800&display=swap" rel="stylesheet">
    
    <!-- Firebase SDKs -->
    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-app.js";
        import { getAuth, signInWithPopup, GoogleAuthProvider, createUserWithEmailAndPassword, signInWithEmailAndPassword, signOut, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-auth.js";
        
        // إعدادات Firebase الخاصة بك (التي أرسلتها)
        const firebaseConfig = {
            apiKey: "AIzaSyA8O0b6eRTSzIL2tBLHRbgOJPvdP3YvbdI",
            authDomain: "redeemstore-442e9.firebaseapp.com",
            projectId: "redeemstore-442e9",
            storageBucket: "redeemstore-442e9.firebasestorage.app",
            messagingSenderId: "310108021195",
            appId: "1:310108021195:web:f7dc3a59286c7d311a964e",
            measurementId: "G-GL65R5EELQ"
        };
        
        // تهيئة Firebase
        const app = initializeApp(firebaseConfig);
        const auth = getAuth(app);
        
        // جعل المصادقة متاحة عالمياً
        window.auth = auth;
        window.signInWithPopup = signInWithPopup;
        window.GoogleAuthProvider = GoogleAuthProvider;
        window.createUserWithEmailAndPassword = createUserWithEmailAndPassword;
        window.signInWithEmailAndPassword = signInWithEmailAndPassword;
        window.signOut = signOut;
        window.onAuthStateChanged = onAuthStateChanged;
        
        console.log("✅ Firebase تم تهيئته بنجاح!");
    </script>
    
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body {
            font-family: 'Cairo', sans-serif;
            background: linear-gradient(135deg, #0a0f1e 0%, #0c1222 100%);
            color: #eef2ff;
            line-height: 1.6;
        }
        ::-webkit-scrollbar { width: 10px; }
        ::-webkit-scrollbar-track { background: #1e293b; }
        ::-webkit-scrollbar-thumb { background: #f59e0b; border-radius: 10px; }
        
        .navbar {
            background: rgba(15, 23, 42, 0.95);
            backdrop-filter: blur(10px);
            padding: 1rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 1rem;
            border-bottom: 1px solid #f59e0b30;
            position: sticky;
            top: 0;
            z-index: 1000;
        }
        .logo {
            display: flex;
            align-items: center;
            gap: 12px;
            font-size: 1.7rem;
            font-weight: 800;
        }
        .logo span:first-child { color: #f59e0b; }
        .logo span:last-child {
            background: linear-gradient(135deg, #f59e0b, #fcd34d);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }
        .nav-links {
            display: flex;
            gap: 1.5rem;
            align-items: center;
            flex-wrap: wrap;
        }
        .nav-links a {
            color: #cbd5e6;
            text-decoration: none;
            font-weight: 500;
            transition: 0.3s;
            cursor: pointer;
        }
        .nav-links a:hover { color: #f59e0b; }
        .user-profile {
            display: flex;
            align-items: center;
            gap: 12px;
            background: #1e293b;
            padding: 6px 16px;
            border-radius: 60px;
            cursor: pointer;
            transition: 0.3s;
        }
        .user-profile:hover { background: #2d3a5e; }
        .user-profile img {
            width: 32px;
            height: 32px;
            border-radius: 50%;
        }
        .cart-icon {
            position: relative;
            cursor: pointer;
            font-size: 1.6rem;
            color: #f59e0b;
        }
        .cart-count {
            position: absolute;
            top: -8px;
            right: -12px;
            background: #ef4444;
            color: white;
            font-size: 0.7rem;
            font-weight: bold;
            border-radius: 50%;
            width: 20px;
            height: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .hero {
            text-align: center;
            padding: 3rem 1rem 2rem;
            background: radial-gradient(circle at 20% 30%, #1e2a47, #0a0f1e);
        }
        .hero h1 { font-size: 2.5rem; margin-bottom: 1rem; }
        .hero h1 i { color: #f59e0b; }
        .hero p { font-size: 1.2rem; color: #a0b3d9; max-width: 700px; margin: 0 auto; }
        .hash { margin-top: 1rem; font-weight: bold; color: #f59e0b; }
        .container { max-width: 1300px; margin: 2rem auto; padding: 0 1.5rem; }
        .section-title {
            font-size: 2rem;
            margin: 2rem 0 1.5rem 0;
            border-right: 6px solid #f59e0b;
            padding-right: 1rem;
        }
        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
            gap: 2rem;
        }
        .card {
            background: #111827cc;
            backdrop-filter: blur(4px);
            border-radius: 28px;
            padding: 1.5rem;
            border: 1px solid #2d3a5e;
            transition: transform 0.2s, box-shadow 0.2s;
        }
        .card:hover {
            transform: translateY(-5px);
            border-color: #f59e0b;
            box-shadow: 0 25px 30px -12px rgba(245,158,11,0.2);
        }
        .card-icon { font-size: 2.5rem; color: #f59e0b; margin-bottom: 1rem; }
        .card h3 { font-size: 1.5rem; margin-bottom: 0.75rem; }
        .card p { color: #b9c3e0; font-size: 0.9rem; margin: 0.75rem 0; }
        .price { font-size: 1.3rem; font-weight: bold; color: #fcd34d; margin: 1rem 0; }
        .btn-order {
            background: linear-gradient(90deg, #f59e0b, #eab308);
            border: none;
            width: 100%;
            padding: 12px;
            font-family: 'Cairo', sans-serif;
            font-weight: bold;
            border-radius: 40px;
            cursor: pointer;
            transition: 0.2s;
        }
        .btn-order:hover { transform: scale(0.97); background: #d97706; color: white; }
        .contact-strip {
            background: #0f172a;
            margin: 3rem 0;
            padding: 1.5rem;
            border-radius: 60px;
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 2rem;
            border: 1px solid #f59e0b30;
        }
        .contact-item {
            display: flex;
            align-items: center;
            gap: 10px;
            cursor: pointer;
            transition: 0.3s;
        }
        .contact-item:hover { color: #f59e0b; }
        .contact-item i { font-size: 1.6rem; color: #f59e0b; }
        
        /* Modal */
        .modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: #000000cc;
            backdrop-filter: blur(8px);
            z-index: 3000;
            display: flex;
            align-items: center;
            justify-content: center;
            visibility: hidden;
            opacity: 0;
            transition: 0.2s;
        }
        .modal.active { visibility: visible; opacity: 1; }
        .modal-card {
            background: #0f172a;
            max-width: 450px;
            width: 90%;
            padding: 2rem;
            border-radius: 48px;
            border: 1px solid #f59e0b;
            text-align: center;
        }
        .modal-card input {
            width: 100%;
            padding: 12px;
            margin: 10px 0;
            border-radius: 60px;
            border: none;
            background: #1e293b;
            color: white;
            font-family: 'Cairo', sans-serif;
        }
        .modal-card button {
            background: #f59e0b;
            border: none;
            padding: 10px;
            border-radius: 40px;
            width: 100%;
            margin-top: 10px;
            font-weight: bold;
            cursor: pointer;
        }
        .google-btn { background: #ffffff20; color: white; border: 1px solid #f59e0b; }
        
        /* Cart Sidebar */
        .cart-sidebar {
            position: fixed;
            top: 0;
            left: -380px;
            width: 380px;
            height: 100%;
            background: #0f172ae6;
            backdrop-filter: blur(20px);
            z-index: 2000;
            transition: left 0.3s;
            padding: 1.5rem;
            display: flex;
            flex-direction: column;
            border-left: 2px solid #f59e0b;
        }
        .cart-sidebar.open { left: 0; }
        .overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: #00000080;
            z-index: 1999;
            display: none;
        }
        .overlay.active { display: block; }
        footer { text-align: center; padding: 2rem; border-top: 1px solid #1e293b; margin-top: 3rem; color: #8192b0; }
        .logout-btn { cursor: pointer; color: #ef4444; margin-right: 10px; }
        .logout-btn:hover { color: #ff6666; }
        
        @media (max-width: 600px) {
            .navbar { flex-direction: column; }
            .cart-sidebar { width: 100%; left: -100%; }
        }
    </style>
</head>
<body>

<div class="navbar">
    <div class="logo">
        <span>Redeem</span>
        <span>خدمات</span>
        <i class="fas fa-store"></i>
    </div>
    <div class="nav-links">
        <a href="#services">الخدمات</a>
        <div class="user-profile" id="userProfileBtn">
            <i class="fas fa-user-circle"></i>
            <span id="userNameDisplay">دخول</span>
            <span id="logoutBtn" class="logout-btn" style="display:none;">✖</span>
        </div>
        <div class="cart-icon" id="cartIcon">
            <i class="fas fa-shopping-cart"></i>
            <span class="cart-count" id="cartCount">0</span>
        </div>
    </div>
</div>

<section class="hero">
    <h1><i class="fas fa-crown"></i> متجر REDEEM الشامل</h1>
    <p>وساطة الشراء | بطاقات VISA | اشتراكات | USDT | شحن أعمال</p>
    <div class="hash">#إشحن_وإنت_مطعم 🔥 #أنتـغرونـا</div>
</section>

<div class="container" id="services">
    <div class="section-title"><i class="fas fa-bolt"></i> خدماتنا المميزة</div>
    <div class="services-grid" id="servicesGrid"></div>
</div>

<div class="container">
    <div class="contact-strip">
        <div class="contact-item" id="whatsappBtn"><i class="fab fa-whatsapp"></i> +249901839168</div>
        <div class="contact-item" id="telegramBtn"><i class="fab fa-telegram"></i> @redeem</div>
        <div class="contact-item" id="telegramChannelBtn"><i class="fab fa-telegram-plane"></i> t.me/REDEEM_00</div>
    </div>
</div>

<footer>
    <p>© 2025 متجر REDEEM - جميع الخدمات رقمية يتم تنفيذها فور تأكيد الدفع</p>
    <p><i class="fas fa-shield-alt"></i> خدمات آمنة وسريعة - تواصل معنا لأي استفسار</p>
</footer>

<!-- Modal تسجيل الدخول -->
<div id="authModal" class="modal">
    <div class="modal-card">
        <h2><i class="fas fa-user-lock"></i> تسجيل الدخول</h2>
        <input type="email" id="loginEmail" placeholder="البريد الإلكتروني">
        <input type="password" id="loginPassword" placeholder="كلمة المرور">
        <button id="signInBtn">تسجيل الدخول</button>
        <button id="signUpBtn">إنشاء حساب جديد</button>
        <button id="googleSignInBtn" class="google-btn"><i class="fab fa-google"></i> تسجيل دخول عبر Google</button>
        <button id="closeModalBtn" style="background:#334155;">إغلاق</button>
    </div>
</div>

<!-- سلة المشتريات -->
<div class="overlay" id="overlayCart"></div>
<div class="cart-sidebar" id="cartSidebar">
    <div style="display:flex; justify-content:space-between; align-items:center; border-bottom:1px solid #f59e0b; padding-bottom:1rem;">
        <h3><i class="fas fa-bag-shopping"></i> سلة المشتريات</h3>
        <button id="closeCartBtn" style="background:none; border:none; color:white; font-size:1.8rem; cursor:pointer;">&times;</button>
    </div>
    <div id="cartItemsList" style="flex:1; overflow:auto; margin:1rem 0;"></div>
    <div id="cartTotal" style="font-size:1.3rem; border-top:1px solid #334155; padding-top:1rem; text-align:center;">المجموع: 0 USDT</div>
    <button id="checkoutBtn" style="background:#22c55e; border:none; padding:12px; border-radius:40px; margin-top:1rem; font-weight:bold; cursor:pointer;">💸 إتمام الدفع (USDT)</button>
</div>

<script type="module">
    // بيانات الخدمات
    const servicesData = [
        { id: 1, name: "وساطة الشراء", desc: "نشتري لك أي منتج من الإنترنت (أمازون، AliExpress، شي إن..)", price: 5, icon: "fas fa-shopping-bag" },
        { id: 2, name: "بطاقة VISA رقمية", desc: "بطاقة دفع إلكترونية عالمية للتسوق والاشتراكات", price: 12, icon: "fab fa-cc-visa" },
        { id: 3, name: "بطاقات المتاجر", desc: "Amazon, Google Play, iTunes, Noon, Shein", price: 10, icon: "fas fa-tags" },
        { id: 4, name: "تجديد الاشتراكات", desc: "Netflix, Canva, Spotify, Starlink, Coursera", price: 8, icon: "fas fa-tv" },
        { id: 5, name: "شراء USDT", desc: "أفضل أسعار لشراء USDT (TRC20 / ERC20)", price: 0, note: "سعر السوق", icon: "fas fa-coins" },
        { id: 6, name: "بيع USDT", desc: "نشتري منك USDT إذا عندك بأفضل الأسعار", price: 0, note: "سعر السوق", icon: "fas fa-exchange-alt" },
        { id: 7, name: "شحن الأعمال الإلكترونية", desc: "شحن مباشر + بطاقات هدايا احترافية", price: 7, icon: "fas fa-charging-station" },
        { id: 8, name: "حزمة الاشتراكات بريميوم", desc: "نتفلكس + سبوتيفاي + كانفا (باقة شهرية)", price: 25, icon: "fas fa-crown" }
    ];
    
    let cart = [];
    let currentUser = null;
    
    // الحصول على مراجع Firebase من window
    const auth = window.auth;
    const signInWithPopup = window.signInWithPopup;
    const GoogleAuthProvider = window.GoogleAuthProvider;
    const createUserWithEmailAndPassword = window.createUserWithEmailAndPassword;
    const signInWithEmailAndPassword = window.signInWithEmailAndPassword;
    const signOut = window.signOut;
    const onAuthStateChanged = window.onAuthStateChanged;
    
    // توليد بطاقات الخدمات
    function renderServices() {
        const grid = document.getElementById('servicesGrid');
        if (!grid) return;
        grid.innerHTML = '';
        servicesData.forEach(service => {
            const priceText = service.price === 0 ? (service.note || "سعر السوق") : `${service.price} USDT`;
            const card = document.createElement('div');
            card.className = 'card';
            card.innerHTML = `
                <div class="card-icon"><i class="${service.icon}"></i></div>
                <h3>${service.name}</h3>
                <p>${service.desc}</p>
                <div class="price">${priceText}</div>
                <button class="btn-order" data-id="${service.id}">🛒 أضف إلى السلة</button>
            `;
            card.querySelector('.btn-order').addEventListener('click', () => addToCart(service));
            grid.appendChild(card);
        });
    }
    
    function addToCart(service) {
        if (!currentUser) {
            alert("🔐 يرجى تسجيل الدخول أولاً لإضافة خدمات إلى السلة");
            openAuthModal();
            return;
        }
        if (service.price === 0) {
            alert("💰 سعر هذه الخدمة متغير حسب السوق. يرجى التواصل معنا عبر واتساب للحصول على السعر.");
            return;
        }
        const existing = cart.find(item => item.id === service.id);
        if (existing) {
            existing.quantity++;
        } else {
            cart.push({ ...service, quantity: 1 });
        }
        saveCart();
        renderCartUI();
        openCartSidebar();
    }
    
    function saveCart() {
        if (currentUser) {
            localStorage.setItem(`cart_${currentUser.uid}`, JSON.stringify(cart));
        }
    }
    
    function loadCart() {
        if (currentUser) {
            const saved = localStorage.getItem(`cart_${currentUser.uid}`);
            cart = saved ? JSON.parse(saved) : [];
        } else {
            cart = [];
        }
        renderCartUI();
    }
    
    function renderCartUI() {
        const container = document.getElementById('cartItemsList');
        const totalSpan = document.getElementById('cartTotal');
        const countSpan = document.getElementById('cartCount');
        
        if (!container) return;
        
        if (cart.length === 0) {
            container.innerHTML = '<p style="text-align:center; color:#a0b3d9;">🛒 السلة فارغة</p>';
            totalSpan.innerText = 'المجموع: 0 USDT';
            if (countSpan) countSpan.innerText = '0';
            return;
        }
        
        let total = 0;
        let itemsCount = 0;
        let html = '';
        
        cart.forEach((item, idx) => {
            const itemTotal = item.price * item.quantity;
            total += itemTotal;
            itemsCount += item.quantity;
            html += `
                <div style="background:#1e293b; margin:8px 0; padding:12px; border-radius:16px;">
                    <div><strong>${item.name}</strong></div>
                    <div style="display:flex; justify-content:space-between; align-items:center; margin-top:8px;">
                        <span>${item.price} USDT × ${item.quantity} = ${itemTotal} USDT</span>
                        <button onclick="window.removeCartItem(${idx})" style="background:#ef4444; border:none; padding:5px 12px; border-radius:20px; color:white; cursor:pointer;">حذف</button>
                    </div>
                </div>
            `;
        });
        
        container.innerHTML = html;
        totalSpan.innerText = `المجموع: ${total} USDT`;
        if (countSpan) countSpan.innerText = itemsCount;
        
        // تعريف الدالة عالمياً
        window.removeCartItem = (idx) => {
            cart.splice(idx, 1);
            saveCart();
            renderCartUI();
        };
    }
    
    // وظائف السلة الجانبية
    function openCartSidebar() {
        document.getElementById('cartSidebar').classList.add('open');
        document.getElementById('overlayCart').classList.add('active');
    }
    
    function closeCartSidebar() {
        document.getElementById('cartSidebar').classList.remove('open');
        document.getElementById('overlayCart').classList.remove('active');
    }
    
    // وظائف المصادقة
    const authModal = document.getElementById('authModal');
    
    function openAuthModal() {
        authModal.classList.add('active');
    }
    
    function closeAuthModal() {
        authModal.classList.remove('active');
    }
    
    async function handleGoogleSignIn() {
        try {
            const provider = new GoogleAuthProvider();
            const result = await signInWithPopup(auth, provider);
            currentUser = result.user;
            updateUIForUser();
            closeAuthModal();
            loadCart();
        } catch (error) {
            console.error(error);
            alert("خطأ في تسجيل الدخول: " + error.message);
        }
    }
    
    async function handleEmailSignUp(email, password) {
        try {
            const result = await createUserWithEmailAndPassword(auth, email, password);
            currentUser = result.user;
            updateUIForUser();
            closeAuthModal();
            loadCart();
        } catch (error) {
            alert(error.message);
        }
    }
    
    async function handleEmailSignIn(email, password) {
        try {
            const result = await signInWithEmailAndPassword(auth, email, password);
            currentUser = result.user;
            updateUIForUser();
            closeAuthModal();
            loadCart();
        } catch (error) {
            alert("خطأ: " + error.message);
        }
    }
    
    async function handleSignOut() {
        try {
            await signOut(auth);
            currentUser = null;
            updateUIForUser();
            cart = [];
            renderCartUI();
            alert("👋 تم تسجيل الخروج بنجاح");
        } catch (error) {
            console.error(error);
        }
    }
    
    function updateUIForUser() {
        const userNameSpan = document.getElementById('userNameDisplay');
        const logoutBtn = document.getElementById('logoutBtn');
        
        if (currentUser) {
            const displayName = currentUser.displayName || currentUser.email || 'مستخدم';
            userNameSpan.innerHTML = `<i class="fas fa-user-check"></i> ${displayName.split('@')[0]}`;
            logoutBtn.style.display = 'inline';
        } else {
            userNameSpan.innerHTML = '<i class="fas fa-user-circle"></i> دخول';
            logoutBtn.style.display = 'none';
        }
    }
    
    // مراقبة حالة تسجيل الدخول
    if (onAuthStateChanged) {
        onAuthStateChanged(auth, (user) => {
            currentUser = user;
            updateUIForUser();
            loadCart();
        });
    }
    
    // إضافة مستمعي الأحداث
    document.getElementById('userProfileBtn').addEventListener('click', () => {
        if (currentUser) {
            // إذا كان مسجل دخول، لا شيء
        } else {
            openAuthModal();
        }
    });
    
    document.getElementById('logoutBtn').addEventListener('click', (e) => {
        e.stopPropagation();
        handleSignOut();
    });
    
    document.getElementById('signInBtn').addEventListener('click', () => {
        const email = document.getElementById('loginEmail').value;
        const pass = document.getElementById('loginPassword').value;
        if (email && pass) handleEmailSignIn(email, pass);
        else alert("✏️ أدخل البريد الإلكتروني وكلمة المرور");
    });
    
    document.getElementById('signUpBtn').addEventListener('click', () => {
        const email = document.getElementById('loginEmail').value;
        const pass = document.getElementById('loginPassword').value;
        if (email && pass) handleEmailSignUp(email, pass);
        else alert("✏️ أدخل البريد الإلكتروني وكلمة المرور");
    });
    
    document.getElementById('googleSignInBtn').addEventListener('click', handleGoogleSignIn);
    document.getElementById('closeModalBtn').addEventListener('click', closeAuthModal);
    document.getElementById('cartIcon').addEventListener('click', openCartSidebar);
    document.getElementById('closeCartBtn').addEventListener('click', closeCartSidebar);
    document.getElementById('overlayCart').addEventListener('click', closeCartSidebar);
    
    // زر إتمام الدفع
    document.getElementById('checkoutBtn').addEventListener('click', () => {
        if (!currentUser) {
            alert("🔐 يرجى تسجيل الدخول أولاً لإتمام الطلب");
            openAuthModal();
            return;
        }
        if (cart.length === 0) {
            alert("🛒 السلة فارغة، أضف خدمات أولاً");
            return;
        }
        
        let total = 0;
        let orderDetails = "🛍️ طلب جديد من متجر REDEEM:\n\n";
        cart.forEach(item => {
            const itemTotal = item.price * item.quantity;
            total += itemTotal;
            orderDetails += `• ${item.name} × ${item.quantity} = ${itemTotal} USDT\n`;
        });
        orderDetails += `\n💰 الإجمالي: ${total} USDT\n`;
        orderDetails += `👤 العميل: ${currentUser.email}\n\n`;
        orderDetails += `📦 الرجاء تأكيد الطلب وإرسال تفاصيل الدفع (USDT).\n شكراً!`;
        
        const encodedMsg = encodeURIComponent(orderDetails);
        const phone = "+249901839168";
        window.open(`https://wa.me/${phone}?text=${encodedMsg}`, '_blank');
    });
    
    // أزرار التواصل
    document.getElementById('whatsappBtn').addEventListener('click', () => {
        window.open('https://wa.me/+249901839168', '_blank');
    });
    document.getElementById('telegramBtn').addEventListener('click', () => {
        window.open('https://t.me/redeem', '_blank');
    });
    document.getElementById('telegramChannelBtn').addEventListener('click', () => {
        window.open('https://t.me/REDEEM_00', '_blank');
    });
    
    // بدء تشغيل المتجر
    renderServices();
    
    // إغلاق المودال عند الضغط خارجها
    authModal.addEventListener('click', (e) => {
        if (e.target === authModal) closeAuthModal();
    });
    
    console.log("✅ Redeem Store يعمل بكامله مع Firebase!");
</script>
</body>
</html>
