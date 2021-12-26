[course vide](https://www.youtube.com/watch?v=q5J5ho7YUhA)
[Firebase quickstart article](https://fireship.io/lessons/firebase-quickstart/)
[source code](https://github.com/fireship-io/3.1-firebase-basics)

# Setup

- go to [firebase dashboard](https://console.firebase.google.com/) to create a project: **Fireship-Demos**
- go to the [project settings](https://console.firebase.google.com/project/fireship-demos-87aa8/overview) to add **Web App**
- copy the `<Script>` to index.html (firebase instruction says to the bottom of the Body; however video directs it to the Header)
  - you can now reference `firebaseas` a global variable in the JavaScript code.
- add [SDKs](https://firebase.google.com/docs/web/setup#available-libraries)
  - Firebase is modular, we can progressively add features we want.
  - from [available libraries, CDN link](https://firebase.google.com/docs/web/learn-more#libraries-cdn), add the following to the above `<script>`
    - `import { auth } from 'https://www.gstatic.com/firebasejs/9.6.1/firebase-auth.js'`
    - `import { firestore } from 'https://www.gstatic.com/firebasejs/9.6.1/firebase-firestore.js'`
- add `<script src="app.js" defer></script>` to above `<Script>`, **defer** makes sure the script loads AFTER the body elements loaded.

- create `App.js`
  - `console.log(firebase)`
- right click `index.html`, Copy Path, and paste it in browser url.

  - we can see the firebase object in browser console

- add VS Code **Firebase Explorer** extension

- connect our local code to the cloud via the Firebase Tools CLIs.
  - `npm install -g firebase-tools`
  - `firebase login` (following instructions for authentication)
  - `firebase init`
    - selected hosting and emulator features
    - selected hosting emulator
    - two files created we can update later
      - `firebase.json`
      - `.firebaserc`

```
    You're about to initialize a Firebase project in this directory:

    /home/david/WebDev/FirebaseBasics

    ? Which Firebase features do you want to set up for this directory? Press Space to select features, then Enter to con
    firm your choices. Hosting: Configure files for Firebase Hosting and (optionally) set up GitHub Action deploys, Hosti
    ng: Set up GitHub Action deploys, Emulators: Set up local emulators for Firebase products

    === Project Setup

    First, let's associate this project directory with a Firebase project.
    You can create multiple project aliases by running firebase use --add,
    but for now we'll just set up a default project.

    ? Please select an option: Use an existing project
    ? Select a default Firebase project for this directory: fireship-demos-87aa8 (Fireship-Demos)
    i  Using project fireship-demos-87aa8 (Fireship-Demos)

    === Hosting Setup

    Your public directory is the folder (relative to your project directory) that
    will contain Hosting assets to be uploaded with firebase deploy. If you
    have a build process for your assets, use your build's output directory.

    ? What do you want to use as your public directory?
    ? Configure as a single-page app (rewrite all urls to /index.html)? Yes
    ? Set up automatic builds and deploys with GitHub? No
    ✔  Wrote /index.html

    === Emulators Setup
    ? Which Firebase emulators do you want to set up? Press Space to select emulators, then Enter to confirm your choices
    . (Press <space> to select, <a> to toggle all, <i> to invert selection)

    i  Writing configuration info to firebase.json...
    i  Writing project information to .firebaserc...
    i  Writing gitignore file to .gitignore...

    ✔  Firebase initialization complete!
```

- `firebase serve` or `firebase emulators:start`, now you shoud see your site at http://localhost:5000

**Commit 1**

# Deploy

- `firebase deploy`
  - `Error: Must supply a "public" directory when using "destination" rewrites.` (mistake in `firebase init` processs
  - remedied situation by changing `"public": "",` to `"public": "public",` in firebase.json

```
  Deploy complete!

  Project Console: https://console.firebase.google.com/project/fireship-demos-87aa8/overview
  Hosting URL: https://fireship-demos-87aa8.web.app
```

# user authentication

## add user

- firebase console -> Authentication -> Sign-in method, to active email/passoword -> add 003 yahoo with usual pw
- also activated Google sign-in method

## add signin / signout button

- `index.html`
- `app.js`

- test run
  - `firebase serve`
  - click "sign in with Google" at localhost, then "sign out"...

**Commit 2**
