<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>小浣熊丛林探险</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #5d4037; /* 深棕色背景 */
            color: #fff;
            overflow: hidden;
            height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            position: relative;
        }
        
        .game-container {
            width: 90%;
            max-width: 1000px;
            height: 85vh;
            background-color: #8d6e63; /* 棕色容器 */
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
            display: flex;
            flex-direction: column;
            overflow: hidden;
            position: relative;
            border: 8px solid #a1887f;
        }
        
        .game-header {
            background-color: #6d4c41; /* 深棕色头部 */
            padding: 15px 25px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 5px solid #ffcc80; /* 明亮黄色边框 */
        }
        
        .logo {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .logo i {
            color: #ffcc80;
            font-size: 2rem;
        }
        
        .logo h1 {
            font-size: 1.8rem;
            color: #fff;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
        }
        
        .stats {
            display: flex;
            gap: 20px;
        }
        
        .stat {
            background-color: #5d4037;
            padding: 8px 15px;
            border-radius: 20px;
            display: flex;
            align-items: center;
            gap: 8px;
            font-weight: bold;
            color: #ffcc80;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.2);
        }
        
        .main-content {
            display: flex;
            flex: 1;
            padding: 20px;
            gap: 20px;
        }
        
        .game-area {
            flex: 2;
            background-color: #795548;
            border-radius: 15px;
            position: relative;
            overflow: hidden;
            box-shadow: inset 0 0 20px rgba(0, 0, 0, 0.3);
        }
        
        .forest-bg {
            width: 100%;
            height: 100%;
            background-image: url('https://images.unsplash.com/photo-1505142468610-359e7d316be0?q=80&w=2000&auto=format&fit=crop');
            background-size: cover;
            background-position: center;
            opacity: 0.7;
        }
        
        .raccoon {
            position: absolute;
            width: 120px;
            height: 120px;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            transition: all 0.3s ease;
            cursor: pointer;
            z-index: 10;
        }
        
        .raccoon img {
            width: 100%;
            height: 100%;
            object-fit: contain;
        }
        
        .collectible {
            position: absolute;
            width: 50px;
            height: 50px;
            cursor: pointer;
            animation: float 3s infinite ease-in-out;
            z-index: 5;
        }
        
        .collectible img {
            width: 100%;
            height: 100%;
            object-fit: contain;
        }
        
        .side-panel {
            flex: 1;
            display: flex;
            flex-direction: column;
            gap: 20px;
        }
        
        .control-panel {
            background-color: #6d4c41;
            border-radius: 15px;
            padding: 20px;
            display: flex;
            flex-direction: column;
            gap: 15px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
        }
        
        .control-panel h2 {
            color: #ffcc80;
            text-align: center;
            margin-bottom: 10px;
            font-size: 1.5rem;
        }
        
        .btn {
            background-color: #ffb74d;
            color: #5d4037;
            border: none;
            padding: 12px;
            border-radius: 10px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            font-size: 1rem;
        }
        
        .btn:hover {
            background-color: #ffa726;
            transform: translateY(-3px);
            box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
        }
        
        .btn:active {
            transform: translateY(0);
        }
        
        .btn.secondary {
            background-color: #81c784; /* 明亮的绿色 */
            color: #1b5e20;
        }
        
        .btn.secondary:hover {
            background-color: #66bb6a;
        }
        
        .btn.danger {
            background-color: #ff8a65; /* 明亮的橙色 */
            color: #bf360c;
        }
        
        .btn.danger:hover {
            background-color: #ff7043;
        }
        
        .inventory {
            background-color: #6d4c41;
            border-radius: 15px;
            padding: 20px;
            flex: 1;
            display: flex;
            flex-direction: column;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
        }
        
        .inventory h2 {
            color: #ffcc80;
            text-align: center;
            margin-bottom: 15px;
            font-size: 1.5rem;
        }
        
        .inventory-items {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            justify-content: center;
            align-content: flex-start;
        }
        
        .inventory-item {
            width: 60px;
            height: 60px;
            background-color: #8d6e63;
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.8rem;
            box-shadow: inset 0 0 5px rgba(0, 0, 0, 0.3);
        }
        
        .music-controls {
            position: absolute;
            bottom: 20px;
            right: 20px;
            display: flex;
            flex-direction: column;
            gap: 10px;
            z-index: 20;
        }
        
        .music-btn {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background-color: #ffcc80;
            border: none;
            color: #5d4037;
            font-size: 1.5rem;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 5px 10px rgba(0, 0, 0, 0.3);
            transition: all 0.3s;
        }
        
        .music-btn:hover {
            transform: scale(1.1);
            background-color: #ffb74d;
        }
        
        .game-message {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background-color: rgba(0, 0, 0, 0.8);
            padding: 20px 40px;
            border-radius: 15px;
            font-size: 2rem;
            color: #ffcc80;
            z-index: 100;
            display: none;
            text-align: center;
            border: 3px solid #ffcc80;
        }
        
        .collectible-count {
            position: absolute;
            top: 10px;
            right: 10px;
            background-color: rgba(0, 0, 0, 0.7);
            color: #ffcc80;
            padding: 5px 10px;
            border-radius: 10px;
            font-weight: bold;
            z-index: 10;
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-15px); }
        }
        
        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-20px); }
        }
        
        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.1); }
        }
        
        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            25% { transform: translateX(-5px); }
            75% { transform: translateX(5px); }
        }
        
        .bounce {
            animation: bounce 0.5s;
        }
        
        .pulse {
            animation: pulse 0.5s;
        }
        
        .shake {
            animation: shake 0.5s;
        }
        
        .instructions {
            position: absolute;
            top: 20px;
            left: 20px;
            background-color: rgba(0, 0, 0, 0.7);
            color: #fff;
            padding: 15px;
            border-radius: 10px;
            max-width: 300px;
            z-index: 10;
            border-left: 5px solid #ffcc80;
        }
        
        .instructions h3 {
            color: #ffcc80;
            margin-bottom: 10px;
        }
        
        .instructions p {
            margin-bottom: 8px;
            font-size: 0.9rem;
        }
        
        @media (max-width: 768px) {
            .main-content {
                flex-direction: column;
            }
            
            .game-container {
                height: 95vh;
            }
            
            .side-panel {
                flex-direction: row;
            }
            
            .inventory {
                flex: 2;
            }
        }
    </style>
</head>
<body>
    <div class="game-container">
        <div class="game-header">
            <div class="logo">
                <i class="fas fa-paw"></i>
                <h1>小浣熊丛林探险</h1>
            </div>
            <div class="stats">
                <div class="stat" id="score">
                    <i class="fas fa-star"></i>
                    <span>分数: <span id="score-value">0</span></span>
                </div>
                <div class="stat" id="time">
                    <i class="fas fa-clock"></i>
                    <span>时间: <span id="time-value">60</span>秒</span>
                </div>
                <div class="stat" id="lives">
                    <i class="fas fa-heart"></i>
                    <span>生命: <span id="lives-value">3</span></span>
                </div>
            </div>
        </div>
        
        <div class="main-content">
            <div class="game-area">
                <div class="forest-bg"></div>
                <div class="instructions">
                    <h3>游戏说明</h3>
                    <p>1. 点击小浣熊让它跳跃</p>
                    <p>2. 收集水果和坚果获得分数</p>
                    <p>3. 躲避危险的蘑菇</p>
                    <p>4. 收集特殊物品获得额外奖励</p>
                </div>
                <div class="collectible-count">已收集: <span id="collected-count">0</span>/10</div>
                <div class="raccoon" id="raccoon">
                    <img src="https://cdn-icons-png.flaticon.com/512/1998/1998610.png" alt="小浣熊">
                </div>
                <!-- 收集物将由JavaScript动态生成 -->
            </div>
            
            <div class="side-panel">
                <div class="control-panel">
                    <h2>游戏控制</h2>
                    <button class="btn" id="start-btn">
                        <i class="fas fa-play"></i> 开始游戏
                    </button>
                    <button class="btn secondary" id="jump-btn">
                        <i class="fas fa-arrow-up"></i> 小浣熊跳跃
                    </button>
                    <button class="btn" id="add-item-btn">
                        <i class="fas fa-plus"></i> 添加收集物
                    </button>
                    <button class="btn secondary" id="special-power">
                        <i class="fas fa-bolt"></i> 使用特殊能力
                    </button>
                    <button class="btn danger" id="reset-btn">
                        <i class="fas fa-redo"></i> 重置游戏
                    </button>
                </div>
                
                <div class="inventory">
                    <h2>收集品仓库</h2>
                    <div class="inventory-items" id="inventory">
                        <!-- 收集品将由JavaScript动态生成 -->
                    </div>
                </div>
            </div>
        </div>
        
        <div class="music-controls">
            <button class="music-btn" id="music-toggle">
                <i class="fas fa-music"></i>
            </button>
            <button class="music-btn" id="sound-toggle">
                <i class="fas fa-volume-up"></i>
            </button>
        </div>
        
        <div class="game-message" id="game-message"></div>
    </div>

    <!-- 背景音乐 -->
    <audio id="background-music" loop>
        <source src="https://assets.mixkit.co/music/preview/mixkit-clear-sky-479.mp3" type="audio/mpeg">
    </audio>
    
    <!-- 音效 -->
    <audio id="collect-sound" src="https://assets.mixkit.co/sfx/preview/mixkit-unlock-game-notification-253.mp3"></audio>
    <audio id="jump-sound" src="https://assets.mixkit.co/sfx/preview/mixkit-jump-arcade-game-166.mp3"></audio>
    <audio id="power-sound" src="https://assets.mixkit.co/sfx/preview/mixkit-magic-sparkles-300.mp3"></audio>
    
    <script>
        // 游戏变量
        let score = 0;
        let lives = 3;
        let timeLeft = 60;
        let gameActive = false;
        let gameTimer = null;
        let collectibles = [];
        let inventory = [];
        let musicPlaying = true;
        let soundEnabled = true;
        let collectedCount = 0;
        let specialPowerAvailable = true;
        
        // DOM元素
        const raccoon = document.getElementById('raccoon');
        const gameArea = document.querySelector('.game-area');
        const startBtn = document.getElementById('start-btn');
        const jumpBtn = document.getElementById('jump-btn');
        const addItemBtn = document.getElementById('add-item-btn');
        const specialPowerBtn = document.getElementById('special-power');
        const resetBtn = document.getElementById('reset-btn');
        const musicToggle = document.getElementById('music-toggle');
        const soundToggle = document.getElementById('sound-toggle');
        const backgroundMusic = document.getElementById('background-music');
        const collectSound = document.getElementById('collect-sound');
        const jumpSound = document.getElementById('jump-sound');
        const powerSound = document.getElementById('power-sound');
        const gameMessage = document.getElementById('game-message');
        const scoreValue = document.getElementById('score-value');
        const timeValue = document.getElementById('time-value');
        const livesValue = document.getElementById('lives-value');
        const inventoryEl = document.getElementById('inventory');
        const collectedCountEl = document.getElementById('collected-count');
        
        // 收集物类型
        const collectibleTypes = [
            { icon: '🍎', name: '苹果', points: 10, color: '#f44336' },
            { icon: '🌰', name: '坚果', points: 15, color: '#795548' },
            { icon: '🍇', name: '葡萄', points: 8, color: '#9c27b0' },
            { icon: '🍄', name: '蘑菇', points: -20, color: '#4caf50', dangerous: true },
            { icon: '⭐', name: '星星', points: 30, color: '#ffeb3b' },
            { icon: '🍯', name: '蜂蜜', points: 25, color: '#ff9800' }
        ];
        
        // 初始化游戏
        function initGame() {
            // 重置游戏变量
            score = 0;
            lives = 3;
            timeLeft = 60;
            collectedCount = 0;
            gameActive = false;
            specialPowerAvailable = true;
            collectibles = [];
            inventory = [];
            
            // 更新UI
            updateUI();
            
            // 清空游戏区域
            document.querySelectorAll('.collectible').forEach(el => el.remove());
            
            // 清空仓库
            inventoryEl.innerHTML = '';
            
            // 停止游戏计时器
            if (gameTimer) {
                clearInterval(gameTimer);
                gameTimer = null;
            }
            
            // 显示开始消息
            showMessage("点击开始游戏！", "#ffcc80");
        }
        
        // 开始游戏
        function startGame() {
            if (gameActive) return;
            
            gameActive = true;
            startBtn.innerHTML = '<i class="fas fa-pause"></i> 暂停游戏';
            
            // 开始游戏计时器
            gameTimer = setInterval(() => {
                timeLeft--;
                timeValue.textContent = timeLeft;
                
                if (timeLeft <= 0) {
                    endGame(false);
                }
            }, 1000);
            
            // 随机生成收集物
            generateCollectibles();
            
            // 隐藏消息
            hideMessage();
        }
        
        // 暂停/继续游戏
        function togglePause() {
            if (!gameActive) return;
            
            if (gameTimer) {
                clearInterval(gameTimer);
                gameTimer = null;
                gameActive = false;
                startBtn.innerHTML = '<i class="fas fa-play"></i> 继续游戏';
                showMessage("游戏已暂停", "#ffcc80");
            } else {
                gameActive = true;
                startBtn.innerHTML = '<i class="fas fa-pause"></i> 暂停游戏';
                gameTimer = setInterval(() => {
                    timeLeft--;
                    timeValue.textContent = timeLeft;
                    
                    if (timeLeft <= 0) {
                        endGame(false);
                    }
                }, 1000);
                hideMessage();
            }
        }
        
        // 生成收集物
        function generateCollectibles() {
            if (!gameActive) return;
            
            // 清除现有的收集物
            collectibles.forEach(item => {
                if (item.element && item.element.parentNode) {
                    item.element.remove();
                }
            });
            
            collectibles = [];
            
            // 生成新的收集物
            for (let i = 0; i < 8; i++) {
                setTimeout(() => {
                    if (!gameActive) return;
                    
                    const type = collectibleTypes[Math.floor(Math.random() * collectibleTypes.length)];
                    createCollectible(type);
                }, i * 500);
            }
        }
        
        // 创建收集物
        function createCollectible(type) {
            const collectible = document.createElement('div');
            collectible.className = 'collectible';
            
            // 随机位置
            const x = Math.random() * (gameArea.offsetWidth - 60);
            const y = Math.random() * (gameArea.offsetHeight - 120);
            
            collectible.style.left = `${x}px`;
            collectible.style.top = `${y}px`;
            
            // 设置图标
            collectible.innerHTML = `<div style="font-size: 2.5rem; text-align: center;">${type.icon}</div>`;
            collectible.title = type.name;
            
            // 如果是危险物品，添加动画
            if (type.dangerous) {
                collectible.classList.add('shake');
            }
            
            // 点击事件
            collectible.addEventListener('click', () => collectItem(collectible, type));
            
            gameArea.appendChild(collectible);
            
            // 保存到数组
            collectibles.push({
                element: collectible,
                type: type,
                x: x,
                y: y
            });
        }
        
        // 收集物品
        function collectItem(collectibleElement, type) {
            if (!gameActive) return;
            
            // 播放音效
            if (soundEnabled) {
                collectSound.currentTime = 0;
                collectSound.play();
            }
            
            // 添加收集动画
            collectibleElement.style.transform = 'scale(0)';
            collectibleElement.style.transition = 'transform 0.3s';
            
            // 更新分数
            score += type.points;
            
            // 如果是危险物品，减少生命值
            if (type.dangerous) {
                lives--;
                showMessage(`危险！${type.name} 扣除了${-type.points}分！`, "#ff5252");
                raccoon.classList.add('shake');
                setTimeout(() => raccoon.classList.remove('shake'), 500);
                
                if (lives <= 0) {
                    endGame(false);
                }
            } else {
                // 添加到仓库
                inventory.push(type);
                collectedCount++;
                updateInventory();
                
                // 显示收集消息
                showMessage(`收集到 ${type.icon} ${type.name}！+${type.points}分`, type.color);
                
                // 小浣熊动画
                raccoon.classList.add('pulse');
                setTimeout(() => raccoon.classList.remove('pulse'), 300);
            }
            
            // 更新UI
            updateUI();
            
            // 移除元素
            setTimeout(() => {
                if (collectibleElement.parentNode) {
                    collectibleElement.remove();
                }
            }, 300);
            
            // 检查是否获胜
            if (collectedCount >= 10) {
                endGame(true);
            }
        }
        
        // 小浣熊跳跃
        function jumpRaccoon() {
            if (!gameActive) return;
            
            // 播放音效
            if (soundEnabled) {
                jumpSound.currentTime = 0;
                jumpSound.play();
            }
            
            // 跳跃动画
            raccoon.classList.add('bounce');
            setTimeout(() => raccoon.classList.remove('bounce'), 500);
            
            // 随机移动位置
            const maxX = gameArea.offsetWidth - raccoon.offsetWidth;
            const maxY = gameArea.offsetHeight - raccoon.offsetHeight;
            
            const newX = Math.random() * maxX;
            const newY = Math.random() * maxY;
            
            raccoon.style.left = `${newX}px`;
            raccoon.style.bottom = `${newY}px`;
        }
        
        // 使用特殊能力
        function useSpecialPower() {
            if (!gameActive || !specialPowerAvailable) return;
            
            // 播放音效
            if (soundEnabled) {
                powerSound.currentTime = 0;
                powerSound.play();
            }
            
            // 显示特殊能力效果
            showMessage("特殊能力！所有收集物分数翻倍！", "#4fc3f7");
            
            // 将所有收集物分数翻倍
            collectibles.forEach(item => {
                if (!item.type.dangerous) {
                    item.element.style.transform = 'scale(1.5)';
                    item.element.style.boxShadow = '0 0 20px gold';
                    
                    setTimeout(() => {
                        if (item.element) {
                            item.element.style.transform = 'scale(1)';
                            item.element.style.boxShadow = 'none';
                        }
                    }, 1000);
                }
            });
            
            // 特殊能力只能使用一次
            specialPowerAvailable = false;
            specialPowerBtn.disabled = true;
            specialPowerBtn.innerHTML = '<i class="fas fa-bolt"></i> 能力已使用';
            specialPowerBtn.style.opacity = '0.5';
        }
        
        // 更新仓库显示
        function updateInventory() {
            inventoryEl.innerHTML = '';
            
            // 只显示最近10个收集物
            const recentItems = inventory.slice(-10);
            
            recentItems.forEach(item => {
                const itemEl = document.createElement('div');
                itemEl.className = 'inventory-item';
                itemEl.innerHTML = `<div style="font-size: 1.8rem;">${item.icon}</div>`;
                itemEl.title = item.name;
                itemEl.style.backgroundColor = item.color;
                inventoryEl.appendChild(itemEl);
            });
        }
        
        // 更新UI
        function updateUI() {
            scoreValue.textContent = score;
            livesValue.textContent = lives;
            collectedCountEl.textContent = collectedCount;
            
            // 更新特殊能力按钮状态
            if (!specialPowerAvailable) {
                specialPowerBtn.disabled = true;
                specialPowerBtn.innerHTML = '<i class="fas fa-bolt"></i> 能力已使用';
                specialPowerBtn.style.opacity = '0.5';
            } else {
                specialPowerBtn.disabled = false;
                specialPowerBtn.innerHTML = '<i class="fas fa-bolt"></i> 使用特殊能力';
                specialPowerBtn.style.opacity = '1';
            }
        }
        
        // 显示消息
        function showMessage(text, color) {
            gameMessage.textContent = text;
            gameMessage.style.color = color;
            gameMessage.style.borderColor = color;
            gameMessage.style.display = 'block';
            
            // 3秒后自动隐藏
            setTimeout(hideMessage, 3000);
        }
        
        // 隐藏消息
        function hideMessage() {
            gameMessage.style.display = 'none';
        }
        
        // 结束游戏
        function endGame(win) {
            gameActive = false;
            
            if (gameTimer) {
                clearInterval(gameTimer);
                gameTimer = null;
            }
            
            if (win) {
                showMessage(`恭喜！你赢了！最终得分: ${score}`, "#4CAF50");
            } else {
                if (lives <= 0) {
                    showMessage("游戏结束！生命值耗尽！", "#f44336");
                } else if (timeLeft <= 0) {
                    showMessage("时间到！游戏结束！", "#f44336");
                }
            }
            
            startBtn.innerHTML = '<i class="fas fa-play"></i> 重新开始';
        }
        
        // 添加收集物
        function addCollectible() {
            if (!gameActive) return;
            
            const type = collectibleTypes[Math.floor(Math.random() * collectibleTypes.length)];
            createCollectible(type);
        }
        
        // 切换背景音乐
        function toggleMusic() {
            if (musicPlaying) {
                backgroundMusic.pause();
                musicToggle.innerHTML = '<i class="fas fa-music-slash"></i>';
                musicPlaying = false;
            } else {
                backgroundMusic.play().catch(e => console.log("自动播放被阻止:", e));
                musicToggle.innerHTML = '<i class="fas fa-music"></i>';
                musicPlaying = true;
            }
        }
        
        // 切换音效
        function toggleSound() {
            soundEnabled = !soundEnabled;
            soundToggle.innerHTML = soundEnabled ? 
                '<i class="fas fa-volume-up"></i>' : 
                '<i class="fas fa-volume-mute"></i>';
        }
        
        // 事件监听
        startBtn.addEventListener('click', function() {
            if (!gameActive) {
                if (this.innerHTML.includes('开始') || this.innerHTML.includes('重新开始')) {
                    startGame();
                } else if (this.innerHTML.includes('继续')) {
                    togglePause();
                }
            } else {
                togglePause();
            }
        });
        
        jumpBtn.addEventListener('click', jumpRaccoon);
        
        raccoon.addEventListener('click', jumpRaccoon);
        
        addItemBtn.addEventListener('click', addCollectible);
        
        specialPowerBtn.addEventListener('click', useSpecialPower);
        
        resetBtn.addEventListener('click', initGame);
        
        musicToggle.addEventListener('click', toggleMusic);
        
        soundToggle.addEventListener('click', toggleSound);
        
        // 尝试自动播放背景音乐
        document.addEventListener('click', function initAudio() {
            if (musicPlaying) {
                backgroundMusic.play().catch(e => console.log("自动播放被阻止，请点击播放按钮:", e));
            }
            document.removeEventListener('click', initAudio);
        });
        
        // 初始化游戏
        initGame();
        
        // 键盘控制
        document.addEventListener('keydown', function(e) {
            if (e.code === 'Space' && gameActive) {
                jumpRaccoon();
            } else if (e.code === 'KeyP') {
                togglePause();
            } else if (e.code === 'KeyS' && gameActive && specialPowerAvailable) {
                useSpecialPower();
            } else if (e.code === 'KeyA' && gameActive) {
                addCollectible();
            } else if (e.code === 'KeyR') {
                initGame();
            }
        });
    </script>
</body>
</html>
