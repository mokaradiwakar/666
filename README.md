# Idea2Impact Auth + Role Dashboards

Files: index.html, citizen.html, university.html, industry.html, ngo.html, firestore.rules.

1. Firebase Console -> Project settings -> General -> Your apps -> Web app. Copy the config.
2. In index.html and all four dashboard HTML files replace the six PASTE_YOUR_* values with your Firebase Web config.
3. Authentication -> Sign-in method -> enable Email/Password and Google.
4. Firestore Database -> Create database.
5. Publish firestore.rules.
6. Authentication -> Settings -> Authorized domains: add your deployed domain. Local testing is best with a local web server.

Run with VS Code Live Server, or:
python3 -m http.server 5500
Then open http://localhost:5500

Flow: intro -> Create Account -> choose role -> Firebase Auth + Firestore -> role dashboard. Wrong password is handled by Firebase and this UI adds a 5-failed-attempt, 30-second client lock. Organization roles remain PENDING until coordinator approval.

For production, implement coordinator approval with Firebase Admin SDK/custom claims; never create a public signup option for ADMIN/COORDINATOR.


Firebase configuration: The supplied Firebase Web App configuration has already been inserted into all HTML pages in this ZIP.
