# AgriConnect Setup Guide for VS Code

## Step 1: Prerequisites

1. **Install Node.js** (v16 or higher)
   - Download from: https://nodejs.org/
   - Verify installation: `node --version`

2. **Install VS Code**
   - Download from: https://code.visualstudio.com/

3. **Install Git** (optional but recommended)
   - Download from: https://git-scm.com/

## Step 2: Project Setup

1. **Open VS Code**

2. **Open Terminal in VS Code**
   - Press `Ctrl + `` (backtick) or
   - Go to `View > Terminal`

3. **Navigate to your desired folder**
   ```bash
   cd C:\Users\YourName\Desktop
   # या जहाँ आप project रखना चाहते हैं
   ```

4. **Create project folder**
   ```bash
   mkdir agriconnect
   cd agriconnect
   ```

5. **Open folder in VS Code**
   ```bash
   code .
   ```

## Step 3: Install Dependencies

In VS Code terminal, run:
```bash
npm install
```

## Step 4: Environment Setup

1. **Create `.env` file** in root directory
2. **Copy content from `.env.example`**
3. **Replace with your actual Supabase credentials**

## Step 5: Supabase Setup

1. **Go to** https://supabase.com
2. **Create account** and **new project**
3. **Get your credentials**:
   - Go to Settings > API
   - Copy Project URL and Anon public key
4. **Update `.env` file** with your credentials

## Step 6: Database Setup

1. **Go to Supabase Dashboard**
2. **SQL Editor** में जाएं
3. **Run the SQL** from README.md database setup section

## Step 7: Start Development

```bash
npm run dev
```

Your application will be available at: http://localhost:5173

## Step 8: Recommended VS Code Extensions

The project will automatically suggest installing these extensions:
- Prettier (Code formatter)
- ESLint (Code linting)
- Tailwind CSS IntelliSense
- Auto Rename Tag
- Path Intellisense

## Troubleshooting

### Common Issues:

1. **npm install fails**
   ```bash
   npm cache clean --force
   npm install
   ```

2. **Port 5173 already in use**
   ```bash
   npm run dev -- --port 3000
   ```

3. **Supabase connection issues**
   - Check your `.env` file
   - Verify Supabase credentials
   - Check internet connection

### Getting Help:

- Check console for errors (F12 in browser)
- Look at VS Code terminal for error messages
- Verify all dependencies are installed

## Development Workflow

1. **Make changes** to your code
2. **Save files** (Ctrl+S)
3. **Browser auto-refreshes** with changes
4. **Check console** for any errors
5. **Test features** in browser

## Building for Production

```bash
npm run build
```

Built files will be in `dist/` folder.

## Deployment

The project is configured for Netlify deployment. Simply:
1. Build the project
2. Upload `dist/` folder to Netlify
3. Configure environment variables in Netlify dashboard