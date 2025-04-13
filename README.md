# PicSpider 写真爬取展示

## 项目简介

PicSpider是一个优雅的写真相册展示系统，提供了简洁美观的界面来浏览和管理图片相册。系统采用现代化的UI设计，支持相册预览、图片浏览、搜索等功能，为用户提供流畅的浏览体验。
项目99%由ai编写

## web展示
![image](https://github.com/user-attachments/assets/aff7d938-9ec3-408c-a48d-09172263df73)

## 主要功能

- **相册展示**：以网格布局展示所有相册，支持缩略图预览
- **响应式设计**：完美适配各种屏幕尺寸，从移动设备到桌面显示器
- **搜索功能**：支持按相册名称搜索
- **分页浏览**：相册列表支持分页显示
- **优雅的UI**：采用现代简约设计风格，提供流畅的用户体验
- **图片预览**：支持查看相册内的完整图片内容

## 技术栈

- **后端框架**：Python Flask
- **前端框架**：
  - Bootstrap 5.3.3
  - PhotoSwipe 5.4.3（图片查看器）
- **UI组件**：
  - Bootstrap Icons
  - 自定义CSS样式

## 目录结构

```
├── app.py          # Web服务器入口
│                   # - 提供相册浏览和图片展示功能
│                   # - 实现相册分页和搜索功能
│                   # - 处理图片文件的访问请求
│                   # - 管理相册缩略图缓存
├── main.py         # 爬虫核心模块
│                   # - 实现并发下载功能
│                   # - 智能任务队列管理
│                   # - 图片处理和存储
│                   # - 异常处理和重试机制
├── templates/      # 前端模板目录
│   ├── index.html  # 首页模板 - 展示相册网格和搜索功能
│   └── album.html  # 相册详情页 - 支持图片预览和浏览
└── downloaded/     # 相册图片存储目录
                    # - 按相册分类存储图片
                    # - 支持增量更新
```

## 安装和运行

1. 确保已安装Python 

2. 安装依赖包：

推荐使用虚拟环境安装依赖：
```bash
# 创建虚拟环境
python -m venv venv

# 激活虚拟环境
# Windows:
venv\Scripts\activate
# Linux/Mac:
source venv/bin/activate

# 安装依赖包
pip install flask requests beautifulsoup4

# 或者使用requirements.txt安装
# pip install -r requirements.txt
```

项目依赖说明：
- Flask: Web应用框架
- requests: HTTP请求库
- beautifulsoup4: HTML解析库

3. 运行应用：
```bash
python main.py
```
开始爬取图片，并等待爬取完毕后在运行下面的操作
```bash
python app.py
```

4. 访问应用：
   打开浏览器访问 `http://localhost:5000`

## 使用说明

1. **浏览相册**
   - 首页以网格形式展示所有相册
   - 点击相册可进入详情页查看完整图片集
   - 支持分页浏览，使用页面底部的分页控件导航

2. **搜索相册**
   - 使用顶部搜索框输入关键词
   - 系统会实时过滤并显示匹配的相册

3. **查看图片**
   - 在相册详情页面可查看所有图片
   - 支持图片放大、滑动浏览等功能

## 爬虫功能

### 工作原理

- **目标网站**：写真网站的内容获取
- **数据获取**：使用requests库进行HTTP请求，beautifulsoup4解析HTML内容
- **处理流程**：
  1. 解析目标页面获取相册信息
  2. 提取图片URL和相关元数据
  3. 下载并保存图片到本地

### 主要功能

- **并发下载**：
  - 多线程并发下载提升效率
  - 智能任务队列管理
  - 动态调整并发数

- **图片处理**：
  - 自动生成缩略图

- **数据管理**：
  - 相册信息本地存储
  - 增量更新机制
  - 重复图片检测

### 性能优化

- **请求优化**：
  - 动态调整请求间隔
  - 自动重试机制
  - 代理IP支持

- **资源控制**：
  - 内存使用优化
  - 磁盘空间管理
  - 带宽占用控制

