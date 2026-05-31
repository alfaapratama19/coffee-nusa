<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Nusantara Coffee</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400&family=Crimson+Pro:wght@300;400;600&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --cream: #F5EDD8;
    --cream-dark: #EAD9B8;
    --brown-light: #C4956A;
    --brown: #7B4F2E;
    --brown-dark: #3E2010;
    --espresso: #1C0D05;
    --gold: #C8933A;
    --green: #3A5940;
    --text: #2A1508;
    --text-muted: #7B5E45;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    background-color: var(--espresso);
    color: var(--cream);
    font-family: 'DM Sans', sans-serif;
    overflow-x: hidden;
  }

  /* ---- NOISE TEXTURE OVERLAY ---- */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 999;
    opacity: 0.5;
  }

  /* ---- NAV ---- */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 1.5rem 4rem;
    background: rgba(28, 13, 5, 0.85);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid rgba(200, 147, 58, 0.2);
  }

  .nav-logo {
    font-family: 'Playfair Display', serif;
    font-size: 1.5rem;
    letter-spacing: 0.05em;
    color: var(--gold);
    text-decoration: none;
  }

  .nav-logo span {
    display: block;
    font-family: 'DM Sans', sans-serif;
    font-size: 0.65rem;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    color: var(--brown-light);
    font-weight: 300;
    margin-top: -2px;
  }

  .nav-links {
    display: flex;
    gap: 2.5rem;
    list-style: none;
  }

  .nav-links a {
    color: var(--cream);
    text-decoration: none;
    font-size: 0.85rem;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    font-weight: 400;
    transition: color 0.3s;
    opacity: 0.85;
  }

  .nav-links a:hover { color: var(--gold); opacity: 1; }

  .nav-cta {
    background: transparent;
    border: 1px solid var(--gold);
    color: var(--gold) !important;
    padding: 0.5rem 1.5rem;
    border-radius: 2px;
    transition: background 0.3s, color 0.3s !important;
  }

  .nav-cta:hover {
    background: var(--gold) !important;
    color: var(--espresso) !important;
    opacity: 1 !important;
  }

  /* ---- HERO ---- */
  .hero {
    min-height: 100vh;
    display: grid;
    grid-template-columns: 1fr 1fr;
    align-items: center;
    padding: 8rem 4rem 4rem;
    position: relative;
    overflow: hidden;
  }

  .hero::after {
    content: '';
    position: absolute;
    right: -10%;
    top: 50%;
    transform: translateY(-50%);
    width: 60vw;
    height: 60vw;
    border-radius: 50%;
    background: radial-gradient(circle, rgba(200,147,58,0.08) 0%, transparent 70%);
    pointer-events: none;
  }

  .hero-left { position: relative; z-index: 1; }

  .hero-badge {
    display: inline-block;
    font-size: 0.7rem;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    color: var(--gold);
    border: 1px solid rgba(200,147,58,0.4);
    padding: 0.4rem 1rem;
    border-radius: 1px;
    margin-bottom: 2rem;
  }

  .hero h1 {
    font-family: 'Playfair Display', serif;
    font-size: clamp(3rem, 5vw, 5.5rem);
    line-height: 1.05;
    color: var(--cream);
    margin-bottom: 1.5rem;
  }

  .hero h1 em {
    font-style: italic;
    color: var(--gold);
  }

  .hero-desc {
    font-family: 'Crimson Pro', serif;
    font-size: 1.25rem;
    line-height: 1.7;
    color: rgba(245, 237, 216, 0.7);
    max-width: 400px;
    margin-bottom: 3rem;
    font-weight: 300;
  }

  .hero-btns {
    display: flex;
    gap: 1rem;
    align-items: center;
  }

  .btn-primary {
    background: var(--gold);
    color: var(--espresso);
    border: none;
    padding: 0.9rem 2.5rem;
    font-family: 'DM Sans', sans-serif;
    font-size: 0.85rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    font-weight: 500;
    cursor: pointer;
    border-radius: 2px;
    text-decoration: none;
    transition: background 0.3s, transform 0.2s;
    display: inline-block;
  }

  .btn-primary:hover {
    background: var(--brown-light);
    transform: translateY(-2px);
  }

  .btn-ghost {
    color: var(--cream);
    text-decoration: none;
    font-size: 0.85rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    opacity: 0.7;
    display: flex;
    align-items: center;
    gap: 0.5rem;
    transition: opacity 0.3s;
  }

  .btn-ghost:hover { opacity: 1; }

  .btn-ghost::before {
    content: '';
    display: inline-block;
    width: 32px;
    height: 1px;
    background: currentColor;
  }

  .hero-right {
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
  }

  .hero-img-container {
    position: relative;
    width: 480px;
    height: 580px;
  }

  .hero-img-main {
    width: 100%;
    height: 100%;
    object-fit: cover;
    border-radius: 4px;
    filter: sepia(15%) brightness(0.9);
  }

  .hero-img-frame {
    position: absolute;
    inset: -16px;
    border: 1px solid rgba(200, 147, 58, 0.3);
    border-radius: 4px;
    pointer-events: none;
  }

  .hero-stat {
    position: absolute;
    background: rgba(28, 13, 5, 0.95);
    border: 1px solid rgba(200,147,58,0.3);
    padding: 1rem 1.5rem;
    border-radius: 2px;
    backdrop-filter: blur(8px);
  }

  .hero-stat-br {
    bottom: 2rem;
    right: -2.5rem;
  }

  .hero-stat-tl {
    top: 2rem;
    left: -2.5rem;
  }

  .hero-stat .num {
    font-family: 'Playfair Display', serif;
    font-size: 2rem;
    color: var(--gold);
    line-height: 1;
  }

  .hero-stat .label {
    font-size: 0.7rem;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--brown-light);
    margin-top: 2px;
  }

  /* ---- SECTION COMMON ---- */
  section { padding: 6rem 4rem; }

  .section-label {
    font-size: 0.7rem;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 0.75rem;
  }

  .section-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2rem, 3.5vw, 3rem);
    line-height: 1.2;
    color: var(--cream);
    margin-bottom: 1rem;
  }

  .section-sub {
    font-family: 'Crimson Pro', serif;
    font-size: 1.15rem;
    color: rgba(245,237,216,0.6);
    max-width: 500px;
    line-height: 1.7;
    font-weight: 300;
  }

  /* ---- ORIGIN BAND ---- */
  .origin-band {
    background: var(--brown-dark);
    border-top: 1px solid rgba(200,147,58,0.15);
    border-bottom: 1px solid rgba(200,147,58,0.15);
    padding: 3rem 4rem;
    display: flex;
    gap: 0;
    align-items: stretch;
    overflow-x: auto;
  }

  .origin-item {
    flex: 1;
    min-width: 180px;
    padding: 1.5rem 2rem;
    border-right: 1px solid rgba(200,147,58,0.15);
    display: flex;
    align-items: center;
    gap: 1.25rem;
  }

  .origin-item:last-child { border-right: none; }

  .origin-icon {
    font-size: 2rem;
    flex-shrink: 0;
  }

  .origin-item h4 {
    font-family: 'Playfair Display', serif;
    font-size: 1rem;
    color: var(--gold);
    margin-bottom: 0.2rem;
  }

  .origin-item p {
    font-size: 0.8rem;
    color: rgba(245,237,216,0.5);
    letter-spacing: 0.05em;
    line-height: 1.5;
  }

  /* ---- CATALOG ---- */
  .catalog { background: rgba(255,255,255,0.02); }

  .catalog-header {
    display: flex;
    align-items: flex-end;
    justify-content: space-between;
    margin-bottom: 3rem;
    flex-wrap: wrap;
    gap: 1.5rem;
  }

  .catalog-filters {
    display: flex;
    gap: 0.5rem;
    flex-wrap: wrap;
  }

  .filter-btn {
    background: transparent;
    border: 1px solid rgba(200,147,58,0.3);
    color: rgba(245,237,216,0.6);
    padding: 0.4rem 1.2rem;
    font-family: 'DM Sans', sans-serif;
    font-size: 0.78rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    cursor: pointer;
    border-radius: 1px;
    transition: all 0.25s;
  }

  .filter-btn:hover, .filter-btn.active {
    background: var(--gold);
    border-color: var(--gold);
    color: var(--espresso);
  }

  .catalog-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 1.5rem;
  }

  .product-card {
    background: var(--brown-dark);
    border: 1px solid rgba(200,147,58,0.12);
    border-radius: 3px;
    overflow: hidden;
    transition: transform 0.3s, border-color 0.3s;
    cursor: pointer;
  }

  .product-card:hover {
    transform: translateY(-6px);
    border-color: rgba(200,147,58,0.4);
  }

  .product-img-wrap {
    position: relative;
    height: 220px;
    overflow: hidden;
    background: #2A1508;
  }

  .product-img-wrap img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.5s;
    filter: sepia(10%) brightness(0.85);
  }

  .product-card:hover .product-img-wrap img {
    transform: scale(1.06);
  }

  .product-badge {
    position: absolute;
    top: 1rem;
    left: 1rem;
    background: var(--gold);
    color: var(--espresso);
    font-size: 0.65rem;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    padding: 0.25rem 0.75rem;
    border-radius: 1px;
    font-weight: 500;
  }

  /* Photo upload overlay */
  .photo-upload-overlay {
    position: absolute;
    inset: 0;
    background: rgba(28,13,5,0.75);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    opacity: 0;
    transition: opacity 0.3s;
    gap: 0.5rem;
  }

  .product-card:hover .photo-upload-overlay {
    opacity: 1;
  }

  .photo-upload-overlay label {
    background: var(--gold);
    color: var(--espresso);
    font-size: 0.75rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    padding: 0.5rem 1.25rem;
    border-radius: 2px;
    cursor: pointer;
    font-weight: 500;
    transition: background 0.2s;
  }

  .photo-upload-overlay label:hover { background: var(--brown-light); }

  .photo-upload-overlay input[type="file"] { display: none; }

  .photo-upload-overlay span {
    font-size: 0.7rem;
    color: rgba(245,237,216,0.6);
    letter-spacing: 0.05em;
  }

  .product-info {
    padding: 1.25rem 1.5rem;
  }

  .product-origin {
    font-size: 0.68rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 0.35rem;
  }

  .product-name {
    font-family: 'Playfair Display', serif;
    font-size: 1.2rem;
    color: var(--cream);
    margin-bottom: 0.4rem;
  }

  .product-desc {
    font-family: 'Crimson Pro', serif;
    font-size: 0.95rem;
    color: rgba(245,237,216,0.55);
    line-height: 1.5;
    font-weight: 300;
    margin-bottom: 1rem;
  }

  .product-footer {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .product-price {
    font-family: 'Playfair Display', serif;
    font-size: 1.3rem;
    color: var(--gold);
  }

  .product-add {
    background: transparent;
    border: 1px solid rgba(200,147,58,0.4);
    color: var(--gold);
    width: 34px;
    height: 34px;
    border-radius: 50%;
    font-size: 1.2rem;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 0.25s;
    font-weight: 300;
    line-height: 1;
  }

  .product-add:hover {
    background: var(--gold);
    color: var(--espresso);
    border-color: var(--gold);
  }

  /* ---- ABOUT ---- */
  .about {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 6rem;
    align-items: center;
  }

  .about-imgs {
    position: relative;
    height: 520px;
  }

  .about-img-1 {
    position: absolute;
    top: 0; left: 0;
    width: 70%;
    height: 75%;
    object-fit: cover;
    border-radius: 3px;
    filter: sepia(10%) brightness(0.85);
  }

  .about-img-2 {
    position: absolute;
    bottom: 0; right: 0;
    width: 55%;
    height: 55%;
    object-fit: cover;
    border-radius: 3px;
    border: 6px solid var(--espresso);
    filter: sepia(10%) brightness(0.85);
  }

  .about-accent {
    position: absolute;
    top: 50%;
    left: 60%;
    transform: translate(-50%, -50%);
    width: 80px;
    height: 80px;
    border-radius: 50%;
    background: var(--brown-dark);
    border: 1px solid rgba(200,147,58,0.4);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 2rem;
  }

  .about-text {}

  .about-text blockquote {
    font-family: 'Playfair Display', serif;
    font-style: italic;
    font-size: 1.4rem;
    color: var(--brown-light);
    border-left: 2px solid var(--gold);
    padding-left: 1.5rem;
    margin: 2rem 0;
    line-height: 1.6;
  }

  .about-text p {
    font-family: 'Crimson Pro', serif;
    font-size: 1.1rem;
    color: rgba(245,237,216,0.65);
    line-height: 1.8;
    font-weight: 300;
    margin-bottom: 1rem;
  }

  /* ---- TESTIMONIAL ---- */
  .testimonials {
    background: var(--brown-dark);
    border-top: 1px solid rgba(200,147,58,0.1);
  }

  .testi-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 1.5rem;
    margin-top: 3rem;
  }

  .testi-card {
    background: rgba(255,255,255,0.03);
    border: 1px solid rgba(200,147,58,0.12);
    padding: 2rem;
    border-radius: 3px;
  }

  .testi-stars {
    color: var(--gold);
    font-size: 0.9rem;
    letter-spacing: 0.1em;
    margin-bottom: 1rem;
  }

  .testi-quote {
    font-family: 'Crimson Pro', serif;
    font-size: 1.1rem;
    color: rgba(245,237,216,0.75);
    line-height: 1.7;
    font-weight: 300;
    margin-bottom: 1.5rem;
  }

  .testi-author {
    display: flex;
    align-items: center;
    gap: 0.75rem;
  }

  .testi-avatar {
    width: 38px;
    height: 38px;
    border-radius: 50%;
    background: var(--brown);
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Playfair Display', serif;
    font-size: 1rem;
    color: var(--gold);
    font-weight: 700;
    flex-shrink: 0;
  }

  .testi-name {
    font-size: 0.85rem;
    color: var(--cream);
    font-weight: 500;
  }

  .testi-loc {
    font-size: 0.72rem;
    color: rgba(245,237,216,0.4);
    letter-spacing: 0.08em;
  }

  /* ---- CTA ---- */
  .cta-section {
    text-align: center;
    padding: 8rem 4rem;
    position: relative;
    overflow: hidden;
  }

  .cta-section::before {
    content: '';
    position: absolute;
    inset: 0;
    background: radial-gradient(ellipse at center, rgba(200,147,58,0.06) 0%, transparent 70%);
    pointer-events: none;
  }

  .cta-section h2 {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2.5rem, 5vw, 4.5rem);
    line-height: 1.1;
    color: var(--cream);
    margin-bottom: 1.5rem;
  }

  .cta-section h2 em {
    font-style: italic;
    color: var(--gold);
  }

  .cta-section p {
    font-family: 'Crimson Pro', serif;
    font-size: 1.2rem;
    color: rgba(245,237,216,0.6);
    margin-bottom: 3rem;
    font-weight: 300;
  }

  .cta-info {
    display: flex;
    justify-content: center;
    gap: 3rem;
    margin-top: 4rem;
    flex-wrap: wrap;
  }

  .cta-info-item {
    text-align: center;
  }

  .cta-info-item .val {
    font-family: 'Playfair Display', serif;
    font-size: 1.5rem;
    color: var(--gold);
    display: block;
  }

  .cta-info-item .key {
    font-size: 0.72rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: rgba(245,237,216,0.4);
    margin-top: 0.25rem;
  }

  /* ---- FOOTER ---- */
  footer {
    background: #0C0602;
    border-top: 1px solid rgba(200,147,58,0.15);
    padding: 4rem;
    display: grid;
    grid-template-columns: 2fr 1fr 1fr 1fr;
    gap: 3rem;
  }

  .footer-brand .brand-name {
    font-family: 'Playfair Display', serif;
    font-size: 1.75rem;
    color: var(--gold);
    margin-bottom: 0.25rem;
  }

  .footer-brand .brand-sub {
    font-size: 0.68rem;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    color: var(--brown-light);
    margin-bottom: 1.25rem;
  }

  .footer-brand p {
    font-family: 'Crimson Pro', serif;
    font-size: 1rem;
    color: rgba(245,237,216,0.45);
    line-height: 1.7;
    font-weight: 300;
    max-width: 260px;
  }

  .footer-col h5 {
    font-size: 0.7rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 1.25rem;
  }

  .footer-col ul { list-style: none; }

  .footer-col li {
    margin-bottom: 0.6rem;
  }

  .footer-col a {
    color: rgba(245,237,216,0.5);
    text-decoration: none;
    font-size: 0.88rem;
    transition: color 0.25s;
  }

  .footer-col a:hover { color: var(--cream); }

  .footer-bottom {
    background: #0C0602;
    border-top: 1px solid rgba(200,147,58,0.08);
    padding: 1.5rem 4rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .footer-bottom p {
    font-size: 0.78rem;
    color: rgba(245,237,216,0.3);
    letter-spacing: 0.05em;
  }

  /* ---- MODAL ---- */
  .modal-overlay {
    display: none;
    position: fixed;
    inset: 0;
    background: rgba(12,6,2,0.85);
    z-index: 500;
    align-items: center;
    justify-content: center;
    backdrop-filter: blur(4px);
  }

  .modal-overlay.open { display: flex; }

  .modal {
    background: var(--brown-dark);
    border: 1px solid rgba(200,147,58,0.3);
    border-radius: 4px;
    max-width: 500px;
    width: 90%;
    padding: 2.5rem;
    position: relative;
    animation: modalIn 0.35s cubic-bezier(0.16, 1, 0.3, 1);
  }

  @keyframes modalIn {
    from { transform: scale(0.92) translateY(20px); opacity: 0; }
    to { transform: scale(1) translateY(0); opacity: 1; }
  }

  .modal-close {
    position: absolute;
    top: 1rem; right: 1rem;
    background: transparent;
    border: none;
    color: rgba(245,237,216,0.4);
    font-size: 1.5rem;
    cursor: pointer;
    line-height: 1;
    transition: color 0.2s;
  }

  .modal-close:hover { color: var(--cream); }

  .modal-img {
    width: 100%;
    height: 240px;
    object-fit: cover;
    border-radius: 2px;
    margin-bottom: 1.5rem;
    filter: sepia(10%);
  }

  .modal-origin {
    font-size: 0.68rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 0.5rem;
  }

  .modal-name {
    font-family: 'Playfair Display', serif;
    font-size: 1.75rem;
    color: var(--cream);
    margin-bottom: 0.75rem;
  }

  .modal-desc {
    font-family: 'Crimson Pro', serif;
    font-size: 1.05rem;
    color: rgba(245,237,216,0.6);
    line-height: 1.7;
    font-weight: 300;
    margin-bottom: 1.5rem;
  }

  .modal-footer {
    display: flex;
    align-items: center;
    justify-content: space-between;
    border-top: 1px solid rgba(200,147,58,0.15);
    padding-top: 1.25rem;
  }

  .modal-price {
    font-family: 'Playfair Display', serif;
    font-size: 1.6rem;
    color: var(--gold);
  }

  .modal-notes {
    display: flex;
    gap: 0.5rem;
    margin-bottom: 1.25rem;
    flex-wrap: wrap;
  }

  .note-tag {
    background: rgba(200,147,58,0.12);
    border: 1px solid rgba(200,147,58,0.2);
    color: var(--brown-light);
    font-size: 0.7rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    padding: 0.25rem 0.75rem;
    border-radius: 1px;
  }

  /* ---- TOAST ---- */
  .toast {
    position: fixed;
    bottom: 2rem;
    right: 2rem;
    background: var(--gold);
    color: var(--espresso);
    padding: 0.75rem 1.5rem;
    border-radius: 2px;
    font-size: 0.85rem;
    font-weight: 500;
    z-index: 1000;
    transform: translateY(100px);
    opacity: 0;
    transition: transform 0.4s cubic-bezier(0.16,1,0.3,1), opacity 0.4s;
    pointer-events: none;
  }

  .toast.show {
    transform: translateY(0);
    opacity: 1;
  }

  /* ---- ANIMATIONS ---- */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(30px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .hero-left > * { animation: fadeUp 0.8s cubic-bezier(0.16,1,0.3,1) both; }
  .hero-badge { animation-delay: 0.1s; }
  .hero h1 { animation-delay: 0.2s; }
  .hero-desc { animation-delay: 0.35s; }
  .hero-btns { animation-delay: 0.5s; }
  .hero-right { animation: fadeUp 1s cubic-bezier(0.16,1,0.3,1) 0.3s both; }

  /* ---- RESPONSIVE ---- */
  @media (max-width: 900px) {
    nav { padding: 1rem 1.5rem; }
    .nav-links { display: none; }
    .hero { grid-template-columns: 1fr; padding: 6rem 1.5rem 3rem; }
    .hero-right { display: none; }
    section { padding: 4rem 1.5rem; }
    .about { grid-template-columns: 1fr; }
    .about-imgs { height: 300px; display: none; }
    footer { grid-template-columns: 1fr 1fr; padding: 3rem 1.5rem; }
    .footer-bottom { flex-direction: column; gap: 0.5rem; padding: 1rem 1.5rem; text-align: center; }
    .origin-band { padding: 2rem 1.5rem; }
    .cta-section { padding: 5rem 1.5rem; }
    .catalog-header { flex-direction: column; align-items: flex-start; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <a href="#" class="nav-logo">
    Nusantara Coffee
    <span>Est. 2012 · Specialty Roaster</span>
  </a>
  <ul class="nav-links">
    <li><a href="#catalog">Menu</a></li>
    <li><a href="#about">Tentang Kami</a></li>
    <li><a href="#testi">Ulasan</a></li>
    <li><a href="#contact" class="nav-cta">Kunjungi</a></li>
  </ul>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-left">
    <div class="hero-badge">Specialty Coffee · From Farm to Cup</div>
    <h1>Cita Rasa<br><em>Nusantara</em><br>dalam Setiap<br>Tegukan</h1>
    <p class="hero-desc">Kami menghadirkan biji kopi terbaik dari seluruh kepulauan Indonesia—dari ketinggian Gayo hingga lembah Toraja—disangrai dengan hati-hati untuk menghormati tanah asalnya.</p>
    <div class="hero-btns">
      <a href="#catalog" class="btn-primary">Jelajahi Menu</a>
      <a href="#about" class="btn-ghost">Cerita Kami</a>
    </div>
  </div>
  <div class="hero-right">
    <div class="hero-img-container">
      <img class="hero-img-main"
        src="https://images.unsplash.com/photo-1495474472287-4d71bcdd2085?w=900&q=80"
        alt="Coffee cup at Nusantara Coffee">
      <div class="hero-img-frame"></div>
      <div class="hero-stat hero-stat-tl">
        <div class="num">12+</div>
        <div class="label">Varietas Kopi</div>
      </div>
      <div class="hero-stat hero-stat-br">
        <div class="num">100%</div>
        <div class="label">Single Origin</div>
      </div>
    </div>
  </div>
</section>

<!-- ORIGIN BAND -->
<div class="origin-band">
  <div class="origin-item">
    <div class="origin-icon">🌋</div>
    <div>
      <h4>Gayo, Aceh</h4>
      <p>Ketinggian 1,400m<br>Earthy & Fruity</p>
    </div>
  </div>
  <div class="origin-item">
    <div class="origin-icon">🏔️</div>
    <div>
      <h4>Toraja, Sulawesi</h4>
      <p>Ketinggian 1,800m<br>Spicy & Complex</p>
    </div>
  </div>
  <div class="origin-item">
    <div class="origin-icon">🌿</div>
    <div>
      <h4>Kintamani, Bali</h4>
      <p>Ketinggian 1,500m<br>Citrusy & Bright</p>
    </div>
  </div>
  <div class="origin-item">
    <div class="origin-icon">☕</div>
    <div>
      <h4>Flores, NTT</h4>
      <p>Ketinggian 1,200m<br>Chocolatey & Sweet</p>
    </div>
  </div>
  <div class="origin-item">
    <div class="origin-icon">🌺</div>
    <div>
      <h4>Java, Jawa Barat</h4>
      <p>Ketinggian 900m<br>Smooth & Clean</p>
    </div>
  </div>
</div>

<!-- CATALOG -->
<section class="catalog" id="catalog">
  <div class="catalog-header">
    <div>
      <div class="section-label">Menu Kami</div>
      <h2 class="section-title">Temukan Pilihan<br>Kopi Favoritmu</h2>
    </div>
    <div class="catalog-filters">
      <button class="filter-btn active" onclick="filterProducts('all', this)">Semua</button>
      <button class="filter-btn" onclick="filterProducts('espresso', this)">Espresso</button>
      <button class="filter-btn" onclick="filterProducts('manual', this)">Manual Brew</button>
      <button class="filter-btn" onclick="filterProducts('cold', this)">Cold Brew</button>
      <button class="filter-btn" onclick="filterProducts('food', this)">Makanan</button>
    </div>
  </div>

  <div class="catalog-grid" id="catalogGrid"></div>
</section>

<!-- ABOUT -->
<section id="about">
  <div class="about">
    <div class="about-imgs">
      <img class="about-img-1"
        src="https://images.unsplash.com/photo-1447933601403-0c6688de566e?w=700&q=80"
        alt="Coffee roasting">
      <img class="about-img-2"
        src="https://images.unsplash.com/photo-1509042239860-f550ce710b93?w=700&q=80"
        alt="Barista preparing coffee">
      <div class="about-accent">☕</div>
    </div>
    <div class="about-text">
      <div class="section-label">Tentang Kami</div>
      <h2 class="section-title">Lebih dari Sekadar Secangkir Kopi</h2>
      <blockquote>"Setiap biji adalah cerita. Setiap cangkir adalah perjalanan."</blockquote>
      <p>Nusantara Coffee lahir dari kecintaan mendalam terhadap kekayaan kopi Indonesia. Sejak 2012, Alfa Adhy Pratama CEO sekaligus Founder Nusantara Coffe bermitra langsung dengan para petani kopi di berbagai wilayah kepulauan nusantara, memastikan kualitas terbaik dari hulu ke hilir.</p>
      <p>Kami percaya bahwa kopi yang baik bukan hanya soal rasa, tetapi juga tentang keberlanjutan dan kesejahteraan komunitas petani yang telah bekerja keras membesarkan setiap pohon kopi dengan penuh kasih.</p>
    </div>
  </div>
</section>

<!-- TESTIMONIALS -->
<section class="testimonials" id="testi">
  <div class="section-label">Cerita Pelanggan</div>
  <h2 class="section-title">Yang Mereka Katakan</h2>
  <div class="testi-grid">
    <div class="testi-card">
      <div class="testi-stars">★★★★★</div>
      <p class="testi-quote">"Kopi Gayo single origin-nya benar-benar membuka mata saya. Kompleks, fruity, dan ada sentuhan floral yang tidak pernah saya temukan di tempat lain."</p>
      <div class="testi-author">
        <div class="testi-avatar">AR</div>
        <div>
          <div class="testi-name">Andrian Ramadhan</div>
          <div class="testi-loc">Jakarta Selatan</div>
        </div>
      </div>
    </div>
    <div class="testi-card">
      <div class="testi-stars">★★★★★</div>
      <p class="testi-quote">"Suasananya hangat dan nyaman. Barista-nya sangat berpengetahuan dan dengan sabar menjelaskan profil rasa setiap kopi. Tempat favorit saya sekarang!"</p>
      <div class="testi-author">
        <div class="testi-avatar">SW</div>
        <div>
          <div class="testi-name">Sari Wulandari</div>
          <div class="testi-loc">Bandung</div>
        </div>
      </div>
    </div>
    <div class="testi-card">
      <div class="testi-stars">★★★★★</div>
      <p class="testi-quote">"Cold brew Flores mereka adalah yang terbaik yang pernah saya coba. Cokelat, creamy, tanpa rasa asam yang mengganggu. Wajib dicoba!"</p>
      <div class="testi-author">
        <div class="testi-avatar">DK</div>
        <div>
          <div class="testi-name">Dimas Kurniawan</div>
          <div class="testi-loc">Yogyakarta</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- CTA -->
<section class="cta-section" id="contact">
  <div class="section-label">Kunjungi Kami</div>
  <h2>Mulai Perjalanan<br>Kopi <em>Anda</em> Hari Ini</h2>
  <p>Nikmati pengalaman kopi yang tak terlupakan bersama kami</p>
  <a href="#catalog" class="btn-primary">Pesan Sekarang</a>
  <div class="cta-info">
    <div class="cta-info-item">
      <span class="val">Jl. Angkrek situ</span>
      <span class="key">Sumedang</span>
    </div>
    <div class="cta-info-item">
      <span class="val">07.00 – 22.00</span>
      <span class="key">Setiap Hari</span>
    </div>
    <div class="cta-info-item">
      <span class="val">+62 857-9845-3836</span>
      <span class="key">Reservasi & Info</span>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-brand">
    <div class="brand-name">Nusantara Coffee</div>
    <div class="brand-sub">Specialty Roaster · Est. 2012</div>
    <p>Menghadirkan cita rasa autentik kopi Indonesia dengan penuh dedikasi dan rasa hormat terhadap bumi dan petaninya.</p>
  </div>
  <div class="footer-col">
    <h5>Menu</h5>
    <ul>
      <li><a href="#">Espresso Bar</a></li>
      <li><a href="#">Manual Brew</a></li>
      <li><a href="#">Cold Brew</a></li>
      <li><a href="#">Pastry & Food</a></li>
      <li><a href="#">Merchandise</a></li>
    </ul>
  </div>
  <div class="footer-col">
    <h5>Layanan</h5>
    <ul>
      <li><a href="#">Coffee Class</a></li>
      <li><a href="#">Roastery Tour</a></li>
      <li><a href="#">Wholesale</a></li>
      <li><a href="#">Subscription</a></li>
    </ul>
  </div>
  <div class="footer-col">
    <h5>Sosial</h5>
    <ul>
      <li><a href="#">Instagram</a></li>
      <li><a href="#">TikTok</a></li>
      <li><a href="#">Facebook</a></li>
      <li><a href="#">WhatsApp</a></li>
    </ul>
  </div>
</footer>
<div class="footer-bottom">
  <p>© 2025 Nusantara Coffee. All rights reserved.</p>
  <p>Crafted with ☕ in Indonesia</p>
</div>

<!-- MODAL -->
<div class="modal-overlay" id="productModal" onclick="closeModal(event)">
  <div class="modal">
    <button class="modal-close" onclick="document.getElementById('productModal').classList.remove('open')">×</button>
    <img class="modal-img" id="modalImg" src="" alt="">
    <div class="modal-origin" id="modalOrigin"></div>
    <div class="modal-name" id="modalName"></div>
    <div class="modal-notes" id="modalNotes"></div>
    <div class="modal-desc" id="modalDesc"></div>
    <div class="modal-footer">
      <div class="modal-price" id="modalPrice"></div>
      <button class="btn-primary" onclick="addToCart(); document.getElementById('productModal').classList.remove('open')">Tambah ke Pesanan</button>
    </div>
  </div>
</div>

<!-- TOAST -->
<div class="toast" id="toast">✓ Ditambahkan ke pesanan!</div>

<script>
const products = [
  {
    id:1, category:'espresso', badge:'Bestseller',
    origin:'Gayo, Aceh', name:'Gayo Single Origin Espresso',
    desc:'Espresso intens dari biji Arabika Gayo pilihan. Earthy, fruity dengan body tebal dan aftertaste yang panjang.',
    notes:['Fruity','Earthy','Full Body'],
    price:'Rp 42.000',
    img:'https://images.unsplash.com/photo-1510591509098-f4fdc6d0ff04?w=600&q=80'
  },
  {
    id:2, category:'espresso', badge:null,
    origin:'Java, Jawa Barat', name:'Cappuccino Jawa',
    desc:'Espresso lembut dari biji Java dengan busa susu segar lokal. Creamy, hazel, dan sangat menyenangkan.',
    notes:['Smooth','Chocolatey','Creamy'],
    price:'Rp 38.000',
    img:'https://images.unsplash.com/photo-1534778101976-62847782c213?w=600&q=80'
  },
  {
    id:3, category:'manual', badge:'Rekomendasi',
    origin:'Kintamani, Bali', name:'Kintamani Pour Over',
    desc:'V60 single cup dari biji Arabika Kintamani. Cerah, citrusy dengan sentuhan floral yang segar dan bersih.',
    notes:['Citrusy','Floral','Light Body'],
    price:'Rp 48.000',
    img:'https://images.unsplash.com/photo-1495474472287-4d71bcdd2085?w=600&q=80'
  },
  {
    id:4, category:'manual', badge:null,
    origin:'Flores, NTT', name:'Flores Syphon',
    desc:'Diseduh dengan syphon untuk menghasilkan cita rasa terbersih. Manis, cokelat, dan penuh nuansa.',
    notes:['Chocolate','Sweet','Complex'],
    price:'Rp 55.000',
    img:'https://images.unsplash.com/photo-1442512595331-e89e73853f31?w=600&q=80'
  },
  {
    id:5, category:'cold', badge:'New',
    origin:'Toraja, Sulawesi', name:'Toraja Cold Brew',
    desc:'Cold brew 20 jam dari biji Toraja Arabika. Spicy, complex, dengan rasa rempah yang khas dan menghangatkan.',
    notes:['Spicy','Complex','Smooth'],
    price:'Rp 45.000',
    img:'https://images.unsplash.com/photo-1461023058943-07fcbe16d735?w=600&q=80'
  },
  {
    id:6, category:'cold', badge:null,
    origin:'Flores, NTT', name:'Flores Nitro Cold Brew',
    desc:'Cold brew nitrogen infused dari biji Flores. Creamy, smooth tanpa tambahan gula. Menyegarkan dan berkarakter.',
    notes:['Nitro','Ultra Smooth','Chocolatey'],
    price:'Rp 52.000',
    img:'https://images.unsplash.com/photo-1558618666-fcd25c85cd64?w=600&q=80'
  },
  {
    id:7, category:'food', badge:null,
    origin:'Dapur Kami', name:'Croissant Butter Klasik',
    desc:'Croissant lapis demi lapis dengan butter berkualitas tinggi. Renyah di luar, lembut di dalam. Pasangan sempurna untuk kopi.',
    notes:['Buttery','Flaky','Fresh'],
    price:'Rp 28.000',
    img:'https://images.unsplash.com/photo-1555507036-ab1f4038808a?w=600&q=80'
  },
  {
    id:8, category:'food', badge:'Favorit',
    origin:'Dapur Kami', name:'Tiramisu Nusantara',
    desc:'Tiramisu klasik dengan sentuhan kopi Gayo dan mascarpone impor. Mewah, creamy, dan tidak terlalu manis.',
    notes:['Creamy','Coffee-infused','Indulgent'],
    price:'Rp 45.000',
    img:'https://images.unsplash.com/photo-1571877227200-a0d98ea607e9?w=600&q=80'
  }
];

// Per-card custom images stored by id
const customImages = {};

function renderProducts(filter) {
  const grid = document.getElementById('catalogGrid');
  const filtered = filter === 'all' ? products : products.filter(p => p.category === filter);
  grid.innerHTML = filtered.map(p => {
    const imgSrc = customImages[p.id] || p.img;
    return `
    <div class="product-card" onclick="openModal(${p.id})">
      <div class="product-img-wrap">
        <img id="cardImg${p.id}" src="${imgSrc}" alt="${p.name}">
        ${p.badge ? `<div class="product-badge">${p.badge}</div>` : ''}
        <div class="photo-upload-overlay" onclick="event.stopPropagation()">
          <label for="fileInput${p.id}">🖼 Ganti Foto</label>
          <input type="file" id="fileInput${p.id}" accept="image/*" onchange="changePhoto(event, ${p.id})">
          <span>Format: JPG, PNG, WebP</span>
        </div>
      </div>
      <div class="product-info">
        <div class="product-origin">${p.origin}</div>
        <div class="product-name">${p.name}</div>
        <div class="product-desc">${p.desc}</div>
        <div class="product-footer">
          <div class="product-price">${p.price}</div>
          <button class="product-add" onclick="event.stopPropagation(); showToast()">+</button>
        </div>
      </div>
    </div>`;
  }).join('');
}

function changePhoto(event, id) {
  const file = event.target.files[0];
  if (!file) return;
  const reader = new FileReader();
  reader.onload = e => {
    customImages[id] = e.target.result;
    const img = document.getElementById('cardImg' + id);
    if (img) img.src = e.target.result;
    showToast('✓ Foto berhasil diperbarui!');
  };
  reader.readAsDataURL(file);
}

function filterProducts(cat, btn) {
  document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
  btn.classList.add('active');
  renderProducts(cat);
}

function openModal(id) {
  const p = products.find(x => x.id === id);
  if (!p) return;
  document.getElementById('modalImg').src = customImages[p.id] || p.img;
  document.getElementById('modalOrigin').textContent = p.origin;
  document.getElementById('modalName').textContent = p.name;
  document.getElementById('modalDesc').textContent = p.desc;
  document.getElementById('modalPrice').textContent = p.price;
  document.getElementById('modalNotes').innerHTML = p.notes.map(n =>
    `<span class="note-tag">${n}</span>`).join('');
  document.getElementById('productModal').classList.add('open');
}

function closeModal(e) {
  if (e.target.id === 'productModal') {
    document.getElementById('productModal').classList.remove('open');
  }
}

function addToCart() { showToast(); }

function showToast(msg) {
  const t = document.getElementById('toast');
  t.textContent = msg || '✓ Ditambahkan ke pesanan!';
  t.classList.add('show');
  setTimeout(() => t.classList.remove('show'), 2800);
}

renderProducts('all');
</script>
</body>
</html>
