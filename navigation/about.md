---
layout: post
title: About
permalink: /about/
comments: true
---

<style>
    @import url('https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,600;1,400&family=Space+Grotesk:wght@400;600;700;800;900&display=swap');

    /* Global Wrapper - Full Bleed Breakout & Deep Black Gradient */
    .portfolio-wrapper {
        font-family: 'Space Grotesk', sans-serif;
        color: #d1d5db;
        line-height: 1.7;
        font-size: 1.1rem;
        position: relative;
        padding-bottom: 5rem;
        background: linear-gradient(to bottom, #0a0a0f 0%, #000000 100%);
        overflow: hidden; 
        width: 100vw;
        margin-left: calc(50% - 50vw);
    }

    /* Interactive Particle Canvas Layer */
    #particleCanvas {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        z-index: 0;
        pointer-events: none; 
    }

    /* Ambient Glow - Light Blue Accent */
    .ambient-glow {
        position: absolute;
        top: 30%;
        left: 50%;
        transform: translate(-50%, -50%);
        width: 100vw;
        height: 500px;
        background: radial-gradient(ellipse at center, rgba(56, 189, 248, 0.08) 0%, transparent 60%);
        filter: blur(60px);
        z-index: 0;
        pointer-events: none;
    }

    /* Section Containers */
    .section-wrapper {
        position: relative;
        width: 100%;
        padding-top: 8rem; 
        padding-bottom: 8rem;
        display: flex;
        flex-direction: column;
        align-items: center;
        z-index: 5;
    }

    /* Background Headers - Edge-to-Edge Adjustments */
    .env-header {
        position: absolute;
        top: 50%; 
        left: 50%;
        font-family: 'Space Grotesk', sans-serif;
        text-transform: uppercase;
        font-weight: 800; 
        text-align: center;
        color: rgba(255, 255, 255, 0.12); 
        white-space: nowrap; 
        z-index: 1; 
        pointer-events: none;
        user-select: none;
        opacity: 0;
        transition: transform 1.5s cubic-bezier(0.16, 1, 0.3, 1), 
                    letter-spacing 1.5s cubic-bezier(0.16, 1, 0.3, 1), 
                    padding-left 1.5s cubic-bezier(0.16, 1, 0.3, 1),
                    opacity 1.5s ease-out;
    }

    /* Reduced letter spacing for a tighter look */
    .header-main {
        font-size: 15vw; 
        line-height: 1.1; 
        letter-spacing: -3vw; 
        padding-left: -3vw; 
        transform: translate(-50%, -50%) scale(0.95);
    }
    .header-main.visible {
        transform: translate(-50%, -50%) scale(1);
        letter-spacing: 6vw; /* Reduced from 9vw to bring letters closer */
        padding-left: 6vw; 
        opacity: 1; 
    }

    .header-sub {
        font-size: 10vw; 
        line-height: 1.2; 
        letter-spacing: -2vw; 
        padding-left: -2vw; 
        transform: translate(-50%, -50%) scale(0.95);
    }
    .header-sub.visible {
        transform: translate(-50%, -50%) scale(1);
        letter-spacing: 3vw; 
        padding-left: 3vw; 
        opacity: 1; 
    }

    /* Intro Typography */
    .intro-text {
        font-family: 'Space Grotesk', sans-serif;
        font-size: 1.45rem; 
        font-weight: 400;
        color: #e5e7eb;
        margin-top: 4rem;
        margin-bottom: 3rem;
        text-align: center;
        max-width: 850px;
        margin-left: auto;
        margin-right: auto;
        line-height: 1.7;
        position: relative;
        z-index: 5;
    }

    .highlight-text {
        color: #38bdf8;
        font-weight: 700;
    }

    /* Row Alignment - Opposing Cards on Same Level */
    .semi-row {
        width: 100vw;
        height: 700px; 
        position: relative;
        margin-bottom: 4rem;
        pointer-events: none; 
        z-index: 5;
    }

    /* Geometrically Locked Semicircles */
    .semi-card {
        pointer-events: auto; 
        position: absolute;
        height: 700px; 
        width: 350px; 
        background-color: rgba(22, 22, 26, 0.4); 
        transform: translateZ(0);
        backdrop-filter: blur(0px); 
        -webkit-backdrop-filter: blur(0px);
        overflow: hidden; 
        cursor: pointer;
        z-index: 10;
        
        display: flex;
        align-items: center;
        justify-content: center;
        
        transition: width 1s cubic-bezier(0.16, 1, 0.3, 1),
                    background-color 1s cubic-bezier(0.16, 1, 0.3, 1),
                    box-shadow 1s cubic-bezier(0.16, 1, 0.3, 1),
                    backdrop-filter 1s ease,
                    -webkit-backdrop-filter 1s ease;
    }

    .semi-row.visible .semi-card {
        backdrop-filter: blur(5px);
        -webkit-backdrop-filter: blur(5px);
    }

    /* Anchors to Screen Edges */
    .semi-card.left {
        left: 0;
        border-radius: 0 700px 700px 0; 
        border: 1px solid rgba(56, 189, 248, 0.3);
        border-left: none; 
        box-shadow: 10px 0 40px rgba(56, 189, 248, 0.05);
    }

    .semi-card.right {
        right: 0;
        border-radius: 700px 0 0 700px; 
        border: 1px solid rgba(56, 189, 248, 0.3);
        border-right: none; 
        box-shadow: -10px 0 40px rgba(56, 189, 248, 0.05);
    }

    /* Expanding Hover State */
    .semi-card:hover {
        width: 650px; 
        background-color: rgba(22, 22, 26, 0.75); 
        backdrop-filter: blur(16px);
        -webkit-backdrop-filter: blur(16px);
        z-index: 50; 
    }
    
    .semi-card.left:hover { box-shadow: 20px 0 60px rgba(56, 189, 248, 0.25); }
    .semi-card.right:hover { box-shadow: -20px 0 60px rgba(56, 189, 248, 0.25); }

    /* Clean White Flash Overlay */
    .flash-overlay {
        position: absolute;
        top: 0; left: 0; right: 0; bottom: 0;
        background-color: #ffffff;
        opacity: 0;
        pointer-events: none;
        z-index: 1; 
        transition: opacity 0.5s ease;
    }

    @keyframes smoothFlash {
        0% { opacity: 0; }
        15% { opacity: 0.5; }
        100% { opacity: 0; }
    }

    .semi-card:hover .flash-overlay {
        animation: smoothFlash 1s cubic-bezier(0.16, 1, 0.3, 1) forwards;
    }

    /* Triangle Image Architecture with Inward Gliding Animation */
    .image-panel {
        position: absolute;
        top: 0;
        height: 100%;
        width: 350px; 
        opacity: 0;
        z-index: 2; 
        transition: opacity 0.8s ease, transform 0.8s cubic-bezier(0.16, 1, 0.3, 1);
    }
    
    .semi-card.left .image-panel { left: 0; transform: translateX(-40px); transform-origin: left center; }
    .semi-card.right .image-panel { right: 0; transform: translateX(40px); transform-origin: right center; }

    .semi-card:hover .image-panel {
        opacity: 1;
        transform: translateX(0);
        transition-delay: 0.1s;
    }

    .image-panel img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        transition: transform 0.6s cubic-bezier(0.16, 1, 0.3, 1), filter 0.5s ease;
    }

    .semi-card.left .image-panel img { clip-path: polygon(0 0, 100% 50%, 0 100%); }
    .semi-card.right .image-panel img { clip-path: polygon(100% 0, 0 50%, 100% 100%); }

    .image-panel img:hover {
        transform: scale(1.05); 
        filter: brightness(1.2);
    }

    /* Tilted Title Container */
    .tilt-container {
        position: absolute;
        width: 100%; 
        height: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        z-index: 10;
        transition: transform 0.8s cubic-bezier(0.16, 1, 0.3, 1), padding 0.8s cubic-bezier(0.16, 1, 0.3, 1);
    }

    .semi-card.left .tilt-container { transform: rotate(0deg); padding-left: 50px; }
    .semi-card.right .tilt-container { transform: rotate(0deg); padding-right: 50px; }

    .semi-card.left:hover .tilt-container { transform: rotate(5deg); padding-left: 0; }
    .semi-card.right:hover .tilt-container { transform: rotate(-5deg); padding-right: 0; }

    /* Title Styling - Kept lower so it stays near the subtext */
    .title-wrapper {
        display: flex;
        align-items: center;
        justify-content: center;
        width: 100%;
        transform: translateY(0);
        transition: transform 0.8s cubic-bezier(0.3, 1, 0.3, 1);
        border: none !important;
    }
    
    .semi-card:hover .title-wrapper {
        transform: translateY(-100px); /* Reduced travel distance so it stays lower */
    }

    .card-title, .card-title::before, .card-title::after {
        font-family: 'Playfair Display', serif !important;
        color: #ffffff !important;
        font-size: 2.2rem !important; 
        font-weight: 600 !important;
        margin: 0 !important;
        text-align: center !important;
        border: none !important; 
        background: transparent !important;
        text-decoration: none !important;
        box-shadow: none !important;
        white-space: nowrap !important; 
    }

    /* Lowered Reveal Content - Raised centering logic removed */
    .card-content {
        position: absolute;
        top: 320px; /* Locked lower in the card, reverting to unraised positioning */
        width: 320px; 
        opacity: 0;
        visibility: hidden;
        z-index: 10;
        transition: opacity 0.5s ease, transform 0.8s cubic-bezier(0.16, 1, 0.3, 1);
    }

    /* Apply default straight alignment without vertical offsets */
    .semi-card.left .card-content { 
        right: 40px; 
        text-align: left; 
        transform: rotate(0deg); 
    }
    .semi-card.right .card-content { 
        left: 40px; 
        text-align: right; 
        transform: rotate(0deg); 
    }

    /* Slant subtext to match the title exactly */
    .semi-card.left:hover .card-content {
        opacity: 1;
        visibility: visible;
        transform: rotate(5deg);
    }
    .semi-card.right:hover .card-content {
        opacity: 1;
        visibility: visible;
        transform: rotate(-5deg);
    }

    /* Immutable Text Block */
    .card-content p {
        width: 100%;
        color: #ffffff !important;
        font-size: 1.15rem;
        margin: 0 0 1.5rem 0; 
        line-height: 1.7;
        opacity: 0;
        transform: translateY(20px);
        transition: color 0.5s ease, opacity 0.5s ease, transform 0.8s cubic-bezier(0.16, 1, 0.3, 1);
    }
    
    .card-content .btn-group {
        opacity: 0;
        transform: translateY(20px);
        display: flex;
        gap: 0.75rem;
        flex-wrap: wrap;
        transition: opacity 0.5s ease, transform 0.8s cubic-bezier(0.16, 1, 0.3, 1);
    }
    .semi-card.left .btn-group { justify-content: flex-start; }
    .semi-card.right .btn-group { justify-content: flex-end; }

    .semi-card:hover .card-content p {
        color: #d1d5db !important;
        opacity: 1;
        transform: translateY(0);
        transition-delay: 0.15s; 
    }
    .semi-card:hover .card-content .btn-group {
        opacity: 1;
        transform: translateY(0);
        transition-delay: 0.25s; 
    }

    /* Standard Buttons */
    .ocs_btn {
        font-family: 'Space Grotesk', sans-serif;
        border-radius: 8px;
        font-weight: 600;
        text-decoration: none;
        padding: 0.6rem 1.25rem;
        display: inline-flex;
        align-items: center;
        justify-content: center;
        transition: all 0.3s ease;
        font-size: 0.9rem;
        letter-spacing: 0.5px;
    }
    .ocs_btn:hover {
        transform: translateY(-2px);
    }

    .ocs_btn.card-btn { 
        background-color: transparent; 
        color: #ffffff; 
        border: 1px solid rgba(255, 255, 255, 0.4); 
    }
    .ocs_btn.card-btn:hover { 
        background-color: rgba(56, 189, 248, 0.15); 
        color: #38bdf8; 
        border-color: #38bdf8;
    }

    /* Scroll Animations */
    .scroll-fade {
        opacity: 0;
        transform: translateY(30px);
        transition: opacity 1s cubic-bezier(0.2, 0.8, 0.2, 1), transform 1s cubic-bezier(0.2, 0.8, 0.2, 1);
    }
    .scroll-fade.visible {
        opacity: 1;
        transform: translateY(0);
    }
</style>

<div class="portfolio-wrapper">
    <canvas id="particleCanvas"></canvas>
    <div class="ambient-glow"></div>

    <p class="intro-text scroll-fade">
        Hi! My name is <span class="highlight-text">Yue Barbara Zhao</span>. <br>
        Born in Santa Barbara, raised in San Diego. (-->(+'□'·-))
    </p>

    <!-- Basic Info Section -->
    <div class="section-wrapper">
        <div class="env-header header-main">ABOUT<br>ME</div>
        
        <div class="semi-row scroll-fade">
            <div class="semi-card left">
                <div class="flash-overlay"></div>
                
                <div class="image-panel">
                    <img src="{{site.baseurl}}/images/about/fin2 (2).jpg" alt="Gallery Image 9">
                </div>
                
                <div class="tilt-container">
                    <div class="title-wrapper">
                        <h3 class="card-title">My Origins</h3>
                    </div>
                </div>

                <div class="card-content">
                    <p>I am Chinese-American. I lived in Santa Barbara for the first couple of years of my life, then moved to San Diego where I've been ever since. I also lived in China for a few months as a baby!</p>
                </div>
            </div>

            <div class="semi-card right">
                <div class="flash-overlay"></div>
                
                <div class="image-panel">
                    <img src="https://cdn.mos.cms.futurecdn.net/8ToUvuPXxcD5ANh3D9Sr8L-1200-80.jpg" alt="Camera">
                </div>

                <div class="tilt-container">
                    <div class="title-wrapper">
                        <h3 class="card-title">Hobbies & Vibe</h3>
                    </div>
                </div>

                <div class="card-content">
                    <p>I spend most of my time drawing, editing photos and videos, and taking pictures. I am heavily fueled by mochi donuts and listening to music.</p>
                </div>
            </div>
        </div>
    </div>

    <!-- Interests Section -->
    <div class="section-wrapper" style="margin-top: 3rem;">
        <div class="env-header header-sub">MY<br>INTERESTS</div>
        
        <div class="semi-row scroll-fade">
            <div class="semi-card left">
                <div class="flash-overlay"></div>
                
                <div class="image-panel">
                    <img src="https://upload.wikimedia.org/wikipedia/en/6/61/Project_SEKAI_title_screen.png?utm_source=en.wikipedia.org&utm_campaign=index&utm_content=original" alt="Project Sekai">
                </div>

                <div class="tilt-container">
                    <div class="title-wrapper">
                        <h3 class="card-title">Audio Space</h3>
                    </div>
                </div>

                <div class="card-content">
                    <p>I primarily listen to J-pop and Vocaloid. I have a massive playlist of over 600 songs, though I tend to loop recent tracks.</p>
                    <div class="btn-group">
                        <a class="ocs_btn card-btn" href="https://youtube.com/playlist?list=PLrSSNb7pD0xFcy_ttT4B4tn8Ag-iBJ9qS&si=Eis16K00riS9n2al" target="_blank">View Playlist</a>
                    </div>
                </div>
            </div>

            <div class="semi-card right">
                <div class="flash-overlay"></div>
                
                <div class="image-panel">
                    <img src="https://images.unsplash.com/photo-1578632767115-351597cf2477?auto=format&fit=crop&q=80&w=400" alt="Anime Style Placeholder">
                </div>

                <div class="tilt-container">
                    <div class="title-wrapper">
                        <h3 class="card-title">Main Fandoms</h3>
                    </div>
                </div>

                <div class="card-content">
                    <p>When I am not working on projects, I am usually keeping up with Alien Stage, Chiikawa, and Project Sekai.</p>
                </div>
            </div>
        </div>
    </div>
</div>

<script>
    document.addEventListener("DOMContentLoaded", function() {
        const observerOptions = { root: null, rootMargin: '0px', threshold: 0.15 };
        const observer = new IntersectionObserver((entries, observer) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                    observer.unobserve(entry.target);
                }
            });
        }, observerOptions);

        document.querySelectorAll('.scroll-fade, .env-header, .semi-row').forEach((el) => {
            observer.observe(el);
        });

        // 2D Physics Particle Canvas
        const canvas = document.getElementById('particleCanvas');
        const ctx = canvas.getContext('2d');
        const wrapper = document.querySelector('.portfolio-wrapper');
        let width, height;

        function resizeCanvas() {
            width = canvas.width = wrapper.clientWidth;
            height = canvas.height = wrapper.scrollHeight;
        }
        window.addEventListener('resize', resizeCanvas);
        resizeCanvas();

        const particles = [];
        const numParticles = 60; 

        for(let i=0; i<numParticles; i++) {
            particles.push({
                x: Math.random() * width,
                y: Math.random() * height,
                vx: (Math.random() - 0.5) * 0.5,
                vy: -Math.random() * 1 - 0.5,
                radius: Math.random() * 2.5 + 1.5
            });
        }

        let mouse = { x: -1000, y: -1000 };
        wrapper.addEventListener('mousemove', (e) => {
            const rect = canvas.getBoundingClientRect();
            mouse.x = e.clientX - rect.left;
            mouse.y = e.clientY - rect.top;
        });

        function animateParticles() {
            ctx.clearRect(0, 0, width, height);
            
            for(let i=0; i<particles.length; i++) {
                let p = particles[i];
                p.x += p.vx;
                p.y += p.vy;

                p.vy -= 0.01;
                if(p.vy < -1.5) p.vy = -1.5;

                if (p.y + p.radius < 0) {
                    p.y = height + p.radius;
                    p.x = Math.random() * width;
                    p.vy = -Math.random() * 1 - 0.5;
                }
                if (p.x > width + p.radius) p.x = -p.radius;
                if (p.x < -p.radius) p.x = width + p.radius;

                let dx = mouse.x - p.x;
                let dy = mouse.y - p.y;
                let dist = Math.sqrt(dx*dx + dy*dy);
                if (dist < 100) {
                    let force = (100 - dist) / 100;
                    p.vx -= (dx / dist) * force * 0.6;
                    p.vy -= (dy / dist) * force * 0.6;
                }

                for(let j = i + 1; j < particles.length; j++) {
                    let p2 = particles[j];
                    let dx2 = p2.x - p.x;
                    let dy2 = p2.y - p.y;
                    let dist2 = Math.sqrt(dx2*dx2 + dy2*dy2);
                    let minDist = p.radius + p2.radius + 2; 

                    if (dist2 < minDist) {
                        let angle = Math.atan2(dy2, dx2);
                        let targetX = p.x + Math.cos(angle) * minDist;
                        let targetY = p.y + Math.sin(angle) * minDist;
                        let ax = (targetX - p2.x) * 0.05;
                        let ay = (targetY - p2.y) * 0.05;
                        p.vx -= ax;
                        p.vy -= ay;
                        p2.vx += ax;
                        p2.vy += ay;
                    }
                }
                
                p.vx *= 0.98;
                p.vy *= 0.98;

                ctx.beginPath();
                ctx.arc(p.x, p.y, p.radius, 0, Math.PI * 2);
                ctx.fillStyle = 'rgba(255, 255, 255, 0.4)';
                ctx.shadowBlur = 12;
                ctx.shadowColor = 'rgba(56, 189, 248, 0.6)'; 
                ctx.fill();
            }
            requestAnimationFrame(animateParticles);
        }
        animateParticles();
    });
</script>