# 英语刷题网 — 在线英语学习平台

免费、无广告的在线英语练习平台。随机出题，即时反馈，支持收藏和错题本。

## 技术栈

| 层 | 技术 |
|---|---|
| 前端 | Vue 3 + Vite + Element Plus + Vue Router |
| 后端 | Express 5 + MySQL2 + JWT + bcrypt |
| 样式 | CSS 自定义属性（设计系统）+ Google Fonts |

## 项目结构

```
├── index.html              # Vite HTML 入口
├── vite.config.js          # Vite 构建配置
├── package.json            # 前端依赖
├── jsconfig.json           # @/ 路径别名
├── .gitignore
│
├── src/                    # ── 前端源码 ──
│   ├── main.js             #   Vue 入口
│   ├── App.vue             #   根组件
│   ├── config/index.js     #   API 地址配置
│   ├── router/index.js     #   路由 + 守卫
│   ├── styles/             #   全局样式 + 设计系统
│   │   ├── variables.css   #     CSS 变量（颜色/字体/间距）
│   │   └── global.css      #     重置 + 动画 + 通用组件类
│   ├── utils/api.js        #   authFetch 请求工具
│   ├── views/              #   页面组件（13 个）
│   │   ├── Home.vue        #     首页
│   │   ├── Explore.vue     #     题库总览
│   │   ├── Login.vue       #     登录
│   │   ├── Register.vue    #     注册
│   │   ├── User.vue        #     个人中心
│   │   ├── Admin.vue       #     管理后台
│   │   ├── Nav.vue         #     导航栏
│   │   ├── Foot.vue        #     页脚
│   │   ├── QuestionLists.vue #   题目组件（单选/阅读/翻译/写作）
│   │   ├── SingleChoice.vue  #   单选题页
│   │   ├── Reading.vue       #   阅读理解页
│   │   ├── Translate.vue     #   翻译练习页
│   │   ├── Writing.vue       #   写作练习页
│   │   └── LetterBackground.vue # 浮动字母背景
│   └── assets/             #   图片资源
│
└── server/                 # ── 后端源码 ──
    ├── server.js           #   Express 服务器（所有 API）
    ├── sql.sql             #   数据库建表脚本
    ├── .env                #   环境变量（JWT 密钥、数据库配置）
    ├── .env.example        #   环境变量模板
    └── package.json        #   后端依赖
```

## 快速开始

### 1. 数据库

```sql
-- 在 MySQL 中执行
source server/sql.sql
```

### 2. 环境变量

```bash
cp server/.env.example server/.env
# 编辑 server/.env 填入你的 JWT 密钥和数据库密码
```

### 3. 安装依赖

```bash
# 前端
npm install

# 后端
cd server && npm install
```

### 4. 启动

```bash
# 后端（端口 3000）
cd server && node server.js

# 前端（端口 5173）
npm run dev
```

访问 http://localhost:5173

## 设计系统

配色方案定义在 `src/styles/variables.css`，通过 CSS 自定义属性全局共享：

| 变量 | 值 | 用途 |
|---|---|---|
| `--primary` | `#5B4AE4` | 主色（按钮、链接） |
| `--accent` | `#FF6B4A` | 强调色（CTA） |
| `--bg-page` | `#F4F2EE` | 页面背景 |
| `--text-primary` | `#1A1635` | 主文字 |
| `--font-display` | DM Serif Display | 标题字体 |
| `--font-body` | DM Sans | 正文字体 |

## API 接口

| 方法 | 路径 | 说明 | 权限 |
|---|---|---|---|
| POST | `/api/user/register` | 注册 | 公开 |
| POST | `/api/user/login` | 登录 | 公开 |
| GET | `/api/auth/verify` | 验证 Token | 登录 |
| GET | `/api/questions/stats` | 题型统计 | 公开 |
| GET | `/api/questions/single-choice` | 获取单选题 | 登录 |
| GET | `/api/questions/reading` | 获取阅读题 | 登录 |
| GET | `/api/questions/translation` | 获取翻译题 | 登录 |
| GET | `/api/questions/writing` | 获取写作题 | 登录 |
| GET/POST/DELETE | `/api/questions/collect` | 收藏管理 | 登录 |
| GET/DELETE | `/api/error-books` | 错题本管理 | 登录 |
| GET | `/api/admin/dashboard` | 管理数据 | 管理员 |
| CRUD | `/api/admin/users` | 用户管理 | 管理员 |
| CRUD | `/api/admin/questions` | 题目管理 | 管理员 |

## License

本项目使用 [CC BY-NC 4.0](LICENSE)（知识共享 署名-非商业性使用 4.0 国际协议）。

- ✅ 允许：个人学习、课程作业参考、毕业设计参考、学术研究
- ⚠️ 要求：使用时需标注来源
- ❌ 禁止：商业用途

详见 [LICENSE](LICENSE) 文件
