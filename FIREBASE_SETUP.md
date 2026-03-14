# Firebase setup for My Week

1. **Create a Firebase project**  
   Go to [Firebase Console](https://console.firebase.google.com/) → Add project (or use an existing one).

2. **Enable Authentication**  
   In the project: Build → Authentication → Get started → enable **Email/Password** (first option).

3. **Create a Firestore database**  
   Build → Firestore Database → Create database → Start in **test mode** (you’ll lock it down with rules next). Pick a region.

4. **Get your config**  
   Project settings (gear) → General → scroll to “Your apps” → Add app → Web (</>).  
   Copy the `firebaseConfig` object. In `susanSchedule.html`, replace the `FIREBASE_CONFIG` object with your values:
   - `apiKey`
   - `authDomain`
   - `projectId`
   - `storageBucket`
   - `messagingSenderId`
   - `appId`

5. **Deploy Firestore rules**  
   Install the Firebase CLI: `npm install -g firebase-tools`  
   Log in: `firebase login`  
   In this folder: `firebase init firestore` (choose the project, use `firestore.rules` as the rules file).  
   Then: `firebase deploy --only firestore:rules`

6. **Deploy the app**  
   Push to GitHub and turn on GitHub Pages for the repo, or use Firebase Hosting: `firebase init hosting` then `firebase deploy`.

After setup, opening the app shows the sign-in screen. Your mom can **Create account** once (email + password), then **Sign in** on any device; her schedule is stored in Firestore and stays in sync.
