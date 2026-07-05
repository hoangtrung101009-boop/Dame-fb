# Dame-fb
Tool dame fb bản thử nghiêm
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>FB MESSAGE DAME TOOL PRO</title>
    
    <!-- CSS -->
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%);
            color: #fff;
            min-height: 100vh;
            padding: 10px;
        }

        .container {
            max-width: 500px;
            margin: 0 auto;
            padding: 15px;
        }

        .header {
            text-align: center;
            padding: 20px 0;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            border-radius: 15px;
            margin-bottom: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
        }

        .header h1 {
            font-size: 24px;
            color: #fff;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        .header p {
            font-size: 12px;
            color: #e0e0e0;
            margin-top: 5px;
        }

        .status-bar {
            background: rgba(255,255,255,0.1);
            border-radius: 10px;
            padding: 10px 15px;
            margin-bottom: 15px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            backdrop-filter: blur(10px);
        }

        .status-item {
            text-align: center;
        }

        .status-item span {
            display: block;
            font-size: 10px;
            color: #aaa;
        }

        .status-item strong {
            font-size: 18px;
            color: #4CAF50;
        }

        .menu-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 10px;
            margin-bottom: 15px;
        }

        .menu-btn {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            border: none;
            color: white;
            padding: 15px 10px;
            border-radius: 10px;
            font-size: 14px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
        }

        .menu-btn:active {
            transform: scale(0.95);
            box-shadow: 0 2px 10px rgba(0,0,0,0.3);
        }

        .menu-btn.danger {
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
        }

        .menu-btn.success {
            background: linear-gradient(135deg, #4CAF50 0%, #45a049 100%);
        }

        .menu-btn.warning {
            background: linear-gradient(135deg, #ff9800 0%, #f57c00 100%);
        }

        .menu-btn.info {
            background: linear-gradient(135deg, #2196F3 0%, #1976D2 100%);
        }

        .section {
            background: rgba(255,255,255,0.1);
            border-radius: 15px;
            padding: 15px;
            margin-bottom: 15px;
            backdrop-filter: blur(10px);
            display: none;
        }

        .section.active {
            display: block;
            animation: slideIn 0.3s ease;
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(-10px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .section-title {
            font-size: 18px;
            font-weight: 700;
            margin-bottom: 15px;
            color: #667eea;
        }

        .form-group {
            margin-bottom: 12px;
        }

        .form-group label {
            display: block;
            font-size: 12px;
            color: #aaa;
            margin-bottom: 5px;
        }

        .form-control {
            width: 100%;
            padding: 10px 12px;
            background: rgba(255,255,255,0.1);
            border: 1px solid rgba(255,255,255,0.2);
            border-radius: 8px;
            color: #fff;
            font-size: 14px;
            transition: all 0.3s ease;
        }

        .form-control:focus {
            outline: none;
            border-color: #667eea;
            background: rgba(255,255,255,0.15);
            box-shadow: 0 0 10px rgba(102,126,234,0.3);
        }

        .form-control::placeholder {
            color: rgba(255,255,255,0.4);
        }

        textarea.form-control {
            min-height: 80px;
            resize: vertical;
        }

        .btn {
            width: 100%;
            padding: 12px;
            border: none;
            border-radius: 8px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            margin-bottom: 8px;
        }

        .btn-primary {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
        }

        .btn-danger {
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            color: white;
        }

        .btn-success {
            background: linear-gradient(135deg, #4CAF50 0%, #45a049 100%);
            color: white;
        }

        .btn-warning {
            background: linear-gradient(135deg, #ff9800 0%, #f57c00 100%);
            color: white;
        }

        .btn:active {
            transform: scale(0.98);
        }

        .btn:disabled {
            opacity: 0.6;
            cursor: not-allowed;
        }

        .log-box {
            background: rgba(0,0,0,0.3);
            border-radius: 10px;
            padding: 10px;
            max-height: 200px;
            overflow-y: auto;
            font-size: 12px;
            font-family: 'Courier New', monospace;
            margin-top: 10px;
        }

        .log-box .log-success {
            color: #4CAF50;
        }

        .log-box .log-error {
            color: #f44336;
        }

        .log-box .log-info {
            color: #2196F3;
        }

        .progress-bar {
            width: 100%;
            height: 6px;
            background: rgba(255,255,255,0.1);
            border-radius: 3px;
            margin: 10px 0;
            overflow: hidden;
        }

        .progress-bar .progress-fill {
            height: 100%;
            background: linear-gradient(90deg, #667eea, #764ba2);
            border-radius: 3px;
            transition: width 0.3s ease;
            width: 0%;
        }

        .cookie-display {
            background: rgba(0,0,0,0.3);
            border-radius: 8px;
            padding: 10px;
            margin: 10px 0;
            word-break: break-all;
            font-size: 11px;
            font-family: 'Courier New', monospace;
            color: #aaa;
        }

        .back-btn {
            background: rgba(255,255,255,0.1);
            border: 1px solid rgba(255,255,255,0.2);
            color: white;
            padding: 8px 15px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 14px;
            margin-bottom: 15px;
            transition: all 0.3s ease;
        }

        .back-btn:active {
            background: rgba(255,255,255,0.2);
        }

        /* Scrollbar */
        ::-webkit-scrollbar {
            width: 5px;
        }

        ::-webkit-scrollbar-track {
            background: rgba(255,255,255,0.1);
        }

        ::-webkit-scrollbar-thumb {
            background: rgba(255,255,255,0.3);
            border-radius: 5px;
        }

        /* Toast notification */
        .toast {
            position: fixed;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
            background: rgba(0,0,0,0.9);
            color: white;
            padding: 12px 24px;
            border-radius: 10px;
            font-size: 14px;
            z-index: 1000;
            display: none;
            animation: toastIn 0.3s ease;
            max-width: 90%;
            text-align: center;
        }

        @keyframes toastIn {
            from {
                opacity: 0;
                transform: translateX(-50%) translateY(-20px);
            }
            to {
                opacity: 1;
                transform: translateX(-50%) translateY(0);
            }
        }

        .toast.success {
            border-left: 4px solid #4CAF50;
        }

        .toast.error {
            border-left: 4px solid #f44336;
        }

        .toast.info {
            border-left: 4px solid #2196F3;
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Toast notification -->
        <div id="toast" class="toast"></div>

        <!-- Header -->
        <div class="header">
            <h1>🔥 FB MESSAGE DAME PRO</h1>
            <p>Tool spam Messenger mạnh mẽ nhất</p>
        </div>

        <!-- Status Bar -->
        <div class="status-bar">
            <div class="status-item">
                <span>Cookie</span>
                <strong id="cookieStatus">❌ Chưa có</strong>
            </div>
            <div class="status-item">
                <span>Đã gửi</span>
                <strong id="sentCount">0</strong>
            </div>
            <div class="status-item">
                <span>Lỗi</span>
                <strong id="errorCount" style="color:#f44336;">0</strong>
            </div>
        </div>

        <!-- Main Menu -->
        <div id="mainMenu">
            <div class="menu-grid">
                <button class="menu-btn info" onclick="showSection('cookieSection')">
                    🍪 Nhập Cookie
                </button>
                <button class="menu-btn success" onclick="showSection('singleSpamSection')">
                    📨 Spam Đơn
                </button>
                <button class="menu-btn warning" onclick="showSection('massSpamSection')">
                    👥 Spam Hàng Loạt
                </button>
                <button class="menu-btn danger" onclick="showSection('autoSpamSection')">
                    🤖 Spam Tự Động
                </button>
                <button class="menu-btn" onclick="showSection('groupSpamSection')">
                    👪 Spam Nhóm
                </button>
                <button class="menu-btn" onclick="showSection('fileSpamSection')">
                    📎 Spam File
                </button>
            </div>
        </div>

        <!-- Cookie Section -->
        <div id="cookieSection" class="section">
            <button class="back-btn" onclick="hideSection('cookieSection')">← Quay lại</button>
            <div class="section-title">🍪 Quản lý Cookie</div>
            
            <div class="form-group">
                <label>Nhập Cookie Facebook</label>
                <textarea id="cookieInput" class="form-control" placeholder="Nhập cookie dạng: c_user=xxx; xs=xxx"></textarea>
            </div>
            
            <button class="btn btn-primary" onclick="saveCookie()">💾 Lưu Cookie</button>
            <button class="btn btn-danger" onclick="deleteCookie()">🗑️ Xóa Cookie</button>
            
            <div class="cookie-display" id="cookieDisplay">
                Chưa có cookie nào được lưu
            </div>
        </div>

        <!-- Single Spam Section -->
        <div id="singleSpamSection" class="section">
            <button class="back-btn" onclick="hideSection('singleSpamSection')">← Quay lại</button>
            <div class="section-title">📨 Spam Tin Nhắn Đơn</div>
            
            <div class="form-group">
                <label>ID Facebook người nhận</label>
                <input type="text" id="singleTarget" class="form-control" placeholder="Nhập ID Facebook">
            </div>
            
            <div class="form-group">
                <label>Nội dung tin nhắn</label>
                <textarea id="singleMessage" class="form-control" placeholder="Nhập nội dung spam"></textarea>
            </div>
            
            <div class="form-group">
                <label>Số lần gửi</label>
                <input type="number" id="singleCount" class="form-control" value="100" min="1">
            </div>
            
            <div class="form-group">
                <label>Delay (giây)</label>
                <input type="number" id="singleDelay" class="form-control" value="0.2" step="0.1" min="0.1">
            </div>
            
            <button class="btn btn-success" onclick="startSingleSpam()">🚀 Bắt đầu Spam</button>
            <button class="btn btn-danger" onclick="stopSpam()">⏹️ Dừng</button>
            
            <div class="progress-bar">
                <div class="progress-fill" id="singleProgress"></div>
            </div>
            
            <div class="log-box" id="singleLog"></div>
        </div>

        <!-- Mass Spam Section -->
        <div id="massSpamSection" class="section">
            <button class="back-btn" onclick="hideSection('massSpamSection')">← Quay lại</button>
            <div class="section-title">👥 Spam Hàng Loạt</div>
            
            <div class="form-group">
                <label>Danh sách ID (mỗi ID 1 dòng)</label>
                <textarea id="massTargets" class="form-control" placeholder="ID1&#10;ID2&#10;ID3"></textarea>
            </div>
            
            <div class="form-group">
                <label>Nội dung tin nhắn</label>
                <textarea id="massMessage" class="form-control" placeholder="Nhập nội dung spam"></textarea>
            </div>
            
            <div class="form-group">
                <label>Số lần gửi mỗi target</label>
                <input type="number" id="massCount" class="form-control" value="10" min="1">
            </div>
            
            <button class="btn btn-success" onclick="startMassSpam()">🚀 Bắt đầu Spam</button>
            <button class="btn btn-danger" onclick="stopSpam()">⏹️ Dừng</button>
            
            <div class="log-box" id="massLog"></div>
        </div>

        <!-- Auto Spam Section -->
        <div id="autoSpamSection" class="section">
            <button class="back-btn" onclick="hideSection('autoSpamSection')">← Quay lại</button>
            <div class="section-title">🤖 Spam Tự Động</div>
            
            <div class="form-group">
                <label>ID Facebook người nhận</label>
                <input type="text" id="autoTarget" class="form-control" placeholder="Nhập ID Facebook">
            </div>
            
            <div class="form-group">
                <label>Số lần spam</label>
                <input type="number" id="autoCount" class="form-control" value="500" min="1">
            </div>
            
            <div class="form-group">
                <label>Delay (giây)</label>
                <input type="number" id="autoDelay" class="form-control" value="0.1" step="0.1" min="0.1">
            </div>
            
            <button class="btn btn-success" onclick="startAutoSpam()">🚀 Bắt đầu Spam</button>
            <button class="btn btn-danger" onclick="stopSpam()">⏹️ Dừng</button>
            
            <div class="progress-bar">
                <div class="progress-fill" id="autoProgress"></div>
            </div>
            
            <div class="log-box" id="autoLog"></div>
        </div>

        <!-- Group Spam Section -->
        <div id="groupSpamSection" class="section">
            <button class="back-btn" onclick="hideSection('groupSpamSection')">← Quay lại</button>
            <div class="section-title">👪 Spam Nhóm</div>
            
            <div class="form-group">
                <label>ID nhóm Facebook</label>
                <input type="text" id="groupTarget" class="form-control" placeholder="Nhập ID nhóm">
            </div>
            
            <div class="form-group">
                <label>Nội dung spam</label>
                <textarea id="groupMessage" class="form-control" placeholder="Nhập nội dung spam"></textarea>
            </div>
            
            <div class="form-group">
                <label>Số lần spam</label>
                <input type="number" id="groupCount" class="form-control" value="100" min="1">
            </div>
            
            <div class="form-group">
                <label>Delay (giây)</label>
                <input type="number" id="groupDelay" class="form-control" value="0.3" step="0.1" min="0.1">
            </div>
            
            <button class="btn btn-success" onclick="startGroupSpam()">🚀 Bắt đầu Spam</button>
            <button class="btn btn-danger" onclick="stopSpam()">⏹️ Dừng</button>
            
            <div class="log-box" id="groupLog"></div>
        </div>

        <!-- File Spam Section -->
        <div id="fileSpamSection" class="section">
            <button class="back-btn" onclick="hideSection('fileSpamSection')">← Quay lại</button>
            <div class="section-title">📎 Spam Kèm File</div>
            
            <div class="form-group">
                <label>ID Facebook người nhận</label>
                <input type="text" id="fileTarget" class="form-control" placeholder="Nhập ID Facebook">
            </div>
            
            <div class="form-group">
                <label>Chọn file</label>
                <input type="file" id="fileInput" class="form-control">
            </div>
            
            <div class="form-group">
                <label>Nội dung tin nhắn</label>
                <textarea id="fileMessage" class="form-control" placeholder="Nhập nội dung (có thể để trống)"></textarea>
            </div>
            
            <div class="form-group">
                <label>Số lần gửi</label>
                <input type="number" id="fileCount" class="form-control" value="10" min="1">
            </div>
            
            <button class="btn btn-success" onclick="startFileSpam()">🚀 Bắt đầu Spam</button>
            <button class="btn btn-danger" onclick="stopSpam()">⏹️ Dừng</button>
            
            <div class="log-box" id="fileLog"></div>
        </div>
    </div>

    <!-- JavaScript -->
    <script>
        // Global variables
        let cookieData = null;
        let isSpamming = false;
        let spamInterval = null;
        let sentCount = 0;
        let errorCount = 0;

        // Auto messages for spam
        const autoMessages = [
            "Xin chào! Bạn khỏe không?",
            "Hôm nay thế nào?",
            "Đang làm gì thế?",
            "Nhớ bạn quá!",
            "Có chuyện gì vui không?",
            "Ăn cơm chưa?",
            "Đi ngủ sớm nhé!",
            "Chúc bạn ngày mới tốt lành!",
            "Hello! How are you?",
            "I miss you!",
            "What are you doing?",
            "Good morning!",
            "Good night!",
            "Have a nice day!",
            "Thinking of you!",
            "You are amazing!",
            "Stay safe!",
            "Take care!",
            "Love you!",
            "Hug you!",
            "Bạn có muốn đi chơi không?",
            "Tôi nhớ bạn nhiều lắm!",
            "Hôm nay trời đẹp quá!",
            "Bạn đã ăn sáng chưa?",
            "Chúc bạn một ngày vui vẻ!",
            "Mình cưới nhau đi!",
            "Yêu bạn nhất trên đời!",
            "Bạn là số 1!",
            "Không có bạn mình buồn lắm!",
            "Mãi mãi bên nhau nhé!"
        ];

        // Toast notification
        function showToast(message, type = 'info') {
            const toast = document.getElementById('toast');
            toast.textContent = message;
            toast.className = `toast ${type}`;
            toast.style.display = 'block';
            
            setTimeout(() => {
                toast.style.display = 'none';
            }, 3000);
        }

        // Show/Hide sections
     
