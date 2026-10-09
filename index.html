<!DOCTYPE html>
<html lang="sv">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Halloween-kort</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Creepster&family=Cinzel:wght@600;800&family=Inter:wght@300;400;600&display=swap" rel="stylesheet">

  <style>
    body {
      font-family: 'Inter', sans-serif;
      background-color: #06040a;
      overflow-x: hidden;
    }

    .font-creepster {
      font-family: 'Creepster', cursive;
      letter-spacing: 2px;
    }

    .font-cinzel {
      font-family: 'Cinzel', serif;
    }

    /* 3D Scene setup */
    .perspective-scene {
      perspective: 2200px;
      perspective-origin: center center;
    }

    /* Card Book Base - shifts smoothly to center when opening/closing */
    .card-book {
      position: relative;
      transform-style: preserve-3d;
      transition: transform 0.85s cubic-bezier(0.35, 1, 0.45, 1);
    }

    /* When closed: spine shifts so cover is dead-center */
    .card-book.is-closed {
      transform: translateX(-50%);
    }

    /* When open: spine is dead-center so both open pages are balanced */
    .card-book.is-open {
      transform: translateX(0%);
    }

    /* The Hinged 3D Front Cover */
    .cover-flap {
      transform-origin: left center;
      transform-style: preserve-3d;
      transition: transform 0.85s cubic-bezier(0.35, 1, 0.45, 1);
      cursor: pointer;
    }

    .card-book.is-closed .cover-flap {
      transform: rotateY(0deg);
    }

    .card-book.is-open .cover-flap {
      transform: rotateY(-180deg);
      cursor: default;
    }

    /* Faces with 3D backface cull */
    .flap-face {
      position: absolute;
      inset: 0;
      width: 100%;
      height: 100%;
      backface-visibility: hidden;
      -webkit-backface-visibility: hidden;
      border-radius: 1rem;
    }

    .flap-front {
      z-index: 10;
      transform: rotateY(0deg);
    }

    .flap-back {
      transform: rotateY(180deg);
      z-index: 5;
    }

    /* Backgrounds & Textures */
    .parchment {
      background: linear-gradient(135deg, #160e1f 0%, #20132b 50%, #11081a 100%);
      box-shadow: inset 0 0 50px rgba(0, 0, 0, 0.85);
    }

    .cover-bg {
      background: radial-gradient(circle at 50% 40%, #3a1505 0%, #1d0a02 65%, #080301 100%);
      box-shadow: inset 0 0 45px rgba(0, 0, 0, 0.9);
    }

    /* Realistic Center Spine Shadow */
    .spine-crease {
      position: absolute;
      top: 0;
      bottom: 0;
      left: 0;
      width: 38px;
      transform: translateX(-50%);
      background: linear-gradient(to right, rgba(0,0,0,0.65), transparent 45%, transparent 55%, rgba(0,0,0,0.65));
      pointer-events: none;
      z-index: 40;
    }

    /* Glow flickers */
    @keyframes glowFlicker {
      0%, 100% {
        filter: drop-shadow(0 0 12px #ff8c00) drop-shadow(0 0 24px rgba(255, 140, 0, 0.6));
      }
      50% {
        filter: drop-shadow(0 0 6px #ff5500) drop-shadow(0 0 12px rgba(255, 85, 0, 0.4));
      }
    }

    .flicker-glow {
      animation: glowFlicker 2s infinite ease-in-out;
    }

    /* Steam bubbles */
    @keyframes bubbleUp {
      0% { transform: translateY(0) scale(0.6); opacity: 0.2; }
      50% { opacity: 0.9; }
      100% { transform: translateY(-24px) scale(1.2); opacity: 0; }
    }

    .bubble-1 { animation: bubbleUp 1.8s infinite ease-in; }
    .bubble-2 { animation: bubbleUp 2.2s infinite ease-in 0.5s; }
    .bubble-3 { animation: bubbleUp 1.6s infinite ease-in 1s; }

    /* Flying treats */
    @keyframes flyPop {
      0% {
        transform: translate(-50%, -50%) scale(0.2) rotate(0deg);
        opacity: 1;
      }
      100% {
        transform: translate(var(--tx), var(--ty)) scale(1.35) rotate(var(--tr));
        opacity: 0;
      }
    }

    .candy-particle {
      position: absolute;
      pointer-events: none;
      animation: flyPop 1.1s cubic-bezier(0.1, 0.8, 0.2, 1) forwards;
      z-index: 100;
    }
  </style>
</head>
<body class="min-h-screen text-gray-200 select-none flex flex-col justify-between relative overflow-y-auto">

  <!-- Ambient Sky Canvas -->
  <canvas id="ambient-canvas" class="fixed inset-0 pointer-events-none z-0"></canvas>

  <!-- Glowing Moon -->
  <div class="fixed top-8 right-8 sm:right-20 w-28 h-28 sm:w-44 sm:h-44 rounded-full bg-gradient-to-br from-amber-100 via-orange-100 to-amber-200/90 pointer-events-none z-0 shadow-[0_0_80px_25px_rgba(255,170,50,0.2)] opacity-85">
    <div class="absolute top-6 left-8 w-6 h-6 rounded-full bg-orange-950/10 blur-[1px]"></div>
    <div class="absolute bottom-9 left-12 w-10 h-10 rounded-full bg-orange-950/10 blur-[2px]"></div>
  </div>

  <!-- Header Controls -->
  <header class="relative z-50 w-full max-w-5xl mx-auto px-4 pt-4 flex flex-wrap gap-2 justify-between items-center">
    <div class="flex items-center space-x-2">
      <span class="text-3xl filter drop-shadow">🎃</span>
      <span class="text-xl sm:text-2xl font-bold font-creepster text-orange-500 tracking-wider">
        HALLOWEEN
      </span>
    </div>

    <div class="flex items-center space-x-2">
      <!-- Toggle Card Button (Folds and Unfolds the 3D cover) -->
      <button id="card-toggle-btn" class="px-4 py-1.5 rounded-full bg-orange-600 hover:bg-orange-500 text-black font-semibold text-xs sm:text-sm shadow-[0_0_15px_rgba(234,88,12,0.6)] transition-all active:scale-95 flex items-center gap-1.5 cursor-pointer">
        <span id="card-toggle-icon">📖</span>
        <span id="card-toggle-text">Öppna kortet</span>
      </button>

      <!-- Audio Button -->
      <button id="sound-btn" class="px-3.5 py-1.5 rounded-full bg-zinc-900/90 border border-orange-500/40 text-orange-400 hover:text-white transition-colors text-xs sm:text-sm backdrop-blur cursor-pointer">
        <span id="sound-icon">🔇</span> Ljud: Av
      </button>

      <!-- Thunder Button -->
      <button id="thunder-btn" class="px-3 py-1.5 rounded-full bg-purple-900/40 border border-purple-500/50 text-purple-300 hover:bg-purple-800/60 transition-colors text-xs sm:text-sm cursor-pointer">
        ⚡ Åska
      </button>
    </div>
  </header>

  <!-- Main Presentation Area with Responsive 3D Book -->
  <main class="relative z-30 flex-1 flex flex-col items-center justify-center p-3 sm:p-6 my-auto">

    <!-- Scaler container so the card fits all phone screens perfectly without clipping -->
    <div id="card-scaler" class="transition-transform duration-300 flex items-center justify-center">

      <div class="perspective-scene py-4">
        
        <!-- CARD BOOK: Fixed spine along x=0. Base page is on the right, Flap flips to the left! -->
        <div id="card-book" class="card-book is-closed w-[340px] sm:w-[380px] h-[510px]">

          <!-- SPINE CREASE SHADOW (Appears down the middle when open) -->
          <div id="spine-shadow" class="spine-crease opacity-0 transition-opacity duration-700"></div>

          <!-- 1. BASE PAGE (Inside Right: The Poem & Names) -->
          <div class="absolute inset-0 w-full h-full parchment rounded-2xl border-2 border-orange-500/40 shadow-[0_20px_50px_rgba(0,0,0,0.9)] p-6 sm:p-7 flex flex-col justify-between z-10 overflow-hidden">
            <div>
              <div class="flex items-center justify-between border-b border-orange-500/25 pb-2 mb-3">
                <span class="text-xs uppercase tracking-widest text-orange-400 font-cinzel">Hösthälsning</span>
                <span class="text-xs text-orange-400">🍂 31 Oktober</span>
              </div>

              <!-- Halloween Poem (No personal/flattering text) -->
              <div class="bg-black/45 border-l-2 border-orange-500/60 pl-3.5 py-2.5 my-2.5 rounded-r">
                <p class="font-serif italic text-xs sm:text-sm text-stone-200 leading-relaxed whitespace-pre-line">
När höststormen viner och skymningen sänks,
och lyktorna tänds där man minst av allt tänks.
Då dansar skelett och små spöken på tå,
och pumporna lyser i natten så blå.
Må helgen ge vila från schema och flit,
med spänning och godis från hit och till dit!
                </p>
              </div>

              <!-- Till & Från Fält -->
              <div class="mt-4 space-y-2.5">
                <div>
                  <label class="block text-[11px] font-semibold tracking-wide text-orange-300 uppercase">Till:</label>
                  <input id="recipient-input" type="text" placeholder="Skriv namn här..." 
                    class="w-full bg-zinc-900/90 border border-orange-500/40 rounded px-2.5 py-1.5 text-xs text-white placeholder-stone-500 focus:outline-none focus:border-orange-400">
                </div>

                <div>
                  <label class="block text-[11px] font-semibold tracking-wide text-orange-300 uppercase">Från:</label>
                  <input id="sender-input" type="text" placeholder="Ditt eller era namn..." 
                    class="w-full bg-zinc-900/90 border border-orange-500/40 rounded px-2.5 py-1.5 text-xs text-white placeholder-stone-500 focus:outline-none focus:border-orange-400">
                </div>
              </div>
            </div>

            <!-- Bottom Close Action Bar -->
            <div class="pt-3 border-t border-orange-500/20 flex items-center justify-between text-xs">
              <span id="sender-display" class="font-cinzel text-orange-300 font-bold truncate max-w-[150px]">
                Från: Vännerna
              </span>

              <button id="close-card-btn" class="px-3.5 py-1.5 bg-orange-950/80 hover:bg-orange-900 text-orange-200 rounded border border-orange-500/40 text-xs font-medium transition-all active:scale-95 cursor-pointer">
                Stäng kortet ✕
              </button>
            </div>
          </div>

          <!-- 2. HINGED 3D COVER FLAP (Flips 180° like a real book cover) -->
          <div id="cover-flap" class="cover-flap absolute inset-0 w-full h-full z-20">

            <!-- FRONT OF COVER (Visible when closed) -->
            <div id="flap-front" class="flap-face flap-front cover-bg border-2 border-orange-500/50 p-6 sm:p-7 flex flex-col items-center justify-between text-center shadow-[0_20px_60px_rgba(0,0,0,0.95)]">
              
              <!-- Spiderweb decoration -->
              <svg class="absolute top-2 left-2 w-16 h-16 opacity-30 text-orange-400 pointer-events-none" viewBox="0 0 100 100" fill="none" stroke="currentColor">
                <path d="M0 0 L100 0 C70 30 70 70 0 100 L0 0 Z" stroke-width="1.5"/>
                <path d="M0 0 L70 70 M0 35 C35 35 35 35 35 0 M0 70 C70 70 70 70 70 0" stroke-width="1.2"/>
              </svg>

              <!-- Cover Title -->
              <div class="mt-2 space-y-1">
                <p class="text-[11px] uppercase tracking-widest text-orange-400/90 font-cinzel">En stämningsfull hälsning</p>
                <h1 class="text-4xl sm:text-5xl font-creepster text-orange-500 tracking-wider drop-shadow-[0_2px_12px_rgba(255,115,0,0.8)]">
                  GLAD HALLOWEEN!
                </h1>
                <p id="cover-sub-label" class="text-orange-200/90 font-cinzel text-xs sm:text-sm">
                  I Höstmörkrets Tid
                </p>
              </div>

              <!-- Pumpkin SVG -->
              <div class="relative my-2 flex items-center justify-center">
                <div class="absolute w-36 h-36 rounded-full bg-orange-600/20 blur-xl"></div>
                <svg class="w-40 h-40 sm:w-44 sm:h-44 flicker-glow" viewBox="0 0 200 200">
                  <path d="M92 28 C90 10 114 12 108 44 Z" fill="#2d5a27" stroke="#1b3d16" stroke-width="2"/>
                  <ellipse cx="64" cy="115" rx="36" ry="58" fill="#d9480f" />
                  <ellipse cx="136" cy="115" rx="36" ry="58" fill="#d9480f" />
                  <ellipse cx="80" cy="118" rx="33" ry="62" fill="#e8590c" />
                  <ellipse cx="120" cy="118" rx="33" ry="62" fill="#e8590c" />
                  <ellipse cx="100" cy="120" rx="35" ry="64" fill="#f76707" />
                  
                  <polygon points="70,88 88,105 60,105" fill="#fff3bf" />
                  <polygon points="130,88 140,105 112,105" fill="#fff3bf" />
                  <polygon points="100,108 108,122 92,122" fill="#fff3bf" />
                  
                  <path d="M58 135 Q100 175 142 135 Q135 152 122 152 L122 143 L110 143 L110 155 Q100 157 90 155 L90 144 L78 144 L78 150 Q66 148 58 135 Z" fill="#fff9db"/>
                </svg>
              </div>

              <!-- Click to open prompt -->
              <div class="mb-1 inline-flex items-center space-x-2 px-4 py-2 rounded-full bg-orange-950/80 border border-orange-500/50 text-orange-300 text-xs sm:text-sm font-semibold tracking-wide shadow-lg">
                <span>✨ Klicka här för att öppna</span>
                <span>➔</span>
              </div>
            </div>

            <!-- BACK OF COVER (Inside Left: Witch Cauldron, visible when open) -->
            <div id="flap-back" class="flap-face flap-back parchment border-2 border-orange-500/40 p-6 sm:p-7 flex flex-col justify-between shadow-[0_20px_50px_rgba(0,0,0,0.9)]">
              <div>
                <div class="flex items-center justify-between border-b border-orange-500/25 pb-2 mb-2">
                  <span class="text-xs uppercase tracking-widest text-orange-400 font-cinzel">Häxans Kittel</span>
                  <span class="text-xs text-purple-300">✨ Magiskt brygg</span>
                </div>
                <p class="text-xs text-stone-300 leading-relaxed">
                  Rör runt i den puttrande grytan för att brygga fram bus och godis!
                </p>
              </div>

              <!-- Cauldron Graphic & Bubbles -->
              <div class="relative py-2 flex flex-col items-center justify-center">
                <!-- Rising Green Steam Bubbles -->
                <div class="relative w-28 h-7 flex justify-center items-end">
                  <span class="bubble-1 absolute left-6 w-3 h-3 rounded-full bg-lime-400/80 blur-[1px]"></span>
                  <span class="bubble-2 absolute left-12 w-4 h-4 rounded-full bg-emerald-400/80 blur-[1px]"></span>
                  <span class="bubble-3 absolute right-6 w-3.5 h-3.5 rounded-full bg-green-300/80 blur-[1px]"></span>
                </div>

                <!-- Clickable Cauldron -->
                <div id="cauldron-container" class="relative cursor-pointer transition-transform duration-200 hover:scale-105 active:scale-95" title="Klicka på grytan!">
                  <svg class="w-36 h-32 sm:w-40 sm:h-36 drop-shadow-[0_12px_22px_rgba(0,0,0,0.95)]" viewBox="0 0 200 170">
                    <ellipse cx="100" cy="55" rx="66" ry="18" fill="#15803d" />
                    <ellipse cx="100" cy="54" rx="58" ry="13" fill="#4ade80" filter="drop-shadow(0 0 8px #4ade80)" />
                    <ellipse cx="100" cy="53" rx="46" ry="9" fill="#a3e635" />
                    <path d="M35 55 Q20 120 70 145 Q100 152 130 145 Q180 120 165 55 Z" fill="#18181b" stroke="#3f3f46" stroke-width="3"/>
                    <ellipse cx="100" cy="55" rx="72" ry="14" fill="none" stroke="#52525b" stroke-width="5"/>
                    <path d="M30 65 Q12 75 28 92" fill="none" stroke="#71717a" stroke-width="4" stroke-linecap="round"/>
                    <path d="M170 65 Q188 75 172 92" fill="none" stroke="#71717a" stroke-width="4" stroke-linecap="round"/>
                    <path d="M55 142 L42 162" stroke="#27272a" stroke-width="7" stroke-linecap="round"/>
                    <path d="M145 142 L158 162" stroke="#27272a" stroke-width="7" stroke-linecap="round"/>
                  </svg>
                </div>

                <!-- Stir Button -->
                <button id="stir-btn" type="button" class="mt-3 px-4 py-2 bg-gradient-to-r from-emerald-600 to-lime-600 hover:from-emerald-500 hover:to-lime-500 text-black font-bold text-xs uppercase tracking-wider rounded-lg shadow-lg shadow-emerald-950/60 transition-all active:scale-95 cursor-pointer">
                  🥄 Rör om i grytan!
                </button>
              </div>

              <!-- Treat Box -->
              <div id="treat-box" class="p-2.5 rounded-lg bg-black/60 border border-emerald-500/40 text-center text-xs sm:text-sm font-medium text-lime-300 min-h-[44px] flex items-center justify-center transition-all">
                Klicka på grytan eller knappen! 🦇
              </div>
            </div>

          </div>

        </div>

      </div>

    </div>

  </main>

  <!-- Footer -->
  <footer class="relative z-40 py-3 text-center text-xs text-stone-500 bg-black/70 border-t border-zinc-900">
    <p>Halloween-kort • Skapat för att sprida höstglädje</p>
  </footer>

  <script>
    /* -------------------------------------------------------------
       1. WEB AUDIO API SYNTHESIZER (No external sound files)
       ------------------------------------------------------------- */
    let audioCtx = null;
    let isSoundOn = false;

    function getAudioContext() {
      if (!audioCtx) {
        audioCtx = new (window.AudioContext || window.webkitAudioContext)();
      }
      if (audioCtx.state === 'suspended') {
        audioCtx.resume();
      }
      return audioCtx;
    }

    /* Card Opening / Closing Paper Whoosh */
    function playFlipSound(isClosing = false) {
      if (!isSoundOn) return;
      const ctx = getAudioContext();
      const osc = ctx.createOscillator();
      const gain = ctx.createGain();

      osc.type = 'sine';
      if (isClosing) {
        osc.frequency.setValueAtTime(160, ctx.currentTime);
        osc.frequency.exponentialRampToValueAtTime(70, ctx.currentTime + 0.3);
      } else {
        osc.frequency.setValueAtTime(80, ctx.currentTime);
        osc.frequency.exponentialRampToValueAtTime(180, ctx.currentTime + 0.3);
      }

      gain.gain.setValueAtTime(0.01, ctx.currentTime);
      gain.gain.linearRampToValueAtTime(0.22, ctx.currentTime + 0.08);
      gain.gain.exponentialRampToValueAtTime(0.001, ctx.currentTime + 0.32);

      osc.connect(gain);
      gain.connect(ctx.destination);

      osc.start();
      osc.stop(ctx.currentTime + 0.33);
    }

    /* Chime sound for open & treats */
    function playChimeSound() {
      if (!isSoundOn) return;
      const ctx = getAudioContext();
      [392, 523.25, 659.25, 783.99].forEach((f, i) => {
        const osc = ctx.createOscillator();
        const gain = ctx.createGain();
        osc.type = 'triangle';
        osc.frequency.setValueAtTime(f, ctx.currentTime + (i * 0.07));

        gain.gain.setValueAtTime(0.07, ctx.currentTime + (i * 0.07));
        gain.gain.exponentialRampToValueAtTime(0.001, ctx.currentTime + 0.5 + (i * 0.07));

        osc.connect(gain);
        gain.connect(ctx.destination);

        osc.start(ctx.currentTime + (i * 0.07));
        osc.stop(ctx.currentTime + 0.6 + (i * 0.07));
      });
    }

    /* Potion bubble sound */
    function playBubbleSound() {
      if (!isSoundOn) return;
      const ctx = getAudioContext();
      const osc = ctx.createOscillator();
      const gain = ctx.createGain();

      osc.type = 'sine';
      osc.frequency.setValueAtTime(260 + Math.random() * 200, ctx.currentTime);
      osc.frequency.exponentialRampToValueAtTime(750, ctx.currentTime + 0.12);

      gain.gain.setValueAtTime(0.18, ctx.currentTime);
      gain.gain.exponentialRampToValueAtTime(0.001, ctx.currentTime + 0.14);

      osc.connect(gain);
      gain.connect(ctx.destination);

      osc.start();
      osc.stop(ctx.currentTime + 0.15);
    }

    /* Thunder crash sound */
    function playThunderSound() {
      const ctx = getAudioContext();
      const bufferSize = ctx.sampleRate * 1.5;
      const buffer = ctx.createBuffer(1, bufferSize, ctx.sampleRate);
      const data = buffer.getChannelData(0);

      let last = 0.0;
      for (let i = 0; i < bufferSize; i++) {
        const white = Math.random() * 2 - 1;
        data[i] = (last + (0.03 * white)) / 1.03;
        last = data[i];
        data[i] *= 3.0;
      }

      const noise = ctx.createBufferSource();
      noise.buffer = buffer;

      const filter = ctx.createBiquadFilter();
      filter.type = 'lowpass';
      filter.frequency.setValueAtTime(260, ctx.currentTime);
      filter.frequency.exponentialRampToValueAtTime(50, ctx.currentTime + 1.4);

      const gain = ctx.createGain();
      gain.gain.setValueAtTime(0.35, ctx.currentTime);
      gain.gain.exponentialRampToValueAtTime(0.001, ctx.currentTime + 1.5);

      noise.connect(filter);
      filter.connect(gain);
      gain.connect(ctx.destination);

      noise.start();
    }

    /* -------------------------------------------------------------
       2. CONTROLS SETUP
       ------------------------------------------------------------- */
    const soundBtn = document.getElementById('sound-btn');
    const soundIcon = document.getElementById('sound-icon');
    const thunderBtn = document.getElementById('thunder-btn');

    soundBtn.addEventListener('click', (e) => {
      e.stopPropagation();
      isSoundOn = !isSoundOn;
      if (isSoundOn) {
        getAudioContext();
        soundIcon.textContent = '🔊';
        soundBtn.innerHTML = `<span>🔊</span> Ljud: På`;
        soundBtn.classList.add('bg-orange-600/40', 'border-orange-400');
        playChimeSound();
      } else {
        soundBtn.innerHTML = `<span>🔇</span> Ljud: Av`;
        soundBtn.classList.remove('bg-orange-600/40', 'border-orange-400');
      }
    });

    thunderBtn.addEventListener('click', (e) => {
      e.stopPropagation();
      playThunderSound();

      const flash = document.createElement('div');
      flash.className = 'fixed inset-0 bg-white/70 z-50 pointer-events-none transition-opacity duration-150';
      document.body.appendChild(flash);
      setTimeout(() => {
        flash.style.opacity = '0';
        setTimeout(() => flash.remove(), 160);
      }, 70);
    });

    /* -------------------------------------------------------------
       3. 3D FOLD CARD OPEN & CLOSE ENGINE
       ------------------------------------------------------------- */
    const cardBook = document.getElementById('card-book');
    const coverFlap = document.getElementById('cover-flap');
    const flapFront = document.getElementById('flap-front');
    const spineShadow = document.getElementById('spine-shadow');
    const cardToggleBtn = document.getElementById('card-toggle-btn');
    const cardToggleText = document.getElementById('card-toggle-text');
    const cardToggleIcon = document.getElementById('card-toggle-icon');
    const closeCardBtn = document.getElementById('close-card-btn');

    let isOpen = false;

    function openCard() {
      if (isOpen) return;
      isOpen = true;

      // 3D Flip Open
      cardBook.classList.remove('is-closed');
      cardBook.classList.add('is-open');

      // Show spine crease shadow
      spineShadow.classList.remove('opacity-0');
      spineShadow.classList.add('opacity-100');

      // Update button text
      cardToggleText.textContent = 'Stäng kortet';
      cardToggleIcon.textContent = '📕';

      playFlipSound(false);
      setTimeout(() => playChimeSound(), 300);
    }

    function closeCard() {
      if (!isOpen) return;
      isOpen = false;

      // 3D Flip Closed (folds cover back like the original card!)
      cardBook.classList.remove('is-open');
      cardBook.classList.add('is-closed');

      // Hide spine crease shadow
      spineShadow.classList.add('opacity-0');
      spineShadow.classList.remove('opacity-100');

      // Update button text
      cardToggleText.textContent = 'Öppna kortet';
      cardToggleIcon.textContent = '📖';

      playFlipSound(true);
    }

    function toggleCard() {
      if (isOpen) {
        closeCard();
      } else {
        openCard();
      }
    }

    // Clicking the front cover when closed opens it
    flapFront.addEventListener('click', () => {
      if (!isOpen) openCard();
    });

    // Top action bar button toggles
    cardToggleBtn.addEventListener('click', (e) => {
      e.stopPropagation();
      toggleCard();
    });

    // Inside close button shuts the card
    closeCardBtn.addEventListener('click', (e) => {
      e.stopPropagation();
      closeCard();
    });

    /* -------------------------------------------------------------
       4. WITCH CAULDRON ACTIONS & CANDY BURSTS
       ------------------------------------------------------------- */
    const cauldronContainer = document.getElementById('cauldron-container');
    const stirBtn = document.getElementById('stir-btn');
    const treatBox = document.getElementById('treat-box');

    const treats = [
      '🍬 Geléhallon & spökfika!',
      '🍫 Chokladfladdermus upphittad!',
      '🍭 Spökklubba med citronsmak!',
      '🎃 Magisk pumpakaka till alla!',
      '✨ En stunds lugn & fikarast!',
      '🦇 En flock snälla fladdermöss!',
      '🍪 Nybakade kanelbullar!'
    ];

    const burstIcons = ['🍬', '🍫', '🍭', '🎃', '✨', '🦇', '⭐', '🕸️'];

    function stirCauldron(e) {
      if (e) e.stopPropagation();
      playBubbleSound();

      cauldronContainer.style.transform = 'scale(1.15) rotate(-6deg)';
      setTimeout(() => {
        cauldronContainer.style.transform = 'scale(1) rotate(0deg)';
      }, 240);

      const randomMsg = treats[Math.floor(Math.random() * treats.length)];
      treatBox.textContent = randomMsg;
      treatBox.classList.add('border-lime-400', 'bg-lime-950/50');
      setTimeout(() => {
        treatBox.classList.remove('bg-lime-950/50');
      }, 400);

      // Spawn flying candy bursts
      const rect = cauldronContainer.getBoundingClientRect();
      const originX = rect.left + rect.width / 2;
      const originY = rect.top + 30;

      for (let i = 0; i < 7; i++) {
        const el = document.createElement('div');
        el.className = 'candy-particle text-2xl';
        el.textContent = burstIcons[Math.floor(Math.random() * burstIcons.length)];

        const tx = (Math.random() - 0.5) * 180 + 'px';
        const ty = -(Math.random() * 120 + 40) + 'px';
        const tr = (Math.random() * 360 - 180) + 'deg';

        el.style.left = `${originX}px`;
        el.style.top = `${originY}px`;
        el.style.setProperty('--tx', tx);
        el.style.setProperty('--ty', ty);
        el.style.setProperty('--tr', tr);

        document.body.appendChild(el);
        setTimeout(() => el.remove(), 1100);
      }
    }

    cauldronContainer.addEventListener('click', stirCauldron);
    stirBtn.addEventListener('click', stirCauldron);

    /* -------------------------------------------------------------
       5. INPUTS
       ------------------------------------------------------------- */
    const recipientInput = document.getElementById('recipient-input');
    const senderInput = document.getElementById('sender-input');
    const coverSubLabel = document.getElementById('cover-sub-label');
    const senderDisplay = document.getElementById('sender-display');

    recipientInput.addEventListener('input', (e) => {
      const val = e.target.value.trim();
      coverSubLabel.textContent = val ? `Till: ${val}` : 'I Höstmörkrets Tid';
    });

    senderInput.addEventListener('input', (e) => {
      const val = e.target.value.trim();
      senderDisplay.textContent = val ? `Från: ${val}` : 'Från: Vännerna';
    });

    /* -------------------------------------------------------------
       6. DYNAMIC SCALE ENGINE FOR MOBILE SCREENS
       ------------------------------------------------------------- */
    function adjustCardScale() {
      const scaler = document.getElementById('card-scaler');
      // When opened, the 2-page spread is ~760px wide; on small devices we scale it smoothly
      const screenWidth = window.innerWidth;
      const targetWidth = isOpen ? 790 : 400;

      if (screenWidth < targetWidth) {
        const factor = Math.max(0.46, (screenWidth - 20) / targetWidth);
        scaler.style.transform = `scale(${factor})`;
      } else {
        scaler.style.transform = 'scale(1)';
      }
    }

    window.addEventListener('resize', adjustCardScale);
    // Also re-adjust when opening/closing
    const originalOpen = openCard;
    openCard = function() {
      originalOpen();
      adjustCardScale();
    };
    const originalClose = closeCard;
    closeCard = function() {
      originalClose();
      adjustCardScale();
    };

    /* -------------------------------------------------------------
       7. AMBIENT BACKGROUND PARTICLES & BATS
       ------------------------------------------------------------- */
    const canvas = document.getElementById('ambient-canvas');
    const ctx = canvas.getContext('2d');
    let width, height;

    function resizeCanvas() {
      width = canvas.width = window.innerWidth;
      height = canvas.height = window.innerHeight;
    }
    window.addEventListener('resize', resizeCanvas);
    resizeCanvas();

    class MistParticle {
      constructor() { this.reset(); }
      reset() {
        this.x = Math.random() * width;
        this.y = height - Math.random() * (height * 0.45);
        this.r = Math.random() * 90 + 50;
        this.vx = Math.random() * 0.3 - 0.15;
        this.vy = -(Math.random() * 0.2 + 0.05);
        this.alpha = Math.random() * 0.07 + 0.02;
      }
      update() {
        this.x += this.vx;
        this.y += this.vy;
        if (this.y < height * 0.4) this.reset();
      }
      draw() {
        ctx.beginPath();
        const grad = ctx.createRadialGradient(this.x, this.y, 0, this.x, this.y, this.r);
        grad.addColorStop(0, `rgba(160, 140, 210, ${this.alpha})`);
        grad.addColorStop(1, 'rgba(0,0,0,0)');
        ctx.fillStyle = grad;
        ctx.arc(this.x, this.y, this.r, 0, Math.PI * 2);
        ctx.fill();
      }
    }

    class AmbientBat {
      constructor() {
        this.x = Math.random() * width;
        this.y = Math.random() * (height * 0.6);
        this.speed = Math.random() * 1.8 + 1.2;
        this.size = Math.random() * 7 + 7;
        this.wingAngle = Math.random() * Math.PI;
        this.direction = Math.random() > 0.5 ? 1 : -1;
      }
      update() {
        this.x += this.speed * this.direction;
        this.y += Math.sin(this.x * 0.02) * 0.9;
        this.wingAngle += 0.25;

        if (this.direction === 1 && this.x > width + 40) {
          this.x = -40;
          this.y = Math.random() * (height * 0.6);
        } else if (this.direction === -1 && this.x < -40) {
          this.x = width + 40;
          this.y = Math.random() * (height * 0.6);
        }
      }
      draw() {
        ctx.save();
        ctx.translate(this.x, this.y);
        ctx.scale(this.direction, 1);
        ctx.fillStyle = '#1e1627';

        const wing = Math.sin(this.wingAngle) * (this.size * 0.7);
        ctx.beginPath();
        ctx.ellipse(0, 0, this.size * 0.3, this.size * 0.5, 0, 0, Math.PI * 2);
        ctx.moveTo(0, 0);
        ctx.quadraticCurveTo(-this.size, -this.size - wing, -this.size * 1.7, -wing);
        ctx.quadraticCurveTo(-this.size * 0.8, 0, 0, this.size * 0.2);
        ctx.moveTo(0, 0);
        ctx.quadraticCurveTo(this.size, -this.size - wing, this.size * 1.7, -wing);
        ctx.quadraticCurveTo(this.size * 0.8, 0, 0, this.size * 0.2);
        ctx.fill();
        ctx.restore();
      }
    }

    const mistList = Array.from({ length: 24 }, () => new MistParticle());
    const batList = Array.from({ length: 8 }, () => new AmbientBat());

    function renderLoop() {
      ctx.clearRect(0, 0, width, height);
      mistList.forEach(m => { m.update(); m.draw(); });
      batList.forEach(b => { b.update(); b.draw(); });
      requestAnimationFrame(renderLoop);
    }

    window.onload = () => {
      adjustCardScale();
      renderLoop();
    };
  </script>
</body>
</html>
