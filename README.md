# Medical_Camp_
This website was created to provide an interactive and engaging experience for our university’s medical camp. It introduces the doctors, their specialties, and services in a fun, animated way while giving participants all the information they need. The goal is to make the medical camp accessible, informative, and easy to register.

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>University Medical Camp | Animated Intro</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css" rel="stylesheet">
    <style>
        :root {
            --med-blue: #0f4c81;
            --med-light: #e0f2fe;
            --med-green: #10b981;
        }

        body, html {
            margin: 0;
            padding: 0;
            overflow-x: hidden;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f8fafc;
        }

        /* Digital Rain Styles */
        #matrix-canvas {
            position: fixed;
            top: 0;
            left: 0;
            z-index: 50;
            background: black;
        }

        /* Page Transitions */
        .page {
            display: none;
            min-height: 100vh;
            width: 100%;
            padding: 20px;
            box-sizing: border-box;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            text-align: center;
        }

        .active-page {
            display: flex;
        }

        /* Banner Styling */
        .banner-container {
            position: relative;
            max-width: 100%;
            margin-top: 20px;
        }

        .welcome-banner-text {
            position: absolute;
            top: 15%;
            left: 50%;
            transform: translateX(-50%);
            width: 85%;
            background: rgba(255, 255, 255, 0.95);
            padding: 12px;
            border-radius: 12px;
            border: 4px solid var(--med-blue);
            font-weight: 900;
            color: var(--med-blue);
            font-size: 1.4rem;
            z-index: 10;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
            text-transform: uppercase;
        }

        /* Doctor Card Animation */
        .doctor-card {
            display: none;
            animation: slideInRight 0.8s ease-out forwards;
        }

        @keyframes slideInRight {
            from { transform: translateX(100%); opacity: 0; }
            to { transform: translateX(0); opacity: 1; }
        }

        /* Registration Form Styles */
        .form-input {
            width: 100%;
            padding: 14px;
            margin: 10px 0;
            border: 2px solid #e2e8f0;
            border-radius: 12px;
            font-size: 16px;
            background: #fff;
        }

        .img-responsive {
            width: 100%;
            max-width: 450px;
            height: auto;
            border-radius: 20px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
            object-fit: cover;
            background: #cbd5e1; /* Gray background until image loads */
        }

        @media (max-width: 640px) {
            .welcome-banner-text { font-size: 1.1rem; top: 10%; }
            h1 { font-size: 2rem; }
        }
    </style>
</head>
<body>

    <!-- Intro: Matrix Rain -->
    <canvas id="matrix-canvas"></canvas>

    <!-- Page 1: The Boom & Banner -->
    <section id="page1" class="page bg-white relative overflow-hidden">
        <div id="boom-overlay" class="hidden absolute inset-0 z-40 pointer-events-none flex items-center justify-center">
            <h1 class="text-7xl font-black text-blue-600 animate__animated animate__zoomIn">BOOM!</h1>
        </div>
        
        <div class="banner-container animate__animated animate__fadeInUp">
            <div class="welcome-banner-text">WELCOME TO OUR MEDICAL CAMP</div>
            <img src="image1.jpg" alt="Doctors Welcome" class="img-responsive" onerror="this.src='https://placehold.co/600x400?text=image1.jpg+Missing'">
        </div>
        <button onclick="nextPage(2)" class="mt-12 px-10 py-4 bg-blue-600 text-white rounded-full font-bold shadow-xl active:scale-95 transition-all">Meet Our Team →</button>
    </section>

    <!-- Page 2: Doctor Introductions -->
    <section id="page2" class="page bg-blue-50">
        <h2 class="text-2xl font-bold text-blue-900 mb-8">Meet Your Specialists</h2>
        
        <div id="doctor-display" class="w-full max-w-sm px-4">
            <!-- Doctor: Physiotherapist -->
            <div class="doctor-card active" id="doc-0">
                <div class="bg-white p-5 rounded-2xl shadow-xl border-b-8 border-blue-500">
                    <div class="bg-blue-600 text-white p-3 rounded-lg mb-4 font-bold animate__animated animate__bounceIn">
                        "Hi, I am a Physiotherapist. I specialize in restoring movement!"
                    </div>
                    <img src="image2.jpg" alt="Physiotherapist" class="img-responsive mb-2" onerror="this.src='https://placehold.co/400x500?text=image2.jpg+Missing'">
                </div>
            </div>

            <!-- Doctor: Sonologist -->
            <div class="doctor-card" id="doc-1">
                <div class="bg-white p-5 rounded-2xl shadow-xl border-b-8 border-green-500">
                    <div class="bg-green-600 text-white p-3 rounded-lg mb-4 font-bold animate__animated animate__bounceIn">
                        "Hello! I am your Sonologist. I use sound waves to see inside!"
                    </div>
                    <img src="image3.jpg" alt="Sonologist" class="img-responsive mb-2" onerror="this.src='https://placehold.co/400x500?text=image3.jpg+Missing'">
                </div>
            </div>

            <!-- Doctor: Gynecologist -->
            <div class="doctor-card" id="doc-2">
                <div class="bg-white p-5 rounded-2xl shadow-xl border-b-8 border-purple-500">
                    <div class="bg-purple-600 text-white p-3 rounded-lg mb-4 font-bold animate__animated animate__bounceIn">
                        "I am a Gynecologist, providing expert care for women's health."
                    </div>
                    <img src="image4.jpg" alt="Gynecologist" class="img-responsive mb-2" onerror="this.src='https://placehold.co/400x500?text=image4.jpg+Missing'">
                </div>
            </div>

            <!-- Doctor: Lab Technician -->
            <div class="doctor-card" id="doc-3">
                <div class="bg-white p-5 rounded-2xl shadow-xl border-b-8 border-red-500">
                    <div class="bg-red-600 text-white p-3 rounded-lg mb-4 font-bold animate__animated animate__bounceIn">
                        "I am the Lab Technician. Ensuring accurate diagnostic results!"
                    </div>
                    <img src="image5.jpg" alt="Lab Technician" class="img-responsive mb-2" onerror="this.src='https://placehold.co/400x500?text=image5.jpg+Missing'">
                </div>
            </div>
        </div>

        <div class="flex gap-4 mt-10">
            <button onclick="cycleDoctor()" id="next-doc-btn" class="px-8 py-3 bg-blue-600 text-white rounded-xl font-bold shadow-lg">Next Specialist</button>
            <button onclick="nextPage(3)" id="group-btn" class="hidden px-8 py-3 bg-green-600 text-white rounded-xl font-bold shadow-lg">Final Message →</button>
        </div>
    </section>

    <!-- Page 3: Group Welcome -->
    <section id="page3" class="page bg-white">
        <div class="w-full max-w-lg">
            <h2 class="text-3xl font-black text-blue-600 mb-6 animate__animated animate__pulse animate__infinite">WE ARE HERE FOR YOU</h2>
            <div class="bg-blue-50 p-6 rounded-3xl shadow-2xl border-4 border-blue-100">
                <p class="text-xl font-bold text-gray-800 mb-6 leading-relaxed">
                    "Join us for consultations, check-ups, and professional guidance. We welcome you all!"
                </p>
                <img src="image6.jpg" alt="Medical Team" class="img-responsive" onerror="this.src='https://placehold.co/600x400?text=image6.jpg+Missing'">
            </div>
            <button onclick="nextPage(4)" class="mt-10 px-12 py-5 bg-blue-600 text-white rounded-full font-black text-xl shadow-2xl transform transition hover:scale-105">REGISTER NOW</button>
        </div>
    </section>

    <!-- Page 4: Registration -->
    <section id="page4" class="page bg-gray-50">
        <div class="w-full max-w-md bg-white p-8 rounded-3xl shadow-2xl">
            <h2 class="text-3xl font-black text-gray-800 mb-2">Registration</h2>
            <p class="text-gray-500 mb-6 font-medium">Please enter your details below.</p>
            
            <form id="regForm" onsubmit="handleRegistration(event)">
                <input type="text" placeholder="Full Name" required class="form-input">
                <input type="email" placeholder="Email Address" required class="form-input">
                <input type="tel" placeholder="Contact Number" required class="form-input">
                
                <div class="flex gap-3">
                    <input type="number" placeholder="Age" required class="form-input w-1/3">
                    <select class="form-input w-2/3">
                        <option>Male</option>
                        <option>Female</option>
                        <option>Other</option>
                    </select>
                </div>

                <textarea placeholder="Medical Concern / History" rows="3" class="form-input"></textarea>
                
                <label class="flex items-center mt-4 text-sm font-semibold text-gray-700">
                    <input type="checkbox" required class="mr-3 h-6 w-6 rounded border-2 border-blue-500">
                    I agree to the camp terms.
                </label>

                <button type="submit" class="w-full mt-8 py-5 bg-green-600 text-white font-black text-xl rounded-2xl shadow-lg active:scale-95 transition-all">
                    SUBMIT DATA
                </button>
            </form>
            <div id="success-msg" class="hidden mt-6 p-6 bg-green-100 text-green-700 rounded-2xl text-center font-black text-xl border-2 border-green-500">
                REGISTRATION COMPLETE!
            </div>
        </div>
    </section>

    <!-- Audio Effects -->
    <audio id="sound-rain" loop src="https://assets.mixkit.co/active_storage/sfx/2557/2557-preview.mp3"></audio>
    <audio id="sound-pop" src="https://assets.mixkit.co/active_storage/sfx/2014/2014-preview.mp3"></audio>

    <script>
        const canvas = document.getElementById('matrix-canvas');
        const ctx = canvas.getContext('2d');
        const rainSound = document.getElementById('sound-rain');
        const popSound = document.getElementById('sound-pop');

        let width, height, columns;
        const characters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789';
        const fontSize = 20;
        let drops = [];

        function initMatrix() {
            width = canvas.width = window.innerWidth;
            height = canvas.height = window.innerHeight;
            columns = Math.floor(width / fontSize);
            drops = Array(columns).fill(1);
        }

        function drawMatrix() {
            ctx.fillStyle = 'rgba(0, 0, 0, 0.1)';
            ctx.fillRect(0, 0, width, height);
            ctx.fillStyle = '#10b981'; // Green rain
            ctx.font = 'bold ' + fontSize + 'px monospace';

            for (let i = 0; i < drops.length; i++) {
                const text = characters.charAt(Math.floor(Math.random() * characters.length));
                ctx.fillText(text, i * fontSize, drops[i] * fontSize);
                if (drops[i] * fontSize > height && Math.random() > 0.98) drops[i] = 0;
                drops[i]++;
            }
        }

        let matrixInterval;
        window.onload = () => {
            initMatrix();
            matrixInterval = setInterval(drawMatrix, 40);
            rainSound.play().catch(() => {});
            setTimeout(triggerBoom, 4000); // 4 Seconds of rain
        };

        function triggerBoom() {
            clearInterval(matrixInterval);
            rainSound.pause();
            canvas.style.display = 'none';
            popSound.play().catch(() => {});
            
            document.getElementById('boom-overlay').classList.remove('hidden');
            setTimeout(() => {
                document.getElementById('boom-overlay').classList.add('hidden');
                nextPage(1);
            }, 800);
        }

        function nextPage(num) {
            document.querySelectorAll('.page').forEach(p => p.classList.remove('active-page'));
            document.getElementById('page' + num).classList.add('active-page');
            window.scrollTo(0,0);
        }

        let currentDocIndex = 0;
        const totalDocs = 4;
        function cycleDoctor() {
            const currentDoc = document.getElementById('doc-' + currentDocIndex);
            currentDoc.style.display = 'none';
            currentDocIndex++;

            if (currentDocIndex < totalDocs) {
                const nextDoc = document.getElementById('doc-' + currentDocIndex);
                nextDoc.style.display = 'block';
            } else {
                document.getElementById('next-doc-btn').classList.add('hidden');
                document.getElementById('group-btn').classList.remove('hidden');
                document.getElementById('doctor-display').innerHTML = `
                    <div class="bg-white p-8 rounded-3xl shadow-xl text-blue-600 font-black text-2xl animate__animated animate__tada">
                        THE ENTIRE TEAM IS READY!
                    </div>
                `;
            }
        }

        function handleRegistration(e) {
            e.preventDefault();
            const btn = e.target.querySelector('button');
            btn.innerHTML = 'SAVING...';
            btn.disabled = true;

            setTimeout(() => {
                e.target.style.display = 'none';
                document.getElementById('success-msg').classList.remove('hidden');
            }, 1500);
        }

        window.addEventListener('resize', initMatrix);
    </script>
</body>
</html>

