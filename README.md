<!-- DeBeatzGH Multi-Form Launcher Console -->
<div id="debeatzgh-launcher-system">
    <!-- Floating Trigger Node -->
    <button id="portal-floating-trigger" onclick="openFormPortal()" title="Launch Form Portal">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
            <path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"></path>
            <polyline points="14 2 14 8 20 8"></polyline>
            <line x1="16" y1="13" x2="8" y2="13"></line>
            <line x1="16" y1="17" x2="8" y2="17"></line>
            <polyline points="10 9 9 9 8 9"></polyline>
        </svg>
    </button>

    <!-- Modal Backdrop Overlay -->
    <div id="portal-modal-overlay" onclick="triggerBlockShake()">
        <!-- Interactive Panel Base -->
        <div id="portal-console-card" onclick="event.stopPropagation()">
            <div class="console-title-row">
                <div class="console-brand-meta">
                    <span class="brand-glow-dot"></span>
                    <h6>DeBeatzGH Centralized Intake</h6>
                </div>
                <button class="console-close-btn" onclick="closeFormPortal()" title="Close Portal">✕</button>
            </div>
            
            <p class="console-instructions">Select your required data profile channel below. Fill out and submit your production fields completely inside the frame before dismissing the panel view.</p>
            
            <!-- Tab Selection Rail -->
            <div class="console-tab-rail">
                <button class="console-tab active" onclick="switchFormChannel(this, 0)">Channel 1</button>
                <button class="console-tab" onclick="switchFormChannel(this, 1)">Channel 2</button>
                <button class="console-tab" onclick="switchFormChannel(this, 2)">Channel 3</button>
            </div>

            <!-- Frame Container Core -->
            <div class="console-frame-container">
                <div class="frame-loading-overlay" id="frameLoader">Compiling Form Data Stream...</div>
                <iframe id="portalIntakeFrame" src="" onload="hideFrameLoader()"></iframe>
            </div>
        </div>
    </div>
</div>

<style>
    /* Floating Launcher Element with Heartbeat Engine */
    #portal-floating-trigger {
        position: fixed;
        top: 24px;
        left: 24px;
        width: 60px;
        height: 60px;
        border-radius: 50%;
        background: linear-gradient(135deg, #bc6cff, #58a6ff);
        border: 1px solid rgba(250, 251, 252, 0.25);
        color: #ffffff;
        cursor: pointer;
        display: flex;
        justify-content: center;
        align-items: center;
        box-shadow: 0 8px 24px rgba(188, 108, 255, 0.4);
        z-index: 999998;
        transition: transform 0.2s, box-shadow 0.2s;
        animation: triggerHeartbeat 2.4s infinite ease-in-out;
    }

    #portal-floating-trigger:hover {
        animation-play-state: paused;
        transform: scale(1.08);
        box-shadow: 0 10px 28px rgba(188, 108, 255, 0.6);
    }

    #portal-floating-trigger svg {
        width: 24px;
        height: 24px;
    }

    @keyframes triggerHeartbeat {
        0% { transform: scale(1); box-shadow: 0 8px 24px rgba(188, 108, 255, 0.4); }
        14% { transform: scale(1.06); box-shadow: 0 10px 28px rgba(188, 108, 255, 0.5); }
        28% { transform: scale(1); box-shadow: 0 8px 24px rgba(188, 108, 255, 0.4); }
        42% { transform: scale(1.06); box-shadow: 0 10px 28px rgba(188, 108, 255, 0.5); }
        70% { transform: scale(1); box-shadow: 0 8px 24px rgba(188, 108, 255, 0.4); }
    }

    /* Modal Backdrop Configuration */
    #portal-modal-overlay {
        position: fixed;
        top: 0;
        left: 0;
        width: 100vw;
        height: 100vh;
        background: rgba(4, 7, 12, 0.85);
        backdrop-filter: blur(10px);
        -webkit-backdrop-filter: blur(10px);
        z-index: 999999;
        display: none;
        justify-content: center;
        align-items: center;
        padding: 20px;
    }

    /* Glassmorphic Panel Core Card with Scale Animation */
    #portal-console-card {
        background: rgba(22, 27, 34, 0.65);
        backdrop-filter: blur(20px);
        -webkit-backdrop-filter: blur(20px);
        border: 1px solid rgba(88, 166, 255, 0.2);
        border-radius: 16px;
        width: 100%;
        max-width: 760px;
        height: 85vh;
        max-height: 800px;
        display: flex;
        flex-direction: column;
        padding: 24px;
        box-shadow: 0 30px 70px rgba(0, 0, 0, 0.8);
        transform: scale(0.92);
        opacity: 0;
        transition: transform 0.3s cubic-bezier(0.34, 1.56, 0.64, 1), opacity 0.3s ease;
    }

    #portal-modal-overlay.portal-active #portal-console-card {
        transform: scale(1);
        opacity: 1;
    }

    /* Attention Mechanics: Shake Keyframes */
    @keyframes panelShake {
        0%, 100% { transform: translateX(0); }
        20%, 60% { transform: translateX(-6px); }
        40%, 80% { transform: translateX(6px); }
    }

    #portal-console-card.shake-attention {
        animation: panelShake 0.4s ease-in-out;
    }

    /* Header Design Styles */
    .console-title-row {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 8px;
    }

    .console-brand-meta {
        display: flex;
        align-items: center;
        gap: 10px;
    }

    .brand-glow-dot {
        width: 10px;
        height: 10px;
        background: #3fb950;
        border-radius: 50%;
        box-shadow: 0 0 10px #3fb950;
    }

    .console-brand-meta h6 {
        font-size: 16px;
        color: #ffffff;
        font-weight: 600;
        margin: 0;
    }

    .console-close-btn {
        background: transparent;
        border: none;
        color: #8b949e;
        font-size: 18px;
        cursor: pointer;
        transition: color 0.2s;
    }

    .console-close-btn:hover {
        color: #ff7b72;
    }

    .console-instructions {
        font-size: 13px;
        color: #8b949e;
        line-height: 1.5;
        margin-bottom: 20px;
    }

    /* Tab Layout Rail */
    .console-tab-rail {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        gap: 8px;
        margin-bottom: 16px;
    }

    .console-tab {
        background: rgba(33, 38, 45, 0.5);
        color: #c9d1d9;
        border: 1px solid rgba(240, 246, 252, 0.1);
        padding: 10px;
        border-radius: 8px;
        font-size: 12.5px;
        font-weight: 600;
        cursor: pointer;
        transition: all 0.2s ease;
    }

    .console-tab:hover, .console-tab.active {
        background: #21262d;
        border-color: #58a6ff;
        color: #ffffff;
    }

    /* Content Containment Frame */
    .console-frame-container {
        flex-grow: 1;
        position: relative;
        background: #0d1117;
        border: 1px solid rgba(240, 246, 252, 0.08);
        border-radius: 10px;
        overflow: hidden;
    }

    .frame-loading-overlay {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: #0d1117;
        color: #8b949e;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 13px;
        font-family: monospace;
        z-index: 2;
    }

    #portalIntakeFrame {
        width: 100%;
        height: 100%;
        border: none;
        position: absolute;
        top: 0;
        left: 0;
        z-index: 1;
    }
</style>

<script>
    // Clean View Route URLs Array
    const formEndpoints = [
        "https://docs.google.com/forms/d/e/1FAIpQLSdx2yQU28hg4L4Rm8rSdvjR4FZPpbys7XKEZDFul5yubv3Olg/viewform?usp=header",
        "https://docs.google.com/forms/d/e/1FAIpQLSdipVP7tU1hjTjECfWUdnhzWN-PROdQp19ng25EUDJk5-8JzA/viewform?usp=header",
        "https://docs.google.com/forms/d/e/1FAIpQLSfBDlR6TcU9sWjbeVOp6dtb4GMKdL6SP_i0KB08IrtbLT9wwA/viewform?usp=header"
    ];

    let initializedChannel = 0;

    function openFormPortal() {
        const overlay = document.getElementById('portal-modal-overlay');
        document.body.style.overflow = 'hidden'; // Lock base screen navigation
        overlay.style.display = 'flex';
        
        // Force rendering paint cycle before adding animation classes
        setTimeout(() => {
            overlay.classList.add('portal-active');
            loadActiveChannel();
        }, 20);
    }

    function closeFormPortal() {
        const overlay = document.getElementById('portal-modal-overlay');
        overlay.classList.remove('portal-active');
        
        setTimeout(() => {
            overlay.style.display = 'none';
            document.body.style.overflow = ''; // Release parent track focus
            document.getElementById('portalIntakeFrame').src = "";
        }, 300);
    }

    function loadActiveChannel() {
        document.getElementById('frameLoader').style.display = 'flex';
        document.getElementById('portalIntakeFrame').src = formEndpoints[initializedChannel];
    }

    function switchFormChannel(tabElement, channelIndex) {
        if(channelIndex === initializedChannel) return;
        
        document.querySelectorAll('.console-tab').forEach(tab => tab.classList.remove('active'));
        tabElement.classList.add('active');
        
        initializedChannel = channelIndex;
        loadActiveChannel();
    }

    function hideFrameLoader() {
        document.getElementById('frameLoader').style.display = 'none';
    }

    // Attention Safeguard Trigger Mechanics
    function triggerBlockShake() {
        const panel = document.getElementById('portal-console-card');
        panel.classList.remove('shake-attention');
        
        // Forces DOM reflow engine validation to reset runtime keyframes
        void panel.offsetWidth; 
        
        panel.classList.add('shake-attention');
    }
</script>


<h2>Privacy Policy for Digital Dynamo</h2>

<p>At Digital Dynamo, we respect your privacy and are committed to protecting any personal information you share with us.</p>

<h3>Information We Collect:</h3>
<ul>
  <li>Basic contact details (name, email address) through sign-up forms</li>
  <li>Voluntary information shared in community discussions or polls</li>
  <li>Non-personal browsing data (via Blogger and Google Analytics)</li>
</ul>

<h3>How We Use Your Information:</h3>
<ul>
  <li>To improve community engagement and services</li>
  <li>To share updates, blog content, and exclusive resources</li>
  <li>To communicate with members regarding community events or feedback</li>
</ul>

<h3>Third-Party Services:</h3>
<p>We use trusted third-party platforms like Blogger, Google Analytics, and affiliate programs. These platforms may collect their own usage data according to their privacy policies.</p>

<h3>Your Privacy Rights:</h3>
<p>You may request to review, update, or delete your personal information by contacting us at:</p>
<p>Email: <a href="debeatz4@gmail.com">debeatz4@gmail.com</a></p>

<h3>Updates to This Policy:</h3>
<p>This privacy policy may be updated periodically. The latest version will always be available on this page.</p>

<p>Last updated: July 2025</p>


<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Creators Hub– AI Tools, Side Hustles & Digital Growth</title>

<!-- Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@500;600;700&family=Inter:wght@400;500;600&display=swap" rel="stylesheet">

<!-- Tailwind -->
<script src="https://cdn.tailwindcss.com"></script>

<script>
tailwind.config = {
  theme: {
    extend: {
      colors: {
        primary: '#0F2A44',
        secondary: '#1E88E5',
        accent: '#00C2A8',
        highlight: '#6C63FF',
        bg: '#F8FAFC'
      },
      fontFamily: {
        heading: ['Poppins','sans-serif'],
        body: ['Inter','sans-serif']
      }
    }
  }
}
</script>

<style>
@keyframes pulseSoft {
  0%,100% { transform: scale(1); }
  50% { transform: scale(1.08); }
}
.floating-btn { animation: pulseSoft 1.8s infinite; }
</style>
</head>

<body class="bg-bg font-body text-gray-800">

<!-- NAVBAR -->
<header class="sticky top-0 z-40 bg-white shadow-sm">
  <div class="max-w-7xl mx-auto px-4 py-4 flex justify-between items-center">
    <button onclick="openFrame('https://debeatzgh1.blogspot.com/')" class="text-2xl font-heading font-bold text-primary">
      Debeatzgh
    </button>
    <nav class="hidden md:flex gap-8 font-medium">
      <button onclick="openFrame('https://debeatzgh1.blogspot.com/')" class="hover:text-secondary">Home</button>
      <button onclick="openFrame('https://mybrandsonline.blogspot.com/')" class="hover:text-secondary">Products</button>
      <button onclick="openFrame('https://digimartgh.blogspot.com/')" class="hover:text-secondary">Side Hustle</button>
      <button onclick="openFrame('https://github.com/debeatzgh1/debeatzgh/discussions/4')" class="hover:text-secondary">Milkshake</button>
    </nav>
    <button onclick="openFrame('https://github.com/debeatzgh1/debeatzgh/discussions/4')" class="bg-secondary text-white px-5 py-2 rounded-xl shadow hover:scale-105 transition">
      comment
    </button>
  </div>
</header>

<!-- HERO -->
<section class="max-w-7xl mx-auto px-4 py-20 grid md:grid-cols-2 gap-12 items-center">
  <div>
    <h2 class="text-4xl md:text-5xl font-heading font-bold text-primary">
      Build Income with <span class="text-secondary">AI Tools</span> & Smart Side Hustles
    </h2>
    <p class="mt-6 text-lg text-gray-600">
      AI tools, blogging guides, and digital products — all curated to help you earn online.
    </p>
    <div class="mt-8 flex gap-4">
      <button onclick="openFrame('https://mybrandsonline.blogspot.com/')" class="bg-secondary text-white px-6 py-3 rounded-xl shadow hover:scale-105 transition">
        View Products
      </button>
      <button onclick="openFrame('https://digimartgh.blogspot.com/')" class="border border-secondary text-secondary px-6 py-3 rounded-xl hover:bg-secondary hover:text-white transition">
        Side Hustle Guide
      </button>
    </div>
  </div>

  <div class="bg-white rounded-xl shadow-lg p-6">
    <img src="https://images.unsplash.com/photo-1674027444485-cec3da58eef4" class="rounded-xl">
  </div>
</section>

<!-- FEATURES -->
<section class="bg-white py-16">
  <div class="max-w-7xl mx-auto px-4">
    <h3 class="text-3xl font-heading font-semibold text-center text-primary">
      What You’ll Find
    </h3>

    <div class="grid md:grid-cols-3 gap-8 mt-12">
      <button onclick="openFrame('https://debeatzgh.wordpress.com/')" class="p-6 rounded-xl shadow hover:shadow-lg transition text-left">
        <span class="bg-accent text-white px-3 py-1 rounded-full text-sm">HUB</span>
        <h4 class="mt-4 font-heading text-xl font-semibold">Central Link Hub</h4>
        <p class="mt-2 text-gray-600">Access all Debeatzgh tools, products & platforms.</p>
      </button>

      <button onclick="openFrame('https://beatzde4.blogspot.com/')" class="p-6 rounded-xl shadow hover:shadow-lg transition text-left">
        <span class="bg-highlight text-white px-3 py-1 rounded-full text-sm">TOOLS</span>
        <h4 class="mt-4 font-heading text-xl font-semibold">Digital Tools</h4>
        <p class="mt-2 text-gray-600">AI prompts, resources & affiliate tools.</p>
      </button>

      <button onclick="openFrame('https://debeatzgh1.github.io/debeatzgh/')" class="p-6 rounded-xl shadow hover:shadow-lg transition text-left">
        <span class="bg-secondary text-white px-3 py-1 rounded-full text-sm">GUIDE</span>
        <h4 class="mt-4 font-heading text-xl font-semibold">Side Hustle Playbook</h4>
        <p class="mt-2 text-gray-600">Proven ways to start earning online.</p>
      </button>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer class="bg-primary text-gray-300 py-10 text-center">
  <h4 class="font-heading text-xl text-white">Debeatzgh</h4>
  <p class="mt-2 text-sm">AI • Blogging • Side Hustles • Digital Growth</p>
  <p class="mt-4 text-xs opacity-70">© 2025 Debeatzgh</p>
</footer>

<!-- FLOATING BUTTON -->
<button onclick="openFrame('https://msha.ke/debeatzgh')" class="fixed bottom-6 right-6 bg-accent text-white w-14 h-14 rounded-full shadow-lg floating-btn text-2xl">
  ☰
</button>

<!-- IFRAME OVERLAY -->
<div id="iframeOverlay" class="fixed inset-0 bg-black/70 hidden z-50">
  <div class="absolute inset-4 bg-white rounded-xl overflow-hidden flex flex-col">
    
    <!-- CONTROLS -->
    <div class="flex items-center justify-between bg-primary text-white px-4 py-2">
      <div class="flex gap-4 text-lg">
        <button onclick="frameBack()">⟵</button>
        <button onclick="frameForward()">⟶</button>
      </div>
      <div class="flex gap-4 text-lg">
        <button onclick="toggleFullscreen()">⛶</button>
        <button onclick="closeFrame()">✕</button>
      </div>
    </div>

    <!-- IFRAME -->
    <iframe id="contentFrame" class="flex-1 w-full border-none"></iframe>
  </div>
</div>

<script>
const frame = document.getElementById('contentFrame');
const overlay = document.getElementById('iframeOverlay');

function openFrame(url){
  frame.src = url;
  overlay.classList.remove('hidden');
}

function closeFrame(){
  frame.src = '';
  overlay.classList.add('hidden');
}

function frameBack(){
  frame.contentWindow.history.back();
}

function frameForward(){
  frame.contentWindow.history.forward();
}

function toggleFullscreen(){
  const box = overlay.querySelector('div');
  if(!document.fullscreenElement){
    box.requestFullscreen();
  } else {
    document.exitFullscreen();
  }
}
</script>

</body>
</html>
