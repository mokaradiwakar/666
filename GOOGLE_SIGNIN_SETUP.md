# Idea2Impact — Firebase Google Sign-In Repair

This version uses Firebase `signInWithPopup()` for both Google Sign-Up and Google Login.
Google Sign-Up no longer asks for a second Idea2Impact password. The Google account itself is the authentication method.

## Firebase Console setup

1. Open Firebase Console and select project `studio-1076302594-e57ec`.
2. Go to **Authentication → Sign-in method**.
3. Enable **Google** and save it.
4. Go to **Authentication → Settings → Authorized domains**. Add the domain where you run this site:
   - `localhost` for local testing
   - your GitHub Pages domain (for example `yourname.github.io`)
   - your Vercel domain (for example `your-project.vercel.app`)
5. Go to **Firestore Database → Rules** and publish the included `firestore.rules`.

## Local testing

Do NOT open `index.html` by double-clicking it. Run a local web server:

```bash
cd Idea2Impact_Auth_GOOGLE_FIXED
python3 -m http.server 5500
```

Open `http://localhost:5500`.

## Google Sign-Up flow

1. Click **Get Started**.
2. Select Citizen, University, Industry, or NGO.
3. Complete the required details.
4. Click **Continue with Google**.
5. Choose a Google account in the popup.
6. Idea2Impact creates the Firebase Auth account/profile and routes to the correct dashboard.

University, Industry, and NGO profiles are stored as `PENDING` for coordinator verification.

## Google Login flow

1. Choose the correct **Account Role**.
2. Click **Continue with Google**.
3. Choose the Google account.
4. The app checks the Firestore profile role before opening the dashboard.

## If Google still does not open

Check the browser console. Common Firebase errors:

- `auth/unauthorized-domain` → add the current website domain under Firebase **Authentication → Settings → Authorized domains**.
- `auth/operation-not-allowed` → enable Google under **Authentication → Sign-in method**.
- `auth/popup-blocked` → allow popups for the site.
- `permission-denied` → publish the included Firestore rules.
- `auth/account-exists-with-different-credential` → that Google email already has an email/password Idea2Impact account; sign in using email/password first.
