<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Day 1: Rose Day 🌹</title>
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,700;1,700&family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
    <style>
        :root { --red: #ff4d6d; --white: #ffffff; }
        * { box-sizing: border-box; margin: 0; padding: 0; }
        
        body { 
            height: 100vh; width: 100vw; overflow: hidden; 
            font-family: 'Poppins', sans-serif; background: #000; 
        }

        .slide { 
            position: absolute; inset: 0; display: flex; flex-direction: column; 
            align-items: center; justify-content: center; text-align: center;
            opacity: 0; visibility: hidden; transition: opacity 1.5s ease-in-out;
        }
        .slide.active { opacity: 1; visibility: visible; }

        /* RAINBOW STYLE BG */
        .rainbow-bg {
            background: linear-gradient(45deg, #ff5f6d, #ffc371, #ff5f6d);
            background-size: 200% 200%;
            animation: rainbowFlow 5s ease infinite;
        }
        @keyframes rainbowFlow {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        /* INITIAL HEART ZOOM */
        #heart-focus { font-size: 5rem; transition: transform 2.5s ease-in, opacity 2s; }
        .zoom-heart { transform: scale(100); opacity: 0; }

        .btn { 
            padding: 18px 40px; border-radius: 50px; border: none; 
            font-weight: 600; background: white; color: var(--red); 
            cursor: pointer; box-shadow: 0 10px 25px rgba(0,0,0,0.2);
        }

        /* THE FILLING HEART (PARTIAL) */
        .heart-loader {
            position: relative; width: 120px; height: 110px;
            background: rgba(255, 255, 255, 0.2);
            clip-path: path('M60 102c-2 0-5-4-18-14C18 66 0 48 0 30 0 12 14 0 30 0c10 0 22 6 30 14 8-8 20-14 30-14 16 0 30 12 30 30 0 18-18 36-42 58-13 10-16 14-18 14z');
            margin-bottom: 20px;
        }
        .heart-fill-inner {
            position: absolute; bottom: 0; width: 100%; 
            height: 0%; /* Will animate to 14% */
            background: #fff; transition: height 6s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .status-text {
            color: white; opacity: 0; transition: 2s;
            font-size: 0.9rem; letter-spacing: 1px; margin-top: 10px;
        }
        .show-text { opacity: 0.8; }
    </style>
</head>
<body>

<audio id="mySong" loop playsinline><source src="https://fireofred17.github.io/VALENTINE_SPECIAL/tum-se.mp3" type="audio/mpeg"></audio>

<div class="slide active" id="s1">
    <h1 style="color: white; font-family: 'Playfair Display'; font-size: 3.5rem;">Hii Manuu...</h1>
    <button class="btn" style="margin-top: 40px;" onclick="startAutoJourney()">Open Day 1</button>
</div>

<div class="slide" id="s2">
    <div id="heart-focus">❤️</div>
</div>

<div class="slide rainbow-bg" id="s3">
    <div style="font-size: 6rem;">🌹</div>
    <h2 style="color: white; font-family: 'Playfair Display'; font-size: 3rem; margin-top: 10px;">Happy Rose Day</h2>
    <p style="color: white; margin-top: 20px; font-weight: 400; font-size: 1.2rem; padding: 0 35px; line-height: 1.6; font-style: italic; font-family: 'Playfair Display';">
        "They say roses are the symbol of beauty, but looking at you, even the most perfect rose feels like a second thought."
    </p>
</div>

<div class="slide" id="s4" style="background: #1a0509;">
    <div class="heart-loader">
        <div class="heart-fill-inner" id="mainFill"></div>
    </div>
    
    <div class="status-text" id="statusMsg">
        <p>Loading love: 14%</p>
        <p style="font-size: 0.7rem; margin-top: 15px; text-transform: uppercase;">To be fully filled on 14 Feb</p>
    </div>
</div>

<script>
    const song = document.getElementById('mySong');
    
    function startAutoJourney() {
        song.play();
        
        // 1. Move to Heart Transition
        showSlide('s1', 's2');

        // 2. Start Zoom
        setTimeout(() => {
            document.getElementById('heart-focus').classList.add('zoom-heart');
        }, 800);

        // 3. Move to Rose Day
        setTimeout(() => {
            showSlide('s2', 's3');
        }, 3000);

        // 4. Move to Heart Filling Slide
        setTimeout(() => {
            showSlide('s3', 's4');
            
            // Start the SLOW partial filling animation
            setTimeout(() => {
                const fill = document.getElementById('mainFill');
                fill.style.height = "14%"; // 1/7th of the way there!
                
                setTimeout(() => {
                    document.getElementById('statusMsg').classList.add('show-text');
                }, 4000); 
            }, 800);

        }, 11000); // 8 seconds for the quote
    }

    function showSlide(currentId, nextId) {
        document.getElementById(currentId).classList.remove('active');
        document.getElementById(nextId).classList.add('active');
    }
</script>
</body>
</html>
