<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Daisy's Jewelry — Handcrafted Fine Jewellery</title>
  <link
    href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;1,300;1,400&family=Jost:wght@300;400;500&display=swap"
    rel="stylesheet">
  <style>
    *,
    *::before,
    *::after {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    :root {
      --cream: #faf8f4;
      --warm-white: #f5f0e8;
      --blush: #e8d5c4;
      --rose: #c9967a;
      --deep-rose: #9e6b52;
      --gold: #c8a96e;
      --dark-gold: #9c7d44;
      --charcoal: #2a2520;
      --mid: #7a6e65;
      --light-mid: #b5aba3;
      --green: #25D366;
      --serif: 'Cormorant Garamond', Georgia, serif;
      --sans: 'Jost', sans-serif;
    }

    html {
      scroll-behavior: smooth;
    }

    body {
      font-family: var(--sans);
      background: var(--cream);
      color: var(--charcoal);
      font-weight: 300;
      line-height: 1.6;
    }

    /* PROMO BAR */
    .promo-bar {
      background: var(--charcoal);
      color: var(--blush);
      text-align: center;
      font-size: 12px;
      letter-spacing: 0.15em;
      padding: 10px 20px;
      text-transform: uppercase;
    }

    .promo-bar span {
      color: var(--gold);
    }

    /* HEADER */
    header {
      background: var(--cream);
      border-bottom: 1px solid var(--blush);
      position: sticky;
      top: 0;
      z-index: 200;
    }

    .header-inner {
      max-width: 1200px;
      margin: 0 auto;
      padding: 0 40px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      height: 72px;
    }

    .logo {
      font-family: var(--serif);
      font-size: 26px;
      font-weight: 300;
      letter-spacing: 0.08em;
      color: var(--charcoal);
      text-decoration: none;
    }

    .logo em {
      color: var(--gold);
      font-style: italic;
    }

    .header-icons {
      display: flex;
      gap: 20px;
      align-items: center;
    }

    .icon-btn {
      background: none;
      border: none;
      cursor: pointer;
      color: var(--charcoal);
      font-size: 13px;
      font-family: var(--sans);
      font-weight: 400;
      display: flex;
      align-items: center;
      gap: 6px;
      transition: color 0.2s;
      position: relative;
    }

    .icon-btn:hover {
      color: var(--gold);
    }

    .icon-btn svg {
      width: 22px;
      height: 22px;
      stroke: currentColor;
      fill: none;
      stroke-width: 1.4;
    }

    .cart-count {
      background: var(--rose);
      color: white;
      border-radius: 50%;
      width: 18px;
      height: 18px;
      font-size: 10px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-weight: 500;
      position: absolute;
      top: -6px;
      right: -8px;
    }

    /* NAV */
    nav {
      background: var(--warm-white);
      border-bottom: 1px solid var(--blush);
    }

    .nav-inner {
      max-width: 1200px;
      margin: 0 auto;
      padding: 0 40px;
      display: flex;
      align-items: center;
      overflow-x: auto;
      scrollbar-width: none;
    }

    nav a {
      font-size: 11.5px;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      text-decoration: none;
      color: var(--mid);
      padding: 14px 16px;
      white-space: nowrap;
      transition: color 0.2s;
      font-weight: 400;
      position: relative;
    }

    nav a::after {
      content: '';
      position: absolute;
      bottom: 0;
      left: 16px;
      right: 16px;
      height: 2px;
      background: var(--gold);
      transform: scaleX(0);
      transition: transform 0.2s;
    }

    nav a:hover {
      color: var(--charcoal);
    }

    nav a:hover::after,
    nav a.active::after {
      transform: scaleX(1);
    }

    nav a.active {
      color: var(--charcoal);
    }

    /* CART SIDEBAR */
    .cart-overlay {
      position: fixed;
      inset: 0;
      background: rgba(0, 0, 0, 0.4);
      z-index: 300;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.3s;
    }

    .cart-overlay.open {
      opacity: 1;
      pointer-events: all;
    }

    .cart-sidebar {
      position: fixed;
      top: 0;
      right: -420px;
      width: 420px;
      max-width: 100vw;
      height: 100vh;
      background: var(--cream);
      z-index: 301;
      transition: right 0.35s ease;
      display: flex;
      flex-direction: column;
    }

    .cart-sidebar.open {
      right: 0;
    }

    .cart-header {
      padding: 24px 28px;
      border-bottom: 1px solid var(--blush);
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .cart-title {
      font-family: var(--serif);
      font-size: 24px;
      font-weight: 300;
    }

    .cart-close {
      background: none;
      border: none;
      font-size: 24px;
      cursor: pointer;
      color: var(--mid);
      line-height: 1;
    }

    .cart-close:hover {
      color: var(--charcoal);
    }

    .cart-items {
      flex: 1;
      overflow-y: auto;
      padding: 20px 28px;
    }

    .cart-empty {
      text-align: center;
      padding: 60px 20px;
      color: var(--mid);
    }

    .cart-empty svg {
      width: 48px;
      height: 48px;
      stroke: var(--light-mid);
      fill: none;
      stroke-width: 1.2;
      margin-bottom: 16px;
      display: block;
      margin-left: auto;
      margin-right: auto;
    }

    .cart-empty p {
      font-family: var(--serif);
      font-size: 18px;
      color: var(--light-mid);
    }

    .cart-item {
      display: flex;
      gap: 14px;
      padding: 16px 0;
      border-bottom: 1px solid var(--blush);
      align-items: center;
    }

    .cart-item-img {
      width: 72px;
      height: 72px;
      background: var(--warm-white);
      border: 1px solid var(--blush);
      flex-shrink: 0;
      display: flex;
      align-items: center;
      justify-content: center;
      overflow: hidden;
    }

    .cart-item-img img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .cart-item-info {
      flex: 1;
    }

    .cart-item-name {
      font-family: var(--serif);
      font-size: 16px;
      margin-bottom: 2px;
    }

    .cart-item-material {
      font-size: 11px;
      color: var(--light-mid);
      text-transform: uppercase;
      letter-spacing: 0.08em;
      margin-bottom: 6px;
    }

    .cart-item-price {
      font-size: 14px;
      font-weight: 400;
      color: var(--deep-rose);
    }

    .cart-item-remove {
      background: none;
      border: none;
      color: var(--light-mid);
      font-size: 20px;
      cursor: pointer;
      padding: 4px;
      line-height: 1;
    }

    .cart-item-remove:hover {
      color: var(--rose);
    }

    .cart-qty {
      display: flex;
      align-items: center;
      gap: 8px;
      margin-top: 6px;
    }

    .qty-btn {
      background: var(--warm-white);
      border: 1px solid var(--blush);
      width: 26px;
      height: 26px;
      font-size: 16px;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      line-height: 1;
      color: var(--charcoal);
    }

    .qty-btn:hover {
      background: var(--blush);
    }

    .qty-val {
      font-size: 14px;
      min-width: 20px;
      text-align: center;
    }

    .cart-footer {
      padding: 20px 28px 28px;
      border-top: 1px solid var(--blush);
    }

    .cart-total {
      display: flex;
      justify-content: space-between;
      font-family: var(--serif);
      font-size: 20px;
      margin-bottom: 20px;
    }

    .cart-total span:last-child {
      color: var(--deep-rose);
    }

    .whatsapp-order-btn {
      width: 100%;
      padding: 16px;
      background: var(--green);
      color: white;
      border: none;
      font-family: var(--sans);
      font-size: 13px;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
      transition: background 0.2s;
      font-weight: 400;
    }

    .whatsapp-order-btn:hover {
      background: #1da851;
    }

    .whatsapp-order-btn svg {
      width: 22px;
      height: 22px;
      fill: white;
      flex-shrink: 0;
    }

    .cart-contact {
      text-align: center;
      margin-top: 14px;
      font-size: 12px;
      color: var(--mid);
    }

    .cart-contact a {
      color: var(--deep-rose);
      text-decoration: none;
    }

    .cart-contact a:hover {
      text-decoration: underline;
    }

    /* HERO */
    .hero {
      min-height: 80vh;
      display: grid;
      grid-template-columns: 1fr 1fr;
      overflow: hidden;
    }

    .hero-left {
      background: linear-gradient(160deg, #e8ddd0 0%, #d4c4b0 100%);
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 80px;
      position: relative;
      overflow: hidden;
    }

    .hero-left::before {
      content: '';
      position: absolute;
      width: 400px;
      height: 400px;
      border-radius: 50%;
      border: 1px solid rgba(200, 169, 110, 0.3);
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
    }

    .hero-left::after {
      content: '';
      position: absolute;
      width: 600px;
      height: 600px;
      border-radius: 50%;
      border: 1px solid rgba(200, 169, 110, 0.15);
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
    }

    .hero-img-wrap {
      width: 300px;
      height: 300px;
      border-radius: 50%;
      overflow: hidden;
      border: 4px solid rgba(255, 255, 255, 0.5);
      position: relative;
      z-index: 1;
      display: flex;
      align-items: center;
      justify-content: center;
      background: rgba(255, 255, 255, 0.25);
    }

    .hero-img-wrap img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .hero-img-wrap .placeholder-svg {
      width: 120px;
      height: 120px;
      opacity: 0.6;
    }

    .hero-right {
      display: flex;
      flex-direction: column;
      justify-content: center;
      padding: 80px;
      background: var(--cream);
    }

    .hero-tag {
      font-size: 11px;
      letter-spacing: 0.25em;
      text-transform: uppercase;
      color: var(--gold);
      margin-bottom: 24px;
      font-weight: 400;
    }

    .hero-title {
      font-family: var(--serif);
      font-size: clamp(40px, 5vw, 70px);
      font-weight: 300;
      line-height: 1.1;
      color: var(--charcoal);
      margin-bottom: 24px;
    }

    .hero-title em {
      font-style: italic;
      color: var(--deep-rose);
      display: block;
    }

    .hero-sub {
      font-size: 15px;
      color: var(--mid);
      max-width: 360px;
      margin-bottom: 40px;
      line-height: 1.8;
    }

    .btn-primary {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      background: var(--charcoal);
      color: var(--cream);
      padding: 14px 36px;
      font-family: var(--sans);
      font-size: 12px;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      text-decoration: none;
      border: none;
      cursor: pointer;
      transition: background 0.3s;
      font-weight: 400;
    }

    .btn-primary:hover {
      background: var(--gold);
    }

    .btn-whatsapp {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      background: var(--green);
      color: white;
      padding: 14px 32px;
      font-family: var(--sans);
      font-size: 12px;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      text-decoration: none;
      border: none;
      cursor: pointer;
      transition: background 0.3s;
      font-weight: 400;
    }

    .btn-whatsapp:hover {
      background: #1da851;
    }

    .btn-whatsapp svg {
      width: 18px;
      height: 18px;
      fill: white;
    }

    .btn-group {
      display: flex;
      gap: 14px;
      flex-wrap: wrap;
    }

    /* MARQUEE */
    .marquee-wrap {
      background: var(--gold);
      overflow: hidden;
      padding: 12px 0;
    }

    .marquee {
      display: flex;
      animation: marquee 25s linear infinite;
      width: max-content;
    }

    .marquee span {
      font-size: 11px;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: white;
      padding: 0 32px;
      opacity: 0.9;
    }

    .marquee span::before {
      content: '✦  ';
      opacity: 0.7;
    }

    @keyframes marquee {
      0% {
        transform: translateX(0);
      }

      100% {
        transform: translateX(-50%);
      }
    }

    /* SECTIONS */
    .section {
      padding: 80px 40px;
      max-width: 1200px;
      margin: 0 auto;
    }

    .section-header {
      text-align: center;
      margin-bottom: 56px;
    }

    .section-tag {
      font-size: 11px;
      letter-spacing: 0.25em;
      text-transform: uppercase;
      color: var(--gold);
      display: block;
      margin-bottom: 12px;
    }

    .section-title {
      font-family: var(--serif);
      font-size: clamp(32px, 3.5vw, 52px);
      font-weight: 300;
      color: var(--charcoal);
      line-height: 1.15;
    }

    .section-title em {
      font-style: italic;
      color: var(--deep-rose);
    }

    /* CATEGORIES */
    .categories-grid {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 20px;
    }

    .cat-card {
      cursor: pointer;
    }

    .cat-img {
      aspect-ratio: 3/4;
      overflow: hidden;
    }

    .cat-img-inner {
      width: 100%;
      height: 100%;
      transition: transform 0.5s;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .cat-card:hover .cat-img-inner {
      transform: scale(1.05);
    }

    .cat-img-inner img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .cat-label {
      padding: 14px 0 0;
      text-align: center;
    }

    .cat-name {
      font-family: var(--serif);
      font-size: 20px;
      font-weight: 300;
      display: block;
      margin-bottom: 4px;
    }

    .cat-count {
      font-size: 11px;
      letter-spacing: 0.1em;
      color: var(--light-mid);
      text-transform: uppercase;
    }

    .cat-bg-1 {
      background: linear-gradient(145deg, #e8ddd4 0%, #d4bfb0 100%);
    }

    .cat-bg-2 {
      background: linear-gradient(145deg, #dde8e0 0%, #b5d4bc 100%);
    }

    .cat-bg-3 {
      background: linear-gradient(145deg, #e8e0d4 0%, #d4c4a0 100%);
    }

    .cat-bg-4 {
      background: linear-gradient(145deg, #e0d8e8 0%, #c4b5d4 100%);
    }

    .cat-icon {
      width: 70px;
      height: 70px;
      opacity: 0.45;
    }

    /* PRODUCTS */
    .products-grid {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 28px;
    }

    .product-card {
      cursor: pointer;
    }

    .product-img {
      aspect-ratio: 1;
      overflow: hidden;
      position: relative;
      margin-bottom: 14px;
      background: var(--warm-white);
    }

    .product-img-inner {
      width: 100%;
      height: 100%;
      display: flex;
      align-items: center;
      justify-content: center;
      transition: transform 0.5s;
    }

    .product-img-inner img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .product-card:hover .product-img-inner {
      transform: scale(1.04);
    }

    .product-badge {
      position: absolute;
      top: 12px;
      left: 12px;
      background: var(--charcoal);
      color: var(--cream);
      font-size: 10px;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      padding: 4px 10px;
    }

    .badge-sale {
      background: var(--rose);
    }

    .badge-new {
      background: var(--gold);
    }

    .product-actions {
      position: absolute;
      bottom: -50px;
      left: 0;
      right: 0;
      padding: 0 10px 10px;
      transition: bottom 0.3s;
    }

    .product-card:hover .product-actions {
      bottom: 0;
    }

    .add-to-cart-btn {
      width: 100%;
      background: var(--charcoal);
      color: var(--cream);
      border: none;
      padding: 11px;
      font-size: 11px;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      cursor: pointer;
      font-family: var(--sans);
      transition: background 0.2s;
    }

    .add-to-cart-btn:hover {
      background: var(--gold);
    }

    .product-name {
      font-family: var(--serif);
      font-size: 17px;
      font-weight: 300;
      margin-bottom: 3px;
    }

    .product-material {
      font-size: 11px;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      color: var(--light-mid);
      margin-bottom: 6px;
    }

    .product-price {
      font-size: 15px;
      font-weight: 400;
    }

    .product-price .original {
      color: var(--light-mid);
      text-decoration: line-through;
      margin-right: 6px;
      font-weight: 300;
    }

    .product-price .sale {
      color: var(--rose);
    }

    /* PROMISE STRIP */
    .promise-strip {
      background: var(--warm-white);
      border-top: 1px solid var(--blush);
      border-bottom: 1px solid var(--blush);
      padding: 48px 40px;
    }

    .promise-inner {
      max-width: 1100px;
      margin: 0 auto;
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 20px;
      text-align: center;
    }

    .promise-item {
      padding: 0 20px;
    }

    .promise-icon {
      width: 44px;
      height: 44px;
      margin: 0 auto 16px;
      color: var(--gold);
    }

    .promise-icon svg {
      width: 44px;
      height: 44px;
      stroke: currentColor;
      fill: none;
      stroke-width: 1.2;
    }

    .promise-label {
      font-family: var(--serif);
      font-size: 18px;
      font-weight: 400;
      margin-bottom: 6px;
    }

    .promise-desc {
      font-size: 13px;
      color: var(--mid);
      line-height: 1.6;
    }

    /* FULL BANNER */
    .full-banner {
      background: var(--charcoal);
      color: var(--cream);
      display: grid;
      grid-template-columns: 1fr 1fr;
      min-height: 460px;
      overflow: hidden;
    }

    .banner-content {
      padding: 80px;
      display: flex;
      flex-direction: column;
      justify-content: center;
    }

    .banner-tag {
      color: var(--gold);
      font-size: 11px;
      letter-spacing: 0.25em;
      text-transform: uppercase;
      margin-bottom: 20px;
    }

    .banner-title {
      font-family: var(--serif);
      font-size: clamp(36px, 4vw, 58px);
      font-weight: 300;
      line-height: 1.1;
      margin-bottom: 20px;
    }

    .banner-title em {
      font-style: italic;
      color: var(--blush);
    }

    .banner-body {
      font-size: 15px;
      color: var(--blush);
      line-height: 1.8;
      margin-bottom: 36px;
      max-width: 380px;
    }

    .banner-visual {
      background: linear-gradient(135deg, #3a3028 0%, #1e1a15 100%);
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .banner-circle {
      width: 300px;
      height: 300px;
      border-radius: 50%;
      background: rgba(200, 169, 110, 0.1);
      border: 1px solid rgba(200, 169, 110, 0.3);
      display: flex;
      align-items: center;
      justify-content: center;
    }

    /* CONTACT / ORDER SECTION */
    .order-section {
      background: #f0ebe3;
      padding: 70px 40px;
      text-align: center;
    }

    .order-inner {
      max-width: 600px;
      margin: 0 auto;
    }

    .order-title {
      font-family: var(--serif);
      font-size: clamp(28px, 3vw, 44px);
      font-weight: 300;
      margin-bottom: 14px;
    }

    .order-sub {
      font-size: 15px;
      color: var(--mid);
      margin-bottom: 36px;
      line-height: 1.8;
    }

    .order-buttons {
      display: flex;
      gap: 14px;
      justify-content: center;
      flex-wrap: wrap;
    }

    .contact-email-btn {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      background: transparent;
      color: var(--charcoal);
      padding: 13px 32px;
      font-family: var(--sans);
      font-size: 12px;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      text-decoration: none;
      border: 1px solid var(--charcoal);
      cursor: pointer;
      transition: all 0.3s;
      font-weight: 400;
    }

    .contact-email-btn:hover {
      background: var(--charcoal);
      color: var(--cream);
    }

    .contact-email-btn svg {
      width: 16px;
      height: 16px;
      stroke: currentColor;
      fill: none;
      stroke-width: 1.5;
    }

    /* TESTIMONIALS */
    .testimonials-bg {
      background: var(--cream);
      padding: 80px 40px;
    }

    .testimonials-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 28px;
      max-width: 1100px;
      margin: 0 auto;
    }

    .testimonial-card {
      background: var(--warm-white);
      border: 1px solid var(--blush);
      padding: 36px;
    }

    .stars {
      color: var(--gold);
      font-size: 14px;
      letter-spacing: 2px;
      margin-bottom: 16px;
    }

    .testimonial-text {
      font-family: var(--serif);
      font-size: 17px;
      font-weight: 300;
      font-style: italic;
      color: var(--charcoal);
      line-height: 1.7;
      margin-bottom: 20px;
    }

    .testimonial-author {
      font-size: 12px;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: var(--light-mid);
    }

    /* NEWSLETTER */
    .newsletter {
      background: var(--blush);
      padding: 70px 40px;
      text-align: center;
    }

    .newsletter-inner {
      max-width: 500px;
      margin: 0 auto;
    }

    .newsletter-title {
      font-family: var(--serif);
      font-size: clamp(26px, 3vw, 42px);
      font-weight: 300;
      margin-bottom: 10px;
    }

    .newsletter-sub {
      font-size: 14px;
      color: var(--deep-rose);
      margin-bottom: 28px;
    }

    .newsletter-form {
      display: flex;
      max-width: 420px;
      margin: 0 auto;
    }

    .newsletter-form input {
      flex: 1;
      padding: 13px 18px;
      border: 1px solid var(--deep-rose);
      border-right: none;
      background: white;
      font-family: var(--sans);
      font-size: 13px;
      outline: none;
    }

    .newsletter-form input::placeholder {
      color: var(--light-mid);
    }

    .newsletter-form button {
      padding: 13px 24px;
      background: var(--charcoal);
      color: var(--cream);
      border: 1px solid var(--charcoal);
      font-family: var(--sans);
      font-size: 11px;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      cursor: pointer;
      transition: background 0.2s;
    }

    .newsletter-form button:hover {
      background: var(--gold);
      border-color: var(--gold);
    }

    /* FOOTER */
    footer {
      background: var(--charcoal);
      color: var(--blush);
      padding: 60px 40px 28px;
    }

    .footer-grid {
      max-width: 1100px;
      margin: 0 auto 48px;
      display: grid;
      grid-template-columns: 2fr 1fr 1fr 1fr;
      gap: 48px;
    }

    .footer-brand .logo {
      color: var(--cream);
    }

    .footer-logo-em {
      color: var(--gold);
      font-style: italic;
    }

    .footer-about {
      font-size: 13px;
      color: var(--mid);
      line-height: 1.8;
      margin-top: 14px;
    }

    .footer-contact-info {
      margin-top: 16px;
    }

    .footer-contact-info a {
      display: flex;
      align-items: center;
      gap: 8px;
      font-size: 13px;
      color: var(--mid);
      text-decoration: none;
      margin-bottom: 8px;
      transition: color 0.2s;
    }

    .footer-contact-info a:hover {
      color: var(--gold);
    }

    .footer-contact-info svg {
      width: 16px;
      height: 16px;
      flex-shrink: 0;
    }

    .footer-col h4 {
      font-size: 11px;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--gold);
      margin-bottom: 20px;
      font-weight: 400;
    }

    .footer-col a {
      display: block;
      font-size: 13px;
      color: var(--mid);
      text-decoration: none;
      margin-bottom: 10px;
      transition: color 0.2s;
    }

    .footer-col a:hover {
      color: var(--cream);
    }

    .footer-bottom {
      max-width: 1100px;
      margin: 0 auto;
      padding-top: 22px;
      border-top: 1px solid rgba(255, 255, 255, 0.08);
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-size: 12px;
      color: var(--mid);
      flex-wrap: wrap;
      gap: 10px;
    }

    .social-links {
      display: flex;
      gap: 16px;
    }

    .social-links a {
      color: var(--mid);
      text-decoration: none;
      transition: color 0.2s;
      font-size: 12px;
      letter-spacing: 0.08em;
    }

    .social-links a:hover {
      color: var(--gold);
    }

    /* FLOATING WHATSAPP */
    .float-wa {
      position: fixed;
      bottom: 28px;
      right: 28px;
      z-index: 400;
      width: 56px;
      height: 56px;
      background: var(--green);
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 4px 20px rgba(37, 211, 102, 0.35);
      cursor: pointer;
      text-decoration: none;
      transition: transform 0.2s;
    }

    .float-wa:hover {
      transform: scale(1.08);
    }

    .float-wa svg {
      width: 30px;
      height: 30px;
      fill: white;
    }

    /* TOAST */
    .toast {
      position: fixed;
      bottom: 100px;
      right: 28px;
      background: var(--charcoal);
      color: var(--cream);
      padding: 12px 20px;
      font-size: 13px;
      z-index: 500;
      opacity: 0;
      transform: translateY(10px);
      transition: all 0.3s;
      pointer-events: none;
      border-left: 3px solid var(--gold);
    }

    .toast.show {
      opacity: 1;
      transform: translateY(0);
    }

    /* RESPONSIVE */
    @media (max-width: 900px) {
      .hero {
        grid-template-columns: 1fr;
      }

      .hero-left {
        min-height: 40vw;
      }

      .categories-grid,
      .products-grid {
        grid-template-columns: repeat(2, 1fr);
      }

      .footer-grid {
        grid-template-columns: 1fr 1fr;
      }

      .full-banner {
        grid-template-columns: 1fr;
      }

      .banner-visual {
        min-height: 260px;
      }

      .promise-inner {
        grid-template-columns: repeat(3, 1fr);
      }

      .testimonials-grid {
        grid-template-columns: 1fr;
      }
    }

    @media (max-width: 600px) {

      .header-inner,
      .nav-inner {
        padding: 0 16px;
      }

      .section,
      .testimonials-bg,
      .newsletter,
      .promise-strip,
      .order-section {
        padding-left: 16px;
        padding-right: 16px;
      }

      .hero-right,
      .banner-content {
        padding: 40px 20px;
      }

      .promise-inner {
        grid-template-columns: 1fr 1fr;
      }

      .footer-grid {
        grid-template-columns: 1fr;
        gap: 28px;
      }

      .newsletter-form {
        flex-direction: column;
      }

      .newsletter-form input {
        border-right: 1px solid var(--deep-rose);
        border-bottom: none;
      }

      .cart-sidebar {
        width: 100vw;
      }
    }
  </style>
</head>

<body>

  <!-- Promo Bar -->
  <div class="promo-bar">
    ✦ DM us on WhatsApp to order &nbsp;·&nbsp; <span>+1 (662) 579-7290</span> &nbsp;·&nbsp; Handcrafted with love ✦
  </div>

  <!-- Header -->
  <header>
    <div class="header-inner">
      <a href="#" class="logo">Daisy's <em>Jewelry</em></a>
      <div class="header-icons">
        <button class="icon-btn" onclick="toggleCart()">
          <svg viewBox="0 0 24 24">
            <path d="M6 2 3 6v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2V6l-3-4z" />
            <line x1="3" y1="6" x2="21" y2="6" />
            <path d="M16 10a4 4 0 0 1-8 0" />
          </svg>
          <span class="cart-count" id="cart-count">0</span>
        </button>
      </div>
    </div>
  </header>

  <!-- Nav -->
  <nav>
    <div class="nav-inner">
      <a href="#" class="active">New Arrivals</a>
      <a href="#">Best Sellers</a>
      <a href="#">Necklaces</a>
      <a href="#">Rings</a>
      <a href="#">Earrings</a>
      <a href="#">Bracelets</a>
      <a href="#">Bangles</a>
      <a href="#">Charms</a>
      <a href="#">Silver</a>
      <a href="#">Personalised</a>
      <a href="#">Sale</a>
    </div>
  </nav>

  <!-- Cart Sidebar -->
  <div class="cart-overlay" id="cart-overlay" onclick="toggleCart()"></div>
  <div class="cart-sidebar" id="cart-sidebar">
    <div class="cart-header">
      <span class="cart-title">Your Cart</span>
      <button class="cart-close" onclick="toggleCart()">×</button>
    </div>
    <div class="cart-items" id="cart-items">
      <div class="cart-empty" id="cart-empty">
        <svg viewBox="0 0 24 24">
          <path d="M6 2 3 6v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2V6l-3-4z" />
          <line x1="3" y1="6" x2="21" y2="6" />
          <path d="M16 10a4 4 0 0 1-8 0" />
        </svg>
        <p>Your cart is empty</p>
      </div>
    </div>
    <div class="cart-footer" id="cart-footer" style="display:none;">
      <div class="cart-total">
        <span>Total</span>
        <span id="cart-total">$0.00</span>
      </div>
      <button class="whatsapp-order-btn" onclick="orderOnWhatsApp()">
        <svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
          <path
            d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 0 1-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 0 1-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 0 1 2.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0 0 12.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 0 0 5.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 0 0-3.48-8.413Z" />
        </svg>
        Order via WhatsApp
      </button>
      <div class="cart-contact">
        Or email us at <a href="mailto:daisypatel8084@gmail.com">daisypatel8084@gmail.com</a>
      </div>
    </div>
  </div>

  <!-- Toast -->
  <div class="toast" id="toast">Added to cart!</div>

  <!-- Hero -->
  <section class="hero">
    <div class="hero-left">
      <div class="hero-img-wrap">
        <!-- REPLACE: swap src="" with your image URL or local file path -->
        <svg class="placeholder-svg" viewBox="0 0 120 120" fill="none" stroke="#9c7d44" stroke-width="1">
          <circle cx="60" cy="60" r="40" opacity="0.4" />
          <circle cx="60" cy="60" r="28" opacity="0.6" />
          <path d="M60 30 L80 52 L60 90 L40 52 Z" stroke="#9c7d44" stroke-width="1.5" fill="rgba(200,169,110,0.15)" />
          <path d="M40 52 L60 52 L80 52" stroke="#9c7d44" stroke-width="1" />
        </svg>
      </div>
    </div>
    <div class="hero-right">
      <span class="hero-tag">New Collection — Spring 2026</span>
      <h1 class="hero-title">
        Jewels that tell<br>
        <em>your story</em>
      </h1>
      <p class="hero-sub">Handcrafted fine jewelry for every occasion. Discover pieces that become part of you —
        timeless, delicate, and made to last.</p>
      <div class="btn-group">
        <a href="#products" class="btn-primary">Shop Now</a>
        <a href="https://wa.me/16625797290?text=Hi%20Daisy!%20I%20want%20to%20browse%20your%20jewelry%20collection%20%F0%9F%92%8D"
          target="_blank" class="btn-whatsapp">
          <svg viewBox="0 0 24 24">
            <path
              d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 0 1-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 0 1-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 0 1 2.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0 0 12.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 0 0 5.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 0 0-3.48-8.413Z" />
          </svg>
          Chat on WhatsApp
        </a>
      </div>
    </div>
  </section>

  <!-- Marquee -->
  <div class="marquee-wrap">
    <div class="marquee">
      <span>Handcrafted with Love</span><span>Order via WhatsApp</span><span>New Spring Collection</span><span>Gift
        Wrapping Included</span><span>Free Returns</span><span>Personalised Pieces</span>
      <span>Handcrafted with Love</span><span>Order via WhatsApp</span><span>New Spring Collection</span><span>Gift
        Wrapping Included</span><span>Free Returns</span><span>Personalised Pieces</span>
    </div>
  </div>

  <!-- Categories -->
  <section>
    <div class="section">
      <div class="section-header">
        <span class="section-tag">Shop by Category</span>
        <h2 class="section-title">Find your <em>perfect piece</em></h2>
      </div>
      <div class="categories-grid">
        <div class="cat-card">
          <div class="cat-img">
            <div class="cat-img-inner cat-bg-1">
              <!-- REPLACE: <img src="your-necklaces-image.jpg" alt="Necklaces"> -->
              <svg class="cat-icon" viewBox="0 0 80 80" fill="none" stroke="#9c7d44" stroke-width="1.2">
                <circle cx="40" cy="40" r="25" opacity="0.4" />
                <circle cx="40" cy="40" r="15" opacity="0.6" />
                <path d="M40 15 L40 10 M65 40 L70 40 M40 65 L40 70 M15 40 L10 40" />
              </svg>
            </div>
          </div>
          <div class="cat-label"><span class="cat-name">Necklaces</span><span class="cat-count">48 styles</span></div>
        </div>
        <div class="cat-card">
          <div class="cat-img">
            <div class="cat-img-inner cat-bg-2">
              <!-- REPLACE: <img src="your-rings-image.jpg" alt="Rings"> -->
              <svg class="cat-icon" viewBox="0 0 80 80" fill="none" stroke="#4a8c65" stroke-width="1.2">
                <circle cx="40" cy="32" r="18" />
                <path d="M22 50 C22 62 58 62 58 50" />
                <circle cx="40" cy="32" r="6" fill="rgba(74,140,101,0.2)" />
              </svg>
            </div>
          </div>
          <div class="cat-label"><span class="cat-name">Rings</span><span class="cat-count">36 styles</span></div>
        </div>
        <div class="cat-card">
          <div class="cat-img">
            <div class="cat-img-inner cat-bg-3">
              <!-- REPLACE: <img src="your-earrings-image.jpg" alt="Earrings"> -->
              <svg class="cat-icon" viewBox="0 0 80 80" fill="none" stroke="#9c7d44" stroke-width="1.2">
                <ellipse cx="30" cy="40" rx="8" ry="14" />
                <ellipse cx="50" cy="40" rx="8" ry="14" />
                <path d="M30 26 L50 26 M30 54 L50 54" />
              </svg>
            </div>
          </div>
          <div class="cat-label"><span class="cat-name">Earrings</span><span class="cat-count">62 styles</span></div>
        </div>
        <div class="cat-card">
          <div class="cat-img">
            <div class="cat-img-inner cat-bg-4">
              <!-- REPLACE: <img src="your-bracelets-image.jpg" alt="Bracelets"> -->
              <svg class="cat-icon" viewBox="0 0 80 80" fill="none" stroke="#7a6a9a" stroke-width="1.2">
                <path d="M15 40 Q15 20 40 20 Q65 20 65 40 Q65 60 40 60 Q15 60 15 40" opacity="0.4" />
                <path d="M20 40 Q20 25 40 25 Q60 25 60 40 Q60 55 40 55 Q20 55 20 40" />
              </svg>
            </div>
          </div>
          <div class="cat-label"><span class="cat-name">Bracelets</span><span class="cat-count">29 styles</span></div>
        </div>
      </div>
    </div>
  </section>

  <!-- Promise Strip -->
  <div class="promise-strip">
    <div class="promise-inner">
      <div class="promise-item">
        <div class="promise-icon"><svg viewBox="0 0 44 44">
            <path d="M22 4 L28 16 L42 18 L32 28 L34 42 L22 36 L10 42 L12 28 L2 18 L16 16 Z" />
          </svg></div>
        <p class="promise-label">Quality Guaranteed</p>
        <p class="promise-desc">Every piece is crafted with premium materials and inspected before shipping.</p>
      </div>
      <div class="promise-item">
        <div class="promise-icon"><svg viewBox="0 0 44 44">
            <path d="M6 22 L14 14 L30 14 L38 22 L30 30 L14 30 Z" />
            <circle cx="22" cy="22" r="4" />
          </svg></div>
        <p class="promise-label">Free Returns</p>
        <p class="promise-desc">Not in love? Return within 30 days — just message us on WhatsApp.</p>
      </div>
      <div class="promise-item">
        <div class="promise-icon"><svg viewBox="0 0 44 44">
            <path d="M8 14 L22 6 L36 14 L36 26 C36 34 22 40 22 40 C22 40 8 34 8 26 Z" />
          </svg></div>
        <p class="promise-label">Gift Ready</p>
        <p class="promise-desc">Beautifully wrapped in our signature gift box — perfect for any occasion.</p>
      </div>
    </div>
  </div>

  <!-- Featured Products -->
  <section id="products">
    <div class="section">
      <div class="section-header">
        <span class="section-tag">Curated for You</span>
        <h2 class="section-title">Best <em>Sellers</em></h2>
      </div>
      <div class="products-grid">

        <div class="product-card" data-id="1" data-name="Celestial Drop Necklace" data-material="18k Gold Plated"
          data-price="48.00">
          <div class="product-img">
            <div class="product-img-inner cat-bg-1">
              <!-- REPLACE: <img src="necklace1.jpg" alt="Celestial Drop Necklace"> -->
              <svg width="70" height="70" viewBox="0 0 70 70" fill="none" stroke="#9c7d44" stroke-width="1.2">
                <circle cx="35" cy="22" r="14" />
                <line x1="35" y1="36" x2="35" y2="60" />
                <circle cx="35" cy="22" r="7" fill="rgba(200,169,110,0.2)" />
              </svg>
            </div>
            <span class="product-badge badge-new">New</span>
            <div class="product-actions">
              <button class="add-to-cart-btn" onclick="addToCart(this)">Add to Cart</button>
            </div>
          </div>
          <p class="product-material">18k Gold Plated</p>
          <h3 class="product-name">Celestial Drop Necklace</h3>
          <div class="product-price">$48.00</div>
        </div>

        <div class="product-card" data-id="2" data-name="Woven Hoop Earrings" data-material="Sterling Silver"
          data-price="24.50">
          <div class="product-img">
            <div class="product-img-inner cat-bg-4">
              <!-- REPLACE: <img src="earrings1.jpg" alt="Woven Hoop Earrings"> -->
              <svg width="70" height="70" viewBox="0 0 70 70" fill="none" stroke="#7a6a9a" stroke-width="1.2">
                <circle cx="35" cy="35" r="22" />
                <circle cx="35" cy="35" r="14" />
                <circle cx="35" cy="13" r="4" fill="rgba(122,106,154,0.3)" />
              </svg>
            </div>
            <span class="product-badge badge-sale">Sale</span>
            <div class="product-actions">
              <button class="add-to-cart-btn" onclick="addToCart(this)">Add to Cart</button>
            </div>
          </div>
          <p class="product-material">Sterling Silver</p>
          <h3 class="product-name">Woven Hoop Earrings</h3>
          <div class="product-price"><span class="original">$35.00</span><span class="sale">$24.50</span></div>
        </div>

        <div class="product-card" data-id="3" data-name="Marquise Signet Ring" data-material="Gold Fill"
          data-price="62.00">
          <div class="product-img">
            <div class="product-img-inner cat-bg-3">
              <!-- REPLACE: <img src="ring1.jpg" alt="Marquise Signet Ring"> -->
              <svg width="70" height="70" viewBox="0 0 70 70" fill="none" stroke="#9c7d44" stroke-width="1.2">
                <path d="M20 35 Q35 18 50 35 Q35 52 20 35 Z" fill="rgba(200,169,110,0.15)" />
                <circle cx="35" cy="35" r="6" fill="rgba(200,169,110,0.3)" />
              </svg>
            </div>
            <div class="product-actions">
              <button class="add-to-cart-btn" onclick="addToCart(this)">Add to Cart</button>
            </div>
          </div>
          <p class="product-material">Gold Fill</p>
          <h3 class="product-name">Marquise Signet Ring</h3>
          <div class="product-price">$62.00</div>
        </div>

        <div class="product-card" data-id="4" data-name="Twisted Chain Bracelet" data-material="Stainless Steel"
          data-price="39.00">
          <div class="product-img">
            <div class="product-img-inner cat-bg-2">
              <!-- REPLACE: <img src="bracelet1.jpg" alt="Twisted Chain Bracelet"> -->
              <svg width="70" height="70" viewBox="0 0 70 70" fill="none" stroke="#4a8c65" stroke-width="1.2">
                <path d="M14 35 Q14 20 35 20 Q56 20 56 35 Q56 50 35 50 Q14 50 14 35" />
                <circle cx="35" cy="20" r="4" fill="rgba(74,140,101,0.3)" />
              </svg>
            </div>
            <span class="product-badge badge-new">New</span>
            <div class="product-actions">
              <button class="add-to-cart-btn" onclick="addToCart(this)">Add to Cart</button>
            </div>
          </div>
          <p class="product-material">Stainless Steel</p>
          <h3 class="product-name">Twisted Chain Bracelet</h3>
          <div class="product-price">$39.00</div>
        </div>

      </div>
    </div>
  </section>

  <!-- Promo Banner -->
  <div class="full-banner">
    <div class="banner-content">
      <span class="banner-tag">Limited Edition</span>
      <h2 class="banner-title">The Charm <em>Collection</em></h2>
      <p class="banner-body">Build your story, one charm at a time. Our personalised charm bracelets let you curate
        pieces that mean something — names, birthstones, symbols.</p>
      <a href="https://wa.me/16625797290?text=Hi%20Daisy!%20I%27d%20love%20to%20order%20from%20the%20Charm%20Collection%20%F0%9F%92%8D"
        target="_blank" class="btn-whatsapp">
        <svg viewBox="0 0 24 24">
          <path
            d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 0 1-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 0 1-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 0 1 2.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0 0 12.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 0 0 5.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 0 0-3.48-8.413Z" />
        </svg>
        Shop Charms on WhatsApp
      </a>
    </div>
    <div class="banner-visual">
      <div class="banner-circle">
        <svg width="100" height="100" viewBox="0 0 100 100" fill="none" stroke="rgba(200,169,110,0.7)" stroke-width="1">
          <circle cx="50" cy="30" r="10" />
          <path d="M30 60 L50 45 L70 60 L62 80 L38 80 Z" />
          <circle cx="50" cy="30" r="4" fill="rgba(200,169,110,0.3)" />
          <path d="M50 20 L50 10" />
        </svg>
      </div>
    </div>
  </div>

  <!-- How to Order Section -->
  <div class="order-section">
    <div class="order-inner">
      <h2 class="order-title">How to Order</h2>
      <p class="order-sub">
        Simply add items to your cart and tap <strong>"Order via WhatsApp"</strong> — your full order list will be sent
        directly to Daisy. She'll confirm availability and share payment details with you personally. Easy, personal,
        and trusted.
      </p>
      <div class="order-buttons">
        <a href="https://wa.me/16625797290" target="_blank" class="btn-whatsapp">
          <svg viewBox="0 0 24 24">
            <path
              d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 0 1-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 0 1-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 0 1 2.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0 0 12.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 0 0 5.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 0 0-3.48-8.413Z" />
          </svg>
          WhatsApp: +1 (662) 579-7290
        </a>
        <a href="mailto:daisypatel8084@gmail.com" class="contact-email-btn">
          <svg viewBox="0 0 24 24">
            <path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z" />
            <polyline points="22,6 12,13 2,6" />
          </svg>
          Email Us
        </a>
      </div>
    </div>
  </div>

  <!-- Testimonials -->
  <div class="testimonials-bg">
    <div style="max-width:1100px; margin:0 auto;">
      <div class="section-header">
        <span class="section-tag">What Our Customers Say</span>
        <h2 class="section-title">Loved by <em>everyone</em></h2>
      </div>
      <div class="testimonials-grid">
        <div class="testimonial-card">
          <div class="stars">★★★★★</div>
          <p class="testimonial-text">"The necklace arrived beautifully packaged and looks even more stunning in person.
            It's become my everyday go-to piece."</p>
          <span class="testimonial-author">— Sophie T.</span>
        </div>
        <div class="testimonial-card">
          <div class="stars">★★★★★</div>
          <p class="testimonial-text">"Ordering on WhatsApp was so easy! Daisy was super responsive and my bracelet
            arrived exactly as described. Love it."</p>
          <span class="testimonial-author">— Mia R.</span>
        </div>
        <div class="testimonial-card">
          <div class="stars">★★★★★</div>
          <p class="testimonial-text">"Fast, friendly and gorgeous jewelry. The gift wrapping is absolutely next level.
            Will definitely be ordering again!"</p>
          <span class="testimonial-author">— Chloe K.</span>
        </div>
      </div>
    </div>
  </div>

  <!-- Newsletter -->
  <div class="newsletter">
    <div class="newsletter-inner">
      <h2 class="newsletter-title">Stay in the Loop</h2>
      <p class="newsletter-sub">New arrivals, exclusive drops & styling tips — straight to your inbox.</p>
      <div class="newsletter-form">
        <input type="email" placeholder="Your email address">
        <button type="button">Subscribe</button>
      </div>
    </div>
  </div>

  <!-- Footer -->
  <footer>
    <div class="footer-grid">
      <div class="footer-brand">
        <a href="#" class="logo">Daisy's <span class="footer-logo-em">Jewelry</span></a>
        <p class="footer-about">Handcrafted fine jewelry made with love. Every piece tells a story — we'd love for it to
          tell yours.</p>
        <div class="footer-contact-info">
          <a href="https://wa.me/16625797290" target="_blank">
            <svg viewBox="0 0 24 24" fill="currentColor">
              <path
                d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 0 1-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 0 1-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 0 1 2.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0 0 12.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 0 0 5.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 0 0-3.48-8.413Z" />
            </svg>
            +1 (662) 579-7290
          </a>
          <a href="mailto:daisypatel8084@gmail.com">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
              <path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z" />
              <polyline points="22,6 12,13 2,6" />
            </svg>
            daisypatel8084@gmail.com
          </a>
        </div>
      </div>
      <div class="footer-col">
        <h4>Shop</h4>
        <a href="#">New Arrivals</a>
        <a href="#">Best Sellers</a>
        <a href="#">Necklaces</a>
        <a href="#">Rings</a>
        <a href="#">Earrings</a>
        <a href="#">Sale</a>
      </div>
      <div class="footer-col">
        <h4>Help</h4>
        <a href="https://wa.me/16625797290" target="_blank">Contact Us</a>
        <a href="#">Shipping Info</a>
        <a href="#">Returns</a>
        <a href="#">Size Guide</a>
        <a href="#">Care Guide</a>
      </div>
      <div class="footer-col">
        <h4>Order</h4>
        <a href="https://wa.me/16625797290" target="_blank">WhatsApp Order</a>
        <a href="mailto:daisypatel8084@gmail.com">Email Order</a>
        <a href="#">Privacy Policy</a>
        <a href="#">Terms & Conditions</a>
      </div>
    </div>
    <div class="footer-bottom">
      <span>© 2026 Daisy's Jewelry. All rights reserved.</span>
      <div class="social-links">
        <a href="#">Instagram</a>
        <a href="#">Pinterest</a>
        <a href="#">Facebook</a>
        <a href="#">TikTok</a>
      </div>
    </div>
  </footer>

  <!-- Floating WhatsApp Button -->
  <a class="float-wa"
    href="https://wa.me/16625797290?text=Hi%20Daisy!%20I%27d%20love%20to%20order%20some%20jewelry%20%F0%9F%92%8D"
    target="_blank" title="Chat on WhatsApp">
    <svg viewBox="0 0 24 24">
      <path
        d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 0 1-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 0 1-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 0 1 2.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0 0 12.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 0 0 5.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 0 0-3.48-8.413Z" />
    </svg>
  </a>

  <script>
    // ── CART STATE ──
    const cart = {};

    function getProductData(btn) {
      const card = btn.closest('.product-card');
      return {
        id: card.dataset.id,
        name: card.dataset.name,
        material: card.dataset.material,
        price: parseFloat(card.dataset.price)
      };
    }

    function addToCart(btn) {
      const p = getProductData(btn);
      if (cart[p.id]) {
        cart[p.id].qty++;
      } else {
        cart[p.id] = { ...p, qty: 1 };
      }
      renderCart();
      showToast(p.name + ' added to cart!');
      openCart();
    }

    function removeFromCart(id) {
      delete cart[id];
      renderCart();
    }

    function changeQty(id, delta) {
      if (!cart[id]) return;
      cart[id].qty += delta;
      if (cart[id].qty <= 0) delete cart[id];
      renderCart();
    }

    function renderCart() {
      const items = Object.values(cart);
      const countEl = document.getElementById('cart-count');
      const itemsEl = document.getElementById('cart-items');
      const emptyEl = document.getElementById('cart-empty');
      const footerEl = document.getElementById('cart-footer');
      const totalEl = document.getElementById('cart-total');

      const totalQty = items.reduce((s, i) => s + i.qty, 0);
      const totalPrice = items.reduce((s, i) => s + i.qty * i.price, 0);

      countEl.textContent = totalQty;

      if (items.length === 0) {
        itemsEl.innerHTML = '';
        itemsEl.appendChild(emptyEl || createEmpty());
        document.getElementById('cart-empty').style.display = '';
        footerEl.style.display = 'none';
        return;
      }

      let html = '';
      items.forEach(item => {
        html += `
        <div class="cart-item">
          <div class="cart-item-img">
            <svg width="40" height="40" viewBox="0 0 70 70" fill="none" stroke="#9c7d44" stroke-width="1.2">
              <circle cx="35" cy="35" r="20" opacity="0.4"/>
              <circle cx="35" cy="35" r="12" opacity="0.6"/>
            </svg>
          </div>
          <div class="cart-item-info">
            <div class="cart-item-name">${item.name}</div>
            <div class="cart-item-material">${item.material}</div>
            <div class="cart-item-price">$${(item.price * item.qty).toFixed(2)}</div>
            <div class="cart-qty">
              <button class="qty-btn" onclick="changeQty('${item.id}', -1)">−</button>
              <span class="qty-val">${item.qty}</span>
              <button class="qty-btn" onclick="changeQty('${item.id}', 1)">+</button>
            </div>
          </div>
          <button class="cart-item-remove" onclick="removeFromCart('${item.id}')">×</button>
        </div>`;
      });
      itemsEl.innerHTML = html;
      footerEl.style.display = '';
      totalEl.textContent = '$' + totalPrice.toFixed(2);
    }

    function toggleCart() {
      document.getElementById('cart-sidebar').classList.toggle('open');
      document.getElementById('cart-overlay').classList.toggle('open');
    }

    function openCart() {
      document.getElementById('cart-sidebar').classList.add('open');
      document.getElementById('cart-overlay').classList.add('open');
    }

    function showToast(msg) {
      const t = document.getElementById('toast');
      t.textContent = msg;
      t.classList.add('show');
      setTimeout(() => t.classList.remove('show'), 2500);
    }

    function orderOnWhatsApp() {
      const items = Object.values(cart);
      if (items.length === 0) return;

      const total = items.reduce((s, i) => s + i.qty * i.price, 0);

      let msg = "Hi Daisy! 💍 I'd like to place an order:\n\n";
      items.forEach(item => {
        msg += `• ${item.name} (${item.material}) × ${item.qty} = $${(item.qty * item.price).toFixed(2)}\n`;
      });
      msg += `\n*Total: $${total.toFixed(2)}*\n\nPlease confirm availability and payment details. Thank you! 🌸`;

      const encoded = encodeURIComponent(msg);
      window.open('https://wa.me/16625797290?text=' + encoded, '_blank');
    }

    // Init
    renderCart();
  </script>

</body>

</html>
