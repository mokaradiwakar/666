# Idea2Impact — Firebase Auth Fixed

## What is fixed
- Email/password Create Account creates a real Firebase Auth user and Firestore profile.
- Signup routes to the correct dashboard: Citizen, University, Industry or NGO.
- Login now requires a role and verifies the selected role against the Firestore profile.
- Google signup uses a popup flow and then creates the Idea2Impact profile.
- Google signup asks for an Idea2Impact website password so the same account can later use email/password.
- Google login requires a role and checks it against the stored profile.
- Wrong role selection is rejected instead of opening the wrong dashboard.

## Firebase setup
1. Firebase Console → Authentication → Sign-in method → enable Email/Password.
2. Enable Google.
3. Authentication → Settings → Authorized domains → add your deployed domain. `localhost` should be present for local development.
4. Firestore Database → Rules → paste the included `firestore.rules` and Publish.
5. Run from a web server. Do not double-click the HTML file.

## Local run
```bash
python3 -m http.server 5500
```
Open:
`http://localhost:5500`

## Important
If you see `permission-denied`, publish the included `firestore.rules`.
If Google says the domain is unauthorized, add the exact domain under Firebase Authentication → Settings → Authorized domains.
If Google sign-in is disabled, enable Google under Authentication → Sign-in method.
