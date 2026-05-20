# MICH Digital Shop 🚀
**Pakistan's #1 Premium Reseller Marketplace**
Pure HTML + CSS + JavaScript PWA — No build tools needed!

---

## ⚡ Deploy in 60 Seconds (Vercel)

1. Go to **vercel.com** → New Project
2. Upload this folder OR connect GitHub repo
3. No build settings needed — just deploy!
4. Set custom domain: **michshop.vercel.app**

---

## 🔧 Firebase Setup (IMPORTANT)

Go to **Firebase Console** → `ramadan-2385b` project:

### Enable Authentication:
- Email/Password ✅
- Google ✅

### Create Firestore Database:
- Start in **Test Mode** first
- Then apply these security rules:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{uid} {
      allow read, write: if request.auth.uid == uid;
      allow read: if request.auth != null;
    }
    match /catalogs/{doc} {
      allow read: if true;
      allow write: if request.auth != null && get(/databases/$(database)/documents/users/$(request.auth.uid)).data.role == 'admin';
    }
    match /orders/{doc} {
      allow create: if true;
      allow read, update: if request.auth != null;
    }
    match /earnings/{doc} {
      allow read, write: if request.auth != null;
    }
    match /withdrawals/{doc} {
      allow create: if request.auth != null;
      allow read, update: if request.auth != null;
    }
    match /shares/{doc}   { allow read, write: if true; }
    match /clients/{doc}  { allow read, write: if request.auth != null; }
    match /notifications/{doc} { allow read, write: if request.auth != null; }
    match /settings/{doc} { allow read: if true; }
  }
}
```

### Make yourself Admin:
1. Login to your app
2. Go to Firebase Console → Firestore → `users` collection
3. Find your user document
4. Edit `role` field → change to `admin`
5. Refresh the app

---

## 📁 File Structure
```
michshop/
├── index.html       ← Main app (SPA shell)
├── css/styles.css   ← All styles
├── js/app.js        ← Complete app logic + Firebase
├── manifest.json    ← PWA config
├── sw.js            ← Service worker (offline)
└── icons/           ← App icons (add your icons here)
```

---

## 🎨 Features Included
- ✅ Google + Email Authentication
- ✅ Product Catalog with Search & Filter
- ✅ Order System (Physical + Digital)
- ✅ Earnings Dashboard with Charts
- ✅ Withdrawal System (JazzCash, Easypaisa, etc.)
- ✅ Admin Panel (Users, Products, Orders, Withdrawals)
- ✅ WhatsApp / Facebook / Telegram Sharing
- ✅ Shareable Product Links
- ✅ Referral System
- ✅ Client Management
- ✅ PWA (Installable on mobile)
- ✅ Glassmorphism Neon Dark UI
- ✅ Mobile App Feel (Bottom Navigation)

---

## 📱 App Icons
Add these to the `/icons/` folder:
- `icon-192.png` (192×192 px)
- `icon-512.png` (512×512 px)

Use your MICH logo: https://i.ibb.co/twVpRFKh/file-0000000018807208a673a881d0f0e953.png

---

**Made with ❤️ for MICH Digital Shop**
