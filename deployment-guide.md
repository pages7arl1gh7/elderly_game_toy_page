# GitHub Pages 部署指南

## 部署步骤

### 1. 准备文件
确保您的项目目录包含以下文件：
```
elderly_game_toy_page/
├── index.html          # 主游戏文件
├── easy.mp4           # 简单难度视频
├── medium.mp4         # 中等难度视频
├── hard.mp4           # 困难难度视频
├── README.md          # 项目说明
└── video-setup-guide.md # 视频设置指南
```

### 2. 推送到 GitHub
```bash
# 如果还没有初始化 git 仓库
git init
git add .
git commit -m "Initial commit: 中老年平衡感训练游戏"

# 推送到 GitHub（替换为您的仓库 URL）
git remote add origin https://github.com/yourusername/elderly_game_toy_page.git
git branch -M main
git push -u origin main
```

### 3. 启用 GitHub Pages
1. 访问您的 GitHub 仓库页面
2. 点击 "Settings" 标签
3. 在左侧菜单中找到 "Pages"
4. 在 "Source" 部分选择 "Deploy from a branch"
5. 选择 "main" 分支和 "/ (root)" 文件夹
6. 点击 "Save"

### 4. 访问网站
部署完成后，您的网站将在以下地址可用：
```
https://yourusername.github.io/elderly_game_toy_page/
```

## 重要注意事项

### HTTPS 要求
- GitHub Pages 使用 HTTPS
- MediaPipe 和摄像头访问需要 HTTPS 环境
- 您的网站将自动支持 HTTPS

### 文件大小限制
- GitHub Pages 有文件大小限制
- 单个文件不能超过 100MB
- 仓库总大小建议不超过 1GB
- 如果视频文件过大，考虑：
  - 压缩视频文件
  - 使用外部视频托管服务
  - 使用 Git LFS（Large File Storage）

### 浏览器兼容性
网站支持以下浏览器：
- Chrome 60+
- Firefox 55+
- Safari 11+
- Edge 79+

### 移动设备优化
- 网站已针对移动设备优化
- 支持触摸操作
- 响应式设计适配不同屏幕尺寸

## 测试清单

部署后请测试以下功能：

### 基本功能
- [ ] 页面正常加载
- [ ] 语言切换功能正常
- [ ] 免责声明弹窗显示
- [ ] 用户信息表单提交

### 游戏功能
- [ ] 摄像头权限请求
- [ ] 视频播放正常
- [ ] MediaPipe 姿态检测工作
- [ ] 分数计算显示
- [ ] 游戏结束流程

### 移动端测试
- [ ] 在手机上正常显示
- [ ] 触摸操作响应
- [ ] 摄像头在移动设备上工作
- [ ] 视频播放无问题

## 常见问题解决

### 1. 摄像头无法访问
- 确保使用 HTTPS 访问
- 检查浏览器权限设置
- 在浏览器中允许摄像头访问

### 2. 视频无法播放
- 检查视频文件是否上传
- 确认视频格式为 MP4
- 验证视频编码兼容性

### 3. MediaPipe 加载失败
- 检查网络连接
- 确认 CDN 资源可访问
- 尝试刷新页面

### 4. 页面在移动设备上显示异常
- 检查 viewport 设置
- 验证 CSS 媒体查询
- 测试不同屏幕尺寸

## 性能优化建议

### 1. 视频优化
- 使用适当的视频压缩
- 考虑使用 WebM 格式作为备选
- 实现视频预加载

### 2. 加载优化
- 启用浏览器缓存
- 考虑使用 Service Worker
- 优化图片和资源加载

### 3. 用户体验
- 添加加载指示器
- 实现错误处理和用户反馈
- 提供离线支持（可选）

## 更新和维护

### 更新网站
```bash
# 修改文件后
git add .
git commit -m "更新描述"
git push origin main
```

### 监控和分析
- 使用 GitHub Pages 内置分析
- 考虑添加 Google Analytics
- 监控用户反馈和问题报告

## 安全考虑

- 网站不收集用户个人数据
- 所有计算在客户端进行
- 不上传视频到服务器
- 遵循隐私保护最佳实践 