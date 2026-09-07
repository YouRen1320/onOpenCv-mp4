# 圆头耄耋 - OpenCV.js 视频处理项目

> [!IMPORTANT]
> **已完成的历史演示，不再维护。** 本仓库只演示浏览器端 OpenCV.js Canny 边缘检测，内置视频用于复现实验，不是通用视频编辑器。代码与示例继续保留用于学习回顾。

## 项目简介

这是一个基于OpenCV.js的Web视频处理应用程序，能够实时对视频进行边缘检测处理。项目使用纯HTML、CSS和JavaScript实现，无需后端服务器。

## 功能特性

- 🎥 **视频播放**: 自动播放本地MP4视频文件
- 🔍 **实时边缘检测**: 使用Canny边缘检测算法处理视频帧
- 📱 **响应式设计**: 自适应浏览器窗口大小
- ⚡ **实时处理**: 使用requestAnimationFrame实现流畅的实时处理

## 技术栈

- **OpenCV.js 4.5.0**: 计算机视觉库，用于图像处理
- **HTML5 Canvas**: 用于视频渲染和图像处理
- **HTML5 Video**: 用于视频播放
- **JavaScript**: 核心逻辑实现

## 项目结构

```
onOpenCv-mp4/
├── index.html          # 主页面文件，包含所有HTML、CSS和JavaScript代码
├── maodie.mp4         # 视频文件（21MB）
└── README.md          # 项目说明文档
```

## 图像处理流程

1. **视频加载**: 加载本地MP4视频文件
2. **帧提取**: 从视频中提取当前帧
3. **灰度转换**: 将彩色图像转换为灰度图像
4. **高斯模糊**: 使用5x5核进行高斯模糊，减少噪声
5. **边缘检测**: 使用Canny算法检测边缘（阈值：50-150）
6. **结果显示**: 在Canvas上显示处理后的图像

## 使用方法

### 本地运行

1. 确保项目文件完整（包含`index.html`和`maodie.mp4`）
2. 使用本地服务器运行项目（由于CORS限制，不能直接双击HTML文件）

#### 方法一：使用Python内置服务器
```bash
# Python 3
python -m http.server 8000

# Python 2
python -m SimpleHTTPServer 8000
```

#### 方法二：使用Node.js http-server
```bash
npm install -g http-server
http-server
```

#### 方法三：使用Live Server（VS Code扩展）
在VS Code中安装Live Server扩展，右键点击`index.html`选择"Open with Live Server"

3. 在浏览器中访问 `http://localhost:8000`

### 浏览器要求

- 支持HTML5 Video和Canvas的现代浏览器
- 建议使用Chrome、Firefox、Safari或Edge最新版本

## 核心参数说明

### Canny边缘检测参数
- **低阈值**: 50 - 用于边缘连接
- **高阈值**: 150 - 用于初始边缘检测

### 高斯模糊参数
- **核大小**: 5x5 - 控制模糊程度
- **标准差**: 0（自动计算）

## 自定义配置

### 更换视频文件
1. 将新的MP4文件放入项目根目录
2. 修改`index.html`中的视频路径：
```javascript
video.src = "your-video-file.mp4";
```

### 调整处理参数
在`processVideo()`函数中修改以下参数：
```javascript
// 高斯模糊核大小
cv.GaussianBlur(src, src, new cv.Size(5, 5), 0, 0, cv.BORDER_DEFAULT);

// Canny边缘检测阈值
cv.Canny(src, dst, 50, 150);
```

## 性能优化建议

- 使用较小分辨率的视频文件以提高处理速度
- 根据需要调整处理参数以平衡效果和性能
- 在低性能设备上可以考虑降低处理频率

## 故障排除

### 常见问题

1. **视频无法播放**
   - 检查视频文件路径是否正确
   - 确保使用HTTP服务器而非直接打开HTML文件

2. **OpenCV.js加载失败**
   - 检查网络连接
   - 确保能够访问OpenCV.js CDN

3. **处理效果不理想**
   - 调整Canny算法的阈值参数
   - 修改高斯模糊的核大小

## 许可证

本项目仅供学习和研究使用。

## 贡献

欢迎提交Issue和Pull Request来改进项目。
