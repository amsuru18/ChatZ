# ChatZ - Real-time Chat Application

A modern, real-time chat application built with React, Node.js, Socket.IO, and MongoDB. ChatZ provides a seamless messaging experience with user authentication, real-time messaging, and file sharing capabilities.

## 🚀 Features

- **Real-time Messaging**: Instant message delivery using Socket.IO
- **User Authentication**: Secure login and registration with JWT
- **File Sharing**: Upload and share images through Cloudinary
- **Responsive Design**: Modern UI built with Tailwind CSS
- **User Profiles**: Manage your profile and avatar
- **Real-time Notifications**: Get notified of new messages instantly
- **Modern UI/UX**: Clean and intuitive interface

## 🛠️ Tech Stack

### Frontend

- **React 19** - Modern React with latest features
- **Vite** - Fast build tool and development server
- **Tailwind CSS** - Utility-first CSS framework
- **Socket.IO Client** - Real-time communication
- **React Router DOM** - Client-side routing
- **Axios** - HTTP client for API calls
- **React Hot Toast** - Beautiful notifications

### Backend

- **Node.js** - JavaScript runtime
- **Express.js** - Web application framework
- **Socket.IO** - Real-time bidirectional communication
- **MongoDB** - NoSQL database
- **Mongoose** - MongoDB object modeling
- **JWT** - JSON Web Tokens for authentication
- **bcryptjs** - Password hashing
- **Cloudinary** - Cloud image management
- **CORS** - Cross-origin resource sharing

## 📁 Project Structure

```
ChatZ/
├── client/                 # Frontend React application
│   ├── src/
│   │   ├── components/     # Reusable UI components
│   │   ├── pages/         # Page components
│   │   ├── context/       # React context providers
│   │   ├── assets/        # Static assets
│   │   └── lib/           # Utility functions
│   ├── public/            # Public assets
│   └── package.json       # Frontend dependencies
├── server/                # Backend Node.js application
│   ├── controllers/       # Route controllers
│   ├── models/           # Database models
│   ├── routes/           # API routes
│   ├── middleware/       # Custom middleware
│   ├── lib/              # Utility libraries
│   └── package.json      # Backend dependencies
└── README.md             # Project documentation
```

## 🚀 Getting Started

### Prerequisites

- Node.js (v18 or higher)
- npm or yarn
- MongoDB database
- Cloudinary account (for image uploads)

### Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/yourusername/ChatZ.git
   cd ChatZ
   ```

2. **Install frontend dependencies**

   ```bash
   cd client
   npm install
   ```

3. **Install backend dependencies**

   ```bash
   cd ../server
   npm install
   ```

4. **Environment Setup**

   Create `.env` file in the `server` directory:

   ```env
   PORT=5000
   MONGODB_URI=your_mongodb_connection_string
   JWT_SECRET=your_jwt_secret_key
   CLOUDINARY_CLOUD_NAME=your_cloudinary_cloud_name
   CLOUDINARY_API_KEY=your_cloudinary_api_key
   CLOUDINARY_API_SECRET=your_cloudinary_api_secret
   ```

   Create `.env` file in the `client` directory:

   ```env
   VITE_API_URL=http://localhost:5000
   VITE_SOCKET_URL=http://localhost:5000
   ```

5. **Run the development servers**

   **Backend (Terminal 1):**

   ```bash
   cd server
   npm run server
   ```

   **Frontend (Terminal 2):**

   ```bash
   cd client
   npm run dev
   ```

6. **Open your browser**
   - Frontend: http://localhost:5173
   - Backend API: http://localhost:5000

## 🌐 Deployment to Vercel

### Step-by-Step Deployment Guide

#### 1. Prepare Your Repository

1. **Push your code to GitHub**

   ```bash
   git add .
   git commit -m "Initial commit"
   git push origin main
   ```

2. **Ensure your repository is public or you have Vercel Pro for private repos**

#### 2. Deploy Backend (Server)

1. **Go to [Vercel Dashboard](https://vercel.com/dashboard)**
2. **Click "New Project"**
3. **Import your GitHub repository**
4. **Configure the project:**

   - **Framework Preset**: Node.js
   - **Root Directory**: `server`
   - **Build Command**: Leave empty (not needed for Node.js)
   - **Output Directory**: Leave empty
   - **Install Command**: `npm install`

5. **Add Environment Variables:**

   - Go to Project Settings → Environment Variables
   - Add all your environment variables from the server `.env` file:
     - `MONGODB_URI`
     - `JWT_SECRET`
     - `CLOUDINARY_CLOUD_NAME`
     - `CLOUDINARY_API_KEY`
     - `CLOUDINARY_API_SECRET`

6. **Deploy**
   - Click "Deploy"
   - Wait for deployment to complete
   - Note your backend URL (e.g., `https://your-backend.vercel.app`)

#### 3. Deploy Frontend (Client)

1. **Update frontend environment variables**

   - In your local `client/.env` file, update the URLs to point to your deployed backend:

   ```env
   VITE_API_URL=https://your-backend.vercel.app
   VITE_SOCKET_URL=https://your-backend.vercel.app
   ```

2. **Commit and push the changes**

   ```bash
   git add .
   git commit -m "Update API URLs for production"
   git push origin main
   ```

3. **Create a new Vercel project for frontend**

   - Go to Vercel Dashboard
   - Click "New Project"
   - Import the same GitHub repository
   - **Configure the project:**
     - **Framework Preset**: Vite
     - **Root Directory**: `client`
     - **Build Command**: `npm run build`
     - **Output Directory**: `dist`
     - **Install Command**: `npm install`

4. **Add Environment Variables:**

   - Add the same environment variables as in step 2

5. **Deploy**
   - Click "Deploy"
   - Wait for deployment to complete
   - Your frontend will be available at the provided URL

#### 4. Configure CORS (if needed)

If you encounter CORS issues, update your backend CORS configuration in `server/server.js`:

```javascript
app.use(
  cors({
    origin: [
      "https://your-frontend-domain.vercel.app",
      "http://localhost:5173",
    ],
    credentials: true,
  })
);
```

#### 5. Test Your Deployment

1. **Test the backend API**: Visit `https://your-backend.vercel.app/api/health` (if you have a health endpoint)
2. **Test the frontend**: Visit your frontend URL and try to register/login
3. **Test real-time features**: Open multiple browser tabs to test chat functionality

### Important Notes for Vercel Deployment

1. **MongoDB Atlas**: Use MongoDB Atlas for cloud database hosting
2. **Environment Variables**: Never commit `.env` files to your repository
3. **CORS**: Ensure your backend allows requests from your frontend domain
4. **WebSocket**: Vercel supports WebSocket connections for real-time features
5. **File Uploads**: Cloudinary handles file storage, so no additional configuration needed

## 🔧 Available Scripts

### Frontend (client/)

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build
- `npm run lint` - Run ESLint

### Backend (server/)

- `npm run server` - Start development server with nodemon
- `npm start` - Start production server

## 📝 API Endpoints

### Authentication

- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `GET /api/auth/profile` - Get user profile

### Messages

- `GET /api/messages` - Get messages
- `POST /api/messages` - Send a message
- `DELETE /api/messages/:id` - Delete a message

### Users

- `GET /api/users` - Get all users
- `PUT /api/users/profile` - Update user profile
- `POST /api/users/upload-avatar` - Upload avatar

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

**Your Name**

- GitHub: [@yourusername](https://github.com/yourusername)

## 🙏 Acknowledgments

- [Socket.IO](https://socket.io/) for real-time communication
- [Tailwind CSS](https://tailwindcss.com/) for styling
- [Vercel](https://vercel.com/) for hosting
- [Cloudinary](https://cloudinary.com/) for image management
