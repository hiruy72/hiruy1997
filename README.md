<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Grace Fellowship Weekend School</title>
    <style>
        /* Internal CSS with Flexbox */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Garamond', 'Times New Roman', serif;
        }
        
        body {
            background: url('https://images.unsplash.com/photo-1518655048521-f130df041f66?ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80') no-repeat center center fixed;
            background-size: cover;
            min-height: 100vh;
            color: #333;
            position: relative;
        }
        
        body::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(255, 255, 255, 0.85);
            z-index: -1;
        }
        
        /* Navigation Bar */
        .navbar {
            background-color: #3a5c40;
            color: white;
            padding: 0 5%;
            height: 80px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 2px 15px rgba(0, 0, 0, 0.1);
        }
        
        .logo-container {
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .logo-img {
            width: 50px;
            height: 50px;
            background-color: #f8f8f8;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            color: #3a5c40;
            font-weight: bold;
            font-size: 22px;
            border: 2px solid #d4a762;
        }
        
        .logo-text h2 {
            font-size: 22px;
            font-weight: 600;
            font-family: 'Palatino', serif;
        }
        
        .logo-text p {
            font-size: 13px;
            opacity: 0.9;
            font-style: italic;
        }
        
        .nav-links {
            display: flex;
            gap: 25px;
        }
        
        .nav-links a {
            color: white;
            text-decoration: none;
            font-size: 16px;
            font-weight: 500;
            transition: all 0.3s;
            padding: 8px 12px;
            border-radius: 5px;
        }
        
        .nav-links a:hover {
            background-color: #d4a762;
            color: #333;
        }
        
        /* Main Content */
        .main-container {
            padding: 30px 5%;
            display: flex;
            min-height: calc(100vh - 80px);
        }
        
        /* Sidebar */
        .sidebar {
            width: 280px;
            background-color: rgba(255, 255, 255, 0.9);
            padding: 30px 20px;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            display: flex;
            flex-direction: column;
            margin-right: 30px;
            border: 1px solid #e0e0e0;
        }
        
        .sidebar-header {
            text-align: center;
            margin-bottom: 30px;
            padding-bottom: 20px;
            border-bottom: 1px solid #e0e0e0;
        }
        
        .user-avatar {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            background-color: #f5f5f5;
            margin: 0 auto 15px;
            overflow: hidden;
            display: flex;
            justify-content: center;
            align-items: center;
            color: #777;
            font-size: 40px;
            border: 3px solid #d4a762;
        }
        
        .sidebar-menu {
            flex-grow: 1;
        }
        
        .menu-item {
            padding: 12px 15px;
            margin-bottom: 8px;
            border-radius: 5px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 12px;
            transition: all 0.3s;
            font-size: 16px;
        }
        
        .menu-item:hover {
            background-color: #e8f0e5;
            color: #3a5c40;
        }
        
        .menu-item.active {
            background-color: #3a5c40;
            color: white;
        }
        
        .menu-icon {
            font-size: 20px;
        }
        
        /* Login Panel */
        .content-area {
            flex-grow: 1;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        
        .login-container {
            width: 100%;
            max-width: 500px;
            background: rgba(255, 255, 255, 0.95);
            border-radius: 10px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            overflow: hidden;
            border: 1px solid #e0e0e0;
        }
        
        .login-header {
            background: linear-gradient(135deg, #3a5c40 0%, #2d4733 100%);
            color: white;
            padding: 25px;
            text-align: center;
            position: relative;
        }
        
        .login-header h2 {
            font-size: 28px;
            font-weight: 600;
            margin-bottom: 5px;
            font-family: 'Palatino', serif;
        }
        
        .login-header p {
            font-size: 16px;
            opacity: 0.9;
            font-style: italic;
        }
        
        .login-form {
            padding: 30px;
        }
        
        .form-group {
            margin-bottom: 20px;
            position: relative;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-size: 15px;
            color: #555;
            font-weight: 500;
        }
        
        .form-group input {
            width: 100%;
            padding: 14px 15px;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 15px;
            transition: all 0.3s;
            background-color: #f9f9f9;
        }
        
        .form-group input:focus {
            border-color: #3a5c40;
            box-shadow: 0 0 0 3px rgba(58, 92, 64, 0.2);
            outline: none;
            background-color: white;
        }
        
        .password-container {
            position: relative;
        }
        
        .toggle-password {
            position: absolute;
            right: 15px;
            top: 50%;
            transform: translateY(-50%);
            cursor: pointer;
            color: #777;
            transition: all 0.3s;
        }
        
        .toggle-password:hover {
            color: #3a5c40;
        }
        
        .options {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 25px;
            font-size: 14px;
        }
        
        .remember-me {
            display: flex;
            align-items: center;
            gap: 5px;
        }
        
        .remember-me input {
            cursor: pointer;
        }
        
        .forgot-password a {
            color: #3a5c40;
            text-decoration: none;
            font-weight: 500;
            transition: all 0.3s;
        }
        
        .forgot-password a:hover {
            text-decoration: underline;
            color: #2d4733;
        }
        
        .login-btn {
            width: 100%;
            padding: 14px;
            background: linear-gradient(135deg, #3a5c40 0%, #2d4733 100%);
            color: white;
            border: none;
            border-radius: 5px;
            font-size: 17px;
            font-weight: 500;
            cursor: pointer;
            transition: all 0.3s;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 10px;
        }
        
        .login-btn:hover {
            background: linear-gradient(135deg, #2d4733 0%, #3a5c40 100%);
            transform: translateY(-2px);
        }
        
        .login-footer {
            text-align: center;
            padding: 20px;
            font-size: 14px;
            color: #777;
            border-top: 1px solid #eee;
        }
        
        .login-footer a {
            color: #3a5c40;
            text-decoration: none;
            font-weight: 500;
        }
        
        .bible-verse {
            margin: 20px 0;
            padding: 15px;
            background-color: #f5f5f5;
            border-left: 4px solid #d4a762;
            font-style: italic;
            color: #555;
            text-align: center;
        }
        
        /* Responsive Design */
        @media (max-width: 992px) {
            .sidebar {
                width: 220px;
                padding: 20px 15px;
            }
        }
        
        @media (max-width: 768px) {
            .navbar {
                padding: 0 20px;
            }
            
            .nav-links {
                display: none;
            }
            
            .main-container {
                flex-direction: column;
                padding: 20px;
            }
            
            .sidebar {
                width: 100%;
                margin-right: 0;
                margin-bottom: 30px;
            }
            
            .content-area {
                width: 100%;
            }
        }
        
        @media (max-width: 576px) {
            .login-container {
                max-width: 100%;
            }
            
            .login-header h2 {
                font-size: 24px;
            }
        }
    </style>
</head>
<body>
    <!-- Navigation Bar -->
    <nav class="navbar">
        <div class="logo-container">
            <div class="logo-img">✝</div>
            <div class="logo-text">
                <h2>Grace Fellowship</h2>
                <p>Weekend Bible School</p>
            </div>
        </div>
        
        <div class="nav-links">
            <a href="#">Home</a>
            <a href="#">Classes</a>
            <a href="#">Events</a>
            <a href="#">Resources</a>
            <a href="#">Contact</a>
        </div>
    </nav>
    
    <!-- Main Content -->
    <div class="main-container">
        <!-- Sidebar -->
        <aside class="sidebar">
            <div class="sidebar-header">
                <div class="user-avatar">🙏</div>
                <h3>Student Portal</h3>
                <p>Welcome to our Bible School</p>
            </div>
            
            <div class="sidebar-menu">
                <div class="menu-item active">
                    <span class="menu-icon">🏠</span>
                    <span>Dashboard</span>
                </div>
                <div class="menu-item">
                    <span class="menu-icon">📖</span>
                    <span>Bible Study</span>
                </div>
                <div class="menu-item">
                    <span class="menu-icon">👨‍👩‍👧‍👦</span>
                    <span>Class Groups</span>
                </div>
                <div class="menu-item">
                    <span class="menu-icon">📅</span>
                    <span>Events Calendar</span>
                </div>
                <div class="menu-item">
                    <span class="menu-icon">🎵</span>
                    <span>Worship Songs</span>
                </div>
                <div class="menu-item">
                    <span class="menu-icon">✝</span>
                    <span>Devotionals</span>
                </div>
                <div class="menu-item">
                    <span class="menu-icon">📚</span>
                    <span>Study Materials</span>
                </div>
            </div>
            
            <div class="menu-item">
                <span class="menu-icon">⚙️</span>
                <span>Account Settings</span>
            </div>
        </aside>
        
        <!-- Login Panel -->
        <main class="content-area">
            <div class="login-container">
                <div class="login-header">
                    <h2>Welcome to Grace Fellowship</h2>
                    <p>Weekend Bible School Portal</p>
                </div>
                
                <div class="bible-verse">
                    "Train up a child in the way he should go, and when he is old he will not depart from it."<br>
                    - Proverbs 22:6
                </div>
                
                <form class="login-form" id="loginForm">
                    <div class="form-group">
                        <label for="username">Family ID or Email</label>
                        <input type="text" id="username" placeholder="e.g. GF12345 or family@email.com" required>
                    </div>
                    
                    <div class="form-group">
                        <label for="password">Password</label>
                        <div class="password-container">
                            <input type="password" id="password" placeholder="Enter your password" required>
                            <span class="toggle-password" id="togglePassword">👁️</span>
                        </div>
                    </div>
                    
                    <div class="options">
                        <div class="remember-me">
                            <input type="checkbox" id="remember">
                            <label for="remember">Remember me</label>
                        </div>
                        <div class="forgot-password">
                            <a href="#">Forgot password?</a>
                        </div>
                    </div>
                    
                    <button type="submit" class="login-btn">
                        <span id="btnText">Sign In</span>
                        <span id="btnIcon">✝</span>
                    </button>
                </form>
                
                <div class="login-footer">
                    <p>New family? <a href="#">Register here</a> | Need help? <a href="#">Contact us</a></p>
                </div>
            </div>
        </main>
    </div>

    <script>
        // Interactive JavaScript for Church Weekend School
        document.addEventListener('DOMContentLoaded', function() {
            // Password toggle
            const togglePassword = document.getElementById('togglePassword');
            const passwordInput = document.getElementById('password');
            
            togglePassword.addEventListener('click', function() {
                const type = passwordInput.getAttribute('type') === 'password' ? 'text' : 'password';
                passwordInput.setAttribute('type', type);
                this.textContent = type === 'password' ? '👁️' : '🔒';
            });
            
            // Form submission with animation
            const loginForm = document.getElementById('loginForm');
            const btnText = document.getElementById('btnText');
            const btnIcon = document.getElementById('btnIcon');
            
            loginForm.addEventListener('submit', function(e) {
                e.preventDefault();
                
                // Get form values
                const username = document.getElementById('username').value;
                const password = document.getElementById('password').value;
                const rememberMe = document.getElementById('remember').checked;
                
                // Show loading state
                btnText.textContent = 'Praying...';
                btnIcon.textContent = '🙏';
                
                // Simulate authentication
                setTimeout(() => {
                    if (username && password.length >= 6) {
                        // Success
                        btnText.textContent = 'Welcome!';
                        btnIcon.textContent = '✝';
                        
                        setTimeout(() => {
                            alert(`Welcome ${username}! May God bless your study time.`);
                            btnText.textContent = 'Sign In';
                            btnIcon.textContent = '✝';
                        }, 1000);
                    } else {
                        // Error
                        btnText.textContent = 'Try Again';
                        btnIcon.textContent = '⚠️';
                        
                        setTimeout(() => {
                            alert('Please check your credentials and try again.');
                            btnText.textContent = 'Sign In';
                            btnIcon.textContent = '✝';
                        }, 1000);
                    }
                }, 1500);
            });
            
            // Menu item interaction
            const menuItems = document.querySelectorAll('.menu-item');
            menuItems.forEach(item => {
                item.addEventListener('click', function() {
                    menuItems.forEach(i => i.classList.remove('active'));
                    this.classList.add('active');
                    
                    // Show content based on selection
                    const section = this.textContent.trim();
                    alert(`Loading ${section} section...`);
                });
            });
            
            // Daily verse rotation (simplified)
            const verses = [
                "\"I can do all things through Christ who strengthens me.\" - Philippians 4:13",
                "\"For God so loved the world that He gave His only begotten Son...\" - John 3:16",
                "\"Your word is a lamp to my feet and a light to my path.\" - Psalm 119:105",
                "\"Trust in the Lord with all your heart...\" - Proverbs 3:5-6"
            ];
            
            const verseElement = document.querySelector('.bible-verse');
            verseElement.textContent = verses[Math.floor(Math.random() * verses.length)];
        });
    </script>
</body>
</html>
