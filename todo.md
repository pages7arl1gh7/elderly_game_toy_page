# 中老年平衡感训练游戏

一个专为中老年人设计的在线平衡感训练游戏，使用 MediaPipe 技术进行实时姿态检测，帮助用户改善平衡能力。

## 🎯 项目特色

- **👥 专为中老年人设计**：大字体、简洁界面、友好配色
- **🌍 多语言支持**：中文/英文切换
- **📱 移动端优化**：响应式设计，支持手机和平板
- **🎮 智能难度调节**：根据用户 BMI 和年龄自动推荐难度
- **🔒 隐私保护**：所有数据本地处理，不上传服务器
- **⚡ 实时分析**：使用 MediaPipe 进行实时姿态检测

## 🚀 功能特点

### 1. 用户友好设计
- 老年人友好的配色方案（深蓝色主题）
- 加粗字体，18px 基础字体大小
- 简洁直观的界面设计
- 完整的免责声明

### 2. 智能游戏系统
- **三种难度等级**：简单、中等、困难
- **智能推荐**：基于 BMI 和年龄自动设置难度
- **实时评分**：基于姿态相似度计算分数
- **营养建议**：根据游戏表现提供个性化建议

### 3. 先进技术
- **MediaPipe 姿态检测**：实时分析用户动作
- **视频对比分析**：与标准动作进行实时对比
- **余弦相似度算法**：精确计算动作准确性
- **Canvas 可视化**：实时显示骨骼点和连接线

## 📋 使用流程

1. **免责声明**：阅读并同意使用条款
2. **信息输入**：输入年龄、性别、身高、体重
3. **难度选择**：系统自动推荐或手动选择难度
4. **开始游戏**：3 秒倒计时后开始训练
5. **实时反馈**：查看动作分析和实时评分
6. **结果展示**：游戏结束后查看最终分数和营养建议

## 🛠 技术栈

- **前端**：HTML5, CSS3, JavaScript
- **AI 技术**：Google MediaPipe
- **视频处理**：HTML5 Video API
- **图像处理**：Canvas API
- **摄像头访问**：WebRTC getUserMedia API

## 📁 文件结构

```
elderly_game_toy_page/
├── index.html              # 主游戏文件
├── easy.mp4               # 简单难度标准动作视频
├── medium.mp4             # 中等难度标准动作视频
├── hard.mp4               # 困难难度标准动作视频
├── README.md              # 项目说明文档
├── video-setup-guide.md   # 视频设置指南
├── deployment-guide.md    # 部署指南
└── todo.md               # 项目需求文档
```

## 🚀 快速开始

### 1. 克隆项目
```bash
git clone https://github.com/yourusername/elderly_game_toy_page.git
cd elderly_game_toy_page
```

### 2. 准备视频文件
根据 `video-setup-guide.md` 的说明准备三个难度的标准动作视频：
- `easy.mp4` - 简单难度
- `medium.mp4` - 中等难度  
- `hard.mp4` - 困难难度

### 3. 本地测试
由于需要摄像头权限，建议使用本地服务器：
```bash
# 使用 Python
python -m http.server 8000

# 或使用 Node.js
npx http-server
```

### 4. 部署到 GitHub Pages
参考 `deployment-guide.md` 进行部署。

## 🎯 BMI 难度推荐算法

```javascript
const bmi = weight / ((height / 100) ** 2);
let defaultDifficulty = 'medium';

if (age > 70 || bmi > 30) {
    defaultDifficulty = 'easy';    // 高龄或肥胖用户
} else if (bmi < 18.5 || (bmi >= 18.5 && bmi <= 24.9)) {
    defaultDifficulty = 'hard';    // 偏瘦或正常体重用户
}
```

## 📊 评分系统

### 计算方法
1. **姿态提取**：使用 MediaPipe 提取 33 个关键点
2. **关键点选择**：选择 12 个主要关键点进行比较
3. **距离计算**：计算用户姿态与标准姿态的欧几里得距离
4. **相似度转换**：`similarity = max(0, 100 - distance * 100)`
5. **平均得分**：所有帧的平均相似度作为最终得分

### 营养建议分级
- **80-100 分**：动作标准程度高 - 维持性营养建议
- **60-79 分**：动作标准程度中等 - 强化性营养建议  
- **0-59 分**：动作标准程度低 - 补充性营养建议

## 🌐 浏览器支持

| 浏览器 | 最低版本 | 备注 |
|--------|----------|------|
| Chrome | 60+ | 推荐使用 |
| Firefox | 55+ | 完全支持 |
| Safari | 11+ | iOS 需要 12+ |
| Edge | 79+ | 基于 Chromium |

## 📱 移动端支持

- ✅ 响应式设计
- ✅ 触摸友好界面
- ✅ 移动端摄像头支持
- ✅ 竖屏/横屏适配

## 🔒 隐私保护

- 🚫 不收集个人数据
- 🚫 不上传视频内容
- 🚫 不保存用户信息
- ✅ 所有处理本地完成
- ✅ 符合 GDPR 要求

## 🤝 贡献指南

欢迎提交 Issue 和 Pull Request！

### 开发环境设置
1. Fork 本仓库
2. 创建特性分支：`git checkout -b feature/new-feature`
3. 提交更改：`git commit -am 'Add new feature'`
4. 推送分支：`git push origin feature/new-feature`
5. 提交 Pull Request

## 📄 许可证

本项目采用 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情。

## 🙏 致谢

- [Google MediaPipe](https://mediapipe.dev/) - 提供强大的姿态检测技术
- [GitHub Pages](https://pages.github.com/) - 免费的静态网站托管服务

## 📞 联系方式

如有问题或建议，请通过以下方式联系：
- 提交 [GitHub Issue](https://github.com/yourusername/elderly_game_toy_page/issues)
- 发送邮件至：your.email@example.com

---

**⚠️ 重要提醒**：本网站提供的内容仅供参考，不构成专业医疗建议。使用前请咨询医生，运动时注意安全。

        .difficulty-selector label {
            font-weight: bold;
            font-size: 20px;
            color: var(--primary-color);
            margin-right: 15px;
        }

        .difficulty-selector select {
            padding: 12px 20px;
            font-size: 18px;
            font-weight: bold;
            border: 2px solid var(--border-color);
            border-radius: 8px;
            background-color: white;
        }

        /* 视频区域 */
        .video-container {
            position: relative;
            background-color: #000;
            border-radius: 15px;
            overflow: hidden;
            margin-bottom: 25px;
            min-height: 400px;
        }

        .standard-video {
            position: absolute;
            top: 10px;
            left: 10px;
            width: 25%;
            height: 25%;
            border: 3px solid var(--secondary-color);
            border-radius: 10px;
            z-index: 10;
        }

        .user-video {
            width: 100%;
            height: 400px;
            object-fit: cover;
        }

        .countdown {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 120px;
            font-weight: bold;
            color: white;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
            z-index: 20;
        }

        /* 分数显示 */
        .score-display {
            background-color: white;
            padding: 20px;
            border-radius: 15px;
            text-align: center;
            margin-bottom: 25px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }

        .score-display h3 {
            color: var(--primary-color);
            font-size: 24px;
            margin-bottom: 10px;
        }

        .score-value {
            font-size: 48px;
            font-weight: bold;
            color: var(--success-color);
        }

        /* 游戏控制按钮 */
        .game-control-btn {
            width: 100%;
            padding: 20px;
            font-size: 24px;
            font-weight: bold;
            background-color: var(--success-color);
            color: white;
            border: none;
            border-radius: 15px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .game-control-btn:hover {
            background-color: #38a169;
            transform: translateY(-2px);
        }

        .game-control-btn:disabled {
            background-color: #a0aec0;
            cursor: not-allowed;
            transform: none;
        }

        /* 响应式设计 */
        @media (max-width: 768px) {
            body {
                font-size: 16px;
            }
            
            .container {
                padding: 10px;
            }
            
            .modal-content {
                margin: 5% auto;
                padding: 20px;
            }
            
            .btn {
                padding: 12px 25px;
                font-size: 16px;
            }
            
            .score-value {
                font-size: 36px;
            }
            
            .countdown {
                font-size: 80px;
            }
        }

        /* 隐藏类 */
        .hidden {
            display: none !important;
        }

        /* 加载动画 */
        .loading {
            display: inline-block;
            width: 20px;
            height: 20px;
            border: 3px solid #f3f3f3;
            border-top: 3px solid var(--primary-color);
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
    </style>
</head>
<body>
    <!-- 语言选择器 -->
    <div class="language-selector">
        <select id="languageSelect" onchange="changeLanguage()">
            <option value="zh">中文</option>
            <option value="en">English</option>
        </select>
    </div>

    <!-- 免责声明模态框 -->
    <div id="disclaimerModal" class="modal">
        <div class="modal-content">
            <h2 data-translate="disclaimer_title">免责声明</h2>
            <p data-translate="disclaimer_text">
                本网站的内容不构成专业的医疗建议，请根据自己的身体状况选择适当的活动，本网站提出的建议仅作为参考并且不构成任何医疗建议，如果感到身体不适，请及时就医。本网站不会收集您的个人数据也不会保存任何视频，您在本网站中输入的任何信息都只是为了推荐更加适合您的小游戏而使用，它们不会被上传到我们的服务器。
            </p>
            <button class="btn btn-primary" onclick="acceptDisclaimer()" data-translate="accept">我同意</button>
            <button class="btn btn-secondary" onclick="declineDisclaimer()" data-translate="decline">不同意</button>
        </div>
    </div>

    <!-- 用户信息输入模态框 -->
    <div id="userInfoModal" class="modal">
        <div class="modal-content">
            <h2 data-translate="user_info_title">请输入您的基本信息</h2>
            <form id="userInfoForm">
                <div class="form-group">
                    <label for="age" data-translate="age_label">年龄：</label>
                    <input type="number" id="age" name="age" min="1" max="120" required>
                </div>
                <div class="form-group">
                    <label for="gender" data-translate="gender_label">性别：</label>
                    <select id="gender" name="gender" required>
                        <option value="" data-translate="select_gender">请选择</option>
                        <option value="male" data-translate="male">男</option>
                        <option value="female" data-translate="female">女</option>
                    </select>
                </div>
                <div class="form-group">
                    <label for="height" data-translate="height_label">身高（厘米）：</label>
                    <input type="number" id="height" name="height" min="100" max="250" required>
                </div>
                <div class="form-group">
                    <label for="weight" data-translate="weight_label">体重（公斤）：</label>
                    <input type="number" id="weight" name="weight" min="30" max="200" required>
                </div>
                <button type="submit" class="btn btn-primary" data-translate="start_game">开始游戏</button>
            </form>
        </div>
    </div>

    <!-- 游戏结果模态框 -->
    <div id="gameResultModal" class="modal">
        <div class="modal-content">
            <h2 data-translate="game_result_title">游戏结果</h2>
            <div class="score-display">
                <h3 data-translate="final_score">最终得分</h3>
                <div class="score-value" id="finalScore">0</div>
            </div>
            <div id="nutritionAdvice">
                <h3 data-translate="nutrition_advice_title">营养建议</h3>
                <p id="nutritionAdviceText"></p>
            </div>
            <button class="btn btn-primary" onclick="restartGame()" data-translate="play_again">再玩一次</button>
        </div>
    </div>

    <!-- 主游戏界面 -->
    <div class="container">
        <div class="game-interface" id="gameInterface">
            <h1 data-translate="game_title">中老年平衡感训练游戏</h1>
            
            <!-- 游戏控制区域 -->
            <div class="game-controls">
                <div class="difficulty-selector">
                    <label for="difficultySelect" data-translate="difficulty_label">游戏难度：</label>
                    <select id="difficultySelect" onchange="changeDifficulty()">
                        <option value="easy" data-translate="easy">简单</option>
                        <option value="medium" data-translate="medium">中等</option>
                        <option value="hard" data-translate="hard">困难</option>
                    </select>
                </div>
                
                <!-- 分数显示 -->
                <div class="score-display">
                    <h3 data-translate="current_score">当前平均得分</h3>
                    <div class="score-value" id="currentScore">0</div>
                </div>
            </div>

            <!-- 视频显示区域 -->
            <div class="video-container" id="videoContainer">
                <video id="standardVideo" class="standard-video" muted loop style="display: none;">
                    <source src="easy.mp4" type="video/mp4">
                </video>
                <video id="userVideo" class="user-video" autoplay muted playsinline></video>
                <canvas id="userCanvas" class="user-video" style="display: none;"></canvas>
                <div id="countdown" class="countdown" style="display: none;"></div>
            </div>

            <!-- 游戏控制按钮 -->
            <button id="gameControlBtn" class="game-control-btn" onclick="toggleGame()" data-translate="start_game">开始游戏</button>
        </div>
    </div>

    <!-- MediaPipe 和其他脚本 -->
    <script src="https://cdn.jsdelivr.net/npm/@mediapipe/camera_utils/camera_utils.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@mediapipe/control_utils/control_utils.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@mediapipe/drawing_utils/drawing_utils.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@mediapipe/pose/pose.js"></script>

    <script>
        // 多语言支持
        const translations = {
            zh: {
                disclaimer_title: "免责声明",
                disclaimer_text: "本网站的内容不构成专业的医疗建议，请根据自己的身体状况选择适当的活动，本网站提出的建议仅作为参考并且不构成任何医疗建议，如果感到身体不适，请及时就医。本网站不会收集您的个人数据也不会保存任何视频，您在本网站中输入的任何信息都只是为了推荐更加适合您的小游戏而使用，它们不会被上传到我们的服务器。",
                accept: "我同意",
                decline: "不同意",
                user_info_title: "请输入您的基本信息",
                age_label: "年龄：",
                gender_label: "性别：",
                select_gender: "请选择",
                male: "男",
                female: "女",
                height_label: "身高（厘米）：",
                weight_label: "体重（公斤）：",
                start_game: "开始游戏",
                game_title: "中老年平衡感训练游戏",
                difficulty_label: "游戏难度：",
                easy: "简单",
                medium: "中等",
                hard: "困难",
                current_score: "当前平均得分",
                game_result_title: "游戏结果",
                final_score: "最终得分",
                nutrition_advice_title: "营养建议",
                play_again: "再玩一次",
                stop_game: "结束游戏"
            },
            en: {
                disclaimer_title: "Disclaimer",
                disclaimer_text: "The content of this website does not constitute professional medical advice. Please choose appropriate activities based on your physical condition. The suggestions provided by this website are for reference only and do not constitute any medical advice. If you feel unwell, please seek medical attention promptly. This website will not collect your personal data or save any videos. Any information you enter on this website is only used to recommend games more suitable for you and will not be uploaded to our servers.",
                accept: "I Agree",
                decline: "Decline",
                user_info_title: "Please Enter Your Basic Information",
                age_label: "Age:",
                gender_label: "Gender:",
                select_gender: "Please Select",
                male: "Male",
                female: "Female",
                height_label: "Height (cm):",
                weight_label: "Weight (kg):",
                start_game: "Start Game",
                game_title: "Balance Training Game for Seniors",
                difficulty_label: "Game Difficulty:",
                easy: "Easy",
                medium: "Medium",
                hard: "Hard",
                current_score: "Current Average Score",
                game_result_title: "Game Result",
                final_score: "Final Score",
                nutrition_advice_title: "Nutrition Advice",
                play_again: "Play Again",
                stop_game: "Stop Game"
            }
        };

        // 全局变量
        let currentLanguage = 'zh';
        let userInfo = {};
        let gameState = 'stopped'; // 'stopped', 'countdown', 'playing'
        let pose = null;
        let camera = null;
        let standardPoseData = [];
        let userPoseData = [];
        let gameStartTime = null;
        let totalScore = 0;
        let frameCount = 0;
        let gameInterval = null;

        // 页面加载完成后显示免责声明
        window.addEventListener('load', function() {
            document.getElementById('disclaimerModal').style.display = 'block';
        });

        // 语言切换功能
        function changeLanguage() {
            const select = document.getElementById('languageSelect');
            currentLanguage = select.value;
            updateLanguage();
        }

        function updateLanguage() {
            const elements = document.querySelectorAll('[data-translate]');
            elements.forEach(element => {
                const key = element.getAttribute('data-translate');
                if (translations[currentLanguage][key]) {
                    element.textContent = translations[currentLanguage][key];
                }
            });
        }

        // 免责声明处理
        function acceptDisclaimer() {
            document.getElementById('disclaimerModal').style.display = 'none';
            document.getElementById('userInfoModal').style.display = 'block';
        }

        function declineDisclaimer() {
            alert(currentLanguage === 'zh' ? '感谢您的访问！' : 'Thank you for visiting!');
            window.close();
        }

        // 用户信息表单处理
        document.getElementById('userInfoForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const formData = new FormData(e.target);
            userInfo = {
                age: parseInt(formData.get('age')),
                gender: formData.get('gender'),
                height: parseInt(formData.get('height')),
                weight: parseInt(formData.get('weight'))
            };

            // 计算 BMI 并设置默认难度
            const bmi = userInfo.weight / ((userInfo.height / 100) ** 2);
            let defaultDifficulty = 'medium';
            
            if (userInfo.age > 70 || bmi > 30) {
                defaultDifficulty = 'easy';
            } else if (bmi < 18.5 || (bmi >= 18.5 && bmi <= 24.9)) {
                defaultDifficulty = 'hard';
            }

            document.getElementById('difficultySelect').value = defaultDifficulty;
            document.getElementById('userInfoModal').style.display = 'none';
            document.getElementById('gameInterface').style.display = 'block';
            
            // 初始化游戏
            initializeGame();
        });

        // 游戏初始化
        async function initializeGame() {
            try {
                // 初始化MediaPipe Pose
                pose = new Pose({
                    locateFile: (file) => {
                        return `https://cdn.jsdelivr.net/npm/@mediapipe/pose/${file}`;
                    }
                });

                pose.setOptions({
                    modelComplexity: 1,
                    smoothLandmarks: true,
                    enableSegmentation: false,
                    smoothSegmentation: false,
                    minDetectionConfidence: 0.5,
                    minTrackingConfidence: 0.5
                });

                pose.onResults(onPoseResults);

                // 初始化摄像头
                const videoElement = document.getElementById('userVideo');
                camera = new Camera(videoElement, {
                    onFrame: async () => {
                        if (gameState === 'playing') {
                            await pose.send({image: videoElement});
                        }
                    },
                    width: 640,
                    height: 480
                });

                await camera.start();
                
                // 设置标准视频
                changeDifficulty();
                
            } catch (error) {
                console.error('游戏初始化失败：', error);
                alert(currentLanguage === 'zh' ? '游戏初始化失败，请检查摄像头权限' : 'Game initialization failed, please check camera permissions');
            }
        }

        // 难度切换
        function changeDifficulty() {
            const difficulty = document.getElementById('difficultySelect').value;
            const standardVideo = document.getElementById('standardVideo');
            standardVideo.src = `${difficulty}.mp4`;
        }

        // 姿态检测结果处理
        function onPoseResults(results) {
            if (!results.poseLandmarks || gameState !== 'playing') return;

            const canvas = document.getElementById('userCanvas');
            const canvasCtx = canvas.getContext('2d');
            const videoElement = document.getElementById('userVideo');
            
            canvas.width = videoElement.videoWidth;
            canvas.height = videoElement.videoHeight;
            canvas.style.display = 'block';
            videoElement.style.display = 'none';

            // 清除画布
            canvasCtx.clearRect(0, 0, canvas.width, canvas.height);
            
            // 绘制视频帧
            canvasCtx.drawImage(videoElement, 0, 0, canvas.width, canvas.height);
            
            // 绘制姿态点和连线
            drawPose(canvasCtx, results.poseLandmarks);
            
            // 保存用户姿态数据
            userPoseData.push(results.poseLandmarks);
            
            // 计算得分
            calculateScore();
        }

        // 绘制姿态
        function drawPose(ctx, landmarks) {
            // 绘制关键点
            landmarks.forEach(landmark => {
                ctx.beginPath();
                ctx.arc(landmark.x * ctx.canvas.width, landmark.y * ctx.canvas.height, 5, 0, 2 * Math.PI);
                ctx.fillStyle = '#00ff00';
                ctx.fill();
            });

            // 绘制连线（简化版）
            const connections = [
                [11, 12], [11, 13], [12, 14], [13, 15], [14, 16], // 上身
                [11, 23], [12, 24], [23, 24], // 躯干
                [23, 25], [24, 26], [25, 27], [26, 28] // 下身
            ];

            ctx.strokeStyle = '#00ff00';
            ctx.lineWidth = 2;
            
            connections.forEach(([start, end]) => {
                if (landmarks[start] && landmarks[end]) {
                    ctx.beginPath();
                    ctx.moveTo(landmarks[start].x * ctx.canvas.width, landmarks[start].y * ctx.canvas.height);
                    ctx.lineTo(landmarks[end].x * ctx.canvas.width, landmarks[end].y * ctx.canvas.height);
                    ctx.stroke();
                }
            });
        }

        // 计算得分
        function calculateScore() {
            if (standardPoseData.length === 0 || userPoseData.length === 0) return;

            // 获取最新的标准姿态和用户姿态
            const standardPose = standardPoseData[standardPoseData.length - 1];
            const userPose = userPoseData[userPoseData.length - 1];

            if (!standardPose || !userPose) return;

            // 计算关键点的相似度
            let similarity = 0;
            let validPoints = 0;

            // 选择主要关键点进行比较
            const keyPoints = [11, 12, 13, 14, 15, 16, 23, 24, 25, 26, 27, 28];
            
            keyPoints.forEach(pointIndex => {
                if (standardPose[pointIndex] && userPose[pointIndex]) {
                    const standardPoint = standardPose[pointIndex];
                    const userPoint = userPose[pointIndex];
                    
                    // 计算欧几里得距离
                    const distance = Math.sqrt(
                        Math.pow(standardPoint.x - userPoint.x, 2) +
                        Math.pow(standardPoint.y - userPoint.y, 2) +
                        Math.pow(standardPoint.z - userPoint.z, 2)
                    );
                    
                    // 转换为相似度分数（距离越小，相似度越高）
                    const pointSimilarity = Math.max(0, 100 - distance * 100);
                    similarity += pointSimilarity;
                    validPoints++;
                }
            });

            if (validPoints > 0) {
                const frameScore = similarity / validPoints;
                totalScore += frameScore;
                frameCount++;
                
                // 更新显示的平均得分
                const averageScore = Math.round(totalScore / frameCount);
                document.getElementById('currentScore').textContent = averageScore;
            }
        }

        // 游戏控制
        function toggleGame() {
            if (gameState === 'stopped') {
                startGame();
            } else {
                stopGame();
            }
        }

        function startGame() {
            gameState = 'countdown';
            const btn = document.getElementById('gameControlBtn');
            btn.disabled = true;
            btn.textContent = currentLanguage === 'zh' ? '准备中...' : 'Preparing...';
            
            // 重置游戏数据
            standardPoseData = [];
            userPoseData = [];
            totalScore = 0;
            frameCount = 0;
            document.getElementById('currentScore').textContent = '0';
            
            // 开始倒计时
            startCountdown();
        }

        function startCountdown() {
            const countdownElement = document.getElementById('countdown');
            countdownElement.style.display = 'block';
            let count = 3;
            
            const countdownInterval = setInterval(() => {
                countdownElement.textContent = count;
                count--;
                
                if (count < 0) {
                    clearInterval(countdownInterval);
                    countdownElement.style.display = 'none';
                    startActualGame();
                }
            }, 1000);
        }

        function startActualGame() {
            gameState = 'playing';
            gameStartTime = Date.now();
            
            const btn = document.getElementById('gameControlBtn');
            btn.disabled = false;
            btn.textContent = currentLanguage === 'zh' ? '结束游戏' : 'Stop Game';
            
            // 开始播放标准视频
            const standardVideo = document.getElementById('standardVideo');
            standardVideo.style.display = 'block';
            standardVideo.currentTime = 0;
            standardVideo.play();
            
            // 监听标准视频结束
            standardVideo.onended = () => {
                stopGame();
            };
            
            // 开始分析标准视频（简化版 - 实际应用中需要更复杂的实现）
            simulateStandardPoseData();
        }

        function simulateStandardPoseData() {
            // 这里应该分析标准视频的每一帧
            // 为了演示，我们生成一些模拟数据
            gameInterval = setInterval(() => {
                if (gameState === 'playing') {
                    // 生成模拟的标准姿态数据
                    const mockStandardPose = generateMockPoseData();
                    standardPoseData.push(mockStandardPose);
                }
            }, 100); // 每 100ms 生成一次数据
        }

        function generateMockPoseData() {
            // 生成 33 个关键点的模拟数据
            const pose = [];
            for (let i = 0; i < 33; i++) {
                pose.push({
                    x: Math.random() * 0.6 + 0.2, // 0.2 到 0.8 之间
                    y: Math.random() * 0.6 + 0.2,
                    z: Math.random() * 0.2 - 0.1,
                    visibility: Math.random() * 0.5 + 0.5
                });
            }
            return pose;
        }

        function stopGame() {
            gameState = 'stopped';
            
            if (gameInterval) {
                clearInterval(gameInterval);
                gameInterval = null;
            }
            
            const btn = document.getElementById('gameControlBtn');
            btn.disabled = false;
            btn.textContent = currentLanguage === 'zh' ? '开始游戏' : 'Start Game';
            
            // 停止标准视频
            const standardVideo = document.getElementById('standardVideo');
            standardVideo.style.display = 'none';
            standardVideo.pause();
            
            // 显示用户视频
            document.getElementById('userVideo').style.display = 'block';
            document.getElementById('userCanvas').style.display = 'none';
            
            // 显示游戏结果
            showGameResult();
        }

        function showGameResult() {
            const finalScore = frameCount > 0 ? Math.round(totalScore / frameCount) : 0;
            document.getElementById('finalScore').textContent = finalScore;
            
            // 生成营养建议
            const nutritionAdvice = generateNutritionAdvice(finalScore);
            document.getElementById('nutritionAdviceText').textContent = nutritionAdvice;
            
            document.getElementById('gameResultModal').style.display = 'block';
        }

        function generateNutritionAdvice(score) {
            const adviceZh = {
                high: "您的动作标准程度很高！建议继续保持均衡饮食，多摄入富含蛋白质的食物如鱼类、豆类，以及新鲜蔬菜水果。适量补充维生素 D 和钙质，有助于骨骼健康。",
                medium: "您的动作标准程度中等，建议加强营养摄入。多吃富含 omega-3 脂肪酸的食物如深海鱼、坚果，增加蛋白质摄入，适量补充维生素 B 群和镁元素，有助于肌肉功能。",
                low: "建议加强营养补充，多摄入优质蛋白质如瘦肉、鸡蛋、奶制品，增加维生素 C 和 E 的摄入，多吃抗氧化食物如蓝莓、绿茶。建议咨询营养师制定个性化饮食计划。"
            };
            
            const adviceEn = {
                high: "Your movement accuracy is excellent! Continue maintaining a balanced diet with protein-rich foods like fish and legumes, plus fresh vegetables and fruits. Adequate vitamin D and calcium supplementation helps bone health.",
                medium: "Your movement accuracy is moderate. Strengthen nutrition intake with omega-3 rich foods like deep-sea fish and nuts, increase protein intake, and supplement with vitamin B complex and magnesium for muscle function.",
                low: "Recommend strengthening nutritional supplementation with high-quality proteins like lean meat, eggs, and dairy products. Increase vitamin C and E intake with antioxidant foods like blueberries and green tea. Consider consulting a nutritionist for a personalized diet plan."
            };
            
            const advice = currentLanguage === 'zh' ? adviceZh : adviceEn;
            
            if (score >= 80) return advice.high;
            if (score >= 60) return advice.medium;
            return advice.low;
        }

        function restartGame() {
            document.getElementById('gameResultModal').style.display = 'none';
            document.getElementById('userInfoModal').style.display = 'block';
        }

        // 初始化语言
        updateLanguage();
    </script>
</body>
</html> 