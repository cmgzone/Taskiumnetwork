# TSK Platform

A cutting-edge decentralized AI-powered blockchain learning platform that transforms complex technological education into an engaging, interactive experience. The platform leverages advanced gamification and adaptive learning mechanisms to make blockchain knowledge accessible and enjoyable for learners of all levels.

## Features

- **Custom Wallet Integration**: Seamless BNB Smart Chain wallet implementation
- **Advanced Learning Paths**: Progressive blockchain education content with adaptive difficulty
- **Gamification Elements**: Mining, rewards, and achievements to incentivize learning
- **Marketplace**: Buy, sell, and trade digital assets within the platform
- **AI-Powered Assistance**: Intelligent chatbot and personalized learning recommendations
- **Admin Dashboard**: Comprehensive tools for content management and user administration

## Getting Started

### Prerequisites

- Node.js (v20+)
- PostgreSQL database
- (Optional) BSC Testnet/Mainnet connection for blockchain features

### Installation

1. Clone the repository:
   ```
   git clone https://github.com/YOUR_USERNAME/tsk-platform.git
   cd tsk-platform
   ```

2. Install dependencies:
   ```
   npm install
   ```

3. Set up environment variables:
   ```
   cp .env.example .env
   ```
   Edit the `.env` file with your database credentials and other configuration.

4. Initialize the database:
   ```
   npm run db:push
   ```

5. Start the development server:
   ```
   npm run dev
   ```

## Project Structure

- `/client` - Frontend React application
- `/server` - Backend Express.js API
- `/shared` - Shared types and utilities
- `/contracts` - Smart contract code
- `/public` - Static assets

## Deployment Options

This repository contains everything needed to deploy the TSK Platform. You have several options:

### Option 1: Complete Full-Stack Deployment (Render)

Deploy both frontend and backend together using Render:

1. Follow the instructions in [RENDER_DEPLOYMENT.md](RENDER_DEPLOYMENT.md)
2. Uses Render's Blueprint feature with `render.yaml` configuration

### Option 2: Hybrid Deployment

Deploy the frontend and backend separately:

1. Frontend on Vercel: Follow [VERCEL_DEPLOYMENT.md](VERCEL_DEPLOYMENT.md)
2. Backend on Replit: Use the existing backend at `https://tsk-platform-api.replit.app`

### Option 3: Netlify Frontend Deployment

Deploy the frontend on Netlify:

1. Follow the instructions in [NETLIFY_DEPLOYMENT.md](NETLIFY_DEPLOYMENT.md) 
2. Uses `netlify.toml` configuration for SPA routing

## Environment Variables

Key environment variables needed for deployment:

- `DATABASE_URL` - PostgreSQL connection string
- `SESSION_SECRET` - Secret for session encryption
- `CORS_ORIGIN` - Allowed origins for CORS
- `VITE_API_URL` - Backend API URL (frontend only)

See `.env.example` for a complete list.

## Core Technologies

- **Frontend**: React, TypeScript, TailwindCSS, shadcn/ui
- **Backend**: Express.js, TypeScript, Drizzle ORM
- **Database**: PostgreSQL
- **Blockchain**: Ethers.js, BNB Smart Chain
- **AI**: OpenAI integration for intelligent assistance

## API Documentation

The API includes the following main endpoints:

- `/api/auth/*` - Authentication endpoints (login, register, etc.)
- `/api/users/*` - User management endpoints
- `/api/wallet/*` - Blockchain wallet operations
- `/api/courses/*` - Learning content endpoints
- `/api/marketplace/*` - Asset marketplace endpoints
- `/api/ai/*` - AI assistant endpoints

## Health Check Endpoints

- `/api/health` - Checks if the API is running
- `/api/health/db` - Checks database connectivity

## Creating Admin Users

Use the provided script to create an admin user:

```
node scripts/create-admin.js <username> <password>
```

## License

Copyright © 2025 TSK Platform | All Rights Reserved