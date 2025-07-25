# AgriConnect - Step by Step VS Code Setup Guide

## Step 1: Create Project Folder

### Windows में:
```bash
# Desktop पर project बनाएं
cd C:\Users\%USERNAME%\Desktop
mkdir agriconnect
cd agriconnect
```

### VS Code open करें:
```bash
code .
```

---

## Step 2: Essential Files बनाएं (Priority Order)

### File 1: package.json
**VS Code में:** `Ctrl+N` → File name: `package.json`

```json
{
  "name": "agriconnect",
  "private": true,
  "version": "1.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "lint": "eslint .",
    "preview": "vite preview"
  },
  "dependencies": {
    "@supabase/supabase-js": "^2.50.4",
    "lucide-react": "^0.344.0",
    "react": "^18.3.1",
    "react-dom": "^18.3.1",
    "react-router-dom": "^7.6.3"
  },
  "devDependencies": {
    "@eslint/js": "^9.9.1",
    "@types/react": "^18.3.5",
    "@types/react-dom": "^18.3.0",
    "@vitejs/plugin-react": "^4.3.1",
    "autoprefixer": "^10.4.18",
    "eslint": "^9.9.1",
    "eslint-plugin-react-hooks": "^5.1.0-rc.0",
    "eslint-plugin-react-refresh": "^0.4.11",
    "globals": "^15.9.0",
    "postcss": "^8.4.35",
    "tailwindcss": "^3.4.1",
    "typescript": "^5.5.3",
    "typescript-eslint": "^8.3.0",
    "vite": "^5.4.2"
  }
}
```

### File 2: tsconfig.json
**New File:** `tsconfig.json`

```json
{
  "files": [],
  "references": [
    { "path": "./tsconfig.app.json" },
    { "path": "./tsconfig.node.json" }
  ]
}
```

### File 3: tsconfig.app.json
**New File:** `tsconfig.app.json`

```json
{
  "compilerOptions": {
    "target": "ES2020",
    "useDefineForClassFields": true,
    "lib": ["ES2020", "DOM", "DOM.Iterable"],
    "module": "ESNext",
    "skipLibCheck": true,
    "moduleResolution": "bundler",
    "allowImportingTsExtensions": true,
    "isolatedModules": true,
    "moduleDetection": "force",
    "noEmit": true,
    "jsx": "react-jsx",
    "strict": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noFallthroughCasesInSwitch": true
  },
  "include": ["src"]
}
```

### File 4: vite.config.ts
**New File:** `vite.config.ts`

```typescript
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';

export default defineConfig({
  plugins: [react()],
  optimizeDeps: {
    exclude: ['lucide-react'],
  },
});
```

### File 5: tailwind.config.js
**New File:** `tailwind.config.js`

```javascript
/** @type {import('tailwindcss').Config} */
export default {
  content: ['./index.html', './src/**/*.{js,ts,jsx,tsx}'],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

---

## Step 3: Install Dependencies

**Terminal में run करें:** `Ctrl + `` (backtick)

```bash
npm install
```

---

## Step 4: Core App Files

### File 6: index.html
**New File:** `index.html`

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" type="image/svg+xml" href="/vite.svg" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>AgriConnect - Empowering Farmers with Technology</title>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.tsx"></script>
  </body>
</html>
```

### File 7: Create src folder और files

**Terminal में:**
```bash
mkdir src
mkdir src/components
mkdir src/components/Layout
mkdir src/pages
mkdir src/contexts
mkdir src/lib
mkdir src/types
mkdir src/utils
mkdir src/hooks
```

### File 8: src/main.tsx
**New File:** `src/main.tsx`

```typescript
import { StrictMode } from 'react';
import { createRoot } from 'react-dom/client';
import App from './App.tsx';
import './index.css';

createRoot(document.getElementById('root')!).render(
  <StrictMode>
    <App />
  </StrictMode>
);
```

### File 9: src/index.css
**New File:** `src/index.css`

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

### File 10: src/App.tsx
**New File:** `src/App.tsx`

```typescript
import React from 'react';
import { BrowserRouter as Router, Routes, Route } from 'react-router-dom';
import { AuthProvider } from './contexts/AuthContext';
import Header from './components/Layout/Header';
import Footer from './components/Layout/Footer';
import Home from './pages/Home';

function App() {
  return (
    <AuthProvider>
      <Router>
        <div className="min-h-screen flex flex-col">
          <Header />
          <main className="flex-grow">
            <Routes>
              <Route path="/" element={<Home />} />
            </Routes>
          </main>
          <Footer />
        </div>
      </Router>
    </AuthProvider>
  );
}

export default App;
```

---

## Step 5: VS Code Configuration

### Create .vscode folder:
```bash
mkdir .vscode
```

### File 11: .vscode/settings.json
**New File:** `.vscode/settings.json`

```json
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": "explicit"
  },
  "typescript.preferences.importModuleSpecifier": "relative",
  "emmet.includeLanguages": {
    "typescript": "html",
    "typescriptreact": "html"
  },
  "files.associations": {
    "*.css": "tailwindcss"
  }
}
```

### File 12: .vscode/extensions.json
**New File:** `.vscode/extensions.json`

```json
{
  "recommendations": [
    "esbenp.prettier-vscode",
    "ms-vscode.vscode-typescript-next",
    "bradlc.vscode-tailwindcss",
    "ms-vscode.vscode-eslint",
    "formulahendry.auto-rename-tag",
    "christian-kohler.path-intellisense"
  ]
}
```

---

## Step 6: Environment Setup

### File 13: .env
**New File:** `.env`

```env
VITE_SUPABASE_URL=your_supabase_url_here
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key_here
```

### File 14: .env.example
**New File:** `.env.example`

```env
VITE_SUPABASE_URL=https://your-project.supabase.co
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key_here
```

---

## Step 7: Test Setup

**Terminal में run करें:**
```bash
npm run dev
```

**Browser में open करें:** `http://localhost:5173`

---

## Next Steps:

1. **Supabase setup करें**
2. **Remaining components बनाएं**
3. **Pages complete करें**
4. **Authentication implement करें**

## Common Issues:

### Error: "Module not found"
```bash
npm install
```

### Error: "Port already in use"
```bash
npm run dev -- --port 3000
```

### VS Code Extensions install करें:
- Prettier
- ESLint
- Tailwind CSS IntelliSense
- Auto Rename Tag

---

**अगला step:** Components और Pages बनाना है। Ready हैं?