# 🛍️ Product Catalog with Cart System

> A fully functional mini e-commerce product listing page with search, filters, sorting, pagination, and a persistent shopping cart using LocalStorage — built with pure HTML, CSS, and JavaScript.

![Project Demo](https://img.shields.io/badge/demo-live-green) ![JavaScript](https://img.shields.io/badge/JavaScript-ES6-yellow) ![License](https://img.shields.io/badge/license-MIT-blue) ![Status](https://img.shields.io/badge/status-completed-brightgreen)

---

## 📌 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Live Demo](#live-demo)
- [Screenshots](#screenshots)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Installation & Setup](#installation--setup)
- [How It Works](#how-it-works)
- [LocalStorage Cart System](#localstorage-cart-system)
- [Future Improvements](#future-improvements)
- [What I Learned](#what-i-learned)
- [Task Requirements](#task-requirements)
- [Author](#author)
- [License](#license)

---

## 📖 Overview

This project was built as **Task 5** of my Full Stack Web Development Internship. The goal was to build a mini e-commerce style **Product Catalog** — similar to what users see in shopping apps like Flipkart or Amazon (basic version) — without using any backend or frameworks.

The project demonstrates core frontend skills including:
- Loading and displaying dynamic data from a local JSON file
- Implementing search, filters, and sorting together
- Adding pagination to improve UX
- Creating a lightweight cart system using LocalStorage

---

## ✨ Features

### Product Listing Page
- ✅ Products displayed in a responsive grid layout
- ✅ Each product shows: image (emoji), name, price, category
- ✅ **Search Bar** — filter products by name (real-time)
- ✅ **Category Filter** — dropdown (Electronics / Fashion / Grocery)
- ✅ **Sorting** — Price (Low→High / High→Low) & Name (A→Z)
- ✅ **Pagination** — 8 products per page with page navigation

### Shopping Cart
- ✅ Add to Cart — stores products in LocalStorage
- ✅ Dedicated **Cart Page** — view all added items
- ✅ Update quantity (+ / - buttons)
- ✅ Remove item from cart
- ✅ Real-time cart total calculation
- ✅ Cart count badge in header

### UI/UX
- ✅ Clean, modern design
- ✅ Mobile responsive
- ✅ Hover effects on product cards
- ✅ Visual feedback when adding to cart

---

## 🎥 Live Demo

> 🔗 **Live Demo:** [Add your deployed link here after hosting on Netlify/Vercel/GitHub Pages]

To run locally:
```bash
git clone https://github.com/your-username/product-catalog.git
cd product-catalog
open index.html


┌─────────────────────────────────────────────────────────┐
│  🛍️ ShopHub                          🛒 Cart (3)        │
├─────────────────────────────────────────────────────────┤
│  🔍 Search: [________]  📂 Category: [All▼]  ⚡ Sort: [Default▼] │
├─────────────────────────────────────────────────────────┤
│  ┌─────────┐  ┌─────────┐  ┌─────────┐  ┌─────────┐    │
│  │   🎧    │  │   👖    │  │   🥜    │  │   ⌚     │    │
│  │Earbuds  │  │ Jeans   │  │Almonds  │  │Watch    │    │
│  │ $49.99  │  │ $39.99  │  │ $12.49  │  │ $89.99  │    │
│  │[Add]    │  │[Add]    │  │[Add]    │  │[Add]    │    │
│  └─────────┘  └─────────┘  └─────────┘  └─────────┘    │
│                                                          │
│  [1] [2] [3]                                      Page 1 │
└─────────────────────────────────────────────────────────┘




┌─────────────────────────────────────────────────────────┐
│  🛍️ ShopHub - Cart                    🏠 Back to Shop    │
├─────────────────────────────────────────────────────────┤
│  Your Cart 🛒                                            │
│                                                          │
│  Wireless Earbuds    [-] 2 [+]    $99.98    [Remove]    │
│  Smart Watch         [-] 1 [+]    $89.99    [Remove]    │
│  ─────────────────────────────────────────────────────  │
│  Total: $189.97                                          │
│                                                          │
│                    [Clear Cart]                          │
└─────────────────────────────────────────────────────────┘


┘
🛠️ Tech Stack
Technology	Purpose
HTML5	Structure & semantics
CSS3	Styling, grid layout, responsive design
JavaScript (ES6)	All logic: filtering, sorting, pagination, cart
LocalStorage API	Persistent cart storage
JSON	Product data source
No frameworks, no libraries — just vanilla JavaScript.

📁 Project Structure
text
product-catalog/
│
├── index.html              # Main product listing page
├── cart.html               # Shopping cart page
├── style.css               # All styles (responsive + modern UI)
├── script.js               # Product listing logic (filters, sort, pagination)
├── cart-script.js          # Cart page logic (quantity, remove, total)
├── products.json           # Product database (16 products)
│
└── README.md               # Project documentation
🚀 Installation & Setup
Prerequisites
Any modern web browser (Chrome, Firefox, Edge, Safari)

VS Code (recommended) or any code editor

Live Server extension (optional, for better development experience)

Steps to Run
Clone the repository

bash
git clone https://github.com/your-username/product-catalog.git
cd product-catalog
Open with Live Server (recommended)

In VS Code: Right-click index.html → Open with Live Server

Or simply double-click index.html to open in browser

Start shopping!

Browse products, apply filters, add items to cart

Navigate to cart page to manage quantities

⚠️ Note: Due to CORS restrictions when using fetch() with local JSON files, you need to serve the files via a local server (Live Server works perfectly).

⚙️ How It Works
1. Product Data (products.json)
All products are stored in a JSON file with the following structure:

json
{
  "id": 1,
  "name": "Wireless Noise Earbuds",
  "price": 49.99,
  "category": "Electronics",
  "image": "🎧",
  "rating": 4
}
2. Filtering Logic
javascript
// Search + Category filter
let filtered = products.filter(product => 
  product.name.toLowerCase().includes(searchTerm) &&
  (category === 'all' || product.category === category)
);
3. Sorting Logic
javascript
if (sortBy === 'price-asc') {
  filtered.sort((a, b) => a.price - b.price);
} else if (sortBy === 'name-asc') {
  filtered.sort((a, b) => a.name.localeCompare(b.name));
}
4. Pagination
javascript
const start = (currentPage - 1) * itemsPerPage;
const paginatedProducts = filteredProducts.slice(start, start + itemsPerPage);
5. Cart System (LocalStorage)
javascript
// Add to cart
function addToCart(product) {
  let cart = getCart();
  const existing = cart.find(item => item.id === product.id);
  if (existing) {
    existing.quantity += 1;
  } else {
    cart.push({ ...product, quantity: 1 });
  }
  localStorage.setItem('ecom_cart', JSON.stringify(cart));
}
💾 LocalStorage Cart System
The cart uses the browser's LocalStorage to persist data even after page refresh.

Key	Value
ecom_cart	Array of cart items with id, name, price, quantity, image, category
Example cart data:

json
[
  {
    "id": 1,
    "name": "Wireless Noise Earbuds",
    "price": 49.99,
    "quantity": 2,
    "image": "🎧",
    "category": "Electronics"
  }
]
Cart Operations:

getCart() — retrieve cart from LocalStorage

saveCart(cart) — save cart to LocalStorage

addToCart(product) — add or increment quantity

updateQuantity(id, delta) — change quantity (+/-)

removeItem(id) — delete item from cart

clearCart() — remove all items

🔮 Future Improvements
These features are optional but would make the project even better:

Price range slider — filter by min/max price

Wishlist / Favorites — save liked products in LocalStorage

Rating filter — show products with 4+ stars only

Product Detail Page — click product to see full details

Skeleton loading — show placeholders before data loads

Dark mode — toggle between light/dark themes

Checkout form — collect user details before order

Order summary — show order confirmation

Backend integration — connect to Node.js/Express + MongoDB

User authentication — login/signup to save cart across devices

📚 What I Learned
This project taught me:

✅ State management — handling filters, search, sorting, and pagination together
✅ Array methods — filter(), sort(), slice(), find(), map()
✅ LocalStorage API — persisting cart data across page reloads
✅ Event handling — input, change, click events with dynamic elements
✅ Pagination logic — slicing data and generating page buttons
✅ Responsive design — CSS Grid, Flexbox, media queries
✅ Modular code — separating concerns across multiple files
✅ Real-world patterns — exactly how e-commerce frontends work

📋 Task Requirements (Checklist)
Feature	Status
Product listing page with grid layout	✅
Search bar (filter by name)	✅
Category filter (dropdown)	✅
Sorting (price low→high, high→low, name A→Z)	✅
Pagination (8 products per page)	✅
Add to cart system	✅
LocalStorage persistence	✅
Dedicated cart page	✅
Update quantity / remove item	✅
Cart total calculation	✅
Clean, responsive UI	✅
👨‍💻 Author
Your Name
https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white
https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white
https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white

📧 Email: your.email@example.com

📄 License
This project is licensed under the MIT License — feel free to use, modify, and distribute.

text
MIT License

Copyright (c) 2025 Your Name

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files...
🙏 Acknowledgments
Task assignment by Full Stack Web Development Internship

Icons and inspiration from Flipkart & Amazon

MDN Web Docs for JavaScript references

FreeCodeCamp for pagination logic tutorial

⭐ Show Your Support
If you found this project helpful, please give it a ⭐ on GitHub and share it with others!

text

---

## 📦 Bonus: Badges You Can Add

Copy-paste these at the top of your README:

```markdown
![HTML5](https://img.shields.io/badge/html5-%23E34F26.svg?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/css3-%231572B6.svg?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E)
![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)
