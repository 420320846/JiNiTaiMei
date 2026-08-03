[README.md](https://github.com/user-attachments/files/30442915/README.md)
# 计你太美 ✨

> 让每一件小事都闪闪发光 —— 一个可爱风的全栈任务管理小应用

计你太美是一个基于 Next.js 16 的任务管理与专注计时应用，采用樱花粉主题的可爱风设计。把目标拆成任务集，专注计时，统计进度，让生活更有条理。支持 **Web / PWA / Android APK** 三端运行，完全离线可用。

![version](https://img.shields.io/badge/version-v1.3.6-FFB7C5)
![license](https://img.shields.io/badge/license-MIT-blue)
![next](https://img.shields.io/badge/Next.js-16-black)
![react](https://img.shields.io/badge/React-19-61dafb)
![capacitor](https://img.shields.io/badge/Capacitor-Android-119EFF)

---

## ✨ 功能特性

### 🏠 首页
- 每日格言卡片（99 条励志诗词轮播 + 随机切换按钮）
- 今日总览（完成率 / 优先任务 / 任务集合）
- 全部任务集快捷入口
- 高优先级任务弹窗、全部任务集弹窗
- 新建任务集

### 📋 任务管理
- **任务集**：把目标分类管理（每日习惯 / 工作项目 / 学习计划 等）
- **任务**：标题、备注、优先级（无/低/中/高）、截止日期、标签、循环任务
- **子任务**：每个任务下可挂载清单项
- **拖拽排序**：dnd-kit 实现的任务 & 子任务拖拽
- **批量操作**：完成 / 取消 / 归档 / 移动 / 删除
- **回收站**：软删除，可恢复或彻底清除
- **循环任务**：每日自动重置完成状态
- **复制任务**：一键克隆（含子任务）
- **截止日期提醒**：到期/逾期/明日提醒通知

### ⏱️ 专注计时
- 番茄钟 / 正向计时双模式
- 专注 / 休息 状态切换（分两行居中排列）
- 关联任务集 & 子任务
- 毛玻璃计时圈 + 旋转光泽 + 呼吸发光动画
- 计时进行时锁定切换，防误触
- 全屏专注界面，底部栏保留
- 大尺寸控制按钮（64px 开始按钮，48px 其他）

### 📊 数据统计
11 个可拖拽排序、可隐藏的统计卡片：
- **快捷统计**：任务集 / 已完成 / 待办中 / 高优先级（可点击弹窗）
- **完成趋势**：日视图（4小时区间）/ 周视图（周一到周日）/ 月视图（日历网格热力图）/ 年视图（12月）
- **平均统计**：日/周/月/年平均完成数 & 专注时长
- **优先级分布**：高/中/低/无 待办占比
- **专注热力图**：30/90 天活动密度（无数字，纯颜色）
- **任务集进度**：各任务集完成率
- **专注分布**：任务集/子任务专注时长占比环形图
- **专注摘要**：总时长 / 番茄数 / 均时长
- **7天专注**：近7天柱状图（点击查看详情）
- **专注时段**：24小时分布（0点~21点横坐标）
- **专注时间轴**：今日时间轴 + 过往月视图日历选择器（全屏 overlay）

### 👤 我的
- 用户资料（等级系统：10级勋章，最高500h）
- **10 个 SVG 勋章**（灰铁→铜→银→金→蓝→紫钻→粉宝→紫星→红冠→彩虹）
- **6 个活跃徽章**（星空天体系列：⭐晨星→🌙新月→☀️骄阳→🌠流星→☄️流火→🌌银河）
- 深色模式
- **22 种主题配色**（8 标准 + 14 特殊）
- 数据管理：导出（4层策略适配移动端）/ 导入 / 刷新 / 清除缓存
- 回收站
- 提醒通知（系统通知权限，自适应客户端文案）
- 存储权限
- 检查版本更新

### 🎨 设计细节
- CSS 变量主题系统（`--accent-50~600`）+ `color-mix` + `backdrop-filter` 毛玻璃
- Framer Motion 微交互动画
- 移动端优先响应式设计
- 安全区适配（刘海 / 底部导航条）
- PWA 离线缓存（Service Worker）
- IndexedDB 双层数据备份（防会话重置丢失）

---

## 🚀 快速开始

### 环境要求

- **Node.js** 20+ 或 **Bun** 1.1+
- **Android Studio**（仅打包 APK 时需要，含 Android SDK 36）

### 本地开发

```bash
# 克隆仓库
git clone https://github.com/420320846/JiNiTaiMei.git
cd JiNiTaiMei

# 安装依赖
bun install

# 启动开发服务器
bun run dev
# 打开 http://localhost:3000
```

### 生产构建

```bash
# 静态导出（默认，离线可用）
bun run build
# 产物在 out/ 目录
```

### 代码检查

```bash
bun run lint
```

---

## 📦 打包 Android APK

计你太美 支持打包成离线 Android APK，无需联网即可使用全部功能。

### 一键构建

```bash
# 自动下载 JDK + Android SDK 并编译
bun run apk:build
# 产出：dist/计你太美-v1.3.3-debug.apk
```

### 手动构建

```bash
# 1. 生成静态导出
bun run build

# 2. 删除 sourcemap（压缩体积）
find out/ -name "*.map" -delete

# 3. 同步到 Android 工程
bun run cap:sync

# 4. 删除 android assets 中的 sourcemap
find android/app/src/main/assets/public/ -name "*.map" -delete

# 5. 编译 APK
cd android && ./gradlew assembleDebug

# 产物：android/app/build/outputs/apk/debug/app-debug.apk
```

### 安装到手机

```bash
adb install dist/计你太美-v1.3.3-debug.apk
```

> 📖 完整构建指南见 [docs/APK-BUILD.md](docs/APK-BUILD.md)

---

## 🏗️ 技术架构

### 技术栈

| 层级 | 技术 | 说明 |
|------|------|------|
| **框架** | Next.js 16 (App Router) | 静态导出模式 |
| **语言** | TypeScript 5 | 全量类型 |
| **样式** | Tailwind CSS 4 + shadcn/ui | New York 风格 |
| **图标** | Lucide React | |
| **动画** | Framer Motion | 微交互 |
| **拖拽** | dnd-kit | 任务排序 |
| **状态** | Zustand + persist | 客户端状态 |
| **数据** | localStorage + IndexedDB | 离线数据层（双层备份） |
| **移动端** | Capacitor 8 | Android 打包 |
| **PWA** | Service Worker | 离线缓存 |
| **通知** | Capacitor Local Notifications | 原生通知权限 |

### 架构说明

```
┌─────────────────────────────────────────────────┐
│                 计你太美 应用                    │
├─────────────────────────────────────────────────┤
│  前端 (React 19)                                │
│  ├── 首页 / 任务 / 计时 / 统计 / 我的           │
│  ├── shadcn/ui 组件库                            │
│  └── Framer Motion 动画                         │
├─────────────────────────────────────────────────┤
│  数据层 (src/lib/local-db.ts)                   │
│  ├── localFetch() — fetch 兼容的本地 API        │
│  ├── 17 个端点（任务集/任务/子任务/专注/统计）  │
│  ├── localStorage 持久化                        │
│  └── IndexedDB 备份（防会话重置丢失）           │
├─────────────────────────────────────────────────┤
│  分发                                            │
│  ├── Web (静态导出 out/)                         │
│  ├── PWA (manifest + Service Worker)            │
│  └── Android APK (Capacitor WebView)            │
└─────────────────────────────────────────────────┘
```

### 离线数据层

应用采用纯前端架构，所有数据存储在浏览器 `localStorage` + `IndexedDB`，**无需服务端**：

- `src/lib/local-db.ts` —— 完整复刻 17 个 API 端点的本地数据层
- `src/lib/persistent-storage.ts` —— IndexedDB 双层备份
- `src/lib/store.ts` —— Zustand 状态管理，通过 `localFetch` 访问数据
- 数据模型：`TaskSet` / `Task` / `SubTask` / `FocusSession`

---

## 📁 项目结构

```
JiNiTaiMei/
├── src/
│   ├── app/                    # Next.js App Router
│   │   ├── layout.tsx          # 根布局（主题初始化）
│   │   ├── page.tsx            # 入口
│   │   └── globals.css         # 全局样式 + 主题系统
│   ├── components/
│   │   ├── app/                # 应用骨架（导航/计时/启动屏）
│   │   ├── pages/              # 五个页面
│   │   │   ├── home-page.tsx
│   │   │   ├── tasks-page.tsx
│   │   │   ├── stats-page.tsx
│   │   │   └── profile-page.tsx
│   │   ├── level-badges.tsx    # 10个SVG勋章组件
│   │   └── ui/                 # shadcn/ui 组件
│   ├── lib/
│   │   ├── local-db.ts         # 离线数据层（核心）
│   │   ├── persistent-storage.ts # IndexedDB备份层
│   │   └── store.ts            # Zustand 状态管理
│   ├── hooks/                  # 自定义 Hooks
│   └── types/                  # TypeScript 类型
├── android/                    # Capacitor Android 工程
├── public/                     # 静态资源（图标/manifest/sw.js）
├── scripts/                    # 构建脚本（图标/APK）
├── docs/
│   └── APK-BUILD.md            # APK 打包指南
└── capacitor.config.ts         # Capacitor 配置
```

---

## 🎯 数据模型

```prisma
model TaskSet {           // 任务集
  id          String
  title       String
  description String
  color       String      // 主题色
  emoji       String      // 图标
  archived    Boolean
  tasks       Task[]
}

model Task {              // 任务
  id          String
  title       String
  notes       String
  completed   Boolean
  priority    Int         // 0无 1低 2中 3高
  dueDate     DateTime?
  archived    Boolean     // 软删除
  tags        String      // 逗号分隔
  recurring   Boolean     // 循环任务
  order       Int         // 拖拽排序
  taskSetId   String
  subtasks    SubTask[]
}

model SubTask {           // 子任务
  id        String
  title     String
  completed Boolean
  order     Int
  taskId    String
}

model FocusSession {      // 专注记录
  id          String
  duration    Int         // 秒
  taskSetId   String?
  taskId      String?
  subtaskId   String?
  createdAt   DateTime
}
```

---

## ⌨️ 快捷键

| 快捷键 | 功能 |
|--------|------|
| `1` ~ `5` | 切换标签页（首页/任务/计时/统计/我的） |
| `N` | 新建任务 |
| `Space` | 开始/暂停专注计时 |

---

## 📈 版本历史

| 版本 | 日期 | 主要更新 |
|------|------|----------|
| **v1.3.3** | 2026-07 | 离线APK、毛玻璃计时圈、月视图日历热力图、截止日期通知、移动端导出 |
| v1.3.2 | 2026-07 | 离线 APK 打包、PWA 支持、移动端适配 |
| v1.3.0 | 2026-07 | 统计卡片可拖拽排序、环形图毛玻璃、月视图时间轴 |
| v1.2.0 | 2026-06 | 专注计时全屏化、子任务关联、22 主题配色 |
| v1.1.0 | 2026-05 | 任务集系统、子任务、回收站、拖拽排序 |
| v1.0.0 | 2026-04 | 初始版本：任务管理 + 番茄钟 |

---

## 🤝 贡献

欢迎提交 Issue 和 PR！

1. Fork 本仓库
2. 创建特性分支：`git checkout -b feature/amazing-feature`
3. 提交更改：`git commit -m 'Add amazing feature'`
4. 推送分支：`git push origin feature/amazing-feature`
5. 提交 Pull Request

---

## 📄 许可证

本项目采用 [MIT License](LICENSE) 开源。

---

## 💖 致谢

- [Next.js](https://nextjs.org/) — React 全栈框架
- [shadcn/ui](https://ui.shadcn.com/) — 组件库
- [Tailwind CSS](https://tailwindcss.com/) — 原子化 CSS
- [Framer Motion](https://www.framer.com/motion/) — 动画
- [dnd-kit](https://dndkit.com/) — 拖拽
- [Capacitor](https://capacitorjs.com/) — 跨平台
- [Lucide](https://lucide.dev/) — 图标

---

## 📞 联系

- **GitHub**：[420320846/JiNiTaiMei](https://github.com/420320846/JiNiTaiMei)
- **反馈邮箱**：420320846@qq.com

---

<div align="center">

**Made with 💗 by 计你太美**

让每一件小事都闪闪发光 ✨

</div>
