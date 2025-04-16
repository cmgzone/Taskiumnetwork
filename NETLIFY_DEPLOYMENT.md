# TSK Platform Netlify Deployment Guide

This guide provides detailed instructions for deploying the frontend of the TSK Platform to Netlify.

## Overview

The TSK Platform can be deployed using a hybrid approach:
- **Frontend**: Deploy to Netlify (this guide)
- **Backend**: Run on Replit, Render, or your preferred hosting platform

## Prerequisites

1. A Netlify account (free tier works for testing)
2. The frontend codebase from the TSK Platform project
3. A running backend API (on Replit, Render, or elsewhere)

## Step 1: Prepare the Frontend

1. Copy the `client` directory and necessary configuration files from the TSK Platform project
2. Ensure you have the following files:
   - `package.json`
   - `vite.config.ts`
   - `tailwind.config.ts`
   - `tsconfig.json`
   - `netlify.toml` (create if not present - see below)

3. Create a `netlify.toml` file in the root directory with the following content:
   ```toml
   [build]
     command = "npm run build:client"
     publish = "client/dist"
   
   [[redirects]]
     from = "/*"
     to = "/index.html"
     status = 200
   ```

## Step 2: Set Up Netlify Project

1. Log in to your Netlify account at [netlify.com](https://netlify.com)
2. Click "Add new site" and select "Import an existing project"
3. Connect your GitHub repository or drag and drop your frontend directory

4. Configure the project:
   - Build command: `npm run build:client` (should be set from netlify.toml)
   - Publish directory: `client/dist` (should be set from netlify.toml)

## Step 3: Configure Environment Variables

1. In your Netlify site settings, go to "Environment variables"
2. Add the following environment variable:
   ```
   VITE_API_URL=https://your-backend-api-url.com
   ```
   Replace `https://your-backend-api-url.com` with your actual backend API URL
   (e.g., `https://tsk-platform-api.replit.app` if using Replit)

## Step 4: Deploy

1. Click "Deploy site" to start the deployment process
2. Netlify will build and deploy your frontend application
3. Once completed, you'll get a URL for your deployed application
   (e.g., `https://tsk-platform.netlify.app`)

## Step 5: Set Up Custom Domain (Optional)

1. In your Netlify site settings, go to "Domain management"
2. Click "Add custom domain" and enter your domain
3. Follow the instructions to configure DNS settings for your domain
4. Wait for DNS propagation to complete

## Verifying the Deployment

After deployment, verify that:
1. The frontend loads correctly
2. It can connect to your backend API
3. Authentication works properly
4. All features function as expected

## Troubleshooting Common Issues

### API Connection Issues

If the frontend can't connect to the API:
1. Check the VITE_API_URL environment variable in Netlify
2. Ensure your backend is running and accessible
3. Verify CORS is configured properly on the backend to allow requests from your Netlify domain

### Build Failures

If you encounter build errors:
1. Check the Netlify build logs for specific error messages
2. Ensure all dependencies are properly declared in package.json
3. Verify that the build command and publish directory are correct

### Routing Issues

If you see "Page Not Found" errors when navigating directly to routes:
1. Verify that the `netlify.toml` file has the proper redirect configuration
2. The redirects section should redirect all routes to index.html for SPA routing

## Backend Connection Configuration

For the frontend to properly connect to your backend, ensure:

1. The VITE_API_URL environment variable points to your backend API URL
2. Your backend has CORS configured to allow requests from your Netlify domain:
   ```javascript
   // Example CORS configuration in your backend
   app.use(cors({
     origin: ['https://your-frontend-domain.netlify.app'],
     credentials: true
   }));
   ```

## Keeping the Frontend Updated

To update your frontend after making changes:
1. Push your changes to the GitHub repository (if using GitHub)
2. Netlify will automatically rebuild and deploy the updates
3. Or manually redeploy from your local files if not using GitHub

---

© 2025 TSK Platform | All Rights Reserved