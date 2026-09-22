<!DOCTYPE html>
<html lang="sw">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NJUNJU ELECTRONICS - Advanced Cloud POS & ERP v7.0</title>
    <style>
        :root {
            --bg-primary: #0f172a;
            --bg-card: #1e293b;
            --accent-blue: #2563eb;
            --accent-hover: #1d4ed8;
            --text-main: #f8fafc;
            --text-muted: #94a3b8;
            --border-color: #334155;
            --success-color: #10b981;
            --danger-color: #ef4444;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--bg-primary);
            color: var(--text-main);
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        /* Auth Screen */
        .auth-wrapper {
            display: flex;
            width: 100%;
            max-width: 950px;
            min-height: 550px;
            background: var(--bg-card);
            border-radius: 16px;
            overflow: hidden;
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.5);
            border: 1px solid var(--border-color);
            margin: 20px;
        }

        .brand-panel {
            flex: 1;
            background: linear-gradient(135deg, #1e293b 0%, #0f172a 100%);
            padding: 40px;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            border-right: 1px solid var(--border-color);
        }

        .brand-title {
            font-size: 2rem;
            font-weight: 800;
            color: #f59e0b;
            letter-spacing: 0.5px;
        }

        .brand-tagline {
            font-size: 0.95rem;
            color: var(--text-muted);
            margin-top: 6px;
            font-style: italic;
        }

        .info-box {
            background: rgba(255, 255, 255, 0.03);
            border-left: 4px solid #f59e0b;
            padding: 16px;
            border-radius: 4px;
            margin-top: 20px;
        }

        .info-box h4 {
            color: #f59e0b;
            font-size: 0.85rem;
            text-transform: uppercase;
            margin-bottom: 6px;
        }

        .info-box p {
            font-size: 0.9rem;
            color: var(--text-main);
            line-height: 1.4;
        }

        .quote-box {
            background: rgba(245, 158, 11, 0.1);
            border: 1px solid rgba(245, 158, 11, 0.2);
            padding: 14px;
            border-radius: 8px;
            font-size: 0.85rem;
            color: #fbbf24;
        }

        .form-panel {
            flex: 1;
            padding: 50px 40px;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }

        .form-header {
            margin-bottom: 30px;
        }

        .form-header h2 {
            font-size: 1.6rem;
            font-weight: 700;
        }

        .form-header p {
            font-size: 0.875rem;
            color: var(--text-muted);
            margin-top: 4px;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            font-size: 0.85rem;
            color: var(--text-muted);
            margin-bottom: 8px;
        }

        .form-group input, .form-group select {
            width: 100%;
            padding: 12px 16px;
            background: #0f172a;
            border: 1px solid var(--border-color);
            border-radius: 8px;
            color: var(--text-main);
            font-size: 0.95rem;
            outline: none;
            transition: border-color 0.2s;
        }

        .form-group input:focus {
            border-color: var(--accent-blue);
        }

        .btn-submit {
            width: 100%;
            padding: 14px;
            background: var(--accent-blue);
            color: white;
            border: none;
            border-radius: 8px;
            font-weight: 600;
            font-size: 0.95rem;
            cursor: pointer;
            transition: background 0.2s;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
        }

        .btn-submit:hover {
            background: var(--accent-hover);
        }

        /* Dashboard UI (Hidden by Default) */
        .dashboard {
            display: none;
            width: 100vw;
            height: 100vh;
            background: var(--bg-primary);
            flex-direction: column;
        }

        .nav-bar {
            height: 60px;
            background: var(--bg-card);
            border-bottom: 1px solid var(--border-color);
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 0 24px;
        }

        .content-area {
            flex: 1;
            padding: 24px;
            overflow-y: auto;
        }

        .card-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
            gap: 20px;
            margin-bottom: 24px;
        }

        .stat-card {
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            padding: 20px;
            border-radius: 12px;
        }

        .stat-card h3 {
            font-size: 0.85rem;
            color: var(--text-muted);
            margin-bottom: 8px;
        }

        .stat-card p {
            font-size: 1.5rem;
            font-weight: 700;
        }

        @media (max-width: 768px) {
            .auth-wrapper {
                flex-direction: column;
            }
            .brand-panel {
                border-right: none;
                border-bottom: 1px solid var(--border-color);
            }
        }
    </style>
</head>
<body>

    <!-- Authentication Screen -->
    <div class="auth-wrapper" id="auth-screen">
        <div class="brand-panel">
            <div>
                <div class="brand-title">NJUNJU ELECTRONICS</div>
                <div class="brand-tagline">"We Lift Your Smartlife"</div>
                
                <div class="info-box">
                    <h4>🎯 DIRA YETU</h4>
                    <p>Kuwa chapa inayoongoza na kuaminika zaidi Afrika Mashariki.</p>
                </div>
                
                <div class="info-box">
                    <h4>🚀 DHANA YETU</h4>
                    <p>Kuinua maisha ya kidijitali ya kila mteja kupitia bidhaa halisi.</p>
                </div>
            </div>

            <div class="quote-box">
                📌 Nidhamu kwenye kila namba ndio nguzo ya leo.
            </div>
        </div>

        <div class="form-panel">
            <div class="form-header">
                <h2>Ingia Kwenye Mfumo</h2>
                <p>Weka akaunti yako ili kufungua v7.0 Salama.</p>
            </div>

            <form id="login-form" onsubmit="handleAuth(event)">
                <div class="form-group">
                    <label for="username">Username</label>
                    <input type="text" id="username" placeholder="Mfn: admin au staff" required autocomplete="username">
                </div>

                <div class="form-group">
                    <label for="password">Password</label>
                    <input type="password" id="password" placeholder="••••••••" required autocomplete="current-password">
                </div>

                <button type="submit" class="btn-submit">
                    🔓 Fungua Mfumo Salama
                </button>
            </form>
        </div>
    </div>

    <!-- Main System Dashboard -->
    <div class="dashboard" id="dashboard-screen">
        <div class="nav-bar">
            <h2 style="color: #f59e0b; font-size: 1.2rem;">NJUNJU ERP v7.0</h2>
            <div>
                <span id="user-display" style="margin-right: 16px; color: var(--text-muted);"></span>
                <button onclick="logout()" style="background: var(--danger-color); border:none; padding: 8px 16px; color: white; border-radius: 6px; cursor: pointer;">Toka</button>
            </div>
        </div>

        <div class="content-area">
            <div class="card-grid">
                <div class="stat-card">
                    <h3>MAUZO YA LEO</h3>
                    <p id="sales-stat">TSH 0</p>
                </div>
                <div class="stat-card">
                    <h3>BIDHAA ZILIZOPO</h3>
                    <p>142</p>
                </div>
                <div class="stat-card">
                    <h3>MAOMBI VIPO</h3>
                    <p>5</p>
                </div>
            </div>

            <div style="background: var(--bg-card); border: 1px solid var(--border-color); padding: 24px; border-radius: 12px;">
                <h3>Karibu Kwenye Mfumo wa Njunju Electronics</h3>
                <p style="color: var(--text-muted); margin-top: 8px;">Mfumo uko tayari kwa ajili ya usimamizi wa mauzo na stoki.</p>
            </div>
        </div>
    </div>

    <script>
        // System Configured Accounts (In production, replace with secure backend API authentication)
        const SYSTEM_ACCOUNTS = {
            'admin': 'Admin2026!',
            'staff': 'Staff2026!'
        };

        function handleAuth(event) {
            event.preventDefault();
            
            const usernameInput = document.getElementById('username').value.trim();
            const passwordInput = document.getElementById('password').value.trim();

            if (SYSTEM_ACCOUNTS[usernameInput] && SYSTEM_ACCOUNTS[usernameInput] === passwordInput) {
                sessionStorage.setItem('authenticated_user', usernameInput);
                showDashboard(usernameInput);
            } else {
                alert('Nenosiri au Jina la Mtumiaji si sahihi!');
            }
        }

        function showDashboard(username) {
            document.getElementById('auth-screen').style.display = 'none';
            document.getElementById('dashboard-screen').style.display = 'flex';
            document.getElementById('user-display').innerText = `Mtumiaji: ${username.toUpperCase()}`;
        }

        function logout() {
            sessionStorage.removeItem('authenticated_user');
            document.getElementById('dashboard-screen').style.display = 'none';
            document.getElementById('auth-screen').style.display = 'flex';
            document.getElementById('login-form').reset();
        }

        // Auto re-login if session exists
        window.addEventListener('DOMContentLoaded', () => {
            const activeUser = sessionStorage.getItem('authenticated_user');
            if (activeUser) {
                showDashboard(activeUser);
            }
        });
    </script>
</body>
</html>
