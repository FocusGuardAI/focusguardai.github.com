<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FocusGuard - Deep Focus & Productivity App</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --matte-black: #141414;
            --deep-charcoal: #262626;
            --graphite-gray: #404040;
            --soft-beige: #F5F4ED;
            --premium-gold: #D9B85C;
            --serene-blue: #6699CC;
            --mindful-green: #4CB88C;
            --ai-purple: #9966CC;
            --challenge-blue: #3399FF;
            --shop-pink: #FF6699;
            --error-red: #CC3333;
            
            --primary: var(--matte-black);
            --secondary: var(--deep-charcoal);
            --accent: var(--premium-gold);
            --text-primary: var(--soft-beige);
            --text-secondary: rgba(245, 244, 237, 0.7);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, sans-serif;
        }

        body {
            background-color: var(--primary);
            color: var(--text-primary);
            overflow-x: hidden;
            padding-top: 80px; /* Ruimte voor vaste header */
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Header & Navigation */
        header {
            background-color: rgba(20, 20, 20, 0.95);
            padding: 15px 0;
            position: fixed;
            width: 100%;
            z-index: 1000;
            backdrop-filter: blur(10px);
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            top: 0;
            left: 0;
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .logo-icon {
            font-size: 24px;
            color: var(--accent);
        }

        .logo-text {
            font-size: 24px;
            font-weight: 700;
            letter-spacing: 1px;
        }

        .nav-links {
            display: flex;
            gap: 30px;
        }

        .nav-link {
            color: var(--text-primary);
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s;
            position: relative;
            font-size: 16px;
        }

        .nav-link:hover {
            color: var(--accent);
        }

        .nav-link::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background-color: var(--accent);
            transition: width 0.3s;
        }

        .nav-link:hover::after {
            width: 100%;
        }

        .cta-button {
            background: linear-gradient(135deg, var(--accent), rgba(217, 184, 92, 0.8));
            color: var(--primary);
            border: none;
            padding: 12px 24px;
            border-radius: 20px;
            font-weight: 600;
            cursor: pointer;
            transition: transform 0.2s, box-shadow 0.2s;
            box-shadow: 0 5px 15px rgba(217, 184, 92, 0.3);
            font-size: 16px;
        }

        .cta-button:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 20px rgba(217, 184, 92, 0.4);
        }

        /* Hero Section */
        .hero {
            padding: 100px 0 80px;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(217, 184, 92, 0.1) 0%, rgba(20, 20, 20, 0) 70%);
            z-index: -1;
        }

        .hero h1 {
            font-size: 56px;
            font-weight: 300;
            margin-bottom: 20px;
            letter-spacing: 2px;
        }

        .hero p {
            font-size: 20px;
            color: var(--text-secondary);
            max-width: 600px;
            margin: 0 auto 40px;
            line-height: 1.6;
        }

        .hero-buttons {
            display: flex;
            gap: 20px;
            justify-content: center;
            margin-top: 40px;
        }

        .secondary-button {
            background: transparent;
            color: var(--accent);
            border: 2px solid var(--accent);
            padding: 12px 24px;
            border-radius: 20px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
        }

        .secondary-button:hover {
            background-color: rgba(217, 184, 92, 0.1);
        }

        /* Glassmorphism Panel */
        .glass-panel {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(10px);
            border-radius: 24px;
            padding: 30px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            position: relative;
            overflow: hidden;
        }

        .glass-panel::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 1px;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
        }

        /* Section Styling */
        section {
            padding: 80px 0;
        }

        .section-header {
            text-align: center;
            margin-bottom: 60px;
        }

        .section-title {
            font-size: 42px;
            font-weight: 300;
            margin-bottom: 20px;
            letter-spacing: 1px;
        }

        .section-subtitle {
            font-size: 18px;
            color: var(--text-secondary);
            max-width: 600px;
            margin: 0 auto;
            line-height: 1.6;
        }

        /* Features Grid */
        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }

        .feature-card {
            height: 100%;
            transition: transform 0.3s;
        }

        .feature-card:hover {
            transform: translateY(-10px);
        }

        .feature-icon {
            font-size: 40px;
            margin-bottom: 20px;
            color: var(--accent);
        }

        .feature-title {
            font-size: 24px;
            margin-bottom: 15px;
            font-weight: 600;
        }

        .feature-description {
            color: var(--text-secondary);
            line-height: 1.6;
        }

        /* Timer Demo */
        .timer-demo {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 40px;
        }

        .timer-circle {
            width: 300px;
            height: 300px;
            border-radius: 50%;
            background: conic-gradient(var(--accent) 0%, var(--secondary) 0%);
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            transition: background 1s ease;
        }

        .timer-circle::before {
            content: '';
            position: absolute;
            width: 270px;
            height: 270px;
            border-radius: 50%;
            background-color: var(--secondary);
        }

        .timer-display {
            position: relative;
            z-index: 1;
            text-align: center;
        }

        .timer-time {
            font-size: 48px;
            font-weight: 300;
            margin-bottom: 10px;
        }

        .timer-state {
            font-size: 18px;
            color: var(--text-secondary);
            letter-spacing: 2px;
        }

        .timer-controls {
            display: flex;
            gap: 15px;
        }

        .timer-button {
            padding: 12px 24px;
            border-radius: 20px;
            border: none;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
        }

        .timer-start {
            background-color: var(--mindful-green);
            color: white;
        }

        .timer-pause {
            background-color: var(--serene-blue);
            color: white;
        }

        .timer-stop {
            background-color: var(--error-red);
            color: white;
        }

        /* Screenshots */
        .screenshots {
            display: flex;
            justify-content: center;
            gap: 30px;
            flex-wrap: wrap;
        }

        .screenshot {
            width: 250px;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.3);
            transition: transform 0.3s;
        }

        .screenshot:hover {
            transform: translateY(-10px);
        }

        .screenshot img {
            width: 100%;
            height: auto;
            display: block;
        }

        /* FAQ */
        .faq-grid {
            max-width: 800px;
            margin: 0 auto;
        }

        .faq-item {
            margin-bottom: 20px;
        }

        .faq-question {
            font-size: 18px;
            font-weight: 600;
            margin-bottom: 10px;
            cursor: pointer;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .faq-answer {
            color: var(--text-secondary);
            line-height: 1.6;
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.3s ease;
        }

        .faq-item.active .faq-answer {
            max-height: 200px;
        }

        /* Download Section */
        .download-section {
            text-align: center;
            padding: 80px 0;
            background: linear-gradient(135deg, var(--primary), var(--deep-charcoal));
        }

        .download-options {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 40px;
            flex-wrap: wrap;
        }

        .download-button {
            display: flex;
            align-items: center;
            gap: 10px;
            padding: 15px 30px;
            border-radius: 12px;
            background: var(--secondary);
            color: var(--text-primary);
            text-decoration: none;
            font-weight: 600;
            transition: transform 0.3s, background 0.3s;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .download-button:hover {
            transform: translateY(-5px);
            background: var(--deep-charcoal);
        }

        .download-button i {
            font-size: 24px;
        }

        /* Footer */
        footer {
            background-color: var(--secondary);
            padding: 60px 0 30px;
        }

        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 40px;
            margin-bottom: 40px;
        }

        .footer-column h3 {
            font-size: 18px;
            margin-bottom: 20px;
            position: relative;
        }

        .footer-column h3::after {
            content: '';
            position: absolute;
            bottom: -8px;
            left: 0;
            width: 30px;
            height: 2px;
            background-color: var(--accent);
        }

        .footer-links {
            list-style: none;
        }

        .footer-links li {
            margin-bottom: 10px;
        }

        .footer-links a {
            color: var(--text-secondary);
            text-decoration: none;
            transition: color 0.3s;
        }

        .footer-links a:hover {
            color: var(--accent);
        }

        .social-links {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }

        .social-link {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background-color: rgba(255, 255, 255, 0.1);
            display: flex;
            align-items: center;
            justify-content: center;
            transition: background-color 0.3s;
        }

        .social-link:hover {
            background-color: var(--accent);
        }

        .copyright {
            text-align: center;
            padding-top: 30px;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            color: var(--text-secondary);
            font-size: 14px;
        }

        /* Privacy Policy Section */
        .privacy-content {
            max-width: 800px;
            margin: 0 auto;
        }

        .privacy-section {
            margin-bottom: 40px;
        }

        .privacy-section h3 {
            font-size: 22px;
            margin-bottom: 15px;
            color: var(--accent);
        }

        .privacy-section p {
            color: var(--text-secondary);
            line-height: 1.6;
            margin-bottom: 15px;
        }

        .privacy-section ul {
            color: var(--text-secondary);
            margin-left: 20px;
            margin-bottom: 15px;
        }

        .privacy-section li {
            margin-bottom: 8px;
            line-height: 1.5;
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            body {
                padding-top: 70px;
            }
            
            header {
                padding: 12px 0;
            }
            
            .nav-links {
                display: none;
            }

            .hero h1 {
                font-size: 36px;
            }

            .hero p {
                font-size: 16px;
            }

            .hero-buttons {
                flex-direction: column;
                align-items: center;
            }

            .section-title {
                font-size: 32px;
            }
            
            .download-options {
                flex-direction: column;
                align-items: center;
            }
            
            .download-button {
                width: 100%;
                max-width: 300px;
                justify-content: center;
            }
        }
        
        /* Mobile Menu */
        .mobile-menu-button {
            display: none;
            background: none;
            border: none;
            color: var(--text-primary);
            font-size: 24px;
            cursor: pointer;
        }
        
        @media (max-width: 768px) {
            .mobile-menu-button {
                display: block;
            }
            
            .nav-links.active {
                display: flex;
                flex-direction: column;
                position: absolute;
                top: 100%;
                left: 0;
                width: 100%;
                background: rgba(20, 20, 20, 0.95);
                backdrop-filter: blur(10px);
                padding: 20px;
                gap: 15px;
                border-top: 1px solid rgba(255, 255, 255, 0.1);
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="container">
            <nav>
                <div class="logo">
                    <div class="logo-icon">
                        <i class="fas fa-brain"></i>
                    </div>
                    <div class="logo-text">FocusGuard</div>
                </div>
                <button class="mobile-menu-button" id="mobileMenuButton">
                    <i class="fas fa-bars"></i>
                </button>
                <div class="nav-links" id="navLinks">
                    <a href="#features" class="nav-link">Features</a>
                    <a href="#how-it-works" class="nav-link">How It Works</a>
                    <a href="#download" class="nav-link">Download</a>
                    <a href="#privacy-policy" class="nav-link">Privacy</a>
                </div>
                <button class="cta-button">Get Started</button>
            </nav>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="hero">
        <div class="container">
            <h1>Master Your Focus,<br>Unlock Your Potential</h1>
            <p>FocusGuard combines cutting-edge productivity techniques with engaging gamification to help you achieve deep focus and accomplish your most important work.</p>
            <div class="hero-buttons">
                <button class="cta-button">
                    <i class="fab fa-apple"></i> Download Now
                </button>
                <button class="secondary-button">Watch Demo</button>
            </div>
        </div>
    </section>

    <!-- Features Section -->
    <section id="features">
        <div class="container">
            <div class="section-header">
                <h2 class="section-title">Powerful Features</h2>
                <p class="section-subtitle">Everything you need to eliminate distractions and build consistent focus habits</p>
            </div>
            <div class="features-grid">
                <div class="glass-panel feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-clock"></i>
                    </div>
                    <h3 class="feature-title">Smart Focus Timer</h3>
                    <p class="feature-description">Customizable Pomodoro timer with adaptive sessions that learn your focus patterns and optimize break times.</p>
                </div>
                <div class="glass-panel feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-robot"></i>
                    </div>
                    <h3 class="feature-title">AI Assistant</h3>
                    <p class="feature-description">Get personalized productivity advice, focus techniques, and motivation from our intelligent AI coach.</p>
                </div>
                <div class="glass-panel feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-shield-alt"></i>
                    </div>
                    <h3 class="feature-title">App Blocking</h3>
                    <p class="feature-description">Automatically block distracting apps and websites during focus sessions using iOS Screen Time integration.</p>
                </div>
                <div class="glass-panel feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-chart-line"></i>
                    </div>
                    <h3 class="feature-title">Progress Tracking</h3>
                    <p class="feature-description">Comprehensive analytics and insights into your focus patterns, streaks, and productivity trends.</p>
                </div>
                <div class="glass-panel feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-trophy"></i>
                    </div>
                    <h3 class="feature-title">Gamification</h3>
                    <p class="feature-description">Earn rewards, complete challenges, and level up your focus pet as you build consistent habits.</p>
                </div>
                <div class="glass-panel feature-card">
                    <div class="feature-icon">
                        <i class="fas fa-palette"></i>
                    </div>
                    <h3 class="feature-title">Custom Themes</h3>
                    <p class="feature-description">Personalize your experience with multiple premium themes including dark, light, gold, and more.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Timer Demo Section -->
    <section id="how-it-works" style="background-color: var(--secondary);">
        <div class="container">
            <div class="section-header">
                <h2 class="section-title">Experience Deep Focus</h2>
                <p class="section-subtitle">Try our interactive timer to see how FocusGuard helps you maintain concentration</p>
            </div>
            <div class="timer-demo">
                <div class="glass-panel" style="padding: 50px;">
                    <div class="timer-circle" id="timerCircle">
                        <div class="timer-display">
                            <div class="timer-time" id="timerTime">25:00</div>
                            <div class="timer-state" id="timerState">READY TO FOCUS</div>
                        </div>
                    </div>
                </div>
                <div class="timer-controls">
                    <button class="timer-button timer-start" id="startTimer">Start Focus</button>
                    <button class="timer-button timer-pause" id="pauseTimer">Pause</button>
                    <button class="timer-button timer-stop" id="stopTimer">Stop</button>
                </div>
            </div>
        </div>
    </section>

    <!-- Screenshots Section -->
    <section style="background-color: var(--secondary);">
        <div class="container">
            <div class="section-header">
                <h2 class="section-title">Beautiful Interface</h2>
                <p class="section-subtitle">Designed for clarity, focus, and premium user experience</p>
            </div>
            <div class="screenshots">
                <!-- These would be actual screenshots in a real implementation -->
                <div class="screenshot">
                    <div style="width:100%;height:500px;background:linear-gradient(135deg, var(--primary), var(--graphite-gray));border-radius:20px;display:flex;flex-direction:column;justify-content:center;align-items:center;padding:30px;">
                        <div style="width:80%;height:60px;background:var(--accent);border-radius:15px;margin-bottom:20px;"></div>
                        <div style="width:90%;height:200px;background:var(--deep-charcoal);border-radius:15px;margin-bottom:20px;"></div>
                        <div style="width:70%;height:40px;background:var(--mindful-green);border-radius:10px;"></div>
                    </div>
                </div>
                <div class="screenshot">
                    <div style="width:100%;height:500px;background:linear-gradient(135deg, var(--primary), var(--graphite-gray));border-radius:20px;display:flex;flex-direction:column;justify-content:center;align-items:center;padding:30px;">
                        <div style="width:200px;height:200px;border-radius:50%;border:5px solid var(--accent);margin-bottom:20px;display:flex;align-items:center;justify-content:center;font-size:36px;">25:00</div>
                        <div style="width:90%;height:40px;background:var(--deep-charcoal);border-radius:10px;margin-bottom:10px;"></div>
                        <div style="width:70%;height:40px;background:var(--serene-blue);border-radius:10px;"></div>
                    </div>
                </div>
                <div class="screenshot">
                    <div style="width:100%;height:500px;background:linear-gradient(135deg, var(--primary), var(--graphite-gray));border-radius:20px;display:flex;flex-direction:column;justify-content:center;align-items:center;padding:30px;">
                        <div style="width:80%;height:40px;background:var(--accent);border-radius:10px;margin-bottom:15px;"></div>
                        <div style="width:90%;height:30px;background:var(--deep-charcoal);border-radius:5px;margin-bottom:10px;"></div>
                        <div style="width:90%;height:30px;background:var(--deep-charcoal);border-radius:5px;margin-bottom:10px;"></div>
                        <div style="width:90%;height:30px;background:var(--deep-charcoal);border-radius:5px;margin-bottom:10px;"></div>
                        <div style="width:60%;height:100px;background:var(--ai-purple);border-radius:15px;margin-top:20px;"></div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Download Section -->
    <section id="download" class="download-section">
        <div class="container">
            <div class="section-header">
                <h2 class="section-title">Get FocusGuard Today</h2>
                <p class="section-subtitle">Start your journey to better focus and productivity</p>
            </div>
            <div class="download-options">
                <a href="#" class="download-button">
                    <i class="fab fa-apple"></i>
                    <div>
                        <div style="font-size: 14px;">Download on the</div>
                        <div>App Store</div>
                    </div>
                </a>
                <a href="#" class="download-button">
                    <i class="fab fa-google-play"></i>
                    <div>
                        <div style="font-size: 14px;">Get it on</div>
                        <div>Google Play</div>
                    </div>
                </a>
            </div>
        </div>
    </section>

    <!-- Privacy Policy Section -->
    <section id="privacy-policy">
        <div class="container">
            <div class="section-header">
                <h2 class="section-title">Privacy Policy</h2>
                <p class="section-subtitle">Your privacy is important to us. Learn how we protect your data.</p>
            </div>
            <div class="privacy-content">
                <div class="glass-panel">
                    <div class="privacy-section">
                        <h3>Data Collection and Use</h3>
                        <p>FocusGuard is designed with your privacy in mind. We collect minimal data necessary to provide our services:</p>
                        <ul>
                            <li>Focus session data (duration, type, completion status) to track your progress</li>
                            <li>App usage statistics to improve our features and user experience</li>
                            <li>Optional account information if you choose to create an account</li>
                        </ul>
                        <p>We do not sell your personal data to third parties. Your focus data is used solely to provide you with insights and improve your productivity experience.</p>
                    </div>
                    
                    <div class="privacy-section">
                        <h3>Data Storage and Security</h3>
                        <p>Your data is stored securely on encrypted servers. We implement industry-standard security measures to protect your information from unauthorized access, alteration, or destruction.</p>
                        <p>Focus session data is primarily stored locally on your device. Cloud synchronization is optional and requires your explicit consent.</p>
                    </div>
                    
                    <div class="privacy-section">
                        <h3>Third-Party Services</h3>
                        <p>FocusGuard may integrate with third-party services for specific functionality:</p>
                        <ul>
                            <li>Analytics services to understand app performance and usage patterns</li>
                            <li>Cloud storage providers for optional data synchronization</li>
                            <li>Payment processors for premium features (if applicable)</li>
                        </ul>
                        <p>All third-party services are carefully vetted to ensure they meet our privacy standards.</p>
                    </div>
                    
                    <div class="privacy-section">
                        <h3>Your Rights</h3>
                        <p>You have the right to:</p>
                        <ul>
                            <li>Access the personal data we hold about you</li>
                            <li>Request correction of inaccurate data</li>
                            <li>Request deletion of your data</li>
                            <li>Export your data in a portable format</li>
                            <li>Opt out of non-essential data collection</li>
                        </ul>
                        <p>To exercise any of these rights, please contact us at privacy@focusguard.app.</p>
                    </div>
                    
                    <div class="privacy-section">
                        <h3>Policy Updates</h3>
                        <p>We may update this privacy policy from time to time. We will notify you of any significant changes through the app or via email. Continued use of FocusGuard after changes constitutes acceptance of the updated policy.</p>
                        <p><strong>Last updated:</strong> January 2025</p>
                    </div>
                    
                    <div class="privacy-section">
                        <h3>Contact Us</h3>
                        <p>If you have any questions about our privacy practices or this policy, please contact our privacy team at:</p>
                        <p>Email: privacy@focusguard.app</p>
                        <p>Address: FocusGuard Privacy Team, 123 Productivity Lane, San Francisco, CA 94105</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- FAQ Section -->
    <section>
        <div class="container">
            <div class="section-header">
                <h2 class="section-title">Frequently Asked Questions</h2>
                <p class="section-subtitle">Everything you need to know about FocusGuard</p>
            </div>
            <div class="faq-grid">
                <div class="glass-panel faq-item">
                    <div class="faq-question">
                        How does the app blocking work?
                        <i class="fas fa-chevron-down"></i>
                    </div>
                    <div class="faq-answer">
                        FocusGuard uses iOS Screen Time APIs to temporarily block distracting apps and websites during your focus sessions. You select which apps to block, and FocusGuard automatically enables blocking when you start a session.
                    </div>
                </div>
                <div class="glass-panel faq-item">
                    <div class="faq-question">
                        Is my data private and secure?
                        <i class="fas fa-chevron-down"></i>
                    </div>
                    <div class="faq-answer">
                        Yes, we take privacy seriously. All your focus data is stored locally on your device and is never shared with third parties without your explicit permission. For more details, see our <a href="#privacy-policy" style="color: var(--accent);">Privacy Policy</a>.
                    </div>
                </div>
                <div class="glass-panel faq-item">
                    <div class="faq-question">
                        Can I use FocusGuard on multiple devices?
                        <i class="fas fa-chevron-down"></i>
                    </div>
                    <div class="faq-answer">
                        Currently, FocusGuard is only available for iOS devices. We're working on a macOS version that will sync with your iOS device for a seamless experience across Apple devices.
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="footer-column">
                    <h3>FocusGuard</h3>
                    <p style="color: var(--text-secondary); line-height: 1.6; margin-bottom: 20px;">The ultimate app for deep focus and productivity, combining cutting-edge techniques with engaging gamification.</p>
                    <div class="social-links">
                        <a href="#" class="social-link"><i class="fab fa-twitter"></i></a>
                        <a href="#" class="social-link"><i class="fab fa-instagram"></i></a>
                        <a href="#" class="social-link"><i class="fab fa-facebook-f"></i></a>
                    </div>
                </div>
                <div class="footer-column">
                    <h3>Product</h3>
                    <ul class="footer-links">
                        <li><a href="#features">Features</a></li>
                        <li><a href="#how-it-works">How It Works</a></li>
                        <li><a href="#download">Download</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>Company</h3>
                    <ul class="footer-links">
                        <li><a href="#">About Us</a></li>
                        <li><a href="#">Careers</a></li>
                        <li><a href="#">Contact</a></li>
                        <li><a href="#">Blog</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>Legal</h3>
                    <ul class="footer-links">
                        <li><a href="#privacy-policy">Privacy Policy</a></li>
                        <li><a href="#">Terms of Service</a></li>
                        <li><a href="#">Cookie Policy</a></li>
                    </ul>
                </div>
            </div>
            <div class="copyright">
                &copy; 2025 FocusGuard. All rights reserved.
            </div>
        </div>
    </footer>

    <script>
        // Timer functionality
        let timerInterval;
        let timeLeft = 25 * 60; // 25 minutes in seconds
        let isRunning = false;
        
        const timerCircle = document.getElementById('timerCircle');
        const timerTime = document.getElementById('timerTime');
        const timerState = document.getElementById('timerState');
        const startButton = document.getElementById('startTimer');
        const pauseButton = document.getElementById('pauseTimer');
        const stopButton = document.getElementById('stopTimer');
        
        function updateTimer() {
            const minutes = Math.floor(timeLeft / 60);
            const seconds = timeLeft % 60;
            timerTime.textContent = `${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
            
            const progress = 1 - (timeLeft / (25 * 60));
            timerCircle.style.background = `conic-gradient(var(--accent) ${progress * 100}%, var(--secondary) 0%)`;
            
            if (timeLeft <= 0) {
                clearInterval(timerInterval);
                isRunning = false;
                timerState.textContent = 'SESSION COMPLETE';
                timerCircle.style.background = `conic-gradient(var(--mindful-green) 100%, var(--secondary) 0%)`;
            }
        }
        
        function startTimer() {
            if (!isRunning) {
                isRunning = true;
                timerState.textContent = 'FOCUSING...';
                timerInterval = setInterval(() => {
                    timeLeft--;
                    updateTimer();
                }, 1000);
            }
        }
        
        function pauseTimer() {
            if (isRunning) {
                clearInterval(timerInterval);
                isRunning = false;
                timerState.textContent = 'PAUSED';
            }
        }
        
        function stopTimer() {
            clearInterval(timerInterval);
            isRunning = false;
            timeLeft = 25 * 60;
            timerState.textContent = 'READY TO FOCUS';
            updateTimer();
        }
        
        startButton.addEventListener('click', startTimer);
        pauseButton.addEventListener('click', pauseTimer);
        stopButton.addEventListener('click', stopTimer);
        
        // Initialize timer
        updateTimer();
        
        // FAQ accordion functionality
        const faqItems = document.querySelectorAll('.faq-item');
        
        faqItems.forEach(item => {
            const question = item.querySelector('.faq-question');
            
            question.addEventListener('click', () => {
                // Close all other items
                faqItems.forEach(otherItem => {
                    if (otherItem !== item) {
                        otherItem.classList.remove('active');
                    }
                });
                
                // Toggle current item
                item.classList.toggle('active');
            });
        });
        
        // Smooth scrolling for navigation links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                
                const targetId = this.getAttribute('href');
                if (targetId === '#') return;
                
                const targetElement = document.querySelector(targetId);
                if (targetElement) {
                    window.scrollTo({
                        top: targetElement.offsetTop - 80,
                        behavior: 'smooth'
                    });
                    
                    // Close mobile menu if open
                    navLinks.classList.remove('active');
                }
            });
        });
        
        // Mobile menu functionality
        const mobileMenuButton = document.getElementById('mobileMenuButton');
        const navLinks = document.getElementById('navLinks');
        
        mobileMenuButton.addEventListener('click', () => {
            navLinks.classList.toggle('active');
        });
        
        // Close mobile menu when clicking outside
        document.addEventListener('click', (e) => {
            if (!e.target.closest('nav') && navLinks.classList.contains('active')) {
                navLinks.classList.remove('active');
            }
        });
    </script>
</body>
</html>
