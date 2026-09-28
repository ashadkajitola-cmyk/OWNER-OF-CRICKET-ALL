<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cricket Schedule & Betting Platform Pro Max</title>
    <style>
        :root {
            --primary: #1e3c72;
            --secondary: #2a5298;
            --accent: #ff9800;
            --bg: #f0f4f8;
            --white: #ffffff;
            --text: #222222;
            --danger: #e74c3c;
            --success: #2ecc71;
            --border: #dcdcdc;
        }
        * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; }
        body { background-color: var(--bg); color: var(--text); padding-bottom: 60px; font-size: 16px; }
        
        header { background: linear-gradient(135deg, var(--primary), var(--secondary)); color: var(--white); padding: 20px 25px; display: flex; justify-content: space-between; align-items: center; box-shadow: 0 4px 20px rgba(0,0,0,0.2); }
        header h1 { font-size: 1.5rem; font-weight: 800; letter-spacing: 0.5px; }
        .user-info { display: flex; gap: 15px; align-items: center; font-size: 1rem; }
        .wallet-badge { background: var(--accent); color: #000; padding: 8px 16px; border-radius: 30px; font-weight: bold; font-size: 1.05rem; box-shadow: 0 3px 6px rgba(0,0,0,0.15); }
        
        .container { max-width: 950px; margin: 25px auto; padding: 0 15px; display: flex; flex-direction: column; gap: 20px; }
        .card { background: var(--white); border-radius: 14px; padding: 25px; box-shadow: 0 6px 18px rgba(0,0,0,0.06); }
        
        h2 { font-size: 1.5rem; margin-bottom: 12px; color: var(--primary); font-weight: 700; }
        h3 { font-size: 1.25rem; margin-bottom: 10px; color: #333; font-weight: 700; }
        
        .btn { background: var(--secondary); color: var(--white); border: none; padding: 14px 20px; border-radius: 8px; cursor: pointer; font-weight: bold; font-size: 1.05rem; transition: 0.2s; box-shadow: 0 3px 6px rgba(0,0,0,0.1); width: 100%; text-align: center; display: inline-block; }
        .btn:hover { opacity: 0.92; transform: translateY(-2px); }
        .btn-danger { background: var(--danger); }
        .btn-success { background: var(--success); }
        .btn-warning { background: var(--accent); color: #000; }
        
        input, select, textarea { width: 100%; padding: 14px 16px; margin: 8px 0 18px 0; border: 2px solid var(--border); border-radius: 8px; font-size: 1.05rem; background: #fff; }
        input:focus, select:focus { border-color: var(--secondary); outline: none; }
        label { font-weight: 700; font-size: 0.95rem; color: #444; display: block; margin-top: 5px; }
        
        .tabs { display: flex; gap: 8px; margin-bottom: 15px; background: #e2e8f0; padding: 6px; border-radius: 10px; flex-wrap: wrap; }
        .tab-btn { flex: 1; min-width: 140px; padding: 12px; background: transparent; border: none; border-radius: 8px; cursor: pointer; font-weight: bold; color: #555; transition: 0.2s; font-size: 0.95rem; text-align: center; }
        .tab-btn.active { background: var(--white); color: var(--primary); box-shadow: 0 3px 8px rgba(0,0,0,0.1); }
        
        .match-card { border: 2px solid var(--border); border-radius: 12px; padding: 20px; margin-bottom: 18px; background: var(--white); box-shadow: 0 3px 8px rgba(0,0,0,0.03); }
        .match-card.new-series-gap { border-left: 6px solid var(--accent); }
        .series-title-bar { background: #e8f4fd; color: #1a5276; padding: 10px 15px; border-radius: 8px; font-weight: bold; font-size: 1.05rem; margin-bottom: 15px; display: flex; justify-content: space-between; align-items: center; }
        .match-row { display: flex; justify-content: space-between; align-items: center; margin: 15px 0; }
        .team-box { font-size: 1.25rem; font-weight: 800; display: flex; align-items: center; gap: 10px; color: var(--primary); }
        .vs-text { font-weight: 800; color: #777; font-size: 1.1rem; text-align: center; display: flex; flex-direction: column; align-items: center; gap: 4px; }
        .match-format-green { background: var(--success); color: #fff; padding: 3px 10px; border-radius: 20px; font-size: 0.8rem; font-weight: bold; letter-spacing: 0.5px; }
        
        .physical-ticket {
            background: linear-gradient(135deg, #1e3c72 0%, #2a5298 50%, #ff9800 100%);
            color: #fff;
            border-radius: 16px;
            padding: 22px;
            margin-bottom: 24px;
            box-shadow: 0 8px 25px rgba(0,0,0,0.25);
            border: 2px dashed rgba(255,255,255,0.7);
        }
        .ticket-header { display: flex; justify-content: space-between; align-items: center; font-size: 0.95rem; text-transform: uppercase; letter-spacing: 1px; border-bottom: 1px solid rgba(255,255,255,0.4); padding-bottom: 10px; margin-bottom: 14px; font-weight: bold; }
        .ticket-teams-title { font-size: 1.8rem; font-weight: 900; letter-spacing: 1px; text-align: center; margin: 12px 0; text-shadow: 2px 2px 6px rgba(0,0,0,0.3); }
        .ticket-format-badge { background: #fff; color: #1e3c72; padding: 6px 12px; border-radius: 6px; font-size: 0.9rem; font-weight: bold; display: inline-block; }
        .ticket-datetime { text-align: center; font-size: 1.1rem; font-weight: bold; background: rgba(0,0,0,0.25); padding: 8px; border-radius: 8px; margin: 12px 0; color: #ffeb3b; }
        .ticket-venue { text-align: center; font-size: 1rem; opacity: 0.95; margin-bottom: 10px; font-weight: 600; }
        .ticket-gate { text-align: center; font-size: 0.95rem; background: rgba(255,255,255,0.25); padding: 6px; border-radius: 6px; margin-bottom: 12px; font-weight: bold; }
        .ticket-footer { display: flex; justify-content: space-between; align-items: center; background: rgba(255,255,255,0.95); color: #333; padding: 12px 16px; border-radius: 8px; font-size: 0.95rem; font-weight: bold; }

        .hidden { display: none !important; }
        .flex-row { display: flex; gap: 12px; }
        .flex-row > * { flex: 1; }
        
        .modal { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.7); display: flex; justify-content: center; align-items: center; z-index: 1000; overflow-y: auto; padding: 20px; }
        .modal-content { background: var(--white); padding: 30px; border-radius: 16px; width: 100%; max-width: 650px; position: relative; max-height: 90vh; overflow-y: auto; box-shadow: 0 10px 30px rgba(0,0,0,0.3); }
        .close-modal { position: absolute; top: 15px; right: 20px; font-size: 1.8rem; cursor: pointer; color: #666; font-weight: bold; }
        
        .alert-box { padding: 14px; margin-bottom: 15px; border-radius: 8px; font-size: 1rem; font-weight: 600; }
        .alert-error { background: #fadbd8; color: #78281f; }
        .alert-success { background: #d4efdf; color: #145a32; }
    </style>
</head>
<body>

    <header>
        <h1>🏏 Cricket Schedule & Betting Pro</h1>
        <div class="user-info">
            <span id="displayNumber" style="font-weight: 700;">Login करें</span>
            <span class="wallet-badge">Wallet: ₹<span id="displayWallet">0</span></span>
            <button class="btn btn-danger" onclick="logout()" style="padding: 8px 16px; font-size: 0.9rem; width: auto;">Logout</button>
        </div>
    </header>

    <div class="container">
        <!-- 1. Login Section -->
        <div id="loginSection" class="card">
            <h2>🔐 Login / Register</h2>
            <p id="deviceLimitInfo" style="font-size:0.95rem; color:#555; margin-bottom:15px;"></p>
            <label>Mobile Number:</label>
            <input type="text" id="loginMobileInput" placeholder="Enter 10-digit mobile number">
            <button class="btn" onclick="handleLogin()">Login to Dashboard</button>
        </div>

        <!-- Main Dashboard -->
        <div id="mainDashboard" class="hidden">
            
            <div id="activeSubStatusBox" class="card hidden" style="border-left: 6px solid var(--primary); background: #f8fafc;">
                <h3>✨ Active Subscription Status</h3>
                <div id="subStatusContent" style="margin-top: 10px; font-size: 1.05rem; font-weight: 600; color: #1e3c72;"></div>
            </div>

            <div class="card" style="border-left: 6px solid var(--accent); background: #fffbeb;">
                <h3>📦 Subscription Plans Hub</h3>
                <p style="font-size: 0.95rem; color: #555; margin-bottom: 12px;">Apna schedule create karne ya premium features ke liye plan select karke buy karein:</p>
                <div id="subPlansList" style="display: flex; flex-direction: column; gap: 10px; margin-bottom: 15px;"></div>
                <button class="btn btn-warning" onclick="buySelectedSubscriptionFromHub()">🚀 Buy Selected Subscription Plan</button>
            </div>

            <div class="card" style="border-left: 6px solid var(--success);">
                <h3>💳 Wallet Recharge Request (Transaction ID / UTR)</h3>
                <p style="font-size: 0.95rem; color: #555; margin-bottom: 12px;">Payment SMS ki Full Transaction ID ya UTR number yahan dalein. Admin verify karne ke baad ₹210 approve karega.</p>
                <label>Full Transaction ID / UTR:</label>
                <input type="text" id="txFullInput" placeholder="Enter full transaction reference ID">
                <button class="btn btn-success" onclick="submitRechargeRequest()">Submit for Admin Verification</button>
            </div>

            <div class="card" style="border-left: 6px solid var(--secondary);">
                <h3>📂 Creator & Schedule Panel</h3>
                <p style="font-size: 0.95rem; color: #555; margin-bottom: 12px;">Match schedule create karne ke liye panel open karein (Active subscription zaroori hai).</p>
                <button class="btn" onclick="openCreatorDashboard()">Open Creator Panel</button>
            </div>

            <div id="adminMainControlCard" class="card hidden" style="border-left: 6px solid var(--danger); background: #fdfefe;">
                <h3 style="color: var(--danger);">👑 Master Website Admin Control Center</h3>
                <p style="font-size: 0.95rem; color: #555; margin-bottom: 15px;">Yahan se aap saare matches, pending recharges, tickets aur plans ko manage kar sakte hain.</p>
                <div style="display: flex; gap: 12px; flex-wrap: wrap;">
                    <button class="btn btn-warning" style="flex: 1;" onclick="openRechargeRequestsModal()">📥 Verify Recharges (<span id="pendingCountBadge">0</span>)</button>
                    <button class="btn btn-danger" style="flex: 1;" onclick="openMasterAdminPanel()">⚙️ Manage Matches & Plans</button>
                </div>
            </div>

            <div class="card">
                <h3>🔍 6-Digit Code Verification</h3>
                <div class="flex-row">
                    <input type="text" id="verifyCodeInput" maxlength="6" placeholder="Enter 6-digit match code">
                    <button class="btn" onclick="verifyMatchCode()" style="height: 52px; margin-top: 8px;">Check Code</button>
                </div>
                <div id="verifyResult" style="margin-top: 12px;"></div>
            </div>

            <div class="tabs">
                <button class="tab-btn active" onclick="switchTab('international', event)">🌍 International</button>
                <button class="tab-btn" onclick="switchTab('apna', event)">👤 Apna Schedule</button>
                <button class="tab-btn" onclick="switchTab('activeTickets', event)">🎟️ Active Tickets & Store</button>
                <button class="tab-btn" onclick="switchTab('myPurchased', event)">📦 Purchased History</button>
            </div>

            <div id="internationalTabContent" class="tab-content card">
                <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 15px; flex-wrap: wrap; gap: 10px;">
                    <h2>International Matches</h2>
                    <button id="adminCreateMatchBtn" class="btn btn-success hidden" style="width: auto;" onclick="openInternationalMatchModal()">+ Create International Match</button>
                </div>
                <div id="internationalMatchesList" style="margin-top: 15px;"></div>
            </div>

            <div id="apnaTabContent" class="tab-content card hidden">
                <h2>Apna Schedule (User Created)</h2>
                <div id="apnaMatchesList" style="margin-top: 15px;"></div>
            </div>

            <div id="activeTicketsTabContent" class="tab-content card hidden">
                <h2>Active Ticket District & Store</h2>
                <div id="activeTicketsList" style="margin-top: 15px;"></div>
            </div>

            <div id="myPurchasedTabContent" class="tab-content card hidden">
                <h2>All Purchased Tickets History</h2>
                <div id="myPurchasedList" style="margin-top: 15px;"></div>
            </div>

        </div>
    </div>

    <!-- Modals -->
    <div id="creatorModal" class="modal hidden">
        <div class="modal-content">
            <span class="close-modal" onclick="closeCreatorModal()">&times;</span>
            <div id="subscriptionRequiredView">
                <h3 style="color: var(--danger);">📢 Subscription Required</h3>
                <p style="font-size:0.95rem; color:#555; margin-bottom:15px;">Apna schedule create karne ke liye pehle subscription plan active karein.</p>
            </div>
            <div id="creatorActionView" class="hidden">
                <h3 style="color: var(--success);">👤 Creator Panel (Schedule Only)</h3>
                <p style="font-size: 1rem; color: #333; margin-bottom: 15px; font-weight: bold;">✔ Aapke paas active subscription hai. Aap match schedule create kar sakte hain:</p>
                <button class="btn" onclick="openMatchModal()">🏏 Create Match Schedule Only</button>
            </div>
        </div>
    </div>

    <div id="matchModal" class="modal hidden">
        <div class="modal-content">
            <span class="close-modal" onclick="closeMatchModal()">&times;</span>
            <h2>🏏 Create Match Schedule</h2>
            
            <label>Series Type:</label>
            <select id="matchSeriesType" onchange="toggleSeriesInput('match')">
                <option value="existing">Existing Series (Auto-select)</option>
                <option value="new">New Series (Enter Name & Gap)</option>
            </select>

            <div id="matchExistingSeriesContainer">
                <label>Select Existing Series:</label>
                <select id="matchExistingSeriesSelect"></select>
            </div>

            <div id="matchNewSeriesContainer" class="hidden">
                <label>New Series Name:</label>
                <input type="text" id="matchSeriesName" placeholder="e.g., Local League 2026">
            </div>

            <div class="flex-row">
                <div><label>Team 1 Name:</label><input type="text" id="matchTeam1" placeholder="Team A"></div>
                <div><label>Team 2 Name:</label><input type="text" id="matchTeam2" placeholder="Team B"></div>
            </div>

            <div class="flex-row">
                <div><label>Match Format:</label><input type="text" id="matchFormat" placeholder="4TH T20I"></div>
                <div><label>Date & Time:</label><input type="text" id="matchDateTime" placeholder="WED, 17 DEC, 2026 | 7 PM"></div>
            </div>

            <label>Venue (Stadium Name):</label>
            <input type="text" id="matchVenue" placeholder="EKANA STADIUM, LUCKNOW">

            <label>Gate Open Time:</label>
            <input type="text" id="matchGateTime" placeholder="Gate Opens: 2 Hours Before">

            <div class="flex-row">
                <div><label>Ticket Price (₹):</label><input type="number" id="matchPrice" placeholder="200"></div>
                <div><label>Total Tickets Limit:</label><input type="number" id="matchLimit" placeholder="100"></div>
            </div>

            <label>6-Digit Security Code:</label>
            <input type="text" id="matchCode6" maxlength="6" placeholder="6 digit code">

            <label>Result / Winner Status:</label>
            <select id="matchResultStatus">
                <option value="Upcoming">Upcoming / Live</option>
                <option value="Team 1 Won">Team 1 Won (Double Payout)</option>
                <option value="Team 2 Won">Team 2 Won (Double Payout)</option>
                <option value="Draw / Abandoned">Draw / Refund</option>
            </select>

            <button class="btn btn-success" style="margin-top:10px;" onclick="saveMatchSchedule(false)">Save & Publish Match</button>
        </div>
    </div>

    <div id="internationalMatchModal" class="modal hidden">
        <div class="modal-content">
            <span class="close-modal" onclick="closeInternationalMatchModal()">&times;</span>
            <h2>🌍 Create International Match</h2>
            
            <label>Series Type:</label>
            <select id="intSeriesType" onchange="toggleSeriesInput('int')">
                <option value="existing">Existing Series (Auto-select)</option>
                <option value="new">New Series (Enter Name)</option>
            </select>

            <div id="intExistingSeriesContainer">
                <label>Select Existing Series:</label>
                <select id="intExistingSeriesSelect"></select>
            </div>

            <div id="intNewSeriesContainer" class="hidden">
                <label>New Series Name:</label>
                <input type="text" id="intSeriesName" placeholder="IND vs SA Series">
            </div>

            <div class="flex-row">
                <div><label>Team 1:</label><input type="text" id="intTeam1" placeholder="IND"></div>
                <div><label>Team 2:</label><input type="text" id="intTeam2" placeholder="SA"></div>
            </div>

            <div class="flex-row">
                <div><label>Match Format:</label><input type="text" id="intFormat" placeholder="4TH T20I"></div>
                <div><label>Date & Time:</label><input type="text" id="intDateTime" placeholder="WED, 17 DEC, 2026 | 7 PM"></div>
            </div>

            <label>Venue:</label>
            <input type="text" id="intVenue" placeholder="Stadium Name">

            <label>Gate Open Time:</label>
            <input type="text" id="intGateTime" placeholder="Gate Opens info">

            <div class="flex-row">
                <div><label>Price (₹):</label><input type="number" id="intPrice" placeholder="200"></div>
                <div><label>Limit:</label><input type="number" id="intLimit" placeholder="100"></div>
            </div>

            <label>6-Digit Security Code:</label>
            <input type="text" id="intCode6" maxlength="6" placeholder="6 digit code">

            <label>Result Status:</label>
            <select id="intResultStatus">
                <option value="Upcoming">Upcoming / Live</option>
                <option value="Team 1 Won">Team 1 Won (Double Payout)</option>
                <option value="Team 2 Won">Team 2 Won (Double Payout)</option>
                <option value="Draw / Abandoned">Draw / Refund</option>
            </select>

            <button class="btn btn-success" style="margin-top:10px;" onclick="saveMatchSchedule(true)">Publish International Match</button>
        </div>
    </div>

    <div id="rechargeModal" class="modal hidden">
        <div class="modal-content">
            <span class="close-modal" onclick="closeRechargeModal()">&times;</span>
            <h2>📥 Pending Recharge Requests</h2>
            <div id="pendingRechargesList" style="margin-top: 15px;"></div>
        </div>
    </div>

    <div id="masterAdminModal" class="modal hidden">
        <div class="modal-content" style="max-width: 750px;">
            <span class="close-modal" onclick="closeMasterAdminModal()">&times;</span>
            <h2>⚙️ Master Admin Panel</h2>
            
            <div class="tabs" style="margin-bottom:15px;">
                <button class="tab-btn active" onclick="switchAdminSubTab('matches', event)">Matches</button>
                <button class="tab-btn" onclick="switchAdminSubTab('tickets', event)">All Tickets</button>
                <button class="tab-btn" onclick="switchAdminSubTab('plans', event)">Subscriptions</button>
            </div>

            <div id="adminTabMatches" class="admin-sub-tab"><div id="adminAllMatchesList"></div></div>
            <div id="adminTabTickets" class="admin-sub-tab hidden"><div id="adminAllTicketsList"></div></div>
            <div id="adminTabPlans" class="admin-sub-tab hidden">
                <div id="adminPlansList" style="margin-bottom: 15px;"></div>
                <hr style="margin: 15px 0;">
                <h3>Add New Subscription Plan</h3>
                <label>Plan ID:</label><input type="text" id="newPlanId" placeholder="e.g., 30days_special">
                <label>Plan Name:</label><input type="text" id="newPlanName" placeholder="30 Days Monthly Pass">
                <div class="flex-row">
                    <div><label>Price (₹):</label><input type="number" id="newPlanPrice" placeholder="449"></div>
                    <div><label>Duration Days:</label><input type="number" id="newPlanDays" placeholder="30"></div>
                </div>
                <button class="btn btn-success" onclick="addNewSubscriptionPlan()">Add New Plan</button>
            </div>
        </div>
    </div>

    <div id="editSingleMatchModal" class="modal hidden">
        <div class="modal-content">
            <span class="close-modal" onclick="closeEditSingleMatchModal()">&times;</span>
            <h2>✏️ Edit Match & Winner Status</h2>
            <input type="hidden" id="editMatchId">

            <label>Series Name:</label><input type="text" id="editSeriesName">
            <div class="flex-row">
                <div><label>Team 1:</label><input type="text" id="editTeam1"></div>
                <div><label>Team 2:</label><input type="text" id="editTeam2"></div>
            </div>
            <div class="flex-row">
                <div><label>Format:</label><input type="text" id="editMatchFormat"></div>
                <div><label>Date & Time:</label><input type="text" id="editMatchDateTime"></div>
            </div>
            <label>Venue:</label><input type="text" id="editMatchVenue">
            <label>Gate Time:</label><input type="text" id="editMatchGateTime">
            <div class="flex-row">
                <div><label>Price (₹):</label><input type="number" id="editMatchPrice"></div>
                <div><label>Limit:</label><input type="number" id="editMatchLimit"></div>
            </div>
            <label>Result / Winner Status:</label>
            <select id="editResultStatus">
                <option value="Upcoming">Upcoming / Live</option>
                <option value="Team 1 Won">Team 1 Won (Double Payout)</option>
                <option value="Team 2 Won">Team 2 Won (Double Payout)</option>
                <option value="Draw / Abandoned">Draw / Refund</option>
            </select>
            <button class="btn btn-success" style="margin-top:10px;" onclick="saveEditedMatch()">Update Match Settings</button>
        </div>
    </div>

    <script>
        const DEFAULT_ADMIN = "9569981484";
        
        let db = JSON.parse(localStorage.getItem('cricket_pro_db')) || {
            users: {},
            matches: [],
            tickets: [],
            rechargeRequests: [],
            usedTransactions: [],
            settings: {
                adminNumber: DEFAULT_ADMIN,
                maxDevices: 6,
                plans: [
                    { id: '4hour', name: '4 Hour Pass', price: 99, durationHours: 4 },
                    { id: '1day', name: '1 Day Pass', price: 108, durationHours: 24 },
                    { id: '30days', name: '30 Days Monthly Plan', price: 449, durationDays: 30 }
                ]
            },
            deviceSessions: {}
        };

        db.settings.adminNumber = DEFAULT_ADMIN;
        db.settings.maxDevices = 6;

        let currentMobile = localStorage.getItem('cricket_pro_current_mobile') || null;
        let deviceId = localStorage.getItem('cricket_pro_device_id') || 'dev_' + Math.random().toString(36).substring(2,9);
        localStorage.setItem('cricket_pro_device_id', deviceId);

        let lastUsedSeries = { match: '', int: '' };

        function saveDB() {
            localStorage.setItem('cricket_pro_db', JSON.stringify(db));
        }

        window.onload = function() {
            if (!db.users[db.settings.adminNumber]) {
                db.users[db.settings.adminNumber] = { wallet: 0, subscription: null };
            }
            if (currentMobile && db.users[currentMobile]) {
                showDashboard();
            } else {
                currentMobile = null;
                showLogin();
            }
        };

        function showLogin() {
            document.getElementById('loginSection').classList.remove('hidden');
            document.getElementById('mainDashboard').classList.add('hidden');
            let infoEl = document.getElementById('deviceLimitInfo');
            if(infoEl) infoEl.innerText = `(Max ${db.settings.maxDevices} numbers allowed per device)`;
        }

        function showDashboard() {
            document.getElementById('loginSection').classList.add('hidden');
            document.getElementById('mainDashboard').classList.remove('hidden');
            
            let isAdmin = (currentMobile === db.settings.adminNumber);
            if (isAdmin) {
                document.getElementById('adminCreateMatchBtn').classList.remove('hidden');
                document.getElementById('adminMainControlCard').classList.remove('hidden');
            } else {
                document.getElementById('adminCreateMatchBtn').classList.add('hidden');
                document.getElementById('adminMainControlCard').classList.add('hidden');
            }

            updateHeader();
            renderSubscriptionStatusBox();
            renderSubscriptionPlansHub();
            renderMatches();
            renderActiveTickets();
            renderMyPurchasedTickets();
        }

        function handleLogin() {
            let mobile = document.getElementById('loginMobileInput').value.trim();
            if (!mobile || mobile.length < 10) { alert("Kripya sahi 10-digit mobile number enter karein!"); return; }

            if (!db.deviceSessions[deviceId]) db.deviceSessions[deviceId] = [];
            let activeNumbers = db.deviceSessions[deviceId];
            
            if (!activeNumbers.includes(mobile)) {
                if (activeNumbers.length >= db.settings.maxDevices) {
                    alert(`Is device par maximum ${db.settings.maxDevices} numbers hi allow hain!`);
                    return;
                }
                activeNumbers.push(mobile);
            }

            if (!db.users[mobile]) {
                let initialWallet = (mobile === db.settings.adminNumber) ? 0 : 200;
                db.users[mobile] = { wallet: initialWallet, subscription: null };
            }

            currentMobile = mobile;
            localStorage.setItem('cricket_pro_current_mobile', currentMobile);
            saveDB();
            showDashboard();
        }

        function logout() {
            currentMobile = null;
            localStorage.removeItem('cricket_pro_current_mobile');
            showLogin();
        }

        function updateHeader() {
            document.getElementById('displayNumber').innerText = currentMobile;
            let user = db.users[currentMobile];
            document.getElementById('displayWallet').innerText = user ? user.wallet : 0;
            
            if (currentMobile === db.settings.adminNumber) {
                let pending = (db.rechargeRequests || []).filter(r => r.status === 'Pending').length;
                let badge = document.getElementById('pendingCountBadge');
                if (badge) badge.innerText = pending;
            }
        }

        function submitRechargeRequest() {
            let txInput = document.getElementById('txFullInput').value.trim();
            if (!txInput || txInput.length < 6) { alert("Kripya valid Transaction ID / UTR enter karein!"); return; }

            if (!db.usedTransactions) db.usedTransactions = [];
            if (db.usedTransactions.includes(txInput)) { alert("Yeh Transaction ID pehle hi use ki ja chuki hai!"); return; }

            if (!db.rechargeRequests) db.rechargeRequests = [];
            db.rechargeRequests.push({ id: 'req_' + Date.now(), mobile: currentMobile, txId: txInput, status: 'Pending' });

            saveDB();
            document.getElementById('txFullInput').value = '';
            alert("Aapki recharge request bhej di gayi hai!");
        }

        function openRechargeRequestsModal() {
            if (currentMobile !== db.settings.adminNumber) return;
            let listDiv = document.getElementById('pendingRechargesList');
            let pending = (db.rechargeRequests || []).filter(r => r.status === 'Pending');

            if (pending.length === 0) {
                listDiv.innerHTML = '<p>Koi pending recharge request nahi hai.</p>';
            } else {
                let html = '';
                pending.forEach(req => {
                    html += `
                        <div class="match-card" style="border-left: 6px solid var(--accent); padding:15px; margin-bottom:12px;">
                            <p><strong>Mobile:</strong> ${req.mobile}</p>
                            <p><strong>Tx ID / UTR:</strong> ${req.txId}</p>
                            <div style="margin-top:10px; display:flex; gap:10px;">
                                <button class="btn btn-success" style="padding:8px 14px; font-size:0.9rem;" onclick="approveRecharge('${req.id}')">Approve & Send ₹210</button>
                                <button class="btn btn-danger" style="padding:8px 14px; font-size:0.9rem;" onclick="rejectRecharge('${req.id}')">Reject</button>
                            </div>
                        </div>
                    `;
                });
                listDiv.innerHTML = html;
            }
            document.getElementById('rechargeModal').classList.remove('hidden');
        }

        function closeRechargeModal() { document.getElementById('rechargeModal').classList.add('hidden'); }

        function approveRecharge(reqId) {
            let req = db.rechargeRequests.find(r => r.id === reqId);
            if (!req) return;

            if (!db.usedTransactions) db.usedTransactions = [];
            db.usedTransactions.push(req.txId);
            req.status = 'Approved';

            if (!db.users[req.mobile]) db.users[req.mobile] = { wallet: 0, subscription: null };
            db.users[req.mobile].wallet += 210;

            saveDB();
            updateHeader();
            openRechargeRequestsModal();
            alert("Request approve ho gayi aur ₹210 bhej diye gaye!");
        }

        function rejectRecharge(reqId) {
            db.rechargeRequests = db.rechargeRequests.filter(r => r.id !== reqId);
            saveDB();
            updateHeader();
            openRechargeRequestsModal();
            alert("Request reject kar di gayi.");
        }

        function checkUserHasActiveSub() {
            let isAdmin = (currentMobile === db.settings.adminNumber);
            if (isAdmin) return true;
            let user = db.users[currentMobile];
            if (user && user.subscription) {
                return new Date().getTime() < user.subscription.expiresAt;
            }
            return false;
        }

        function renderSubscriptionStatusBox() {
            let box = document.getElementById('activeSubStatusBox');
            let content = document.getElementById('subStatusContent');
            let user = db.users[currentMobile];
            let isAdmin = (currentMobile === db.settings.adminNumber);

            if (isAdmin) {
                box.classList.remove('hidden');
                content.innerHTML = `Role: Master Website Admin (Full Unlimited Access)`;
                return;
            }

            if (user && user.subscription && checkUserHasActiveSub()) {
                box.classList.remove('hidden');
                let sub = user.subscription;
                let now = new Date().getTime();
                let diffMs = sub.expiresAt - now;
                let diffHrs = Math.floor(diffMs / (1000 * 60 * 60));
                let diffDays = Math.floor(diffHrs / 24);
                
                let timeLeftText = diffDays > 0 ? `${diffDays} Days Left (~${diffHrs} Hours)` : `${diffHrs} Hours Left`;
                content.innerHTML = `Active Plan: <b>${sub.planName}</b> <br>⏱️ Validity Status: <b>${timeLeftText}</b>`;
            } else {
                box.classList.add('hidden');
            }
        }

        function renderSubscriptionPlansHub() {
            let listHTML = '';
            db.settings.plans.forEach((plan, index) => {
                let checked = index === 0 ? 'checked' : '';
                let durationDesc = plan.durationDays ? `${plan.durationDays} Days Pass` : `${plan.durationHours} Hours Pass`;
                listHTML += `
                    <label style="background:#fff; padding:12px 15px; border-radius:8px; border:2px solid var(--border); display:flex; align-items:center; gap:12px; cursor:pointer;">
                        <input type="radio" name="subPlanHub" value="${plan.id}" ${checked} style="width:auto; margin:0;">
                        <div style="flex:1;">
                            <strong>${plan.name}</strong> (${durationDesc})
                        </div>
                        <span style="font-weight:bold; color:var(--primary); font-size:1.1rem;">₹${plan.price}</span>
                    </label>
                `;
            });
            document.getElementById('subPlansList').innerHTML = listHTML;
        }

        function buySelectedSubscriptionFromHub() {
            let selectedRadio = document.querySelector('input[name="subPlanHub"]:checked');
            if (!selectedRadio) { alert("Kripya pehle koi plan select karein!"); return; }
            let planObj = db.settings.plans.find(p => p.id === selectedRadio.value);
            if (!planObj) return;

            let user = db.users[currentMobile];
            if (user.wallet < planObj.price) { alert("Wallet me balance kam hai! Pehle recharge request bhej kar balance add karein."); return; }

            user.wallet -= planObj.price;
            let adminMob = db.settings.adminNumber;
            if (!db.users[adminMob]) db.users[adminMob] = { wallet: 0, subscription: null };
            db.users[adminMob].wallet += planObj.price;

            let now = new Date().getTime();
            let expiresAt = now + (30 * 24 * 3600 * 1000);
            if (planObj.durationHours) expiresAt = now + (planObj.durationHours * 3600 * 1000);
            if (planObj.durationDays) expiresAt = now + (planObj.durationDays * 24 * 3600 * 1000);

            user.subscription = { planId: planObj.id, planName: planObj.name, expiresAt: expiresAt };

            saveDB();
            updateHeader();
            renderSubscriptionStatusBox();
            alert("Subscription successfully buy ho gaya!");
        }

        function openCreatorDashboard() {
            let modal = document.getElementById('creatorModal');
            let reqView = document.getElementById('subscriptionRequiredView');
            let actView = document.getElementById('creatorActionView');

            if (checkUserHasActiveSub()) {
                reqView.classList.add('hidden');
                actView.classList.remove('hidden');
            } else {
                reqView.classList.remove('hidden');
                actView.classList.add('hidden');
            }
            modal.classList.remove('hidden');
        }

        function closeCreatorModal() { document.getElementById('creatorModal').classList.add('hidden'); }
        
        function openMatchModal() { 
            closeCreatorModal(); 
            populateExistingSeriesDropdown('match');
            toggleSeriesInput('match');
            document.getElementById('matchModal').classList.remove('hidden'); 
        }
        function closeMatchModal() { document.getElementById('matchModal').classList.add('hidden'); }
        
        function openInternationalMatchModal() { 
            populateExistingSeriesDropdown('int');
            toggleSeriesInput('int');
            document.getElementById('internationalMatchModal').classList.remove('hidden'); 
        }
        function closeInternationalMatchModal() { document.getElementById('internationalMatchModal').classList.add('hidden'); }

        function toggleSeriesInput(prefix) {
            let type = document.getElementById(`${prefix}SeriesType`).value;
            let existingContainer = document.getElementById(`${prefix}ExistingSeriesContainer`);
            let newContainer = document.getElementById(`${prefix}NewSeriesContainer`);

            if (type === 'existing') {
                existingContainer.classList.remove('hidden');
                newContainer.classList.add('hidden');
            } else {
                existingContainer.classList.add('hidden');
                newContainer.classList.remove('hidden');
            }
        }

        function populateExistingSeriesDropdown(prefix) {
            let selectEl = document.getElementById(`${prefix}ExistingSeriesSelect`);
            let seriesList = [];
            db.matches.forEach(m => {
                if (m.seriesName && !seriesList.includes(m.seriesName)) {
                    seriesList.push(m.seriesName);
                }
            });

            if (seriesList.length === 0) {
                selectEl.innerHTML = '<option value="">Koi existing series nahi hai (New select karein)</option>';
                document.getElementById(`${prefix}SeriesType`).value = 'new';
                toggleSeriesInput(prefix);
            } else {
                let html = '';
                seriesList.forEach(s => {
                    html += `<option value="${s}">${s}</option>`;
                });
                selectEl.innerHTML = html;
                
                if (lastUsedSeries[prefix] && seriesList.includes(lastUsedSeries[prefix])) {
                    selectEl.value = lastUsedSeries[prefix];
                }
            }
        }

        function saveMatchSchedule(isInternational) {
            let prefix = isInternational ? 'int' : 'match';
            let seriesType = document.getElementById(`${prefix}SeriesType`).value;
            let seriesName = '';

            if (seriesType === 'existing') {
                seriesName = document.getElementById(`${prefix}ExistingSeriesSelect`).value;
                if (!seriesName) {
                    alert("Kripya existing series select karein ya 'New Series' choose karein!");
                    return;
                }
            } else {
                seriesName = document.getElementById(`${prefix}SeriesName`).value.trim();
                if (!seriesName) {
                    alert("Kripya New Series ka naam enter karein!");
                    return;
                }
            }

            lastUsedSeries[prefix] = seriesName;

            let matchObj = {
                id: 'match_' + Date.now(),
                creator: currentMobile,
                isInternational: isInternational,
                seriesType: seriesType,
                seriesName: seriesName,
                team1: document.getElementById(`${prefix}Team1`).value.trim(),
                team2: document.getElementById(`${prefix}Team2`).value.trim(),
                matchFormat: document.getElementById(`${prefix}Format`).value.trim() || "T20I",
                dateTime: document.getElementById(`${prefix}DateTime`).value.trim() || "WED, 17 DEC, 2026 | 7 PM",
                venue: document.getElementById(`${prefix}Venue`).value.trim() || "STADIUM, LUCKNOW",
                gateTime: document.getElementById(`${prefix}GateTime`).value.trim() || "Gate Opens: 2 Hours Before",
                price: Number(document.getElementById(`${prefix}Price`).value) || 0,
                limit: Number(document.getElementById(`${prefix}Limit`).value) || 0,
                soldCount: 0,
                code6: document.getElementById(`${prefix}Code6`).value.trim(),
                resultStatus: document.getElementById(`${prefix}ResultStatus`).value
            };

            if (!matchObj.seriesName || !matchObj.team1 || !matchObj.team2 || matchObj.code6.length !== 6) {
                alert("Sabhi zaroori fields bharein (6 digit code zarouri hai)!");
                return;
            }

            db.matches.push(matchObj);
            saveDB();
            if (isInternational) closeInternationalMatchModal();
            else closeMatchModal();
            renderMatches();
            renderActiveTickets();
            alert("Match successfully publish ho gaya!");
        }

        function verifyMatchCode() {
            let code = document.getElementById('verifyCodeInput').value.trim();
            let resDiv = document.getElementById('verifyResult');
            let match = db.matches.find(m => m.code6 === code);

            if (!match) {
                resDiv.innerHTML = `<div class="alert-box alert-error">Invalid 6-Digit Code!</div>`;
                return;
            }

            resDiv.innerHTML = `
                <div class="alert-box alert-success">
                    <strong>Series:</strong> ${match.seriesName}<br>
                    <strong>Match:</strong> ${match.team1} vs ${match.team2} (${match.matchFormat})<br>
                    <strong>Venue:</strong> ${match.venue}<br>
                    <strong>Date:</strong> ${match.dateTime}<br>
                    <strong>Gate Open:</strong> ${match.gateTime || 'N/A'}
                </div>
            `;
        }

        function renderMatches() {
            let intList = document.getElementById('internationalMatchesList');
            let apnaList = document.getElementById('apnaMatchesList');
            let intHTML = '', apnaHTML = '';

            // Group matches by Series Name to avoid repeating the series title bar for every match
            let groupMatches = (matchesArr) => {
                let grouped = {};
                matchesArr.forEach(m => {
                    let sName = m.seriesName || 'Other Matches';
                    if (!grouped[sName]) grouped[sName] = [];
                    grouped[sName].push(m);
                });
                return grouped;
            };

            let intGrouped = groupMatches(db.matches.filter(m => m.isInternational));
            let apnaGrouped = groupMatches(db.matches.filter(m => !m.isInternational));

            let buildGroupHTML = (groupedObj) => {
                let finalHTML = '';
                for (let sName in groupedObj) {
                    finalHTML += `
                        <div class="match-card" style="background:#f8fafc; border-left: 6px solid var(--primary); margin-bottom: 25px;">
                            <div class="series-title-bar" style="margin-bottom: 12px;">
                                <span>🏆 Series: ${sName}</span>
                            </div>
                    `;
                    groupedObj[sName].forEach(match => {
                        checkAndSettleMatchResults(match);
                        finalHTML += `
                            <div style="background:#fff; border: 1px solid var(--border); border-radius: 10px; padding: 15px; margin-bottom: 12px;">
                                <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 8px;">
                                    <span style="font-size:0.85rem; background:#e2e8f0; padding:2px 8px; border-radius:4px; color:#333;">Code: ${match.code6}</span>
                                </div>
                                <div class="match-row">
                                    <div class="team-box">🏏 ${match.team1}</div>
                                    <div class="vs-text">
                                        <span>VS</span>
                                        <span class="match-format-green">${match.matchFormat || 'T20I'}</span>
                                    </div>
                                    <div class="team-box">${match.team2} 🏏</div>
                                </div>
                                <div style="font-size:0.95rem; color:#444; margin-bottom:6px;">📍 <strong>Venue:</strong> ${match.venue || 'Stadium'}</div>
                                <div style="font-size:0.95rem; color:#444; margin-bottom:10px;">📅 <strong>Date/Time:</strong> ${match.dateTime || 'TBD'}</div>
                                <div style="margin-top: 12px; display:flex; justify-content:space-between; align-items:center; border-top: 1px dashed var(--border); padding-top: 10px;">
                                    <span style="font-size:0.95rem; font-weight:bold; color:var(--success);">Result Status: ${match.resultStatus}</span>
                                    <div>
                                        ${(currentMobile === db.settings.adminNumber || currentMobile === match.creator) ? 
                                            `<button class="btn btn-danger" style="padding:6px 14px; font-size:0.9rem; width:auto;" onclick="deleteMatch('${match.id}')">Delete</button>` : ''}
                                    </div>
                                </div>
                            </div>
                        `;
                    });
                    finalHTML += `</div>`;
                }
                return finalHTML;
            };

            intList.innerHTML = buildGroupHTML(intGrouped) || '<p>Koi International match nahi hai.</p>';
            apnaList.innerHTML = buildGroupHTML(apnaGrouped) || '<p>Koi apna schedule create nahi kiya gaya hai.</p>';
        }

        function buyTicket(matchId) {
            let match = db.matches.find(m => m.id === matchId);
            if (!match || !match.price || match.price <= 0) { alert("Ticket price available nahi hai!"); return; }
            if (match.soldCount >= match.limit && match.limit > 0) { alert("Sold out!"); return; }

            let user = db.users[currentMobile];
            if (user.wallet < match.price) { alert("Wallet balance kam hai!"); return; }

            user.wallet -= match.price;
            let recipientMob = match.creator || db.settings.adminNumber;
            if (!db.users[recipientMob]) db.users[recipientMob] = { wallet: 0, subscription: null };
            db.users[recipientMob].wallet += match.price;

            match.soldCount += 1;
            db.tickets.push({
                id: 'tkt_' + Date.now(),
                matchId: match.id,
                mobile: currentMobile,
                pricePaid: match.price,
                teamPicked: null,
                sattaAmount: 0,
                status: 'Active'
            });

            saveDB();
            updateHeader();
            renderMatches();
            renderActiveTickets();
            renderMyPurchasedTickets();
            alert("Ticket successfully buy ho gayi! Ab aap niche 'Active Ticket District' se satta laga sakte hain.");
        }

        function renderActiveTickets() {
            let listDiv = document.getElementById('activeTicketsList');
            let userActiveTickets = db.tickets.filter(t => t.mobile === currentMobile && t.status === 'Active');

            let storeHTML = '<h3>🛍️ Available Matches Store (Buy Tickets)</h3>';
            db.matches.forEach(m => {
                let hasPrice = (m.price && m.price > 0);
                let buttonHTML = hasPrice 
                    ? `<button class="btn btn-success" style="padding:10px 18px; font-size:0.95rem; width:auto;" onclick="buyTicket('${m.id}')">Buy Ticket - ₹${m.price}</button>`
                    : `<span style="font-size:0.9rem; color:var(--danger); font-weight:bold;">Price Not Fixed Yet</span>`;

                storeHTML += `
                    <div style="background:#fff; padding:18px; margin-bottom:14px; border-radius:10px; border:2px solid var(--border); display:flex; justify-content:space-between; align-items:center; flex-wrap:wrap; gap:12px;">
                        <div>
                            <strong style="font-size:1.1rem; color:var(--primary);">${m.seriesName}</strong><br>
                            <span style="font-size:1.05rem; font-weight:bold;">${m.team1} vs ${m.team2}</span><br>
                            <small style="color:#666; font-size:0.9rem;">${m.matchFormat} | 📍 ${m.venue}</small>
                        </div>
                        <div>${buttonHTML}</div>
                    </div>
                `;
            });

            let ticketsHTML = '<h3 style="margin-top:25px;">🎟️ Your Active Tickets & Satta Zone</h3>';
            if (userActiveTickets.length === 0) {
                ticketsHTML += '<p style="color:#666; margin-bottom:15px;">Aapne abhi koi ticket buy nahi ki hai.</p>';
            } else {
                userActiveTickets.forEach(tkt => {
                    let match = db.matches.find(m => m.id === tkt.matchId);
                    if (!match) return;

                    ticketsHTML += `
                        <div class="physical-ticket">
                            <div class="ticket-header">
                                <span>🎫 ${match.seriesName || 'Series Ticket'}</span>
                                <span class="ticket-format-badge">${match.matchFormat || 'T20I'}</span>
                            </div>
                            <div class="ticket-teams-title">${match.team1} <span style="font-size:1.3rem; color:#ffeb3b;">VS</span> ${match.team2}</div>
                            <div class="ticket-venue">📍 ${match.venue || 'Stadium'}</div>
                            <div class="ticket-gate">🚪 ${match.gateTime || 'Gate Opens Info'}</div>
                            <div class="ticket-datetime">📅 ${match.dateTime || 'TBD'}</div>
                            
                            <div class="ticket-footer">
                                <span>ID: ${tkt.id}</span>
                                <span style="font-size:1.05rem; color:var(--primary);">Paid: ₹${tkt.pricePaid}</span>
                            </div>

                            <div style="margin-top:16px; background:rgba(255,255,255,0.95); color:#333; padding:16px; border-radius:10px;">
                                <h4 style="margin-bottom:10px; color:#1e3c72; font-size:1.1rem;">🎲 Satta & Bet Zone</h4>
                                ${tkt.teamPicked ? 
                                    `<p style="font-size:1rem;">Chuni gayi team: <b>${tkt.teamPicked}</b> | Lagaye gaye ₹: <b>${tkt.sattaAmount}</b></p>` :
                                    `<label>Konsi team jeete gi?</label>
                                    <select id="sattaTeam_${tkt.id}"><option value="${match.team1}">${match.team1}</option><option value="${match.team2}">${match.team2}</option></select>
                                    <label>Bet Amount (₹):</label>
                                    <input type="number" id="sattaAmt_${tkt.id}" placeholder="Enter amount">
                                    <button class="btn btn-warning" onclick="placeSatta('${tkt.id}')">Confirm Satta</button>`
                                }
                            </div>
                        </div>
                    `;
                });
            }

            listDiv.innerHTML = storeHTML + '<hr style="margin:25px 0; border:0; border-top:2px solid #ddd;">' + ticketsHTML;
        }

        function renderMyPurchasedTickets() {
            let listDiv = document.getElementById('myPurchasedList');
            let userTickets = db.tickets.filter(t => t.mobile === currentMobile);

            if (userTickets.length === 0) {
                listDiv.innerHTML = '<p>Koi ticket history nahi hai.</p>';
                return;
            }

            let html = '';
            userTickets.forEach(tkt => {
                let match = db.matches.find(m => m.id === tkt.matchId);
                let matchName = match ? `${match.team1} vs ${match.team2} (${match.matchFormat})` : 'Expired Match';

                html += `
                    <div class="physical-ticket" style="opacity: 0.95;">
                        <div class="ticket-header">
                            <span>🎫 History Ticket</span>
                            <span>Status: ${tkt.status}</span>
                        </div>
                        <div class="ticket-teams-title" style="font-size:1.5rem;">${matchName}</div>
                        <div class="ticket-venue">📍 ${match ? match.venue : ''}</div>
                        <div class="ticket-footer">
                            <span>ID: ${tkt.id}</span>
                            <span>Paid: ₹${tkt.pricePaid}</span>
                        </div>
                    </div>
                `;
            });
            listDiv.innerHTML = html;
        }

        function placeSatta(tktId) {
            let tkt = db.tickets.find(t => t.id === tktId);
            let match = db.matches.find(m => m.id === tkt.matchId);
            let team = document.getElementById(`sattaTeam_${tktId}`).value;
            let amt = Number(document.getElementById(`sattaAmt_${tktId}`).value);

            let user = db.users[currentMobile];
            if (amt <= 0 || user.wallet < amt) { alert("Wallet balance kam hai!"); return; }

            user.wallet -= amt;
            let recipientMob = match.creator || db.settings.adminNumber;
            if (!db.users[recipientMob]) db.users[recipientMob] = { wallet: 0, subscription: null };
            db.users[recipientMob].wallet += amt;

            tkt.teamPicked = team;
            tkt.sattaAmount = amt;
            saveDB();
            updateHeader();
            renderActiveTickets();
            renderMyPurchasedTickets();
            alert("Satta successfully lag gaya!");
        }

        function checkAndSettleMatchResults(match) {
            if (match.resultStatus === 'Upcoming') return;

            db.tickets.forEach(tkt => {
                if (tkt.matchId === match.id && tkt.status === 'Active' && tkt.teamPicked) {
                    let user = db.users[tkt.mobile];
                    let recipientMob = match.creator || db.settings.adminNumber;

                    if (match.resultStatus.includes('Won')) {
                        let winnerTeam = match.resultStatus.includes('Team 1') ? match.team1 : match.team2;
                        if (tkt.teamPicked === winnerTeam) {
                            let winAmt = tkt.sattaAmount * 2;
                            let adminDeduction = tkt.sattaAmount * 0.10; 
                            if (db.users[recipientMob]) {
                                db.users[recipientMob].wallet -= adminDeduction;
                            }
                            if (user) user.wallet += winAmt;
                            tkt.status = 'Settled (Won)';
                        } else {
                            tkt.status = 'Settled (Lost)';
                        }
                    } else if (match.resultStatus === 'Draw / Abandoned') {
                        if (user) user.wallet += tkt.sattaAmount;
                        tkt.status = 'Refunded';
                    }
                }
            });
            saveDB();
        }

        function openMasterAdminPanel() {
            if (currentMobile !== db.settings.adminNumber) return;
            renderAdminAllMatches();
            renderAdminAllTickets();
            renderAdminPlansList();
            document.getElementById('masterAdminModal').classList.remove('hidden');
        }

        function closeMasterAdminModal() { document.getElementById('masterAdminModal').classList.add('hidden'); }

        function switchAdminSubTab(tabName, evt) {
            document.querySelectorAll('.admin-sub-tab').forEach(el => el.classList.add('hidden'));
            if (tabName === 'matches') document.getElementById('adminTabMatches').classList.remove('hidden');
            if (tabName === 'tickets') document.getElementById('adminTabTickets').classList.remove('hidden');
            if (tabName === 'plans') document.getElementById('adminTabPlans').classList.remove('hidden');
            
            if(evt && evt.target) {
                let parent = evt.target.parentElement;
                parent.querySelectorAll('.tab-btn').forEach(el => el.classList.remove('active'));
                evt.target.classList.add('active');
            }
        }

        function renderAdminAllMatches() {
            let container = document.getElementById('adminAllMatchesList');
            let html = '';
            db.matches.forEach(match => {
                html += `
                    <div class="match-card">
                        <p><strong>${match.seriesName}</strong> (${match.team1} vs ${match.team2}) - ₹${match.price}</p>
                        <div style="margin-top:10px; display:flex; gap:10px;">
                            <button class="btn btn-warning" style="padding:8px 14px; font-size:0.9rem; width:auto;" onclick="openEditMatchModal('${match.id}')">✏️ Edit Details & Winner</button>
                            <button class="btn btn-danger" style="padding:8px 14px; font-size:0.9rem; width:auto;" onclick="adminDeleteMatch('${match.id}')">Delete</button>
                        </div>
                    </div>
                `;
            });
            container.innerHTML = html || '<p>Koi match nahi hai.</p>';
        }

        function openEditMatchModal(matchId) {
            let match = db.matches.find(m => m.id === matchId);
            if (!match) return;

            document.getElementById('editMatchId').value = match.id;
            document.getElementById('editSeriesName').value = match.seriesName;
            document.getElementById('editTeam1').value = match.team1;
            document.getElementById('editTeam2').value = match.team2;
            document.getElementById('editMatchFormat').value = match.matchFormat || 'T20I';
            document.getElementById('editMatchDateTime').value = match.dateTime || '';
            document.getElementById('editMatchVenue').value = match.venue || '';
            document.getElementById('editMatchGateTime').value = match.gateTime || '';
            document.getElementById('editMatchPrice').value = match.price;
            document.getElementById('editMatchLimit').value = match.limit;
            document.getElementById('editResultStatus').value = match.resultStatus;

            document.getElementById('editSingleMatchModal').classList.remove('hidden');
        }

        function closeEditSingleMatchModal() { document.getElementById('editSingleMatchModal').classList.add('hidden'); }

        function saveEditedMatch() {
            let id = document.getElementById('editMatchId').value;
            let match = db.matches.find(m => m.id === id);
            if (!match) return;

            match.seriesName = document.getElementById('editSeriesName').value.trim();
            match.team1 = document.getElementById('editTeam1').value.trim();
            match.team2 = document.getElementById('editTeam2').value.trim();
            match.matchFormat = document.getElementById('editMatchFormat').value.trim();
            match.dateTime = document.getElementById('editMatchDateTime').value.trim();
            match.venue = document.getElementById('editMatchVenue').value.trim();
            match.gateTime = document.getElementById('editMatchGateTime').value.trim();
            match.price = Number(document.getElementById('editMatchPrice').value);
            match.limit = Number(document.getElementById('editMatchLimit').value);
            match.resultStatus = document.getElementById('editResultStatus').value;

            checkAndSettleMatchResults(match);
            saveDB();
            closeEditSingleMatchModal();
            renderAdminAllMatches();
            renderMatches();
            renderActiveTickets();
            alert("Match updated successfully!");
        }

        function adminDeleteMatch(matchId) {
            if (confirm("Delete karna chahte hain?")) {
                db.matches = db.matches.filter(m => m.id !== matchId);
                saveDB();
                renderAdminAllMatches();
                renderMatches();
                renderActiveTickets();
            }
        }

        function renderAdminAllTickets() {
            let container = document.getElementById('adminAllTicketsList');
            let html = '';
            db.tickets.forEach(tkt => {
                html += `<div class="match-card"><p><strong>Ticket ID:</strong> ${tkt.id} | User: ${tkt.mobile} | Status: ${tkt.status}</p></div>`;
            });
            container.innerHTML = html || '<p>Koi ticket nahi hai.</p>';
        }

        function renderAdminPlansList() {
            let container = document.getElementById('adminPlansList');
            let html = '';
            db.settings.plans.forEach(plan => {
                html += `
                    <div class="match-card" style="padding:12px; margin-bottom:10px;">
                        <p><strong>${plan.name}</strong> - ₹${plan.price}</p>
                        <button class="btn btn-danger" style="padding:6px 12px; font-size:0.85rem; margin-top:8px; width:auto;" onclick="deletePlan('${plan.id}')">Delete Plan</button>
                    </div>
                `;
            });
            container.innerHTML = html;
        }

        function addNewSubscriptionPlan() {
            let id = document.getElementById('newPlanId').value.trim();
            let name = document.getElementById('newPlanName').value.trim();
            let price = Number(document.getElementById('newPlanPrice').value);
            let days = Number(document.getElementById('newPlanDays').value);

            if (!id || !name || !price) { alert("Saari details bharein!"); return; }

            db.settings.plans.push({ id: id, name: name, price: price, durationDays: days || 30 });
            saveDB();
            renderSubscriptionPlansHub();
            renderAdminPlansList();
            alert("Naya subscription plan successfully add ho gaya!");
        }

        function deletePlan(planId) {
            db.settings.plans = db.settings.plans.filter(p => p.id !== planId);
            saveDB();
            renderSubscriptionPlansHub();
            renderAdminPlansList();
            alert("Plan delete ho gaya.");
        }

        function deleteMatch(matchId) {
            if (confirm("Delete karna chahte hain?")) {
                db.matches = db.matches.filter(m => m.id !== matchId);
                saveDB();
                renderMatches();
                renderActiveTickets();
            }
        }

        function switchTab(tabName, evt) {
            document.querySelectorAll('.tab-content').forEach(el => el.classList.add('hidden'));
            document.querySelectorAll('.tab-btn').forEach(el => el.classList.remove('active'));

            if (tabName === 'international') document.getElementById('internationalTabContent').classList.remove('hidden');
            else if (tabName === 'apna') document.getElementById('apnaTabContent').classList.remove('hidden');
            else if (tabName === 'activeTickets') {
                document.getElementById('activeTicketsTabContent').classList.remove('hidden');
                renderActiveTickets();
            }
            else if (tabName === 'myPurchased') document.getElementById('myPurchasedTabContent').classList.remove('hidden');
            
            if(evt && evt.target) evt.target.classList.add('active');
        }
    </script>
</body>
</html>
