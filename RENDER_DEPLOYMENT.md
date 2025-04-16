# TSK Platform Render Deployment Guide

This guide provides detailed instructions for deploying the complete TSK Platform (both frontend and backend) to Render.

## Overview

The TSK Platform is a full-stack application with separate frontend and backend components:

1. **Backend**: Express.js API server that handles database operations, authentication, and business logic
2. **Frontend**: React/Vite single page application that provides the user interface

## Prerequisites

1. A Render account (free tier works for testing)
2. A PostgreSQL database (can be created on Render or use external)
3. The complete TSK Platform codebase from Replit

## Step 1: Deploy the Backend Web Service

1. Log in to your Render account at [render.com](https://render.com)
2. Click "New" and select "Web Service"
3. Connect your GitHub repository or upload the code manually
4. Configure the service as follows:
   - **Name**: tsk-platform-api (or your preferred name)
   - **Environment**: Node
   - **Build Command**: `npm install`
   - **Start Command**: `npm run start:server`
   - **Branch**: main (or your preferred branch)

5. Add the following environment variables:
   ```
   NODE_ENV=production
   DATABASE_URL=your_database_connection_string
   SESSION_SECRET=your_secure_random_string
   PORT=10000
   CLIENT_URL=https://your-frontend-url.onrender.com
   ```

6. Click "Create Web Service"

## Step 2: Deploy the Frontend Static Site

1. In your Render dashboard, click "New" and select "Static Site"
2. Connect your GitHub repository or upload the code manually
3. Configure the service as follows:
   - **Name**: tsk-platform (or your preferred name)
   - **Build Command**: `npm run build:client`
   - **Publish Directory**: `client/dist`
   - **Branch**: main (or your preferred branch)

4. Add the following environment variables:
   ```
   VITE_API_URL=https://your-backend-service-url.onrender.com
   ```

5. Click "Create Static Site"

## Step 3: Set Up the Database

1. In your Render dashboard, click "New" and select "PostgreSQL"
2. Configure your database:
   - **Name**: tsk-platform-db (or your preferred name)
   - **Database**: tsk_platform
   - **User**: tsk_admin
   - Select your preferred region and plan

3. Once created, get the connection details from the dashboard
4. Update the DATABASE_URL environment variable in your backend service

## Step 4: Finalize Configuration

1. In your backend service settings, add the following environment variables:
   ```
   CORS_ORIGIN=https://your-frontend-url.onrender.com
   ```

2. Restart your backend service

## Step 5: Run Database Migrations

1. Connect to your backend service's shell (via Render dashboard)
2. Run the database migration command:
   ```
   npm run db:push
   ```

## Troubleshooting Common Issues

### CORS Errors

If you see CORS errors in the browser console:
1. Verify the CORS_ORIGIN environment variable in the backend service
2. Make sure it matches exactly with your frontend URL (including https://)

### Database Connection Issues

If the backend can't connect to the database:
1. Check the DATABASE_URL environment variable
2. Ensure the database is running and accessible from the backend service
3. Check for any IP restrictions on the database

### Frontend API Connection Issues

If the frontend can't connect to the API:
1. Verify the VITE_API_URL environment variable in the frontend static site
2. Make sure it points to the correct backend service URL
3. Ensure the backend service is running

## Alternative Deployment Strategy

You can also use a hybrid approach:
- Deploy the backend on Render
- Deploy the frontend on Vercel (using our optimized frontend package)

This gives you the best of both platforms - Render's excellent Node.js support for the backend and Vercel's optimized frontend hosting.

---

© 2025 TSK Platform | All Rights Reserved