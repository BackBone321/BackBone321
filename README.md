<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Developer Profile</title>
    <link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;600;800&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary: #00F0FF;
            --secondary: #FF006E;
            --accent: #FFBE0B;
            --dark: #0A0E27;
            --light: #F0F4F8;
            --glow: rgba(0, 240, 255, 0.6);
        }

        body {
            background: linear-gradient(135deg, #0A0E27 0%, #1a1d3f 50%, #0A0E27 100%);
            color: var(--light);
            font-family: 'Space Mono', monospace;
            line-height: 1.6;
            overflow-x: hidden;
            position: relative;
        }

        /* Animated background particles */
        .particles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            z-index: 0;
            pointer-events: none;
        }

        .particle {
            position: absolute;
            background: var(--primary);
            border-radius: 50%;
            animation: float 20s infinite;
            opacity: 0.1;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0) translateX(0); }
            25% { transform: translateY(-100px) translateX(50px); }
            50% { transform: translateY(-200px) translateX(-50px); }
            75% { transform: translateY(-100px) translateX(100px); }
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 2rem;
            position: relative;
            z-index: 1;
        }

        /* Header Section */
        .header {
            text-align: center;
            padding: 4rem 0;
            position: relative;
        }

        .glitch-wrapper {
            position: relative;
            display: inline-block;
        }

        .name {
            font-family: 'Syne', sans-serif;
            font-size: clamp(3rem, 8vw, 6rem);
            font-weight: 800;
            background: linear-gradient(90deg, var(--primary), var(--secondary), var(--accent));
            background-size: 200% auto;
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: gradientShift 3s ease infinite;
            text-transform: uppercase;
            letter-spacing: -2px;
            margin-bottom: 1rem;
        }

        @keyframes gradientShift {
            0%, 100% { background-position: 0% center; }
            50% { background-position: 100% center; }
        }

        .tagline {
            font-size: clamp(1rem, 2vw, 1.5rem);
            color: var(--primary);
            letter-spacing: 4px;
            margin-bottom: 2rem;
            text-transform: uppercase;
            opacity: 0;
            animation: fadeInUp 1s ease forwards 0.3s;
        }

        @keyframes fadeInUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
            from {
                opacity: 0;
                transform: translateY(20px);
            }
        }

        /* Skills Grid */
        .section-title {
            font-family: 'Syne', sans-serif;
            font-size: clamp(2rem, 4vw, 3rem);
            font-weight: 800;
            margin: 4rem 0 2rem;
            position: relative;
            display: inline-block;
        }

        .section-title::before {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 0;
            width: 60%;
            height: 4px;
            background: linear-gradient(90deg, var(--primary), var(--secondary));
            animation: expandWidth 1s ease forwards;
        }

        @keyframes expandWidth {
            from { width: 0; }
            to { width: 60%; }
        }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
            margin: 3rem 0;
        }

        .skill-category {
            background: rgba(255, 255, 255, 0.03);
            border: 2px solid rgba(0, 240, 255, 0.2);
            border-radius: 20px;
            padding: 2rem;
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            position: relative;
            overflow: hidden;
            backdrop-filter: blur(10px);
        }

        .skill-category::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(0, 240, 255, 0.1), transparent);
            transition: left 0.6s;
        }

        .skill-category:hover::before {
            left: 100%;
        }

        .skill-category:hover {
            transform: translateY(-10px);
            border-color: var(--primary);
            box-shadow: 0 20px 60px rgba(0, 240, 255, 0.3);
        }

        .category-title {
            font-family: 'Syne', sans-serif;
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--primary);
            margin-bottom: 1.5rem;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .category-icon {
            width: 32px;
            height: 32px;
            background: var(--primary);
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.2rem;
        }

        .skill-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 0.8rem;
        }

        .skill-tag {
            background: rgba(0, 240, 255, 0.1);
            border: 1px solid var(--primary);
            padding: 0.6rem 1.2rem;
            border-radius: 50px;
            font-size: 0.9rem;
            transition: all 0.3s ease;
            cursor: pointer;
            position: relative;
            overflow: hidden;
        }

        .skill-tag::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 0;
            height: 0;
            border-radius: 50%;
            background: var(--primary);
            transition: all 0.5s ease;
            transform: translate(-50%, -50%);
        }

        .skill-tag:hover::before {
            width: 200%;
            height: 200%;
        }

        .skill-tag:hover {
            color: var(--dark);
            border-color: var(--primary);
            transform: scale(1.05);
        }

        .skill-tag span {
            position: relative;
            z-index: 1;
        }

        /* Stats Section */
        .stats-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin: 3rem 0;
        }

        .stat-card {
            background: linear-gradient(135deg, rgba(0, 240, 255, 0.1), rgba(255, 0, 110, 0.1));
            border: 2px solid rgba(255, 255, 255, 0.1);
            border-radius: 20px;
            padding: 2rem;
            text-align: center;
            position: relative;
            overflow: hidden;
            transition: all 0.4s ease;
        }

        .stat-card::after {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(0, 240, 255, 0.2), transparent);
            opacity: 0;
            transition: opacity 0.4s;
        }

        .stat-card:hover::after {
            opacity: 1;
            animation: rotate 4s linear infinite;
        }

        @keyframes rotate {
            to { transform: rotate(360deg); }
        }

        .stat-number {
            font-family: 'Syne', sans-serif;
            font-size: 3rem;
            font-weight: 800;
            background: linear-gradient(45deg, var(--primary), var(--accent));
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
            position: relative;
            z-index: 1;
        }

        .stat-label {
            color: rgba(255, 255, 255, 0.7);
            margin-top: 0.5rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            font-size: 0.9rem;
            position: relative;
            z-index: 1;
        }

        /* Contact Section */
        .contact-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1.5rem;
            margin: 3rem 0;
        }

        .contact-link {
            background: rgba(255, 255, 255, 0.05);
            border: 2px solid var(--primary);
            border-radius: 15px;
            padding: 1.5rem;
            text-align: center;
            text-decoration: none;
            color: var(--light);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .contact-link::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(0, 240, 255, 0.2), transparent);
            transition: left 0.5s;
        }

        .contact-link:hover::before {
            left: 100%;
        }

        .contact-link:hover {
            transform: translateY(-5px);
            background: rgba(0, 240, 255, 0.1);
            box-shadow: 0 10px 30px var(--glow);
        }

        .contact-icon {
            font-size: 2rem;
            margin-bottom: 0.5rem;
            display: block;
        }

        /* Footer */
        .footer {
            text-align: center;
            padding: 3rem 0;
            margin-top: 5rem;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
        }

        .footer-quote {
            font-style: italic;
            color: rgba(255, 255, 255, 0.6);
            font-size: 1.1rem;
            margin-bottom: 1rem;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .skills-grid {
                grid-template-columns: 1fr;
            }
            
            .name {
                font-size: 3rem;
            }
        }

        /* Scroll animations */
        .fade-in {
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.8s ease;
        }

        .fade-in.visible {
            opacity: 1;
            transform: translateY(0);
        }
    </style>
</head>
<body>
    <!-- Animated Background -->
    <div class="particles" id="particles"></div>

    <div class="container">
        <!-- Header -->
        <header class="header">
            <div class="glitch-wrapper">
                <h1 class="name">Your Name</h1>
            </div>
            <p class="tagline">Full-Stack Developer & Innovator</p>
        </header>

        <!-- Skills Section -->
        <section class="fade-in">
            <h2 class="section-title">⚡ Tech Arsenal</h2>
            
            <div class="skills-grid">
                <div class="skill-category">
                    <h3 class="category-title">
                        <span class="category-icon">🎨</span>
                        Frontend
                    </h3>
                    <div class="skill-tags">
                        <div class="skill-tag"><span>HTML5</span></div>
                        <div class="skill-tag"><span>CSS3</span></div>
                        <div class="skill-tag"><span>JavaScript</span></div>
                    </div>
                </div>

                <div class="skill-category">
                    <h3 class="category-title">
                        <span class="category-icon">⚙️</span>
                        Backend
                    </h3>
                    <div class="skill-tags">
                        <div class="skill-tag"><span>Python</span></div>
                        <div class="skill-tag"><span>C#</span></div>
                        <div class="skill-tag"><span>C</span></div>
                        <div class="skill-tag"><span>PHP</span></div>
                        <div class="skill-tag"><span>Node.js</span></div>
                    </div>
                </div>

                <div class="skill-category">
                    <h3 class="category-title">
                        <span class="category-icon">📱</span>
                        Mobile
                    </h3>
                    <div class="skill-tags">
                        <div class="skill-tag"><span>Dart</span></div>
                        <div class="skill-tag"><span>Flutter</span></div>
                    </div>
                </div>

                <div class="skill-category">
                    <h3 class="category-title">
                        <span class="category-icon">☁️</span>
                        Cloud & DB
                    </h3>
                    <div class="skill-tags">
                        <div class="skill-tag"><span>Firebase</span></div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Stats Section -->
        <section class="fade-in">
            <h2 class="section-title">📊 GitHub Stats</h2>
            
            <div class="stats-container">
                <div class="stat-card">
                    <div class="stat-number">500+</div>
                    <div class="stat-label">Commits</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">50+</div>
                    <div class="stat-label">Projects</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">10+</div>
                    <div class="stat-label">Languages</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">∞</div>
                    <div class="stat-label">Ideas</div>
                </div>
            </div>
        </section>

        <!-- Contact Section -->
        <section class="fade-in">
            <h2 class="section-title">🌐 Connect</h2>
            
            <div class="contact-grid">
                <a href="mailto:your.email@example.com" class="contact-link">
                    <span class="contact-icon">📧</span>
                    <div>Email</div>
                </a>
                <a href="https://linkedin.com/in/yourprofile" class="contact-link">
                    <span class="contact-icon">💼</span>
                    <div>LinkedIn</div>
                </a>
                <a href="https://github.com/yourusername" class="contact-link">
                    <span class="contact-icon">💻</span>
                    <div>GitHub</div>
                </a>
                <a href="https://twitter.com/yourhandle" class="contact-link">
                    <span class="contact-icon">🐦</span>
                    <div>Twitter</div>
                </a>
            </div>
        </section>

        <!-- Footer -->
        <footer class="footer">
            <p class="footer-quote">"First, solve the problem. Then, write the code."</p>
            <p>© 2024 | Built with 💙 and ☕</p>
        </footer>
    </div>

    <script>
        // Create floating particles
        function createParticles() {
            const particles = document.getElementById('particles');
            for (let i = 0; i < 30; i++) {
                const particle = document.createElement('div');
                particle.className = 'particle';
                particle.style.width = Math.random() * 4 + 2 + 'px';
                particle.style.height = particle.style.width;
                particle.style.left = Math.random() * 100 + '%';
                particle.style.top = Math.random() * 100 + '%';
                particle.style.animationDelay = Math.random() * 20 + 's';
                particle.style.animationDuration = Math.random() * 20 + 20 + 's';
                particles.appendChild(particle);
            }
        }

        // Scroll animation observer
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -100px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, observerOptions);

        document.querySelectorAll('.fade-in').forEach(el => observer.observe(el));

        // Initialize
        createParticles();

        // Skill tag interaction
        document.querySelectorAll('.skill-tag').forEach(tag => {
            tag.addEventListener('click', function() {
                this.style.animation = 'none';
                setTimeout(() => {
                    this.style.animation = '';
                }, 10);
            });
        });
    </script>
</body>
</html>
