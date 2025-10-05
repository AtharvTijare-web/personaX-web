PersonaX-Web
<br>
Minor Project 2nd Year 2025
<br>
Repo structure
<br>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PersonaX - Scale Your Business with AI-Powered Personal Branding & Marketing</title>
    <!-- Optimized: Inline critical CSS for faster render, Tailwind purged/minified if possible, but using CDN for simplicity. In production, compile Tailwind to a single minified file. -->
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <!-- Optimized: Defer GSAP and ScrollTrigger loading -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js" defer></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js" defer></script>
    <!-- Optimized: Replaced particles.js with lightweight CSS-based ambient effect (no JS overhead). Removed particles.js entirely for speed. -->
    <style>
        /* Critical CSS inlined for above-the-fold content. Non-critical can be deferred. */
        :root {
            --primary-black: #000000;
            --accent-yellow: #FFD700;
            --gradient-multi: linear-gradient(135deg, #FFD700, #FF6B6B, #4ECDC4, #45B7D1, #96CEB4, #FFEAA7);
            --glow-yellow: 0 0 20px rgba(255, 215, 0, 0.5);
            --bg-gradient: linear-gradient(135deg, #0a0a0a 0%, #1a1a2e 50%, #16213e 100%);
        }
        body {
            background: var(--bg-gradient);
            color: white;
            font-family: 'Inter', sans-serif;
            overflow-x: hidden;
            margin: 0;
            padding: 0;
        }
        /* Optimized: Simplified animations using CSS where possible, reduced keyframes complexity. */
        .gradient-text {
            background: var(--gradient-multi);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: gradientShift 3s ease-in-out infinite;
        }
        @keyframes gradientShift {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }
        .glow-text {
            text-shadow: var(--glow-yellow);
            animation: glowPulse 2s ease-in-out infinite alternate;
        }
        @keyframes glowPulse {
            from { text-shadow: var(--glow-yellow); }
            to { text-shadow: 0 0 30px rgba(255, 215, 0, 0.8); }
        }
        .hover-glow {
            transition: all 0.3s ease;
        }
        .hover-glow:hover {
            box-shadow: var(--glow-yellow), 0 0 40px rgba(255, 215, 0, 0.3);
            transform: translateY(-5px);
        }
        .highlight-line {
            background: linear-gradient(90deg, transparent 0%, var(--accent-yellow) 50%, transparent 100%);
            background-size: 0% 2px;
            background-repeat: no-repeat;
            background-position: bottom;
            transition: background-size 0.5s ease;
        }
        .highlight-line:hover {
            background-size: 100% 2px;
        }
        /* Optimized: CSS-only ambient background with subtle animation (no JS library). Uses CSS gradients and transforms for low CPU usage. */
        .ambient-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            z-index: -1;
            opacity: 0.05;
            background: radial-gradient(circle at 20% 80%, rgba(255, 215, 0, 0.1) 0%, transparent 50%),
                        radial-gradient(circle at 80% 20%, rgba(255, 107, 107, 0.1) 0%, transparent 50%),
                        radial-gradient(circle at 40% 40%, rgba(78, 205, 196, 0.1) 0%, transparent 50%);
            animation: ambientFloat 20s ease-in-out infinite;
        }
        @keyframes ambientFloat {
            0%, 100% { transform: translate(0, 0) rotate(0deg); }
            33% { transform: translate(10px, -10px) rotate(1deg); }
            66% { transform: translate(-10px, 10px) rotate(-1deg); }
        }
        .pain-point {
            background: rgba(255, 215, 0, 0.1);
            border-left: 4px solid var(--accent-yellow);
            padding: 1rem;
            margin: 1rem 0;
            border-radius: 0 8px 8px 0;
        }
        .challenge-solved {
            font-weight: bold;
            color: var(--accent-yellow);
        }
        /* Optimized: CSS transitions for fade-in instead of heavy JS animations where possible. GSAP only for scroll-triggered ones. */
        .fade-in {
            opacity: 0;
            transform: translateY(50px);
            transition: all 0.8s ease;
        }
        .fade-in.visible {
            opacity: 1;
            transform: translateY(0);
        }
        /* Chatbot Styles - Kept minimal */
        #chatbot {
            position: fixed;
            bottom: 20px;
            right: 20px;
            width: 300px;
            height: 400px;
            background: var(--primary-black);
            border-radius: 10px;
            box-shadow: var(--glow-yellow);
            display: none;
            flex-direction: column;
            z-index: 1000;
            overflow: hidden; /* Prevent scroll lag */
        }
        #chatbot-header {
            background: var(--gradient-multi);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            padding: 10px;
            border-radius: 10px 10px 0 0;
            text-align: center;
        }
        #chatbot-messages {
            flex: 1;
            padding: 10px;
            overflow-y: auto;
            /* Optimized: Hardware acceleration for smooth scrolling */
            transform: translateZ(0);
        }
        #chatbot-input {
            display: flex;
            padding: 10px;
            border-top: 1px solid #333;
        }
        #chatbot-input input {
            flex: 1;
            background: #333;
            border: none;
            color: white;
            padding: 5px;
            border-radius: 5px;
        }
        /* Booking Modal - Optimized for quick open/close */
        #booking-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.8);
            z-index: 2000;
            justify-content: center;
            align-items: center;
            opacity: 0;
            transition: opacity 0.3s ease;
        }
        #booking-modal.active {
            display: flex;
            opacity: 1;
        }
        .plan-card {
            background: var(--primary-black);
            border: 1px solid var(--accent-yellow);
            padding: 2rem;
            border-radius: 10px;
            text-align: center;
            max-width: 300px;
            margin: 1rem;
            transition: transform 0.3s ease;
        }
        .plan-card:hover {
            transform: scale(1.05);
        }
        .plan-name {
            font-size: 1.5rem;
            color: var(--accent-yellow);
        }
        /* Optimized: Preload fonts and critical resources */
        @font-face {
            font-family: 'Inter';
            src: url('https://fonts.googleapis.com/css2?family=Inter:wght@400;700&display=swap');
        }
    </style>
    <!-- Preconnect to CDNs for faster loading -->
    <link rel="preconnect" href="https://cdnjs.cloudflare.com">
    <link rel="preconnect" href="https://cdn.jsdelivr.net">
</head>
<body>
    <!-- Optimized: Lightweight CSS ambient background (no JS) -->
    <div class="ambient-bg"></div>

    <!-- Navigation - Kept fixed but with opacity for performance -->
    <nav class="fixed top-0 w-full bg-black bg-opacity-80 z-50 p-4">
        <div class="container mx-auto flex justify-between items-center">
            <h1 class="gradient-text text-2xl font-bold">PersonaX</h1>
            <ul class="flex space-x-6">
                <li><a href="#services" class="hover:text-yellow-400 transition">Services</a></li>
                <li><a href="#testimonials" class="hover:text-yellow-400 transition">Testimonials</a></li>
                <li><a href="#stats" class="hover:text-yellow-400 transition">Results</a></li>
                <li><a href="#booking" class="bg-yellow-500 text-black px-4 py-2 rounded hover-glow">Book Appointment</a></li>
            </ul>
        </div>
    </nav>

    <!-- Hero Section - Above-the-fold, no lazy load needed -->
    <section class="min-h-screen flex items-center justify-center relative overflow-hidden">
        <div class="container mx-auto text-center px-4 fade-in">
            <h1 class="text-6xl md:text-8xl font-bold gradient-text glow-text mb-4">
                Unlock Your <span class="highlight-line">Business Potential</span>
            </h1>
            <p class="text-xl md:text-2xl mb-8 max-w-4xl mx-auto">
                At <strong>PersonaX</strong>, we build <span class="challenge-solved">unstoppable personal brands</span> for business owners like you. Tired of struggling with inconsistent leads, manual workflows, and scaling pains? We solve that with AI-powered organic marketing, SEO mastery, and psychology-driven strategies to <span class="highlight-line">boost sales and acquire clients effortlessly</span>.
            </p>
            <div class="pain-point">
                <strong>Pain Point Solved:</strong> As a business owner, you face <em>overwhelm from manual social media management</em> and <em>low ROI on ads</em>. Our AI automates 80% of your workflow, reducing hiring needs by 50% so you can focus on growth.
            </div>
            <button onclick="openBooking()" class="bg-gradient-to-r from-yellow-500 to-orange-500 text-black px-8 py-4 rounded-full text-xl font-bold hover-glow mt-8">
                <i class="fas fa-calendar"></i> Book Free Consultation
            </button>
        </div>
    </section>

    <!-- Services Section - Lazy load via Intersection Observer in JS -->
    <section id="services" class="py-20">
        <div class="container mx-auto px-4">
            <h2 class="text-5xl font-bold text-center gradient-text mb-16 glow-text fade-in">Our AI-Powered Services</h2>
            <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
                <!-- Service 1 -->
                <div class="hover-glow p-6 rounded-lg bg-black bg-opacity-50 fade-in">
                    <i class="fas fa-user-tie text-4xl text-yellow-500 mb-4"></i>
                    <h3 class="text-2xl font-bold mb-2 gradient-text">Personal Brand Building</h3>
                    <p class="mb-4">We craft authentic personal brands that resonate with your audience, turning you into an industry authority. <span class="challenge-solved">Challenge Solved:</span> Generic branding leads to forgettable presence—ours uses psychology to create magnetic appeal.</p>
                    <div class="pain-point">
                        <strong>Key Benefit:</strong> Increase client acquisition by 3x through storytelling that builds trust.
                    </div>
                </div>
                <!-- Service 2 -->
                <div class="hover-glow p-6 rounded-lg bg-black bg-opacity-50 fade-in">
                    <i class="fas fa-chart-line text-4xl text-yellow-500 mb-4"></i>
                    <h3 class="text-2xl font-bold mb-2 gradient-text">Organic Marketing & Social Media Boost</h3>
                    <p class="mb-4">Scale organically with content strategies that go viral. SEO optimization ensures top Google rankings. <span class="highlight-line">Pain Solved:</span> Inconsistent social engagement drains time—our AI curates and posts for you.</p>
                </div>
                <!-- Service 3 -->
                <div class="hover-glow p-6 rounded-lg bg-black bg-opacity-50 fade-in">
                    <i class="fas fa-bullhorn text-4xl text-yellow-500 mb-4"></i>
                    <h3 class="text-2xl font-bold mb-2 gradient-text">Google Ads & Sales Strategies</h3>
                    <p class="mb-4">Targeted Google Ads with psychology-driven copy to convert visitors into high-ticket clients. <span class="challenge-solved">Challenge:</span> Wasted ad spend— we optimize for 40% higher ROI.</p>
                    <div class="pain-point">
                        <strong>Impact:</strong> Acquire 200+ leads/month without cold outreach.
                    </div>
                </div>
                <!-- Service 4 -->
                <div class="hover-glow p-6 rounded-lg bg-black bg-opacity-50 fade-in">
                    <i class="fas fa-brain text-4xl text-yellow-500 mb-4"></i>
                    <h3 class="text-2xl font-bold mb-2 gradient-text">Psychology-Driven Marketing</h3>
                    <p class="mb-4">Leverage behavioral science to influence decisions, boosting sales by tapping into subconscious triggers. <span class="highlight-line">Solves:</span> Low conversion rates from uninspired messaging.</p>
                </div>
                <!-- Service 5 -->
                <div class="hover-glow p-6 rounded-lg bg-black bg-opacity-50 fade-in">
                    <i class="fas fa-robot text-4xl text-yellow-500 mb-4"></i>
                    <h3 class="text-2xl font-bold mb-2 gradient-text">AI Sales Boost & Automation</h3>
                    <p class="mb-4">AI tools to personalize outreach, predict buyer behavior, and automate sales funnels. Reduce manual work by 70%. <span class="challenge-solved">Pain:</span> Overworked teams—focus on core business while AI handles the rest.</p>
                    <div class="pain-point">
                        <strong>Key Point:</strong> Cut hiring costs by automating workflows, saving $50K/year.
                    </div>
                </div>
                <!-- Service 6 -->
                <div class="hover-glow p-6 rounded-lg bg-black bg-opacity-50 fade-in">
                    <i class="fas fa-code text-4xl text-yellow-500 mb-4"></i>
                    <h3 class="text-2xl font-bold mb-2 gradient-text">Custom AI Software Development</h3>
                    <p class="mb-4">Build tailored AI solutions for your business— from chatbots to predictive analytics. <span class="highlight-line">Solves:</span> Inefficient tools that don't scale with your growth.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Stats Section -->
    <section id="stats" class="py-20 bg-black bg-opacity-20">
        <div class="container mx-auto px-4 text-center">
            <h2 class="text-5xl font-bold gradient-text mb-16 glow-text fade-in">Proven Results in 5 Years</h2>
            <div class="grid md:grid-cols-4 gap-8">
                <div class="fade-in">
                    <h3 class="text-4xl font-bold text-yellow-500">$10M+</h3>
                    <p class="text-xl">Revenue Generated for Clients</p>
                </div>
                <div class="fade-in">
                    <h3 class="text-4xl font-bold text-yellow-500">150+</h3>
                    <p class="text-xl">Brands Built & Scaled</p>
                </div>
                <div class="fade-in">
                    <h3 class="text-4xl font-bold text-yellow-500">$5M+</h3>
                    <p class="text-xl">Sales from AI Strategies</p>
                </div>
                <div class="fade-in">
                    <h3 class="text-4xl font-bold text-yellow-500">80%</h3>
                    <p class="text-xl">Workflow Automation Savings</p>
                </div>
            </div>
            <div class="pain-point mt-8 max-w-4xl mx-auto">
                <strong>Challenge Solved:</strong> Business owners often hit plateaus after 3 years—our strategies have scaled 150+ brands past $1M revenue, using AI to eliminate bottlenecks like manual content creation and lead tracking.
            </div>
        </div>
    </section>

    <!-- Testimonials Section -->
    <section id="testimonials" class="py-20">
        <div class="container mx-auto px-4">
            <h2 class="text-5xl font-bold text-center gradient-text mb-16 glow-text fade-in">What Our Clients Say</h2>
            <div class="grid md:grid-cols-3 gap-8">
                <div class="hover-glow p-6 rounded-lg bg-black bg-opacity-50 fade-in">
                    <p class="mb-4">"PersonaX transformed my personal brand—went from 0 to 500k followers in 18 months. AI automation saved me 20 hours/week!"</p>
                    <h4 class="font-bold text-yellow-500">- Sarah L., CEO TechStartup</h4>
                </div>
                <div class="hover-glow p-6 rounded-lg bg-black bg-opacity-50 fade-in">
                    <p class="mb-4">"Their psychology-driven ads boosted my sales by 300%. No more guessing—pure data and AI magic."</p>
                    <h4 class="font-bold text-yellow-500">- Mike R., E-com Owner</h4>
                </div>
                <div class="hover-glow p-6 rounded-lg bg-black bg-opacity-50

