# Firebase Setup for KPL Auction Dashboard

## Step 1: Create Firebase Project (5 minutes)

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Click "Add project"
3. Enter project name: `kpl-auction`
4. Disable Google Analytics (not needed)
5. Click "Create project"

## Step 2: Enable Realtime Database

1. In your Firebase project, click "Realtime Database" in the left menu
2. Click "Create Database"
3. Choose location: **United States** (or closest to you)
4. Start in **Test mode** (we'll secure it later)
5. Click "Enable"

## Step 3: Get Firebase Configuration

1. Click the gear icon ⚙️ next to "Project Overview"
2. Click "Project settings"
3. Scroll down to "Your apps"
4. Click the web icon `</>`
5. Register app name: `KPL Dashboard`
6. Click "Register app"
7. Copy the `firebaseConfig` object

## Step 4: Update auction-dashboard.html

1. Open `auction-dashboard.html` in a text editor
2. Find this section (around line 10-20):

```javascript
const firebaseConfig = {
    apiKey: "AIzaSyBXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
    authDomain: "kpl-auction.firebaseapp.com",
    databaseURL: "https://kpl-auction-default-rtdb.firebaseio.com",
    projectId: "kpl-auction",
    storageBucket: "kpl-auction.appspot.com",
    messagingSenderId: "123456789",
    appId: "1:123456789:web:xxxxxxxxxxxxx"
};
```

3. Replace it with YOUR config from Firebase
4. Save the file

## Step 5: Set Database Rules (Security)

1. In Firebase Console, go to "Realtime Database"
2. Click "Rules" tab
3. Replace with these rules:

```json
{
  "rules": {
    "players": {
      ".read": true,
      ".write": true
    },
    "teams": {
      ".read": true,
      ".write": true
    }
  }
}
```

4. Click "Publish"

## Step 6: Deploy to GitHub Pages

```bash
git add auction-dashboard.html FIREBASE_SETUP.md
git commit -m "Add Firebase real-time sync"
git push
```

## Step 7: Test Real-Time Sync

1. Open your dashboard: https://commanderbax.github.io/auction-dashboard.html
2. Load the CSV file
3. Open the same URL in another browser/tab
4. Sell a player in one tab
5. Watch it update instantly in the other tab! 🎉

## How It Works

- **Real-Time Updates**: When anyone sells a player, it syncs to Firebase
- **All Users See Changes**: Everyone viewing the dashboard sees updates instantly
- **No Refresh Needed**: Changes appear automatically
- **Fallback**: If Firebase fails, it uses local storage

## Sync Status Indicator

Look for the sync status in the header:
- 🔄 **Live Sync Active** = Firebase working, real-time updates enabled
- **Local Mode (No Sync)** = Using local storage only

## Free Tier Limits

Firebase Spark (free) plan includes:
- 1 GB stored data
- 10 GB/month downloaded
- 100 simultaneous connections

This is MORE than enough for your auction!

## Troubleshooting

**"Local Mode (No Sync)" showing?**
- Check that you replaced the Firebase config with your own
- Make sure Realtime Database is enabled in Firebase Console
- Check browser console (F12) for errors

**Changes not syncing?**
- Verify database rules are set to allow read/write
- Check your internet connection
- Look at Firebase Console > Realtime Database to see if data is being written

## Need Help?

Check the browser console (F12) for error messages. Common issues:
- Wrong Firebase config
- Database rules not set
- Internet connection issues
