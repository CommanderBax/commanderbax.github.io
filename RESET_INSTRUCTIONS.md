# How to Reset Dashboard Data

If you need to reload the player list (like after replacing Hasaranga with George Linde), follow these steps:

## Method 1: Reload CSV File (Recommended)

1. Open the dashboard: https://commanderbax.github.io/auction-dashboard.html
2. Click the green "📁 Load Excel/CSV File" button at the top
3. Select "KPL Round 2.csv" from your computer
4. The dashboard will reload with George Linde instead of Wanindu Hasaranga

**Note:** This will keep all your existing auction data (sold players, teams, etc.) and only update the base player list.

## Method 2: Clear Firebase Data (Full Reset)

If you want to completely reset everything (all sold players, teams, etc.):

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Select your "kpl-auction-c92e3" project
3. Click "Realtime Database" in the left menu
4. Click the three dots (⋮) next to your database URL
5. Select "Delete all data"
6. Confirm the deletion
7. Reload the dashboard and upload the CSV again

**Warning:** This will erase ALL auction data including:
- All sold players
- All team names
- All purchase prices

## Method 3: Update Only the Player List in Firebase

If you want to update just the player list without losing sold player data:

1. Open the dashboard
2. Click "📁 Load Excel/CSV File"
3. Select "KPL Round 2.csv"
4. The system will merge the new player data with existing sales

This is the safest method during an active auction.

## Verifying George Linde is Loaded

After reloading:
1. Go to "All Players" tab
2. Use the search box and type "George Linde"
3. You should see: George Linde | All-Rounder | Overseas | Lucknow | ₹0.25 Cr
4. Wanindu Hasaranga should no longer appear in the list
