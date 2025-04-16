# TSK Platform Vercel Deployment Guide

This guide provides detailed instructions for deploying the frontend of the TSK Platform to Vercel.

## Overview

The TSK Platform can be deployed using a hybrid approach:
- **Frontend**: Deploy to Vercel (this guide)
- **Backend**: Run on Replit, Render, or your preferred hosting platform

## Prerequisites

1. A Vercel account (free tier works for testing)
2. The optimized frontend package from the TSK Platform project
3. A running backend API (on Replit, Render, or elsewhere)

## Step 1: Download the Frontend Package

### Option 1: From Replit
1. Go to the TSK Platform project on Replit
2. Navigate to the URL: `/vercel-download.html`
3. Click the download button to get the `vercel-frontend.zip` file
4. Extract the ZIP file to your local machine

### Option 2: From GitHub
If you have access to the GitHub repository:
1. Download the frontend package from the releases section
2. Or, clone the repository and use the `frontend-for-vercel` directory

## Step 2: Set Up Vercel Project

1. Log in to your Vercel account at [vercel.com](https://vercel.com)
2. Click "Add New" and select "Project"
3. Import your project:
   - If using GitHub: Connect your GitHub account and select the repository
   - If using local files: Drag and drop the extracted frontend files

4. Configure the project:
   - **Framework Preset**: Vite
   - **Build Command**: `npm run build` (should be pre-configured)
   - **Output Directory**: `dist` (should be pre-configured)
   - **Install Command**: `npm install` (should be pre-configured)

## Step 3: Configure Environment Variables

1. In the project settings, go to the "Environment Variables" section
2. Add the following environment variable:
   ```
   VITE_API_URL=https://your-backend-api-url.com
   ```
   Replace `https://your-backend-api-url.com` with your actual backend API URL
   (e.g., `https://tsk-platform-api.replit.app` if using Replit)

## Step 4: Deploy

1. Click "Deploy" to start the deployment process
2. Vercel will build and deploy your frontend application
3. Once completed, you'll get a URL for your deployed application
   (e.g., `https://tsk-platform.vercel.app`)

## Step 5: Set Up Custom Domain (Optional)

1. In your Vercel project, go to the "Domains" section
2. Click "Add" and enter your custom domain
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
1. Check the VITE_API_URL environment variable in Vercel
2. Ensure your backend is running and accessible
3. Verify CORS is configured properly on the backend to allow requests from your Vercel domain

### Build Failures

If you encounter build errors:
1. Check the Vercel build logs for specific error messages
2. Ensure all dependencies are properly declared in package.json
3. Verify that the build command and output directory are correct

### Routing Issues

If you see "Page Not Found" errors when navigating directly to routes:
1. Verify that the `vercel.json` file is present in your project with the proper configuration
2. The file should include a rewrite rule to redirect all routes to index.html for SPA routing

## Backend Connection Configuration

For the frontend to properly connect to your backend, ensure:

1. The VITE_API_URL environment variable points to your backend API URL
2. Your backend has CORS configured to allow requests from your Vercel domain:
   ```javascript
   // Example CORS configuration in your backend
   app.use(cors({
     origin: ['https://your-frontend-domain.vercel.app'],
     credentials: true
   }));
   ```

## Keeping the Frontend Updated

To update your frontend after making changes:
1. Push your changes to the GitHub repository (if using GitHub)
2. Vercel will automatically rebuild and deploy the updates
3. Or manually redeploy from your local files if not using GitHub

---

© 2025 TSK Platform | All Rights Reserved