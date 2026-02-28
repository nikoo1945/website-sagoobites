<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sagobites - Cookies Anti Stunting</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">
    <style>
        /* ==================== VARIABEL & RESET ==================== */
        :root {
            --primary: #ff6bcb;
            --secondary: #6b5bff;
            --bg-dark: #050505;
            --card-bg: rgba(20, 20, 30, 0.6);
            --text-main: #ffffff;
            --text-muted: #94a3b8;
            --gradient-main: linear-gradient(135deg, #ff6bcb 0%, #6b5bff 100%);
            --glass-border: 1px solid rgba(255, 255, 255, 0.1);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Inter', sans-serif;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            background-color: var(--bg-dark);
            color: var(--text-main);
            overflow-x: hidden;
            line-height: 1.6;
        }

        /* ==================== BACKGROUND ANIMASI ==================== */
        .bg-grid {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: 
                linear-gradient(rgba(255, 255, 255, 0.03) 1px, transparent 1px),
                linear-gradient(90deg, rgba(255, 255, 255, 0.03) 1px, transparent 1px);
            background-size: 50px 50px;
            z-index: -2;
        }

        .bg-glow {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: 
                radial-gradient(circle at 10% 10%, rgba(107, 91, 255, 0.15), transparent 40%),
                radial-gradient(circle at 90% 90%, rgba(255, 107, 203, 0.15), transparent 40%);
            z-index: -1;
            pointer-events: none;
        }

        /* ==================== NAVIGASI ==================== */
        nav {
            position: fixed;
            top: 0;
            width: 100%;
            padding: 1.5rem 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            z-index: 1000;
            backdrop-filter: blur(12px);
            background: rgba(5, 5, 5, 0.7);
            border-bottom: var(--glass-border);
        }

        .logo {
            font-size: 1.5rem;
            font-weight: 800;
            display: flex;
            align-items: center;
            gap: 10px;
            color: white;
        }
        
        .logo span {
            background: var(--gradient-main);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .nav-links {
            display: flex;
            gap: 2rem;
        }

        .nav-links a {
            color: var(--text-muted);
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s;
            font-size: 0.9rem;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .nav-links a:hover {
            color: var(--text-main);
        }

        .btn-nav {
            background: var(--gradient-main);
            color: white;
            padding: 0.6rem 1.5rem;
            border-radius: 50px;
            text-decoration: none;
            font-weight: 600;
            font-size: 0.9rem;
            box-shadow: 0 0 20px rgba(255, 107, 203, 0.3);
            transition: transform 0.2s;
        }

        .btn-nav:hover {
            transform: translateY(-2px);
        }

        /* ==================== HERO SECTION ==================== */
        #hero {
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 0 20px;
            position: relative;
        }

        .hero-badge {
            display: inline-block;
            padding: 8px 16px;
            border-radius: 50px;
            background: rgba(255, 107, 203, 0.1);
            border: 1px solid rgba(255, 107, 203, 0.3);
            color: var(--primary);
            font-size: 0.85rem;
            font-weight: 600;
            margin-bottom: 24px;
            animation: fadeInDown 1s ease-out;
        }

        h1 {
            font-size: clamp(3rem, 10vw, 6rem);
            font-weight: 900;
            line-height: 1.1;
            margin-bottom: 24px;
            animation: fadeInUp 1s ease-out;
        }

        h1 span {
            background: var(--gradient-main);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-size: 200% auto;
            animation: gradientShift 3s ease infinite;
        }

        .hero-desc {
            max-width: 600px;
            color: var(--text-muted);
            font-size: 1.1rem;
            margin-bottom: 40px;
            animation: fadeInUp 1.2s ease-out;
        }

        .hero-cta {
            display: flex;
            gap: 1rem;
            animation: fadeInUp 1.4s ease-out;
        }

        .btn-primary {
            background: var(--text-main);
            color: #000;
            padding: 1rem 2rem;
            border-radius: 12px;
            font-weight: 700;
            text-decoration: none;
            display: flex;
            align-items: center;
            gap: 8px;
            transition: transform 0.2s, box-shadow 0.2s;
        }

        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 30px rgba(255, 255, 255, 0.2);
        }

        .btn-secondary {
            background: rgba(255, 255, 255, 0.05);
            color: white;
            padding: 1rem 2rem;
            border-radius: 12px;
            font-weight: 600;
            border: var(--glass-border);
            cursor: pointer;
            transition: background 0.2s;
        }

        .btn-secondary:hover {
            background: rgba(255, 255, 255, 0.1);
        }

        /* Floating Elements */
        .floating {
            position: absolute;
            font-size: 3rem;
            opacity: 0.8;
            animation: float 6s ease-in-out infinite;
            filter: drop-shadow(0 10px 20px rgba(0,0,0,0.3));
        }
        .f1 { top: 20%; left: 10%; animation-delay: 0s; }
        .f2 { top: 30%; right: 15%; animation-delay: 2s; font-size: 4rem; }
        .f3 { bottom: 20%; left: 20%; animation-delay: 4s; }

        /* ==================== MARQUEE ==================== */
        .marquee-container {
            overflow: hidden;
            white-space: nowrap;
            padding: 1.5rem 0;
            background: rgba(255, 255, 255, 0.02);
            border-top: var(--glass-border);
            border-bottom: var(--glass-border);
        }
        
        .marquee-content {
            display: inline-block;
            animation: marquee 25s linear infinite;
        }

        .marquee-item {
            display: inline-flex;
            align-items: center;
            gap: 10px;
            margin-right: 80px;
            color: var(--text-muted);
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .marquee-item span {
            color: var(--primary);
            font-size: 1.2rem;
        }

        /* ==================== CONTENT GRID (BENTO) ==================== */
        .bento-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 20px;
            padding: 40px 5%;
            max-width: 1400px;
            margin: 0 auto;
        }

        .card {
            background: var(--card-bg);
            border: var(--glass-border);
            border-radius: 24px;
            padding: 24px;
            backdrop-filter: blur(10px);
            transition: transform 0.3s, border-color 0.3s;
        }

        .card:hover {
            border-color: rgba(255, 107, 203, 0.3);
        }

        /* Bento Layout Spesifik */
        .bento-hero { grid-column: span 2; display: flex; flex-direction: column; justify-content: space-between; min-height: 400px; }
        .bento-chat { grid-column: span 2; grid-row: span 2; display: flex; flex-direction: column; }
        .bento-order { grid-column: span 2; }
        .bento-stats { grid-column: span 1; display: flex; flex-direction: column; justify-content: center; text-align: center; }
        .bento-stats:nth-child(5) { grid-column: span 1; }
        .bento-stats:nth-child(6) { grid-column: span 2; flex-direction: row; justify-content: space-around; text-align: left; }

        /* Produk Card Content */
        .product-header { display: flex; justify-content: space-between; align-items: start; }
        .tag { background: rgba(255,255,255,0.1); padding: 6px 12px; border-radius: 6px; font-size: 12px; font-weight: 600; }
        .price { font-size: 2.5rem; font-weight: 800; margin: 10px 0; background: var(--gradient-main); -webkit-background-clip: text; -webkit-text-fill-color: transparent; }
        .features { display: flex; gap: 10px; margin-top: 10px; }
        .feature-pill { background: rgba(255, 107, 203, 0.1); color: var(--primary); padding: 6px 12px; border-radius: 50px; font-size: 0.85rem; font-weight: 600; }

        /* Chat Card Content */
        .chat-header { display: flex; align-items: center; gap: 12px; margin-bottom: 16px; padding-bottom: 16px; border-bottom: var(--glass-border); }
        .chat-avatar { width: 40px; height: 40px; border-radius: 50%; background: var(--gradient-main); display: flex; align-items: center; justify-content: center; font-size: 20px; }
        
        #chat-box {
            flex: 1;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
            gap: 12px;
            padding-right: 8px;
            margin-bottom: 16px;
            scrollbar-width: thin;
            scrollbar-color: rgba(255,255,255,0.2) transparent;
        }

        .message {
            padding: 12px 16px;
            border-radius: 12px;
            max-width: 85%;
            font-size: 14px;
            animation: fadeIn 0.3s ease;
        }
        .msg-user { background: var(--secondary); align-self: flex-end; border-bottom-right-radius: 4px; }
        .msg-ai { background: rgba(255,255,255,0.1); align-self: flex-start; border-bottom-left-radius: 4px; }
        
        .chat-input-area { display: flex; gap: 10px; margin-top: auto; }
        .input-style { background: rgba(0,0,0,0.3); border: 1px solid rgba(255,255,255,0.1); color: white; padding: 12px; border-radius: 10px; outline: none; width: 100%; }
        .input-style:focus { border-color: var(--primary); }
        
        .btn-send { background: var(--gradient-main); color: white; border: none; padding: 0 20px; border-radius: 10px; cursor: pointer; font-weight: 600; transition: opacity 0.2s; }
        .btn-send:hover { opacity: 0.9; }
        .btn-send:disabled { opacity: 0.5; cursor: not-allowed; }

        /* Order Form */
        .order-form { display: grid; gap: 12px; margin-top: 16px; }
        .btn-wa { background: #25D366; color: white; border: none; padding: 12px; border-radius: 10px; font-weight: 700; cursor: pointer; width: 100%; margin-top: 8px; display: flex; justify-content: center; align-items: center; gap: 8px; }

        /* Stats */
        .stat-val { font-size: 2rem; font-weight: 800; color: white; }
        .stat-label { font-size: 0.9rem; color: var(--text-muted); }

        /* ==================== ANIMASI KEYFRAMES ==================== */
        @keyframes fadeInUp { from { opacity: 0; transform: translateY(20px); } to { opacity: 1; transform: translateY(0); } }
        @keyframes fadeInDown { from { opacity: 0; transform: translateY(-20px); } to { opacity: 1; transform: translateY(0); } }
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
        @keyframes float { 0%, 100% { transform: translateY(0px); } 50% { transform: translateY(-20px); } }
        @keyframes gradientShift { 0% { background-position: 0% 50%; } 50% { background-position: 100% 50%; } 100% { background-position: 0% 50%; } }
        @keyframes marquee { 0% { transform: translateX(0); } 100% { transform: translateX(-50%); } }

        /* ==================== RESPONSIVE ==================== */
        @media (max-width: 1024px) {
            .bento-grid { grid-template-columns: repeat(2, 1fr); }
            .bento-hero { grid-column: span 2; }
            .bento-chat { grid-column: span 2; grid-row: span 1; height: 500px; }
            .bento-stats:nth-child(6) { grid-column: span 2; }
        }
        @media (max-width: 640px) {
            .bento-grid { grid-template-columns: 1fr; }
            .bento-hero, .bento-chat, .bento-order, .bento-stats { grid-column: span 1; }
            .nav-links { display: none; }
            h1 { font-size: 2.5rem; }
        }
    </style>
</head>
<body>

    <!-- Background Effects -->
    <div class="bg-grid"></div>
    <div class="bg-glow"></div>

    <!-- Navbar -->
    <nav>
        <div class="logo">🍪 Sagobites</div>
        <div class="nav-links">
            <a href="#produk">Produk</a>
            <a href="#chat">AI Chat</a>
            <a href="#order">Pesan</a>
        </div>
        <a href="#order" class="btn-nav">Beli Sekarang</a>
    </nav>

    <!-- Hero Section -->
    <section id="hero">
        <div class="floating f1">🍪</div>
        <div class="floating f2">🍪</div>
        <div class="floating f3">🍪</div>

        <div class="hero-badge">🚀 Solusi Stunting Terenak di Indonesia</div>
        <h1>Bangun Masa Depan <br><span>Dengan Gizi Lezat</span></h1>
        <p class="hero-desc">Sagobites Cookies. Tinggi Protein (15g), Rendah Kalori, Tanpa Gula. Dibuat untuk anak Indonesia agar tumbuh tinggi, kuat, dan cerdas.</p>
        
        <div class="hero-cta">
            <a href="#order" class="btn-primary">🛒 Pesan Sekarang</a>
            <button onclick="document.getElementById('chat').scrollIntoView({behavior: 'smooth'})" class="btn-secondary">💬 Tanya Magoo AI</button>
        </div>
    </section>

    <!-- Marquee -->
    <div class="marquee-container">
        <div class="marquee-content">
            <div class="marquee-item"><span>🔥</span> PROTEIN TINGGI 15g</div>
            <div class="marquee-item"><span>🌿</span> PEMANIS ALAMI STEVIA</div>
            <div class="marquee-item"><span>🚫</span> BEBAS GULA</div>
            <div class="marquee-item"><span>👶</span> ANTI STUNTING</div>
            <div class="marquee-item"><span>💪</span> PERTUMBUHAN ANAK</div>
            <!-- Duplikat untuk seamless loop -->
            <div class="marquee-item"><span>🔥</span> PROTEIN TINGGI 15g</div>
            <div class="marquee-item"><span>🌿</span> PEMANIS ALAMI STEVIA</div>
            <div class="marquee-item"><span>🚫</span> BEBAS GULA</div>
            <div class="marquee-item"><span>👶</span> ANTI STUNTING</div>
            <div class="marquee-item"><span>💪</span> PERTUMBUHAN ANAK</div>
        </div>
    </div>

    <!-- Bento Grid Content -->
    <div class="bento-grid" style="margin-top: 40px;">
        
        <!-- 1. Produk Utama -->
        <div class="card bento-hero" id="produk">
            <div>
                <div class="product-header">
                    <span class="tag">Best Seller</span>
                    <span class="tag">Terlaris 2024</span>
                </div>
                <h2 style="font-size: 2rem; margin: 10px 0;">Sagobites Cookies</h2>
                <p style="color: var(--text-muted); font-size: 0.95rem;">Camilan fungsional tinggi protein untuk mendukung tumbuh kembang anak. Cocok untuk pencegahan stunting dengan rasa yang disukai anak-anak.</p>
                <div class="price">Rp 35.000</div>
                <div class="features">
                    <div class="feature-pill">15g Protein</div>
                    <div class="feature-pill">0g Gula</div>
                    <div class="feature-pill">100 Kkal</div>
                </div>
            </div>
            <div style="margin-top: 20px; font-size: 4rem; text-align: right;">🍪</div>
        </div>

        <!-- 2. AI Chat Card -->
        <div class="card bento-chat" id="chat">
            <div class="chat-header">
                <div class="chat-avatar">🐛</div>
                <div>
                    <h4 style="margin: 0;">Magoo AI</h4>
                    <div style="font-size: 12px; color: #10b981;">● Online - Siap Membantu</div>
                </div>
            </div>
            
            <div id="chat-box">
                <div class="message msg-ai">Halo! Saya Magoo, asisten virtual Sagobites. Silakan tanyakan seputar stunting, gizi, atau produk kita! 🍪</div>
            </div>

            <div class="chat-input-area">
                <input type="text" id="user-input" class="input-style" placeholder="Ketik pertanyaan..." onkeydown="if(event.key==='Enter')sendMessage()">
                <button id="send-btn" onclick="sendMessage()" class="btn-send">Kirim</button>
            </div>
        </div>

        <!-- 3. Stats 1 -->
        <div class="card bento-stats">
            <div class="stat-val">100%</div>
            <div class="stat-label">Bahan Alami</div>
        </div>

        <!-- 4. Stats 2 -->
        <div class="card bento-stats">
            <div class="stat-val">15g</div>
            <div class="stat-label">Protein</div>
        </div>

        <!-- 5. Order Form -->
        <div class="card bento-order" id="order">
            <h3 style="margin-bottom: 10px;">📝 Form Pemesanan</h3>
            <div style="color: var(--text-muted); font-size: 0.9rem;">Isi data di bawah untuk langsung order via WhatsApp.</div>
            
            <div class="order-form">
                <input type="text" id="nama" class="input-style" placeholder="Nama Lengkap">
                <input type="text" id="alamat" class="input-style" placeholder="Alamat Pengiriman">
                <input type="number" id="qty" class="input-style" placeholder="Jumlah Pack" value="1">
                <button onclick="handleOrder()" class="btn-wa">💬 Pesan via WhatsApp</button>
            </div>
        </div>

        <!-- 6. Info Stunting -->
        <div class="card bento-stats" style="background: linear-gradient(135deg, rgba(107, 91, 255, 0.2), rgba(255, 107, 203, 0.1)); text-align: left; align-items: flex-start;">
            <div class="stat-val" style="font-size: 1.5rem; color: var(--primary);">Apa itu Stunting?</div>
            <p style="font-size: 0.85rem; margin-top: 8px; color: #cbd5e1;">Stunting adalah gangguan pertumbuhan anak akibat kekurangan gizi kronis. Sagobites hadir sebagai solusi camilan tinggi protein untuk mendukung tumbuh kembang optimal.</p>
        </div>

    </div>

    <footer style="text-align: center; padding: 40px 0; color: var(--text-muted); font-size: 0.8rem;">
        © 2024 Sagobites Indonesia. Built with ❤️ for healthier generation.
    </footer>

    <script>
        // ==========================================
        // CONFIGURATION & VARIABLES
        // ==========================================
        const API_KEY = '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'; // OpenRouter Key
        const API_URL = 'https://openrouter.ai/api/v1/chat/completions';
        
        // System prompt untuk mendefinisikan karakter Magoo
        const SYSTEM_PROMPT = `
            Kamu adalah Magoo, seekor ulat sagu yang ramah, lucu, dan cerdas. 
            Kamu adalah maskot resmi produk 'Sagobites Protein Cookies'.
            Tugasmu adalah membantu menjawab pertanyaan seputar:
            1. Stunting dan pencegahannya (gizi buruk, protein, dll).
            2. Nutrisi dan kesehatan anak.
            3. Informasi produk Sagobites (Tinggi protein 15g, 100kkal, tanpa gula/stevia, harga Rp 35.000).
            
            Aturan:
            - Jawab dengan bahasa Indonesia yang santai namun informatif.
            - Gunakan emoji yang sesuai untuk membuat suasana lebih hidup.
            - Jika ditanya di luar konteks kesehatan/nutrisi, jawab dengan pintar tapi tetap ingatkan bahwa kamu ahli gizi.
            - Dorong pengguna untuk membeli Sagobites jika relevan.
        `;

        const chatBox = document.getElementById('chat-box');
        const userInput = document.getElementById('user-input');
        const sendBtn = document.getElementById('send-btn');
        let conversationHistory = [{ role: 'system', content: SYSTEM_PROMPT }];

        // ==========================================
        // CHAT FUNCTION (AI MAGOO)
        // ==========================================
        function addMessage(role, text) {
            const div = document.createElement('div');
            div.className = `message ${role === 'user' ? 'msg-user' : 'msg-ai'}`;
            div.textContent = text;
            chatBox.appendChild(div);
            chatBox.scrollTop = chatBox.scrollHeight;
        }

        function showTyping() {
            const div = document.createElement('div');
            div.className = 'message msg-ai';
            div.id = 'typing-indicator';
            div.textContent = '...';
            chatBox.appendChild(div);
            chatBox.scrollTop = chatBox.scrollHeight;
        }

        function removeTyping() {
            const el = document.getElementById('typing-indicator');
            if (el) el.remove();
        }

        async function sendMessage() {
            const text = userInput.value.trim();
            if (!text) return;

            // 1. Tampilkan pesan user
            addMessage('user', text);
            userInput.value = '';
            sendBtn.disabled = true;
            
            // 2. Tambahkan ke history
            conversationHistory.push({ role: 'user', content: text });

            // 3. Tampilkan typing indicator
            showTyping();

            try {
                const response = await fetch(API_URL, {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                        'Authorization': `Bearer ${API_KEY}`,
                        'HTTP-Referer': window.location.href, 
                        'X-Title': 'Sagobites Magoo AI'
                    },
                    body: JSON.stringify({
                        model: 'openai/gpt-3.5-turbo', // Cepat dan murah via OpenRouter
                        messages: conversationHistory
                    })
                });

                const data = await response.json();
                removeTyping();

                if (data.choices && data.choices.length > 0) {
                    const reply = data.choices[0].message.content;
                    addMessage('assistant', reply);
                    
                    // Tambahkan jawaban AI ke history
                    conversationHistory.push({ role: 'assistant', content: reply });
                } else {
                    console.error(data);
                    addMessage('assistant', 'Oops, ada gangguan jaringan otak saya. Coba lagi ya! 🤖');
                }

            } catch (error) {
                removeTyping();
                console.error(error);
                addMessage('assistant', 'Waduh, server saya lagi istirahat. Coba sebentar lagi ya! 🛑');
            } finally {
                sendBtn.disabled = false;
            }
        }

        // ==========================================
        // ORDER FUNCTION
        // ==========================================
        function handleOrder() {
            const nama = document.getElementById('nama').value;
            const alamat = document.getElementById('alamat').value;
            const qty = document.getElementById('qty').value;

            if(!nama || !alamat) {
                alert("Nama dan Alamat harus diisi ya!");
                return;
            }

            const total = qty * 35000;
            const text = `Halo Admin Sagobites! Saya mau pesan:\n\n` +
                         `*Produk:* Sagobites Protein Cookie\n` +
                         `*Jumlah:* ${qty} Pack\n` +
                         `*Total:* Rp ${total.toLocaleString('id-ID')}\n\n` +
                         `*Nama:* ${nama}\n` +
                         `*Alamat:* ${alamat}`;
            
            // GANTI DENGAN NOMOR WHATSAPP ADMIN ANDA
            const waLink = `https://wa.me/6281234567890?text=${encodeURIComponent(text)}`;
            window.open(waLink, '_blank');
        }
    </script>
</body>
</html>
