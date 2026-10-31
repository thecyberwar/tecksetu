# TechSetu App — Releases

Private release repository for TechSetu Android app.

## Structure

```
techsetu-releases/
├── version.json    ← Served via Render (auto-update check)
├── CHANGELOG.md    ← Version history
└── README.md       ← This file
```

## How Auto-Update Works

1. App opens → fetches `version.json` from Render
2. Compares version with installed app
3. If newer → shows Update modal
4. User clicks "Update Now" → APK downloads from GitHub Releases
5. APK installs → app updates

## Update Release Steps

### Step 1 — Build new APK
```bash
cd D:\TechSetu\app
git add .
git commit -m "v1.x.x — description"
eas build -p android --profile preview
```

### Step 2 — Download APK from EAS
- Go to: https://expo.dev/accounts/techsetu123s-team/projects/techsetu/builds
- Download the .apk file
- Rename to: `techsetu-v1.x.x.apk`

### Step 3 — Create GitHub Release
- Go to this repo → Releases → New Release
- Tag: `v1.x.x`
- Upload: `techsetu-v1.x.x.apk`
- Publish release
- Copy APK download URL

### Step 4 — Update version.json
```json
{
  "version": "1.x.x",
  "url": "https://github.com/.../releases/download/v1.x.x/techsetu-v1.x.x.apk",
  "releaseNotes": "What changed in this version",
  "mandatory": true
}
```

### Step 5 — Push to GitHub
```bash
git add version.json CHANGELOG.md
git commit -m "Release v1.x.x"
git push
```

Render auto-deploys → users get update notification! ✅

## Current Version

See `version.json`

## APK Download

Go to [Releases](../../releases) tab.
