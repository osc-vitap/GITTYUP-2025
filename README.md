<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Portfolio | CS Student</title>
    <meta name="description" content="Portfolio of a Computer Science Student and Developer">
    
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Fira+Code:wght@300;400;600&family=JetBrains+Mono:wght@400;700&display=swap" rel="stylesheet">

    <style>
        /* ========================================
           CSS VARIABLES & RESET
        ======================================== */
        :root {
            --bg-color: #0a192f;        /* Deep Navy */
            --bg-light: #112240;        /* Lighter Navy for cards */
            --text-primary: #e6f1ff;    /* White-ish */
            --text-secondary: #8892b0;  /* Slate Grey */
            --accent-color: #64ffda;    /* Neon Cyan/Green */
            --font-mono: 'Fira Code', 'JetBrains Mono', 'Courier New', monospace;
            --transition: all 0.25s cubic-bezier(0.645, 0.045, 0.355, 1);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-secondary);
            font-family: var(--font-mono);
            font-size: 16px;
            line-height: 1.6;
            overflow-x: hidden;
        }

        a {
            text-decoration: none;
            color: inherit;
            transition: var(--transition);
        }

        ul {
            list-style: none;
        }

        /* ========================================
           UTILITY CLASSES
        ======================================== */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
        }

        .section {
            padding: 100px 0;
        }

        .accent-text {
            color: var(--accent-color);
            font-size: 14px;
            margin-bottom: 20px;
        }

        .section-title {
            display: flex;
            align-items: center;
            color: var(--text-primary);
            font-size: clamp(26px, 5vw, 32px);
            margin-bottom: 40px;
        }

        .section-title::after {
            content: "";
            display: block;
            width: 200px;
            height: 1px;
            background-color: #233554;
            margin-left: 20px;
        }

        .hash {
            color: var(--accent-color);
            margin-right: 10px;
        }

        /* Buttons */
        .btn {
            display: inline-block;
            padding: 12px 24px;
            border-radius: 4px;
            font-size: 14px;
            cursor: pointer;
            font-family: var(--font-mono);
            margin-top: 10px;
        }

        .btn-primary {
            border: 1px solid var(--accent-color);
            color: var(--accent-color);
            background: transparent;
        }

        .btn-primary:hover {
            background: rgba(100, 255, 218, 0.1);
        }

        .btn-outline {
            border: 1px solid var(--text-secondary);
            color: var(--text-secondary);
            margin-left: 15px;
        }

        .btn-outline:hover {
            border-color: var(--text-primary);
            color: var(--text-primary);
        }

        /* ========================================
           NAVBAR
        ======================================== */
        .navbar {
            position: fixed;
            top: 0;
            width: 100%;
            height: 80px;
            background: rgba(10, 25, 47, 0.95);
            backdrop-filter: blur(10px);
            z-index: 1000;
            display: flex;
            align-items: center;
            box-shadow: 0 2px 10px rgba(0,0,0,0.3);
        }

        .nav-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            width: 100%;
        }

        .logo {
            color: var(--accent-color);
            font-weight: 700;
            font-size: 1.2rem;
            border: 2px solid var(--accent-color);
            padding: 5px 10px;
        }

        .nav-links {
            display: flex;
            gap: 30px;
        }

        .nav-item {
            font-size: 13px;
            color: var(--text-primary);
        }

        .nav-item:hover {
            color: var(--accent-color);
        }

        .nav-item::before {
            content: ">";
            color: var(--accent-color);
            margin-right: 5px;
            opacity: 0;
            transition: opacity 0.3s;
        }

        .nav-item:hover::before {
            opacity: 1;
        }

        /* Hamburger Menu */
        .hamburger {
            display: none;
            cursor: pointer;
        }

        .bar {
            display: block;
            width: 25px;
            height: 3px;
            margin: 5px auto;
            background-color: var(--accent-color);
            transition: all 0.3s ease-in-out;
        }

        /* ========================================
           HERO SECTION
        ======================================== */
        .hero-section {
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            padding-top: 0;
        }

        .glitch-text {
            font-size: clamp(40px, 8vw, 80px);
            color: var(--text-primary);
            font-weight: 600;
            line-height: 1.1;
        }

        .role-text {
            font-size: clamp(30px, 5vw, 60px);
            color: var(--text-secondary);
            font-weight: 600;
            margin-bottom: 20px;
        }

        .tagline {
            font-size: 18px;
            max-width: 500px;
            margin-bottom: 50px;
            height: 24px;
        }

        .cursor {
            color: var(--accent-color);
            animation: blink 1s step-end infinite;
        }

        @keyframes blink {
            0%, 100% { opacity: 1; }
            50% { opacity: 0; }
        }

        /* ========================================
           ABOUT SECTION
        ======================================== */
        .about-grid {
            display: grid;
            grid-template-columns: 3fr 2fr;
            gap: 50px;
            align-items: start;
        }

        .terminal-list li {
            margin-bottom: 10px;
            position: relative;
            padding-left: 20px;
        }

        .terminal-list li::before {
            content: "▹";
            position: absolute;
            left: 0;
            color: var(--accent-color);
        }

        /* Terminal Box Look */
        .terminal-box {
            background-color: #1a1a1a;
            border-radius: 5px;
            border: 1px solid #333;
            overflow: hidden;
            box-shadow: 0 10px 30px -15px rgba(2,12,27,0.7);
        }

        .terminal-header {
            background-color: #252526;
            padding: 5px 10px;
            display: flex;
            align-items: center;
            gap: 6px;
            border-bottom: 1px solid #333;
        }

        .dot {
            width: 10px;
            height: 10px;
            border-radius: 50%;
        }
        .red { background: #ff5f56; }
        .yellow { background: #ffbd2e; }
        .green { background: #27c93f; }

        .title {
            margin-left: 10px;
            font-size: 12px;
            color: #ccc;
        }

        .terminal-body {
            padding: 20px;
            color: #fff;
            font-size: 14px;
            font-family: var(--font-mono);
        }

        /* ========================================
           SKILLS SECTION
        ======================================== */
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
        }

        .skill-card {
            background-color: var(--bg-light);
            padding: 25px;
            border-radius: 4px;
            transition: var(--transition);
        }

        .skill-card:hover {
            transform: translateY(-5px);
        }

        .skill-card h3 {
            color: var(--text-primary);
            margin-bottom: 20px;
            border-bottom: 1px solid #233554;
            padding-bottom: 10px;
        }

        .skill-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
        }

        .skill-tags span {
            font-size: 13px;
            color: var(--accent-color);
        }

        /* ========================================
           PROJECTS SECTION
        ======================================== */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 15px;
        }

        .project-card {
            background-color: var(--bg-light);
            padding: 2rem;
            border-radius: 4px;
            transition: var(--transition);
            display: flex;
            flex-direction: column;
            height: 100%;
        }

        .project-card:hover {
            transform: translateY(-7px);
        }

        .folder-icon {
            color: var(--accent-color);
            margin-bottom: 20px;
        }

        .project-title {
            color: var(--text-primary);
            font-size: 22px;
            margin-bottom: 10px;
        }

        .project-desc {
            font-size: 15px;
            margin-bottom: 20px;
            flex-grow: 1;
        }

        .tech-stack {
            display: flex;
            gap: 15px;
            font-size: 12px;
            margin-bottom: 20px;
            color: var(--text-secondary);
        }

        .project-links a {
            color: var(--text-primary);
            margin-right: 15px;
        }

        .project-links a:hover {
            color: var(--accent-color);
        }

        /* ========================================
           CONTACT & FOOTER
        ======================================== */
        .text-center {
            text-align: center;
        }

        .narrow-container {
            max-width: 600px;
            margin: 0 auto;
        }

        .big-title {
            font-size: clamp(40px, 5vw, 60px);
            color: var(--text-primary);
            margin-bottom: 20px;
        }

        .social-links {
            margin-top: 50px;
            display: flex;
            justify-content: center;
            gap: 30px;
        }

        .social-links a:hover {
            color: var(--accent-color);
        }

        footer {
            text-align: center;
            padding: 20px;
            font-size: 13px;
            margin-bottom: 20px;
        }

        /* ========================================
           MEDIA QUERIES
        ======================================== */
        @media (max-width: 768px) {
            .about-grid {
                grid-template-columns: 1fr;
            }

            .hamburger {
                display: block;
            }

            .hamburger.toggle .bar:nth-child(2) {
                opacity: 0;
            }
            .hamburger.toggle .bar:nth-child(1) {
                transform: translateY(8px) rotate(45deg);
            }
            .hamburger.toggle .bar:nth-child(3) {
                transform: translateY(-8px) rotate(-45deg);
            }

            .nav-links {
                position: fixed;
                right: -100%;
                top: 80px;
                gap: 0;
                flex-direction: column;
                background-color: var(--bg-light);
                width: 70%; /* Slide out width */
                height: 100vh;
                text-align: center;
                transition: 0.3s;
                padding-top: 2rem;
            }

            .nav-item {
                margin: 1.5rem 0;
                display: block;
                font-size: 1.2rem;
            }

            .nav-links.active {
                right: 0;
            }
        }
    </style>
</head>
<body>

    <header class="navbar">
        <div class="container nav-container">
            <a href="#hero" class="logo">&lt;AlexDev /&gt;</a>
            
            <nav class="nav-links" id="navLinks">
                <a href="#about" class="nav-item">01. About</a>
                <a href="#skills" class="nav-item">02. Skills</a>
                <a href="#projects" class="nav-item">03. Projects</a>
                <a href="#contact" class="nav-item">04. Contact</a>
            </nav>
            
            <div class="hamburger" id="hamburger">
                <div class="bar"></div>
                <div class="bar"></div>
                <div class="bar"></div>
            </div>
        </div>
    </header>

    <main>
        <section id="hero" class="hero-section">
            <div class="container">
                <p class="accent-text">Hello, World! I am</p>
                <h1 class="glitch-text">Alex Dev</h1>
                <h2 class="role-text">Systems Engineer & CS Student</h2>
                <p class="tagline">
                    <span id="typewriter"></span><span class="cursor">|</span>
                </p>
                <div class="cta-group">
                    <a href="#projects" class="btn btn-primary">View Work</a>
                    <a href="#contact" class="btn btn-outline">Contact Me</a>
                </div>
            </div>
        </section>

        <section id="about" class="section">
            <div class="container">
                <h2 class="section-title"><span class="hash">#</span> About Me</h2>
                <div class="about-grid">
                    <div class="about-text">
                        <p>
                            I am a Computer Science student passionate about low-level systems and building efficient software. 
                            I enjoy solving complex problems using Python and C++, and I have a keen interest in cybersecurity and digital logic.
                        </p>
                        <br>
                        <h3 class="sub-title">// Education</h3>
                        <ul class="terminal-list">
                            <li><strong>University:</strong> Institute of Technology</li>
                            <li><strong>Degree:</strong> B.Tech in Computer Science</li>
                            <li><strong>Grad Year:</strong> 2026</li>
                        </ul>
                    </div>
                    <div class="interests-box terminal-box">
                        <div class="terminal-header">
                            <span class="dot red"></span>
                            <span class="dot yellow"></span>
                            <span class="dot green"></span>
                            <span class="title">interests.json</span>
                        </div>
                        <div class="terminal-body">
                            <p>"Hobbies": ["Debating", "CTF Challenges", "Robotics"],</p>
                            <p style="margin-top:10px;">"Soft_Skills": ["Public Speaking", "Leadership", "Problem Solving"]</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section id="skills" class="section">
            <div class="container">
                <h2 class="section-title"><span class="hash">#</span> Technical Arsenal</h2>
                <div class="skills-grid">
                    <div class="skill-card">
                        <h3>Languages</h3>
                        <div class="skill-tags">
                            <span>Python</span>
                            <span>C++</span>
                            <span>Java</span>
                            <span>SQL</span>
                            <span>Bash</span>
                        </div>
                    </div>
                    <div class="skill-card">
                        <h3>Tools</h3>
                        <div class="skill-tags">
                            <span>Git/GitHub</span>
                            <span>Linux (Kali/Ubuntu)</span>
                            <span>Docker</span>
                            <span>VS Code</span>
                            <span>Wireshark</span>
                        </div>
                    </div>
                    <div class="skill-card">
                        <h3>Core Concepts</h3>
                        <div class="skill-tags">
                            <span>Data Structures</span>
                            <span>Algorithms</span>
                            <span>Network Security</span>
                            <span>OS Architecture</span>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section id="projects" class="section">
            <div class="container">
                <h2 class="section-title"><span class="hash">#</span> Projects</h2>
                <div class="projects-grid">
                    
                    <article class="project-card">
                        <div class="folder-icon">
                            <svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M22 19a2 2 0 0 1-2 2H4a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h5l2 3h9a2 2 0 0 1 2 2z"></path></svg>
                        </div>
                        <h3 class="project-title">Network Packet Sniffer</h3>
                        <p class="project-desc">A Python-based tool to analyze network traffic and identify potential security threats in real-time.</p>
                        <ul class="tech-stack">
                            <li>Python</li>
                            <li>Scapy</li>
                            <li>Networking</li>
                        </ul>
                        <div class="project-links">
                            <a href="#" target="_blank">GitHub</a>
                            <a href="#" target="_blank">Demo</a>
                        </div>
                    </article>

                    <article class="project-card">
                        <div class="folder-icon">
                            <svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M22 19a2 2 0 0 1-2 2H4a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h5l2 3h9a2 2 0 0 1 2 2z"></path></svg>
                        </div>
                        <h3 class="project-title">Algorithmic Trading Bot</h3>
                        <p class="project-desc">Automated trading script utilizing moving average crossover strategies to execute mock trades.</p>
                        <ul class="tech-stack">
                            <li>Python</li>
                            <li>Pandas</li>
                            <li>API Integration</li>
                        </ul>
                        <div class="project-links">
                            <a href="#" target="_blank">GitHub</a>
                        </div>
                    </article>

                    <article class="project-card">
                        <div class="folder-icon">
                            <svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"><path d="M22 19a2 2 0 0 1-2 2H4a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h5l2 3h9a2 2 0 0 1 2 2z"></path></svg>
                        </div>
                        <h3 class="project-title">Portfolio v1</h3>
                        <p class="project-desc">My first personal portfolio website built with raw HTML and CSS to showcase my frontend fundamentals.</p>
                        <ul class="tech-stack">
                            <li>HTML5</li>
                            <li>CSS3</li>
                            <li>Responsive Design</li>
                        </ul>
                        <div class="project-links">
                            <a href="#" target="_blank">GitHub</a>
                            <a href="#" target="_blank">Live</a>
                        </div>
                    </article>

                </div>
            </div>
        </section>

        <section id="contact" class="section text-center">
            <div class="container narrow-container">
                <p class="accent-text">04. What's Next?</p>
                <h2 class="big-title">Get In Touch</h2>
                <p>
                    I am currently looking for internship opportunities and open-source collaborations. 
                    Whether you have a question or just want to say hi, my inbox is open!
                </p>
                <br>
                <a href="mailto:email@example.com" class="btn btn-primary">Say Hello</a>
                
                <div class="social-links">
                    <a href="https://github.com" target="_blank">GitHub</a>
                    <a href="https://linkedin.com" target="_blank">LinkedIn</a>
                    <a href="https://twitter.com" target="_blank">Twitter</a>
                </div>
            </div>
        </section>
    </main>

    <footer>
        <p>Designed & Built by Alex Dev.</p>
    </footer>

    <script>
        // 1. Mobile Menu Toggle
        const hamburger = document.getElementById('hamburger');
        const navLinks = document.getElementById('navLinks');

        hamburger.addEventListener('click', () => {
            navLinks.classList.toggle('active');
            hamburger.classList.toggle('toggle');
        });

        // Close menu when a link is clicked
        document.querySelectorAll('.nav-item').forEach(n => n.addEventListener('click', () => {
            navLinks.classList.remove('active');
            hamburger.classList.remove('toggle');
        }));

        // 2. Typewriter Effect for Tagline
        const textElement = document.getElementById('typewriter');
        // Edit these phrases to match your specific interests
        const phrases = ["Building secure systems...", "Exploring digital logic...", "Crafting clean code..."];
        let phraseIndex = 0;
        let charIndex = 0;
        let isDeleting = false;
        let typeSpeed = 100;

        function type() {
            const currentPhrase = phrases[phraseIndex];
            
            if (isDeleting) {
                textElement.textContent = currentPhrase.substring(0, charIndex - 1);
                charIndex--;
                typeSpeed = 50; // Faster deleting
            } else {
                textElement.textContent = currentPhrase.substring(0, charIndex + 1);
                charIndex++;
                typeSpeed = 100; // Normal typing
            }

            if (!isDeleting && charIndex === currentPhrase.length) {
                isDeleting = true;
                typeSpeed = 2000; // Pause at end of sentence
            } else if (isDeleting && charIndex === 0) {
                isDeleting = false;
                phraseIndex = (phraseIndex + 1) % phrases.length;
                typeSpeed = 500; // Pause before next sentence
            }

            setTimeout(type, typeSpeed);
        }

        document.addEventListener('DOMContentLoaded', type);
    </script>
</body>
</html>
