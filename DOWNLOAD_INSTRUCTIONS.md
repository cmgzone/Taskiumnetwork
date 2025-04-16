# TSK Platform Download Instructions

To get the complete TSK Platform codebase, follow these steps:

## Option 1: Download from Replit (Recommended)

1. Go to the Replit project: https://replit.com/@Cmgzone/TSK-Platform
2. Click on the menu icon (three dots) at the top right
3. Select "Download as zip"
4. Extract the zip file to your local machine

## Option 2: Download Frontend-Only Package

If you only need the frontend for Vercel deployment:

1. Go to the Replit project: https://replit.com/@Cmgzone/TSK-Platform
2. Visit the URL: `/vercel-download.html`
3. Click the download button for the Vercel-optimized frontend package

## Option 3: Manual Download

For a more selective download:

1. Use git clone if you have permission: `git clone https://github.com/Cmgzone/Taskium.git`
2. Or download individual directories as needed from Replit

## After Download: Deployment

1. For Render deployment: Follow instructions in RENDER_DEPLOYMENT.md
2. For Vercel deployment: Use the Vercel-optimized frontend package

## Required Files

Make sure your download includes:
- /client (frontend code)
- /server (backend code)
- /shared (shared types and interfaces)
- package.json (dependencies)
- .env.example (template for environment variables)
