# TSK Platform - Full-Stack Deployment

This repository contains configuration files for deploying the TSK Platform.

## Deployment Options

You have several options for deploying the TSK Platform:

### Option 1: Download & Deploy from Replit

1. Go to the Replit project at: https://replit.com/@Cmgzone/TSK-Platform
2. Download the entire codebase using Replit's download option
3. Deploy to Render using the instructions in `render_deployment_guide.md`

### Option 2: Vercel Frontend Deployment

For frontend-only deployment:

1. Visit `/vercel-download.html` in the Replit project
2. Download the Vercel-optimized frontend package
3. Deploy to Vercel with the following settings:
   - Build Command: `npm run build`
   - Output Directory: `dist`
   - Environment variables:
     - VITE_API_URL=https://tsk-platform-api.replit.app

### Option 3: Render Blueprint Deployment

If you have the entire codebase:

1. Add this repository's `render.yaml` to your project root
2. Push to GitHub
3. Use Render's "Blueprint" deployment option

## Project Structure

- **/client**: Frontend React application
- **/server**: Backend Express API
- **/shared**: Shared types and utilities
- **/contracts**: Smart contract code

## Core Technologies

- TypeScript full-stack blockchain application
- PostgreSQL database for data persistence
- React frontend with dynamic, interactive interfaces
- Express.js backend with enhanced security protocols
- Custom wallet implementation with BNB Smart Chain support
- AI-driven personalized learning mechanisms

## License

Copyright © 2025 TSK Platform | All Rights Reserved
