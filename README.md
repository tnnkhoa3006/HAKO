# HAKO

[![Next.js](https://img.shields.io/badge/Next.js-15.5.7-black)](https://nextjs.org/)
[![React](https://img.shields.io/badge/React-19.0.0-blue)](https://reactjs.org/)
[![Node.js](https://img.shields.io/badge/Node.js-18+-green)](https://nodejs.org/)
[![MongoDB](https://img.shields.io/badge/MongoDB-6+-green)](https://www.mongodb.com/)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

A comprehensive full-stack HAKO application built with modern web technologies. Features real-time messaging, stories, posts, video calls, and a responsive UI designed for seamless user interaction.

## ✨ Key Features

### 🔐 Authentication & Security
- JWT-based authentication system
- Google OAuth integration
- Secure user sessions and data protection

### 📸 Content Management
- **Posts**: Create, edit, delete, and interact with multimedia posts
- **Stories**: Temporary content with music integration
- **Comments & Replies**: Nested comment system with real-time updates

### 💬 Real-time Communication
- **Messaging**: Socket.io-powered instant messaging with media support
- **Video Calls**: Peer-to-peer video calling using PeerJS
- **Notifications**: Real-time push notifications for user interactions

### 👥 Social Features
- User profiles with follow/unfollow functionality
- Feed with infinite scrolling and lazy loading
- Search and discovery features

### 🎨 User Experience
- Responsive design optimized for mobile and desktop
- Modern UI with TailwindCSS and Framer Motion animations
- Dark/light theme support
- Progressive Web App (PWA) capabilities

### 🤖 AI-Powered Recommendations
- Gợi ý bài viết dựa trên lịch sử tương tác (like, comment, follow)
- Hệ thống logging tương tác thông minh với trọng số khác nhau cho mỗi loại hành động
- API gợi ý feed có thể tích hợp với các mô hình AI (Gemini/OpenAI) trong tương lai

## 🏗️ Architecture Overview

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Frontend      │    │   Backend       │    │   Database      │
│   (Next.js)     │◄──►│   (Express.js)  │◄──►│   (MongoDB)     │
│                 │    │                 │    │                 │
│ - React 19      │    │ - REST API      │    │ - User data     │
│ - TypeScript    │    │ - Socket.io     │    │ - Posts         │
│ - Redux Toolkit │    │ - JWT Auth      │    │ - Messages      │
│ - TailwindCSS   │    │ - Cloudinary    │    │ - Stories       │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         └───────────────────────┼───────────────────────┘
                                 │
                    ┌─────────────────┐
                    │   External      │
                    │   Services      │
                    │                 │
                    │ - Cloudinary    │
                    │ - Google OAuth  │
                    │ - Twilio        │
                    │ - FFmpeg        │
                    └─────────────────┘
```

## 📁 Project Structure

This monorepo uses Git Submodules to manage frontend and backend as separate repositories:

```
HAKO/
├── front-end/                    # Next.js Frontend Application
│   ├── src/
│   │   ├── app/                  # Next.js App Router
│   │   ├── components/           # Reusable React Components
│   │   ├── contexts/             # React Context Providers
│   │   ├── store/                # Redux Store & Slices
│   │   ├── types/                # TypeScript Type Definitions
│   │   ├── utils/                # Utility Functions
│   │   └── styles/               # Global Styles & CSS
│   ├── public/                   # Static Assets
│   ├── package.json
│   ├── next.config.ts
│   └── tsconfig.json
│
├── bach-end/                     # Express.js Backend API
│   ├── controllers/              # Route Controllers
│   ├── models/                   # MongoDB Models
│   ├── routes/                   # API Routes
│   ├── middlewares/              # Express Middlewares
│   ├── services/                 # Business Logic Services
│   ├── utils/                    # Backend Utilities
│   ├── config/                   # Configuration Files
│   ├── server/                   # Server Setup
│   ├── package.json
│   └── app.js
│
├── README.md                     # Project Documentation
└── .gitmodules                   # Git Submodules Configuration
```

### Submodules
- **Frontend**: [HAKO_Front-End](https://github.com/khoatnn/HAKO_Front-End)
- **Backend**: [HAKO_BackEnd](https://github.com/khoatnn/HAKO_BackEnd)

## 🛠️ Technology Stack

### Frontend
- **Framework**: Next.js 15.5.7 (App Router)
- **Language**: TypeScript
- **State Management**: Redux Toolkit + Zustand
- **Styling**: TailwindCSS v4
- **Animations**: Framer Motion
- **Real-time**: Socket.io Client
- **Video Calls**: PeerJS
- **Image Processing**: React Cropper, CropperJS
- **Charts**: Swiper
- **HTTP Client**: SWR

### Backend
- **Runtime**: Node.js 18+
- **Framework**: Express.js 5
- **Database**: MongoDB 6+ with Mongoose
- **Authentication**: JWT + Passport.js
- **Real-time**: Socket.io
- **File Upload**: Multer + Cloudinary
- **Video Processing**: FFmpeg
- **SMS/Communication**: Twilio
- **Security**: Helmet, CORS, Compression

### DevOps & Tools
- **Version Control**: Git with Submodules
- **Package Manager**: npm
- **Linting**: ESLint
- **Code Formatting**: Prettier
- **Testing**: Jest (planned)
- **CI/CD**: GitHub Actions (planned)

## 🚀 Getting Started

### Prerequisites

Before running this application, make sure you have the following installed:

- **Node.js** v18.x or higher ([Download](https://nodejs.org/))
- **MongoDB** v6.x or higher ([Download](https://www.mongodb.com/))
- **Git** v2.x or higher ([Download](https://git-scm.com/))
- **FFmpeg** (for video processing) ([Download](https://ffmpeg.org/))

### Installation

1. **Clone the repository with submodules**:
   ```bash
   git clone --recurse-submodules https://github.com/khoatnn/HAKO.git
   cd HAKO
   ```

2. **Install backend dependencies**:
   ```bash
   cd bach-end
   npm install
   ```

3. **Install frontend dependencies**:
   ```bash
   cd ../front-end
   npm install
   ```

4. **Environment Setup**:
   - Copy `.env.example` files in both `bach-end` and `front-end` directories
   - Configure your environment variables (MongoDB URI, JWT secrets, Cloudinary keys, etc.)

### Running the Application

#### Development Mode

**Start Backend Server** (Port 5000):
```bash
cd bach-end
npm run server
```

**Start Frontend Development Server** (Port 3000):
```bash
cd front-end
npm run dev
```

The application will be available at:
- Frontend: http://localhost:3000
- Backend API: http://localhost:5000

#### Production Mode

**Build and Start Frontend**:
```bash
cd front-end
npm run build
npm start
```

**Start Backend**:
```bash
cd bach-end
npm start
```

## 🔧 Development Commands

### Frontend
```bash
cd front-end
npm run dev          # Start development server
npm run build        # Build for production
npm run start        # Start production server
npm run lint         # Run ESLint
```

### Backend
```bash
cd bach-end
npm run server       # Start development server
npm start            # Start production server
npm run dev          # Start with nodemon
```

### Submodules Management
```bash
# Update all submodules to latest
git submodule update --remote

# Initialize submodules (if not cloned with --recurse-submodules)
git submodule update --init --recursive
```

## 📡 API Documentation

The backend provides a comprehensive REST API with the following main endpoints:

- `POST /api/auth/login` - User authentication
- `GET /api/posts` - Fetch user feed
- `POST /api/posts` - Create new post
- `GET /api/messages` - Fetch messages
- `POST /api/messages` - Send message
- `GET /api/stories` - Fetch stories
- `POST /api/stories` - Create story

For detailed API documentation, see the [Backend README](bach-end/README.md).

## 🤝 Contributing

We welcome contributions! Please follow these steps:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Commit your changes: `git commit -m 'Add amazing feature'`
4. Push to the branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

### Development Guidelines
- Follow the existing code style
- Write meaningful commit messages
- Test your changes thoroughly
- Update documentation as needed

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Inspired by Instagram's design and functionality
- Built with modern web technologies and best practices
- Special thanks to the open-source community

## 📞 Support

If you have any questions or need help, please:
- Open an issue on GitHub
- Check the documentation in each submodule
- Review existing issues for similar problems

---

**Note**: This project is for educational purposes and demonstrates modern full-stack development practices. It is not affiliated with Instagram or Meta Platforms, Inc.
- Each submodule can be developed and deployed independently

## 📄 License

Copyright © 2025 khoatnn. All rights reserved.

This project is proprietary and confidential. Unauthorized copying, modification, distribution, or use of this project, via any medium is strictly prohibited.

## 👤 Contact

**khoatnn**

- 📧 Email: [tokhoatnn@gmail.com](mailto:tokhoatnn@gmail.com)
- 📘 Facebook: [khoatnn63](https://www.facebook.com/khoatnn63/)
- 💻 GitHub: [@khoatnn](https://github.com/khoatnn)

---

**Note:** This is a clone project for educational purposes. Please comply with Instagram's terms of service and respect intellectual property rights.
