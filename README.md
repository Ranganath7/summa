
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Bus Safety Tracker</title>
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      margin: 0;
      padding: 0;
      background-color: #f5f7fa;
      color: #333;
    }

    .container {
      max-width: 1200px;
      margin: 0 auto;
      padding: 0 20px;
    }

    nav {
      background: linear-gradient(135deg, #3a86ff, #4361ee);
      color: white;
      padding: 15px 0;
      box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    }

    .navbar {
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .logo {
      display: flex;
      align-items: center;
      font-size: 24px;
      font-weight: bold;
    }

    .logo-icon {
      margin-right: 10px;
      font-size: 26px;
    }

    .nav-links {
      display: flex;
      gap: 20px;
    }

    .nav-link {
      color: white;
      text-decoration: none;
      padding: 8px 15px;
      border-radius: 4px;
      transition: background-color 0.3s;
    }

    .nav-link:hover, .nav-link.active {
      background-color: rgba(255, 255, 255, 0.2);
    }

    .page {
      display: none;
      padding: 30px 0;
    }

    .page.active {
      display: block;
    }

    .card {
      background-color: white;
      border-radius: 10px;
      padding: 25px;
      margin-bottom: 20px;
      box-shadow: 0 2px 10px rgba(0, 0, 0, 0.08);
    }

    h2 {
      margin-top: 0;
      color: #3a86ff;
      font-size: 24px;
    }

    h3 {
      color: #333;
      margin-top: 20px;
      margin-bottom: 15px;
    }

    .tabs {
      display: flex;
      border-bottom: 1px solid #ddd;
      margin-bottom: 20px;
    }

    .tab {
      padding: 10px 20px;
      cursor: pointer;
      border-bottom: 2px solid transparent;
    }

    .tab.active {
      border-bottom-color: #3a86ff;
      color: #3a86ff;
    }

    .tab-content {
      display: none;
    }

    .tab-content.active {
      display: block;
    }

    .form-group {
      margin-bottom: 15px;
    }

    label {
      display: block;
      margin-bottom: 5px;
      font-weight: 500;
    }

    input[type="text"],
    input[type="email"],
    input[type="password"] {
      width: 100%;
      padding: 10px;
      border: 1px solid #ddd;
      border-radius: 4px;
      box-sizing: border-box;
    }

    .button {
      padding: 10px 15px;
      border: none;
      border-radius: 4px;
      cursor: pointer;
      font-weight: 600;
      transition: background-color 0.3s, transform 0.2s;
    }

    .button:hover {
      transform: translateY(-2px);
    }

    .button-primary {
      background-color: #3a86ff;
      color: white;
    }

    .button-primary:hover {
      background-color: #2a75ee;
    }

    .button-secondary {
      background-color: #fb5607;
      color: white;
    }

    .button-secondary:hover {
      background-color: #ea4c04;
    }

    .button-outline {
      background-color: transparent;
      border: 1px solid #3a86ff;
      color: #3a86ff;
    }

    .button-outline:hover {
      background-color: rgba(58, 134, 255, 0.1);
    }

    .button-block {
      display: block;
      width: 100%;
      margin-top: 10px;
    }

    .checkbox-group {
      display: flex;
      align-items: center;
      margin-bottom: 10px;
    }

    .checkbox-group input {
      margin-right: 10px;
    }

    .map-placeholder {
      background-color: #eee;
      height: 200px;
      display: flex;
      align-items: center;
      justify-content: center;
      border-radius: 8px;
      margin: 20px 0;
    }

    .map-icon {
      font-size: 48px;
      color: #3a86ff;
    }

    .bus-item {
      padding: 15px;
      border-bottom: 1px solid #eee;
      display: flex;
      align-items: center;
    }

    .bus-icon {
      width: 40px;
      height: 40px;
      background-color: #3a86ff;
      color: white;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      margin-right: 15px;
    }

    .bus-info {
      flex-grow: 1;
    }

    .bus-name {
      font-weight: bold;
    }

    .bus-eta {
      font-size: 14px;
      color: #666;
    }

    .or-divider {
      display: flex;
      align-items: center;
      margin: 20px 0;
      color: #666;
    }

    .or-divider:before, 
    .or-divider:after {
      content: "";
      flex-grow: 1;
      height: 1px;
      background-color: #ddd;
    }

    .or-divider span {
      padding: 0 15px;
    }

    .google-button {
      display: flex;
      align-items: center;
      justify-content: center;
      background-color: white;
      border: 1px solid #ddd;
      color: #333;
      width: 100%;
      padding: 10px;
      border-radius: 4px;
      cursor: pointer;
      gap: 10px;
    }

    .google-icon {
      color: #4285F4;
    }

    .notification {
      position: fixed;
      bottom: 20px;
      right: 20px;
      background-color: #4CAF50;
      color: white;
      padding: 15px 20px;
      border-radius: 4px;
      display: none;
      box-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
    }
    
    .features {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
      gap: 20px;
      margin-bottom: 20px;
    }
    
    .feature {
      background-color: #f8f9fa;
      padding: 20px;
      border-radius: 8px;
      text-align: center;
    }
    
    .feature-icon {
      font-size: 32px;
      color: #3a86ff;
      margin-bottom: 15px;
    }
    
    /* User profile in navbar */
    .user-profile {
      display: flex;
      align-items: center;
      gap: 10px;
      background-color: rgba(255, 255, 255, 0.1);
      padding: 5px 15px;
      border-radius: 20px;
      display: none;
    }
    
    .user-avatar {
      width: 30px;
      height: 30px;
      background-color: white;
      color: #3a86ff;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-weight: bold;
    }
    
    /* Modal */
    .modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.5);
      z-index: 1000;
      align-items: center;
      justify-content: center;
    }
    
    .modal-content {
      background-color: white;
      padding: 25px;
      border-radius: 10px;
      width: 400px;
      max-width: 90%;
    }
    
    .modal-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 15px;
    }
    
    .close-modal {
      font-size: 24px;
      cursor: pointer;
    }
    
    footer {
      background-color: #333;
      color: white;
      padding: 30px 0;
      margin-top: 40px;
    }
    
    .footer-content {
      display: flex;
      justify-content: space-between;
      flex-wrap: wrap;
    }
    
    .footer-logo {
      margin-bottom: 20px;
    }
    
    .footer-links {
      display: flex;
      gap: 20px;
    }
    
    .footer-links a {
      color: #ddd;
      text-decoration: none;
    }
    
    .footer-links a:hover {
      color: white;
    }
    
    @media (max-width: 768px) {
      .footer-content {
        flex-direction: column;
        gap: 20px;
      }
      
      .features {
        grid-template-columns: 1fr;
      }
    }
  </style>
</head>

<body>
  <nav>
    <div class="container navbar">
      <div class="logo">
        <span class="logo-icon">🚌</span>
        <span>Bus Safety Tracker</span>
      </div>
      <div class="nav-links">
        <a href="#" class="nav-link active" id="loginLink" onclick="showPage('loginPage')">Login</a>
        <a href="#" class="nav-link" id="trackerLink" onclick="showPage('trackerPage')">Tracker</a>
      </div>
      <div class="user-profile" id="userProfile">
        <div class="user-avatar" id="userAvatar">U</div>
        <span id="userName">User</span>
      </div>
    </div>
  </nav>
  
  <div class="container">
    <div id="loginPage" class="page active">
      <div class="card">
        <div class="tabs">
          <div class="tab active" id="loginTab" onclick="switchTab('login')">Login</div>
          <div class="tab" id="signupTab" onclick="switchTab('signup')">Sign Up</div>
        </div>
        
        <div id="loginContent" class="tab-content active">
          <h2>Welcome Back</h2>
          <form id="loginForm">
            <div class="form-group">
              <label for="loginEmail">Email</label>
              <input type="email" id="loginEmail" required>
            </div>
            <div class="form-group">
              <label for="loginPassword">Password</label>
              <input type="password" id="loginPassword" required>
            </div>
            <button type="button" class="button button-primary button-block" onclick="login()">Login</button>
          </form>
          
          <div class="or-divider">
            <span>or</span>
          </div>
          
          <button class="google-button" onclick="googleLogin()">
            <span class="google-icon">G</span>
            Continue with Google
          </button>
        </div>
        
        <div id="signupContent" class="tab-content">
          <h2>Create Account</h2>
          <form id="signupForm">
            <div class="form-group">
              <label for="fullName">Full Name</label>
              <input type="text" id="fullName" required>
            </div>
            <div class="form-group">
              <label for="phoneNumber">Phone Number</label>
              <input type="text" id="phoneNumber" required>
            </div>
            <div class="form-group">
              <label for="signupEmail">Email</label>
              <input type="email" id="signupEmail" required>
            </div>
            <div class="form-group">
              <label for="collegeEmail">College Email ID (if student)</label>
              <input type="email" id="collegeEmail">
            </div>
            <div class="form-group">
              <label for="signupPassword">Password</label>
              <input type="password" id="signupPassword" required>
            </div>
            <div class="form-group">
              <label for="collegeName">College Name</label>
              <input type="text" id="collegeName">
            </div>
            <div class="form-group">
              <label for="regNumber">Registration Number</label>
              <input type="text" id="regNumber">
            </div>
            <div class="form-group">
              <label for="degree">Degree / Course</label>
              <input type="text" id="degree">
            </div>
            <div class="form-group">
              <label for="parentNumber">Parent Number</label>
              <input type="text" id="parentNumber">
            </div>
            <button type="button" class="button button-secondary button-block" onclick="signup()">Sign Up</button>
          </form>
        </div>
      </div>
    </div>
    
    <div id="trackerPage" class="page">
      <div class="card">
        <h2>Safety Tracker</h2>
        
        <div class="features">
          <div class="feature">
            <div class="feature-icon">📍</div>
            <h3>Real-time Tracking</h3>
            <p>Track your bus location in real-time</p>
          </div>
          <div class="feature">
            <div class="feature-icon">🚨</div>
            <h3>Safety Alerts</h3>
            <p>Get instant notifications for safety concerns</p>
          </div>
          <div class="feature">
            <div class="feature-icon">📱</div>
            <h3>Mobile Access</h3>
            <p>Access the tracker from any device</p>
          </div>
        </div>
        
        <button class="button button-primary" onclick="openApp()">Go to App</button>
      </div>
      
      <div class="card">
        <h3>Find Your Bus</h3>
        <div class="form-group" style="display: flex; gap: 10px;">
          <input type="text" id="busNumber" placeholder="Enter your bus no" style="flex: 1;">
          <button class="button button-secondary" onclick="searchBus()">Search</button>
        </div>
      </div>
      
      <div class="card">
        <h3>Options</h3>
        <div class="checkbox-group">
          <input type="checkbox" id="leftBus" onclick="toggleOption('leftBus')">
          <label for="leftBus">I left the bus</label>
        </div>
        <div class="checkbox-group">
          <input type="checkbox" id="cameraOn" onclick="toggleOption('cameraOn')">
          <label for="cameraOn">Camera on</label>
        </div>
        <div class="checkbox-group">
          <input type="checkbox" id="settingsToggle" onclick="toggleSettings()">
          <label for="settingsToggle">Settings</label>
        </div>
        <div class="checkbox-group">
          <input type="checkbox" id="filterBus" onclick="toggleOption('filterBus')">
          <label for="filterBus">Filter your bus no</label>
        </div>
      </div>
      
      <div class="card" id="settingsCard" style="display: none;">
        <h3>Settings</h3>
        <div class="checkbox-group">
          <input type="checkbox" id="accidentAlert" checked onclick="updateSetting('accidentAlert')">
          <label for="accidentAlert">Accident Alert</label>
        </div>
        <div class="checkbox-group">
          <input type="checkbox" id="gps" checked onclick="updateSetting('gps')">
          <label for="gps">GPS</label>
        </div>
        <div class="checkbox-group">
          <input type="checkbox" id="locationTracking" checked onclick="updateSetting('locationTracking')">
          <label for="locationTracking">Location Tracking</label>
        </div>
      </div>
      
      <div class="card">
        <h3>Map</h3>
        <div class="map-placeholder">
          <div class="map-icon" id="mapIcon">🗺️</div>
        </div>
      </div>
      
      <div class="card">
        <h3>Nearby Buses</h3>
        <div id="nearbyBuses">
          <div class="bus-item" onclick="selectBus('B101')">
            <div class="bus-icon">🚌</div>
            <div class="bus-info">
              <div class="bus-name">Bus B101</div>
              <div class="bus-eta">ETA: 5 minutes</div>
            </div>
          </div>
          <div class="bus-item" onclick="selectBus('B202')">
            <div class="bus-icon">🚌</div>
            <div class="bus-info">
              <div class="bus-name">Bus B202</div>
              <div class="bus-eta">ETA: 12 minutes</div>
            </div>
          </div>
          <div class="bus-item" onclick="selectBus('B308')">
            <div class="bus-icon">🚌</div>
            <div class="bus-info">
              <div class="bus-name">Bus B308</div>
              <div class="bus-eta">ETA: 18 minutes</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  
  <div class="modal" id="appModal">
    <div class="modal-content">
      <div class="modal-header">
        <h2>Bus Safety App</h2>
        <span class="close-modal" onclick="closeModal()">×</span>
      </div>
      <p>The Bus Safety App is loading. You'll be redirected shortly.</p>
      <div style="text-align: center; margin: 20px 0;">
        Loading...
      </div>
      <button class="button button-primary button-block" onclick="closeModal()">Close</button>
    </div>
  </div>
  
  <div class="notification" id="notification"></div>
  
  <footer>
    <div class="container">
      <div class="footer-content">
        <div class="footer-logo">
          <div class="logo">
            <span class="logo-icon">🚌</span>
            <span>Bus Safety Tracker</span>
          </div>
          <p>Keeping students safe during transit</p>
        </div>
        <div class="footer-links">
          <a href="#">About Us</a>
          <a href="#">Privacy Policy</a>
          <a href="#">Terms of Service</a>
          <a href="#">Contact</a>
        </div>
      </div>
    </div>
  </footer>

  <script>
    // Page Navigation
    function showPage(pageId) {
      // Hide all pages
      document.querySelectorAll('.page').forEach(page => {
        page.classList.remove('active');
      });
      
      // Show selected page
      document.getElementById(pageId).classList.add('active');
      
      // Update active nav link
      document.querySelectorAll('.nav-link').forEach(link => {
        link.classList.remove('active');
      });
      
      if (pageId === 'loginPage') {
        document.getElementById('loginLink').classList.add('active');
      } else if (pageId === 'trackerPage') {
        document.getElementById('trackerLink').classList.add('active');
      }
    }
    
    // Tab Switching
    function switchTab(tabName) {
      // Update tab active state
      if (tabName === 'login') {
        document.getElementById('loginTab').classList.add('active');
        document.getElementById('signupTab').classList.remove('active');
        document.getElementById('loginContent').classList.add('active');
        document.getElementById('signupContent').classList.remove('active');
      } else {
        document.getElementById('loginTab').classList.remove('active');
        document.getElementById('signupTab').classList.add('active');
        document.getElementById('loginContent').classList.remove('active');
        document.getElementById('signupContent').classList.add('active');
      }
    }
    
    // Login Function
    function login() {
      const email = document.getElementById('loginEmail').value;
      const password = document.getElementById('loginPassword').value;
      
      if (!email || !password) {
        showNotification('Please fill in all fields', 'error');
        return;
      }
      
      // Simulate successful login
      setTimeout(() => {
        showNotification('Login successful!');
        updateUserProfile('User');
        showPage('trackerPage');
      }, 1000);
    }
    
    // Signup Function
    function signup() {
      const name = document.getElementById('fullName').value;
      const email = document.getElementById('signupEmail').value;
      const password = document.getElementById('signupPassword').value;
      
      if (!name || !email || !password) {
        showNotification('Please fill in all required fields', 'error');
        return;
      }
      
      // Simulate successful signup
      setTimeout(() => {
        showNotification('Account created successfully!');
        updateUserProfile(name);
        showPage('trackerPage');
      }, 1000);
    }
    
    // Google Login
    function googleLogin() {
      // Simulate Google login
      setTimeout(() => {
        showNotification('Google login successful!');
        updateUserProfile('Google User');
        showPage('trackerPage');
      }, 1000);
    }
    
    // Update User Profile
    function updateUserProfile(name) {
      const userProfile = document.getElementById('userProfile');
      const userName = document.getElementById('userName');
      const userAvatar = document.getElementById('userAvatar');
      
      userProfile.style.display = 'flex';
      userName.textContent = name;
      userAvatar.textContent = name.charAt(0);
    }
    
    // Toggle Settings
    function toggleSettings() {
      const settingsCard = document.getElementById('settingsCard');
      if (settingsCard.style.display === 'none') {
        settingsCard.style.display = 'block';
        showNotification('Settings opened');
      } else {
        settingsCard.style.display = 'none';
        showNotification('Settings closed');
      }
    }
    
    // Toggle Option
    function toggleOption(optionId) {
      const option = document.getElementById(optionId);
      showNotification(`${optionId} ${option.checked ? 'enabled' : 'disabled'}`);
    }
    
    // Update Setting
    function updateSetting(settingId) {
      const setting = document.getElementById(settingId);
      showNotification(`${settingId} ${setting.checked ? 'enabled' : 'disabled'}`);
    }
    
    // Search Bus
    function searchBus() {
      const busNumber = document.getElementById('busNumber').value;
      if (!busNumber) {
        showNotification('Please enter a bus number', 'error');
        return;
      }
      
      showNotification(`Searching for bus ${busNumber}...`);
      
      // Simulate bus search
      setTimeout(() => {
        document.getElementById('mapIcon').textContent = '📍';
        showNotification(`Bus ${busNumber} found!`);
      }, 1500);
    }
    
    // Select Bus
    function selectBus(busId) {
      showNotification(`Bus ${busId} selected`);
      document.getElementById('busNumber').value = busId;
    }
    
    // Open App
    function openApp() {
      document.getElementById('appModal').style.display = 'flex';
      
      // Simulate app loading
      setTimeout(() => {
        showNotification('App launched successfully!');
      }, 2000);
    }
    
    // Close Modal
    function closeModal() {
      document.getElementById('appModal').style.display = 'none';
    }
    
    // Show Notification
    function showNotification(message, type = 'success') {
      const notification = document.getElementById('notification');
      notification.textContent = message;
      notification.style.display = 'block';
      
      if (type === 'error') {
        notification.style.backgroundColor = '#d90429';
      } else {
        notification.style.backgroundColor = '#4CAF50';
      }
      
      // Hide after 3 seconds
      setTimeout(() => {
        notification.style.display = 'none';
      }, 3000);
    }
  </script>
</body>
</html>
