# Insights+ Demo — Vercel Deployment

## Folder structure
```
insights-vercel/
├── api/
│   └── chat.js          ← Gemini proxy (serverless function)
├── public/
│   └── index.html       ← Your app
├── vercel.json          ← Routing config
└── package.json
```

## Step-by-step deployment

### 1. Get your Gemini API key
- Go to https://aistudio.google.com/app/apikey
- Click "Create API Key"
- Copy it — you'll need it in step 4

### 2. Push to GitHub
- Create a new repo at github.com (can be private)
- Upload this entire `insights-vercel` folder as the repo root
- Commit and push

### 3. Connect to Vercel
- Go to https://vercel.com and sign in (free account is fine)
- Click "Add New Project"
- Import your GitHub repo
- Leave all build settings as default (no framework, no build command needed)
- Click Deploy — it will fail the first time because the API key isn't set yet

### 4. Add your Gemini API key as an environment variable
- In Vercel, go to your project → Settings → Environment Variables
- Add:
  - Name: `GEMINI_API_KEY`
  - Value: (paste your key)
  - Environment: Production (tick all three if you want)
- Click Save

### 5. Redeploy
- Go to Deployments tab → click the three dots on the latest → Redeploy
- Done — you'll have a live public URL like `https://insights-plus-demo.vercel.app`

## That's it
The chat in each widget now calls Gemini 1.5 Flash with the widget's actual data as context.
The visualizations and all dummy data remain exactly as before.
No auth on the URL — anyone with the link can access it.
