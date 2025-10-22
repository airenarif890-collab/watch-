<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>Earning Technology - Admin</title>
    
    <!-- MONETAG SCRIPTS (MUST BE HOSTED ON YOUR OWN SERVER TO WORK) -->
    <script src='//libtl.com/sdk.js' data-zone='10060125' data-sdk='show_10060125'></script>
    <script type='text/javascript' src='//otieu.com/4/10061162.js'></script>

    <script src="https://telegram.org/js/telegram-web-app.js"></script>
    <script src="https://cdn.tailwindcss.com"></script>
    
    <style>
        /* --- Base CSS Setup & Theme Adaptation --- */
        :root {
            --tg-bg: var(--tg-theme-bg-color, #121212);
            --tg-text: var(--tg-theme-text-color, #e0e0e0);
            --tg-button: var(--tg-theme-button-color, #007bff);
            --tg-button-text: var(--tg-theme-button-text-color, #ffffff);
            --tg-hint: var(--tg-theme-hint-color, #8a8a8a);
            --success-color: #28a745;
            --secondary-bg-color: #1e1e1e;
            --border-color: #333333;
            --admin-color: #ffc107;
        }
        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            background-color: var(--tg-bg);
            color: var(--tg-text);
            padding: 20px 15px 90px 15px;
            display: flex;
            flex-direction: column;
            align-items: center;
            min-height: 100vh;
            box-sizing: border-box;
        }
        .container { width: 100%; max-width: 500px; }
        .view { display: none; width: 100%; }
        #home-view { display: block; }
        .card { background-color: var(--secondary-bg-color); border: 1px solid var(--border-color); }
        .btn { background-color: var(--tg-button); color: var(--tg-button-text); transition: all 0.2s ease; }
        .btn-admin { background-color: var(--admin-color); color: #000; }
        .btn:hover:not(:disabled) { filter: brightness(1.1); transform: translateY(-1px); }
        .btn:disabled { background: #555 !important; color: #888 !important; cursor: not-allowed !important; box-shadow: none !important; transform: none !important; }
        .footer-nav {
            position: fixed; bottom: 0; left: 0; right: 0; background-color: var(--secondary-bg-color);
            box-shadow: 0 -4px 12px rgba(0,0,0,0.3); border-top: 1px solid var(--border-color);
        }
        .nav-btn.active { color: var(--tg-button); }
        .nav-admin.active { color: var(--admin-color); }
        .spinner {
            border: 4px solid rgba(255, 255, 255, 0.3); border-top: 4px solid var(--tg-button); border-radius: 50%;
            width: 24px; height: 24px; animation: spin 1s linear infinite;
        }
        @keyframes spin { 0% { transform: rotate(0deg); } 100% { transform: rotate(360deg); } }
        /* Style for individual withdrawal request in admin view */
        .withdrawal-item { border-bottom: 1px dashed var(--border-color); padding-bottom: 10px; margin-bottom: 10px; }
        .withdrawal-item:last-child { border-bottom: none; margin-bottom: 0; padding-bottom: 0; }
    </style>
</head>
<body>
    
    <!-- Firebase SDK Imports (Module setup) -->
    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInAnonymously, signInWithCustomToken, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { getFirestore, doc, onSnapshot, setDoc, collection, runTransaction, deleteDoc, query, orderBy } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";
        import { setLogLevel } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";
        
        // Global variables for Firebase services
        window.firebaseApp = null; window.db = null; window.auth = null; window.userId = null; window.USER_DOC_REF = null;

        const appId = typeof __app_id !== 'undefined' ? __app_id : 'default-app-id';
        const firebaseConfig = typeof __firebase_config !== 'undefined' ? JSON.parse(__firebase_config) : {};
        const initialAuthToken = typeof __initial_auth_token !== 'undefined' ? __initial_auth_token : null;
        
        try {
            if (Object.keys(firebaseConfig).length > 0) {
                window.firebaseApp = initializeApp(firebaseConfig);
                window.db = getFirestore(window.firebaseApp);
                window.auth = getAuth(window.firebaseApp);
                setLogLevel('error'); // Set log level to reduce noise
                
                const signInPromise = initialAuthToken ? signInWithCustomToken(window.auth, initialAuthToken) : signInAnonymously(window.auth);
                signInPromise.catch(error => { console.error("Firebase Auth Error:", error); });
                
                onAuthStateChanged(window.auth, (user) => {
                    if (user) {
                        window.userId = user.uid;
                        window.USER_DOC_REF = doc(window.db, 'artifacts', appId, 'users', window.userId, 'earnings', 'user_data');
                        if (typeof window.initializeAppLogic === 'function') {
                            // Call main application logic after successful authentication
                            window.initializeAppLogic();
                        }
                    } else {
                        console.log("User not signed in.");
                    }
                });
            } else {
                console.error("Firebase config is missing. Cannot initialize Firestore.");
            }
        } catch (e) {
            console.error("Critical Firebase Initialization Failure:", e);
        }

        // Expose necessary Firestore functions globally for use in the main script block
        window.firebaseExports = { doc, onSnapshot, setDoc, collection, runTransaction, deleteDoc, query };
    </script>

    <div class="container">
        <!-- Home View -->
        <div id="home-view" class="view">
            <div class="header text-center mb-6">
                <h1 class="text-3xl font-bold">Earning Technology</h1>
                <p class="text-sm" style="color:var(--tg-hint);">Watch Ads and Earn BDT</p>
                <div id="loading-indicator" class="mt-4 hidden justify-center items-center">
                    <div class="spinner"></div>
                    <p class="ml-3 text-sm font-semibold text-white">Loading User Data...</p>
                </div>
            </div>
            
            <div class="card p-6 rounded-2xl mb-6 shadow-lg">
                <h2 class="text-xs tracking-wider uppercase font-medium" style="color:var(--tg-hint);">Current Balance</h2>
                <div class="balance-amount text-5xl font-extrabold mt-2 mb-3" id="balanceDisplay">BDT 0.00</div>
                <div class="ad-info-grid grid grid-cols-2 gap-4 text-center">
                    <div class="ad-info-item p-3 rounded-lg bg-gray-700/50">
                        <h3 class="text-2xl font-bold text-white" id="adCountDisplay">0</h3>
                        <p class="text-xs" style="color:var(--tg-hint);">Total Ads Watched</p>
                    </div>
                    <div class="ad-info-item p-3 rounded-lg bg-gray-700/50">
                        <h3 class="text-2xl font-bold text-white" id="dailyAdCountDisplay">0 / 1000</h3>
                        <p class="text-xs" style="color:var(--tg-hint);">Today's Ads</p>
                    </div>
                </div>
            </div>
            
            <!-- AD WARNING ELEMENT -->
            <div id="ad-warning" class="hidden p-3 mb-4 text-sm rounded-lg border border-yellow-500 bg-yellow-500/10 text-yellow-300">
                <!-- Warning will be inserted here by JS -->
            </div>

            <div class="ad-buttons flex flex-col gap-4 mb-6">
                <button class="btn py-4 text-lg font-semibold rounded-xl" id="rewardedBtn" disabled>
                    Watch Ad (+0.20 BDT)
                </button>
            </div>
            <button class="btn py-4 text-lg font-semibold rounded-xl" id="mainWithdrawBtn" disabled>
                Reach 240.00 BDT to Withdraw
            </button>
        </div>

        <!-- Withdraw View (Same as previous) -->
        <div id="withdraw-view" class="view">
            <div class="header text-center mb-6">
                <h1 class="text-3xl font-bold">Withdraw Earnings</h1>
                <p class="text-sm" style="color:var(--tg-hint);">Securely request your funds.</p>
            </div>
            <div class="card p-6 rounded-2xl mb-6 shadow-lg">
                <h2 class="text-xs tracking-wider uppercase font-medium" style="color:var(--tg-hint);">Current Balance</h2>
                <div class="balance-amount text-4xl font-extrabold mt-1 mb-3" id="withdrawBalanceDisplay">BDT 0.00</div>
                <p class="text-xs" style="color: var(--tg-hint);">Minimum withdrawal is **240.00 BDT** (2.00 USDT).</p>
            </div>
            
            <div class="card p-6 rounded-2xl mb-6 shadow-lg">
                <h2 class="text-md font-semibold mb-4 text-left">Choose Payment Method</h2>
                <div class="payment-method-select flex justify-between gap-3 mb-6">
                    <input type="radio" id="method-bkash" name="paymentMethod" value="Bkash" class="hidden">
                    <label for="method-bkash" class="flex-1 text-center">🔴 Bkash</label>
                    
                    <input type="radio" id="method-nagad" name="paymentMethod" value="Nagad" class="hidden">
                    <label for="method-nagad" class="flex-1 text-center">🟠 Nagad</label>
                    
                    <input type="radio" id="method-usdt" name="paymentMethod" value="USDT" checked class="hidden">
                    <label for="method-usdt" class="flex-1 text-center">🪙 USDT</label>
                </div>

                <h2 class="text-md font-semibold mb-2 text-left">Payment Details</h2>
                <div class="input-group mb-4">
                    <label for="paymentAddress" id="addressLabel" class="block text-left text-sm mb-1" style="color:var(--tg-hint);">Your USDT Wallet Address (TRC20)</label>
                    <input type="text" id="paymentAddress" placeholder="Enter your address/phone number" class="w-full p-3 rounded-lg focus:ring-2 focus:ring-blue-500 outline-none">
                </div>
                
                <button class="btn py-3 text-lg font-semibold rounded-xl" id="finalWithdrawBtn" disabled>Withdraw</button>
            </div>
        </div>
        
        <!-- Referral View (Same as previous) -->
        <div id="referral-view" class="view">
            <div class="header text-center mb-6">
                <h1 class="text-3xl font-bold">Referrals</h1>
                <p class="text-sm" style="color:var(--tg-hint);">Invite friends and earn more!</p>
            </div>
            <div class="card p-6 rounded-2xl mb-6 shadow-lg">
                <h2 class="text-xs tracking-wider uppercase font-medium mb-3" style="color:var(--tg-hint);">Your Referral Stats</h2>
                <div class="ad-info-grid grid grid-cols-2 gap-4 text-center">
                    <div class="ad-info-item p-3 rounded-lg bg-gray-700/50">
                        <h3 class="text-2xl font-bold text-white" id="referralCountDisplay">0</h3>
                        <p class="text-xs" style="color:var(--tg-hint);">Total Referrals</p>
                    </div>
                    <div class="ad-info-item p-3 rounded-lg bg-gray-700/50">
                        <h3 class="text-2xl font-bold text-white" id="referralBonusDisplay">USDT 0.00</h3>
                        <p class="text-xs" style="color:var(--tg-hint);">Referral Earnings (Calculated)</p>
                    </div>
                </div>
            </div>
            <div class="card p-6 rounded-2xl mb-6 shadow-lg">
                <h2 class="text-lg font-semibold mb-2 text-left">Your Referral Link</h2>
                <p class="text-sm mb-3" style="color:var(--tg-hint);">Share this link. You get **0.5 USDT** for each verified friend who joins!</p>
                <div id="referralLink" title="Click to copy" class="p-3 text-sm text-center bg-gray-800 rounded-lg cursor-pointer border-2 border-dashed border-gray-600 truncate hover:bg-gray-700/70 transition" style="color:var(--tg-text);">
                    Referral link is loading...
                </div>
                <p class="text-xs mt-3 text-left" style="color:var(--tg-hint);">
                    Note: Referral rewards require successful signup and backend processing.
                </p>
            </div>
        </div>

        <!-- NEW ADMIN VIEW -->
        <div id="admin-view" class="view">
            <div class="header text-center mb-6">
                <h1 class="text-3xl font-bold text-red-400">ADMIN CONTROL</h1>
                <p class="text-sm" style="color:var(--tg-hint);">Manage Withdrawal Requests</p>
                <p class="text-xs mt-1" style="color:var(--tg-hint);">Logged in as User ID: <span id="adminIdDisplay" class="font-mono text-xs"></span></p>
            </div>
            <div class="card p-4 rounded-xl mb-4 shadow-lg">
                <h2 class="text-lg font-semibold mb-3 border-b pb-2 border-gray-700">Pending Withdrawals (<span id="pendingCount">0</span>)</h2>
                <div id="withdrawalRequests" class="flex flex-col gap-3">
                    <p id="noRequests" class="text-sm text-center py-4" style="color:var(--tg-hint);">No pending withdrawal requests.</p>
                </div>
            </div>
        </div>
        <!-- END NEW ADMIN VIEW -->


        <div class="status-message fixed bottom-20 left-1/2 -translate-x-1/2 w-11/12 max-w-sm p-3 rounded-lg font-medium text-center z-50 transition-opacity duration-300" id="statusMessage" style="display:none; opacity:0;"></div>
        
    </div>

    <!-- Footer Navigation -->
    <footer class="footer-nav flex justify-around p-2">
        <button class="nav-btn active flex flex-col items-center" id="navHome">
            <span class="icon mb-1"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="currentColor" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-home"><path d="m3 9 9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"/><polyline points="9 22 9 12 15 12 15 22"/></svg></span>
            <span class="text-xs">Home</span>
        </button>
        <button class="nav-btn flex flex-col items-center" id="navWithdraw">
            <span class="icon mb-1"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="currentColor" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-wallet"><path d="M21 12V7H5a2 2 0 0 1 0-4h14v16a2 2 0 0 1-2 2h-4"/><path d="M4 19v-5a2 2 0 0 1 2-2h12"/></svg></span>
            <span class="text-xs">Withdraw</span>
        </button>
        <button class="nav-btn flex flex-col items-center" id="navRefer">
            <span class="icon mb-1"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="currentColor" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-users"><path d="M16 21v-2a4 4 0 0 0-4-4H6a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M22 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/></svg></span>
            <span class="text-xs">Referrals</span>
        </button>
        <button class="nav-btn flex flex-col items-center hidden" id="navAdmin">
            <span class="icon mb-1"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="currentColor" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-wrench"><path d="M.2 13a2.41 2.41 0 0 0 0 3.84L5.6 22l4.8-4.8c1.64-1.64 1.4-4.38-.8-5.54z"/><path d="m11.13 5.86 5.51 5.51-2.94 2.94"/><circle cx="15.5" cy="4.5" r="2.5"/><path d="M18.5 12.5 12 19"/></svg></span>
            <span class="text-xs">Admin</span>
        </button>
        <button class="nav-btn flex flex-col items-center" id="navJoin">
            <span class="icon mb-1"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="currentColor" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-youtube"><path d="M2.8 14.5c0-.8.5-1.5 1.4-1.5h14.4c.8 0 1.3.7 1.3 1.5v4c0 .8-.5 1.5-1.4 1.5H4.2c-.8 0-1.4-.7-1.4-1.5z"/><path d="M22 8.5c0-.8-.5-1.5-1.4-1.5H4.2c-.8 0-1.4.7-1.4 1.5v4c0 .8.5 1.5 1.4 1.5h14.4c.8 0 1.3-.7 1.3-1.5z"/></svg></span>
            <span class="text-xs">Join Channel</span>
        </button>
    </footer>

    <script>
        document.addEventListener('DOMContentLoaded', function () {
            
            if (typeof window.firebaseExports === 'undefined') {
                console.error("Firebase exports are not available.");
            }
            
            const tg = window.Telegram.WebApp;
            const { runTransaction, onSnapshot, doc, collection, deleteDoc, query } = window.firebaseExports || {};

            // --- App Constants & Configuration (Updated for 0.20 BDT per ad) ---
            const ADMIN_ID = '8316125795'; // আপনার ইউজার আইডি এখানে বসান
            const BOT_USERNAME = 'fast4t_bot'; 
            const YOUTUBE_CHANNEL_LINK = 'https://youtube.com/@mdariftips4889?si=EsydbelhkDUyAew5';
            
            const USDT_TO_BDT_RATE = 120; 
            const SU_PER_USDT = 12000;    // Updated to 12000 to allow exact 0.20 BDT calculation
            const AD_REWARD_SU = 20;        // 20 SU = (20/12000) * 120 = 0.20 BDT (20 Paisa)
            const WITHDRAW_THRESHOLD_SU = 24000; // Equivalent to 2.00 USDT (240 BDT)
            const DAILY_AD_LIMIT = 1000;

            // --- DOM Elements ---
            const rewardedBtn = document.getElementById('rewardedBtn');
            const statusMessage = document.getElementById('statusMessage');
            const adWarning = document.getElementById('ad-warning');
            const mainWithdrawBtn = document.getElementById('mainWithdrawBtn');
            const navHome = document.getElementById('navHome');
            const navWithdraw = document.getElementById('navWithdraw');
            const navRefer = document.getElementById('navRefer');
            const navAdmin = document.getElementById('navAdmin'); // NEW
            const navJoin = document.getElementById('navJoin');
            const addressLabel = document.getElementById('addressLabel');
            const paymentAddress = document.getElementById('paymentAddress');
            const finalWithdrawBtn = document.getElementById('finalWithdrawBtn');
            const referralLinkElement = document.getElementById('referralLink');
            const loadingIndicator = document.getElementById('loading-indicator');
            const withdrawalRequestsContainer = document.getElementById('withdrawalRequests'); // NEW
            const pendingCountDisplay = document.getElementById('pendingCount'); // NEW

            let appState = {
                balanceInSmallestUnit: 0,
                totalAdCount: 0,
                dailyAdCount: 0,
                lastAdDate: null,
                referralCount: 0,
                selectedMethod: 'USDT',
                isAdmin: false // NEW
            };

            // ---- Helper Functions ----
            function getTodayDateString() { return new Date().toISOString().split('T')[0]; }
            function showStatus(message, type, duration = 4000) { 
                let bgColor, borderColor, textColor;
                switch(type) {
                    case 'success':
                        bgColor = 'rgba(40, 167, 69, 0.25)'; borderColor = 'var(--success-color)'; textColor = 'var(--success-color)'; break;
                    case 'error':
                        bgColor = 'rgba(220, 53, 69, 0.25)'; borderColor = '#dc3545'; textColor = '#dc3545'; break;
                    case 'info':
                    default:
                        bgColor = 'rgba(0, 123, 255, 0.25)'; borderColor = 'var(--tg-button)'; textColor = 'var(--tg-button)'; break;
                }
                statusMessage.textContent = message;
                statusMessage.style.cssText = `display:block; opacity:1; background-color:${bgColor}; border-left: 5px solid ${borderColor}; color: ${textColor};`;
                clearTimeout(window.statusTimeout);
                window.statusTimeout = setTimeout(() => { statusMessage.style.opacity = '0'; }, duration);
            }
            
            function showView(viewId) { 
                document.querySelectorAll('.view').forEach(v => v.style.display = 'none');
                document.getElementById(viewId).style.display = 'block';
                
                document.querySelectorAll('.nav-btn').forEach(b => {
                    b.classList.remove('active', 'nav-admin');
                    if (b.id === 'navAdmin') b.classList.remove('nav-admin');
                    b.style.color = 'var(--tg-text)';
                });

                const navButtonId = 'nav' + viewId.replace('-view', '').charAt(0).toUpperCase() + viewId.replace('-view', '').slice(1);
                const navButton = document.getElementById(navButtonId);
                if(navButton) {
                    navButton.classList.add('active');
                    if(viewId === 'admin-view') {
                         navButton.style.color = 'var(--admin-color)';
                    } else {
                         navButton.style.color = 'var(--tg-button)';
                    }
                }
            }

            function updateUI(state) { 
                const balanceInUSDT = (state.balanceInSmallestUnit / SU_PER_USDT).toFixed(2);
                const balanceInBDT = (parseFloat(balanceInUSDT) * USDT_TO_BDT_RATE).toFixed(2);
                const thresholdInBDT = (WITHDRAW_THRESHOLD_SU / SU_PER_USDT * USDT_TO_BDT_RATE).toFixed(2);
                
                document.getElementById('balanceDisplay').textContent = `BDT ${balanceInBDT}`;
                document.getElementById('withdrawBalanceDisplay').textContent = `BDT ${balanceInBDT}`;
                document.getElementById('adCountDisplay').textContent = state.totalAdCount;
                document.getElementById('dailyAdCountDisplay').textContent = `${state.dailyAdCount} / ${DAILY_AD_LIMIT}`;
                
                document.getElementById('referralCountDisplay').textContent = state.referralCount;
                const referralBonus = (state.referralCount * 5000 / SU_PER_USDT).toFixed(2); 
                document.getElementById('referralBonusDisplay').textContent = `USDT ${referralBonus}`;

                const isWithdrawalPossible = state.balanceInSmallestUnit >= WITHDRAW_THRESHOLD_SU;
                
                mainWithdrawBtn.disabled = !isWithdrawalPossible;
                mainWithdrawBtn.textContent = isWithdrawalPossible ? 'Go to Withdraw' : `Reach ${thresholdInBDT} BDT to Withdraw`;

                const adLimitReached = state.dailyAdCount >= DAILY_AD_LIMIT;
                rewardedBtn.disabled = adLimitReached;
                // Updated button text to reflect exactly 0.20 BDT
                rewardedBtn.textContent = adLimitReached ? 'Daily Limit Reached' : 'Watch Ad (+0.20 BDT)';
                
                updateWithdrawalInput(appState.selectedMethod, state.balanceInSmallestUnit);
            }

            function displayAdNotLoadingWarning() {
                const warningText = "বিজ্ঞাপন লোড হচ্ছে না: এই প্রিভিউ পরিবেশের (Canvas) নিরাপত্তা বিধিনিষেধের কারণে Monetag অ্যাডগুলি ব্লক করা হচ্ছে। তবে, আপনার নিজস্ব হোস্টিং সার্ভারে এটি সঠিকভাবে কাজ করবে। আপনি এখনও আর্ন বাটনে ক্লিক করে ব্যালেন্স বাড়াতে পারেন (সিমুলেশন চলছে)।";
                
                adWarning.innerHTML = `⚠️ <strong>গুরুত্বপূর্ণ:</strong> ${warningText}`;
                adWarning.classList.remove('hidden');
            }

            function updateWithdrawalInput(method, currentBalanceSU) {
                appState.selectedMethod = method;
                const isWithdrawalPossible = currentBalanceSU >= WITHDRAW_THRESHOLD_SU;
                const thresholdInBDT = (WITHDRAW_THRESHOLD_SU / SU_PER_USDT * USDT_TO_BDT_RATE).toFixed(2);
                
                finalWithdrawBtn.disabled = !isWithdrawalPossible || !paymentAddress.value.trim();
                finalWithdrawBtn.textContent = isWithdrawalPossible ? 'Withdraw' : `Minimum ${thresholdInBDT} BDT Required`;

                switch (method) {
                    case 'Bkash':
                        addressLabel.textContent = 'আপনার Bkash ফোন নম্বর (পার্সোনাল)';
                        paymentAddress.placeholder = '01xxxxxxxxx';
                        break;
                    case 'Nagad':
                        addressLabel.textContent = 'আপনার Nagad ফোন নম্বর (পার্সোনাল)';
                        paymentAddress.placeholder = '01xxxxxxxxx';
                        break;
                    case 'USDT':
                    default:
                        addressLabel.textContent = 'আপনার USDT Wallet Address (TRC20)';
                        paymentAddress.placeholder = 'Enter TRC20 Address';
                        break;
                }
            }

            // ---- Firestore & Ad Logic ----
            
            async function handleAdSuccessTransaction() {
                if (!window.USER_DOC_REF || !runTransaction) {
                    showStatus("Error: User data path or transaction module not ready.", 'error');
                    rewardedBtn.disabled = false;
                    return;
                }

                const db = window.db; 
                try {
                    await runTransaction(db, async (transaction) => {
                        const userDoc = await transaction.get(window.USER_DOC_REF);
                        
                        let currentData = userDoc.exists() ? userDoc.data() : { balanceInSmallestUnit: 0, totalAdCount: 0, dailyAdCount: 0, lastAdDate: getTodayDateString(), referralCount: 0 };
                        
                        const today = getTodayDateString();
                        let newDailyCount = (currentData.lastAdDate !== today) ? 0 : currentData.dailyAdCount;

                        if (newDailyCount >= DAILY_AD_LIMIT) {
                            throw new Error("Daily limit reached.");
                        }

                        const updatedData = {
                            balanceInSmallestUnit: currentData.balanceInSmallestUnit + AD_REWARD_SU,
                            totalAdCount: currentData.totalAdCount + 1,
                            dailyAdCount: newDailyCount + 1,
                            lastAdDate: today,
                        };

                        transaction.set(window.USER_DOC_REF, updatedData, { merge: true });
                    });
                    // Updated success message to reflect exactly 0.20 BDT
                    showStatus(`Success! +0.20 BDT has been added.`, 'success');

                } catch (error) {
                    if (error.message.includes("Daily limit reached")) {
                        showStatus("You've reached the daily ad limit.", 'error');
                    } else {
                        console.error("Ad Transaction Failed:", error);
                        showStatus("An error occurred. Please try again.", 'error');
                    }
                }
            }

            function requestAd() {
                rewardedBtn.disabled = true;
                if (appState.dailyAdCount >= DAILY_AD_LIMIT) {
                    showStatus("You've reached the daily ad limit.", 'error');
                    rewardedBtn.disabled = false;
                    return;
                }

                showStatus('Loading ad, please wait...', 'info');
                
                if (typeof window.show_10060125 === 'function') {
                    // Actual ad function call (will likely be blocked in this environment)
                    Promise.resolve(window.show_10060125())
                        .then(() => handleAdSuccessTransaction())
                        .catch(error => {
                            console.error('Monetag Ad Error or Interruption:', error);
                            showStatus('Ad failed or was interrupted. Please try again.', 'error');
                            rewardedBtn.disabled = false;
                        });

                } else {
                    // Fallback / Simulation
                    console.warn("Monetag SDK not detected. Falling back to simulated ad timer.");
                    displayAdNotLoadingWarning(); 
                    
                    setTimeout(async () => {
                        await handleAdSuccessTransaction();
                    }, 2000); // 2 second simulation time
                }
            }
            
            async function handleWithdrawal() {
                if (!window.db || !window.userId || !runTransaction) { 
                    showStatus("Initialization error. Please reload.", 'error'); return; 
                }
                
                const address = paymentAddress.value.trim();
                const method = appState.selectedMethod;
                const minUSDT = (WITHDRAW_THRESHOLD_SU / SU_PER_USDT).toFixed(2);
                
                if (!address) { showStatus("Please enter your withdrawal address/number.", 'error'); return; }
                if (appState.balanceInSmallestUnit < WITHDRAW_THRESHOLD_SU) { 
                    showStatus(`Minimum withdrawal is ${minUSDT} USDT (240 BDT).`, 'error'); return; 
                }

                showStatus('Processing withdrawal request...', 'info');
                finalWithdrawBtn.disabled = true;

                try {
                    await runTransaction(db, async (transaction) => {
                        const userDoc = await transaction.get(window.USER_DOC_REF);
                        if (!userDoc.exists()) { throw new Error("User data not found."); }
                        
                        const currentBalance = userDoc.data().balanceInSmallestUnit;
                        if (currentBalance < WITHDRAW_THRESHOLD_SU) { throw new Error("Insufficient balance."); }

                        // Create a withdrawal request document (Public data for Admin to see)
                        const withdrawalCollectionRef = collection(window.db, 'artifacts', window.appId, 'public', 'data', 'withdrawals');
                        transaction.set(doc(withdrawalCollectionRef), {
                            userId: window.userId,
                            amountSU: WITHDRAW_THRESHOLD_SU, 
                            amountBDT: (WITHDRAW_THRESHOLD_SU / SU_PER_USDT * USDT_TO_BDT_RATE).toFixed(2),
                            method: method,
                            address: address,
                            status: 'Pending',
                            timestamp: new Date().toISOString()
                        });

                        // Deduct the minimum withdrawal amount from user's balance
                        const newBalance = currentBalance - WITHDRAW_THRESHOLD_SU;
                        transaction.update(window.USER_DOC_REF, { balanceInSmallestUnit: newBalance });
                    });
                    
                    showStatus(`Withdrawal requested for 240.00 BDT to ${method}. Status: Pending.`, 'success', 8000);
                    paymentAddress.value = '';

                } catch (error) {
                    if (error.message.includes("Insufficient balance")) {
                        showStatus("Withdrawal failed: Insufficient balance.", 'error');
                    } else {
                        console.error("Withdrawal Transaction Failed:", error);
                        showStatus("An error occurred during withdrawal. Please try again.", 'error');
                    }
                } finally {
                    finalWithdrawBtn.disabled = false;
                }
            }
            
            // --- NEW ADMIN LOGIC ---
            
            // Function to handle the admin "Pay & Clear" action
            async function handleApproval(docId) {
                if (!appState.isAdmin || !window.db || !deleteDoc) {
                    showStatus("Authentication Error. You are not the admin.", 'error');
                    return;
                }
                if (!window.confirm("Are you sure you have paid this user and want to clear the request?")) {
                    return;
                }

                showStatus('Processing payment confirmation...', 'info');
                const withdrawalDocRef = doc(window.db, 'artifacts', window.appId, 'public', 'data', 'withdrawals', docId);

                try {
                    // Simulate approval by deleting the request
                    await deleteDoc(withdrawalDocRef);
                    showStatus('Withdrawal request marked as PAID and cleared!', 'success', 5000);
                } catch (error) {
                    console.error("Failed to delete withdrawal document:", error);
                    showStatus('Error clearing request. Check console.', 'error');
                }
            }

            // Function to listen for and render pending withdrawal requests
            function setupAdminListener() {
                if (!appState.isAdmin || !window.db) return;
                
                document.getElementById('adminIdDisplay').textContent = window.userId;
                
                const withdrawalCollectionRef = collection(window.db, 'artifacts', window.appId, 'public', 'data', 'withdrawals');
                // Note: We avoid orderBy here to prevent index creation issues in the environment
                const q = query(withdrawalCollectionRef); 

                const unsubscribe = onSnapshot(q, (snapshot) => {
                    const requests = [];
                    snapshot.forEach(doc => {
                        requests.push({ id: doc.id, ...doc.data() });
                    });

                    pendingCountDisplay.textContent = requests.length;
                    withdrawalRequestsContainer.innerHTML = '';
                    
                    if (requests.length === 0) {
                        withdrawalRequestsContainer.innerHTML = '<p id="noRequests" class="text-sm text-center py-4" style="color:var(--tg-hint);">No pending withdrawal requests.</p>';
                        return;
                    }

                    requests.forEach(req => {
                        const date = new Date(req.timestamp).toLocaleDateString();
                        const time = new Date(req.timestamp).toLocaleTimeString();

                        const item = document.createElement('div');
                        item.className = 'withdrawal-item p-3 card rounded-xl shadow-md flex flex-col gap-2';
                        item.innerHTML = `
                            <p class="text-sm font-semibold text-white">💰 BDT ${req.amountBDT} (${req.method})</p>
                            <p class="text-xs" style="color:var(--tg-hint);">User ID (Click to Copy): <span class="font-mono text-xs cursor-pointer text-blue-400" onclick="copyTextToClipboard('${req.userId}')">${req.userId}</span></p>
                            <p class="text-xs break-all" style="color:var(--tg-hint);">Address: ${req.address}</p>
                            <p class="text-xs italic" style="color:var(--tg-hint);">Requested on: ${date} at ${time}</p>
                            <button id="pay-${req.id}" class="btn btn-admin py-2 mt-2 text-sm font-bold rounded-lg transition-colors">
                                Paid & Clear Request
                            </button>
                        `;
                        withdrawalRequestsContainer.appendChild(item);

                        document.getElementById(`pay-${req.id}`).addEventListener('click', () => handleApproval(req.id));
                    });
                    
                }, (error) => {
                    console.error("Admin Listener Error:", error);
                    showStatus("Failed to load admin data.", 'error', 10000);
                });
                
                window.onbeforeunload = unsubscribe;
            }

            // Utility function for copying text (used in admin panel)
            window.copyTextToClipboard = function(text) {
                const tempInput = document.createElement('textarea');
                tempInput.value = text;
                document.body.appendChild(tempInput);
                tempInput.select();
                try {
                    document.execCommand('copy');
                    showStatus('User ID copied!', 'success', 2000);
                } catch (err) {
                    console.error('Copy failed:', err);
                    showStatus('Failed to copy. Copy manually.', 'error');
                }
                document.body.removeChild(tempInput);
            }
            // --- END NEW ADMIN LOGIC ---

            function setupFirestoreListener() {
                if (!window.USER_DOC_REF || !onSnapshot || !window.db) {
                    loadingIndicator.classList.remove('hidden');
                    return; 
                }
                loadingIndicator.classList.add('hidden');
                rewardedBtn.disabled = false; 

                // Check if user is admin
                appState.isAdmin = (window.userId === ADMIN_ID);
                if (appState.isAdmin) {
                    navAdmin.classList.remove('hidden');
                    setupAdminListener();
                } else {
                    navAdmin.classList.add('hidden');
                }


                const unsubscribe = onSnapshot(window.USER_DOC_REF, (docSnapshot) => {
                    if (docSnapshot.exists()) {
                        const data = docSnapshot.data();
                        
                        appState.balanceInSmallestUnit = data.balanceInSmallestUnit || 0;
                        appState.totalAdCount = data.totalAdCount || 0;
                        appState.dailyAdCount = (data.lastAdDate === getTodayDateString()) ? (data.dailyAdCount || 0) : 0;
                        appState.lastAdDate = data.lastAdDate || getTodayDateString();
                        appState.referralCount = data.referralCount || 0;
                        
                        updateUI(appState);
                    } else {
                        // Initialize document if it doesn't exist
                        console.log("Initializing new user data...");
                        doc(window.db, 'artifacts', window.appId, 'users', window.userId, 'earnings', 'user_data').set({
                            balanceInSmallestUnit: 0,
                            totalAdCount: 0,
                            dailyAdCount: 0,
                            lastAdDate: getTodayDateString(),
                            referralCount: 0
                        }, { merge: true }).catch(e => console.error("Initial doc set failed:", e));
                    }
                    
                }, (error) => {
                    console.error("Firestore Listener Error:", error);
                    showStatus("Failed to load data. Check console.", 'error', 10000);
                });
                
                window.onbeforeunload = unsubscribe;

                // Set referral link
                const refLink = `https://t.me/${BOT_USERNAME}?start=ref_${window.userId}`;
                referralLinkElement.textContent = refLink;
                referralLinkElement.onclick = () => {
                    // Use the globally exposed copy function
                    window.copyTextToClipboard(refLink);
                };
            }

            // --- Core App Initialization Logic (Called after Auth) ---
            window.initializeAppLogic = function() {
                tg.ready(); tg.expand();
                tg.setHeaderColor('secondary_bg_color'); tg.setBackgroundColor('bg_color');
                
                setupFirestoreListener(); 

                // Initial check for Ad script visibility
                if (typeof window.show_10060125 !== 'function') {
                    displayAdNotLoadingWarning();
                }

                // Attach Firebase/Ad dependent event listeners
                rewardedBtn.addEventListener('click', requestAd);
                finalWithdrawBtn.addEventListener('click', handleWithdrawal);
                
            };
            
            // --- Immediate DOM Event Listeners (For fast navigation) ---
            navHome.addEventListener('click', () => showView('home-view'));
            mainWithdrawBtn.addEventListener('click', () => { 
                if(!mainWithdrawBtn.disabled) showView('withdraw-view'); 
            });
            navWithdraw.addEventListener('click', () => showView('withdraw-view'));
            navRefer.addEventListener('click', () => showView('referral-view'));
            navAdmin.addEventListener('click', () => showView('admin-view')); // NEW
            navJoin.addEventListener('click', () => window.open(YOUTUBE_CHANNEL_LINK, '_blank'));
            
            // Withdrawal Input/Method Change
            document.querySelectorAll('input[name="paymentMethod"]').forEach(radio => {
                radio.addEventListener('change', (e) => updateWithdrawalInput(e.target.value, appState.balanceInSmallestUnit));
            });
            paymentAddress.addEventListener('input', () => updateWithdrawalInput(appState.selectedMethod, appState.balanceInSmallestUnit));

            // Initial view setup
            showView('home-view'); 

            // Handle immediate Firebase logic if auth is already complete
            if (window.userId && window.db) {
                window.initializeAppLogic();
            } else if (!window.userId) {
                 loadingIndicator.classList.remove('hidden');
            }
        });
    </script>
</body>
</html>
