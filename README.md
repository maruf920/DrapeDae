<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>পোশাক ব্র্যান্ড ওয়েবসাইট | DrapeDae - স্টাইল ও গুণগত মান</title>
    <!-- Load Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Tailwind Configuration for new colors and font -->
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                    },
                    colors: {
                        // Brand Color: A sophisticated, deep Crimson/Maroon
                        'primary-brand': '#b91c1c', // Red-700
                        // Accent Color: A luxurious Gold/Amber for pricing/ratings
                        'accent-gold': '#fbbf24', // Amber-400
                        // Backgrounds
                        'bg-dark': '#0f0f0f', // Slightly softer near-black
                        'card-bg': '#1a1a1a', // Dark card background for contrast
                    }
                }
            }
        }
    </script>
    <!-- Load Inter font -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap" rel="stylesheet">
    <style>
        /* Smooth scrolling for better user experience */
        html {
            scroll-behavior: smooth;
        }
        /* Custom styles for premium look */
        .premium-shadow {
            box-shadow: 0 10px 15px -3px rgba(185, 28, 28, 0.5), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
        }
        .hero-title-underline {
            display: inline-block;
            position: relative;
        }
        .hero-title-underline::after {
            content: '';
            position: absolute;
            width: 80%;
            height: 4px;
            bottom: -10px;
            left: 10%;
            background-color: #fbbf24; /* Accent Gold */
            border-radius: 2px;
        }
        /* Style for the checkout modal overlay */
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1000;
        }
        .modal-content {
            max-height: 90vh;
            overflow-y: auto;
            /* Scrollbar styling for dark mode */
            scrollbar-color: #b91c1c #1a1a1a;
            scrollbar-width: thin;
        }
        
        /* --- NEW: Cart Pulse Animation --- */
        .btn-pulse {
            animation: pulse-once 0.5s cubic-bezier(0.25, 0.1, 0.25, 1);
        }
        @keyframes pulse-once {
            0% { transform: scale(1); box-shadow: 0 0 0 0 rgba(251, 191, 36, 0.7); } /* Start with gold shadow */
            50% { transform: scale(1.2); box-shadow: 0 0 0 15px rgba(251, 191, 36, 0); } /* Pop bigger, shadow fades */
            100% { transform: scale(1); } /* Back to normal */
        }
        /* --------------------------------- */
    </style>
</head>

<body class="font-sans bg-bg-dark text-gray-200">

    <!-- NAVIGATION BAR -->
    <header class="sticky top-0 z-50 bg-bg-dark/90 backdrop-blur-md shadow-2xl border-b border-gray-800">
        <nav class="container mx-auto max-w-7xl px-6 py-5 flex justify-between items-center">
            <!-- Brand Logo -->
            <a href="#home" class="text-3xl font-extrabold tracking-wider text-primary-brand hover:text-accent-gold transition duration-300">DrapeDae</a>
            
            <!-- Desktop Navigation Links -->
            <div class="flex items-center space-x-8 text-lg font-medium">
                <a href="#new-collection" class="hidden md:block hover:text-primary-brand transition">নতুন কালেকশন</a>
                <a href="#products" class="hidden md:block hover:text-primary-brand transition">পণ্য</a>
                <a href="#story" class="hidden md:block hover:text-primary-brand transition">আমাদের কথা</a>
                <a href="#contact" class="hidden md:block px-4 py-2 bg-primary-brand text-white rounded-full hover:bg-red-800 transition duration-300 transform hover:scale-105 shadow-md">যোগাযোগ</a>

                <!-- Cart Icon with Counter - PULSE TARGET -->
                <button id="open-cart-btn" onclick="openCheckoutModal()" class="relative p-2 rounded-full hover:bg-gray-800 transition duration-300 focus:outline-none">
                    <!-- Shopping Cart SVG Icon -->
                    <svg class="w-7 h-7 text-gray-200" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 3h2l.4 2M7 13h10l4-8H5.4M7 13L5.4 5M7 13l-2.293 2.293c-.63.63-.184 1.707.707 1.707H17m0 0a2 2 0 100 4 2 2 0 000-4zm-8 2a2 2 0 11-4 0 2 2 0 014 0z"></path>
                    </svg>
                    <!-- Cart Counter Bubble -->
                    <span id="cart-count" class="absolute top-0 right-0 inline-flex items-center justify-center px-2 py-1 text-xs font-bold leading-none text-white transform translate-x-1/2 -translate-y-1/2 bg-accent-gold rounded-full">
                        0
                    </span>
                </button>
            </div>
            
            <!-- Mobile Menu Button (Hamburger Icon) - Now only for the navigation menu, cart is separate -->
            <button class="md:hidden text-gray-200 hover:text-primary-brand transition focus:outline-none" aria-label="Toggle menu">
                <svg class="w-7 h-7" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path></svg>
            </button>
        </nav>
    </header>

    <main class="container mx-auto max-w-7xl px-6">

        <!-- HERO SECTION: Dynamic Main Banner -->
        <section id="home" class="min-h-[90vh] flex items-center justify-center text-center py-20 bg-center bg-cover rounded-2xl mt-6 border border-gray-800 premium-shadow" 
                 style="background-image: url('https://images.unsplash.com/photo-1558769114-15cb9f3c7062?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w0NDUyMnwwfDF8c2VhcmNofDE3fHxjbG90aGluZyUyMGJvbnVzfGVufDB8fHx8MTcyNzE3MTk5N3ww&ixlib=rb-4.0.3&q=80&w=1080'); background-blend-mode: overlay; background-color: rgba(0, 0, 0, 0.4);">
            <!-- আপনার মূল ব্যানার/হিরো ইমেজ URL এখানে পরিবর্তন করুন -->
            <div class="space-y-8 max-w-5xl p-8 rounded-xl backdrop-blur-sm">
                <h1 class="text-5xl sm:text-7xl md:text-8xl font-black leading-tight text-white shadow-lg">
                    <span class="hero-title-underline">প্রিমিয়াম স্টাইল ও গুণমান</span>
                </h1>
                <p class="text-xl md:text-3xl font-light text-gray-300 max-w-4xl mx-auto tracking-wide">
                    DrapeDae: যেখানে আপনার প্রতিদিনের পোশাক হয়ে ওঠে ফ্যাশন স্টেটমেন্ট।
                </p>
                <div class="pt-8">
                    <a href="#products" class="px-12 py-4 bg-primary-brand text-white text-xl font-bold rounded-xl shadow-2xl shadow-primary-brand/50 hover:bg-red-800 transition duration-500 transform hover:scale-[1.05] inline-block border-2 border-primary-brand tracking-widest">
                        বিশেষ কালেকশন দেখুন
                    </a>
                </div>
            </div>
        </section>

        <!-- NEW COLLECTION / CATEGORIES SECTION (Enhanced look) -->
        <section id="new-collection" class="py-24 border-t border-gray-900">
            <h2 class="text-4xl font-bold text-center mb-16 text-white border-b-2 border-accent-gold/50 inline-block px-4 pb-2">নতুন কালেকশন</h2>
            <div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-8">
                
                <!-- Category Card 1 (Refined Style) -->
                <div class="bg-card-bg rounded-2xl overflow-hidden shadow-xl group cursor-pointer border border-gray-800 hover:border-primary-brand transition duration-500 transform hover:-translate-y-1">
                    <!-- ক্যাটাগরি ১ (T-Shirt) ছবি URL এখানে পরিবর্তন করুন -->
                    <img class="w-full h-72 object-cover group-hover:scale-105 transition duration-700 ease-in-out"
                        src="https://images.unsplash.com/photo-1579227114347-154484050d2d?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w0NDUyMnwwfDF8c2VhcmNofDJ8fGJhc2ljJTIwdCUyMHNoaXJ0fGVufDB8fHx8MTcyNzE3MjE3Mnww&ixlib=rb-4.0.3&q=80&w=600" alt="T-Shirt Collection">
                    <div class="p-6 text-center">
                        <h3 class="text-3xl font-semibold text-white">ডেইলী টি-শার্ট</h3>
                        <p class="text-gray-400 mt-2 text-sm uppercase tracking-wider text-accent-gold">সর্বোচ্চ আরাম</p>
                    </div>
                </div>

                <!-- Category Card 2 -->
                <div class="bg-card-bg rounded-2xl overflow-hidden shadow-xl group cursor-pointer border border-gray-800 hover:border-primary-brand transition duration-500 transform hover:-translate-y-1">
                    <!-- ক্যাটাগরি ২ (Formal) ছবি URL এখানে পরিবর্তন করুন -->
                    <img class="w-full h-72 object-cover group-hover:scale-105 transition duration-700 ease-in-out"
                        src="https://images.unsplash.com/photo-1621251356515-385054366050?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w0NDUyMnwwfDF8c2VhcmNofDE3fHxmb3JtYWwlMjBzaGlydHxlbnwwfHx8fDE3MjcxNzIyMjN8MA&ixlib=rb-4.0.3&q=80&w=600" alt="Formal Collection">
                    <div class="p-6 text-center">
                        <h3 class="text-3xl font-semibold text-white">ফর্মাল ওয়্যার</h3>
                        <p class="text-gray-400 mt-2 text-sm uppercase tracking-wider text-accent-gold">কর্মক্ষেত্রের স্টাইল</p>
                    </div>
                </div>

                <!-- Category Card 3 -->
                <div class="bg-card-bg rounded-2xl overflow-hidden shadow-xl group cursor-pointer border border-gray-800 hover:border-primary-brand transition duration-500 transform hover:-translate-y-1">
                    <!-- ক্যাটাগরি ৩ (Winter) ছবি URL এখানে পরিবর্তন করুন -->
                    <img class="w-full h-72 object-cover group-hover:scale-105 transition duration-700 ease-in-out"
                        src="https://images.unsplash.com/photo-1544520623-a55d64024c08?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w0NDUyMnwwfDF8c2VhcmNofDExfHx3aW50ZXIlMjBqYWNrZXR8ZW58MHx8fHwxNzI3MTcyMjUxfDA&ixlib=rb-4.0.3&q=80&w=600" alt="Winter Collection">
                    <div class="p-6 text-center">
                        <h3 class="text-3xl font-semibold text-white">শীতকালীন জ্যাকেট</h3>
                        <p class="text-gray-400 mt-2 text-sm uppercase tracking-wider text-accent-gold">উষ্ণতা ও ফ্যাশন</p>
                    </div>
                </div>
            </div>
        </section>
        
        <!-- FEATURED PRODUCTS SECTION (With Discounts and Ratings) -->
        <section id="products" class="py-24 border-t border-gray-900">
            <h2 class="text-4xl font-bold text-center mb-16 text-white border-b-2 border-accent-gold/50 inline-block px-4 pb-2">জনপ্রিয় পণ্য</h2>
            <div class="grid sm:grid-cols-2 lg:grid-cols-4 gap-8">
                
                <!-- Product 1: Highlighting Discount (ID 1) -->
                <div class="product-card bg-card-bg rounded-2xl shadow-2xl p-4 space-y-3 border border-gray-700 hover:border-accent-gold transition duration-300 transform hover:scale-[1.02] relative group" data-id="1" data-name="প্রিমিয়াম কটন টি-শার্ট" data-price="1020">
                    <!-- Discount Badge -->
                    <div class="absolute top-0 right-0 bg-primary-brand text-white text-xs font-bold px-3 py-1 rounded-bl-lg rounded-tr-2xl z-10">
                        ১৫% ছাড়
                    </div>
                    <!-- পণ্য ১ ছবি URL এখানে পরিবর্তন করুন -->
                    <img class="w-full h-56 object-cover rounded-xl transition duration-500 group-hover:opacity-80"
                        src="https://images.unsplash.com/photo-1582270966779-1af489816f06?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w0NDUyMnwwfDF8c2VhcmNofDZ8fGJsYWNrJTIwdC1zaGlydHxlbnwwfHx8fDE3MjcxNzIyNzZ8MA&ixlib=rb-4.0.3&q=80&w=400" alt="Product A">
                    <h3 class="text-xl font-bold text-white">প্রিমিয়াম কটন টি-শার্ট</h3>
                    
                    <!-- Star Rating -->
                    <div class="flex items-center space-x-1">
                        <span class="text-accent-gold">★</span>
                        <span class="text-accent-gold">★</span>
                        <span class="text-accent-gold">★</span>
                        <span class="text-accent-gold">★</span>
                        <span class="text-gray-500">★</span>
                        <span class="text-sm text-gray-500">(২৫)</span>
                    </div>

                    <!-- Pricing with Discount -->
                    <div class="flex items-end space-x-3">
                        <p class="text-2xl text-primary-brand font-extrabold">৳ ১,০২০</p>
                        <p class="text-sm text-gray-500 line-through">৳ ১,২০০</p>
                    </div>

                    <button onclick="addToCart(1, 'প্রিমিয়াম কটন টি-শার্ট', 1020)" class="w-full py-3 mt-2 bg-primary-brand text-white font-semibold rounded-xl hover:bg-red-800 transition transform group-hover:scale-100 scale-[0.98] duration-300 **active:scale-[0.95]**">
                        কার্টে যোগ করুন
                    </button>
                </div>

                <!-- Product 2: Regular Price (ID 2) -->
                <div class="product-card bg-card-bg rounded-2xl shadow-2xl p-4 space-y-3 border border-gray-700 hover:border-accent-gold transition duration-300 transform hover:scale-[1.02] group" data-id="2" data-name="ক্যাজুয়াল ডেনিম শার্ট" data-price="2850">
                    <!-- পণ্য ২ ছবি URL এখানে পরিবর্তন করুন -->
                    <img class="w-full h-56 object-cover rounded-xl transition duration-500 group-hover:opacity-80"
                        src="https://images.unsplash.com/photo-1580227181467-ed5b0f55e4b6?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w0NDUyMnwwfDF8c2VhcmNofDF8fGRlbmltJTIwc2hpcnR8ZW58MHx8fHwxNzI3MTcyMzAyfDA&ixlib=rb-4.0.3&q=80&w=400" alt="Product B">
                    <h3 class="text-xl font-bold text-white">ক্যাজুয়াল ডেনিম শার্ট</h3>

                    <div class="flex items-center space-x-1">
                        <span class="text-accent-gold">★</span>
                        <span class="text-accent-gold">★</span>
                        <span class="text-accent-gold">★</span>
                        <span class="text-accent-gold">★</span>
                        <span class="text-accent-gold">★</span>
                        <span class="text-sm text-gray-500">(১২)</span>
                    </div>

                    <div class="flex items-end space-x-3">
                        <p class="text-2xl text-primary-brand font-extrabold">৳ ২,৮৫০</p>
                    </div>

                    <button onclick="addToCart(2, 'ক্যাজুয়াল ডেনিম শার্ট', 2850)" class="w-full py-3 mt-2 bg-primary-brand text-white font-semibold rounded-xl hover:bg-red-800 transition transform group-hover:scale-100 scale-[0.98] duration-300 **active:scale-[0.95]**">
                        কার্টে যোগ করুন
                    </button>
                </div>
                
                <!-- Product 3: MADE ACTIVE (ID 3) -->
                <div class="product-card bg-card-bg rounded-2xl shadow-2xl p-4 space-y-3 border border-gray-700 hover:border-accent-gold transition duration-300 transform hover:scale-[1.02] group" data-id="3" data-name="উলের সোয়েটার" data-price="3500">
                    <!-- পণ্য ৩ ছবি URL এখানে পরিবর্তন করুন -->
                    <img class="w-full h-56 object-cover rounded-xl transition duration-500 group-hover:opacity-80"
                        src="https://images.unsplash.com/photo-1610488057262-6af1184a44f3?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w0NDUyMnwwfDF8c2VhcmNofDZ8fGdyeSUyMHN3ZWF0ZXJ8ZW58MHx8fHwxNzI3MTcyMzQ0fDA&ixlib=rb-4.0.3&q=80&w=400" alt="Product C">
                    <h3 class="text-xl font-bold text-white">উলের সোয়েটার</h3>

                    <!-- Updated Star Rating -->
                    <div class="flex items-center space-x-1">
                        <span class="text-accent-gold">★</span>
                        <span class="text-accent-gold">★</span>
                        <span class="text-accent-gold">★</span>
                        <span class="text-accent-gold">★</span>
                        <span class="text-gray-500">★</span>
                        <span class="text-sm text-gray-500">(৫০)</span>
                    </div>
                    <div class="flex items-end space-x-3">
                        <p class="text-2xl text-primary-brand font-extrabold">৳ ৩,৫০০</p>
                    </div>

                    <!-- Updated Button (Active) -->
                    <button onclick="addToCart(3, 'উলের সোয়েটার', 3500)" class="w-full py-3 mt-2 bg-primary-brand text-white font-semibold rounded-xl hover:bg-red-800 transition transform group-hover:scale-100 scale-[0.98] duration-300 **active:scale-[0.95]**">
                        কার্টে যোগ করুন
                    </button>
                </div>

                <!-- Product 4: New Arrival (ID 4) -->
                <div class="product-card bg-card-bg rounded-2xl shadow-2xl p-4 space-y-3 border border-gray-700 hover:border-accent-gold transition duration-300 transform hover:scale-[1.02] relative group" data-id="4" data-name="ফ্যাশন ব্যাগ কালেকশন" data-price="6990">
                    <!-- New Badge -->
                    <div class="absolute top-0 right-0 bg-accent-gold text-bg-dark text-xs font-bold px-3 py-1 rounded-bl-lg rounded-tr-2xl z-10">
                        নতুন!
                    </div>
                    <!-- পণ্য ৪ ছবি URL এখানে পরিবর্তন করুন -->
                    <img class="w-full h-56 object-cover rounded-xl transition duration-500 group-hover:opacity-80"
                        src="https://images.unsplash.com/photo-1607593674609-00f727c6225a?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w0NDUyMnwwfDF8c2VhcmNofDE5fHxsZWF0aGVyJTIwYmFnfGVufDB8fHx8MTcyNzE3MjQ1Mnww&ixlib=rb-4.0.3&q=80&w=400" alt="Product D">
                    <h3 class="text-xl font-bold text-white">ফ্যাশন ব্যাগ কালেকশন</h3>
                    
                    <div class="flex items-center space-x-1">
                        <span class="text-accent-gold">★</span>
                        <span class="text-accent-gold">★</span>
                        <span class="text-accent-gold">★</span>
                        <span class="text-accent-gold">★</span>
                        <span class="text-gray-500">★</span>
                        <span class="text-sm text-gray-500">(৩)</span>
                    </div>

                    <div class="flex items-end space-x-3">
                        <p class="text-2xl text-primary-brand font-extrabold">৳ ৬,৯৯০</p>
                    </div>

                    <button onclick="addToCart(4, 'ফ্যাশন ব্যাগ কালেকশন', 6990)" class="w-full py-3 mt-2 bg-primary-brand text-white font-semibold rounded-xl hover:bg-red-800 transition transform group-hover:scale-100 scale-[0.98] duration-300 **active:scale-[0.95]**">
                        কার্টে যোগ করুন
                    </button>
                </div>
            </div>
        </section>

        <!-- BRAND STORY / ABOUT SECTION (Improved Layout and Focus) -->
        <section id="story" class="py-24 border-t border-gray-900">
            <div class="md:grid md:grid-cols-2 items-center gap-16 bg-card-bg p-12 rounded-2xl shadow-2xl border border-gray-700">
                <div class="md:order-2">
                    <!-- আমাদের গল্প/ফিলোসফি ছবি URL এখানে পরিবর্তন করুন -->
                    <img class="w-full rounded-xl shadow-xl border border-gray-800 transition duration-500 hover:shadow-accent-gold/30"
                        src="https://images.unsplash.com/photo-1507646874987-94d80a184e46?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=M3w0NDUyMnwwfDF8c2VhcmNofDV8fGNsb3RoaW5nJTIwd29ya3Nob3B8ZW58MHx8fHwxNzI3MTcyNTA3fDA&ixlib=rb-4.0.3&q=80&w=600" alt="Brand Philosophy">
                </div>
                <div class="md:order-1 mt-8 md:mt-0 space-y-6">
                    <h2 class="text-5xl font-extrabold mb-4 text-primary-brand tracking-tight">DrapeDae দর্শন</h2>
                    <p class="text-lg text-gray-300">
                        আমরা বিশ্বাস করি **ফ্যাশন কেবল পোশাক নয়**, এটি আপনার **ব্যক্তিত্ব, আরাম এবং আত্মবিশ্বাসের** প্রকাশ। আমাদের প্রতিটি ডিজাইন তৈরি হয় এই তিনটি মূল স্তম্ভকে মাথায় রেখে।
                    </p>
                    <ul class="list-disc list-inside space-y-2 text-gray-400 text-lg ml-4">
                        <li class="hover:text-white transition"><span class="text-accent-gold font-bold">উচ্চ মানের ফেব্রিক:</span> শুধুমাত্র দীর্ঘস্থায়ী এবং আরামদায়ক উপকরণ ব্যবহার।</li>
                        <li class="hover:text-white transition"><span class="text-accent-gold font-bold">সময়ের আগে ডিজাইন:</span> আন্তর্জাতিক ফ্যাশন ট্রেন্ডের সঙ্গে মিল রেখে নতুনত্ব আনা।</li>
                        <li class="hover:text-white transition"><span class="text-accent-gold font-bold">পরিবেশ-বান্ধব উৎপাদন:</span> আমাদের গ্রহের প্রতি দায়বদ্ধতা।</li>
                    </ul>
                </div>
            </div>
        </section>

        <!-- CONTACT & NEWSLETTER CTA SECTION (Sharper CTA) -->
        <section id="contact" class="py-24 border-t border-gray-900">
            <h2 class="text-4xl font-bold text-center mb-12 text-white border-b-2 border-accent-gold/50 inline-block px-4 pb-2">যোগাযোগ ও আপডেট</h2>
            <div class="max-w-xl mx-auto bg-card-bg p-10 rounded-2xl shadow-2xl border border-gray-700">
                <p class="text-center text-gray-400 mb-6 text-lg">
                    DrapeDae-এর সকল নতুন লুক, বিশেষ অফার এবং ইভেন্ট সম্পর্কে সবার আগে জানতে আমাদের টিমে যোগ দিন।
                </p>
                <!-- Form -->
                <form onsubmit="event.preventDefault(); showContactMessage();" class="space-y-6">
                    <div>
                        <label for="newsletter-email" class="block text-sm font-medium text-gray-300 mb-1">আপনার সেরা ইমেইল</label>
                        <input type="email" id="newsletter-email" required placeholder="example@email.com"
                            class="w-full px-4 py-3 bg-gray-900 border border-gray-700 rounded-xl focus:ring-primary-brand focus:border-primary-brand text-white placeholder-gray-500 transition duration-150">
                    </div>
                    <button type="submit"
                        class="w-full py-3 bg-primary-brand text-white text-lg font-bold rounded-xl shadow-lg hover:bg-red-800 transition duration-300 transform hover:scale-[1.01]">
                        DrapeDae আপডেট সাবস্ক্রাইব করুন
                    </button>
                    <!-- Message Box for Feedback -->
                    <div id="contact-message" class="hidden text-center p-3 mt-4 rounded-lg bg-green-500/20 text-green-300 font-medium" role="alert">
                        <!-- Message will be inserted here -->
                    </div>
                </form>
            </div>
        </section>

    </main>

    <!-- CHECKOUT MODAL (Hidden by default) -->
    <div id="checkout-modal" class="modal-overlay hidden">
        <div class="modal-content bg-card-bg w-full max-w-lg p-8 rounded-xl shadow-3xl border border-primary-brand/50">
            <div class="flex justify-between items-center mb-6 border-b border-gray-700 pb-4">
                <h3 class="text-3xl font-extrabold text-white">কার্ট এবং চেকআউট</h3>
                <button onclick="closeCheckoutModal()" class="text-gray-400 hover:text-primary-brand transition">
                    <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path></svg>
                </button>
            </div>
            
            <div id="cart-summary">
                <!-- Cart items will be listed here by JS -->
                <p id="empty-cart-message" class="text-center text-xl text-gray-500 py-8 hidden">আপনার কার্ট খালি। কিছু পণ্য যোগ করুন!</p>
            </div>

            <div id="checkout-form-container" class="mt-8 pt-6 border-t border-gray-700 hidden">
                <h4 class="text-xl font-bold mb-4 text-primary-brand">আপনার যোগাযোগের তথ্য</h4>
                <form id="checkout-form" onsubmit="event.preventDefault(); placeOrder()">
                    <div class="space-y-4">
                        <div>
                            <label for="customer-name" class="block text-sm font-medium text-gray-300 mb-1">সম্পূর্ণ নাম</label>
                            <input type="text" id="customer-name" required placeholder="আপনার নাম"
                                class="w-full px-4 py-3 bg-gray-900 border border-gray-700 rounded-lg focus:ring-accent-gold focus:border-accent-gold text-white">
                        </div>
                        <div>
                            <label for="customer-phone" class="block text-sm font-medium text-gray-300 mb-1">ফোন নম্বর (WhatsApp)</label>
                            <input type="tel" id="customer-phone" required placeholder="+8801XXXXXXXXX"
                                class="w-full px-4 py-3 bg-gray-900 border border-gray-700 rounded-lg focus:ring-accent-gold focus:border-accent-gold text-white">
                        </div>
                        <div>
                            <label for="customer-address" class="block text-sm font-medium text-gray-300 mb-1">ডেলিভারি ঠিকানা</label>
                            <textarea id="customer-address" required rows="3" placeholder="জেলা, থানা, বিস্তারিত ঠিকানা"
                                class="w-full px-4 py-3 bg-gray-900 border border-gray-700 rounded-lg focus:ring-accent-gold focus:border-accent-gold text-white"></textarea>
                        </div>
                    </div>

                    <div class="mt-6 p-4 rounded-xl bg-primary-brand/20 border border-primary-brand text-white">
                        <p class="font-bold text-xl mb-2">মোট মূল্য: <span id="cart-total" class="text-accent-gold">৳ ০</span></p>
                        <p class="text-sm">দ্রষ্টব্য: এই মূল্যের সাথে ডেলিভারি চার্জ প্রযোজ্য হতে পারে।</p>
                    </div>

                    <button type="submit"
                        class="w-full py-3 mt-6 bg-primary-brand text-white text-xl font-bold rounded-xl hover:bg-red-800 transition transform shadow-xl">
                        WhatsApp-এ অর্ডার করুন
                    </button>
                </form>
            </div>

        </div>
    </div>

    <!-- FOOTER -->
    <footer class="mt-20 py-8 border-t border-gray-800 text-center bg-gray-900">
        <p class="text-gray-500 text-sm">&copy; <span id="year"></span> DrapeDae. সকল অধিকার সংরক্ষিত।</p>
        <div class="flex justify-center space-x-6 mt-3 text-lg">
            <a href="#" class="text-gray-400 hover:text-primary-brand transition">Facebook</a>
            <a href="#" class="text-gray-400 hover:text-primary-brand transition">Instagram</a>
            <a href="#" class="text-gray-400 hover:text-primary-brand transition">TikTok</a>
        </div>
    </footer>

    <!-- JavaScript for dynamic functionality and WhatsApp order -->
    <script>
        // --- CONFIGURATION ---
        // !!! এখানে আপনার WhatsApp নম্বরটি দিন (কান্ট্রি কোড সহ, কোনো চিহ্ন বা স্পেস ছাড়া) !!!
        const WHATSAPP_NUMBER = "8801340109330"; 
        // Example: "8801700000000" (Replace X's with your actual number)

        let cartItems = []; // Array to store {id, name, price, quantity} objects
        const TAX = 0; // Assuming tax is included or zero for simplicity
        const DELIVERY_CHARGE = 100; // Fixed delivery charge (৳ 100)

        // Set current year in footer
        document.getElementById('year').textContent = new Date().getFullYear();

        /**
         * Updates the cart count shown in the navigation bar.
         */
        function updateCartCount() {
            const totalItems = cartItems.reduce((sum, item) => sum + item.quantity, 0);
            document.getElementById('cart-count').textContent = totalItems;
        }

        /**
         * Adds an item to the cart or increments its quantity if it already exists.
         * @param {number} id - Product ID.
         * @param {string} name - Product name.
         * @param {number} price - Product price.
         */
        function addToCart(id, name, price) {
            const existingItem = cartItems.find(item => item.id === id);
            const cartButton = document.getElementById('open-cart-btn'); // Get the cart button

            if (existingItem) {
                existingItem.quantity += 1;
            } else {
                cartItems.push({ id, name, price, quantity: 1 });
            }

            updateCartCount();
            
            // 1. Trigger the Cart Pulse Animation
            cartButton.classList.remove('btn-pulse');
            // Force reflow/repaint to restart the animation
            void cartButton.offsetWidth; 
            cartButton.classList.add('btn-pulse');


            // 2. Show confirmation message (using contact-message element temporarily)
            const msgBox = document.getElementById('contact-message');
            msgBox.textContent = `${name} কার্টে যোগ করা হয়েছে (${existingItem ? existingItem.quantity : 1}টি)!`;
            msgBox.classList.remove('hidden', 'bg-green-500/20', 'text-green-300');
            msgBox.classList.add('bg-accent-gold/20', 'text-accent-gold');
            
            setTimeout(() => {
                msgBox.classList.add('hidden');
            }, 3000);
        }

        /**
         * Renders the current cart summary inside the modal.
         */
        function renderCartSummary() {
            const summaryDiv = document.getElementById('cart-summary');
            const totalDiv = document.getElementById('cart-total');
            const formContainer = document.getElementById('checkout-form-container');
            const emptyMsg = document.getElementById('empty-cart-message');

            summaryDiv.innerHTML = ''; // Clear previous content

            if (cartItems.length === 0) {
                emptyMsg.classList.remove('hidden');
                formContainer.classList.add('hidden');
                totalDiv.textContent = '৳ ০';
                return;
            }

            emptyMsg.classList.add('hidden');
            formContainer.classList.remove('hidden');

            let subtotal = 0;

            const listHtml = cartItems.map(item => {
                const itemTotal = item.price * item.quantity;
                subtotal += itemTotal;
                return `
                    <div class="flex justify-between items-center py-3 border-b border-gray-800">
                        <div class="flex flex-col">
                            <span class="font-semibold text-white">${item.name}</span>
                            <span class="text-sm text-gray-500">৳ ${item.price} x ${item.quantity}</span>
                        </div>
                        <div class="flex items-center space-x-3">
                            <span class="text-primary-brand font-bold">৳ ${itemTotal}</span>
                            <button onclick="removeItem(${item.id})" class="text-gray-500 hover:text-red-500 transition focus:outline-none">
                                <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16"></path></svg>
                            </button>
                        </div>
                    </div>
                `;
            }).join('');

            const finalTotal = subtotal + DELIVERY_CHARGE + TAX;
            
            // Add subtotal, delivery and final total lines
            const totalsHtml = `
                <div class="mt-4 space-y-2 text-lg text-gray-300">
                    <div class="flex justify-between">
                        <span>সাবটোটাল:</span>
                        <span class="font-medium">৳ ${subtotal}</span>
                    </div>
                    <div class="flex justify-between border-b border-gray-800 pb-2">
                        <span>ডেলিভারি চার্জ:</span>
                        <span class="font-medium text-accent-gold">৳ ${DELIVERY_CHARGE}</span>
                    </div>
                    <div class="flex justify-between pt-2 text-2xl font-extrabold text-white">
                        <span>মোট (ডেলিভারি সহ):</span>
                        <span class="text-primary-brand">৳ ${finalTotal}</span>
                    </div>
                </div>
            `;

            summaryDiv.innerHTML = listHtml + totalsHtml;
            totalDiv.textContent = `৳ ${finalTotal}`;
        }

        /**
         * Removes an item from the cart.
         * @param {number} id - Product ID to remove.
         */
        function removeItem(id) {
            cartItems = cartItems.filter(item => item.id !== id);
            updateCartCount();
            renderCartSummary();
        }

        /**
         * Opens the checkout modal and updates the cart summary.
         */
        function openCheckoutModal() {
            renderCartSummary();
            document.getElementById('checkout-modal').classList.remove('hidden');
        }

        /**
         * Closes the checkout modal.
         */
        function closeCheckoutModal() {
            document.getElementById('checkout-modal').classList.add('hidden');
        }

        /**
         * Generates the WhatsApp link with order details and redirects.
         */
        function placeOrder() {
            if (cartItems.length === 0) {
                // Use the contact message box for feedback
                const msgBox = document.getElementById('contact-message');
                msgBox.textContent = `অর্ডার করতে অনুগ্রহ করে কার্টে পণ্য যোগ করুন।`;
                msgBox.classList.remove('hidden', 'bg-green-500/20', 'text-green-300');
                msgBox.classList.add('bg-primary-brand/20', 'text-primary-brand');
                setTimeout(() => msgBox.classList.add('hidden'), 5000);
                return;
            }

            const name = document.getElementById('customer-name').value;
            const phone = document.getElementById('customer-phone').value;
            const address = document.getElementById('customer-address').value;

            if (!name || !phone || !address) {
                // Use the contact message box for feedback
                const msgBox = document.getElementById('contact-message');
                msgBox.textContent = `অর্ডার করতে অনুগ্রহ করে সকল তথ্য (নাম, ফোন, ঠিকানা) পূরণ করুন।`;
                msgBox.classList.remove('hidden', 'bg-green-500/20', 'text-green-300');
                msgBox.classList.add('bg-primary-brand/20', 'text-primary-brand');
                setTimeout(() => msgBox.classList.add('hidden'), 5000);
                return;
            }


            // --- MESSAGE GENERATION ---
            let subtotal = 0;
            const orderList = cartItems.map(item => {
                const itemTotal = item.price * item.quantity;
                subtotal += itemTotal;
                return `\n- ${item.name} | পরিমাণ: ${item.quantity} | মোট: ৳ ${itemTotal}`;
            }).join('');
            
            const finalTotal = subtotal + DELIVERY_CHARGE + TAX;

            const message = 
                `*DrapeDae নতুন অর্ডার*

*গ্রাহকের তথ্য:*
নাম: ${name}
ফোন: ${phone}
ঠিকানা: ${address}

*অর্ডারের তালিকা:*
----------------------
${orderList}
----------------------

সাবটোটাল: ৳ ${subtotal}
ডেলিভারি চার্জ: ৳ ${DELIVERY_CHARGE}
মোট মূল্য: ৳ ${finalTotal}

দ্রষ্টব্য: এই মেসেজটি স্বয়ংক্রিয়ভাবে তৈরি হয়েছে। অনুগ্রহ করে নিশ্চিত করুন।`;
            
            // Encode the message for URL safety
            const encodedMessage = encodeURIComponent(message);
            
            // Generate the WhatsApp URL
            const whatsappURL = `https://wa.me/${WHATSAPP_NUMBER}?text=${encodedMessage}`;

            // Redirect to WhatsApp
            window.open(whatsappURL, '_blank');
            
            // Optional: Clear cart and close modal after successful redirection
            // Note: We don't clear the cart immediately as the user might not complete the WhatsApp send.
            // But we can notify the user that the process is initiated.
            // Using a simple alert, as custom modal implementation would be too lengthy for this context.
            alert('আপনার অর্ডার WhatsApp-এ পাঠানোর জন্য প্রস্তুত। অনুগ্রহ করে WhatsApp অ্যাপে গিয়ে মেসেজটি সেন্ড করুন।');
            closeCheckoutModal();
        }


        /**
         * Function to show a success message after newsletter form submission
         */
        function showContactMessage() {
            const email = document.getElementById('newsletter-email').value;
            const msgBox = document.getElementById('contact-message');

            msgBox.textContent = `ধন্যবাদ! ${email} ইমেইলটি DrapeDae নিউজলেটারে সাফল্যের সাথে যুক্ত করা হয়েছে।`;
            msgBox.classList.remove('hidden', 'bg-primary-brand/20', 'text-primary-brand');
            msgBox.classList.add('bg-green-500/20', 'text-green-300');

            // Clear the form after submission
            document.getElementById('newsletter-email').value = '';

            // Hide the message after 5 seconds
            setTimeout(() => {
                msgBox.classList.add('hidden');
            }, 5000);
        }
    </script>
</body>
</html>
