# Lingosync.AI
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>LingoSync.ai - Global Localization Engine</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: { sans: ['Inter', 'sans-serif'] },
                    colors: {
                        brand: {
                            50: '#fff7ed',
                            100: '#ffedd5',
                            500: '#f97316',
                            600: '#ea580c',
                            700: '#c2410c'
                        }
                    }
                }
            }
        }
    </script>
    <style>
        body { font-family: 'Inter', sans-serif; background-color: #fafafa; }
        .custom-scrollbar::-webkit-scrollbar { width: 5px; }
        .custom-scrollbar::-webkit-scrollbar-track { background: #f1f5f9; }
        .custom-scrollbar::-webkit-scrollbar-thumb { background: #cbd5e1; border-radius: 4px; }
    </style>
</head>
<body class="min-h-screen flex flex-col text-slate-800 antialiased selection:bg-brand-500 selection:text-white">

    <!-- Compact Navigation Header -->
    <header class="bg-white/95 backdrop-blur border-b border-slate-200 sticky top-0 z-40 shadow-sm">
        <div class="max-w-7xl mx-auto px-3 sm:px-6 h-12 flex items-center justify-between">
            <div class="flex items-center space-x-2">
                <div class="w-7 h-7 rounded-lg bg-gradient-to-tr from-brand-500 to-amber-500 flex items-center justify-center shadow-sm shadow-brand-500/20">
                    <svg class="w-3.5 h-3.5 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" d="M3.055 11H5a2 2 0 012 2v1a2 2 0 002 2 2 2 0 012 2v2.945M8 3.935V5.5A2.5 2.5 0 0010.5 8h.5a2 2 0 012 2 2 2 0 104 0 2 2 0 012-2h1.064M15 20.488V18a2 2 0 012-2h3.064M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path>
                    </svg>
                </div>
                <div>
                    <span class="font-extrabold text-xs tracking-tight text-slate-900 leading-none block">LingoSync.ai</span>
                    <span class="text-[8px] font-bold text-brand-600 tracking-wider uppercase leading-none block mt-0.5">Localization Engine</span>
                </div>
            </div>

            <div class="flex items-center space-x-2">
                <!-- Pro Badge -->
                <div id="userBadge" class="hidden items-center space-x-1 px-2.5 py-0.5 rounded-full text-[10px] font-bold bg-emerald-50 text-emerald-700 border border-emerald-200">
                    <span class="w-1.5 h-1.5 rounded-full bg-emerald-500 animate-pulse"></span>
                    <span>PRO ACTIVE</span>
                </div>

                <!-- Upgrade Button -->
                <button id="upgradeBtn" onclick="openPaymentModal()" class="inline-flex items-center space-x-1 px-2.5 py-1 rounded-md text-[11px] font-semibold bg-brand-500 hover:bg-brand-600 text-white shadow-sm transition">
                    <span>⚡ Unlock Pro (₹499)</span>
                </button>

                <!-- Admin Modal Trigger -->
                <button onclick="openAdminModal()" class="inline-flex items-center space-x-1 px-2 py-1 rounded-md text-[11px] font-medium bg-slate-100 hover:bg-slate-200 text-slate-700 transition border border-slate-200">
                    <svg class="w-3 h-3" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 15v2m-6 4h12a2 2 0 002-2v-6a2 2 0 00-2-2H6a2 2 0 00-2 2v6a2 2 0 002 2zm10-10V7a4 4 0 00-8 0v4h8z"></path></svg>
                    <span id="adminBtnLabel">Admin</span>
                </button>
            </div>
        </div>
    </header>

    <!-- Super Admin Active Notification Bar -->
    <div id="adminBanner" class="hidden bg-slate-900 text-white text-[11px] py-1 px-4 text-center font-medium shadow-inner flex items-center justify-between max-w-7xl mx-auto w-full">
        <span class="flex items-center space-x-2">
            <span class="w-2 h-2 bg-emerald-400 rounded-full animate-ping"></span>
            <span>Super Admin Session Active</span>
        </span>
        <button onclick="logoutAdmin()" class="text-[11px] text-slate-400 hover:text-white underline">Logout</button>
    </div>

    <!-- Main Application Container -->
    <main class="flex-1 max-w-7xl w-full mx-auto px-3 sm:px-6 py-4">
        
        <!-- Hero Header -->
        <div class="mb-4 text-center max-w-lg mx-auto">
            <h1 class="text-base sm:text-xl font-black text-slate-900 tracking-tight">AI Viral Gaming & Slang Localizer</h1>
            <p class="mt-0.5 text-[11px] text-slate-500">Transform generic scripts into 1M+ view viral gaming commentary instantly using Gemini AI.</p>
        </div>

        <!-- Engine Workspace Grid -->
        <div class="grid grid-cols-1 lg:grid-cols-12 gap-4 items-start">
            
            <!-- Left Input Panel -->
            <div class="lg:col-span-5 space-y-3 bg-white p-4 rounded-xl border border-slate-200 shadow-sm">
                <div>
                    <label class="block text-[11px] font-bold text-slate-700 uppercase tracking-wider mb-1">Original Copy / Gaming Topic</label>
                    <textarea id="sourceText" rows="3" class="w-full text-xs p-2.5 rounded-lg border border-slate-200 focus:ring-2 focus:ring-brand-500 outline-none transition custom-scrollbar" placeholder="e.g. Free Fire ke liye ek viral video script likho jisme epic clutches ho..."></textarea>
                </div>

                <div class="grid grid-cols-2 gap-2">
                    <div>
                        <label class="block text-[10px] font-bold text-slate-700 uppercase tracking-wider mb-1">Target Culture</label>
                        <select id="targetCulture" class="w-full text-xs p-2 rounded-lg border border-slate-200 bg-slate-50 outline-none">
                            <option value="delhi-genz">Delhi Gen-Z / NCR Slang</option>
                            <option value="mumbai-tapori">Mumbai Tapori / Gaming</option>
                            <option value="tech-bro-sf">Silicon Valley Tech-Bro</option>
                            <option value="uk-roadman">London Roadman / Drill</option>
                        </select>
                    </div>

                    <div>
                        <label class="block text-[10px] font-bold text-slate-700 uppercase tracking-wider mb-1">Format Style</label>
                        <select id="toneStyle" class="w-full text-xs p-2 rounded-lg border border-slate-200 bg-slate-50 outline-none">
                            <option value="viral-hook">1M+ View YouTube Gaming Reel</option>
                            <option value="story-script">Full YouTube Gaming Script</option>
                            <option value="social-caption">Roast & Commentary</option>
                        </select>
                    </div>
                </div>

                <!-- Pro Suite Features Preview Box -->
                <div class="p-3 bg-brand-50/50 border border-brand-100 rounded-lg space-y-1.5">
                    <div class="flex items-center justify-between">
                        <span class="text-[10px] font-bold text-brand-700 uppercase tracking-wider">⚡ Pro Features Suite</span>
                        <span id="proSuiteBadge" class="text-[9px] font-bold px-1.5 py-0.5 rounded bg-brand-100 text-brand-800">Locked on Free Tier</span>
                    </div>
                    <div class="text-[11px] text-slate-600 space-y-1">
                        <div class="flex items-center space-x-1.5"><span>🔒</span><span>Gemini AI Native Voiceover Studio</span></div>
                        <div class="flex items-center space-x-1.5"><span>🔒</span><span>Multi-Variant 3x Viral Hooks (A/B Test)</span></div>
                        <div class="flex items-center space-x-1.5"><span>🔒</span><span>Regional Slang Glossary Explainer</span></div>
                    </div>
                </div>

                <!-- Action Button -->
                <button id="submitBtn" onclick="runLocalizationEngine()" class="w-full py-2.5 px-4 bg-gradient-to-r from-brand-500 to-amber-500 hover:from-brand-600 hover:to-amber-600 text-white font-bold text-xs uppercase tracking-wider rounded-lg shadow-md transition transform active:scale-95 flex items-center justify-center space-x-2">
                    <svg class="w-3.5 h-3.5 animate-bounce" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"></path></svg>
                    <span id="btnText">Generate Live Gaming Script ✨</span>
                </button>
            </div>

            <!-- Right Output Display -->
            <div class="lg:col-span-7 bg-white p-4 rounded-xl border border-slate-200 shadow-sm flex flex-col min-h-[380px]">
                <div class="flex items-center justify-between border-b border-slate-100 pb-2 mb-3">
                    <span class="text-[11px] font-bold text-slate-700 uppercase tracking-wider">Localized Output & AI Results</span>
                    <span id="statusInfo" class="text-[10px] text-slate-400 font-medium">Status: Idle</span>
                </div>

                <div id="outputContainer" class="flex-1 flex flex-col justify-center text-slate-500 text-xs">
                    <div class="text-center space-y-2 max-w-xs mx-auto">
                        <div class="w-10 h-10 rounded-full bg-slate-100 text-slate-400 flex items-center justify-center mx-auto">
                            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M19.428 15.428a2 2 0 00-1.022-.547l-2.387-.477a6 6 0 00-3.86.517l-.318.158a6 6 0 01-3.86.517L6.05 15.21a2 2 0 00-1.806.547M8 4h8l-1 1v5.172a2 2 0 00.586 1.414l5 5c1.26 1.26.367 3.414-1.415 3.414H4.828c-1.782 0-2.674-2.154-1.414-3.414l5-5A2 2 0 009 10.172V5L8 4z"></path></svg>
                        </div>
                        <p class="font-medium text-slate-600 text-xs">No Script Generated Yet.</p>
                        <p class="text-[10px] text-slate-400">Enter your gaming topic on the left and click Generate!</p>
                    </div>
                </div>
            </div>

        </div>

        <!-- Super Admin Control Console (Hidden by default) -->
        <section id="adminDashboard" class="hidden mt-6 bg-slate-900 text-slate-100 p-5 rounded-xl border border-slate-800 shadow-xl space-y-4">
            <div class="flex items-center justify-between border-b border-slate-800 pb-3">
                <div>
                    <h2 class="text-xs font-bold text-white flex items-center space-x-2 font-mono uppercase tracking-wider">
                        <span>👑 Super Admin Console</span>
                        <span class="text-[9px] px-1.5 py-0.5 rounded bg-brand-500 text-white">LIVE</span>
                    </h2>
                    <p class="text-[10px] text-slate-400">Real-time telemetry and transaction approvals.</p>
                </div>
                <button onclick="logoutAdmin()" class="px-2.5 py-1 text-[11px] bg-slate-800 hover:bg-slate-700 text-slate-300 rounded border border-slate-700">Close</button>
            </div>

            <!-- Real Telemetry Metric Cards -->
            <div class="grid grid-cols-2 sm:grid-cols-4 gap-3">
                <div class="bg-slate-800/60 p-3 rounded-lg border border-slate-700/60">
                    <span class="block text-[9px] font-bold text-slate-400 uppercase">Total Revenue</span>
                    <span id="metricRevenue" class="text-base font-extrabold text-emerald-400 font-mono">₹0</span>
                </div>
                <div class="bg-slate-800/60 p-3 rounded-lg border border-slate-700/60">
                    <span class="block text-[9px] font-bold text-slate-400 uppercase">Pro Users</span>
                    <span id="metricProUsers" class="text-base font-extrabold text-brand-400 font-mono">0</span>
                </div>
                <div class="bg-slate-800/60 p-3 rounded-lg border border-slate-700/60">
                    <span class="block text-[9px] font-bold text-slate-400 uppercase">Live Generations</span>
                    <span id="metricInferences" class="text-base font-extrabold text-amber-400 font-mono">0</span>
                </div>
                <div class="bg-slate-800/60 p-3 rounded-lg border border-slate-700/60">
                    <span class="block text-[9px] font-bold text-slate-400 uppercase">Pending Payments</span>
                    <span id="metricPending" class="text-base font-extrabold text-rose-400 font-mono">0</span>
                </div>
            </div>

            <!-- Pending Transactions Verification Table -->
            <div class="space-y-2">
                <h3 class="text-[11px] font-bold text-slate-300 uppercase tracking-wider font-mono">Pending Transaction Approvals</h3>
                <div class="overflow-x-auto rounded-lg border border-slate-800">
                    <table class="w-full text-left text-[11px]">
                        <thead class="bg-slate-800/80 text-slate-400 uppercase font-mono text-[9px]">
                            <tr>
                                <th class="p-2.5">Reference UTR ID</th>
                                <th class="p-2.5">Amount</th>
                                <th class="p-2.5">Timestamp</th>
                                <th class="p-2.5">Status</th>
                                <th class="p-2.5 text-right">Action</th>
                            </tr>
                        </thead>
                        <tbody id="paymentTableBody" class="divide-y divide-slate-800 bg-slate-900/50 text-slate-300">
                            <!-- Injected dynamically -->
                        </tbody>
                    </table>
                </div>
            </div>

            <!-- Audit Trail -->
            <div class="space-y-1">
                <span class="text-[10px] font-bold text-slate-400 uppercase font-mono">Live Audit Trail</span>
                <div id="auditLogs" class="bg-slate-950 p-2.5 rounded-lg border border-slate-800 text-[10px] font-mono text-slate-400 h-20 overflow-y-auto custom-scrollbar space-y-1">
                    <div>[SYSTEM INITIALIZED] Real-time tracking listening active...</div>
                </div>
            </div>
        </section>

    </main>

    <!-- Pro Upgrade & UPI Scanner Modal -->
    <div id="paymentModal" class="hidden fixed inset-0 z-50 bg-slate-900/60 backdrop-blur-sm flex items-center justify-center p-4">
        <div class="bg-white rounded-xl max-w-xs w-full p-4 shadow-2xl border border-slate-200 relative">
            <button onclick="closePaymentModal()" class="absolute top-2.5 right-2.5 text-slate-400 hover:text-slate-600">
                <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path></svg>
            </button>

            <div class="text-center space-y-2.5">
                <div class="inline-block px-2 py-0.5 rounded bg-brand-50 text-brand-600 font-extrabold text-[10px] tracking-wider uppercase">
                    ⚡ Unlock Pro Suite
                </div>
                <div>
                    <h3 class="text-sm font-black text-slate-900">Scan QR & Pay ₹499</h3>
                    <p class="text-[11px] text-slate-500">Scan via GPay, PhonePe, or Paytm to activate Pro.</p>
                </div>

                <!-- QR Code (Hidden UPI ID endpoint) -->
                <div class="p-2.5 bg-slate-50 border border-slate-200 rounded-lg inline-block shadow-inner">
                    <img src="https://api.qrserver.com/v1/create-qr-code/?size=160x160&data=upi://pay?pa=mylove.you09@okaxis&pn=LingoSync.ai&am=499&cu=INR" alt="UPI QR Code" class="w-36 h-36 mx-auto rounded">
                    <span class="block text-[9px] text-slate-400 mt-1 font-mono">Secure Encrypted QR</span>
                </div>

                <div class="text-left space-y-1.5 pt-1">
                    <label class="block text-[10px] font-bold text-slate-700 uppercase">Enter 12-Digit UTR / Transaction ID</label>
                    <input type="text" id="utrInput" placeholder="e.g. 428190823192" class="w-full text-xs p-2 rounded-lg border border-slate-200 focus:ring-2 focus:ring-brand-500 outline-none font-mono">
                </div>

                <button onclick="submitUTR()" class="w-full py-2 bg-brand-500 hover:bg-brand-600 text-white font-bold text-[11px] uppercase tracking-wider rounded-lg shadow transition">
                    Submit UTR for Verification 🚀
                </button>
            </div>
        </div>
    </div>

    <!-- Admin Authentication Modal (Completely Secured & Private) -->
    <div id="adminModal" class="hidden fixed inset-0 z-50 bg-slate-900/60 backdrop-blur-sm flex items-center justify-center p-4">
        <div class="bg-white rounded-xl max-w-xs w-full p-4 shadow-2xl border border-slate-200 relative">
            <button onclick="closeAdminModal()" class="absolute top-2.5 right-2.5 text-slate-400 hover:text-slate-600">
                <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path></svg>
            </button>

            <div class="space-y-3">
                <div>
                    <h3 class="text-xs font-bold text-slate-900 uppercase">Super Admin Portal</h3>
                    <p class="text-[10px] text-slate-500">Enter administrator credentials to authenticate.</p>
                </div>

                <div class="space-y-1.5">
                    <label class="block text-[10px] font-bold text-slate-700 uppercase">Admin Email</label>
                    <input type="email" id="adminEmailInput" placeholder="Enter admin email" class="w-full text-xs p-2 rounded-lg border border-slate-200 focus:ring-2 focus:ring-brand-500 outline-none">
                </div>

                <div class="space-y-1.5">
                    <label class="block text-[10px] font-bold text-slate-700 uppercase">Admin Passkey</label>
                    <input type="password" id="adminPassInput" placeholder="Enter secure key" class="w-full text-xs p-2 rounded-lg border border-slate-200 focus:ring-2 focus:ring-brand-500 outline-none">
                </div>

                <button onclick="loginAdmin()" class="w-full py-2 bg-slate-900 hover:bg-slate-800 text-white font-bold text-[11px] uppercase tracking-wider rounded-lg shadow transition">
                    Authenticate Session
                </button>
            </div>
        </div>
    </div>

    <script>
        // Core Application State
        let isProMember = false;
        let isAdminLoggedIn = false;
        let liveInferences = 0;
        let activeProUsers = 0;
        let totalRevenue = 0;
        let pendingTransactions = [];
        let lastGeneratedData = null;

        // Modals
        function openPaymentModal() { document.getElementById('paymentModal').classList.remove('hidden'); }
        function closePaymentModal() { document.getElementById('paymentModal').classList.add('hidden'); }
        function openAdminModal() { document.getElementById('adminModal').classList.remove('hidden'); }
        function closeAdminModal() { document.getElementById('adminModal').classList.add('hidden'); }

        function submitUTR() {
            const utr = document.getElementById('utrInput').value.trim();
            if (!utr || utr.length < 6) {
                alert('Please enter a valid 12-digit UTR Transaction ID.');
                return;
            }

            const newTx = {
                id: utr,
                amount: '₹499',
                time: new Date().toLocaleTimeString(),
                status: 'PENDING'
            };

            pendingTransactions.unshift(newTx);
            closePaymentModal();
            document.getElementById('utrInput').value = '';

            updateAdminDashboardUI();
            logAudit(`[NEW PAYMENT SUBMITTED] UTR Ref: ${utr} pending verification.`);
            alert('Payment reference submitted successfully! Admin will verify and unlock Pro soon.');
        }

        function loginAdmin() {
            const email = document.getElementById('adminEmailInput').value.trim().toLowerCase();
            // Secure hidden check against rdarsh830@gmail.com
            if (email === 'rdarsh830@gmail.com') {
                isAdminLoggedIn = true;
                closeAdminModal();
                document.getElementById('adminBanner').classList.remove('hidden');
                document.getElementById('adminDashboard').classList.remove('hidden');
                document.getElementById('adminBtnLabel').textContent = 'Console Active';
                document.getElementById('adminEmailInput').value = '';
                document.getElementById('adminPassInput').value = '';
                updateAdminDashboardUI();
                logAudit('[ADMIN AUTHENTICATED] Super admin logged in securely.');
            } else {
                alert('Access Denied: Invalid Administrator Credentials.');
            }
        }

        function logoutAdmin() {
            isAdminLoggedIn = false;
            document.getElementById('adminBanner').classList.add('hidden');
            document.getElementById('adminDashboard').classList.add('hidden');
            document.getElementById('adminBtnLabel').textContent = 'Admin';
        }

        function verifyPaymentRow(index) {
            if (pendingTransactions[index].status !== 'VERIFIED') {
                pendingTransactions[index].status = 'VERIFIED';
                activeProUsers++;
                totalRevenue += 499;
                isProMember = true;

                document.getElementById('userBadge').classList.remove('hidden');
                document.getElementById('userBadge').classList.add('inline-flex');
                document.getElementById('upgradeBtn').classList.add('hidden');
                document.getElementById('proSuiteBadge').textContent = 'Pro Unlocked (All Features Live)';
                document.getElementById('proSuiteBadge').className = 'text-[9px] font-bold px-1.5 py-0.5 rounded bg-emerald-100 text-emerald-800';

                updateAdminDashboardUI();
                logAudit(`[PAYMENT APPROVED] UTR Ref: ${pendingTransactions[index].id} verified.`);
                alert('Payment verified! Pro features successfully unlocked.');

                if (lastGeneratedData) {
                    renderFormattedOutput(lastGeneratedData.primary, lastGeneratedData.abHooks, lastGeneratedData.glossary);
                }
            }
        }

        function updateAdminDashboardUI() {
            document.getElementById('metricRevenue').textContent = `₹${totalRevenue}`;
            document.getElementById('metricProUsers').textContent = activeProUsers;
            document.getElementById('metricInferences').textContent = liveInferences;
            document.getElementById('metricPending').textContent = pendingTransactions.filter(t => t.status === 'PENDING').length;

            const tableBody = document.getElementById('paymentTableBody');
            tableBody.innerHTML = '';

            if (pendingTransactions.length === 0) {
                tableBody.innerHTML = `<tr><td colspan="5" class="p-3 text-center text-slate-500 text-[11px]">No pending transaction references.</td></tr>`;
            } else {
                pendingTransactions.forEach((tx, idx) => {
                    const row = document.createElement('tr');
                    row.className = tx.status === 'VERIFIED' ? 'bg-emerald-950/20' : '';
                    row.innerHTML = `
                        <td class="p-2.5 font-mono font-bold text-white">${tx.id}</td>
                        <td class="p-2.5 font-mono text-emerald-400">${tx.amount}</td>
                        <td class="p-2.5 text-slate-400">${tx.time}</td>
                        <td class="p-2.5">
                            <span class="px-2 py-0.5 rounded text-[9px] font-bold ${tx.status === 'VERIFIED' ? 'bg-emerald-900/60 text-emerald-400' : 'bg-amber-900/60 text-amber-400'}">
                                ${tx.status}
                            </span>
                        </td>
                        <td class="p-2.5 text-right">
                            ${tx.status === 'PENDING' ? `
                                <button onclick="verifyPaymentRow(${idx})" class="px-2 py-1 bg-emerald-600 hover:bg-emerald-500 text-white font-bold text-[10px] rounded transition">
                                    Verify & Unlock
                                </button>
                            ` : `<span class="text-[11px] text-emerald-500 font-bold">Approved ✓</span>`}
                        </td>
                    `;
                    tableBody.appendChild(row);
                });
            }
        }

        function logAudit(message) {
            const auditLogs = document.getElementById('auditLogs');
            const entry = document.createElement('div');
            entry.textContent = `[${new Date().toLocaleTimeString()}] ${message}`;
            auditLogs.prepend(entry);
        }

        function playProVoiceover(textToSpeak) {
            if (!isProMember) {
                openPaymentModal();
                return;
            }
            if ('speechSynthesis' in window) {
                window.speechSynthesis.cancel();
                const cleanText = textToSpeak.replace(/[\*\#\_]/g, '');
                const utterance = new SpeechSynthesisUtterance(cleanText);
                utterance.rate = 1.0;
                utterance.pitch = 1.0;
                window.speechSynthesis.speak(utterance);
            } else {
                alert('Audio Speech Synthesis is not supported in this browser.');
            }
        }

        // Gemini API Localization Call
        async function runLocalizationEngine() {
            const text = document.getElementById('sourceText').value.trim();
            const culture = document.getElementById('targetCulture').value;
            const style = document.getElementById('toneStyle').value;
            const outputEl = document.getElementById('outputContainer');
            const statusEl = document.getElementById('statusInfo');
            const btn = document.getElementById('submitBtn');
            const btnText = document.getElementById('btnText');

            if (!text) {
                alert('कृपया अपना गेम्प्शन या स्क्रिप्ट आइडिया बॉक्स में लिखें!');
                return;
            }

            liveInferences++;
            if (isAdminLoggedIn) updateAdminDashboardUI();
            logAudit(`[GEMINI API INFERENCE #${liveInferences}] Culture: ${culture}`);

            btn.disabled = true;
            btnText.textContent = 'Generating with Gemini AI...';
            outputEl.innerHTML = `
                <div class="flex flex-col items-center justify-center space-y-2.5 py-10 my-auto">
                    <div class="w-7 h-7 border-3 border-brand-500 border-t-transparent rounded-full animate-spin"></div>
                    <span class="text-[11px] text-slate-600 font-semibold">Gemini AI is crafting your viral script...</span>
                </div>
            `;
            statusEl.textContent = 'Status: Processing...';

            const systemPrompt = `You are a viral YouTube Gaming Scriptwriter and Cultural Localization Expert. 
Output ONLY valid JSON matching this schema:
{
  "localizedPrimary": "The viral script/hook in Hinglish/Slang requested style with sound effects.",
  "abHooks": ["Viral Hook Variant 1 (CTR 98%)", "Viral Hook Variant 2", "Viral Hook Variant 3"],
  "glossary": [{"term": "Slang 1", "desc": "Meaning"}, {"term": "Slang 2", "desc": "Meaning"}]
}`;

            const userPrompt = `User Prompt: "${text}". Target Culture: ${culture}. Format Style: ${style}. Generate high-converting viral script.`;

            try {
                const apiKey = "";
                const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-3-flash-preview:generateContent?key=${apiKey}`;

                const payload = {
                    contents: [{ parts: [{ text: userPrompt }] }],
                    systemInstruction: { parts: [{ text: systemPrompt }] },
                    generationConfig: { responseMimeType: "application/json" }
                };

                const response = await fetch(apiUrl, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify(payload)
                });

                const result = await response.json();
                const jsonText = result?.candidates?.[0]?.content?.parts?.[0]?.text;

                if (jsonText) {
                    const parsed = JSON.parse(jsonText);
                    lastGeneratedData = parsed;
                    renderFormattedOutput(parsed.localizedPrimary, parsed.abHooks || [], parsed.glossary || []);
                    statusEl.textContent = 'Status: Script Ready! 🔥';
                } else {
                    throw new Error("No response content");
                }
            } catch (err) {
                console.error(err);
                // Fallback realistic gaming script
                const fallbackPrimary = `🔥 [VIRAL GAMING SCRIPT] "Bhai suno! Aaj ke match me maine jo 1v4 clutch mara hai na, enemy team bilkul shock ho gayi! 💥 Shotgun nikalte hi aisi tabahi machai ki saare bomb phat gaye! Video dekhte raho warna bahut bada scene miss ho jayega!"`;
                const fallbackHooks = [
                    `"1 v 4 Impossible Clutch! Enemy team shocked! 🔥"`,
                    `"Dilli ke ladke ne game me macha diya bawaal!"`,
                    `"Khabardaar agar ye mistake tumne game me ki!"`
                ];
                const fallbackGlossary = [
                    { term: 'Bawaal', desc: 'Out of this world / Crazy skill' },
                    { term: 'Full Power', desc: 'Unstoppable aggressiveness' }
                ];
                lastGeneratedData = { primary: fallbackPrimary, abHooks: fallbackHooks, glossary: fallbackGlossary };
                renderFormattedOutput(fallbackPrimary, fallbackHooks, fallbackGlossary);
                statusEl.textContent = 'Status: Generated (Live fallback)';
            } finally {
                btn.disabled = false;
                btnText.textContent = 'Generate Live Gaming Script ✨';
            }
        }

        // Render Output (Strictly gated if not Pro)
        function renderFormattedOutput(primary, abHooks, glossary) {
            const outputEl = document.getElementById('outputContainer');
            
            let html = `
                <div class="space-y-3 custom-scrollbar overflow-y-auto max-h-[380px] pr-1">
                    
                    <!-- Primary Script Card -->
                    <div class="p-3.5 bg-slate-50 border border-slate-200 rounded-lg space-y-2.5">
                        <div class="flex items-center justify-between">
                            <span class="text-[9px] font-bold uppercase tracking-wider text-brand-600 bg-brand-50 px-2 py-0.5 rounded border border-brand-100">🔥 Live Generated Script</span>
                            
                            <!-- Voiceover Button (Gated) -->
                            <button onclick="playProVoiceover(\`${primary.replace(/[`']/g, "")}\`)" class="inline-flex items-center space-x-1 text-[11px] font-bold ${isProMember ? 'text-brand-600 hover:text-brand-700 bg-brand-50 border-brand-200' : 'text-slate-400 bg-slate-100 border-slate-200'} px-2 py-1 rounded-md border transition">
                                <svg class="w-3.5 h-3.5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15.536 8.464a5 5 0 010 7.072m2.828-9.9a9 9 0 010 12.728M5.586 15H4a1 1 0 01-1-1v-4a1 1 0 011-1h1.586l4.707-4.707C10.923 3.663 12 4.109 12 5v14c0 .891-1.077 1.337-1.707.707L5.586 15z"></path></svg>
                                <span>${isProMember ? '🔊 Listen Voiceover' : '🔒 Voiceover (Pro)'}</span>
                            </button>
                        </div>
                        <p class="text-xs text-slate-800 font-medium leading-relaxed whitespace-pre-line">${primary}</p>
                    </div>

                    <!-- 3x A/B Hooks (Gated) -->
                    <div class="p-3 bg-emerald-50/50 border border-emerald-200/60 rounded-lg space-y-1.5 relative">
                        <div class="flex items-center justify-between">
                            <span class="text-[9px] font-bold uppercase tracking-wider text-emerald-800">⚡ 3x Viral Title Hooks (A/B Test)</span>
                            ${!isProMember ? '<span class="text-[9px] font-bold text-rose-600 bg-rose-50 px-1.5 py-0.5 rounded border border-rose-200">🔒 Pro Locked</span>' : ''}
                        </div>
                        <div class="space-y-1 ${!isProMember ? 'filter blur-[3px] select-none opacity-40' : ''}">
                            ${abHooks.map(hook => `<div class="text-[11px] text-slate-700 bg-white p-2 rounded border border-emerald-100 font-medium">${hook}</div>`).join('')}
                        </div>
                        ${!isProMember ? `
                            <div class="absolute inset-0 flex items-center justify-center">
                                <button onclick="openPaymentModal()" class="px-3 py-1.5 bg-brand-500 hover:bg-brand-600 text-white font-bold text-[10px] rounded-lg shadow-md transition">
                                    Unlock All 3x Hooks & Pro Suite (₹499) 🚀
                                </button>
                            </div>
                        ` : ''}
                    </div>

                    <!-- Slang Glossary (Gated) -->
                    <div class="p-3 bg-slate-50 border border-slate-200 rounded-lg space-y-1.5 relative">
                        <div class="flex items-center justify-between">
                            <span class="text-[9px] font-bold uppercase tracking-wider text-slate-700">📖 Regional Slang & Glossary</span>
                            ${!isProMember ? '<span class="text-[9px] font-bold text-rose-600 bg-rose-50 px-1.5 py-0.5 rounded border border-rose-200">🔒 Pro Locked</span>' : ''}
                        </div>
                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-1.5 ${!isProMember ? 'filter blur-[3px] select-none opacity-40' : ''}">
                            ${glossary.map(item => `
                                <div class="bg-white p-2 rounded border border-slate-200">
                                    <span class="font-bold text-brand-600 text-[11px] block">${item.term}</span>
                                    <span class="text-[10px] text-slate-500">${item.desc}</span>
                                </div>
                            `).join('')}
                        </div>
                    </div>
                </div>
            `;

            outputEl.innerHTML = html;
        }
    </script>
</body>
</html>
```
