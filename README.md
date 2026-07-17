# SafeHaven — GitHub Pages + Firebase Deployment

## 1. Create a Firebase project

Create a project in Firebase, then create a Web App.

Copy the Firebase Web App configuration into `index.html`:

```js
const firebaseConfig = {
    apiKey: "...",
    authDomain: "...",
    projectId: "...",
    storageBucket: "...",
    messagingSenderId: "...",
    appId: "..."
};
```

## 2. Enable Anonymous Authentication

Firebase Console → Authentication → Sign-in method → Anonymous → Enable.

This allows adopters to use the site without creating an account.

## 3. Create Firestore

Firebase Console → Firestore Database → Create database.

The app uses:

```text
artifacts/safehaven-app-v1/public/data/animals
artifacts/safehaven-app-v1/public/data/requests
artifacts/safehaven-app-v1/public/data/users
```

## 4. Add the Firestore rules

Copy `firestore.rules` into Firebase's Firestore Rules editor and publish.

IMPORTANT: the current rules are suitable for testing, not a secure production shelter system. The next improvement should be replacing the frontend password with Firebase Email/Password authentication and checking admin privileges in Firestore Rules.

## 5. Deploy to GitHub Pages

Create a GitHub repository and upload:

```text
index.html
firestore.rules
README.md
```

Then:

```text
Repository Settings
→ Pages
→ Deploy from branch
→ main
→ /root
→ Save
```

Your site will then be available at your GitHub Pages address.

## Current limitation

The old code used:

```js
__firebase_config
__app_id
__initial_auth_token
```

Those variables were provided by the original hosting environment and do not exist on GitHub Pages. This version removes that dependency and uses a normal Firebase Web App configuration.

The admin password is still only a temporary prototype gate. It must be replaced with real Firebase Authentication before using this for a real shelter.
