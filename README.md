<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ehsan's GitHub Universe</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&family=Orbitron:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #F75C7E;
            --secondary: #9C27B0;
            --dark: #0f0c29;
            --darker: #0a081c;
            --light: #f8f9fa;
            --accent: #00d9ff;
            --gradient: linear-gradient(135deg, #F75C7E, #9C27B0, #673AB7);
            --card-bg: rgba(25, 20, 60, 0.7);
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            background: var(--darker);
            background-image: 
                radial-gradient(circle at 10% 20%, rgba(155, 39, 176, 0.1) 0%, transparent 20%),
                radial-gradient(circle at 90% 80%, rgba(247, 92, 126, 0.1) 0%, transparent 20%);
            color: var(--light);
            font-family: 'Poppins', sans-serif;
            line-height: 1.6;
            overflow-x: hidden;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        /* Header Styles */
        header {
            text-align: center;
            padding: 60px 20px;
            position: relative;
            overflow: hidden;
        }
        
        .stars {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
        }
        
        .star {
            position: absolute;
            background-color: white;
            border-radius: 50%;
            animation: twinkle var(--duration, 4s) infinite ease-in-out;
            opacity: 0;
        }
        
        .header-content {
            position: relative;
            z-index: 2;
        }
        
        h1 {
            font-family: 'Orbitron', sans-serif;
            font-size: 4rem;
            margin-bottom: 20px;
            background: var(--gradient);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            text-shadow: 0 0 15px rgba(247, 92, 126, 0.3);
            animation: glow 2s infinite alternate;
        }
        
        .typing-container {
            min-height: 120px;
            display: flex;
            justify-content: center;
            align-items: center;
            margin: 30px 0;
        }
        
        .typing-text {
            font-family: 'Fira Code', monospace;
            font-weight: 600;
            font-size: 2.5rem;
            text-align: center;
            color: var(--primary);
        }
        
        .cursor {
            display: inline-block;
            width: 10px;
            height: 2.5rem;
            background-color: var(--accent);
            margin-left: 5px;
            animation: blink 0.7s infinite;
        }
        
        /* Section Styles */
        section {
            background: var(--card-bg);
            border-radius: 20px;
            padding: 30px;
            margin: 30px 0;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            border: 1px solid rgba(128, 0, 128, 0.2);
            position: relative;
            overflow: hidden;
            transition: transform 0.3s ease;
        }
        
        section:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 40px rgba(247, 92, 126, 0.2);
        }
        
        section::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background: var(--gradient);
            animation: border-glow 3s infinite linear;
        }
        
        h2 {
            font-family: 'Orbitron', sans-serif;
            font-size: 2.5rem;
            margin-bottom: 25px;
            color: var(--accent);
            text-align: center;
            position: relative;
            display: inline-block;
        }
        
        h2::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 4px;
            background: var(--gradient);
            border-radius: 2px;
        }
        
        /* About Me */
        .about-content {
            display: flex;
            flex-wrap: wrap;
            gap: 30px;
            align-items: center;
        }
        
        .astronaut {
            flex: 1;
            min-width: 300px;
            height: 300px;
            position: relative;
            animation: float 6s infinite ease-in-out;
        }
        
        .astronaut-inner {
            position: absolute;
            width: 100%;
            height: 100%;
            background: url('https://i.postimg.cc/4y1fM2W7/astronaut.png') center no-repeat;
            background-size: contain;
        }
        
        .about-text {
            flex: 2;
            min-width: 300px;
            font-size: 1.2rem;
        }
        
        .about-text ul {
            list-style-type: none;
            margin-top: 20px;
        }
        
        .about-text li {
            margin-bottom: 15px;
            padding-left: 30px;
            position: relative;
            font-size: 1.1rem;
        }
        
        .about-text li::before {
            content: '➤';
            position: absolute;
            left: 0;
            color: var(--primary);
        }
        
        /* Skills */
        .skills-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 20px;
            margin-top: 30px;
        }
        
        .skill-card {
            width: 100px;
            height: 120px;
            perspective: 1000px;
        }
        
        .skill-inner {
            position: relative;
            width: 100%;
            height: 100%;
            text-align: center;
            transition: transform 0.6s;
            transform-style: preserve-3d;
        }
        
        .skill-card:hover .skill-inner {
            transform: rotateY(180deg);
        }
        
        .skill-front, .skill-back {
            position: absolute;
            width: 100%;
            height: 100%;
            backface-visibility: hidden;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            border-radius: 15px;
            padding: 10px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }
        
        .skill-front {
            background: rgba(40, 30, 80, 0.8);
            border: 1px solid rgba(247, 92, 126, 0.3);
        }
        
        .skill-back {
            background: var(--gradient);
            transform: rotateY(180deg);
            font-weight: bold;
            font-size: 0.9rem;
        }
        
        .skill-icon {
            font-size: 2.5rem;
            margin-bottom: 10px;
        }
        
        /* Stats */
        .stats-container {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            justify-content: center;
            margin-top: 30px;
        }
        
        .stat-card {
            background: var(--gradient);
            border-radius: 15px;
            padding: 25px;
            text-align: center;
            min-width: 250px;
            flex: 1;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
            position: relative;
            overflow: hidden;
        }
        
        .stat-card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(255, 255, 255, 0.1), transparent);
            transform: rotate(45deg);
            animation: shine 3s infinite;
        }
        
        .stat-number {
            font-size: 3rem;
            font-weight: bold;
            margin: 10px 0;
            font-family: 'Orbitron', sans-serif;
        }
        
        /* Goals */
        .goals-container {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            justify-content: center;
            margin-top: 30px;
        }
        
        .goal-card {
            background: rgba(40, 30, 80, 0.6);
            border-radius: 15px;
            padding: 25px;
            width: 270px;
            border: 1px solid rgba(247, 92, 126, 0.3);
            position: relative;
            overflow: hidden;
            transition: all 0.3s ease;
        }
        
        .goal-card:hover {
            transform: translateY(-10px);
            border-color: var(--primary);
            box-shadow: 0 10px 25px rgba(247, 92, 126, 0.3);
        }
        
        .goal-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 5px;
            height: 100%;
            background: var(--gradient);
        }
        
        .goal-icon {
            font-size: 2.5rem;
            margin-bottom: 15px;
            color: var(--primary);
        }
        
        .goal-card h3 {
            margin-bottom: 15px;
            color: var(--accent);
        }
        
        /* Contact */
        .contact-container {
            display: flex;
            justify-content: center;
            gap: 25px;
            flex-wrap: wrap;
            margin-top: 30px;
        }
        
        .contact-btn {
            display: flex;
            align-items: center;
            gap: 10px;
            padding: 15px 30px;
            border-radius: 50px;
            font-size: 1.1rem;
            font-weight: 500;
            text-decoration: none;
            color: white;
            background: rgba(40, 30, 80, 0.8);
            border: 2px solid transparent;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }
        
        .contact-btn:hover {
            transform: translateY(-5px);
            border-color: var(--primary);
            box-shadow: 0 10px 25px rgba(247, 92, 126, 0.3);
        }
        
        .contact-btn i {
            font-size: 1.5rem;
        }
        
        /* Animations */
        @keyframes twinkle {
            0% { opacity: 0; }
            50% { opacity: 1; }
            100% { opacity: 0; }
        }
        
        @keyframes glow {
            0% { text-shadow: 0 0 15px rgba(247, 92, 126, 0.3); }
            100% { text-shadow: 0 0 25px rgba(247, 92, 126, 0.6), 0 0 50px rgba(155, 39, 176, 0.4); }
        }
        
        @keyframes blink {
            0%, 100% { opacity: 1; }
            50% { opacity: 0; }
        }
        
        @keyframes float {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-20px); }
            100% { transform: translateY(0px); }
        }
        
        @keyframes border-glow {
            0% { background-position: 0% 50%; }
            100% { background-position: 200% 50%; }
        }
        
        @keyframes shine {
            0% { transform: rotate(45deg) translate(-50%, -50%); opacity: 0; }
            20% { opacity: 1; }
            100% { transform: rotate(45deg) translate(50%, 50%); opacity: 0; }
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            h1 { font-size: 2.5rem; }
            .typing-text { font-size: 1.8rem; }
            .stat-card { min-width: 100%; }
            .about-content { flex-direction: column; }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Header Section -->
        <header>
            <div class="stars" id="stars-container"></div>
            <div class="header-content">
                <h1>🌌 Welcome to My Universe! 🌌</h1>
                <div class="typing-container">
                    <div class="typing-text" id="typing-text">Hey There! I'm Ehsan 👋</div>
                    <div class="cursor"></div>
                </div>
            </div>
        </header>

        <!-- About Me Section -->
        <section>
            <h2>✨ About Me</h2>
            <div class="about-content">
                <div class="astronaut">
                    <div class="astronaut-inner"></div>
                </div>
                <div class="about-text">
                    <p>Hi, I’m <strong>Ehsan</strong>! 👨‍💻 A passionate <strong>Full-Stack Developer</strong> and <strong>aspiring entrepreneur</strong> who loves creating captivating and functional digital experiences.</p>
                    <p>Whether it's crafting interactive UI designs or building robust backend systems, I aim to leave a mark in the tech world! 🌍</p>
                    <ul>
                        <li><strong>Why I Code:</strong> To bring <em>ideas to life</em> through technology and design.</li>
                        <li><strong>Mission:</strong> Create impactful solutions with a perfect blend of aesthetics and functionality.</li>
                        <li><strong>Fun Fact:</strong> Coding feels like magic, and I'm the wizard! 🪄</li>
                    </ul>
                </div>
            </div>
        </section>

        <!-- Skills Section -->
        <section>
            <h2>🚀 Skillset and Tools</h2>
            <div class="skills-container">
                <div class="skill-card">
                    <div class="skill-inner">
                        <div class="skill-front">
                            <div class="skill-icon"><i class="fab fa-js"></i></div>
                            <div>JavaScript</div>
                        </div>
                        <div class="skill-back">JavaScript</div>
                    </div>
                </div>
                <div class="skill-card">
                    <div class="skill-inner">
                        <div class="skill-front">
                            <div class="skill-icon"><i class="fab fa-react"></i></div>
                            <div>React</div>
                        </div>
                        <div class="skill-back">React</div>
                    </div>
                </div>
                <div class="skill-card">
                    <div class="skill-inner">
                        <div class="skill-front">
                            <div class="skill-icon"><i class="fab fa-node-js"></i></div>
                            <div>Node.js</div>
                        </div>
                        <div class="skill-back">Node.js</div>
                    </div>
                </div>
                <div class="skill-card">
                    <div class="skill-inner">
                        <div class="skill-front">
                            <div class="skill-icon"><i class="fas fa-database"></i></div>
                            <div>MongoDB</div>
                        </div>
                        <div class="skill-back">MongoDB</div>
                    </div>
                </div>
                <div class="skill-card">
                    <div class="skill-inner">
                        <div class="skill-front">
                            <div class="skill-icon"><i class="fab fa-css3-alt"></i></div>
                            <div>Tailwind</div>
                        </div>
                        <div class="skill-back">Tailwind</div>
                    </div>
                </div>
                <div class="skill-card">
                    <div class="skill-inner">
                        <div class="skill-front">
                            <div class="skill-icon"><i class="fab fa-docker"></i></div>
                            <div>Docker</div>
                        </div>
                        <div class="skill-back">Docker</div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Expertise Section -->
        <section>
            <h2>💻 What I Do Best</h2>
            <div class="stats-container">
                <div class="stat-card">
                    <i class="fas fa-laptop-code fa-2x"></i>
                    <div class="stat-number">Frontend</div>
                    <p>React, Tailwind CSS, Animation, Responsiveness</p>
                </div>
                <div class="stat-card">
                    <i class="fas fa-server fa-2x"></i>
                    <div class="stat-number">Backend</div>
                    <p>Node.js, Express, Mongoose, MongoDB</p>
                </div>
                <div class="stat-card">
                    <i class="fas fa-magic fa-2x"></i>
                    <div class="stat-number">Full-Stack</div>
                    <p>Bringing ideas to life from concept to deployment!</p>
                </div>
                <div class="stat-card">
                    <i class="fas fa-shopping-cart fa-2x"></i>
                    <div class="stat-number">E-Commerce</div>
                    <p>Building seamless online shopping experiences</p>
                </div>
            </div>
        </section>

        <!-- Goals Section -->
        <section>
            <h2>🚀 Goals for 2025</h2>
            <div class="goals-container">
                <div class="goal-card">
                    <div class="goal-icon"><i class="fas fa-rocket"></i></div>
                    <h3>Build 5 Projects</h3>
                    <p>Full-stack projects with outstanding UI/UX</p>
                </div>
                <div class="goal-card">
                    <div class="goal-icon"><i class="fas fa-lightbulb"></i></div>
                    <h3>Launch Startup</h3>
                    <p>Bring my innovative ideas to market</p>
                </div>
                <div class="goal-card">
                    <div class="goal-icon"><i class="fas fa-cogs"></i></div>
                    <h3>Master DevOps</h3>
                    <p>Learn advanced DevOps and microservices</p>
                </div>
                <div class="goal-card">
                    <div class="goal-icon"><i class="fas fa-hands-helping"></i></div>
                    <h3>Open Source</h3>
                    <p>Contribute to meaningful projects</p>
                </div>
            </div>
        </section>

        <!-- Contact Section -->
        <section>
            <h2>✨ Find Me Here</h2>
            <div class="contact-container">
                <a href="https://linkedin.com/in/shah-ehsan" class="contact-btn" target="_blank">
                    <i class="fab fa-linkedin"></i> LinkedIn
                </a>
                <a href="https://instagram.com/s_a_ehsan" class="contact-btn" target="_blank">
                    <i class="fab fa-instagram"></i> Instagram
                </a>
                <a href="mailto:shahehsan2002@gmail.com" class="contact-btn">
                    <i class="fas fa-envelope"></i> Email
                </a>
            </div>
        </section>

        <!-- Quote Section -->
        <section>
            <h2>🔥 What Keeps Me Going?</h2>
            <div style="text-align: center; padding: 30px;">
                <blockquote style="font-size: 1.5rem; font-style: italic; max-width: 800px; margin: 0 auto 30px; position: relative;">
                    <i class="fas fa-quote-left" style="position: absolute; left: -40px; top: -20px; font-size: 4rem; opacity: 0.2;"></i>
                    "The only limit to our realization of tomorrow is our doubts of today."
                    <div style="margin-top: 15px; font-weight: bold;">– Franklin D. Roosevelt</div>
                </blockquote>
            </div>
        </section>
    </div>

    <script>
        // Create dynamic stars
        const starsContainer = document.getElementById('stars-container');
        for (let i = 0; i < 150; i++) {
            const star = document.createElement('div');
            star.classList.add('star');
            star.style.left = `${Math.random() * 100}%`;
            star.style.top = `${Math.random() * 100}%`;
            star.style.width = `${Math.random() * 3 + 1}px`;
            star.style.height = star.style.width;
            star.style.animationDelay = `${Math.random() * 5}s`;
            starsContainer.appendChild(star);
        }

        // Typing animation
        const typingText = document.getElementById('typing-text');
        const phrases = [
            "Hey There! I'm Ehsan 👋",
            "Full-Stack Web Developer 💻",
            "Coding to Make a Difference 🌍",
            "Always Innovating 🚀"
        ];
        
        let phraseIndex = 0;
        let charIndex = 0;
        let isDeleting = false;
        let typingSpeed = 100;
        
        function type() {
            const currentPhrase = phrases[phraseIndex];
            
            if (isDeleting) {
                typingText.textContent = currentPhrase.substring(0, charIndex - 1);
                charIndex--;
                typingSpeed = 50;
            } else {
                typingText.textContent = currentPhrase.substring(0, charIndex + 1);
                charIndex++;
                typingSpeed = charIndex === currentPhrase.length ? 1500 : 100;
            }
            
            if (!isDeleting && charIndex === currentPhrase.length) {
                isDeleting = true;
                typingSpeed = 1500;
            } else if (isDeleting && charIndex === 0) {
                isDeleting = false;
                phraseIndex = (phraseIndex + 1) % phrases.length;
            }
            
            setTimeout(type, typingSpeed);
        }
        
        // Start typing animation
        setTimeout(type, 1000);
        
        // Add hover effect to sections
        const sections = document.querySelectorAll('section');
        sections.forEach(section => {
            section.addEventListener('mouseenter', () => {
                section.style.transform = 'translateY(-10px)';
            });
            
            section.addEventListener('mouseleave', () => {
                section.style.transform = 'translateY(0)';
            });
        });
    </script>
    
</body>
</html>
