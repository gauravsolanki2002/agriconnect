# GitHub से VS Code में Direct Connection

## Step 1: GitHub Repository बनाएं

1. **GitHub.com** पर जाएं
2. **New Repository** बनाएं
3. **Repository name:** `agriconnect`
4. **Public/Private** select करें
5. **Create Repository** click करें

## Step 2: VS Code में Clone करें

### Option A: Command Palette से
1. **VS Code open करें**
2. **Ctrl+Shift+P** press करें
3. **Git: Clone** type करें
4. **GitHub repository URL** paste करें
5. **Folder select** करें

### Option B: Terminal से
```bash
# Terminal open करें
git clone https://github.com/yourusername/agriconnect.git
cd agriconnect
code .
```

## Step 3: Files Upload करें

### Automatic Upload:
1. **Files create करें** VS Code में
2. **Source Control** panel open करें (Ctrl+Shift+G)
3. **Changes stage** करें (+)
4. **Commit message** लिखें
5. **Commit & Push** करें

### Manual Upload:
1. **GitHub repository** में जाएं
2. **Upload files** click करें
3. **Drag & drop** files
4. **Commit changes**

## Step 4: VS Code Extensions Install करें

```json
{
  "recommendations": [
    "ms-vscode.vscode-github-pullrequest",
    "github.vscode-pull-request-github",
    "ms-vscode.remote-repositories"
  ]
}
```

## Step 5: Live Development

### GitHub Codespaces:
1. **Repository** में जाएं
2. **Code** button click करें
3. **Create codespace** select करें
4. **Browser में VS Code** open होगा

### Local Development:
```bash
npm install
npm run dev
```