<!DOCTYPE html>

<html lang="mn">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Номын Ертөнц</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet"/>
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

```
:root {
  --bg: #0f0d0a;
  --surface: #1a1710;
  --card: #211e18;
  --gold: #c9a84c;
  --gold-light: #e8c97a;
  --cream: #f5efe0;
  --muted: #7a7060;
  --text: #e8e0d0;
}

body {
  font-family: 'DM Sans', sans-serif;
  background: var(--bg);
  color: var(--text);
  min-height: 100vh;
  overflow-x: hidden;
}

/* NOISE TEXTURE */
body::before {
  content: '';
  position: fixed;
  inset: 0;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
  pointer-events: none;
  z-index: 0;
  opacity: 0.4;
}

/* NAV */
nav {
  position: fixed;
  top: 0; left: 0; right: 0;
  z-index: 100;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.2rem 3rem;
  background: rgba(15,13,10,0.85);
  backdrop-filter: blur(12px);
  border-bottom: 1px solid rgba(201,168,76,0.15);
}

.logo {
  font-family: 'Playfair Display', serif;
  font-size: 1.4rem;
  color: var(--gold);
  letter-spacing: 0.05em;
}

.nav-links {
  display: flex;
  gap: 2rem;
  list-style: none;
}

.nav-links a {
  color: var(--muted);
  text-decoration: none;
  font-size: 0.85rem;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  transition: color 0.3s;
}

.nav-links a:hover { color: var(--gold); }

/* HERO */
.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  padding: 6rem 2rem 4rem;
  position: relative;
}

.hero-bg {
  position: absolute;
  inset: 0;
  background: radial-gradient(ellipse 80% 60% at 50% 40%, rgba(201,168,76,0.08) 0%, transparent 70%);
}

.hero-content { position: relative; z-index: 1; max-width: 700px; }

.hero-tag {
  display: inline-block;
  font-size: 0.75rem;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--gold);
  border: 1px solid rgba(201,168,76,0.4);
  padding: 0.3rem 1rem;
  border-radius: 100px;
  margin-bottom: 2rem;
  animation: fadeUp 0.8s ease both;
}

.hero h1 {
  font-family: 'Playfair Display', serif;
  font-size: clamp(3rem, 8vw, 5.5rem);
  line-height: 1.1;
  color: var(--cream);
  margin-bottom: 1.5rem;
  animation: fadeUp 0.8s 0.15s ease both;
}

.hero h1 em {
  font-style: italic;
  color: var(--gold);
}

.hero p {
  font-size: 1.05rem;
  color: var(--muted);
  line-height: 1.8;
  margin-bottom: 2.5rem;
  animation: fadeUp 0.8s 0.3s ease both;
}

.hero-btns {
  display: flex;
  gap: 1rem;
  justify-content: center;
  flex-wrap: wrap;
  animation: fadeUp 0.8s 0.45s ease both;
}

.btn-primary {
  background: var(--gold);
  color: var(--bg);
  padding: 0.85rem 2rem;
  border: none;
  border-radius: 4px;
  font-size: 0.9rem;
  font-weight: 500;
  cursor: pointer;
  letter-spacing: 0.05em;
  transition: background 0.3s, transform 0.2s;
  text-decoration: none;
}

.btn-primary:hover { background: var(--gold-light); transform: translateY(-2px); }

.btn-outline {
  background: transparent;
  color: var(--gold);
  padding: 0.85rem 2rem;
  border: 1px solid rgba(201,168,76,0.4);
  border-radius: 4px;
  font-size: 0.9rem;
  cursor: pointer;
  letter-spacing: 0.05em;
  transition: border-color 0.3s, transform 0.2s;
  text-decoration: none;
}

.btn-outline:hover { border-color: var(--gold); transform: translateY(-2px); }

/* SEARCH */
.search-section {
  padding: 3rem 2rem;
  max-width: 600px;
  margin: 0 auto;
}

.search-box {
  display: flex;
  background: var(--card);
  border: 1px solid rgba(201,168,76,0.2);
  border-radius: 8px;
  overflow: hidden;
  transition: border-color 0.3s;
}

.search-box:focus-within { border-color: var(--gold); }

.search-box input {
  flex: 1;
  background: transparent;
  border: none;
  padding: 1rem 1.2rem;
  color: var(--text);
  font-size: 0.95rem;
  outline: none;
  font-family: 'DM Sans', sans-serif;
}

.search-box input::placeholder { color: var(--muted); }

.search-box button {
  background: var(--gold);
  border: none;
  padding: 1rem 1.5rem;
  color: var(--bg);
  cursor: pointer;
  font-size: 1rem;
  transition: background 0.3s;
}

.search-box button:hover { background: var(--gold-light); }

/* CATEGORIES */
.section { padding: 4rem 2rem; max-width: 1100px; margin: 0 auto; }

.section-header {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
  margin-bottom: 2rem;
}

.section-title {
  font-family: 'Playfair Display', serif;
  font-size: 1.8rem;
  color: var(--cream);
}

.section-link {
  color: var(--gold);
  font-size: 0.85rem;
  text-decoration: none;
  letter-spacing: 0.05em;
}

.categories {
  display: flex;
  gap: 0.8rem;
  flex-wrap: wrap;
  margin-bottom: 3rem;
}

.cat-btn {
  padding: 0.5rem 1.2rem;
  border-radius: 100px;
  border: 1px solid rgba(201,168,76,0.25);
  background: transparent;
  color: var(--muted);
  font-size: 0.85rem;
  cursor: pointer;
  transition: all 0.3s;
  font-family: 'DM Sans', sans-serif;
}

.cat-btn:hover, .cat-btn.active {
  background: var(--gold);
  color: var(--bg);
  border-color: var(--gold);
}

/* BOOK GRID */
.books-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 1.5rem;
}

.book-card {
  background: var(--card);
  border-radius: 8px;
  overflow: hidden;
  border: 1px solid rgba(255,255,255,0.05);
  transition: transform 0.3s, border-color 0.3s;
  cursor: pointer;
  animation: fadeUp 0.6s ease both;
}

.book-card:hover {
  transform: translateY(-6px);
  border-color: rgba(201,168,76,0.3);
}

.book-cover {
  width: 100%;
  aspect-ratio: 2/3;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: 'Playfair Display', serif;
  font-size: 1rem;
  text-align: center;
  padding: 1.5rem;
  position: relative;
  overflow: hidden;
}

.book-cover::after {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(to bottom, transparent 50%, rgba(0,0,0,0.5));
}

.book-cover span { position: relative; z-index: 1; line-height: 1.4; }

.book-info { padding: 1rem; }

.book-title {
  font-family: 'Playfair Display', serif;
  font-size: 0.95rem;
  color: var(--cream);
  margin-bottom: 0.3rem;
  line-height: 1.4;
}

.book-author {
  font-size: 0.8rem;
  color: var(--muted);
  margin-bottom: 0.6rem;
}

.book-meta {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.book-price {
  color: var(--gold);
  font-size: 0.9rem;
  font-weight: 500;
}

.book-rating {
  font-size: 0.8rem;
  color: var(--muted);
}

/* FEATURED */
.featured {
  background: var(--surface);
  border: 1px solid rgba(201,168,76,0.15);
  border-radius: 12px;
  padding: 3rem;
  display: grid;
  grid-template-columns: auto 1fr;
  gap: 3rem;
  align-items: center;
  margin: 2rem 0;
}

.featured-cover {
  width: 160px;
  aspect-ratio: 2/3;
  border-radius: 6px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: 'Playfair Display', serif;
  font-size: 1.1rem;
  text-align: center;
  padding: 1rem;
  background: linear-gradient(135deg, #2a5f3a, #1a3f28);
  box-shadow: 8px 8px 30px rgba(0,0,0,0.5);
}

.featured-tag {
  font-size: 0.7rem;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--gold);
  margin-bottom: 1rem;
}

.featured h2 {
  font-family: 'Playfair Display', serif;
  font-size: 2rem;
  color: var(--cream);
  margin-bottom: 0.5rem;
}

.featured .author {
  color: var(--muted);
  margin-bottom: 1rem;
  font-size: 0.9rem;
}

.featured p {
  color: var(--muted);
  line-height: 1.8;
  font-size: 0.9rem;
  margin-bottom: 1.5rem;
}

/* FOOTER */
footer {
  border-top: 1px solid rgba(255,255,255,0.06);
  padding: 3rem 2rem;
  text-align: center;
  color: var(--muted);
  font-size: 0.85rem;
}

footer .logo { display: block; margin-bottom: 1rem; font-size: 1.2rem; }

/* ANIMATIONS */
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(24px); }
  to { opacity: 1; transform: translateY(0); }
}

@media (max-width: 600px) {
  nav { padding: 1rem 1.5rem; }
  .nav-links { display: none; }
  .featured { grid-template-columns: 1fr; }
  .featured-cover { width: 120px; }
}
```

  </style>
</head>
<body>

<nav>
  <div class="logo">📖 Номын Ертөнц</div>
  <ul class="nav-links">
    <li><a href="#">Нүүр</a></li>
    <li><a href="#">Номнууд</a></li>
    <li><a href="#">Зохиолчид</a></li>
    <li><a href="#">Холбоо барих</a></li>
  </ul>
</nav>

<!-- HERO -->

<section class="hero">
  <div class="hero-bg"></div>
  <div class="hero-content">
    <div class="hero-tag">✦ Монголын хамгийн том номын сан</div>
    <h1>Номын <em>ертөнцөд</em><br/>тавтай морил</h1>
    <p>Мянга мянган ном нэг дороос. Уншиж, суралцаж,<br/>өөрийгөө хөгжүүл.</p>
    <div class="hero-btns">
      <a href="#books" class="btn-primary">Номуудыг үзэх</a>
      <a href="#" class="btn-outline">Бүртгүүлэх</a>
    </div>
  </div>
</section>

<!-- SEARCH -->

<div class="search-section">
  <div class="search-box">
    <input type="text" placeholder="Ном, зохиолч хайх..." />
    <button>🔍</button>
  </div>
</div>

<!-- FEATURED -->

<div class="section">
  <div class="featured">
    <div class="featured-cover">
      <span style="color:#a8d5b5">Нэгэн<br/>зуны<br/>үдэш</span>
    </div>
    <div>
      <div class="featured-tag">✦ Долоо хоногийн онцлох ном</div>
      <h2>Нэгэн зуны үдэш</h2>
      <div class="author">Д. Намдаг · 2023</div>
      <p>Монголын өргөн тал нутгийн дунд өрнөх энэхүү романд хайр, залуу нас, алдаа, эргэн тойрны ертөнцийг ухаарах тухай гүн ухагдахуун багтсан байдаг.</p>
      <a href="#" class="btn-primary">Унших</a>
    </div>
  </div>
</div>

<!-- BOOKS -->

<div class="section" id="books">
  <div class="section-header">
    <h2 class="section-title">Шинэ номнууд</h2>
    <a href="#" class="section-link">Бүгдийг харах →</a>
  </div>

  <div class="categories">
    <button class="cat-btn active">Бүгд</button>
    <button class="cat-btn">Роман</button>
    <button class="cat-btn">Шинжлэх ухаан</button>
    <button class="cat-btn">Түүх</button>
    <button class="cat-btn">Хүүхдийн</button>
    <button class="cat-btn">Бизнес</button>
    <button class="cat-btn">Сэтгэл судлал</button>
  </div>

  <div class="books-grid">
    <!-- Book 1 -->
    <div class="book-card" style="animation-delay:0.1s">
      <div class="book-cover" style="background:linear-gradient(135deg,#1a3a5c,#0d2035)">
        <span>Монгол нууц товчоо</span>
      </div>
      <div class="book-info">
        <div class="book-title">Монгол нууц товчоо</div>
        <div class="book-author">XIII зуун</div>
        <div class="book-meta">
          <span class="book-price">Үнэгүй</span>
          <span class="book-rating">⭐ 4.9</span>
        </div>
      </div>
    </div>

```
<!-- Book 2 -->
<div class="book-card" style="animation-delay:0.2s">
  <div class="book-cover" style="background:linear-gradient(135deg,#5c1a1a,#3d0d0d)">
    <span>Жаргалын тухай</span>
  </div>
  <div class="book-info">
    <div class="book-title">Жаргалын тухай</div>
    <div class="book-author">Б. Явуухулан</div>
    <div class="book-meta">
      <span class="book-price">₮12,000</span>
      <span class="book-rating">⭐ 4.7</span>
    </div>
  </div>
</div>

<!-- Book 3 -->
<div class="book-card" style="animation-delay:0.3s">
  <div class="book-cover" style="background:linear-gradient(135deg,#2a4a1a,#1a3010)">
    <span>Цагаан хэрэм</span>
  </div>
  <div class="book-info">
    <div class="book-title">Цагаан хэрэм</div>
    <div class="book-author">Д. Мягмар</div>
    <div class="book-meta">
      <span class="book-price">₮9,500</span>
      <span class="book-rating">⭐ 4.5</span>
    </div>
  </div>
</div>

<!-- Book 4 -->
<div class="book-card" style="animation-delay:0.4s">
  <div class="book-cover" style="background:linear-gradient(135deg,#4a3a1a,#2d2010)">
    <span>Тал нутгийн дуулал</span>
  </div>
  <div class="book-info">
    <div class="book-title">Тал нутгийн дуулал</div>
    <div class="book-author">Ц. Дамдинсүрэн</div>
    <div class="book-meta">
      <span class="book-price">₮11,000</span>
      <span class="book-rating">⭐ 4.8</span>
    </div>
  </div>
</div>

<!-- Book 5 -->
<div class="book-card" style="animation-delay:0.5s">
  <div class="book-cover" style="background:linear-gradient(135deg,#1a2a4a,#0d1a30)">
    <span>Оюун ухааны хүч</span>
  </div>
  <div class="book-info">
    <div class="book-title">Оюун ухааны хүч</div>
    <div class="book-author">Э. Батцэцэг</div>
    <div class="book-meta">
      <span class="book-price">₮8,000</span>
      <span class="book-rating">⭐ 4.6</span>
    </div>
  </div>
</div>

<!-- Book 6 -->
<div class="book-card" style="animation-delay:0.6s">
  <div class="book-cover" style="background:linear-gradient(135deg,#3a1a4a,#220d30)">
    <span>Шөнийн гэрэл</span>
  </div>
  <div class="book-info">
    <div class="book-title">Шөнийн гэрэл</div>
    <div class="book-author">Н. Энхбаяр</div>
    <div class="book-meta">
      <span class="book-price">₮10,500</span>
      <span class="book-rating">⭐ 4.4</span>
    </div>
  </div>
</div>
```

  </div>
</div>

<footer>
  <span class="logo">📖 Номын Ертөнц</span>
  <p>© 2024 Номын Ертөнц. Бүх эрх хуулиар хамгаалагдсан.</p>
</footer>

<script>
  // Category filter buttons
  document.querySelectorAll('.cat-btn').forEach(btn => {
    btn.addEventListener('click', () => {
      document.querySelectorAll('.cat-btn').forEach(b => b.classList.remove('active'));
      btn.classList.add('active');
    });
  });

  // Search functionality
  document.querySelector('.search-box button').addEventListener('click', () => {
    const val = document.querySelector('.search-box input').value;
    if (val.trim()) alert(`"${val}" хайж байна...`);
  });
</script>

</body>
</html>
